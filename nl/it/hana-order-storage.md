---



copyright:
  years: 2018
lastupdated: "2018-08-20"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 1. Ordine dell'archiviazione
{: #order_storage}

{{site.data.keyword.blockstoragefull}}, {{site.data.keyword.filestorage_full_notm}} e NAS (Network Attached Storage) vengono ordinati dopo che distribuisci il tuo {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}.

## Ordine dell'archiviazione {{site.data.keyword.cloud_notm}}
{: #ibm_storage}

Puoi utilizzare la procedura in [Provisioning and Managing {{site.data.keyword.blockstorageshort}}](https://console.bluemix.net/docs/infrastructure/BlockStorage/provisioning-block_storage.html#provisioning-and-managing-block-storage) o [Provisioning and Managing {{site.data.keyword.filestorage_full_notm}}](https://console.bluemix.net/docs/infrastructure/FileStorage/provisioning-file-storage.html#provisioning-and-managing-ibm-file-storage-for-ibm-cloud) per ordinare la tua soluzione di archiviazione del backup e del ripristino. Vieni guidato attraverso il processo di decisione di quale tipo di archiviazione utilizzare, come ordinarla e come distribuirla al tuo server.

## Ordine di NAS
{: #order-nas}

L'archiviazione NAS può essere un'altra soluzione importante dell'archiviazione locale del tuo server se hai bisogno di archiviare i file di log del tuo database o frequenti backup online e offline. Visita [Ordering NAS/FTP Storage](https://console.bluemix.net/docs/infrastructure/network-attached-storage/index.html#ordering-nas-ftp-storage) per ordinare e configurare NAS. Inoltre, fai riferimento a [Mounting NAS Storage in Linux](https://console.bluemix.net/docs/infrastructure/network-attached-storage/mount-nas-storage-linux.html#mounting-nas-storage-in-linux) per vedere come associare NFS (network file storage) al tuo server Linux. [NAS storage can also be mapped to VMware ESXi as a datastore through NFS](https://console.bluemix.net/docs/infrastructure/network-attached-storage/connect-nas-storage-windows.html#connecting-to-nas-storage-in-windows).

## Passi successivi

  [2. Protezione dell'ambiente](/docs/infrastructure/sap-hana/hana-secure-environment.html)

  [3. Installazione del tuo SO guest nell'hypervisor ESX (facoltativo)](/docs/infrastructure/sap-hana/hana-installing-guest-operating-system-VMware-deployments.html)

  [4. Scaricamento e installazione delle applicazioni e del software SAP](/docs/infrastructure/sap-hana/hana-installing-SAP-landscape.html)

  [5. Configurazione della tua infrastruttura IBM Cloud per supportare SAP HANA a più nodi](/docs/infrastructure/sap-hana/hana-multi-node.html)
