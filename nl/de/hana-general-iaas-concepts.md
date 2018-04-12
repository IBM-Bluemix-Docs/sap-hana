---



copyright:
  years: 2017, 2018
lastupdated: "2018-02-02"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# SAP HANA in IBM Cloud-IaaS - Übersicht
{: #iaas-overview}

Eine IaaS- (Infrastructure-as-a-server) Umgebung setzt sich aus mehreren Komponenten zusammen: Rechenzentrum, Computer, Konnektivität, Speicher und Netz. 

## Rechenzentren

Mit Rechenzentren in ganz Nord- und Südamerika, Europa, Asien und Australien können Sie Cloudressourcen jederzeit und an jedem Ort bereitstellen. Jedes Rechenzentrum ist an das globale private Netz von {{site.data.keyword.cloud_notm}} angebunden, wodurch Datenübertragungen in alle Welt schneller und effizienter werden.

Weitere Informationen finden Sie unter [Rechenzentren](https://www.ibm.com/cloud-computing/bluemix/data-centers){: new_window}.

## Bare-Metal-Server

{{site.data.keyword.baremetal_long}} sind physische Server mit eingeschränkten Anpassungsfähigkeiten. Die Server sind für die Verwendung durch Sie oder Ihren Kunden dediziert und werden in keinen Teilen, auch nicht den Serverressourcen, mit anderen {{site.data.keyword.cloud_notm}}-Kunden gemeinsam genutzt. Sie werden als komplette physische Server mit einem Betriebssystem Ihrer Wahl bereitgestellt. Das Betriebssystem für das SAP HANA-Angebot ist Red Hat Linux for SAP HANA 6.7.

Da die Anpassung auf Bare-Metal-Servern begrenzt ist, sind schnellere Bereitstellungszeiten von 1 bis 4 Stunden erhältlich. Eine schnelle Bereitstellung ist hilfreich, wenn Sie versuchen, eine App vor den Wettbewerbern auf den Markt zu bringen.

Es besteht das Angebot eines Arrays von RAM- und CPU-Kombinationen, da die von SAP zertifizierten Server eine vorkonfigurierte Menge an RAM und Anzahl von CPUs besitzen. Die Kombination kann während des Bestellablaufs oder über ein Support-Ticket nach Bereitstellung der Server *nicht* mehr geändert werden.

Weitere Informationen finden Sie unter [Informationen zu Bare-Metal-Servern](https://console.bluemix.net/docs/bare-metal/index.html#about-bare-metal-servers). 

## Netzkonnektivität

Die VPN-Konnektivität (Virtual Private Network) zum {{site.data.keyword.cloud_notm}} Virtual Cloud Network wird bei der Einrichtung Ihres {{site.data.keyword.cloud_notm}}-Kontos automatisch gewährt. Standardmäßig hat Ihr Server eine öffentliche und eine private IP-Adresse. Wenn Ihr Server privat sein soll, können Sie entweder die allgemein zugängliche Schnittstelle nach Bereitstellung Ihres Servers ausschalten oder Ihren Server als privat bestellen. 

Wenngleich die Netzanforderungen für SAP HANA (10 GB redundantes Netz) durch das {{site.data.keyword.cloud_notm}}-Angebot erfüllt sind, müssen je nach Anwendungsszenario möglicherweise bestimmte Key Performance Indicator (KPIs) für Latenz und Durchsatz erfüllt werden. Weitere Informationen dazu, wie festgelegt wird, in welchem Rechenzentrum Ihr SAP HANA-Server positioniert sein soll, und zur Auswahl der besten Lösung für Netzkonnektivität finden Sie in den Aspekten zur [Netzkonnektivität](/docs/infrastructure/sap-hana/hana-considerations.html#network_connectivity).

Weitere Informationen finden Sie unter [Einführung in Virtual Private Network](https://console.bluemix.net/docs/infrastructure/iaas-vpn/getting-started.html#getting-started-with-virtual-private-networking-vpn-) und dem Whitepaper [*SAP HANA - Netzanforderungen*](https://www.sap.com/documents/2016/08/1cd2c2fb-807c-0010-82c7-eda71af511fa.html).

## Speicher
{: #storage}

Mit Ihren {{site.data.keyword.baremetal_short}}n wird ein lokaler Speicher bereitgestellt, der das virtuelle LAN (VLAN) des privaten Netzes von {{site.data.keyword.cloud_notm}} nutzt, um eine auf Unternehmen abgestimmte Sicherheit zu bieten, die den Administratorzugriff nicht beeinträchtigt. Für die SAP HANA-zertifizierten Server ist er so ausgelegt und konfiguriert, dass die von SAP definierten KPIs für Durchsatz und Latenz gemäß den SAP HANA-Zertifizierungskriterien erfüllt sind. Der lokale Speicher hat die relevante Größe der unterschiedlichen Subdateisysteme, wie im SAP HANA-Installationshandbuch (`data.log` und `shared`) definiert. Von Ihrer Seite sind keine weiteren Anpassungen notwendig.

Es gibt zwei Arten von Speicherung für {{site.data.keyword.cloud_notm}}: Blockspeicherung und Dateispeicherung. Aus diesen kann eine für Sicherungen und Wiederherstellungen für SAP HANA gewählt werden. Beide Typen verwenden E/A-Operationen pro Sekunde (IOPS), mit denen der Speicherbedarf bestimmt wird. IOPS werden anhand einer Blockgröße von 16 KB bei einem 50:50-Anteil an Lese- und Schreibvorgängen gemessen. Um maximale IOPS für ein Volumen zu erreichen, müssen ausreichende Netzressourcen vorhanden sein. Zu den weiteren Aspekten gehören die Nutzung des privaten Netzes abseits von Speicher und Hostseite sowie anwendungsspezifische Optimierungen (z. B. IP-Stacks und Warteschlangenlängen). Weitere Informationen finden Sie unter [Einführung in Blockspeicher](https://console.bluemix.net/docs/infrastructure/BlockStorage/index.html#getting-started-with-block-storage) und [Einführung in Dateispeicher](https://console.bluemix.net/docs/infrastructure/FileStorage/index.html#getting-started-with-file-storage).

{{site.data.keyword.cloud_notm}} bietet zudem Network Attached Storage (NAS), wenn Sie nach einer schnellen, kosteneffizienten Sicherungslösung für Ihre Geräte suchen. NAS kann über Network File System (NFS) angehängt und mit File Transfer Protocol (FTP), sowohl mit Parallels Plesk Panel als auch mit cPanel@WHM, genutzt werden.

Der NAS-Speicher ist für beliebige Zwecke einsetzbar, darf aber in diesem Fall *nicht* für Daten oder Protokolldateien von SAP HANA verwendet werden. Der Speicher erfüllt nicht die KPI-Kriterien hinsichtlich der Ein-/Ausgabe. Jedoch kann der Speicher für Sicherungseinheiten und alle anderen Arten von Daten verwendet werden. Er lässt sich für SAP HANA als Backup-Einheit und für Daten und Protokolldateien nutzen, wenn er durch NFS angehängt wird.  
  
NAS- und FTP-Speicher werden monatlich abgerechnet und sind in unterschiedlichen Speichergrößen verfügbar. Die Interaktion mit Ihrem NAS- und FTP-Speicher erfolgt primär über die Befehlszeile oder das Terminal mit dem Betriebssystem oder durch Point-and-click-Interaktionen in den Panels innerhalb des Kundenportals der {{site.data.keyword.cloud_notm}}-Infrastruktur. Innerhalb des Kundenportals können NAS-Details und -Belegung verwendet werden, aber der Service kann nicht außerhalb von Befehlszeile, Kernel oder Steuerkonsole geändert werden.

Weitere Informationen zu NAS in {{site.data.keyword.cloud_notm}}-Umgebungen finden Sie unter [Einführung in NAS](https://console.bluemix.net/docs/infrastructure/network-attached-storage/index.html#getting-started-with-nas).

## Bereitstellung und Verwaltung

{{site.data.keyword.cloud_notm}}-{{site.data.keyword.baremetal_short}} werden über das Kundenportal oder die API der {{site.data.keyword.cloud_notm}}-Infrastruktur bereitgestellt, nachdem Sie Ihr {{site.data.keyword.cloud_notm}}-Kundenkonto eingerichtet haben. Die Server können über das Kundenportal, die API oder die Befehlszeilenschnittstelle (CLI) verwaltet werden. Weitere Informationen finden Sie unter [Informationen zu Bare-Metal-Servern](https://console.bluemix.net/docs/bare-metal/index.html#about-bare-metal-servers).

## Unterstützung

Der [{{site.data.keyword.cloud_notm}}-Kundendienst](https://console.bluemix.net/docs/support/index.html#getting-customer-support) bearbeitet alle auftretenden Support-Fragen und Probleme über verschiedene Kanäle, darunter Chat, Telefon und Ticket-basierter Support. Die Kundendienst wird {{site.data.keyword.cloud_notm}}-Kunden völlig kostenfrei angeboten und deckt die meisten Tickets ab, die an einem Tag eingereicht werden. Weitere Informationen finden Sie unter [Kundenunterstützung erhalten](https://console.bluemix.net./docs/support/index.html#getting-customer-support).

Sie können auch weiterhin Tickets über den SAP-Support erstellen, die sich auf Ihre {{site.data.keyword.cloud_notm}}-IaaS- und auf SAP-Produkte beziehen. Weitere Informationen erhalten Sie vom [SAP-Support](https://support.sap.com/en/index.html) und im [SAP-Hinweis 2414820](https://launchpad.support.sap.com/#/notes/2414820).

## SAP HANA installieren

Ihre SAP HANA-Software muss von einem für SAP HANA zertifizierten Systemverantwortlichen installiert werden, der den Zertifizierungskurs für SAP HANA-Installationen durchlaufen hat. Weitere Informationen finden Sie unter [Wer darf SAP HANA installieren?](http://www.saphanacentral.com/p/who-can-install-sap-hana.html).