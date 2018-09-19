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

# SAP HANA on IBM Cloud IaaS 概觀
{: #iaas-overview}

「基礎架構即伺服器 (IaaS)」環境包含許多元件：資料中心、運算、連線功能、儲存空間及網路。 

## 資料中心

使用跨北美洲、南美洲、歐洲、亞洲及澳洲的資料中心，您可以在需要它們的位置（及時機）佈建雲端資源。每一個資料中心都會連接至 {{site.data.keyword.cloud_notm}} 廣域專用網路，讓世界各地的資料傳送更為快速且更具效率。

如需相關資訊，請參閱[資料中心](https://www.ibm.com/cloud-computing/bluemix/data-centers){: new_window}。

## 裸機伺服器

{{site.data.keyword.baremetal_long}} 是具有有限自訂功能的實體伺服器。這些伺服器專供您或您的客戶使用，而且不會與其他 {{site.data.keyword.cloud_notm}} 客戶共用任何部分（包括伺服器資源），並且佈建為執行您選擇之作業系統 (OS) 的整個實體伺服器。SAP HANA 供應項目的作業系統是 Red Hat Enterprise Linux 7.4 for SAP HANA、SUSE Linux Enterprise Server 12 SP2 for SAP HANA 及 VMware Server Virtualization 6.5。

因為自訂作業在裸機伺服器上受到限制，所以可以達到 1 到 4 小時的更快佈建時間。當您嘗試在競爭開始之前讓應用程式進入市場時，快速佈建很有幫助。

已為您提供 RAM 及 CPU 組合的陣列，因為 SAP 認證的伺服器具有預先配置的 RAM 數量及 CPU 數目。在訂購處理程序期間，或在部署伺服器之後透過支援問題單，並*無法* 變更組合。

如需相關資訊，請參閱[關於裸機伺服器](https://console.bluemix.net/docs/bare-metal/about.html#about-bare-metal-servers)。 

## 網路連線功能

設定 {{site.data.keyword.cloud_notm}} 帳戶時，會自動授與「虛擬專用網路 (VPN)」與「{{site.data.keyword.cloud_notm}} 虛擬雲端網路」的連線功能。依預設，您的伺服器具有公用及專用 IP 位址。如果要讓伺服器成為專用伺服器，則可以在佈建伺服器之後關閉公用介面，或將伺服器訂購為專用伺服器。 

{{site.data.keyword.cloud_notm}} 供應項目滿足 SAP HANA（10 Gb 備用網路）的網路需求時，您可能需要符合特定延遲及傳輸量關鍵績效指標 (KPI)（根據應用程式情境而定）。如需判斷哪個資料中心找到 SAP HANA 伺服器以及決定最佳網路連線功能解決方案的相關資訊，請參閱[網路連線功能](/docs/infrastructure/sap-hana/hana-considerations.html#network_connectivity)考量。

如需相關資訊，請參閱[開始使用虛擬專用網路](https://console.bluemix.net/docs/infrastructure/iaas-vpn/getting-started.html#getting-started-with-virtual-private-networking-vpn-)及 [*SAP HANA 網路需求*](https://www.sap.com/documents/2016/08/1cd2c2fb-807c-0010-82c7-eda71af511fa.html) 白皮書。

## 儲存空間
{: #storage}

本端儲存空間隨附於 {{site.data.keyword.baremetal_short}}，並使用 {{site.data.keyword.cloud_notm}} 專用網路虛擬 LAN (VLAN) 來協助提供企業級安全，而又不會妨礙管理者存取。對於 SAP HANA 認證的伺服器，其設計並配置成符合 SAP 針對 SAP HANA 憑證準則的傳輸量及延遲所定義的 KPI。本端儲存空間具有不同子檔案系統的相關大小（如《SAP HANA 安裝手冊》所定義）（`data.log` 及 `shared`）。您不需要再進一步改寫。

{{site.data.keyword.cloud_notm}}-block 及 file-from 有兩種類型的儲存空間，而您可以從中選擇來執行 SAP HANA 的備份及還原。兩種類型都使用每秒輸入/輸出作業數 (IOPS)，以用來決定儲存空間需求。IOPS 是根據 16 KB 區塊大小與 50/50 讀寫混合大小進行測量。若要達到磁區的 IOPS 上限，需要備妥足夠的網路資源。其他考量包括在儲存空間和主機端外的專用網路使用情形，以及應用程式特定的調整（例如，IP 堆疊及佇列深度）。如需相關資訊，請參閱[開始使用區塊儲存空間](https://console.bluemix.net/docs/infrastructure/BlockStorage/index.html#getting-started-with-block-storage)及[開始使用檔案儲存空間](https://console.bluemix.net/docs/infrastructure/FileStorage/index.html#getting-started-with-file-storage)。

如果您要尋找裝置的快速、具成本效益的備份解決方案，則 {{site.data.keyword.cloud_notm}} 也提供「網路連接儲存空間 (NAS)」。NAS 可以透過「網路檔案系統 (NFS)」進行裝載，而且可以與具有 Parallels Plesk Panel 及 cPanel@WHM 的「檔案傳送通訊協定 (FTP)」搭配使用。

NAS 儲存空間可以用於任何用途，但在此情況下，*不* 是用於 SAP HANA 資料或日誌檔。儲存空間未滿足有關 I/O KPI 的準則。不過，儲存空間可以用於備份裝置及所有其他類型的資料。透過 NFS 裝載時，SAP HANA 可以將它當成備份裝置用於資料及日誌檔。  
  
NAS 及 FTP 儲存空間是每月計費，並且提供各種儲存空間大小。您主要可以透過作業系統，在指令行或終端機內與 NAS 及 FTP 儲存空間進行互動，或者透過 {{site.data.keyword.cloud_notm}} 基礎架構客戶入口網站內之畫面上的點按方式來進行互動。在客戶入口網站內，可以使用 NAS 詳細資料及使用情形，但無法在指令行、核心或控制台外部操作服務。

如需 {{site.data.keyword.cloud_notm}} 環境中 NAS 的相關資訊，請參閱[開始使用 NAS](https://console.bluemix.net/docs/infrastructure/network-attached-storage/index.html#getting-started-with-nas)。

## 部署及管理

在您建立 {{site.data.keyword.cloud_notm}} 客戶帳戶之後，會透過 {{site.data.keyword.cloud_notm}} 基礎架構客戶入口網站或 API 來部署 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}。伺服器可以透過客戶入口網站、API 或指令行介面 (CLI) 進行管理。如需相關資訊，請參閱[關於裸機伺服器](https://console.bluemix.net/docs/bare-metal/about.html#about-bare-metal-servers)。

## 支援

[{{site.data.keyword.cloud_notm}} 客戶支援中心](https://console.bluemix.net/docs/support/index.html#getting-customer-support)能處理因使用各種銷路（包括會談、電話及問題單型支援）而可能引起的任何支援問題和議題。客戶支援中心是免費提供給所有 {{site.data.keyword.cloud_notm}} 客戶使用，並涵蓋每天所提出的大部分問題單。如需相關資訊，請參閱[取得客戶支援](https://console.bluemix.net./docs/support/index.html#getting-customer-support)。

您也可以透過「SAP 支援中心」繼續建立與 {{site.data.keyword.cloud_notm}} IaaS 及 SAP 產品相關的問題單。如需相關資訊，請參閱 [SAP 支援中心](https://support.sap.com/en/index.html)及 [SAP Note 2414820](https://launchpad.support.sap.com/#/notes/2414820)。

## 安裝 SAP HANA

必須由已完成 SAP HANA 安裝憑證課程的認證 SAP HANA 安裝者來安裝 SAP HANA 軟體。如需相關資訊，請參閱[誰可以安裝 SAP HANA？](http://www.saphanacentral.com/p/who-can-install-sap-hana.html)。
