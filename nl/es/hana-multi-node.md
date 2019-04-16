---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-26"

keywords: SAP HANA, {{site.data.keyword.cloud_notm}}, SAP ABAP, LACP, KPIs,VLANs

subcollection: sap-hana

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}

# 5. Configuración de la infraestructura de IBM Cloud para dar soporte al sistema SAP HANA de varios nodos
{: #multi-node-storage}

{{site.data.keyword.cloud}} da soporte al almacenamiento SAP HANA de varios nodos para cargas de trabajo de procesamiento analítico en línea (OLAP), como SAP Business Warehouse (SAP BW) y SAP BW/4HANA. La solución {{site.data.keyword.cloud_notm}} para el sistema SAP HANA de varios nodos consta de hasta 15+1 nodos (15 nodos de trabajador más uno en espera) para un máximo de 30 TB de memoria utilizada para un sistema.

Con este sistema de varios nodos, se crea un solo sistema SAP HANA con varios nodos de SAP HANA. Los datos se distribuyen entre estos nodos, que forman una sola base de datos. La configuración de varios nodos admite escalabilidad y alta disponibilidad en la configuración en espera. La oferta de {{site.data.keyword.cloud_notm}} para esta configuración concuerda con la [Integración de un centro de datos adaptado (TDI) de SAP HANA ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://blogs.saphana.com/2015/02/18/sap-hana-tailored-data-center-integration-tdi-overview/){: new_window}, y utiliza servidores certificados SAP HANA de {{site.data.keyword.cloud_notm}} para el almacenamiento empresarial centralizado y compartido.

Debe seguir las directrices de configuración detalladas en [Realización del pedido del sistema de varios nodos](#ordering) para cumplir los requisitos de TDI de SAP HANA y recibir soporte de SAP.
{: note}

Siga las directrices de [Dimensionamiento de SAP HANA ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://help.sap.com/viewer/eb3777d5495d46c5b2fa773206bbfb46/2.0.00/en-US/d4a122a7bb57101493e3f5ca08e6b039.html){: new_window} para determinar el tamaño necesario del sistema SAP HANA de destino, incluida la cantidad total de memoria y almacenamiento necesarios para el despliegue. Los requisitos de dimensionamiento permiten establecer el número de nodos SAP HANA necesarios para el sistema SAP HANA de varios nodos y el almacenamiento necesario para alojar los datos.

## Revisión de la topología de red y el diseño de almacenamiento
{: #reviewing-topology}

La figura 1 muestra la topología de red necesaria para la configuración de TDI de SAP HANA de la Infraestructura como servicio de {{site.data.keyword.cloud_notm}}.

Figura 1. Topología de red de TDI de SAP HANA de Infraestructura como servicio de IBM Cloud

![Figura 1. Topología de red de TDI de SAP HANA de Infraestructura como servicio de IBM Cloud](/images/SAP-BW.png "Topología de red de TDI de SAP HANA de Infraestructura como servicio de IBM Cloud")

## Configuración de los requisitos previos
{: #prerequisites}

Para que funcione el sistema SAP HANA de varios nodos, es necesario contar con unas redes determinadas. Antes de solicitar otros componentes para el sistema, estas redes deben estar correctamente configuradas, junto con los nodos de base de datos. Son necesarias
* Una red del lado del cliente, que conecte los servidores de aplicaciones de SAP ABAP (SAP Advanced Business Application Programming), los clientes de SAP HANA Studio y cualquier otro cliente de red con el sistema de varios nodos. Las opciones de disponibilidad y rendimiento de la red dependen del escenario de uso del sistema de varios nodos SAP HANA. Tenga en cuenta la cantidad de datos transferidos a y desde la base de datos SAP HANA y los indicadores clave de rendimiento (KPI) de disponibilidad necesarios para la aplicación.
* Una red de almacenamiento, que es necesaria para conectarse a {{site.data.keyword.filestorage_full_notm}} y {{site.data.keyword.blockstoragefull}} de fondo. Para maximizar el rendimiento y la redundancia, es necesaria una red de 10 Gb con dos interfaces en acoplamiento Linux con LACP (Link Aggregation Control Protocol). Sin las cifras de rendimiento indicadas de las directrices de dimensionamiento de SAP HANA, no se pueden cumplir los KPI de TDI de SAP HANA.
* Una red internodal para comunicación interna de SAP HANA que se configure de forma equivalente a la red de almacenamiento. La red internodal solo se utiliza para la comunicación entre nodos y la transferencia de datos que puede ser necesaria entre los nodos durante las operaciones. Esta configuración de red necesaria se realiza en dos adaptadores físicos de 10 Gb en acoplamiento Linux con LACP.

## Realización del pedido del sistema de varios nodos
{: #ordering}

Para cumplir los indicadores de rendimiento que necesita SAP, las VLAN, el almacenamiento y los nodos de cálculo se deben pedir en el mismo centro de datos. Si se distribuyen los componentes en varios centros de datos, SAP no admitirá el sistema de varios nodos.

1. Solicite tres VLAN y servidores diferentes con cuatro adaptadores (dos privados y dos públicos). Para obtener más información sobre los pedidos de VLAN, consulte [Paso 1 Realización del pedido de VLAN primarias y públicas](/docs/infrastructure/virtualization?topic=Virtualization-advanced-single-site-vmware-reference-architecture#step-1-ordering-primary-public-and-private-vlans). Para obtener más información sobre el pedido de los servidores, consulte [Configuración de la infraestructura](/docs/infrastructure/sap-hana?topic=sap-hana-set_up_infrastructure#set_up_infrastructure#set_up_infrastructure).
2. Configure la VLAN privada inicial como "VLAN de almacenamiento".
3. [Abra una incidencia](/docs/get-support?topic=get-support-open-case#open-case) con el Soporte de {{site.data.keyword.cloud_notm}} para (a) mover las interfaces públicas a la segunda VLAN, y (b) solicitar que se asignen dos adaptadores más a la tercera VLAN, que es la VLAN de cliente.

Ahora dispone del número de servidores correspondientes al dimensionamiento, y la red está configurada, de forma que
* El almacenamiento se puede conectar a todos los nodos
* La instalación SAP HANA de varios nodos se puede realizar una vez conectado el almacenamiento

El despliegue de {{site.data.keyword.cloud_notm}} configura las conexiones internodales y las conexiones de LAN de almacenamiento. Solicite las conexiones con dos adaptadores de 10 Gb con configuración de migración tras error en cada uno. De esta forma, la configuración de LACP y acoplamiento Linux será la correcta. Póngase en contacto con el equipo de soporte de {{site.data.keyword.cloud_notm}} si tiene alguna pregunta.

Existen criterios de rendimiento específicos que deben cumplir los volúmenes Network File System (NFS) conectados (consulte [Iniciación a {{site.data.keyword.filestorage_short}}](/docs/infrastructure/FileStorage?topic=FileStorage-GettingStarted#getting-started-with-ibm-file-storage-for-bluemix) para obtener más información). Para los volúmenes de `/data/`, es necesario un almacenamiento resistente de 2 TB con un KPI de rendimiento de 10 IOPS/GB para cada nodo de trabajador. Es necesario un volumen adicional del mismo tamaño como un volumen de `/shared/` de SAP HANA, ya que se compartirá en todos los nodos. Según las pruebas, el volumen de `/shared/` debe ser un volumen de almacenamiento de rendimiento con 12 IOPS/GB.

Para los volúmenes de registro, es necesario un volumen de 512 GB de almacenamiento de rendimiento para cada nodo con un KPI de rendimiento de 10.000 IOPS.

Puede seguir los pasos indicados en [Suministro y gestión de {{site.data.keyword.blockstorageshort}}](/docs/infrastructure/BlockStorage?topic=BlockStorage-getting-started#getting-started) o [Suministro y gestión de {{site.data.keyword.filestorage_full_notm}}](/docs/infrastructure/FileStorage?topic=FileStorage-orderingConsole#orderingConsole) para realizar el pedido de almacenamiento de Resistencia y Rendimiento.

## Configuración de varios nodos de SAP HANA
{: #configuring}

El volumen compartido de SAP HANA, y cada uno de los volúmenes de registro y de datos, debe ser accesible para todos los nodos. De esta forma, todos los volúmenes son accesibles para toda la VLAN de almacenamiento, que se ha configurado en [Realización del pedido del sistema de varios nodos](#ordering). Si no desea enumerar todas las direcciones IP implicadas, facilite el acceso a los volúmenes a toda la subred de IP de VLAN.

Siga las instrucciones de [SAP HANA en sistemas NetApp FAS con NFS ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://www.netapp.com/us/media/tr-4290.pdf){: new_window} para configurar el sistema SAP HANA de varios nodos. Utilice las opciones siguientes de montaje de NFS (Network File System) para montar cada volumen:

`rw,bg,hard,timeo=600,intr,noatime,vers=4,minorversion=1,lock,rsize=1048576,wsize=1048576` en `/etc/fstab`.

Estas opciones se han probado en NetApp e {{site.data.keyword.cloud_notm}}. Póngase en contacto con el equipo de soporte de {{site.data.keyword.cloud_notm}} si tiene pensado cambiar alguno de los valores o las opciones de montaje.

Una vez que haya montado todos los volúmenes en todos los nodos, los servidores de varios nodos estarán configurados y listos para instalar la base de datos SAP HANA de varios nodos. Siga los pasos de la [Guía de instalación y actualización de servidor de SAP HANA ![Icono de enlace externo](../../icons/launch-glyph.svg "Icono de enlace externo")](https://help.sap.com/viewer/2c1988d620e04368aa4103bf26f17727/2.0.03/en-US){: new_window} para instalar una base de datos SAP HANA de la versión que necesite.
