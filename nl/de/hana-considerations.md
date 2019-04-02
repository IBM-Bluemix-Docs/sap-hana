---

copyright:
  years: 2017, 2019
lastupdated: "2019-02-26"

keywords: SAP HANA, network connectivity, VLANs, external storage, high availability, highly available, disaster recovery, HA, DR, VLANs,

subcollection: sap-hana

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Bei der Planung einer SAP-Umgebung zu berücksichtigende Aspekte
{: #considerations}

Die SAP-Systeme innerhalb einer Umgebung stellen spezifische Anforderungen an die Konnektivität, sowohl an die Konnektivität untereinander als auch an die zu externen Systemen. Zudem müssen der externe Speicher für Ihre Umgebung sowie die Maßnahmen geplant werden, die zu ergreifen sind, wenn VMware auf Ihrem Server bereitgestellt werden soll.

## Netzkonnektivität
{: #network_connectivity}

[{{site.data.keyword.cloud_notm}}-Netz](/docs/infrastructure/sap-hana?topic=sap-hana-about_ibmcloud_for_sap#ibm_cloud_network) hat eine Übersicht über den {{site.data.keyword.cloud}}-Ansatz für Netzkonnektivität zur Verfügung gestellt. Probleme mit der Netzkonnektivität können zu erheblichen Verzögerungen für Ihr Projekt führen, wenn Sie nicht entsprechend vorausplanen, unabhängig davon, auf welche Weise das System später verwendet werden soll.

Im Allgemeinen gibt es für Ihre als IaaS bereitgestellten {{site.data.keyword.cloud_notm}}-Server zwei Schnittstellenoptionen. Die eine ist eine externe Schnittstelle mit einer öffentlichen IP. Die zweite ist eine interne Schnittstelle mit einer "privaten IP" entsprechend dem Request for Comment (RFC) 1918. Sie können auch eine einzelne interne Schnittstelle mit "privater IP" wählen. Die externe IP ist möglicherweise benutzerfreundlicher, allerdings besteht selbst bei einer installierten und vorkonfigurierten grundlegenden Firewall ein Risiko.

Bei der zweiten Option wird entweder über das Kundenportal der {{site.data.keyword.cloud_notm}}-Infrastruktur auf das {{site.data.keyword.cloud_notm}} Virtual Private Network (VPN) zugegriffen oder eine Sicherheitskomponente in Ihrer Umgebung implementiert. Sicherheitskomponenten werden für Firewalls, Umwandlungen von Netzadressen, VPN-Zugriff und andere Netzfunktionen angeboten. Es wird empfohlen, dass sich Ihre Abteilung für Vernetzung vom [{{site.data.keyword.cloud_notm}}-Support](/docs/get-support?topic=get-support-getting-customer-support#getting-customer-support) beraten lässt, nachdem das Layout Ihrer Umgebung und die für die Schicht der SAP-Anwendung erforderliche Konnektivität festgelegt sind.

### VLANs
{: #vlans}

Wenn Sie unterschiedliche Typen von Netzverkehr in Ihrer Umgebung voneinander trennen möchten, können Sie weitere virtuelle LANs (VLANs) bestellen. Denken Sie daran, dass die zusätzlichen VLANs nur die Trennung des Datenverkehrs bewirken, keine Steigerung der Leistung. SAP empfiehlt im Allgemeinen die Verwendung von 10-GB-Netzen für den Datenverkehr zwischen den Anwendungsservern und den SAP HANA-Datenbanken sowie für andere SAP HANA-Clients wie z. B. SAP Business Intelligence. Wenn Sie den Verwaltungszugriff auf Ihren SAP HANA-Server von anderen Clients trennen möchten, sollten Sie für Ihre Umgebung ein weiteres VLAN bestellen. Eine weitere Option ist die Trennung des Datenverkehrs durch das öffentliche und das private Netz, da weitere "physische" Uplinks von {{site.data.keyword.cloud_notm}} nicht unterstützt werden. Folgen Sie den Empfehlungen von SAP für [SAP HANA Tailored Data Center Integration (TDI) ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://blogs.saphana.com/2015/02/18/sap-hana-tailored-data-center-integration-tdi-overview/){: new_window}.

Der Zugriff über VPN, wie auch der über eine Jumpbox, ermöglicht transparenten Zugriff auf Ihre SAP HANA-Instanzen über SAP HANA Studio.

## Externer Speicher
{: #external_storage}

Zusätzlich zum lokalen Speicher benötigen Sie möglicherweise zusätzlichen externen Speicher, um Backups durchführen zu können. Für diese Anforderungen können Sie Blockspeicher oder Network Attached Storage (NAS) bestellen, wie unter [Speicher](/docs/infrastructure/sap-hana?topic=sap-hana-iaas-overview#storage) beschrieben. Da zusätzliche Blockspeicher- und NFS-Daten (Network File System) über dieselben physischen Adapter wie der gesamte übrige Netzverkehr übertragen werden, müssen die Auswirkungen in Betracht gezogen werden.

Für den externen Speicher ist es wichtig, Ihre Projektanforderungen zu berechnen, bevor Sie sich für eine Speicherlösung entscheiden. Wenn Sie ein SAP HANA-System wiederherstellen müssen, haben die E/A-Operationen pro Sekunde Ihres Speichers signifikanten Einfluss auf Ihr Wiederherstellungsfenster. Backup-Fenster sind bei SAP HANA nicht so kritisch, da alle Backups Online-Backups sind, unabhängig von Ihrer Konfiguration von SAP HANA.

Zum Beispiel können Sie unter Verwendung von {{site.data.keyword.cloud_notm}} {{site.data.keyword.blockstorageshort}} eine ungefähre Wiederherstellung von SAP HANA von 12 TB bei maximaler Geschwindigkeit berechnen. Sie müssen drei physische Speichereinheiten (Blockspeicher-iSCSI-LUNs) erstellen, da die maximale Größe pro Gerät 4 TB beträgt. Sie können mit dem Linux Logical Volume Manager einen Stripe über diese drei Geräte ziehen und eine logische Einheit von 12 TB erstellen.

Die 12 TB ermöglichen Ihnen 3x10 E/A-Operationen pro Sekunde/GB, also insgesamt 122.880 E/A-Operationen pro Sekunde/GB bei 16 KB. Dadurch erhalten Sie eine Wiederherstellungszeit von 1875 GB pro Sekunde oder eine Gesamt-Wiederherstellungszeit von weniger als 2 Stunden. Da die Messung hinsichtlich E/A-Operationen pro Sekunde bei einer Verteilung der Lese- und Schreibvorgänge von 50/50 erfolgt, können Sie die Zahlen als Untergrenze für die Wiederherstellungsleistung betrachten. Es wird empfohlen, Backups und Wiederherstellungstests durchzuführen, wenn Sie sich auf ein bestimmtes Wiederherstellungsfenster verlassen.

{{site.data.keyword.cloud_notm}} {{site.data.keyword.blockstorageshort}}, {{site.data.keyword.filestorage_full_notm}} oder NAS können als Backup-Bereich oder als Speicher für zusätzliche Softwarekomponenten dienen, die auf Ihrem Server installiert sind. {{site.data.keyword.cloud_notm}}-Speicher und NSA können jedoch nicht als Speicher für SAP HANA verwendet werden, da diese Optionen nicht die KPI-Kriterien erfüllen.

Weitere Informationen finden Sie unter [Einführung in {{site.data.keyword.blockstorageshort}}](/docs/infrastructure/BlockStorage?topic=BlockStorage-GettingStarted#GettingStarted) und [Einführung in {{site.data.keyword.filestorage_full_notm}}](/docs/infrastructure/FileStorage?topic=FileStorage-GettingStarted#getting-started-with-file-storage).

## Hochverfügbarkeits- und Disaster Recovery-Szenarien
{: #ha_dr}

Die {{site.data.keyword.cloud_notm}}-Umgebung unterstützt keine vorkonfigurierten Hochverfügbarkeits- (HA-) Szenarien. Sie eröffnet aber die Möglichkeit, HA-Lösungen für SAP HANA über HA-Erweiterungen für Red Hat Enterprise Linux zu implementieren, wie z. B. einen On-Premises-Fall.

Die SAP HANA-Systemreplikation kann mit einem automatisierten Failover von einem Server auf ein Replikat konfiguriert werden. Folgen Sie der SAP-Dokumentation zur Systemreplikation, um den Replikationsmodus zu bestimmen, der am besten zu Ihrem Anwendungsszenario und Ihrem Niveau an Ausfallsicherheit passt. Je nach Replikationsmodus müssen unterschiedliche Netz-KPIs erfüllt werden. Lesen Sie die SAP-Empfehlungen zum Netzdurchsatz und zur Latenz, um den erforderlichen Durchsatz und die maximale Latenz für den Betriebsmodus Ihrer Wahl zu bestimmen. Die {{site.data.keyword.cloud_notm}}-Netztopologie sollte in der Lage sein, alle erforderlichen Konfigurationen zu bedienen. Wenden Sie sich an den {{site.data.keyword.cloud_notm}}-Support, um die optimale Konfiguration für Ihr Szenario zu bestimmen, wenn Sie sich nicht sicher sind oder wenn Sie Ihren Disaster-Recovery-Standort in einem anderen Rechenzentrum wünschen, um maximale Ausfallsicherheit zu erreichen.

Wir weisen darauf hin, dass SAP HANA-Scale-out- (Mehrfachknoten-) Umgebungen noch in der Evaluierung sind. Ein Standby-Knoten für SAP HANA ist also für eine {{site.data.keyword.cloud_notm}}-Umgebung aktuell keine Option.

Weitere Informationen zur Hochverfügbarkeit und Disaster-Recovery finden Sie unter [{{site.data.keyword.cloud_notm}}-Hochverfügbarkeitsunterstützung](/docs/infrastructure/sap-hana?topic=sap-hana-ha#ha) und [Disaster-Recovery](/docs/infrastructure/sap-reference-architecture?topic=sap-reference-architecture-recommendations#dr).

Weitere Informationen zur Systemreplikation und zu Netzdurchsatz und Latenz finden Sie unter folgenden Links:
  * [Vorgehensweise zur Durchführung einer Systemreplikation für SAP HANA ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.sap.com/documents/2013/10/26c02b58-5a7c-0010-82c7-eda71af511fa.html){: new_window}
  * [Für SAP HANA-Systemreplikation erforderliches Netz ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.sap.com/documents/2014/06/babb2b55-5a7c-0010-82c7-eda71af511fa.html){: new_window}

Weitere Informationen zum Einrichten der HA-Clustererweiterungen für Ihr Linux-Betriebssystem finden Sie unter folgenden Links:
  * [Automatisierte SAP HANA-Systemreplikation mit Pacemaker unter RHEL - Installationshandbuch ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://access.redhat.com/articles/1466063){: new_window}
  * [SAP HANA SR - Szenario mit Leistungsoptimierung ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.suse.com/docrep/documents/ir8w88iwu7/suse_linux_enterprise_server_for_sap_applications_12_sp1.pdf){: new_window}

## VMware ESXi-Serverbereitstellungen
{: #vmware_server}

Alle Server im {{site.data.keyword.cloud_notm}} SAP HANA-Angebot sind für VMware ESX zertifiziert, wodurch SAP HANA auf virtuellen Maschinen (VMs) bereitgestellt werden kann. Wird ein Server mit VMware ESX bestellt, wird er mit einer vorinstallierten ESX-Instanz mit Basiskonfiguration bereitgestellt; es wird keine VM implementiert. Wir weisen darauf hin, dass Sie für die Bereitstellung des richtigen Gastbetriebssystems in einer ESX-basierten Implementierung selbst verantwortlich sind. Befolgen Sie die im SAP-Hinweis 2414820 definierten Anweisungen, um eine Betriebssystemversion auszuwählen, die mit SAP HANA in {{site.data.keyword.cloud_notm}} unterstützt wird.

Die Dimensionierung einer ESX-basierten Bereitstellung unterscheidet sich von der einer Bare-Metal-Server-Bereitstellung. Folgen Sie den Empfehlungen im *Handbuch mit Architektur-Leitlinien und Best Practices für Bereitstellungen von SAP HANA in VMware vSphere-Architekturen und technischen Aspekten*. Der Aufwand für die Virtualisierungsebene muss entsprechend den Regeln im *Handbuch mit Architektur-Leitlinien und Best Practices für Bereitstellungen von SAP HANA in VMware vSphere-Architekturen und technischen Aspekten* berechnet werden. Nach der Bereitstellung des Gastbetriebssystems auf einer VM stellen Sie sicher, dass die Key-Performance-Indikatoren für die SAP HANA-TDI erfüllt sind. Details zum Testen der Umgebung hinsichtlich Compliance mit den SAP-Supportvoraussetzungen finden Sie im SAP-Hinweis 1943937. Die Voraussetzungen müssen für jede auf einem bestimmten Server bereitgestellte VM erfüllt sein.

Bei der Bereitstellung von SAP HANA in einer virtualisierten Umgebung müssen noch mehrere andere SAP-definierte Regeln befolgt werden. Für Produktionszwecke berücksichtigen Sie die Einschränkungen, die im SAP-Hinweis 1995460 aufgeführt sind. Der SAP-Hinweis 2024433 beschreibt die Regeln für mehrere VMs auf einem Server.

Weitere Informationen finden Sie in der folgenden Dokumentation:
  * [SAP-Hinweis 2414820 ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://launchpad.support.sap.com/#/notes/2414820){: new_window}
  * [*Handbuch mit Architektur-Leitlinien und Best Practices für Bereitstellungen von SAP HANA in VMware vSphere-Architekturen und technischen Aspekten* ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.vmware.com/content/dam/digitalmarketing/vmware/en/pdf/whitepaper/sap_hana_on_vmware_vsphere_best_practices_guide-white-paper.pdf){: new_window}
  * [SAP-Hinweis 1943937 ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://launchpad.support.sap.com/#/notes/1943937){: new_window}
  * [SAP HANA Tailored Data Center Integration - Häufig gestellte Fragen ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.sap.com/documents/2016/05/e8705aae-717c-0010-82c7-eda71af511fa.html){: new_window}
  * [SAP-Hinweis 1995460 ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://launchpad.support.sap.com/#/notes/1995460){: new_window}
  * [SAP-Hinweis 2024433 ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://launchpad.support.sap.com/#/notes/2024433){: new_window}
  * [SAP HANA Tailored Data Center Intgration (TDI) - Übersicht ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://blogs.saphana.com/2015/02/18/sap-hana-tailored-data-center-integration-tdi-overview/){: new_window}
