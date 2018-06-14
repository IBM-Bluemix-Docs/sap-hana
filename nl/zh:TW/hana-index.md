---



copyright:
  years: 2017, 2018
lastupdated: "2018-03-02"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 開始使用 IBM Cloud for SAP Applications 指導教學
{: #getting-started}

{{site.data.keyword.IBM_notm}} 及 SAP 已在多個領域（包括硬體、軟體、雲端、服務及融資）分工合作 45 年。它們現在分工合作以最佳化 {{site.data.keyword.cloud}} 基礎架構產品，支援全球超過 60 個 {{site.data.keyword.cloud_notm}} 資料中心內的 SAP HANA 解決方案。
{: shortdesc}

此內容提供 {{site.data.keyword.cloud_notm}} 上 SAP HANA 基礎架構及訂閱的佈建及安裝建議。它不會取代為任何 SAP HANA 文件，也不是要提供安裝處理程序的完整說明。其目的是協助您進行基礎架構規劃及佈建，以開始 SAP 安裝。SAP 安裝（包括資料庫安裝）不會因內部部署環境的安裝而不同。關於提供的基礎架構，提供建議及準則，以協助您在 {{site.data.keyword.cloud_notm}} 環境中操作 SAP 系統。在基礎架構備妥之後，SAP HANA 系統的作業不會與其在任何其他資料中心內的作業不同。

「表 1」包含的步驟可協助您快速建置 {{site.data.keyword.cloud_notm}} 基礎架構。
<table>
   <CAPTION>表 1. 快速入門步驟</CAPTION>
   <THEAD>
   <TR>
   <th>作業</th>
   <th>詳細資料</th>
   </TR>
   </THEAD>
   <TBODY>
   <tr>
   <td>1. 閱讀與您實作相關的 IBM Cloud 及 SAP 內容。</td>
   <td>如果您的組織初次使用 IBM Cloud，則下列資訊可能有用，您應該在規劃階段之前閱讀它。
   <li><a href="https://ibm.com/cloud-computing/">何謂 IBM Cloud</a></li>
   <li><a href="https://ibm.com/cloud/get-started">開始使用 IBM Cloud</a></li>
   <li><a href="https://www.ibm.com/cloud/bare-metal-servers/sap">IBM Cloud 上的 SAP 認證基礎架構</a></li>
     
   您也可能會發現下列 SAP 文件十分有用：     
   <li><a href="https://www.sap.com/products/hana/implementation/resources.html">SAP HANA 安裝手冊</a>；下載安裝手冊</li> 
   <li><a href="https://www.sapappsdevelopmentpartnercenter.com/en/faq/program-faqs_2/how-to-receive-an-s-user-to-access-the-s_77/">如何設定 SAP S 使用者 ID</a></li>
   <li><a href="https://help.sap.com/hana/SAP_HANA_Administration_Guide_en.pdf">SAP HANA 管理手冊</a></li>
   <li><a href="https://support.sap.com">SAP Notes</a>；需要 SAP S 使用者 ID</li>
   <tr>
   <td>2. 註冊 IBM Cloud</td>
   <td>如需如何設定 IBM Cloud 帳戶的步驟，請參閱<a href="https://console.bluemix.net/docs/admin/adminpublic.html#signing-up-for-ibm-cloud">註冊 IBM Cloud</a>。</td>
 <tr>
   <td>3. 存取 IBM Cloud 基礎架構客戶入口網站</td>
   <td><a href="https://control.softlayer.com">IBM Cloud 基礎架構客戶入口網站</a>是您所有基礎架構元件（運算、連線功能、儲存空間、網路及資料中心）的圖形閘道。您需要 <a href="https://console.bluemix.net/docs/customer-portal/getting-started.html#getting-started">IBM ID 及密碼</a>，才能存取客戶入口網站。</td> 
   <tr>
   <td>4. 規劃系統架構</td>
   <td>使用<a href="hana-planning-your-system-landscape.html">規劃系統架構</a>中的資訊來架構、調整大小及佈建 IBM Cloud 環境，以支援 SAP HANA 工作負載。</td>  
 <tr>
   <td>5. 佈建系統</td>
   <td>使用<a href="hana-provision-environment.html#provision_environment">佈建 SAP HANA 環境</a>中的步驟及資訊，來設定 IBM Cloud 基礎架構。</td>
   <tr>
   <td>6. 安裝 SAP 架構</td>
   <td>您可以在 IBM Cloud 基礎架構上安裝 SAP 架構，就像伺服器是內部部署一樣。如需相關資訊，請參閱<a href="hana-installing-SAP-landscape.htm#install_sap">下載並安裝 SAP 軟體及應用程式</a>。</td>
   </td>
   </tr>
   </TBODY>
   </table>
