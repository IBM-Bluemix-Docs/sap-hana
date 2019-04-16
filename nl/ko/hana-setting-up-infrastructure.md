---

copyright:
  years: 2017, 2019
lastupdated: "2019-02-28"

keywords: SAP HANA, {{site.data.keyword.cloud_notm}}, infrastructure, {{site.data.keyword.baremetal_short}}, SAP-certified infrastructure, deployment, BYOL,

subcollection: sap-hana

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}

# 2. 인프라 설정
{: #set_up_infrastructure}

SAP HANA {{site.data.keyword.baremetal_long}}, 네트워크, 보안, 스토리지 및 운영 체제(OS) 설정에 대한 안내는 다음 섹션에 있습니다. 궁금하신 사항은 [{{site.data.keyword.cloud_notm}} 지원 팀](/docs/get-support?topic=get-support-getting-customer-support#getting-customer-support)에 문의하십시오.

## 서버 주문
{: order-server}

다음 단계를 사용하여 {{site.data.keyword.baremetal_short}}를 주문하십시오. 추가 정보는 [사용자 설치 베어메탈 서버 빌드](/docs/bare-metal?topic=bare-metal-ordering-baremetal-server#ordering-baremetal-server)에서 찾을 수 있습니다. 

1. 고유 인증 정보를 사용하여 [{{site.data.keyword.cloud_notm}} 인프라 고객 포털![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://control.softlayer.com){: new_window}에 로그인하십시오.
2. 계정 요약 페이지에서 **계정** > **주문하기**를 클릭하십시오.
3. 디바이스 페이지에서 {{site.data.keyword.baremetal_short}} 아래의 **월별** 링크를 클릭하십시오. 서버 목록이 표시됩니다. SAP 인증 서버는 목록의 맨 위에 있습니다.
4. **월별 시작 가격** 아래의 하이퍼링크를 클릭하여 적절한 서버를 선택하십시오. 그러면 구성/주문 페이지로 이동합니다. SAP HANA 인증 서버는 CPU 모델 아래에서 **-H**로 식별됩니다.  

BI.S3.H2192 및 BI.S3.H238 서버 또한 **시간별** 청구용으로 사용 가능합니다.
{: note}

5. **수량** 필드에 주문 중인 서버의 수를 입력하고 **데이터 센터**를 선택하십시오.
6. 서버 옵션에 따라 **서버**, **RAM** 및 개인용 스토리지 옵션의 기본값이 설정되며 이는 변경할 수 없습니다. 서버를 주문한 후 {{site.data.keyword.IBM_notm}} {{site.data.keyword.blockstorageshort}} for {{site.data.keyword.cloud_notm}} 또는 {{site.data.keyword.filestorage_full_notm}} 및 NAS(Network Attached Storage)가 주문됩니다.
7. Red Hat 또는 SUSE 중에서 **운영 체제**를 선택하고 서버에 대한 특정 운영 체제 또는 VMware 하이퍼바이저를 선택하십시오.

운영 체제에 대해 BYOL(Bring Your Own License)을 이용 중이면 **기타** > **운영 체제 없음**을 선택하십시오. 자세한 정보는 [BYOL(Bring Your Own License)](#byol)을 참조하십시오.
{ :note}

## 서버 옵션 선택
{: #select_options}

다음 단계에서는 구성에 추가할 디스크의 수와 유형을 선택합니다. RAID(Redundant Array of Independent Disks) 스토리지 그룹 및 RAID 스토리지 그룹 위의 파티셔닝 레이아웃에 대한 여러 옵션을 선택할 수도 있습니다. 자세한 정보는 [RAID 정보](/docs/bare-metal?topic=bare-metal-about-raid#about-raid) 또는 [{{site.data.keyword.cloud_notm}} 지원](/docs/get-support?topic=get-support-getting-customer-support#getting-customer-support)을 참조하십시오.

1. **SAP 인증 서버** 아래에서 서버 사용 계획에 따라 선택하십시오. 자세한 정보는 [Design Decision Tool![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://github.com/ibm-cloud-architecture/infrastructure-design-decision-tool){: new_window}(아래로 스크롤하여 도구로 이동) 또는 [{{site.data.keyword.cloud_notm}} 지원](/docs/get-support?topic=get-support-getting-customer-support#getting-customer-support)에 문의하십시오. 
2. 페이지의 맨 아래에서 **주문에 추가**를 클릭하십시오.

## 고급 시스템 구성 설정
{: #adv_config}

1. **고급 시스템 구성** 창의 값에 대한 도움말을 얻으려면 [고급 시스템 구성](/docs/bare-metal?topic=bare-metal-ordering-baremetal-server#ordering-baremetal-server) 가이드라인에 따르십시오.

SAP 호스트 이름은 최대 13자의 영숫자 문자로 구성되어야 합니다. SAP 호스트 이름에 대한 자세한 정보는 [SAP Notes 611361 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://launchpad.support.sap.com/#/611361){: new_window} 및 [129997 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://launchpad.support.sap.com/#/129997){: new_window}을 참조하십시오.

## 선택사항 확인
{: #confirm_selections}

1. 체크아웃 페이지에서 선택사항을 확인하고 **클라우드 서비스 이용 약관** 및 **서드파티 소프트웨어 계약**을 클릭하십시오.
2. 계정 작성: 청구 입력으로 스크롤하여 **지불 유형, 이름, 카드** 및 비용 청구에 사용될 신용 카드의 **만기**(날짜)를 입력하십시오.
3. **주문 제출**을 클릭하십시오. 주문 번호가 표시된 화면으로 이동합니다. 이 화면은 주문 영수증이기도 하므로 화면을 인쇄할 수 있습니다.

_{{site.data.keyword.cloud_notm}} 주문 ##이(가) 제출됨_이라는 제목의 확인 이메일이 프로파일에 있는 이메일 주소로 발송됩니다. 이 이메일은 서버가 승인되었으며 배치 중이라는 알림입니다. 서버가 배치되고 나면 서버가 사용 가능하며 [{{site.data.keyword.cloud_notm}} 인프라 고객 포털![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://control.softlayer.com){: new_window}을 통해 관리할 수 있음을 알리는 또 다른 알림이 발송됩니다.

## BYOL(Bring Your Own License)
{: #byol}

자체 운영 체제 라이센스가 있는 경우 벤더의 지시사항에 따라 {{site.data.keyword.baremetal_short}}에 이를 설치합니다. 자세한 정보는 [OS 없음 옵션](/docs/bare-metal?topic=bare-metal-how-to-install-an-operating-system-on-a-no-os-server-#bm-no-os)을 참조하십시오.

## 다음 단계

이제 {{site.data.keyword.baremetal_short}} 관리를 시작할 준비가 되었습니다. 다음 단계는 [SAP HANA 환경 관리](/docs/infrastructure/sap-hana?topic=sap-hana-manage_environment#manage_environment)를 참조하십시오.
