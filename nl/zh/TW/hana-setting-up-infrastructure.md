---



copyright:
  years: 2017, 2018
lastupdated: "2010-08-10"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 2. 設定基礎架構
{: #set_up_infrastructure}

下節說明如何設定 SAP HANA {{site.data.keyword.baremetal_long}}、網路、安全、儲存空間及作業系統 (OS) 的指引。如有任何問題，請聯絡 [{{site.data.keyword.cloud_notm}} 支援中心](https://console.bluemix.net/docs/get-support/howtogetsupport.html#getting-customer-support)。

## 訂購伺服器
{: order-server}

請使用下列步驟來訂購 {{site.data.keyword.baremetal_short}}。您可以在使用唯一的認證[建置自訂裸機伺服器](https://console.bluemix.net/docs/bare-metal/baremetal-provision.html#building-a-custom-bare-metal-server)下找到其他資訊。

1. 使用唯一的認證登入 [{{site.data.keyword.cloud_notm}} 基礎架構客戶入口網站](https://control.softlayer.com)。
2. 按一下「帳戶摘要」頁面上的**帳戶** > **下訂單**圖示。
3. 在「裝置」頁面上，按一下 {{site.data.keyword.baremetal_short}} 下的**每月**鏈結。會出現「伺服器清單」；SAP 認證伺服器會在清單頂端。
4. 按一下**每個月的起始價格**下的超鏈結，以選取適當的伺服器並進入「配置/訂購」頁面。在「CPU 模型」下，使用 **-H** 識別 SAP HANA 認證伺服器。  
5. 在**數量**欄位中輸入您要訂購的伺服器數目，然後選取**資料中心**。
6. **伺服器**、**RAM** 及專用儲存空間選項的預設值是根據您的伺服器選擇，無法加以變更。在您訂購伺服器之後，請訂購 {{site.data.keyword.IBM_notm}} {{site.data.keyword.blockstorageshort}} for {{site.data.keyword.cloud_notm}} 或 {{site.data.keyword.filestorage_full_notm}} 及「網路連接儲存空間 (NAS)」。
7. 從 Red Hat 或 SUSE 中選取**作業系統**，並選取特定的作業系統，或為您的伺服器選取 VMware Hypervisor。**附註**：如果您為作業系統自帶授權 (BYOL)，請選取**其他** > **無作業系統**。如需相關資訊，請參閱[自帶授權](#byol)。

## 選取伺服器選項
{: #select_options}

在下一步中，您將選取您要新增至配置的磁碟類型及數目。針對「獨立磁碟的備用陣列 (RAID)」儲存空間群組以及 RAID 儲存空間群組上的分割佈置，您也可以選取不同的選項。如需相關資訊，請參閱[關於 RAID](https://console.bluemix.net/docs/bare-metal/what-raid.html#about-raid) 或 [{{site.data.keyword.cloud_notm}} 支援中心](https://console.bluemix.net/docs/get-support/howtogetsupport.html#getting-customer-support)。

1. 在 **SAP 認證伺服器**下，根據如何規劃伺服器的使用進行選取。如需相關資訊，請參閱[設計決策工具](https://github.com/ibm-cloud-architecture/infrastructure-design-decision-tool)（向下捲動至工具）或 [{{site.data.keyword.cloud_notm}} 支援中心](https://console.bluemix.net/docs/get-support/howtogetsupport.html#getting-customer-support)。
2. 按一下頁面底端的**新增至訂單**。

## 設定進階系統配置
{: #adv_config}

1. 遵循[進階系統配置](https://console.bluemix.net/docs/bare-metal/baremetal-provision.html#advanced-server-configuration-options)準則，以協助輸入**進階系統配置**視窗中的值。

SAP 主機名稱必須包含最多 13 個英數字元。如需 SAP 主機名稱的相關資訊，請參閱 [SAP Notes 611361](https://launchpad.support.sap.com/#/611361) 及 [129997](https://launchpad.support.sap.com/#/129997)。 

## 確認選取項目
{: #confirm_selections}

1. 在「結帳」頁面上確認您的選取項目，然後按一下**雲端服務條款**及**協力廠商軟體合約**。
2. 向下捲動至「建立帳戶：輸入計費」，然後輸入**付款類型、名稱、卡片**及**到期**（日期），以使用信用卡付費。
3. 按一下**提交訂單**。會將您重新導向至具有訂單號碼的畫面。您可以列印畫面，因為它也是訂單收據。

主旨為_{{site.data.keyword.cloud_notm}}已核准訂單 ##_ 的確認電子郵件會傳送至您設定檔中的電子郵件位址。此電子郵件是一種通知，通知您已核准您的伺服器，並且正在進行部署。部署之後，會傳送另一個通知，通知您已有伺服器可用，而且可以透過 [{{site.data.keyword.cloud_notm}} 基礎架構客戶入口網站](https://control.softlayer.com)進行管理。

## 自帶授權
{: #byol}

當您有自己的作業系統授權時，請根據供應商的指示將它安裝在 {{site.data.keyword.baremetal_short}} 上。如需相關資訊，請參閱[無 OS 選項](https://console.bluemix.net/docs/bare-metal/introduction-no-os.html#how-to-install-an-operating-system-on-a-no-os-server-)。

## 後續步驟

您現在已準備好開始管理{{site.data.keyword.baremetal_short}}。請參閱[管理 SAP HANA 環境](/docs/infrastructure/sap-hana/hana-manage-environment.html)。

