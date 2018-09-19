---



copyright:
  years: 2017, 2018
lastupdated: "2018-06-07"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Aspectos a considerar cuando planifique su entorno SAP
{: #considerations}

Los sistemas SAP en un entorno tienen requisitos específicos para la conectividad, ya sea entre ellos o bien con sistemas externos. También debe tener en cuenta el almacenamiento externo para su entorno, y qué hacer si decide desplegar VMware en el servidor.

## Conectividad de red
{: #network_connectivity}

[Red {{site.data.keyword.cloud_notm}}](/docs/infrastructure/sap-hana/hana-about.html#ibm_cloud_network) proporciona una visión general del enfoque de {{site.data.keyword.cloud}} a la conectividad de red. Los problemas relacionados con la conectividad de red pueden provocar retrasos importantes en su proyecto si no los planifica correctamente, independientemente de cómo tenga previsto utilizar el sistema. 

En general, tiene dos opciones de interfaz para los servidores de {{site.data.keyword.cloud_notm}} suministrados por IaaS, la primera es una interfaz externa con una IP pública. La segunda es una interfaz interna suministrada con una “IP privada” de conformidad con Request for Comment (RFC) 1918. También puede elegir una única interfaz interna con una “IP privada”. La IP externa puede ser más fácil de utilizar, pero existe un riesgo potencial, aunque se instale y configure previamente un cortafuegos básico.

La segunda opción accede a la red privada virtual (VPN) de {{site.data.keyword.cloud_notm}} a través del portal de clientes de infraestructura de {{site.data.keyword.cloud_notm}}, o despliega un dispositivo de seguridad en su entorno. Los dispositivos de seguridad se ofrecen para cortafuegos, la conversión de la dirección de red, el acceso VPN y otras funciones de red. Se recomienda que el departamento de redes hable con [{{site.data.keyword.cloud_notm}} Soporte](https://console.bluemix.net/docs/get-support/howtogetsupport.html#getting-customer-support) después de determinar el diseño del entorno y la conectividad necesarios en la capa de aplicación SAP.

### Redes VLAN
{: #vlans}

Si desea separar distintos tipos de tráfico de red en su entorno, puede solicitar más LAN virtual (VLAN). Tenga en cuenta que las VLAN adicionales sólo generan segregación de tráfico, no mayor rendimiento. SAP suele recomendar que se utilicen redes de 10 Gb para el tráfico entre sus servidores de aplicaciones y las bases de datos SAP HANA, y para otros clientes SAP HANA, como SAP Business Intelligence. Si desea separar el acceso administrativo a su servidor SAP HANA de otros clientes, debe solicitar otra VLAN para su entorno. Otra opción consiste en separar el tráfico mediante red pública y privada, ya que {{site.data.keyword.cloud_notm}} no da soporte a otros enlaces ascendentes "físicos". Siga las recomendaciones de SAP en cuanto a la [Integración de un centro de datos adaptado (TDI) de SAP HANA](https://blogs.saphana.com/2015/02/18/sap-hana-tailored-data-center-integration-tdi-overview/).

El acceso a través de VPN, así como el acceso desde jumpbox, permite un acceso transparente a las instancias de SAP HANA desde SAP HANA Studio.

## Almacenamiento externo
{: #external_storage}

Además del almacenamiento local, podría requerir más almacenamiento externo para realizar copias de seguridad. Para estos requisitos, puede solicitar almacenamiento en bloque o almacenamiento adjunto en red (NAS), como se describe en [Almacenamiento](/docs/infrastructure/sap-hana/hana-general-iaas-concepts.html#storage). Como los datos adicionales de NFS (Network File System) y almacenamiento en bloque se transfieren a través de los mismos adaptadores físicos que todo el tráfico de red, deberá tener en cuenta su posible impacto. 

Para el almacenamiento externo, es importante para calcular los requisitos del proyecto antes de tomas una decisión sobre una solución de almacenamiento. Si tiene que restaurar un sistema SAP HANA, el IOPS del almacenamiento afecta significativamente a la ventana de restauración. Las ventanas de copia de seguridad no resultan tan críticas con SAP HANA, ya que todas las copias de seguridad son en línea, independientemente de la configuración de SAP HANA.

Por ejemplo, con {{site.data.keyword.cloud_notm}} {{site.data.keyword.blockstorageshort}} puede calcular una restauración aproximada de 12 TB de SAP HANA a velocidad máxima. Debe crear tres dispositivos de almacenamiento físico (LUN iSCSI de almacenamiento en bloques) porque el tamaño máximo por dispositivo es de 4 TB. Puede crear una sección sobre estos tres dispositivos con Linux Logical Volume Manager y crear un dispositivo lógico de 12 TB. 

Los 12 TB le permiten 3x10 IOPS/GB, lo que suma un total de 122.880 IOPS/GB a 16 KB. Esto le ofrece un tiempo de restauración de 1,875 GB por segundo o un tiempo de restauración total por debajo de las 2 horas. Puesto que la medida de IOPS se toma a una distribución de lectura y escritura de 50/50, puede considerar estos números como un límite inferior del rendimiento de la restauración. Se recomienda realizar pruebas de copia de seguridad y restauración si depende de una determinada ventana de restauración.

Tanto {{site.data.keyword.cloud_notm}} {{site.data.keyword.blockstorageshort}} como {{site.data.keyword.filestorage_full_notm}} o NAS pueden actuar como espacio de copia de seguridad o como almacenamiento para componentes de software adicionales instalados en el servidor. Sin embargo, {{site.data.keyword.cloud_notm}} Storage y NSA no se pueden utilizar como almacenamiento para SAP HANA porque estas opciones no cumplen con los criterios de KPI.

Para obtener más información, consulte [Iniciación a {{site.data.keyword.blockstorageshort}}](https://console.bluemix.net/docs/infrastructure/BlockStorage/index.html#getting-started-with-block-storage) e [Iniciación a {{site.data.keyword.filestorage_full_notm}}](https://console.bluemix.net/docs/infrastructure/FileStorage/index.html#getting-started-with-file-storage).

## Escenarios de alta disponibilidad de recuperación en caso de error
{: #ha_dr}

El entorno {{site.data.keyword.cloud_notm}} no admite ningún escenario de alta disponibilidad (HA) preconfigurado. Sin embargo, le permite implementar soluciones de HA para SAP HANA mediante extensiones de HA de Red Hat Enterprise Linux, con un caso local.

La réplica del sistema SAP HANA se puede configurar con un sistema de migración tras error automatizado de un servidor a una réplica. Siga las instrucciones de la documentación de SAP sobre réplica del sistema para determinar la modalidad de réplica que mejor se ajusta a su escenario de aplicación y a su nivel de resiliencia a desastres. En función de la modalidad de réplica, se pueden cumplir distintos KPI de red. Consulte las recomendaciones de SAP sobre rendimiento y latencia de la red para determinar el rendimiento necesario y la latencia máxima para la modalidad de operación que elija. La topología de red de {{site.data.keyword.cloud_notm}} debería poder satisfacer todas las configuraciones necesarias. Póngase en contacto con el equipo de soporte de {{site.data.keyword.cloud_notm}} para determinar la configuración óptima para su escenario si no está seguro o si desea que su sitio de recuperación en caso de error esté en un centro de datos distinto para conseguir la máxima resiliencia a desastres.

Tenga en cuenta que los entornos SAP HANA Scale-Out (de varios nodos) todavía están en fase de evaluación. Es decir, un nodo autónomo para SAP HANA no es una opción actual en un entorno de {{site.data.keyword.cloud_notm}}.

Para obtener más información sobre la alta disponibilidad y la recuperación tras desastre, consulte [Alta disponibilidad](https://console.bluemix.net/docs/infrastructure/sap-reference-architecture/sap-ra-recommendations.html#availability) y [Recuperación tras desastre](https://console.bluemix.net/docs/infrastructure/sap-reference-architecture/sap-ra-recommendations.html#dr).

Para obtener más información sobre la réplica del sistema y el rendimiento y la latencia de red, consulte
  * [Cómo realizar una réplica del sistema para SAP HANA](https://www.sap.com/documents/2013/10/26c02b58-5a7c-0010-82c7-eda71af511fa.html)
  * [Red necesaria para una réplica del sistema SAP HANA](https://www.sap.com/documents/2014/06/babb2b55-5a7c-0010-82c7-eda71af511fa.html)

Para obtener más información sobre cómo configurar las extensiones de clúster HA para el sistema operativo Linux, consulte
  * [Réplica automatizada del sistema SAP HANA con Pacemaker en la Guía de configuración de RHEL](https://access.redhat.com/articles/1466063)
  * [Escenario optimizado de rendimiento de SAP HANA SR](https://www.suse.com/docrep/documents/ir8w88iwu7/suse_linux_enterprise_server_for_sap_applications_12_sp1.pdf)

## Despliegues de servidor VMware ESXi
{: #vmware_server}

Todos los servidores de la oferta {{site.data.keyword.cloud_notm}} SAP HANA tienen certificación para VMware ESX, lo que hace que SAP HANA se pueda desplegar en máquinas virtuales (VM). Si se adquiere un servidor con VMware ESX, se despliega con una instancia de ESX básica preinstalada; no se despliega ninguna VM. Tenga en cuenta que es el responsable de desplegar el sistema operativo invitado correcto en un despliegue basado en ESX. Siga las instrucciones definidas en la Nota de SAP 2414820 para elegir una versión de sistema operativo que reciba soporte con SAP HANA en {{site.data.keyword.cloud_notm}}.

El proceso de dimensionamiento para un despliegue basado en ESX difiere del de un despliegue de servidor nativo. Siga las recomendaciones del manual *Architecture Guidelines and Best Practices for Deployments of SAP HANA on VMware vSphere Architecture and Technical Considerations Guide*. Hay que calcular la sobrecarga de los requisitos de la capa de virtualización siguiendo las reglas del manual *Architecture...and Considerations Guide*. Después de desplegar el sistema operativo invitado en una máquina virtual, asegúrese de que se cumplan los KPI de TDI de SAP HANA. Consulte la Nota de SAP 1943937 para ver detalles sobre cómo comprobar que el entorno cumple con los requisitos previos del soporte de SAP. Se deben cumplir los requisitos previos en cada máquina virtual desplegada en un servidor específico.

Hay que seguir otras reglas definidas por SAP para desplegar SAP HANA en un entorno virtualizado. Para entornos de producción, siga las restricciones que se describen en la Nota de SAP 1995460. En la Nota de SAP 2024433 se describen las reglas para varias máquinas virtuales en un servidor.

Para obtener más información, consulte la documentación siguiente:
  * [Nota de SAP 2414820](https://launchpad.support.sap.com/#/notes/2414820)
  * [*Architecture Guidelines and Best Practices for Deployments of SAP HANA on VMware vSphere Architecture and Technical Considerations Guide*](https://www.vmware.com/content/dam/digitalmarketing/vmware/en/pdf/whitepaper/sap_hana_on_vmware_vsphere_best_practices_guide-white-paper.pdf)
  * [Nota de SAP 1943937](https://launchpad.support.sap.com/#/notes/1943937)
  * [Preguntas más frecuentes sobre la integración de un centro de datos adaptado de SAP HANA](https://www.sap.com/documents/2016/05/e8705aae-717c-0010-82c7-eda71af511fa.html)
  * [Nota de SAP 1995460](https://launchpad.support.sap.com/#/notes/1995460)
  * [Nota de SAP 2024433](https://launchpad.support.sap.com/#/notes/2024433)
  * [Visión general sobre la integración de un centro de datos adaptado (TDI) de SAP HANA](https://blogs.saphana.com/2015/02/18/sap-hana-tailored-data-center-integration-tdi-overview/)
