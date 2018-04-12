---



copyright:
  years: 2018
lastupdated: "2018-03-02"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}


# 3. SAP-Anwendungen festlegen

Sie müssen die SAP-basierten Anwendungen festlegen, die auf Ihrem {{site.data.keyword.baremetal_long}} ausgeführt werden sollen. Bei Ihrer Entscheidung sollten Sie u. a. folgende Aspekte berücksichtigen:

 * Wie wird die Datenbank verwendet werden? Es gibt zwei Arten der Bereitstellung von SAP HANA. Die erste ist als Datenbank für einen SAP NetWeaver-Stack, wo sie primär als Datenquelle dient. Die zweite Bereitstellungsmethode ist die Ausführung von SAP HANA im Standalone-Modus, während die Anwendungen direkt im SAP HANA-System implementiert werden. In beiden Fällen können die Dimensionierung und andere Systemanforderungen und Abhängigkeiten abweichen, je nachdem, wie Sie Ihr System verwenden (Entwicklung und Tests, Konzeptnachweis oder Produktion).
 * Wie haben Sie vor, die Anwendungen zu verwenden? Ist der vorgesehene Gebrauch Entwicklung, Tests oder Produktion?
 * Verwenden Sie eine {{site.data.keyword.cloud_notm}} Virtual Private Network-Service--SSL oder ein Point-to-Point Tunneling Protocol (PPTP)?
  
## Nächste Schritte

  [4. Server dimensionieren](/docs/infrastructure/sap-hana/hana-size-server.html)
  
  [5. Konfiguration festlegen](/docs/infrastructure/sap-hana/hana-determine-configuration.html)
