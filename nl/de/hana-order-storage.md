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

# 1. Speicher bestellen
{: #order_storage}

{{site.data.keyword.blockstoragefull}}, {{site.data.keyword.filestorage_full_notm}} und Network Attached Storage (NAS) werden nach der Bereitstellung Ihrer {{site.data.keyword.cloud_notm}}-{{site.data.keyword.baremetal_short}} bestellt. 

## {{site.data.keyword.cloud_notm}}-Speicher bestellen
{: #ibm_storage}

Anhand der Schritte unter [{{site.data.keyword.blockstorageshort}} bereitstellen und verwalten](https://console.bluemix.net/docs/infrastructure/BlockStorage/provisioning-block_storage.html#provisioning-and-managing-block-storage) oder [{{site.data.keyword.filestorage_full_notm}} bereitstellen und verwalten](https://console.bluemix.net/docs/infrastructure/FileStorage/provisioning-file-storage.html#provisioning-and-managing-ibm-file-storage-for-ibm-cloud) können Sie Ihre Sicherungs- und Wiederherstellungslösung bestellen. Sie werden durch den Entscheidungsprozess geführt, welcher Speichertyp für Sie sinnvoll ist, wie er bestellt und wie er auf Ihrem Server bereitgestellt wird.

## NAS bestellen
{: #order-nas}

NAS-Speicher kann eine weitere wertvolle Ergänzung des lokalen Speichers für Ihren Server darstellen, wenn Sie Speicherplatz für archivierte Protokolldateien oder häufige Online- und Offline-Backups benötigen. Gehen Sie zu [NAS/FTP-Speicher bestellen](https://console.bluemix.net/docs/infrastructure/network-attached-storage/index.html#ordering-nas-ftp-storage), um NAS zu bestellen und einzurichten. Lesen Sie außerdem [NAS-Speicher unter Linux anhängen](https://console.bluemix.net/docs/infrastructure/network-attached-storage/mount-nas-storage-linux.html#mounting-nas-storage-in-linux), um zu erfahren, wie NFS-Speicher an Ihren Linux-Server angehängt wird. [NAS-Speicher kann auch als Datenspeicher durch NFS zu VMware ESXi zugeordnet werden](https://console.bluemix.net/docs/infrastructure/network-attached-storage/connect-nas-storage-windows.html#connecting-to-nas-storage-in-windows).

## Nächste Schritte

  [2. Umgebung sichern](/docs/infrastructure/sap-hana/hana-secure-environment.html)

  [3. Gastbetriebssystem auf dem ESX-Hypervisor installieren (optional)](/docs/infrastructure/sap-hana/hana-installing-guest-operating-system-VMware-deployments.html)

  [4. SAP-Software und -anwendungen herunterladen und installieren](/docs/infrastructure/sap-hana/hana-installing-SAP-landscape.html)
  
  [5. Konnektivität zu Ihrem {{site.data.keyword.cloud_notm}}-Rechenzentrum testen](/docs/infrastructure/sap-hana/hana-testing-connectivity.html)
