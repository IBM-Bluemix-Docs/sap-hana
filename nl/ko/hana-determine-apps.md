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


# 3. SAP 애플리케이션 판별

{{site.data.keyword.baremetal_long}}에서 실행하려는 SAP 기반 애플리케이션을 판별해야 합니다. 판별 시 고려해야 할 항목에는 다음이 포함됩니다.

 * 데이터베이스가 어떻게 사용됩니까? SAP HANA가 배치될 수 있는 두 가지 방법이 있습니다. 첫 번째는 SAP NetWeaver 스택에 대한 데이터베이스로 배치하는 것입니다. 이 경우에는 주로 데이터 소스로 사용됩니다. 두 번째 배치 방법은 애플리케이션이 SAP HANA 시스템에 직접 배치된 독립형 모드로 SAP HANA를 실행하는 것입니다. 어느 방법이든 크기 조정 프로세스와 기타 시스템 요구사항 및 종속성은 시스템을 사용하는 방법(개발 및 테스트, 개념 증명 또는 프로덕션)에 따라 달라질 수 있습니다.
 * 애플리케이션을 어떻게 사용하시겠습니까? 개발 및 테스트 또는 프로덕션용으로 사용하시겠습니까? 
 * {{site.data.keyword.cloud_notm}} 가상 사설망(VPN) 서비스(SSL 또는 지점간 터널링 프로토콜(PPTP))를 사용합니까?
  
## 다음 단계

  [4. 서버 크기 조정](/docs/infrastructure/sap-hana/hana-size-server.html)
  
  [5. 구성 판별](/docs/infrastructure/sap-hana/hana-determine-configuration.html)
