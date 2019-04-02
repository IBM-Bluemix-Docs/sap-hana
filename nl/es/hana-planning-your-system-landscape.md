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

# Planificación del entorno de sistemas
{: #planning-your-system-landscape}

Un *entorno* SAP es un grupo de dos o más *sistemas* SAP, que normalmente incluyen desarrollo, calidad y pruebas y producción. Un sistema SAP consta de una o más *instancias de SAP*, que son un grupo de procesos que se inician y detienen al mismo tiempo. Para obtener más información sobre los entornos SAP, consulte [*SAP Business Suite sobre la arquitectura de referencia de IBM X6 Systems* ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://lenovopress.com/redp5073.pdf){: new_window}.
{: shortdesc}

Existen varias posibles configuraciones de entorno, como servidor (tamaño)/almacenamiento (tamaño), para todas las soluciones SAP del mercado. Estas soluciones incluyen productos basados en SAP NetWeaver, como
[SAP Business Suite ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://open.sap.com/courses/suitehana1){: new_window}, SAP Business Warehouse, y todos los complementos de SAP específicos, que admiten los servidores de infraestructura certificados por SAP de
{{site.data.keyword.cloud}}. Otra solución a tener en cuenta es cualquier software de terceros que pueda integrarse con SAP.

SAP HANA se puede ejecutar como una base de datos para una solución basada en la pila de SAP NetWeaver o como una entidad autónoma dependiendo del caso de uso. En ambos casos, la oferta {{site.data.keyword.cloud_notm}} proporciona servidores preconfigurados con el certificado de SAP NetWeaver alrededor de los cuales se puede crear el entorno desde cualquier otro servidor.

Intente ser lo más detallado posible al determinar el tamaño de su servidor sobre la base de las aplicaciones que tiene previsto ejecutar, el crecimiento potencial y el rendimiento. Además, tenga en cuenta los requisitos de memoria y almacenamiento para sus aplicaciones. Los sistemas SAP en un entorno tienen requisitos específicos para la conectividad, ya sea entre ellos o bien con sistemas externos. Para obtener más información, consulte [Aspectos a considerar cuando planifique su entorno SAP](/docs/infrastructure/sap-hana?topic=sap-hana-considerations#considerations).

La Tabla 1 contiene los pasos del proceso de planificación. Aplíquela para crear su entorno SAP de destino.

Tabla 1. Visión general del proceso de planificación

| Paso | Detalles |
| --- | --- |
| 1 | [Obtención de credenciales de SAP y {{site.data.keyword.cloud_notm}} y creación de cuentas](/docs/infrastructure/sap-hana?topic=sap-hana-get_sap_ibm_credentials#get_sap_ibm_credentials) |
| 2 | [Revisión de la documentación de SAP y {{site.data.keyword.cloud_notm}} relevante](/docs/infrastructure/sap-hana?topic=sap-hana-review_doc#review_doc) |
| 3 | [Determinación de sus aplicaciones SAP](/docs/infrastructure/sap-hana?topic=sap-hana-3-determining-your-sap-applications#3-determining-your-sap-applications) |
| 4 | [Dimensionamiento del servidor](/docs/infrastructure/sap-hana?topic=sap-hana-size_the_server#size_the_server) |
| 5 | [Determinación de la configuración](/docs/infrastructure/sap-hana?topic=sap-hana-determine_configuration#determine_configuration) |

## Siguientes pasos

Seleccione el paso correspondiente en la Tabla 1 para empezar a planificar su entorno SAP.
