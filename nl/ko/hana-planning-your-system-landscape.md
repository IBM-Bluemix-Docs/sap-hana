---



copyright:
  years: 2017, 2018
lastupdated: "2018-05-30"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 시스템 랜드스케이프 계획
{: #planning-your-system-landscape}

SAP *랜드스케이프*는 일반적으로 개발, 품질 및 테스트와 프로덕션을 포함하는 둘 이상의 SAP *시스템*으로 이루어진 그룹입니다. 하나의 SAP 시스템은 동시에 시작되고 중지되는 프로세스의 그룹인 하나 이상의 *SAP 인스턴스*로 구성됩니다. SAP 랜드스케이프에 대한 자세한 정보는 [*SAP Business Suite on IBM X6 Systems Reference Architecture*](https://lenovopress.com/redp5073.pdf)를 참조하십시오. 
{: shortdesc}

시장의 모든 SAP 솔루션에는 여러 가능한 랜드스케이프 구성(예: 서버 (크기)/스토리지 (크기))이 있습니다. 이러한 솔루션에는 SAP NetWeaver 기반 제품(예: [SAP Business Suite](https://open.sap.com/courses/suitehana1)), SAP Business Warehouse 및 {{site.data.keyword.cloud}} SAP 인증 인프라의 서버에서 지원하는 모든 특정 SAP 추가 기능이 포함됩니다. 유의해야 할 추가 솔루션은 SAP와 통합될 수 있는 써드파티 소프트웨어입니다. 

SAP HANA는 사용 시나리오에 따라 SAP NetWeaver 스택 기반 솔루션용 데이터베이스 또는 독립형 엔티티로 실행될 수 있습니다. 두 시나리오 모두 {{site.data.keyword.cloud_notm}} 오퍼링은 해당 서버 주위의 랜드스케이프가 다른 서버에서 빌드될 수 있는 사전 구성된 SAP NetWeaver 인증 서버를 제공합니다.

실행하려는 애플리케이션, 잠재적인 성장 및 성능을 기반으로 서버의 크기를 판별할 때 가능한 세부적으로 수행하려고 합니다. 또한 애플리케이션에 대한 스토리지 및 메모리 요구사항에 유의하십시오. 랜드스케이프의 SAP 시스템에는 각 SAP 시스템 간이나 외부 시스템으로의 연결에 대한 특정 요구사항이 있습니다. 자세한 정보는 [SAP 랜드스케이프 계획 시 고려해야 할 항목](/docs/infrastructure/sap-hana/hana-considerations.html)을 참조하십시오.

표 1에는 계획 프로세스 내의 단계가 포함되어 있습니다. 이 표를 사용하여 대상 SAP 랜드스케이프를 빌드하는 데 도움을 받으십시오.

표 1. 계획 프로세스 개요

|단계 |세부사항 |
| --- | --- |
|1 |[SAP 및 {{site.data.keyword.cloud_notm}} 신임 정보를 가져오고 계정 작성](/docs/infrastructure/sap-hana/hana-get-credentials.html) |
|2 |[관련 SAP 및 {{site.data.keyword.cloud_notm}} 문서 검토](/docs/infrastructure/sap-hana/hana-review-doc.html) |
|3 |[SAP 애플리케이션 판별](/docs/infrastructure/sap-hana/hana-determine-apps.html) |
|4 |[서버 크기 조정](/docs/infrastructure/sap-hana/hana-size-server.html) |
|5 |[구성 판별](/docs/infrastructure/sap-hana/hana-determine-configuration.html) |

## 다음 단계

표 1에서 해당 단계를 선택하여 SAP 랜드스케이프 계획을 시작하십시오.
