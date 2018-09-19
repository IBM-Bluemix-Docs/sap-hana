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


# 4. 서버 크기 조정
{: #size_the_server}

사용할 SAP 솔루션을 결정한 후 다음 단계는 SAP 랜드스케이프를 지원하는 데 필요한 {{site.data.keyword.baremetal_long}}의 수를 판별하고 서버의 크기가 올바르게 조정되었는지를 확인하는 것입니다.
{: shortdesc}

## SAP 크기 조정 방법론 이해
{: #size_method}

SAP HANA는 총 RAM 크기가 다음과 같은 단일 노드 구성의 {{site.data.keyword.cloud_notm}}에 제공됩니다. 
  * 512GB
  * 1,024GB(1TB)
  * 2,048GB(2TB)
  * 4,096GB(4TB)
  * 8,192GB(8TB)
  
이는 일반적으로 기존의 행 기반 관계형 데이터베이스 관리 시스템(RDMS)에 비해 데이터를 저장하는 데 더 적은 공간이 필요한 열 형식 데이터베이스입니다. 데이터는 고도로 압축될 수 있으며 압축 비율은 소스 데이터 및 데이터베이스에 따라 3:1에서 10:1 이상의 범위일 수 있습니다. 

크기 조정은 프로젝트 성공의 핵심 요소이므로 서버를 구매하기 *전에* 올바르게 크기를 조정해야 합니다. 메모리 또는 스토리지 요구사항의 크기를 잘못 조정하면 더 큰 서버로 업그레이드 또는 마이그레이션될 수 있습니다.

## SAP Quick Sizer 액세스
{: #quick_sizer}

주 메모리는 SAP HANA 인증 어플라이언스의 크기를 조정할 때 가장 중요한 리소스 중 하나입니다. 공용 [*SAP HANA Master Guide*](https://help.sap.com/doc/e95f6750b0fd10148ea5c6be75016694/2.0.00/en-US/SAP_HANA_Master_Guide_en.pdf)에서 크기 조정 관련 주제에 대한 시작점을 제공합니다. 이 안내서의 [Sizing SAP HANA](https://help.sap.com/viewer/eb3777d5495d46c5b2fa773206bbfb46/2.0.00/en-US/d4a122a7bb57101493e3f5ca08e6b039.html) 정보에서 SAP HANA 시스템의 크기를 조정하는 방법에 대한 지침을 제공합니다. 새로운 설치 및 기존 시스템 모두에 대한 여러 설치 및 마이그레이션 시나리오를 가리킵니다. SAP Quick Sizer 도구의 SAP HANA 버전에 대한 링크가 있습니다(도구에 액세스하려면 SAP S-사용자 ID가 필요함). 또한 이 페이지에는 SAP HANA 서버 크기 조정과 관련된 SAP 노트가 나열되어 있습니다. 

## 가상화된 환경에 대한 크기 조정
{: #size_virtual}

가상화된 환경에서 SAP HANA를 실행하는 경우 추가 크기 조정 고려사항은 [VMware ESXi 서버 배치](/docs/infrastructure/sap-hana/hana-considerations.html#vmware-server) 및 [*Architecture Guidelines and Best Practices for Deployments of SAP HANA on VMware vSphere Architecture and Technical Considerations Guide*](https://www.vmware.com/content/dam/digitalmarketing/vmware/en/pdf/whitepaper/sap_hana_on_vmware_vsphere_best_practices_guide-white-paper.pdf)를 참조하십시오.

## 다음 단계

 [5. 구성 판별](/docs/infrastructure/sap-hana/hana-determine-configuration.html)
