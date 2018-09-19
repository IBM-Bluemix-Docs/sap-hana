---



copyright:
  years: 2017, 2018
lastupdated: "2018-06-28"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Visión general de SAP HANA on IBM Cloud IaaS
{: #iaas-overview}

Un entorno de infraestructura como servicio (IaaS) consta de muchos componentes: centro de datos, cálculo, conectividad, almacenamiento y red. 

## Centros de datos

Con centros de datos en Norteamérica y Sudamérica, Europa, Asia y Australia, puede suministrar recursos de nube donde (y cuando) los necesite. Cada centro de datos está conectado a la red privada global de {{site.data.keyword.cloud_notm}}, realizando transferencias de datos de forma más rápida y eficiente en todo el mundo.

Para obtener más información, consulte [Centros de datos](https://www.ibm.com/cloud-computing/bluemix/data-centers){: new_window}.

## Servidores nativos

{{site.data.keyword.baremetal_long}} son servidores físicos con funcionalidades de personalización limitadas. Los servidores están dedicados a su uso, o de su cliente, y no se comparten, ni los recursos de servidor, con otros clientes de {{site.data.keyword.cloud_notm}}, y se suministran como servidores físicos completos en los que se ejecuta el sistema operativo (SO) que elija. Los sistemas operativos que corresponden a la oferta de SAP HANA son Red Hat Enterprise Linux 7.4 for SAP HANA, SUSE Linux Enterprise Server 12 SP2 for SAP HANA y VMware Server Virtualization 6.5.

Como la personalización está limitada en los servidores nativos, se pueden obtener tiempos de suministro de 1 a 4 horas más rápidos. El suministro rápido es útil si intenta lanzar al mercado una app antes que la competencia.

Se le ofrece una matriz de combinaciones de RAM y CPU, ya que los servidores certificados por SAP tienen una cantidad de RAM y un número de CPU preconfigurados. La combinación *no se puede* cambiar durante el proceso de pedido o mediante una incidencia de soporte después de desplegar los servidores.

Para obtener más información, consulte [Acerca de los servidores nativos](https://console.bluemix.net/docs/bare-metal/about.html#about-bare-metal-servers). 

## Conectividad de red

Se otorga automáticamente conectividad de red privada virtual (VPN) a la red en la nube virtual de {{site.data.keyword.cloud_notm}} cuando se configura su cuenta de {{site.data.keyword.cloud_notm}}. De forma predeterminada, el servidor tiene una dirección IP pública y privada. Si quiere que el servidor sea privado, puede desactivar la interfaz pública después de suministrar el servidor o solicitar el servidor como privado. 

Si bien los requisitos de red de SAP HANA (red redundante de 10 Gb) se cumplen con la oferta {{site.data.keyword.cloud_notm}}, es posible que tenga que cumplir con ciertos indicadores de rendimiento claves (KPI) de latencia y de rendimiento, en función del caso de uso. Para obtener más información sobre cómo determinar en qué centro de datos debe ubicar el servidor SAP HANA y para decidir la mejor solución de conectividad de red, consulte las consideraciones sobre [Conectividad de red](/docs/infrastructure/sap-hana/hana-considerations.html#network_connectivity).

Para obtener más información, consulte [Iniciación a la red privada virtual (VPN)](https://console.bluemix.net/docs/infrastructure/iaas-vpn/getting-started.html#getting-started-with-virtual-private-networking-vpn-) y el documento sobre [*Requisitos de red de SAP HANA*](https://www.sap.com/documents/2016/08/1cd2c2fb-807c-0010-82c7-eda71af511fa.html).

## Almacenamiento
{: #storage}

Se suministra almacenamiento local con el {{site.data.keyword.baremetal_short}} y utiliza la LAN virtual (VLAN) de red privada de {{site.data.keyword.cloud_notm}} para proporcionar seguridad empresarial sin obstruir el acceso de administrador. Para los servidores con certificado de SAP HANA, está diseñado y configurado para cumplir con los KPI definidos por SAP en cuanto a rendimiento y a latencia, a fin de cumplir con los criterios de certificación de SAP HANA. El almacenamiento local tiene el tamaño relevante de los distintos sistemas de diferentes definidos en la Guía de instalación de SAP HANA (`data.log` y `compartido`). No es necesario que el cliente realice ninguna otra adaptación.

Existen dos tipos de almacenamiento para {{site.data.keyword.cloud_notm}}, en bloque y archivo, a elegir para realizar copias de seguridad y restauraciones para SAP HANA. Ambos tipos utilizan operaciones de entrada/salida por segundo (IOPS), que se utilizan para determinar las necesidades de almacenamiento. Los IOPS se calculan sobre la base de un tamaño de bloque de 16 KB con una combinación de lectura/escritura 50/50. Para alcanzar los máximos IOPS en un volumen, se requieren los recursos de red adecuados. Otras consideraciones incluyen el uso de la red privada fuera del almacenamiento y host, y los ajustes específicos de la aplicación (por ejemplo, pilas de IP y profundidades de cola). Para obtener más información, consulte [Iniciación a Block Storage](https://console.bluemix.net/docs/infrastructure/BlockStorage/index.html#getting-started-with-block-storage) e [Iniciación a File Storage](https://console.bluemix.net/docs/infrastructure/FileStorage/index.html#getting-started-with-file-storage).

{{site.data.keyword.cloud_notm}} también ofrece almacenamiento adjunto en red (NAS), si busca una solución de copia de seguridad rápida, rentable y eficiente para sus dispositivos. NAS se puede montar mediante el sistema de archivos de red (NFS) y se puede utilizar con el protocolo de transferencia de archivos (FTP) tanto con Parallels Plesk Panel como con cPanel@WHM.

El almacenamiento NAS se puede utilizar para cualquier fin, pero, en este caso, *no* se utilizará para datos SAP HANA ni para archivos de registro. El almacenamiento no cumple los criterios en cuanto a KPI de E/S. Sin embargo, el almacenamiento se puede utilizar para dispositivos de copia seguridad y para todos los demás tipos de datos. SAP HANA lo puede utilizar como dispositivos de copia de seguridad, para datos y archivos de registro, si se monta mediante NFS.  
  
El almacenamiento de NAS y FTP se factura mensualmente y está disponible en distintos tamaños de almacenamiento. Puede interactuar con el almacenamiento de NAS y FTP en la línea de mandatos o el terminal con el sistema operativo, o bien a través de interacciones de apuntar y pulsar en los paneles del portal de clientes de infraestructura de {{site.data.keyword.cloud_notm}}. En el portal de clientes, se pueden utilizar los detalles y uso de NAS, pero el servicio no se puede manipular fuera de la línea de mandatos, del kernel o del panel de control.

Para obtener más información sobre NAS en un entorno {{site.data.keyword.cloud_notm}}, consulte [Iniciación a NAS](https://console.bluemix.net/docs/infrastructure/network-attached-storage/index.html#getting-started-with-nas).

## Despliegue y gestión

Los {{site.data.keyword.baremetal_short}} {{site.data.keyword.cloud_notm}} se despliegan a través del portal de clientes de infraestructura de {{site.data.keyword.cloud_notm}} o la API, después de crear su cuenta de cliente de {{site.data.keyword.cloud_notm}}. Los servidores se pueden gestionar a través del portal de clientes, API o interfaz de línea de mandatos (CLI). Para obtener más información, consulte [Acerca de los servidores nativos](https://console.bluemix.net/docs/bare-metal/about.html#about-bare-metal-servers).

## Soporte

El [Soporte a clientes de {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/support/index.html#getting-customer-support) trata cualquier pregunta y problemas que puedan surgir, a través de distintos canales, como chat, teléfono o incidencias. El soporte al cliente es gratuito para todos los clientes de {{site.data.keyword.cloud_notm}} y cubre la mayoría de las incidencias que se presentan a diario. Para obtener más información, consulte [Obtención de soporte al cliente](https://console.bluemix.net./docs/support/index.html#getting-customer-support).

A través del soporte de SAP también puede seguir creando incidencias relacionadas con los productos {{site.data.keyword.cloud_notm}} IaaS y SAP. Para obtener más información, consulte [Soporte de SAP](https://support.sap.com/en/index.html) y [Nota de SAP 2414820](https://launchpad.support.sap.com/#/notes/2414820).

## Instalación de SAP HANA

Debe instalar el software de SAP HANA un instalador de SAP HANA certificado que haya realizado el curso de certificación para la instalación de SAP HANA. Para obtener más información, consulte [¿Quién puede instalar SAP HANA?](http://www.saphanacentral.com/p/who-can-install-sap-hana.html).
