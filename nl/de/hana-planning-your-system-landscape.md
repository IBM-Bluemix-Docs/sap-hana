---

copyright:
  years: 2017, 2019
lastupdated: "2019-02-26"

keywords: SAP HANA, SAP landscape, {{site.data.keyword.cloud_notm}}

subcollection: sap-hana

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Systemumgebung planen
{: #planning-your-system-landscape}

Eine SAP-*Umgebung* ist eine Gruppe von zwei oder mehr SAP-*Systemen*, die gewöhnlich eine Entwicklungsumgebung, eine Qualitätsprüfungs- und Testumgebung und eine Produktionsumgebung umfassen. Ein SAP-System setzt sich aus einer oder mehreren *SAP-Instanzen* zusammen, bei denen es sich um eine Gruppe von Prozessen handelt, die zur selben Zeit gestartet und gestoppt werden. Weitere Informationen zu SAP-Umgebungen finden Sie unter [*SAP Business Suite auf IBM X6-Systemen - Referenzarchitektur* ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://lenovopress.com/redp5073.pdf){: new_window}.
{: shortdesc}

Es gibt mehrere mögliche Umgebungskonfigurationen, z. B. Server (Größe)/Speicher (Größe), für alle SAP-Lösungen auf dem Markt. Zu diesen Lösungen gehören auch SAP NetWeaver-basierte Produkte wie z. B. [SAP Business Suite ![Symbol für externen Link](../../icons/launch-glyph.svg "Symbol für externen Link")](https://open.sap.com/courses/suitehana1){: new_window}, SAP Business Warehouse sowie alle spezifischen SAP-Add-ons, die von den Servern in der SAP-zertifizierten {{site.data.keyword.cloud}}-Infrastruktur unterstützt werden. Weitere zu berücksichtigende Lösungen sind Software anderer Anbieter, die in SAP integriert werden könnte.

SAP HANA kann, je nach Ihrem Einsatzszenario, als Datenbank für eine Stack-basierte SAP NetWeaver-Lösung oder als eigenständige Entität ausgeführt werden. Für beide Szenarios bietet das {{site.data.keyword.cloud_notm}}-Angebot vorkonfigurierte SAP NetWeaver-zertifizierte Server, deren Umgebung aus einem anderen Server aufgebaut sein kann.

Bei der Bestimmung der Größe für Ihren Server auf Grundlage der Anwendungen, die ausgeführt werden sollen, des potenziellen Wachstums und der Leistung sollten Sie so detailliert wie möglich vorgehen. Zudem sollten Sie den Speicherbedarf für Ihre Anwendungen berücksichtigen. Die SAP-Systeme innerhalb einer Umgebung stellen spezifische Anforderungen an die Konnektivität, sowohl an die Konnektivität untereinander als auch an die zu externen Systemen. Weitere Informationen finden Sie unter [Bei der Planung einer SAP-Umgebung zu berücksichtigende Aspekte](/docs/infrastructure/sap-hana?topic=sap-hana-considerations#considerations).

Tabelle 1 enthält die Schritte innerhalb des Planungsprozesses. Anhand dieser Schritte können Sie Ihre SAP-Zielumgebung aufbauen.

Tabelle 1. Planungsprozess - Übersicht

| Schritt | Details |
| --- | --- |
| 1 | [Berechtigungsnachweise für SAP und {{site.data.keyword.cloud_notm}} abrufen und Konten erstellen](/docs/infrastructure/sap-hana?topic=sap-hana-get_sap_ibm_credentials#get_sap_ibm_credentials) |
| 2 | [Alle relevante Dokumentation zu SAP und {{site.data.keyword.cloud_notm}} lesen](/docs/infrastructure/sap-hana?topic=sap-hana-review_doc#review_doc) |
| 3 | [SAP-Anwendungen festlegen](/docs/infrastructure/sap-hana?topic=sap-hana-3-determining-your-sap-applications#3-determining-your-sap-applications) |
| 4 | [Server dimensionieren](/docs/infrastructure/sap-hana?topic=sap-hana-size_the_server#size_the_server) |
| 5 | [Konfiguration festlegen](/docs/infrastructure/sap-hana?topic=sap-hana-determine_configuration#determine_configuration) |

## Nächste Schritte

Wählen Sie in Tabelle 1 den entsprechenden Schritt aus, um mit der Planung Ihrer SAP-Umgebung zu beginnen.
