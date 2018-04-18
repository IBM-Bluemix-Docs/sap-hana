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


# 3. Determinación de sus aplicaciones SAP

Debe determinar qué aplicaciones basadas en SAP piensa ejecutar en los {{site.data.keyword.baremetal_long}}. Entre los aspectos a considerar a la hora de determinar las aplicaciones destacan:

 * ¿Cómo se va a utilizar la base de datos? Hay dos formas de desplegar SAP HANA. La primera es como base de datos a una pila de SAP NetWeaver, donde principalmente actúa como fuente de datos. El segundo método de despliegue consiste en ejecutar SAP HANA en modalidad autónoma con las aplicaciones desplegadas directamente en el sistema SAP HANA. En cualquiera de los casos, el proceso de dimensionamiento y otros requisitos y dependencias del sistema puede variar en función de cómo se utiliza el sistema (desarrollo y pruebas, prueba de concepto o producción).
 * ¿Cómo tiene previsto utilizar las aplicaciones? ¿El uso previsto es para desarrollo y pruebas o para producción?
 * ¿Utiliza un SSL de servicio de red privada virtual {{site.data.keyword.cloud_notm}} o el protocolo de túnel de punto a punto (PPTP)?
  
## Siguientes pasos

  [4. Dimensionamiento del servidor](/docs/infrastructure/sap-hana/hana-size-server.html)
  
  [5. Determinación de la configuración](/docs/infrastructure/sap-hana/hana-determine-configuration.html)
