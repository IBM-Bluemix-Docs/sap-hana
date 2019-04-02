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


# Soporte de alta disponibilidad de IBM Cloud
{: #ha}

La infraestructura como servicio (IaaS) de {{site.data.keyword.cloud}} le ofrece un entorno de cálculo sólido con un despliegue de sistema operativo (SO) opcional que admite soluciones de alta disponibilidad (HA). La solución se basa en la versión del SO admitida, que se describe en
[Nota SAP 2414097 ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://launchpad.support.sap.com/#/notes/2414097){: new_window}. La solución de alta disponibilidad está restringida a las licencias de SO solicitadas que se suministran con el despliegue, o licencias de terceros, como BYOL (traiga su propia licencia). Asegúrese de debatir los detalles de la alta disponibilidad con el soporte de {{site.data.keyword.cloud_notm}} antes del despliegue.

Los sistemas operativos admitidos y desplegados por {{site.data.keyword.cloud_notm}} para SAP son
* Linux [Red Hat Enterprise Linux (RHEL) o SUSE Enterprise Linux Server (SLES)] admite las dos soluciones de alta disponibilidad, SAP NetWeaver y SAP HANA. Existen restricciones menores en el entorno de
{{site.data.keyword.cloud_notm}}, que se describen en [Visión general de las configuraciones de alta disponibilidad de SAP NetWeaver](#overview-configs).
* Microsoft Windows solo tiene soporte para la solución de alta disponibilidad SAP NetWeaver (debido a las restricciones de base de datos de SAP
HANA).

## Visión general de las configuraciones de alta disponibilidad de SAP NetWeaver
{: #overview-configs}

Hay un gran número de documentos que proporcionan ayuda detallada sobre la planificación e instalación de un entorno de alta disponibilidad para servicios SAP. Los documentos incluyen información sobre migración tras error, réplica, reducción de escala y recuperación tras desastre (DR). Se proporcionan referencias a determinados documentos donde corresponda.

Todos los sistemas operativos y distribuciones que admite
{{site.data.keyword.cloud_notm}} para un despliegue SAP (Windows, Linux RHEL y SLES) se proporcionan con software de alta disponibilidad y extensiones específicas. A continuación se muestran los SO y distribuciones con soporte.

* [Nuevas mejoras en clústeres de migración tras error en Windows Server 2012 y beneficios para SAP NetWeaver High Availability ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://blogs.sap.com/2013/10/16/new-failover-clustering-improvements-in-windows-server-2012-and-its-benefits-for-sap-netweaver-high-availability/){: new_window} proporciona una descripción sobre Microsoft Windows Server Failover Clustering (WFSC) en el SO Windows con SAP NetWeaver.

* A continuación se indican dos referencias como guía para desplegar SAP NetWeaver en un entorno de alta disponibilidad basado en Linux con Linux Pacemaker:
  * Guía de configuración de SUSE SAP NetWeaver High Availability Cluster 7.40
  * Despliegue de servidores de alta disponibilidad basados en SAP NetWeaver utilizando el complemento Red Hat Enterprise Linux HA con Pacemaker

* [Creación de la alta disponibilidad para SAP NetWeaver y SAP HANA en Linux ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://support.sap.com/content/dam/SAAP/SAP_Activate/AGS_70.pdf){: new_window} es un documento de métodos recomendados de SAP y proporciona una descripción técnica en profundidad que se centra especialmente en SAP HANA.

* [Alta disponibilidad y continuidad de negocio de SAP NetWeaver en entornos virtuales con VMware e Hyper-V en Microsoft Windows ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.sap.com/documents/2015/07/508b62bc-5b7c-0010-82c7-eda71af511fa.html){: new_window} abarca los aspectos de virtualización si tiene pensado implementar la alta disponibilidad en servidores virtualizados.

Para ver más productos de alta disponibilidad certificados por socios de SAP para escenarios de alta disponibilidad, consulte
[Información de socios de alta disponibilidad ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://wiki.scn.sap.com/wiki/display/SI/High+Availability+Partner+Information){: new_window}.
Para ver las bases de datos que no sean de HANA SAP, más información sobre la migración tras error de alta disponibilidad y configuraciones de recuperación tras desastre, consulte la documentación de su base de datos.

Tenga en cuenta que el acceso compartido a almacenamiento Network File System (NFS)/Common Internet File System (CIFS), o el acceso compartido a LUNS (almacenamiento de número exclusivo lógico) basado en iSCSI, es necesario habitualmente para dar soporte a la migración tras error del sistema. El almacenamiento local, combinado con un método de réplica, es necesario normalmente para dar soporte a una configuración de recuperación tras desastre. Al igual que con las instalaciones locales, consulte los requisitos de rendimiento y latencia del producto de base de datos al planificar el despliegue.

## Directrices adicionales
{: #extra-guide}

[Almacenamiento basado en quórum](#quorum) y [Consideraciones de red](#network) le proporcionan directrices que necesita tener en cuenta durante el despliegue. Además de las consideraciones descritas en estas secciones, la instalación de SAP NetWeaver y de su sistema de base de datos en un entorno de alta disponibilidad no difiere de otras instalaciones locales.

### Almacenamiento basado en quórum
{: #quorum}

Debido a las restricciones de seguridad del entorno de {{site.data.keyword.cloud_notm}}, el acceso basado en red a los dispositivos de gestión remota a través de Intelligent Platform Management Interface (IPMI) no está disponible. Los entornos en clúster normalmente utilizan componentes basados en IPMI para “delimitar los nodos de clúster” para garantizar siempre un quórum. En ausencia de un dispositivo habilitado por IPMI, se utilizan dispositivos de almacenamiento compartido. En un entorno de {{site.data.keyword.cloud_notm}}, los dispositivos de almacenamiento compartido se implementan desplegando un LUN iSCSI en los servidores como dispositivo de quórum. Por ejemplo, un File Share Witness (FSW) en un clúster de Microsoft y SDB (Storage-based Death) para Stonith de Linux Pacemaker.
* Pulse [aquí ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](http://linux-ha.org/wiki/Cluster_Concepts){: new_window} para obtener más información sobre los conceptos del clúster de alta disponibilidad de Linux.
* Pulse [aquí
![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://docs.microsoft.com/en-us/windows-server/failover-clustering/manage-cluster-quorum){: new_window} para obtener más información sobre la configuración y la gestión de servidores de quórum para Windows Server 2012 y Windows Server 2012 R2.

{{site.data.keyword.cloud_notm}} Storage tiene funciones de alta disponibilidad incorporadas, por lo que un único LUN iSCSI compartido no presentará un punto único de anomalía (SPOF) debido a que el diseño de la red es redundante. No obstante, es posible que los aspectos específicos del producto de clúster requieran varios dispositivos de quórum.

### Consideraciones de red
{: #network}

Una instalación basada en {{site.data.keyword.cloud_notm}} se suministra con una de las configuraciones de red siguientes:
* Red privada
* Red pública
* Redes pública y privada
* Dos redes privadas (bajo solicitud especial)

Al igual que en las instalaciones locales, se pueden solicitar adaptadores de red adicionales en función de las restricciones físicas del hardware. La restricción es la misma que en las instalaciones locales. La solicitud de adaptadores de red redundantes durante los despliegues de hardware ayuda a evitar un SPOF (punto único de anomalía) en la topología de la red. Se configuran adaptadores redundantes en una configuración de migración tras error con LACP (Link Aggregation Control Protocol). Para Linux, la configuración utiliza interfaces de acoplamiento y se utilizan adaptadores de asociación para Microsoft Windows. La infraestructura de conmutación de
{{site.data.keyword.cloud_notm}} a la que se conectan estos adaptadores es redundante, por lo que no se introducen nuevos SPOF. Las VLAN solicitadas pueden utilizar la infraestructura redundante.

En función de los requisitos de la red, como los casos de réplica en una configuración de recuperación tras desastre, debe comprobar la ubicación de los dispositivos conectados y los posibles nuevos requisitos de red específicos del producto en cuestión. En algunos casos, la réplica basada en almacenamiento de instantáneas de {{site.data.keyword.cloud_notm}} podría ajustarse a sus requisitos. Consulte con el soporte de
{{site.data.keyword.cloud_notm}} para determinar qué solución funciona mejor para sus necesidades de proceso de negocio.
