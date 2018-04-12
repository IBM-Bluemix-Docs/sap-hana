---



copyright:
  years: 2018
lastupdated: "2018-02-05"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}


# 4. Server dimensionieren
{: #size_the_server}

Nach Ihrer Entscheidung, welche SAP-Lösungen verwendet werden sollen, besteht Ihr nächster Schritt in der Festlegung der Anzahl von {{site.data.keyword.baremetal_long}}n, die Sie zur Unterstützung Ihrer SAP-Umgebung benötigen, und im Sicherstellen, dass die Server richtig dimensioniert sind.
{: shortdesc}

## Nähere Informationen zur Methodik der SAP-Dimensionierung
{: #size_method}

SAP HANA wird in {{site.data.keyword.cloud_notm}} in Einzelknotenkonfigurationen mit folgenden RAM-Gesamtgrößen angeboten: 
  * 512 GB
  * 1024 GB (1 TB)
  * 2048 GB (2 TB)
  * 4096 GB (4 TB)
  * 8192 GB (8 TB)
  
Es handelt sich um eine spaltenorientierte Datenbank, die meist weniger Platz zum Speichern von Daten erfordert als ein herkömmliches zeilenbasiertes RDMS (Relation Database Management System). Die Daten können hoch komprimiert werden und die Komprimierungsverhältnisse können je nach Quellendaten und Datenbank zwischen 3:1 und mehr als 10:1 variieren. 

Ihr Server muss richtig dimensioniert sein, *bevor* Sie ihn erwerben, da die Dimensionierung für den Erfolg Ihres Projekts entscheidend ist. Ein falsch dimensionierter Speicherbedarf kann zur Folge haben, dass später ein Upgrade und eine Migration auf einen größeren Server durchgeführt werden müssen.

## Auf SAP-Schnelldimensionierer zugreifen
{: #quick_sizer}

Der Hauptspeicher ist bei der Dimensionierung einer SAP HANA-zertifizierten Einheit eine der wichtigsten zu berücksichtigenden Ressourcen. Der öffentliche [*SAP HANA-Master-Leitfaden*](https://help.sap.com/doc/e95f6750b0fd10148ea5c6be75016694/2.0.00/en-US/SAP_HANA_Master_Guide_en.pdf) bietet einen Ausgangspunkt für Themen im Zusammenhang mit der Dimensionierung. Die Informationen zur [Dimensionierung von SAP HANA](https://help.sap.com/viewer/eb3777d5495d46c5b2fa773206bbfb46/2.0.00/en-US/d4a122a7bb57101493e3f5ca08e6b039.html) beinhalten Anweisungen zur Dimensionierung des SAP HANA-Systems. Sie verweisen auf die unterschiedlichen Installations- und Migrationsszenarios sowohl für Greenfield-Installationen als auch für vorhandene Systeme. Es gibt einen Link zur SAP HANA-Version des Tools für die SAP-Schnelldimensionierung (für den Zugriff auf das Tools ist eine SAP S-Benutzer-ID erforderlich). Zudem sind auf der Seite die SAP-Hinweise zur Dimensionierung Ihres SAP HANA-Servers aufgelistet. 

## Dimensionierung für eine virtualisierte Umgebung
{: #size_virtual}

Weitere Dimensionierungsaspekte für die Ausführung von SAP HANA in einer virtualisierten Umgebung finden Sie unter [VMware ESXi-Serverbereitstellungen](/docs/infrastructure/sap-hana/hana-considerations.html#vmware-server) und im [*Handbuch mit Architektur-Leitlinien und Best Practices für Bereitstellungen von SAP HANA in VMware vSphere-Architekturen und technischen Aspekten*](https://www.vmware.com/content/dam/digitalmarketing/vmware/en/pdf/whitepaper/sap_hana_on_vmware_vsphere_best_practices_guide-white-paper.pdf).

## Nächste Schritte

 [5. Konfiguration festlegen](/docs/infrastructure/sap-hana/hana-determine-configuration.html)
