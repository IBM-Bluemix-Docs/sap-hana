---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-26"

keywords: SAP HANA, {{site.data.keyword.cloud_notm}}, high availability, highly available, SPOF, VLANs, HA, DR, disaster recovery, SAP NetWeaver

subcollection: sap-hana

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}


# IBM Cloud 고가용성 지원
{: #ha}

{{site.data.keyword.cloud}} IaaS(Infrastructure as a Service)는 고가용성(HA) 솔루션을 지원하는 상단에 선택적 운영 체제(OS) 배치를 통한 강력한 컴퓨팅 환경을 제공합니다. 솔루션은 지원되는 OS 버전을 기반으로 하며 이에 대해서는 [SAP Note 2414097 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://launchpad.support.sap.com/#/notes/2414097){: new_window}에서 설명합니다. HA 솔루션은 배치 시 함께 제공되는 주문된 OS 라이센스 또는 서드파티 라이센스(예: BYOL(Bring Your Own License)로 제한됩니다. 배치 전에 {{site.data.keyword.cloud_notm}} 지원과 HA 세부사항에 대해 논의하십시오.

{{site.data.keyword.cloud_notm}} for SAP에 의해 지원되고 배치되는 운영 체제
* Linux[Red Hat Enterprise Linux(RHEL) 또는 SUSE Enterprise Linux Server(SLES)]는 SAP NetWeaver 및 SAP HANA HA 솔루션을 둘 다 지원합니다. {{site.data.keyword.cloud_notm}} 환경에서는 사소한 제한이 있으며 이에 대해서는 [SAP NetWeaver 고가용성 구성](#overview-configs)에서 논의합니다.
* (SAP HANA 데이터베이스 제한사항으로 인해) Microsoft Windows는 SAP NetWeaver HA 솔루션만 지원합니다.

## SAP NetWeaver 고가용성 구성의 개요
{: #overview-configs}

SAP 서비스용 HA 환경을 계획하고 설치하는 데 심층적인 도움을 제공하는 수많은 문서가 있습니다. 이러한 문서에는 장애 복구, 복제, 스케일 확장 및 재해 복구(DR)에 대한 정보가 포함됩니다. 특정 문서에 대한 참조는 적절한 경우에 제공됩니다.

SAP 배치용 {{site.data.keyword.cloud_notm}}에 의해 지원되는 모든 운영 체제 및 배포판(Windows, Linux RHEL 및 SLES)은 고가용성 소프트웨어 및 특정 확장기능과 함께 제공됩니다. 다음은 지원되는 OS 및 배포판입니다.

* [Windows Server 2012의 새 장애 복구 클러스터링 개선사항 및 SAP NetWeaver 고가용성에 대한 이점 ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://blogs.sap.com/2013/10/16/new-failover-clustering-improvements-in-windows-server-2012-and-its-benefits-for-sap-netweaver-high-availability/){: new_window}은 SAP NetWeaver가 있는 Windows OS에서의 Microsoft Windows Server Failover Clustering(WFSC)을 기반으로 하는 설명을 제공합니다.

* Linux Pacemaker가 있는 Linux 기반의 HA 환경에서 SAP NetWeaver를 배치하는 것에 대한 안내에 대한 두 가지 참조서가 있습니다.
  * SUSE SAP NetWeaver High Availability Cluster 7.40 Setup Guide
  * Deploying Highly Available SAP NetWeaver-based Servers Using Red Hat Enterprise Linux HA add-on with Pacemaker

* [Building High Availability for SAP NetWeaver and SAP HANA on Linux ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://support.sap.com/content/dam/SAAP/SAP_Activate/AGS_70.pdf){: new_window}는 SAP 우수 사례 문서이며 SAP HANA에 중점을 준 심층적인 기술 설명을 제공합니다.

* [SAP NetWeaver High Availability and Business Continuity in Virtual Environments with VMware and Hyper-V on Microsoft Windows ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://www.sap.com/documents/2015/07/508b62bc-5b7c-0010-82c7-eda71af511fa.html){: new_window}는 가상화된 서버에서 HA를 구현할 예정인 경우, 가상화 측면에 대해 설명합니다.

고가용성 시나리오의 경우, SAP 파트너에 의해 인증된 고가용성 제품에 대한 자세한 정보는 [High Availability Partner Information ![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://wiki.scn.sap.com/wiki/display/SI/High+Availability+Partner+Information){: new_window}을 참조하십시오.
비HANA SAP 데이터베이스의 경우, 데이터베이스 문서에서 HA 장애 복구, DR 구성에 대한 더 많은 정보를 볼 수 있습니다.

NFS(Network File System)/CIFS(Common Internet File System) 스토리지에 대한 공유 액세스 또는 iSCSI 기반의 LUNS(Logical Unique Number Storage)에 대한 공유 액세스는 일반적으로 시스템 장애 복구를 지원해야 합니다. 복제 메소드와 결합된 로컬 스토리지는 일반적으로 DR과 같은 설정을 지원해야 합니다. 온프레미스 설치의 경우, 배치를 계획할 때 데이터베이스 제품의 성능 및 대기 시간 요구사항을 확인하십시오.

## 추가 안내
{: #extra-guide}

[쿼럼 기반의 스토리지](#quorum) 및 [네트워크 고려사항](#network)은 배치 동안 고려해야 하는 지침을 제공합니다. 이러한 절에 설명된 고려사항과 별개로, HA 환경에 SAP NetWeaver 및 데이터베이스 시스템을 설치하는 것은 기타 온프레미스 설치와 다르지 않습니다.

### 쿼럼 기반의 스토리지
{: #quorum}

{{site.data.keyword.cloud_notm}} IBM Cloud 환경의 보안 제한사항으로 인해 IPMI(Intelligent Platform Management Interface)를 통한 원격 관리 디바이스에 대한 네트워크 기반의 액세스는 사용 가능하지 않습니다. 클러스터 환경은 일반적으로 항상 쿼럼을 보장하기 위해 "클러스터 노드의 보호"에 대한 IPMI 기반의 컴포넌트를 사용합니다. IPMI 사용 가능 디바이스의 부재 시, 공유 스토리지 디바이스가 사용됩니다. {{site.data.keyword.cloud_notm}} 환경에서 공유 스토리지 디바이스는 iSCSI LUN을 쿼럼 디바이스로서 서버에 배치하여 구현됩니다. 예를 들어, Microsoft Cluster의 경우, FSW(File Share Witness)이며 Linux Pacemaker 솔루션의 경우 SDB(Storage-Based Death)입니다. 
* Linux 고가용성 클러스터 개념에 대한 자세한 정보를 보려면 [여기![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](http://linux-ha.org/wiki/Cluster_Concepts){: new_window}를 클릭하십시오.
* Windows Server 2012 및 Windows Server 2012 R2에 대한 쿼럼 서버를 구성하고 관리하는 데 대한 자세한 정보를 보려면 [여기![외부 링크 아이콘](../../icons/launch-glyph.svg "외부 링크 아이콘")](https://docs.microsoft.com/en-us/windows-server/failover-clustering/manage-cluster-quorum){: new_window}를 클릭하십시오.

{{site.data.keyword.cloud_notm}} 스토리지에는 기본 제공 HA 기능이 있으므로 네트워크 레이아웃 중복을 방지하기 위해 단일 공유 iSCSI LUN이 SPOF(Single Point Of Failure)를 도입하지 않습니다. 단, 특정 클러스터 제품의 경우, 다중 쿼럼 디바이스가 필요할 수 있습니다.

### 네트워크 고려사항
{: #network}

{{site.data.keyword.cloud_notm}} 기반의 설치는 다음 네트워크 구성 중 하나와 함께 제공됩니다.
* 사설 네트워크
* 공용 네트워크
* 공용 네트워크 및 사설 네트워크
* 두 개의 사설 네트워크(특수한 요구가 있는 경우)

온프레미스 설치와 같이 하드웨어의 물리적인 제한에 따라 추가 네트워크 어댑터가 주문될 수 있습니다. 제한사항은 온프레미스 설치의 경우와 동일합니다. 하드웨어 배치 동안 중복 네트워크 어댑터를 주문하면 네트워크 토폴로지에 걸쳐 SPOF를 방지하는 데 도움이 됩니다. 중복 어댑터는 LACP(Link Aggregation Control Protocol)가 있는 장애 복구 구성에서 설정됩니다. Linux의 경우 설정에서 본딩 인터페이스를 사용하며 Microsoft Windows의 경우 팀 어댑터가 사용됩니다. 이러한 어댑터가 연결된 {{site.data.keyword.cloud_notm}} 스위치 인프라가 중복이므로 새 SPOF가 도입되지 않습니다. 중복 인프라가 주문된 VLAN에 의해 사용될 수 있습니다.

DR 설정에서의 복제 시나리오와 같이 네트워크 요구사항에 따라 연결된 디바이스의 위치 및 문제가 되는 제품에 특정한 새 네트워크 요구사항을 확인해야 합니다. 일부 경우에는 {{site.data.keyword.cloud_notm}} 스냅샷 스토리지 기반의 복제가 요구사항을 충족할 수 있습니다. 사용자의 비즈니스 프로세스 요구에 가장 적합한 솔루션을 판별하려면 {{site.data.keyword.cloud_notm}} 지원에 문의하십시오.
