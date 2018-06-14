---



copyright:
  years: 2018
lastupdated: "2018-03-02"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}


# 3. 決定 SAP 應用程式

您需要決定打算在 {{site.data.keyword.baremetal_long}} 上執行的 SAP 型應用程式。決定時要考量的項目包括：

 * 如何使用資料庫？有兩種方式可以部署 SAP HANA。第一種是作為 SAP NetWeaver 堆疊的資料庫，而此資料庫主要作為資料來源。第二種部署方法是以獨立式模式執行 SAP HANA，並在 SAP HANA 系統中直接部署應用程式。在任一方法中，調整大小處理程序以及其他系統需求和相依關係，可能會根據您使用系統的方式（開發及測試、概念證明或正式作業）而不同。
 * 您要如何使用應用程式？要用於開發及測試，或正式作業？
 * 您要使用「{{site.data.keyword.cloud_notm}} 虛擬專用網路」服務 SSL 或「點對點通道通訊協定 (PPTP)」嗎？
  
## 後續步驟

  [4. 調整伺服器大小](/docs/infrastructure/sap-hana/hana-size-server.html)
  
  [5. 決定配置](/docs/infrastructure/sap-hana/hana-determine-configuration.html)
