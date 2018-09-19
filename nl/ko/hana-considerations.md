---



copyright:
  years: 2017, 2018
lastupdated: "2018-06-07"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# SAP 랜드스케이프 계획 시 고려해야 할 항목
{: #considerations}

랜드스케이프의 SAP 시스템에는 각 SAP 시스템 간이나 외부 시스템으로의 연결에 대한 특정 요구사항이 있습니다. 또한 사용자의 랜드스케이프에 맞는 외부 스토리지와 서버에 VMware를 배치하도록 결정한 경우 수행할 작업에 대해 고려해야 합니다.

## 네트워크 연결
{: #network_connectivity}

[{{site.data.keyword.cloud_notm}} 네트워크](/docs/infrastructure/sap-hana/hana-about.html#ibm_cloud_network)에서 네트워크 연결에 대한 {{site.data.keyword.cloud}} 접근 방식의 개요를 제공했습니다. 네트워크 연결 문제는 시스템 사용 방법에 관계없이 적절하게 계획하지 않으면 프로젝트의 상당한 지연을 초래할 수 있습니다. 

일반적으로 IaaS에서 프로비저닝된 {{site.data.keyword.cloud_notm}} 서버에는 두 가지 인터페이스 선택사항이 있습니다. 첫 번째는 공인 IP를 사용하는 외부인터페이스입니다. 두 번째는 RFC(Request for Comment) 1918에 따라 "사설 IP"와 함께 제공되는 내부 인터페이스입니다. "사설 IP"를 사용하는 단일 내부 인터페이스를 선택할 수도 있습니다. 외부 IP가 더 사용하기 쉽지만 기본 방화벽이 설치되고 사전 구성된 경우에도 잠재적인 위험이 있습니다.

두 번째 옵션은 {{site.data.keyword.cloud_notm}} 인프라 고객 포털을 통해 {{site.data.keyword.cloud_notm}} 가상 사설망(VPN)에 액세스하거나 랜드스케이프에 보안 디바이스를 배치합니다. 보안 디바이스는 방화벽, 네트워크 주소 변환, VPN 액세스 및 기타 네트워크 기능을 위해 제공됩니다. 랜드스케이프의 레이아웃과 SAP 애플리케이션 계층에 필요한 연결이 판별된 후 네트워킹 부서에서 [{{site.data.keyword.cloud_notm}} 지원 팀](https://console.bluemix.net/docs/get-support/howtogetsupport.html#getting-customer-support)과 논의하는 것이 좋습니다.

### VLAN
{: #vlans}

랜드스케이프에서 여러 유형의 네트워크 트래픽을 분리하려는 경우 추가 가상 LAN (VLAN)을 주문할 수 있습니다. 추가 VLAN을 사용할 때 성능이 향상되지 않고 트래픽 분리만 발생할 수 있음에 유의하십시오. 일반적으로 SAP에서는 애플리케이션 서버와 SAP HANA 데이터베이스 간의 트래픽 및 SAP Business Intelligence와 같은 다른 SAP HANA 클라이언트에 대해 10Gb 네트워크를 사용하도록 권장합니다. SAP HANA 서버에 대한 관리 액세스를 다른 클라이언트로부터 분리하려면 사용자 랜드스케이프에 대한 다른 VLAN을 주문해야 합니다. 
또 다른 옵션은 공용 및 사설 네트워크를 통해 트래픽을 분리하는 것입니다. 추가 "물리적" 업링크가 {{site.data.keyword.cloud_notm}}에서 지원되지 않기 때문입니다. [SAP HANA Tailored Data Center Integration(TDI)](https://blogs.saphana.com/2015/02/18/sap-hana-tailored-data-center-integration-tdi-overview/)에 대한 SAP의 권장사항에 따르십시오.

점프 박스에서 액세스하고 VPN을 통해 액세스하면 SAP HANA Studio에서 SAP HANA 인스턴스에 액세스할 수 있습니다.

## 외부 스토리지
{: #external_storage}

로컬 스토리지 이외에 백업을 수행하기 위한 추가 외부 스토리지가 필요할 수 있습니다. 이러한 요구사항을 위해 [스토리지](/docs/infrastructure/sap-hana/hana-general-iaas-concepts.html#storage)에 설명된 대로 블록 스토리지 또는 NAS(Network Attached Storage)를 주문할 수 있습니다. 추가 블록 스토리지 및 NFS(Network File System) 데이터는 다른 모든 네트워크 트래픽과 동일한 물리적 어댑터를 통해 전송되므로 이러한 영향에 유의해야 합니다. 

외부 스토리지의 경우 스토리지 솔루션에 대해 결정하기 전에 프로젝트 요구사항을 계산하는 것이 중요합니다. SAP HANA 시스템을 복원해야 하는 경우 스토리지의 IOPS가 복원 기간에 상당한 영향을 미칩니다. SAP HANA를 구성하는 방법에 관계없이 모든 백업은 온라인 백업이므로 SAP HANA에는 백업 기간이 중요하지 않습니다.

예를 들어, {{site.data.keyword.cloud_notm}} {{site.data.keyword.blockstorageshort}}를 사용하는 경우 최대 속도로 약 12TB의 SAP HANA 복원에 대해 계산할 수 있습니다. 디바이스당 최대 크기는 4TB이므로 세 개의 물리적 스토리지 디바이스(블록 스토리지 iSCSI LUN)를 작성해야 합니다. Linux 논리적 볼륨 관리자(LVM)를 사용하여 이러한 세 개의 디바이스에 걸쳐 스트라이프를 작성하고 하나의 12TB 논리 디바이스를 작성할 수 있습니다. 

12TB는 3 x 10 IOPS/GB를 허용하며, 16KB에서 총 122,880 IOPS/GB입니다. 이는 초당 1.875GB의 복원 시간 또는 2시간 미만의 전체 복원 시간을 제공합니다. IOPS에 대한 측정은 읽기 및 쓰기가 50/50 분포로 수행되므로 이 수를 복원 성능의 하한으로 간주할 수 있습니다. 특정 복원 기간에 의존하는 경우 백업 및 복원 테스트를 수행하는 것이 좋습니다.

{{site.data.keyword.cloud_notm}} {{site.data.keyword.blockstorageshort}}, {{site.data.keyword.filestorage_full_notm}} 또는 NAS는 서버에 설치된 추가 소프트웨어 컴포넌트에 대한 스토리지 또는 백업 공간으로 사용될 수 있습니다. 그러나 {{site.data.keyword.cloud_notm}} Storage 및 NSA는 SAP HANA에 대한 스토리지로 사용될 수 없습니다. 이러한 옵션은 KPI 기준을 충족하지 않기 때문입니다.

자세한 정보는 [{{site.data.keyword.blockstorageshort}} 시작하기](https://console.bluemix.net/docs/infrastructure/BlockStorage/index.html#getting-started-with-block-storage) 및 [{{site.data.keyword.filestorage_full_notm}} 시작하기](https://console.bluemix.net/docs/infrastructure/FileStorage/index.html#getting-started-with-file-storage)를 참조하십시오.

## 고가용성 및 재해 복구 시나리오
{: #ha_dr}

{{site.data.keyword.cloud_notm}} 환경은 사전 구성된 고가용성(HA) 시나리오를 지원하지 않습니다. 그러나 Red Hat Enterprise Linux HA 확장기능을 통해 SAP HANA용 HA 솔루션을 구현할 수 있습니다(예: 온프레미스 사례).

SAP HANA 시스템 복제는 하나의 서버에서 복제본으로의 자동화된 장애 복구로 구성될 수 있습니다. 시스템 복제에 대한 SAP 문서에 따라 애플리케이션 시나리오 및 재해 복원력 레벨에 가장 적합한 복제 모드를 판별하십시오. 복제 모드에 따라 다른 네트워크 KPI를 충족해야 합니다. 네트워크 처리량 및 대기 시간에 대한 SAP의 권장사항을 참조하여 선택한 오퍼레이션 모드에 필요한 처리량 및 최대 대기 시간을 판별하십시오. {{site.data.keyword.cloud_notm}} 네트워크 토폴로지가 모든 필수 구성을 제공할 수 있어야 합니다. 확실하지 않거나 다른 데이터 센터의 재해 복구 사이트가 최대 재해 복원력을 달성하도록 하려는 경우 {{site.data.keyword.cloud_notm}} 지원 센터에 문의하여 시나리오에 대한 최적의 설정을 판별하십시오.

SAP HANA 스케일 확장(다중 노드)은 여전히 평가 중입니다. 즉, SAP HANA에 대한 대기 노드는 {{site.data.keyword.cloud_notm}} 환경에서 현재 옵션이 아닙니다.

고가용성 및 재해 복구에 대한 자세한 정보는 [고가용성](https://console.bluemix.net/docs/infrastructure/sap-reference-architecture/sap-ra-recommendations.html#availability) 및 [재해 복구](https://console.bluemix.net/docs/infrastructure/sap-reference-architecture/sap-ra-recommendations.html#dr)를 참조하십시오.

시스템 복제와 네트워크 처리량 및 대기 시간에 대한 자세한 정보는 다음을 참조하십시오.
  * [How To Perform System Replication for SAP HANA](https://www.sap.com/documents/2013/10/26c02b58-5a7c-0010-82c7-eda71af511fa.html)
  * [Network Required for SAP HANA System Replication](https://www.sap.com/documents/2014/06/babb2b55-5a7c-0010-82c7-eda71af511fa.html)

Linux 운영 체제의 HA 클러스터 확장기능 설정에 대한 자세한 정보는 다음을 참조하십시오.
  * [Automated SAP HANA System Replication with Pacemaker on RHEL Setup Guide](https://access.redhat.com/articles/1466063)
  * [SAP HANA SR Performance Optimized Scenario](https://www.suse.com/docrep/documents/ir8w88iwu7/suse_linux_enterprise_server_for_sap_applications_12_sp1.pdf)

## VMware ESXi 서버 배치
{: #vmware_server}

{{site.data.keyword.cloud_notm}} SAP HANA 오퍼링의 모든 서버는 SAP HANA를 가상 머신(VM)에 배치할 수 있도록 하는 VMware ESX에 대해 인증되었습니다. 서버를 VMware ESX와 함께 주문하면 사전 설치되고 기본적으로 구성된 ESX 인스턴스와 함께 배치됩니다. VM은 배치되지 않습니다. ESX 기반 배치에서 올바른 게스트 운영 체제를 배치하는 것은 사용자의 책임입니다. SAP 노트 2414820에 정의된 지시사항에 따라 {{site.data.keyword.cloud_notm}}의 SAP HANA에 지원되는 운영 체제 버전을 선택하십시오.

ESX 기반 배치의 크기 조정 프로세스는 베어메탈 서버 배치의 크기 조정 프로세스와 다릅니다. *Architecture Guidelines and Best Practices for Deployments of SAP HANA on VMware vSphere Architecture and Technical Considerations Guide*의 권장사항에 따르십시오. *Architecture...and Considerations Guide*의 규칙에 따라 가상화 계층에 대한 오버헤드를 계산해야 합니다. 게스트 운영 체제가 VM에 배치된 후 SAP HANA TDI KPI가 충족되었는지 확인하십시오. 환경이 SAP 지원의 전제조건을 준수하는지 테스트하는 데 대한 세부사항은 SAP 노트 1943937을 확인하십시오. 특정 서버에 배치된 모든 VM에 대한 전제조건이 완료되어야 합니다.

가상화된 환경에서 SAP HANA를 배치하려면 몇 가지 다른 SAP 정의 규칙을 따라야 합니다. 프로덕션의 경우 SAP 노트 1995460에 설명된 제한사항을 따르십시오. SAP 노트 2024433에는 하나의 서버에 있는 여러 VM에 대한 규칙이 설명되어 있습니다.

자세한 정보는 다음 문서를 참조하십시오.
  * [SAP 노트 2414820](https://launchpad.support.sap.com/#/notes/2414820)
  * [*Architecture Guidelines and Best Practices for Deployments of SAP HANA on VMware vSphere Architecture and Technical Considerations Guide*](https://www.vmware.com/content/dam/digitalmarketing/vmware/en/pdf/whitepaper/sap_hana_on_vmware_vsphere_best_practices_guide-white-paper.pdf)
  * [SAP 노트 1943937](https://launchpad.support.sap.com/#/notes/1943937)
  * [SAP HANA Tailored Data Center Integration Frequently Asked Questions](https://www.sap.com/documents/2016/05/e8705aae-717c-0010-82c7-eda71af511fa.html)
  * [SAP 노트 1995460](https://launchpad.support.sap.com/#/notes/1995460)
  * [SAP 노트 2024433](https://launchpad.support.sap.com/#/notes/2024433)
  * [SAP HANA Tailored Data Center Intgration (TDI) Overview](https://blogs.saphana.com/2015/02/18/sap-hana-tailored-data-center-integration-tdi-overview/)
