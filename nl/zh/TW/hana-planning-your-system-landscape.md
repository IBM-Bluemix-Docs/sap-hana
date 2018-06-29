---



copyright:
  years: 2017, 2018
lastupdated: "2018-02-05"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 規劃系統架構
{: #planning-your-system-landscape}

SAP *架構* 是一組兩個以上的 SAP *系統*，通常包括開發、品質和測試以及正式作業。一個 SAP 系統包含一個以上的 *SAP 實例*，而這些實例是同時啟動及停止的一組處理程序。如需 SAP 架構的相關資訊，請參閱 [*SAP Business Suite on IBM X6 Systems Reference Architecture*](https://lenovopress.com/redp5073.pdf)。
{: shortdesc}

針對市場中的所有 SAP 解決方案，有數個可能的架構配置，例如伺服器（大小）/儲存空間（大小）。這些解決方案包括 SAP NetWeaver 型產品，例如 [SAP Business Suite](https://open.sap.com/courses/suitehana1)、SAP Business Warehouse 及所有特定 SAP 附加程式，而 {{site.data.keyword.cloud}} for SAP Applications 供應項目中的伺服器支援這些附加程式。其他要記住的解決方案是可能與 SAP 整合的任何協力廠商軟體。 

根據使用情境，SAP HANA 可以當成 SAP NetWeaver 堆疊型解決方案的資料庫來執行，或當成獨立式實體來執行。在這兩個情境中，{{site.data.keyword.cloud_notm}} 供應項目提供預先配置的 SAP NetWeaver 認證伺服器，而這些伺服器的架構可以從任何其他伺服器進行建置。

當您根據計劃執行的應用程式、潛在成長及效能來決定伺服器大小時，請盡可能詳細。此外，請記住您應用程式的儲存空間及記憶體需求。架構中的 SAP 系統具有連線功能（彼此之間或與外部系統之間）的特定需求。如需相關資訊，請參閱[規劃 SAP 架構時要考量的項目](/docs/infrastructure/sap-hana/hana-considerations.html)。

「表 1」包含規劃程序內的步驟。請使用它來協助建置目標 SAP 架構。

表 1. 規劃程序概觀

| 步驟 | 詳細資料|
| --- | --- |
| 1 | [取得 SAP 及 {{site.data.keyword.cloud_notm}} 認證，並建立帳戶](/docs/infrastructure/sap-hana/hana-get-credentials.html) |
| 2 | [檢閱任何相關的 SAP 及 {{site.data.keyword.cloud_notm}} 文件](/docs/infrastructure/sap-hana/hana-review-doc.html) |
| 3 | [決定 SAP 應用程式](/docs/infrastructure/sap-hana/hana-determine-apps.html) |
| 4 | [調整伺服器大小](/docs/infrastructure/sap-hana/hana-size-server.html) |
| 5 | [決定配置](/docs/infrastructure/sap-hana/hana-determine-configuration.html) |

## 後續步驟

在「表 1」中選取適當的步驟，以開始規劃 SAP 架構。