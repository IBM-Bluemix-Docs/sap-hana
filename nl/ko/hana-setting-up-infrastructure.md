---



copyright:
  years: 2017, 2018
lastupdated: "2010-03-05"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 2. 인프라 설정
{: #set_up_infrastructure}

SAP HANA {{site.data.keyword.baremetal_long}}, 네트워크, 보안, 스토리지 및 운영 체제(OS) 설정에 대한 안내는 다음 섹션에 있습니다. 궁금하신 사항은 [{{site.data.keyword.cloud_notm}} 지원 팀](https://console.bluemix.net/docs/get-support/howtogetsupport.html#getting-customer-support)에 문의하십시오.

## 서버 주문
{: order-server}

다음 단계를 사용하여 {{site.data.keyword.baremetal_short}}를 주문하십시오. 고유 신임 정보를 사용하여 [베어메탈 서버 구성](https://console.bluemix.net/docs/bare-metal/configuring.html#configuring-your-bare-metal-server) 아래에서 추가 정보를 찾을 수 있습니다.

1. 고유 신임 정보로 [{{site.data.keyword.cloud_notm}} 인프라 고객 포털](https://control.softlayer.com)에 로그인하십시오.
2. 계정 요약 페이지에서 **디바이스** 아이콘을 클릭하십시오.
3. 디바이스 페이지에서 {{site.data.keyword.baremetal_short}} 아래의 **월별** 링크를 클릭하십시오. 서버 목록 대화 상자가 표시됩니다.
4. SAP 인증 서버는 목록의 맨 위에 있습니다. **월별 시작 가격** 아래의 하이퍼링크를 클릭하여 적절한 서버를 선택하십시오. 그러면 구성/주문 페이지로 이동합니다. SAP HANA 인증 서버는 CPU 모델 아래에서 **-H**로 식별됩니다.  
5. **수량** 필드에 주문 중인 서버의 수를 입력하고 **데이터 센터**를 선택하십시오.
6. 서버 선택사항에 따라 **서버**, **RAM**, **운영 체제** 및 개인용 스토리지 옵션의 기본값이 설정되며 이는 변경할 수 없습니다. 스토리지 크기는 지정된 용량의 RAM이 있는 SAP HANA에 필요한 크기와 일치하도록 조정됩니다. 서버를 주문한 후 {{site.data.keyword.IBM_notm}} {{site.data.keyword.blockstorageshort}} for {{site.data.keyword.cloud_notm}} 또는 {{site.data.keyword.filestorage_full_notm}} 및 NAS(Network Attached Storage)가 주문됩니다.
7. Red Hat 또는 Microsoft 중에서 **운영 체제**를 선택하고 서버에 대한 특정 운영 체제 또는 VMware 하이퍼바이저를 선택하십시오.

## 서버 옵션 선택
{: #select_options}

다음 단계에서는 구성에 추가할 디스크의 수와 유형을 선택합니다. RAID(Redundant Array of Independent Disks) 스토리지 그룹 및 RAID 스토리지 그룹 위의 파티셔닝 레이아웃에 대한 여러 옵션을 선택할 수도 있습니다. 자세한 정보는 [RAID 정보](https://console.bluemix.net/docs/bare-metal/what-raid.html#about-raid} or [{{site.data.keyword.cloud_notm}} Support](https://console.bluemix.net/docs/get-support/howtogetsupport.html#getting-customer-support)를 참조하십시오.

1. **SAP 인증 서버** 아래에서 서버 사용 계획에 따라 선택하십시오. 각 옵션에 대한 세부사항은 [베어메탈 서버 설정](https://console.bluemix.net/docs/bare-metal/configuring.html#setting-up-your-bare-metal-servers)에서 찾을 수 있습니다. 자세한 정보는 [Design Decision Tool](https://github.com/ibm-cloud-architecture/infrastructure-design-decision-tool)(도구로 스크롤) 또는 [{{site.data.keyword.cloud_notm}} 지원 팀](https://console.bluemix.net/docs/get-support/howtogetsupport.html#getting-customer-support)에 문의할 수도 있습니다.
2. 페이지의 맨 아래에서 **주문에 추가**를 클릭하십시오.

## 고급 시스템 구성 설정
{: #adv_config}

1. **고급 시스템 구성** 창의 값에 대한 도움말을 얻으려면 [고급 시스템 구성](https://console.bluemix.net/docs/bare-metal/configuring.html#advanced-system-configuration) 가이드라인에 따르십시오.

SAP 호스트 이름은 최대 13자의 영숫자 문자로 구성되어야 합니다. SAP 호스트 이름에 대한 자세한 정보는 [SAP 노트 611361](https://launchpad.support.sap.com/#/611361) 및 [129997](https://launchpad.support.sap.com/#/129997)을 참조하십시오. 

## 선택사항 확인
{: #confirm_selections}

1. 체크아웃 페이지에서 선택사항을 확인하고 **클라우드 서비스 이용 약관** 및 **써드파티 소프트웨어 계약**을 클릭하십시오.
2. 계정 작성: 청구 입력으로 스크롤하여 **지불 유형, 이름, 카드** 및 비용 청구에 사용될 신용 카드의 **만기**(날짜)를 입력하십시오.
3. **주문 제출**을 클릭하십시오. 주문 번호가 표시된 화면으로 경로 재지정됩니다. 이 화면은 주문 영수증이기도 하므로 화면을 인쇄할 수 있습니다.

_{{site.data.keyword.cloud_notm}} 주문 ##이(가) 제출됨_이라는 제목의 확인 이메일이 프로파일에 있는 이메일 주소로 발송됩니다. 이 이메일은 서버가 승인되었으며 배치 중이라는 알림입니다. 서버가 배치된 후에는 서버가 사용 가능하며 [{{site.data.keyword.cloud_notm}} 인프라 고객 포털](https://control.softlayer.com)을 통해 관리할 수 있음을 알리는 다른 알림이 발송됩니다.

## 다음 단계

이제 {{site.data.keyword.baremetal_short}} 관리를 시작할 준비가 되었습니다. [SAP HANA 환경 관리](/docs/infrastructure/sap-hana/hana-manage-environment.html)를 참조하십시오.

