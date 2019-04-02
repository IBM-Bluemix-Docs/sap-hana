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


# IBM Cloud 高可用性支援
{: #ha}

{{site.data.keyword.cloud}} 基礎架構即服務 (IaaS) 提供建全的運算環境，並在其上可有選用的作業系統 (OS) 部署，以支援高可用性 (HA) 解決方案。這個解決方案是根據支援的作業系統版本，相關內容會在 [SAP 附註 2414097 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://launchpad.support.sap.com/#/notes/2414097){: new_window} 中提及。HA 解決方案受限於您與部署一起提供的已訂購作業系統授權，或協力廠商授權，例如自帶授權 (BYOL)。部署之前請務必與 {{site.data.keyword.cloud_notm}} 支援中心討論 HA 的詳細資料。

{{site.data.keyword.cloud_notm}} for SAP 有支援且已部署的的作業系統為
* Linux [Red Hat Enterprise Linux (RHEL) 或 SUSE Enterprise Linux Server (SLES)] 同時支援 SAP NetWeaver 及 SAP HANA HA 解決方案。這些是在 {{site.data.keyword.cloud_notm}} 環境中的次要限制，相關內容會在 [SAP NetWeaver 高可用性配置的概觀](#overview-configs)中提及。
* Microsoft Windows 僅支援 SAP NetWeaver HA 解決方案（這是 SAP HANA 資料庫的限制）。

## SAP NetWeaver 高可用性配置的概觀
{: #overview-configs}

大量文件能提供深度說明，以協助規劃及安裝適用於 SAP 服務的 HA 環境。這些文件包括失效接手、抄寫、橫向擴充，以及災難回復 (DR)。在適當處會提供對特定文件的參照。

SAP 部署（Windows、Linux RHEL，以及 SLES）的 {{site.data.keyword.cloud_notm}} 所支援的所有作業系統及發行套件，與高可用性軟體及特定延伸規格一起提供。下列是支援的作業系統及發行套件。

* [Windows Server 2012 中新的失效接手叢集作業增進功能及 SAP NetWeaver 高可用性的好處 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://blogs.sap.com/2013/10/16/new-failover-clustering-improvements-in-windows-server-2012-and-its-benefits-for-sap-netweaver-high-availability/){: new_window} 會根據 Windows 作業系統上搭配 SAP NetWeaver 使用的「Microsoft Windows Server 失效接手叢集作業 (WFSC)」來提供說明。

* 下列為在 Linux 型 HA 環境中搭配 Linux Pacemaker 以部署 SAP NetWeaver 的兩個指引參照：
  * SUSE SAP NetWeaver High Availability Cluster 7.40 安裝手冊
  * 使用 Red Hat Enterprise Linux HA 附加程式搭配 Pacemaker 來部署高可用性 SAP NetWeaver 型伺服器

* [建置 SAP NetWeaver 及 SAP HANA on Linux 的高可用性 ![外部鏈結圖示](../../icons/launch-glyph.svg "External link icon")](https://support.sap.com/content/dam/SAAP/SAP_Activate/AGS_70.pdf){: new_window} 是 SAP 的最佳作法文件，能提供著重於 SAP HANA 的深度技術說明。

* [在 Microsoft Windows 中使用 VMware 及 Hyper-V 虛擬環境中執行 SAP NetWeaver High Availability 及 Business Continuity ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://www.sap.com/documents/2015/07/508b62bc-5b7c-0010-82c7-eda71af511fa.html){: new_window} 涵蓋了虛擬化層面（如果您規劃要在虛擬化伺服器上實作 HA）。

如需更多關於由 SAP 合作夥伴所認證的高可用性產品的可用性情境，請參閱[高可用性合作夥伴資訊 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://wiki.scn.sap.com/wiki/display/SI/High+Availability+Partner+Information){: new_window}。
在您的資料庫文件中有更多針對非 HANA SAP 資料庫的 HA 失效接手，以及 DR 配置的相關資訊。

請注意，若要共用存取「網路檔案系統 (NFS)/網路文件共享系統 (CIFS)」儲存空間，或是共用存取 iSCSI 型邏輯唯一的號碼儲存空間 (LUNS)，通常都需要支援系統失效接手。本端儲存空間與抄寫方法結合，通常都需要支援 DR 類型的設定。如同內部部署，需要在規劃您的部署時檢查資料庫產品的效能及延遲需求。

## 額外的指引
{: #extra-guide}

[以仲裁為基礎的儲存空間](#quorum)及[網路考量](#network)會提供部署時需要考量的指引。除了這幾小節所概述的考量之外，在 HA 環境中安裝 SAP NetWeaver 和其資料庫系統與從其他內部部署安裝沒有什麼不同。

### 以仲裁為基礎的儲存空間
{: #quorum}

由於在 {{site.data.keyword.cloud_notm}} IBM Cloud 環境中的安全限制，無法透過「智慧平台管理介面 (IPMI)」以網路型存取遠端管理裝置。叢集環境一般會使用以 IPMI 為基礎的元件來進行「隔離叢集節點」，以一律確定仲裁。如果沒有啟用 IPMI 功能的裝置，則會使用共用儲存體裝置。在 {{site.data.keyword.cloud_notm}} 環境中，會透過將 iSCSI LUN 部署至您的伺服器來將共用儲存體實作為仲裁裝置。例如，「Microsoft 叢集」上的「檔案如需見證 (FSW)」以及適用於 Linux Pacemaker 的 Stonithon 的儲存空間型終止 (SDB)。
* 如需 Linux High Availability Cluster 概念的相關資訊，請按一下[這裡 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](http://linux-ha.org/wiki/Cluster_Concepts){: new_window}。
* 如需配置與管理 Windows Server 2012 及 Windows Server 2012 R2 的仲裁伺服器的相關資訊，請按一下[這裡 ![外部鏈結圖示](../../icons/launch-glyph.svg "外部鏈結圖示")](https://docs.microsoft.com/en-us/windows-server/failover-clustering/manage-cluster-quorum){: new_window}。

「{{site.data.keyword.cloud_notm}} 儲存空間」具有內建的 HA 功能，所以單一共用 iSCSI LUN 並不會造成「單一失敗點 (SPOF)」，因為您的網路佈置為備援網路。然而，您的叢集產品可能需要多個仲裁裝置。

### 網路考量
{: #network}

{{site.data.keyword.cloud_notm}} 型安裝具有下列其中一個網路配置：
* 專用網路
* 公用網路
* 公開和專用網路
* 兩個專用網路（應特殊需求）

如同內部部署安裝，可以依據硬體的實體限制來訂購額外的網路配接卡。此限制對內部部署安裝是相同的。在硬體部署期間訂購備用網路配接卡，可避免您的網路拓蹼各處都有 SPOF。可以透過「鏈結聚集控制通訊協定 (LACP)」在失效接手配置中設定備用配接卡。若是 Linux，則會使用連結的介面來進行設定，而 Microsoft Windows 則會使用 Teaming 配接卡進行設定。這些配接卡所連接的 {{site.data.keyword.cloud_notm}} 交換器基礎架構為備用，因此不會引進新的 SPOF。已訂購的 VLAN 可以使用備用基礎架構。

依據網路需求，像是在 DR 設定中的抄寫情境，您必須檢查連接裝置的位置及任何關於特定於產品的新網路需求。在某些情況下，{{site.data.keyword.cloud_notm}} Snapshot 儲存空間型抄寫可能會滿足您的需求。請諮詢 {{site.data.keyword.cloud_notm}} 支援中心以判定哪一種解決方案最適合您的商業程序需要。
