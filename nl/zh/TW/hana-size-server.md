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
{:tip: .tip}
{:table: .aria-labeledby="caption"}


# 4. 調整伺服器大小
{: #size_the_server}

在您決定打算要使用的 SAP 解決方案之後，下一步是判斷要支援 SAP 架構所需的 {{site.data.keyword.baremetal_long}} 數目，並確定伺服器已正確調整大小。
{: shortdesc}

## 瞭解 SAP 大小調整方法
{: #size_method}

在具有下列 RAM 大小總計的單一節點配置中，於 {{site.data.keyword.cloud_notm}} 上提供 SAP HANA： 
  * 512 GB
  * 1024 GB (1 TB)
  * 2048 GB (2 TB)
  * 4096 GB (4 TB)
  * 8192 GB (8 TB)
  
相較於傳統的橫列型「關聯式資料庫管理系統 (RDMS)」，這個直欄式資料庫一般需要較少的空間來儲存資料。資料可以進行高度壓縮，而且根據來源資料及資料庫，壓縮比例的範圍可以從 3:1 到 10:1 以上。 

在購買伺服器*之前*，您需要正確地調整伺服器大小，因為大小調整是專案成功的關鍵。大小不適當的記憶體或儲存空間需求，可能會導致升級及移轉至較大的伺服器。

## 存取 SAP Quick Sizer
{: #quick_sizer}

調整 SAP HANA 認證的應用裝置大小時，主要記憶體是要考量的其中一個最重要資源。公用 [*SAP HANA 主要手冊*](https://help.sap.com/doc/e95f6750b0fd10148ea5c6be75016694/2.0.00/en-US/SAP_HANA_Master_Guide_en.pdf) 提供調整大小相關主題的起點。本手冊內的[調整 SAP HANA 大小](https://help.sap.com/viewer/eb3777d5495d46c5b2fa773206bbfb46/2.0.00/en-US/d4a122a7bb57101493e3f5ca08e6b039.html)資訊提供如何調整 SAP HANA 系統大小的指引。它指向全新安裝及現有系統的不同安裝及移轉情境。具有 SAP Quick Sizer 工具之 SAP HANA 版本的鏈結（需要 SAP S 使用者 ID 才能存取工具）。此頁面也會列出與 SAP HANA 伺服器大小調整相關的 SAP Notes。 

## 虛擬化環境大小調整
{: #size_virtual}

如需在虛擬化環境中執行 SAP HANA 時的其他大小調整考量，請參閱 [VMware ESXi 伺服器部署](/docs/infrastructure/sap-hana/hana-considerations.html#vmware-server)及 [*Architecture Guidelines and Best Practices for Deployments of SAP HANA on VMware vSphere Architecture and Technical Considerations Guide*](https://www.vmware.com/content/dam/digitalmarketing/vmware/en/pdf/whitepaper/sap_hana_on_vmware_vsphere_best_practices_guide-white-paper.pdf)。

## 後續步驟

 [5. 決定配置](/docs/infrastructure/sap-hana/hana-determine-configuration.html)
