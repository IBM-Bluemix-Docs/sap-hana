---



copyright:
  years: 2017, 2018
lastupdated: "2018-08-10"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 시작하기 튜토리얼
{: #getting-started}

{{site.data.keyword.IBM_notm}}과 SAP는 45년 이상 동안 하드웨어, 소프트웨어, 클라우드, 서비스 및 금융을 포함한 여러 영역에서 협업해 왔습니다. 현재 전세계 60개 이상의 {{site.data.keyword.cloud_notm}} 데이터 센터에서 SAP HANA 솔루션에 대한 지원을 포함하도록 {{site.data.keyword.cloud}} 인프라 제품을 최적화하기 위해 협업하고 있습니다.
{: shortdesc}

이 컨텐츠는 SAP HANA 인프라 프로비저닝 및 설치와 {{site.data.keyword.cloud_notm}} 구독에 대한 권장사항을 제공합니다. SAP HANA 문서를 대체하지 않으며 설치 프로세스에 대한 전체 설명을 제공하기 위한 것이 아닙니다. 이 컨텐츠의 목적은 SAP 설치를 시작할 수 있도록 인프라 계획 및 프로비저닝에 도움을 주기 위한 것입니다. SAP 설치(데이터베이스 설치 포함)는 온프레미스 환경의 설치와 다르지 않습니다. {{site.data.keyword.cloud_notm}} 환경에서 SAP 시스템을 작동하는 데 도움을 주기 위해 제공된 인프라(예: 네트워크 설정 또는 백업 스토리지)와 관련된 권장사항 및 가이드라인이 제공됩니다. SAP HANA 시스템의 오퍼레이션은 인프라가 준비된 후 다른 데이터 센터에서의 오퍼레이션과 다르지 않습니다.

표 1에는 {{site.data.keyword.cloud_notm}} 인프라를 빠르게 빌드하는 데 도움이 되는 단계가 포함되어 있습니다.
<table>
   <CAPTION>표 1. 빠른 시작 단계</CAPTION>
   <THEAD>
   <TR>
   <th>태스크</th>
   <th>세부사항</th>
   </TR>
   </THEAD>
   <TBODY>
   <tr>
   <td>1. 구현과 관련된 IBM Cloud 및 SAP 컨텐츠 읽기</td>
   <td>조직에서 IBM Cloud를 처음 사용하는 경우 다음 정보가 유용할 수 있으며 계획 단계 이전에 읽어야 합니다.
   <li><a href="https://ibm.com/cloud-computing/">IBM Cloud의 개념</a></li>
   <li><a href="https://ibm.com/cloud/get-started">IBM Cloud 시작하기</a></li>
   <li><a href="https://www.ibm.com/cloud/bare-metal-servers/sap">IBM Cloud의 SAP 인증 인프라</a></li>
     
   다음과 같은 SAP 문서도 유용할 수 있습니다.     
   <li><a href="https://www.sap.com/products/hana/implementation/resources.html">SAP HANA 설치 안내서</a>: 설치 안내서 다운로드</li> 
   <li><a href="https://www.sapappsdevelopmentpartnercenter.com/en/faq/program-faqs_2/how-to-receive-an-s-user-to-access-the-s_77/">SAP S-사용자 ID를 설정하는 방법</a></li>
   <li><a href="https://help.sap.com/hana/SAP_HANA_Administration_Guide_en.pdf">SAP HANA 관리 안내서</a></li>
   <li><a href="https://support.sap.com">SAP 노트</a>: SAP S-사용자 ID가 필요함</li>
   <tr>
   <td>2. IBM Cloud에 등록</td>
   <td>IBM Cloud 계정을 설정하는 방법에 대한 단계는 <a href="https://console.bluemix.net/docs/admin/adminpublic.html#signing-up-for-ibm-cloud">IBM Cloud에 등록</a>을 참조하십시오.</td>
 <tr>
   <td>3. IBM Cloud 인프라 고객 포털 액세스</td>
   <td><a href="https://control.softlayer.com">IBM Cloud 인프라 고객 포털</a>은 컴퓨팅, 연결, 스토리지, 네트워크 및 데이터 센터 등 모든 인프라 컴포넌트에 대한 그래픽 게이트웨이입니다. 고객 포털에 액세스하려면 <a href="https://console.bluemix.net/docs/customer-portal/getting-started.html#getting-started">IBM ID 및 비밀번호</a>가 필요합니다.</td> 
   <tr>
   <td>4. 시스템 랜드스케이프 계획</td>
   <td><a href="hana-planning-your-system-landscape.html">시스템 랜드스케이프 계획</a>의 정보를 사용하여 SAP HANA 워크로드를 지원하기 위한 IBM Cloud 환경을 설계, 크기 조정 및 프로비저닝하십시오.</td>  
 <tr>
   <td>5. 시스템 프로비저닝</td>
   <td><a href="hana-provision-environment.html#provision_environment">SAP HANA 환경 프로비저닝</a>의 단계 및 정보를 사용하여 IBM Cloud 인프라를 설정하십시오.</td>
   <tr>
   <td>6. SAP 랜드스케이프 설치</td>
   <td>서버가 온프레미스에 있었던 것과 동일하게 IBM Cloud 인프라에 SAP 랜드스케이프를 설치합니다. 자세한 정보는 <a href="hana-installing-SAP-landscape.html#install_sap">SAP 소프트웨어 및 애플리케이션 다운로드 및 설치</a>를 참조하십시오.</td>
   </td>
   </tr>
   </TBODY>
   </table>
