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

# 1. 訂購儲存空間
{: #order_storage}

在您部署 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} 之後，請訂購 {{site.data.keyword.blockstoragefull}}、{{site.data.keyword.filestorage_full_notm}} 及「網路連接儲存空間 (NAS)」。

## 訂購 {{site.data.keyword.cloud_notm}} 儲存空間
{: #ibm_storage}

您可以使用[佈建及管理 {{site.data.keyword.blockstorageshort}}](https://console.bluemix.net/docs/infrastructure/BlockStorage/provisioning-block_storage.html#provisioning-and-managing-block-storage) 或[佈建及管理 {{site.data.keyword.filestorage_full_notm}}](https://console.bluemix.net/docs/infrastructure/FileStorage/provisioning-file-storage.html#provisioning-and-managing-ibm-file-storage-for-ibm-cloud) 下的步驟，來訂購備份及還原儲存空間解決方案。引導您完成下列處理程序：決定要使用的儲存空間類型、訂購方式，以及如何將它部署至伺服器。

## 訂購 NAS
{: #order-nas}

如果您需要有用於資料庫的保存日誌檔或用於頻繁的線上及離線備份的儲存空間，則 NAS 儲存空間可能是伺服器本端儲存空間的另一項重要延伸。請造訪[訂購 NAS/FTP 儲存空間](https://console.bluemix.net/docs/infrastructure/network-attached-storage/index.html#ordering-nas-ftp-storage)，以訂購及設定 NAS。也請參照[在 Linux 中裝載 NAS 儲存空間](https://console.bluemix.net/docs/infrastructure/network-attached-storage/mount-nas-storage-linux.html#mounting-nas-storage-in-linux)，以查看如何將網路檔案儲存空間 (NFS) 對映至 Linux 伺服器。[也可以透過 NFS 將 NAS 儲存空間對映至 VMware ESXi 作為資料儲存庫](https://console.bluemix.net/docs/infrastructure/network-attached-storage/connect-nas-storage-windows.html#connecting-to-nas-storage-in-windows)。

## 後續步驟

  [2. 保護環境的安全](/docs/infrastructure/sap-hana/hana-secure-environment.html)

  [3. 在 ESX Hypervisor 上安裝來賓作業系統（選用）](/docs/infrastructure/sap-hana/hana-installing-guest-operating-system-VMware-deployments.html)

  [4. 下載並安裝 SAP 軟體及應用程式](/docs/infrastructure/sap-hana/hana-installing-SAP-landscape.html)

  [5. 配置 IBM Cloud 基礎架構以支援 SAP HANA 多節點](/docs/infrastructure/sap-hana/hana-multi-node.html)
