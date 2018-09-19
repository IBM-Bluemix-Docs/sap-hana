---



copyright:
  years: 2018
lastupdated: "2018-08-29"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 5. IBM Cloud-Infrastruktur für die Unterstützung von SAP HANA-Mehrfachknotensystemen konfigurieren
{: #multi-node-storage}

{{site.data.keyword.cloud_notm}} unterstützt SAP HANA-Speicher mit mehreren Knoten für OLAP-Workloads (OLAP: Online Analytical Processing) wie SAP Business Warehouse (SAP BW) und SAP BW/4HANA. Die {{site.data.keyword.cloud}}-Lösung für SAP HANA-Mehrfachknotensysteme besteht aus bis zu 15 + 1 Knoten (15 Workerknoten und ein Standbyknoten) für bis zu 30 TB belegtem Hauptspeicher für ein System. 

Bei der Mehrfachknotenoption wird ein einzelnes SAP HANA-System aus mehreren SAP HANA-Knoten erstellt. Zwischen diesen Knoten, die eine einzelne Datenbank bilden, werden Daten verteilt. Diese Konfiguration mit mehreren Knoten unterstützt die Skalierbarkeit und Hochverfügbarkeit durch die Standbykonfiguration. Das {{site.data.keyword.cloud_notm}}-Angebot für diese Konfiguration folgt dem Programm von [SAP HANA Tailored Data Center Integration](https://blogs.saphana.com/2015/02/18/sap-hana-tailored-data-center-integration-tdi-overview/) (TDI) und verwendet für SAP HANA zertifizierte {{site.data.keyword.cloud_notm}}-Server als zentralisierten, gemeinsam genutzten Speicher. 

*Hinweis:* Gehen Sie unbedingt gemäß den unter [Mehrfachknotensystem bestellen](#ordering) dargelegten Konfigurationsrichtlinien vor, um die Anforderungen für SAP HANA TDI zu erfüllen und Anrecht auf Unterstützung von SAP zu haben. 

Folgen Sie den Richtlinien zur Dimensionierung in [Sizing SAP HANA](https://help.sap.com/viewer/eb3777d5495d46c5b2fa773206bbfb46/2.0.00/en-US/d4a122a7bb57101493e3f5ca08e6b039.html), um die erforderliche Größe für Ihr SAP-HANA-Zielsystem einschließlich der Gesamtmenge an Hauptspeicher und Speicher zu ermitteln, die für Ihre Bereitstellung erforderlich ist. Mithilfe der Dimensionierungsanforderungen können Sie feststellen, welche Anzahl von SAP HANA-Knoten für Ihr SAP-HANA-Mehrfachknotensystem erforderlich ist und wie viel Speicher zum Hosten der Daten benötigt wird.

## Netztopologie und Speicherlayout prüfen
{: #reviewing-topology}

Abbildung 1 zeigt die Netztopologie, die für die Konstellation der {{site.data.keyword.cloud_notm}}-Infrastructure as a Service gemäß SAP HANA TDI erforderlich ist. 

Abbildung 1. Netztopologie der IBM Cloud-Infrastructure as a Service gemäß SAP HANA TDI

![Abbildung 1. Netztopologie der IBM Cloud-Infrastructure as a Service gemäß SAP HANA TDI](/images/SAP-BW.png "Netztopologie der IBM Cloud-Infrastructure as a Service gemäß SAP HANA TDI")

## Voraussetzungen einrichten
{: #prerequisites}

Das SAP HANA-Mehrfachknotensystem kann nur funktionieren, wenn bestimmte Netze vorhanden sind. Bevor Sie andere Komponenten für Ihr System bestellen, müssen Sie diese Netze zusammen mit den Datenbankknoten ordnungsgemäß einrichten. Sie benötigen Folgendes: 
* Ein clientseitiges Netz, das die SAP Advanced Business Application Programming-Anwendungsserver (SAP ABAP-Anwendungsserver), SAP HANA Studio-Clients und alle weiteren Netzclients mit dem Mehrfachknotensystem verbindet. Die Optionen für Netzdurchsatz und Verfügbarkeit richten sich dabei jeweils nach dem Einsatzszenario Ihres SAP HANA-Mehrfachknotensystems. Berücksichtigen Sie jeweils die Menge an Daten, die von und zur SAP-HANA-Datenbank übertragen werden, und die KPIs (Key Performance Indicator, wesentliche Leistungsindikatoren) für die Verfügbarkeit, die für Ihre Anwendung erforderlich sind. 
* Ein Speichernetz, das zum Herstellen der Verbindung zum Back-End mit {{site.data.keyword.blockstoragefull}} und {{site.data.keyword.filestorage_full_notm}} erforderlich ist. Zum Maximieren von Leistung und Redundanz ist ein 10-GB-Netz mit zwei Schnittstellen unter Linux erforderlich, die mit dem Link Aggregation Control Protocol (LACP) per Bonding zusammengefasst sind. Ohne die angegebenen Leistungswerte aus den Richtlinien zur Dimensionierung von SAP HANA können die KPIs (Key Performance Indicator, wesentliche Leistungsindikatoren) für SAP HANA TDI nicht erfüllt werden. 
* Ein knotenübergreifendes Netz für die SAP-HANA-interne Kommunikation, das dem Speichernetz entsprechend eingerichtet ist. Das knotenübergreifende Netz wird nur für die Kommunikation zwischen den Knoten und die Datenübertragung verwendet, die gegebenenfalls zwischen den einzelnen Operationen zwischen den Knoten erforderlich ist. Diese erforderliche Netzkonfiguration besteht aus zwei physischen 10-GB-Adaptern unter Linux, die mit LACP per Bonding zusammengefasst sind. 

## Mehrfachknotensystem bestellen
{: #ordering}

Damit die für SAP erforderlichen KPIs (Key Performance Indicator, wesentliche Leistungsindikatoren) für Leistung und Durchsatz erfüllt werden, müssen Ihre VLANs, Ihr Speicher und Ihre Rechenknoten in demselben Rechenzentrum bestellt werden. Wenn Ihre Komponenten über mehrere Rechenzentren verteilt sind, unterstützt SAP Ihr Mehrfachknotensystem nicht. 

1. Bestellen Sie drei verschiedene VLANs und Server mit vier Adaptern (zwei private und zwei öffentliche Adapter). Weitere Informationen zum Bestellen von VLANs finden Sie unter [Schritt 1: Primäre und öffentliche VLANs bestellen](https://console.bluemix.net/docs/infrastructure/virtualization/advanced-single-site-vmware-reference-architecturesoftlayer.html#step-1-ordering-primary-public-and-private-vlans). Weitere Informationen zum Bestellen Ihrer Server finden Sie in [2. Infrastruktur einrichten](https://console.bluemix.net/docs/infrastructure/sap-hana/hana-setting-up-infrastructure.html#set_up_infrastructure). 
2. Richten Sie das ursprüngliche private VLAN als "Speicher-VLAN" ein. 
3. Als Nächstes müssen Sie über den {{site.data.keyword.cloud_notm}}-Support ein [Ticket öffnen](https://console.bluemix.net/docs/get-support/howtogetsupport.html#open-ticket), um Folgendes zu erzielen: 
   a. Verschieben der öffentlichen Schnittstellen auf das zweite VLAN
   b. Bestellen von zwei weiteren Adaptern, die dann dem dritten VLAN zugewiesen werden, das als Client-VLAN agiert

Sie verfügen nun über die Anzahl von Servern, die gemäß Ihrer Dimensionierung erforderlich sind, und Ihr Netz ist so eingerichtet, dass ...
* ... an alle Knoten Speicher angehängt werden kann,
* ... die SAP HANA-Mehrfachknoteninstallation durchgeführt werden kann, nachdem der Speicher anhängt worden ist. 

Ihre LAN-Verbindungen und knotenübergreifenden Verbindung für den Speicher werden durch die Bereitstellung von {{site.data.keyword.cloud_notm}} konfiguriert. Stellen Sie sicher, dass Sie die Verbindungen jeweils mit zwei 10-GB-Adaptern mit Failover-Konfiguration bestellen. Durch diese Konstellation wird die korrekte Konfiguration für Linux-Bonding und LACP sichergestellt. Wenden Sie sich bei Fragen an das {{site.data.keyword.cloud_notm}}-Support-Team. 

Es gibt bestimmte Leistungskriterien, die von {{site.data.keyword.IBM_notm}} {{site.data.keyword.blockstorageshort}} (Endurance) und {{site.data.keyword.IBM_short}} {{site.data.keyword.filestorage_short}} (Performance) erfüllt sein müssen. Für Datenträger für Daten sind für jeden Workerknoten 2 TB Endurance-Speicher mit einem Leistungs-KPI von 10 E/A-Operationen pro Sekunde/GB erforderlich. Ein zusätzlicher, identisch dimensionierter Datenträger ist als SAP HANA-Speicher erforderlich, der von allen Knoten gemeinsam genutzt wird. 

Für Datenträger für Protokolle ist für jeden Knoten ein 512-GB-Datenträger Performance-Speicher mit einem Leistungs-KPI von 10 K E/A-Operationen pro Sekunde erforderlich. 

Zum Bestellen Ihres Endurance- und Performance-Speichers können Sie anhand der Schritte unter [{{site.data.keyword.blockstorageshort}} bereitstellen und verwalten](https://console.bluemix.net/docs/infrastructure/BlockStorage/provisioning-block_storage.html#provisioning-and-managing-block-storage) oder [{{site.data.keyword.filestorage_full_notm}} bereitstellen und verwalten](https://console.bluemix.net/docs/infrastructure/FileStorage/provisioning-file-storage.html#provisioning-and-managing-ibm-file-storage-for-ibm-cloud) vorgehen. 

## SAP HANA-Multiknotensystem konfigurieren
{: #configuring}

Der gemeinsam genutzte SAP-HANA-Datenträger sowie alle Datenträger für Daten und Protokolle müssen für alle Knoten zugänglich sein. Dieser Ansatz bedeutet, dass das gesamte Speicher-VLAN, das Sie gemäß [Mehrfachknotensystem bestellen](#ordering) konfiguriert haben, auf alle Datenträger zugreifen kann. Wenn Sie nicht jede beteiligte IP-Adresse auflisten möchten, machen Sie die Datenträger für das gesamte IP-Teilnetz des VLANs zugänglich. 

Konfigurieren Sie Ihr SAP HANA-Mehrfachknotensystem gemäß den Anweisungen im Dokument [SAP HANA on NetApp FAS Systems with NFS](https://www.netapp.com/us/media/tr-4290.pdf). Verwenden Sie für jeden Datenträger, der angehängt werden soll, die folgenden NFS-Optionen (NFS - Network File System): 

`rw,bg,hard,timeo=600,intr,noatime,vers=4,minorversion=1,lock,rsize=1048576,wsize=1048576` in `/etc/fstab`.

Diese Optionen wurden von NetApp und {{site.data.keyword.cloud_notm}} getestet. Wenden Sie sich an den {{site.data.keyword.cloud_notm}}-Support, falls Sie beabsichtigen, Änderungen an Mountoptionen oder -werten vorzunehmen. 

Nachdem Sie alle Datenträger an alle Knoten angehängt haben, sind Ihre Mehrfachknotenserver konfiguriert, sodass die SAP HANA-Mehrfachknotendatenbank installiert werden kann. Gehen Sie gemäß den Schritten im [SAP HANA Server Installation and Update Guide](https://help.sap.com/viewer/2c1988d620e04368aa4103bf26f17727/2.0.03/en-US) vor, um eine SAP HANA-Datenbank mit der erforderlichen Version zu installieren. 
