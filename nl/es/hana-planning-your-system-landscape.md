---



copyright:
  years: 2017, 2018
lastupdated: "2018-02-05"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Planificación del entorno de sistemas
{: #planning-your-system-landscape}

Un *entorno* SAP es un grupo de dos o más *sistemas* SAP, que normalmente incluyen desarrollo, calidad y pruebas y producción. Un sistema SAP consta de una o más *instancias de SAP*, que son un grupo de procesos que se inician y detienen al mismo tiempo. Para obtener más información sobre entornos SAP, consulte [*SAP Business Suite sobre la arquitectura de referencia de IBM X6 Systems*](https://lenovopress.com/redp5073.pdf). 
{: shortdesc}

Existen varias posibles configuraciones de entorno, como servidor (tamaño)/almacenamiento (tamaño), para todas las soluciones SAP del mercado. Estas soluciones incluyen productos basados en SAP NetWeaver, como [SAP Business Suite](https://open.sap.com/courses/suitehana1), SAP Business Warehouse y todos los complementos específicos de SAP, que admiten los servidores de la oferta de {{site.data.keyword.cloud}} para aplicaciones SAP. Otra solución a tener en cuenta es cualquier software de terceros que pueda integrarse con SAP. 

SAP HANA se puede ejecutar como una base de datos para una solución basada en la pila de SAP NetWeaver o como una entidad autónoma dependiendo del caso de uso. En ambos casos, la oferta {{site.data.keyword.cloud_notm}} proporciona servidores preconfigurados con el certificado de SAP NetWeaver alrededor de los cuales se puede crear el entorno desde cualquier otro servidor.

Intente ser lo más detallado posible al determinar el tamaño de su servidor sobre la base de las aplicaciones que tiene previsto ejecutar, el crecimiento potencial y el rendimiento. Además, tenga en cuenta los requisitos de memoria y almacenamiento para sus aplicaciones. Los sistemas SAP en un entorno tienen requisitos específicos para la conectividad, ya sea entre ellos o bien con sistemas externos. Para obtener más información, consulte [Aspectos a considerar cuando planifique su entorno SAP](/docs/infrastructure/sap-hana/hana-considerations.html).

La Tabla 1 contiene los pasos del proceso de planificación. Aplíquela para crear su entorno SAP de destino.

Tabla 1. Visión general del proceso de planificación

| Paso | Detalles |
| --- | --- |
| 1 | [Obtención de credenciales de SAP y {{site.data.keyword.cloud_notm}} y creación de cuentas](/docs/infrastructure/sap-hana/hana-get-credentials.html) |
| 2 | [Revisión de la documentación de SAP y {{site.data.keyword.cloud_notm}} relevante](/docs/infrastructure/sap-hana/hana-review-doc.html) |
| 3 | [Determinación de sus aplicaciones SAP](/docs/infrastructure/sap-hana/hana-determine-apps.html) |
| 4 | [Dimensionamiento del servidor](/docs/infrastructure/sap-hana/hana-size-server.html) |
| 5 | [Determinación de la configuración](/docs/infrastructure/sap-hana/hana-determine-configuration.html) |

## Siguientes pasos

Seleccione el paso correspondiente en la Tabla 1 para empezar a planificar su entorno SAP.
