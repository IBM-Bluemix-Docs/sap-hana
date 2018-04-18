---



copyright:
  years: 2018
lastupdated: "2018-02-12"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 1. Realización del pedido de almacenamiento
{: #order_storage}

El pedido de {{site.data.keyword.blockstoragefull}}, {{site.data.keyword.filestorage_full_notm}} y el almacenamiento adjunto en red (NAS) se realiza después de desplegar {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}. 

## Realización del pedido de almacenamiento de {{site.data.keyword.cloud_notm}}
{: #ibm_storage}

Puede seguir los pasos indicados en [Suministro y gestión de {{site.data.keyword.blockstorageshort}}](https://console.bluemix.net/docs/infrastructure/BlockStorage/provisioning-block_storage.html#provisioning-and-managing-block-storage) o [Suministro y gestión de {{site.data.keyword.filestorage_full_notm}}](https://console.bluemix.net/docs/infrastructure/FileStorage/provisioning-file-storage.html#provisioning-and-managing-ibm-file-storage-for-ibm-cloud) para realizar el pedido de su solución de almacenamiento de copia de seguridad y restauración. Se le guiará en el proceso de decidir qué tipo de almacenamiento utilizar, cómo realizar el pedido y cómo desplegarlo en el servidor.

## Realización del pedido de NAS
{: #order-nas}

El almacenamiento NAS (almacenamiento adjunto en red) puede ser otra ampliación valiosa del almacenamiento local de su servidor, si necesita almacenamiento para los archivos de registro archivados de su base de datos o copias de seguridad en línea y fuera de línea frecuentes. Visite [Realización de pedido de almacenamiento NAS/FTP](https://console.bluemix.net/docs/infrastructure/network-attached-storage/index.html#ordering-nas-ftp-storage) para realizar el pedido y configurar NAS. También puede consultar [Montaje de almacenamiento NAS en Linux](https://console.bluemix.net/docs/infrastructure/network-attached-storage/mount-nas-storage-linux.html#mounting-nas-storage-in-linux) para ver cómo correlacionar el almacenamiento de archivos de red (NFS) al servidor Linux. [El almacenamiento NAS también se puede correlacionar con VMware ESXi como almacén de datos a través de NFS](https://console.bluemix.net/docs/infrastructure/network-attached-storage/connect-nas-storage-windows.html#connecting-to-nas-storage-in-windows).

## Siguientes pasos

  [2. Protección del entorno](/docs/infrastructure/sap-hana/hana-secure-environment.html)

  [3. Instalación del sistema operativo de invitado en el hipervisor ESX (opcional)](/docs/infrastructure/sap-hana/hana-installing-guest-operating-system-VMware-deployments.html)

  [4. Descarga e instalación de software y aplicaciones SAP](/docs/infrastructure/sap-hana/hana-installing-SAP-landscape.html)
  
  [5. Prueba de conectividad a su centro de datos {{site.data.keyword.cloud_notm}}](/docs/infrastructure/sap-hana/hana-testing-connectivity.html)
