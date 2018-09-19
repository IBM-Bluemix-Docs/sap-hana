---



copyright:
  years: 2017, 2018
lastupdated: "2018-06-07"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 規劃 SAP 架構時要考量的項目
{: #considerations}

架構中的 SAP 系統具有連線功能（彼此之間或與外部系統之間）的特定需求。您還需要思考您架構的外部儲存空間，以及如果您決定在伺服器上部署 VMware，則還需要執行些什麼動作。

## 網路連線功能
{: #network_connectivity}

[{{site.data.keyword.cloud_notm}} 網路](/docs/infrastructure/sap-hana/hana-about.html#ibm_cloud_network)提供網路連線功能的 {{site.data.keyword.cloud}} 方法的概觀。如果您未適當規劃，則無論您打算要如何使用系統，網路連線功能的問題都會造成專案嚴重延遲。 

一般而言，對於 IaaS 佈建的 {{site.data.keyword.cloud_notm}} 伺服器，您有兩個介面選擇 - 第一個是具有公用 IP 的外部介面。第二個是有提供「專用 IP」的內部介面，其符合 Request for Comment (RFC) 1918。您也可以選擇具有「專用 IP」的單一內部介面。外部 IP 可能較容易使用，但存在潛在風險，即使已安裝及預先配置基本防火牆也是一樣。

第二個選項透過 {{site.data.keyword.cloud_notm}} 基礎架構客戶入口網站存取「{{site.data.keyword.cloud_notm}} 虛擬專用網路 (VPN)」，或將安全裝置部署至架構。針對防火牆、網址轉換、VPN 存取及其他網路功能，提供安全裝置。建議在決定 SAP 應用程式層所需的架構佈置及連線功能之後，您的網路部門與 [{{site.data.keyword.cloud_notm}} 支援中心](https://console.bluemix.net/docs/get-support/howtogetsupport.html#getting-customer-support)交談。

### VLAN
{: #vlans}

如果您想要在架構中區隔不同類型的網路資料流量，則可以訂購更多虛擬 LAN (VLAN)。請記住，其他 VLAN 只會導致資料流量隔離，而不會提高效能。SAP 一般建議將 10 Gb 網路用於處理其應用程式伺服器與 SAP HANA 資料庫之間的資料流量，以及用於其他 SAP HANA 用戶端（例如 SAP Business Intelligence）。如果您要隔離 SAP HANA 伺服器與其他用戶端的管理存取權，則應該為架構訂購另一個 VLAN。另一個選項是透過公用及專用網路來區隔資料流量，因為 {{site.data.keyword.cloud_notm}} 不支援進一步的「實體」上行鏈路。請遵循 SAP for [SAP HANA Tailored Data Center Integration (TDI)](https://blogs.saphana.com/2015/02/18/sap-hana-tailored-data-center-integration-tdi-overview/) 的建議。

透過 VPN 存取，以及從跳箱存取，容許從 SAP HANA Studio 透通存取 SAP HANA 實例。

## 外部儲存空間
{: #external_storage}

除了本端儲存空間之外，您可能需要更多的外部儲存空間才能執行備份。對於這些需求，您可以訂購區塊儲存空間或「網路連接儲存空間 (NAS)」（如[儲存空間](/docs/infrastructure/sap-hana/hana-general-iaas-concepts.html#storage)所述）。因為透過與所有其他網路資料流量相同的實體配接卡傳送額外區塊儲存空間及「網路檔案系統 (NFS)」資料，所以需要記住這項影響。 

對於外部儲存空間，在決定儲存空間解決方案之前，請務必計算專案需求。如果您需要還原 SAP HANA 系統，則儲存空間的 IOPS 會對還原時間範圍造成顯著影響。因為所有備份都是線上備份，不論 SAP HANA 配置方式為何，所以備份時間範圍對 SAP HANA 來不是那麼重要。

例如，使用 {{site.data.keyword.cloud_notm}} {{site.data.keyword.blockstorageshort}}，您可以計算以最大速度進行大約 12 TB 的 SAP HANA 還原。您必須建立三個實體儲存裝置（區塊儲存空間 iSCSI LUN），因為每個裝置的大小上限是 4 TB。您可以使用 Linux Logical Volume Manager 透過這三個裝置建立分段，並建立一個 12 TB 的邏輯裝置。 

12 TB 可讓您使用 3x10 IOPS/GB，這總共 122,880 IOPS/GB，以 16 KB 為單位。這可讓您具有每秒 1.875 GB 的還原時間，或還原時間總計低於 2 小時。因為以 50/50 分配的讀取及寫入進行 IOPS 測量，所以您可以將數字視為還原效能的較低界限。如果您依賴特定還原時間範圍，則建議執行備份及還原測試。

{{site.data.keyword.cloud_notm}} {{site.data.keyword.blockstorageshort}}、{{site.data.keyword.filestorage_full_notm}} 或 NAS 可以提供為備份空間，或伺服器上所安裝之其他軟體元件的儲存空間。不過，「{{site.data.keyword.cloud_notm}} 儲存空間」及 NSA 無法用來作為 SAP HANA 的儲存空間，因為這些選項不滿足 KPI 準則。

如需相關資訊，請參閱[開始使用 {{site.data.keyword.blockstorageshort}}](https://console.bluemix.net/docs/infrastructure/BlockStorage/index.html#getting-started-with-block-storage) 及[開始使用 {{site.data.keyword.filestorage_full_notm}}](https://console.bluemix.net/docs/infrastructure/FileStorage/index.html#getting-started-with-file-storage)。

## 高可用性及災難回復情境
{: #ha_dr}

{{site.data.keyword.cloud_notm}} 環境不支援任何預先配置的高可用性 (HA) 情境。不過，它可讓您透過 Red Hat Enterprise Linux HA 延伸（例如內部部署案例）實作 SAP HANA 的 HA 解決方案。

SAP HANA 系統抄寫可以配置從某部伺服器自動失效接手至抄本。遵循系統抄寫上的 SAP 文件，以判定最適合您應用程式情境及災難備援層次的抄寫模式。根據抄寫模式，需要滿足不同的網路 KPI。請查閱網路傳輸量及延遲的 SAP 建議，以判斷您選擇的作業模式所需的傳輸量及延遲上限。{{site.data.keyword.cloud_notm}} 網路拓蹼應該可以提供所有必要的配置。如果您不確定，或想要不同資料中心內的災難回復站台達到最大災難備援，則請與「{{site.data.keyword.cloud_notm}} 支援中心」聯絡以決定您情境的最佳設定。

請注意，「SAP HANA 橫向擴充（多節點）」環境仍在評估中。換句話說，SAP HANA 的待命節點不是 {{site.data.keyword.cloud_notm}} 環境中的現行選項。

如需高可用性及災難回復的相關資訊，請參閱[High availability](https://console.bluemix.net/docs/infrastructure/sap-reference-architecture/sap-ra-recommendations.html#availability), and [災難回復](https://console.bluemix.net/docs/infrastructure/sap-reference-architecture/sap-ra-recommendations.html#dr)。

如需系統抄寫以及網路傳輸量和延遲的相關資訊，請參閱
  * [如何執行 SAP HANA 的系統抄寫](https://www.sap.com/documents/2013/10/26c02b58-5a7c-0010-82c7-eda71af511fa.html)
  * [SAP HANA 系統抄寫所需的網路](https://www.sap.com/documents/2014/06/babb2b55-5a7c-0010-82c7-eda71af511fa.html)

如需設定 Linux 作業系統之 HA 叢集延伸的相關資訊，請參閱
  * [使用 Pacemaker on RHEL 自動化 SAP HANA 系統抄寫設定手冊](https://access.redhat.com/articles/1466063)
  * [SAP HANA SR 效能最佳化情境](https://www.suse.com/docrep/documents/ir8w88iwu7/suse_linux_enterprise_server_for_sap_applications_12_sp1.pdf)

## VMware ESXi 伺服器部署
{: #vmware_server}

{{site.data.keyword.cloud_notm}} SAP HANA 供應項目中的所有伺服器已認證可用於 VMware ESX，讓 SAP HANA 可以在虛擬機器 (VM) 上進行部署。如果伺服器與 VMware ESX 一起訂購，則已部署一個預先安裝、基本的已配置 ESX 實例；未部署任何 VM。請注意，您負責在 ESX 型部署中部署正確的來賓作業系統。遵循 SAP Note 2414820 中所定義的指示，以選擇 SAP HANA on {{site.data.keyword.cloud_notm}} 所支援的作業系統版本。

ESX 型部署的調整大小處理程序與裸機伺服器部署的調整大小處理程序不同。請遵循 *Architecture Guidelines and Best Practices for Deployments of SAP HANA on VMware vSphere Architecture and Technical Considerations Guide* 中的建議。需要計算虛擬化層級的額外負擔，請遵循 *Architecture...and Considerations Guide* 中的規則。在 VM 上部署來賓作業系統之後，請確定符合 SAP HANA TDI KPI。如需測試環境中與「SAP 支援中心」必要條件相符性的詳細資料，請參閱 SAP Note 1943937。特定伺服器上部署的每個 VM 都需要完成必要條件。

在虛擬化環境中，必須遵循數個其他 SAP 定義的規則來部署 SAP HANA。若為正式作業，請遵循 SAP Note 1995460 中概述的限制。SAP Note 2024433 說明一部伺服器上多個 VM 的規則。

如需相關資訊，請參閱下列文件：
  * [SAP Note 2414820](https://launchpad.support.sap.com/#/notes/2414820)
  * [*Architecture Guidelines and Best Practices for Deployments of SAP HANA on VMware vSphere Architecture and Technical Considerations Guide*](https://www.vmware.com/content/dam/digitalmarketing/vmware/en/pdf/whitepaper/sap_hana_on_vmware_vsphere_best_practices_guide-white-paper.pdf)
  * [SAP Note 1943937](https://launchpad.support.sap.com/#/notes/1943937)
  * [SAP HANA Tailored Data Center Integration Frequently Asked Questions](https://www.sap.com/documents/2016/05/e8705aae-717c-0010-82c7-eda71af511fa.html)
  * [SAP Note 1995460](https://launchpad.support.sap.com/#/notes/1995460)
  * [SAP Note 2024433](https://launchpad.support.sap.com/#/notes/2024433)
  * [SAP HANA Tailored Data Center Intgration (TDI) Overview](https://blogs.saphana.com/2015/02/18/sap-hana-tailored-data-center-integration-tdi-overview/)
