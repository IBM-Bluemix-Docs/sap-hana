---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-26"

keywords: SAP HANA, {{site.data.keyword.cloud_notm}}, high availability, highly available, SPOF, VLANs, HA, DR, disaster recovery, SAP NetWeaver

subcollection: sap-hana

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}


# Hochverfügbarkeitsunterstützung für IBM Cloud
{: #ha}

{{site.data.keyword.cloud}} Infrastructure as a Service (IaaS) bietet Ihnen eine leistungsfähige Rechenumgebung mit optionaler Betriebssystem-Bereitstellung, die Hochverfügbarkeits- (HA-) Lösungen unterstützt. Die Lösung basiert auf der unterstützten Betriebssystemversion, die in [SAP-Hinweis 2414097 ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://launchpad.support.sap.com/#/notes/2414097){: new_window} erläutert wird. Die Hochverfügbarkeitslösung ist auf die bestellten Betriebssystemlizenzen begrenzt, die Inhalt Ihrer Bereitstellung sind, oder auf Lizenzen anderer Anbieter wie z. B. "Bring your own license" (BYOL). Achten Sie unbedingt darauf, die Details zur Hochverfügbarkeit mit dem {{site.data.keyword.cloud_notm}} Support besprochen zu haben, bevor Sie mit Ihrer Bereitstellung beginnen.

Die von {{site.data.keyword.cloud_notm}} für SAP unterstützten und bereitgestellten Betriebssysteme sind:
* Linux [Red Hat Enterprise Linux (RHEL) oder SUSE Enterprise Linux Server (SLES)] unterstützen sowohl die SAP NetWeaver- als auch die SAP HANA-Hochverfügbarkeitslösung. Für die {{site.data.keyword.cloud_notm}}-Umgebung bestehen geringfügige Einschränkungen, die in der [Übersicht über die SAP NetWeaver-Hochverfügbarkeitskonfigurationen](#overview-configs) erläutert werden.
* Microsoft Windows unterstützt nur die SAP NetWeaver-Hochverfügbarkeitslösung (Grund sind Einschränkungen der SAP HANA-Datenbank).

## Übersicht über die SAP NetWeaver-Hochverfügbarkeitskonfigurationen
{: #overview-configs}

Es gibt zahlreiche Dokumente, die Ihnen bei der Planung und Installation einer HA-Umgebung für SAP-Services eine umfassende Hilfe bieten. Die Dokumente enthalten Informationen zu Failover, Replikation, Scale-out und Disaster-Recovery (DR). An entsprechenden Stellen werden Verweise auf bestimmte Dokumente angegeben.

Alle Betriebssysteme und Verteilungen, die von {{site.data.keyword.cloud_notm}} für eine SAP-Bereitstellung (Windows, Linux RHEL und SLES) unterstützt werden, umfassen Hochverfügbarkeitssoftware und spezifische Erweiterungen. Folgende Betriebssysteme und Verteilungen werden unterstützt.

* [Neue Verbesserungen der Failover-Cluster in Windows Server 2012 und ihre Vorteile für die Hochverfügbarkeit von SAP NetWeaver ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://blogs.sap.com/2013/10/16/new-failover-clustering-improvements-in-windows-server-2012-and-its-benefits-for-sap-netweaver-high-availability/){: new_window} enthält eine Beschreibung auf Grundlage von Microsoft Windows Server Failover Clustering (WFSC) auf dem Windows Betriebssystem mit SAP NetWeaver.

* Es gibt zwei Verweise zur Hilfestellung bei der Bereitstellung von SAP NetWeaver in einer Linux-basierten HA-Umgebung mit Linux Pacemaker:
  * SUSE SAP NetWeaver-Hochverfügbarkeitscluster 7.40 - Installationshandbuch
  * Bereitstellung von hoch verfügbaren SAP NetWeaver-basierten Servern mit Red Hat Enterprise Linux-HA-Add-on und Pacemaker

* [Erstellung von Hochverfügbarkeit für SAP NetWeaver und SAP HANA unter Linux ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://support.sap.com/content/dam/SAAP/SAP_Activate/AGS_70.pdf){: new_window} ist ein SAP-Dokument zu Best Practices, das eine umfassende technische Beschreibung mit ausdrücklichem Fokus auf SAP HANA bietet.

* [SAP NetWeaver-Hochverfügbarkeit und Business-Continuity in virtuellen Umgebungen mit VMware und Hyper-V unter Microsoft Windows ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://www.sap.com/documents/2015/07/508b62bc-5b7c-0010-82c7-eda71af511fa.html){: new_window} behandelt die Aspekte der Virtualisierung für den Fall, dass Sie Hochverfügbarkeit auf virtualisierten Servern bereitstellen möchten.

Weitere Hochverfügbarkeits-Produkte, die von SAP-Partnern für Hochverfügbarkeitsszenarios zertifiziert sind, finden Sie unter [Informationen für Hochverfügbarkeits-Partner ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://wiki.scn.sap.com/wiki/display/SI/High+Availability+Partner+Information){: new_window}. Für Nicht-HANA SAP-Datenbanken stehen weitere Informationen zum HA-Failover und zu DR-Konfigurationen in Ihrer Datenbankdokumentation zur Verfügung.

Beachten Sie, dass in der Regel gemeinsamer Zugriff auf Network File System (NFS)/Common Internet File System (CIFS)-Speicherung oder aber gemeinsamer Zugriff auf iSCSI-basierten LUN-Speicher (Logical Unique Number) erforderlich ist, um ein System-Failover zu unterstützen. Für die Unterstützung einer DR-ähnlichen Konfiguration ist zumeist lokaler Speicher in Kombination mit einer Replikationsmethode erforderlich. Wie bei lokalen Installationen berücksichtigen Sie bei der Planung Ihrer Bereitstellung die Leistungs- und Latenzvoraussetzungen des Datenbankprodukts.

## Zusätzliche Anweisungen
{: #extra-guide}

[Quorum-basierter Speicher](#quorum) und [Aspekte zum Netz](#network) bieten die notwendige Hilfestellung für Ihre Bereitstellung. Abgesehen von den in diesen Abschnitten beschriebenen Aspekten unterscheidet sich die Installation von SAP NetWeaver und dessen Datenbanksystem in einer HA-Umgebung nicht von anderen lokalen Installationen.

### Quorum-basierter Speicher
{: #quorum}

Aufgrund von Sicherheitseinschränkungen in der {{site.data.keyword.cloud_notm}} IBM Cloud-Umgebung ist der netzbasierte Zugriff auf Fernverwaltungseinheiten über die Intelligent Platform Management Interface (IPMI) nicht verfügbar. Clusterumgebungen verwenden in der Regel IPMI-basierte Komponenten für die "Abschirmung von Clusterknoten", um jederzeit ein Quorum zu gewährleisten. Bei Fehlen einer IPMI-fähigen Einheit werden gemeinsam genutzte Speichereinheiten verwendet. In einer {{site.data.keyword.cloud_notm}}-Umgebung werden gemeinsam genutzte Speichereinheiten bereitgestellt, indem ein iSCSI-LUN auf den Servern als Quorumeinheit implementiert wird. Dies kann z. B. ein File Share Witness (FSW) in einem Microsoft-Cluster oder für Linux Pacemaker's Stonith "Storage-Based Death" (SDB ) sein.
* Klicken Sie [auf dieses Symbol ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](http://linux-ha.org/wiki/Cluster_Concepts){: new_window}, um weitere Informationen zu den Konzepten für Linux-Hochverfügbarkeitscluster zu erhalten.
* Klicken Sie [auf dieses Symbol ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://docs.microsoft.com/en-us/windows-server/failover-clustering/manage-cluster-quorum){: new_window}, um weitere Informationen zur Konfiguration und Verwaltung von Quorumservern für Windows Server 2012 und Windows Server 2012 Release 2 zu erhalten.

Der {{site.data.keyword.cloud_notm}}-Speicher besitzt integrierte HA-Funktionen, sodass ein einzelner gemeinsam genutzter iSCSI-LUN keinen Single Point Of Failure (SPOF) einführt, da Ihr Netzlayout redundant ist. Allerdings können die Spezifikationen Ihres Clusterprodukts unter Umständen mehrere Quorumeinheiten erfordern.

### Aspekte zum Netz
{: #network}

Eine {{site.data.keyword.cloud_notm}}-basierte Installation umfasst eine der folgenden Netzkonfigurationen:
* Privates Netz
* Öffentliches Netz
* Öffentliches und privates Netz
* Zwei private Netze (auf Sonderanforderung)

Wie bei lokalen Installationen können in Abhängigkeit von den physischen Einschränkungen der Hardware zusätzliche Netzadapter bestellt werden. Die Einschränkung gilt gleichermaßen für lokale Installationen. Die Bestellung redundanter Netzadapter im Rahmen von Hardwarebereitstellungen trägt zur Vermeidung von SPOFs in Ihrer Netztopologie bei. Redundante Adapter werden in einer Failover-Konfiguration mit LACP (Link Aggregation Control Protocol) eingerichtet. Für Linux werden zur Einrichtung Bonding-Schnittstellen verwendet, für Microsoft Windows Teaming-Adapter. Die {{site.data.keyword.cloud_notm}}-Switch-Infrastruktur, mit der diese Adapter verbunden sind, ist redundant, sodass keine neuen SPOFs eingeführt werden. Die redundante Infrastruktur kann von den bestellten VLANs verwendet werden.

Abhängig von den Netzanforderungen, wie z. B. Replikationsszenarios bei einem DR-Setup, müssen Sie die Position der verbundenen Einheiten und alle neuen Netzanforderungen, die für das jeweilige Produkt spezifisch sind, überprüfen. In einigen Fällen könnten Ihre Anforderungen durch die speicherbasierte {{site.data.keyword.cloud_notm}}-Snapshot-Replikation erfüllt sein. Überprüfen Sie zusammen mit dem {{site.data.keyword.cloud_notm}} Support, welche Lösung sich für den Bedarf Ihrer Geschäftsprozesse am besten eignet.
