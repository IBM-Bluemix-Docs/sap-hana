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

# 1. 订购存储器
{: #order_storage}

部署 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} 后，即订购了 {{site.data.keyword.blockstoragefull}}、{{site.data.keyword.filestorage_full_notm}} 和网络连接的存储器 (NAS)。 

## 订购 {{site.data.keyword.cloud_notm}} 存储器
{: #ibm_storage}

您可以执行[供应和管理 {{site.data.keyword.blockstorageshort}}](https://console.bluemix.net/docs/infrastructure/BlockStorage/provisioning-block_storage.html#provisioning-and-managing-block-storage) 或[供应和管理 {{site.data.keyword.filestorage_full_notm}}](https://console.bluemix.net/docs/infrastructure/FileStorage/provisioning-file-storage.html#provisioning-and-managing-ibm-file-storage-for-ibm-cloud) 下的步骤，以订购备份和复原存储器解决方案。这些步骤将逐步指导您确定要使用哪种存储器类型、如何进行订购以及如何将其部署到服务器。

## 订购 NAS
{: #order-nas}

如果需要存储数据库的归档日志文件或者频繁存储联机和脱机备份，那么 NAS 存储器可能是服务器的本地存储器的另一个有价值的扩展。访问[订购 NAS/FTP 存储器](https://console.bluemix.net/docs/infrastructure/network-attached-storage/index.html#ordering-nas-ftp-storage)以订购和设置 NAS。另请参考[在 Linux 中安装 NAS 存储器](https://console.bluemix.net/docs/infrastructure/network-attached-storage/mount-nas-storage-linux.html#mounting-nas-storage-in-linux)，以了解如何将网络文件存储器 (NFS) 映射到 Linux 服务器。[也可通过 NFS 将 NAS 存储器映射到 VMware ESXi 作为数据存储器](https://console.bluemix.net/docs/infrastructure/network-attached-storage/connect-nas-storage-windows.html#connecting-to-nas-storage-in-windows)。

## 后续步骤

  [2. 保护环境](/docs/infrastructure/sap-hana/hana-secure-environment.html)

  [3. 在 ESX 管理程序上安装访客操作系统（可选）](/docs/infrastructure/sap-hana/hana-installing-guest-operating-system-VMware-deployments.html)

  [4. 下载和安装 SAP 软件和应用程序](/docs/infrastructure/sap-hana/hana-installing-SAP-landscape.html)
  
  [5. 测试与 {{site.data.keyword.cloud_notm}} 数据中心的连接](/docs/infrastructure/sap-hana/hana-testing-connectivity.html)
