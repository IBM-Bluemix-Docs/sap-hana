---



copyright:
  years: 2018
lastupdated: "2018-08-29"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 5. 配置 IBM Cloud 基礎架構以支援 SAP HANA 多節點
{: #multi-node-storage}

{{site.data.keyword.cloud_notm}} 支援線上分析程序 (OLAP) 工作負載的 SAP HANA 多節點儲存空間，例如 SAP Business Warehouse (SAP BW) 和 SAP BW/4HANA。SAP HANA 多節點的 {{site.data.keyword.cloud}} 解決方案包含多達 15+1 個節點（15 個工作者節點，加上一個待命節點），一個系統可以使用最多 30 TB 的記憶體。

使用多節點，多個 SAP HANA 節點會建立單一個 SAP HANA 系統。資料分散在這些節點，它們形成單一個資料庫。多節點配置透過待命配置，支援可擴充性與高可用性。此配置的 {{site.data.keyword.cloud_notm}} 供應項目會遵循 [SAP HANA Tailored Data Center Integration](https://blogs.saphana.com/2015/02/18/sap-hana-tailored-data-center-integration-tdi-overview/) (TDI)，並且使用 {{site.data.keyword.cloud_notm}} SAP-HANA 認證伺服器來進行集中式、共用的企業儲存。

*請注意*，您必須遵循[訂購多節點系統](#ordering)下概述的配置準則，以達成 SAP HANA TDI 需求並獲得 SAP 的支援。

請遵循 [Sizing SAP HANA](https://help.sap.com/viewer/eb3777d5495d46c5b2fa773206bbfb46/2.0.00/en-US/d4a122a7bb57101493e3f5ca08e6b039.html) 中的準則，以判定您的目標 SAP HANA 系統需要的大小，包括部署所需的記憶體及儲存空間數量總計。大小需求有助於您建立 SAP HANA 多節點系統需要的 SAP HANA 節點數，以及管理資料所需的儲存空間。

## 檢閱網路拓蹼及儲存空間佈置
{: #reviewing-topology}

圖 1 顯示 {{site.data.keyword.cloud_notm}} 基礎架構即服務 SAP HANA TDI 設定所需的網路拓蹼。

圖 1. IBM Cloud 基礎架構即服務 SAP HANA TDI 網路拓蹼

![圖 1. IBM Cloud 基礎架構即服務 SAP HANA TDI 網路拓蹼](/images/SAP-BW.png "IBM Cloud 基礎架構即服務 SAP HANA TDI 網路拓蹼")

## 設定必要條件
{: #prerequisites}

SAP HANA 多節點需要特定網路就緒才能運作。在您訂購其他系統元件之前，必須先正確地設定這些網路，以及資料庫節點。您需要
* 用戶端網路，將 SAP Advanced Business Application Programming (SAP ABAP) 應用程式伺服器、SAP HANA Studio 用戶端及任何其他網路用戶端連接至多節點系統。網路傳輸量及可用性選項取決於 SAP HANA 多節點系統的使用情境。請考量從 SAP HANA 資料庫傳送及傳送到其中的資料量，以及您應用程式所需的可用性關鍵績效指標 (KPI)。
* 儲存空間儲存，連接至後端 {{site.data.keyword.blockstoragefull}} 及 {{site.data.keyword.filestorage_full_notm}} 時需要。若要使效能及備援達到最大，需要 10 Gb 網路，並且具有兩個介面，使用 Linux 連結與鏈結聚集控制通訊協定 (LACP)。若無來自 SAP HANA 大小準則的所提供效能數據，將無法滿足 SAP HANA TDI KPI。
* SAP HANA 內部通訊的節點間網路，其已設定為相等於儲存空間網路。節點間網路只用於節點之間的通訊，以及在作業期間可能在節點之間需要進行的資料傳送。這項必要網路配置是在兩片實體 10 Gb 配接卡上，使用 Linux 連結與 LACP。

## 訂購多節點系統
{: #ordering}

若要滿足 SAP 所要求的效能及傳輸量 KPI，您的 VLAN、儲存空間和運算節點必須在相同的資料中心裡訂購。如果您的元件分散在多個資料中心，SAP 將不支援您的多節點系統。

1. 訂購三個不同的 VLAN 和具有四片配接卡的伺服器（兩片專用、兩片公用）。如需訂購 VLAN 的相關資訊，請參閱[步驟 1. 訂購主要及公用 VLAN](https://console.bluemix.net/docs/infrastructure/virtualization/advanced-single-site-vmware-reference-architecturesoftlayer.html#step-1-ordering-primary-public-and-private-vlans)。如需訂購伺服器的相關資訊，請參閱 [2. 設定基礎架構](https://console.bluemix.net/docs/infrastructure/sap-hana/hana-setting-up-infrastructure.html#set_up_infrastructure)。
2. 設定起始專用 VLAN 作為「儲存空間 VLAN」。
3. [開立問題單](https://console.bluemix.net/docs/get-support/howtogetsupport.html#open-ticket)，讓 {{site.data.keyword.cloud_notm}} 支援中心：
   a. 將公用介面移到第二個 VLAN
   b. 額外訂購兩片配接卡，以便指派給第三個 VLAN，此為用戶端 VLAN

您現在會有根據調整大小努力的伺服器數目，且您的網路設定以便：
* 儲存空間可以連接到所有節點
* 儲存空間連接之後，可以執行 SAP HANA 多節點安裝

您的儲存空間 LAN 連線和節點間連線已由 {{site.data.keyword.cloud_notm}} 部署配置。請務必訂購具有兩張 10 Gb 配接卡的連線，且每張配接卡都有失效接手配置。此設定可確保正確的 Linux 連結和 LACP 配置。如有任何問題，請與 {{site.data.keyword.cloud_notm}} 支援中心團隊聯絡。

有特定的效能準則，{{site.data.keyword.IBM_notm}} {{site.data.keyword.blockstorageshort}}（耐久性）和 {{site.data.keyword.IBM_short}} {{site.data.keyword.filestorage_short}}（效能）必須符合。若為資料磁區，每個工作者節點需要具有效能 KPI 10 IOPS/GB 的 2 TB 耐久性儲存空間。需要額外有一個相同大小的磁區作為 SAP HANA 共用儲存空間，將由所有節點所共用。

若為日誌磁區，每個節點需要一個 512 GB 磁區的效能儲存空間，並且具有效能 KPI 10 K IOPS。

您可以使用[佈建及管理 {{site.data.keyword.blockstorageshort}}](https://console.bluemix.net/docs/infrastructure/BlockStorage/provisioning-block_storage.html#provisioning-and-managing-block-storage) 或[佈建及管理 {{site.data.keyword.filestorage_full_notm}}](https://console.bluemix.net/docs/infrastructure/FileStorage/provisioning-file-storage.html#provisioning-and-managing-ibm-file-storage-for-ibm-cloud) 下的步驟，來訂購耐久性及效能儲存空間。

## 配置 SAP HANA 多節點
{: #configuring}

SAP HANA 共用磁區，以及每個資料和日誌磁區，都必須可以供所有節點存取。此方法表示所有磁區都可供整個儲存空間 VLAN 存取，這是您在[訂購多節點系統](#ordering)之下所配置。如果您不想要列出每個相關的 IP 位址，請讓磁區可供 VLAN 的整個 IP 子網路存取。

請遵循 [SAP HANA on NetApp FAS Systems with NFS](https://www.netapp.com/us/media/tr-4290.pdf) 中的指引，來配置 SAP HANA 多節點系統。請使用下列「網路檔案系統 (NFS)」裝載選項，以讓每個磁區能裝載：

`/etc/fstab` 中的 `rw,bg,hard,timeo=600,intr,noatime,vers=4,minorversion=1,lock,rsize=1048576,wsize=1048576`。

這些選項已經過 NetApp 和 {{site.data.keyword.cloud_notm}} 的測試。如果您計劃變更任何裝載選項或值，請與 {{site.data.keyword.cloud_notm}} 支援中心聯絡。

將所有磁區裝載至所有節點之後，您的多節點伺服器便已配置好，可以安裝 SAP HANA 多節點資料庫。請遵循 [SAP HANA Server Installation and Update Guide](https://help.sap.com/viewer/2c1988d620e04368aa4103bf26f17727/2.0.03/en-US) 中的步驟，以安裝您所需版本的 SAP HANA 資料庫。
