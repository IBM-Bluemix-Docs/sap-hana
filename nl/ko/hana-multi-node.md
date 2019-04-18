---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-26"

keywords: SAP HANA, {{site.data.keyword.cloud_notm}}, SAP ABAP, LACP, KPIs,VLANs

subcollection: sap-hana

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}

# 5. SAP HANA 다중 노드를 지원하도록 IBM Cloud 인프라 구성
{: #multi-node-storage}

{{site.data.keyword.cloud}}는 OLAP(Online Analytical Processing) 워크로드에 맞는 SAP HANA 다중 노드 스토리지(예: SAP Business Warehouse(SAP BW) 및 SAP BW/4HANA)를 지원합니다. SAP HANA 다중 노드에 대한 {{site.data.keyword.cloud_notm}} 솔루션은 하나의 시스템에 사용되는 최대 30TB의 메모리에 대한 최대 15+1개의 노드(15개의 작업자 노드와 한 개의 대기 노드)로 구성됩니다.

다중 노드를 사용하면 다중 SAP HANA 노드가 단일 SAP HANA 시스템을 빌드합니다. 데이터는 이러한 노드 간에 분배되며, 이러한 노드는 단일 데이터베이스를 형성합니다. 다중 노드 구성은 대기 구성을 통해 확장성과 고가용성을 지원합니다. 이 구성에 대한 {{site.data.keyword.cloud_notm}} 오퍼링은 [SAP HANA TDI(Tailored Data Center Integration)![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://blogs.saphana.com/2015/02/18/sap-hana-tailored-data-center-integration-tdi-overview/){: new_window}를 따르며 중앙 집중식 공유 엔터프라이즈 스토리지를 위해 {{site.data.keyword.cloud_notm}} SAP-HANA 인증 서버를 사용합니다.

[다중 노드 시스템 주문](#ordering)에 설명된 구성 가이드라인에 따라 SAP HANA TDI 요구사항을 충족해야 하고 이는 SAP에서 지원되어야 합니다.
{: note}

[SAP HANA 크기 조정![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://help.sap.com/viewer/eb3777d5495d46c5b2fa773206bbfb46/2.0.00/en-US/d4a122a7bb57101493e3f5ca08e6b039.html){: new_window}의 가이드라인에 따라 배치에 필요한 메모리 및 스토리지의 총 크기를 포함한 대상 SAP HANA 시스템의 필수 크기를 판별하십시오. 크기 조정 요구사항을 사용하여 SAP HANA 다중 노드 시스템에 필요한 SAP HANA 노드의 수 및 데이터 호스팅에 필요한 스토리지를 설정할 수 있습니다.

## 네트워크 토폴로지 및 스토리지 레이아웃 검토
{: #reviewing-topology}

그림 1에서는 {{site.data.keyword.cloud_notm}} IaaS(Infrastructure as a Service) SAP HANA TDI 설정에 필요한 네트워크 토폴로지를 보여줍니다.

그림 1. IBM Cloud IaaS(Infrastructure as a Service) SAP HANA TDI 네트워크 토폴로지

![그림 1. IBM Cloud IaaS(Infrastructure as a Service) SAP HANA TDI 네트워크 토폴로지](/images/SAP-BW.png "IBM Cloud IaaS(Infrastructure as a Service) SAP HANA TDI 네트워크 토폴로지")

## 전제조건 설정
{: #prerequisites}

SAP HANA 다중 노드에서는 작동을 위해 특정 네트워크가 있어야 합니다. 시스템의 다른 컴포넌트를 주문하기 전에 이러한 네트워크가 데이터베이스 노드와 함께 올바르게 설정되어 있어야 합니다. 다음이 필요합니다.
* 클라이언트 측 네트워크. SAP Advanced Business Application Programming(SAP ABAP) 애플리케이션 서버, SAP HANA Studio 클라이언트 및 다른 모든 네트워크 클라이언트를 다중 노드 시스템에 연결합니다. 네트워크 처리량 및 가용성 옵션은 SAP HANA 다중 노드 시스템의 사용 시나리오에 따라 다릅니다. 애플리케이션에 필요한 가용성 핵심성과지표(KPI)와 SAP HANA 데이터베이스에서/로 전송되는 데이터 양을 고려하십시오.
* 스토리지 네트워크. 백엔드 {{site.data.keyword.blockstoragefull}} 및 {{site.data.keyword.filestorage_full_notm}}에 연결해야 합니다. 성능 및 중복성을 최대화하려면 LACP(Link Aggregation Control Protocol) 사용 Linux 본딩 아래 두 개의 인터페이스가 있는 10Gb 네트워크가 필요합니다. SAP HANA 크기 조정 가이드라인에서 제공되는 성능 지수가 없으면 SAP HANA TDI KPI를 충족할 수 없습니다.
* 스토리지 네트워크와 동일하게 설정된 SAP HANA 내부 통신용 인터노드 네트워크. 인터노드 네트워크는 오퍼레이션 중에 노드 간에 필요한 데이터 전송과 노드 간 통신에만 사용됩니다. 이 필수 네트워크 구성은 LCAP 사용 Linux 본딩 아래 두 개의 실제 10Gb 어댑터에 있습니다.

## 다중 노드 시스템 주문
{: #ordering}

SAP에 필요한 성능 및 처리량 KPI를 충족하려면 VLAN, 스토리지 및 컴퓨팅 노드를 동일한 데이터 센터에서 주문해야 합니다. 컴포넌트가 다중 데이터 센터에 분배되는 경우 SAP는 다중 노드 시스템을 지원하지 않습니다.

1. 네 개의 어댑터(두 개는 개인용, 두 개는 공용)가 있는 세 개의 서로 다른 VLAN 및 서버를 주문하십시오. VLAN 주문에 대한 자세한 정보는 [1단계 기본 및 공용 VLAN 주문](/docs/infrastructure/virtualization?topic=Virtualization-advanced-single-site-vmware-reference-architecture#step-1-ordering-primary-public-and-private-vlans)을 참조하십시오. 서버 주문에 대한 자세한 정보는 [인프라 설정](/docs/infrastructure/sap-hana?topic=sap-hana-set_up_infrastructure#set_up_infrastructure#set_up_infrastructure)을 참조하십시오.
2. 초기 사설 VLAN을 "스토리지 VLAN"으로 설정하십시오.
3. {{site.data.keyword.cloud_notm}} (a)두 번째 VLAN으로 공용 인터페이스 이동 및 (b)세 번째 VLAN(클라이언트 VLAN)에 지정할 둘 이상의 어댑터 주문으로 [티켓을 여십시오](/docs/get-support?topic=get-support-open-case#open-case).

크기 조정에 따른 서버 수가 있으며 네트워크는 다음을 위해 설정됩니다.
* 스토리지를 모든 노드에 접속할 수 있습니다.
* 스토리지 접속 후 SAP HANA 다중 노드 설치를 수행할 수 있습니다.

스토리지 LAN 연결 및 인터노드 연결은 {{site.data.keyword.cloud_notm}} 배치를 통해 구성됩니다. 각각 장애 복구 구성이 있는 두 개의 10Gb 어댑터에 대한 연결을 주문하십시오. 이 설정은 올바른 Linux 본딩 및 LACP 구성을 보장합니다. 질문이 있는 경우 {{site.data.keyword.cloud_notm}} 지원 팀에 문의하십시오.

연결된 NFS(Network File System) 볼륨에서 충족해야 하는 특정 성능 기준이 있습니다(자세한 정보는 [{{site.data.keyword.filestorage_short}} 시작하기](/docs/infrastructure/FileStorage?topic=FileStorage-getting-started#getting-started) 참조). `/data/` 볼륨의 경우, 테스트에 의하면 성능 KPI가 10IOPS/GB인 2TB Endurance 스토리지가 각 작업자 노드에 필요합니다. 동일한 크기의 하나의 추가 볼륨이 SAP HANA `/shared/` 볼륨으로 필요하며 모든 노드에서 공유됩니다. 테스트에 의하면 `/shared/` 볼륨이 12 IOPS/GB의 성능 스토리지 볼륨이어야 합니다.

로그 볼륨의 경우, 하나의 512GB 볼륨의 Performance 스토리지가 성능 KPI가 10K IOPS인 각 노드에 필요합니다.

[{{site.data.keyword.blockstorageshort}} 프로비저닝 및 관리](/docs/infrastructure/BlockStorage?topic=BlockStorage-getting-started#getting-started) 또는 [{{site.data.keyword.filestorage_full_notm}} 프로비저닝 및 관리](/docs/infrastructure/FileStorage?topic=FileStorage-orderingConsole#orderingConsole)의 단계를 사용하여 Endurance 및 Performance 스토리지를 주문할 수 있습니다.

## SAP HANA 다중 노드 구성
{: #configuring}

SAP HANA 공유 볼륨 및 각 데이터와 로그 볼륨은 모든 노드에서 액세스 가능해야 합니다. 이러한 방식은 모든 볼륨이 [다중 노드 시스템 주문](#ordering)에서 구성한 전체 스토리지 VLAN에서 액세스 가능함을 의미합니다. 관련된 각 IP 주소를 나열하지 않으려면 볼륨이 VLAN의 전체 IP 서브넷에서 액세스 가능하도록 설정하십시오.

[SAP HANA on NetApp FAS Systems with NFS ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.netapp.com/us/media/tr-4290.pdf){: new_window}의 안내에 따라 SAP HANA 다중 노드 시스템을 구성하십시오. 각 볼륨을 마운트하려면 다음 NFS(Network File System) 마운트 옵션을 사용하십시오.

`/etc/fstab`의 `rw,bg,hard,timeo=600,intr,noatime,vers=4,minorversion=1,lock,rsize=1048576,wsize=1048576`.

이러한 옵션은 NetApp 및 {{site.data.keyword.cloud_notm}}에서 테스트되었습니다. 마운트 옵션 또는 값을 변경하려는 경우 {{site.data.keyword.cloud_notm}} 지원에 문의하십시오.

모든 노드로 모든 볼륨을 마운트한 후 다중 노드 서버가 구성되어 SAP HANA 다중 노드 데이터베이스를 설치할 준비가 됩니다. [SAP HANA 서버 설치 및 업데이트 안내서![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://help.sap.com/viewer/2c1988d620e04368aa4103bf26f17727/2.0.03/en-US){: new_window}의 단계에 따라 필수 버전의 SAP HANA 데이터베이스를 설치하십시오.
