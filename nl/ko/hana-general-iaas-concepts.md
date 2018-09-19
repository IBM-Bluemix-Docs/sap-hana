---



copyright:
  years: 2017, 2018
lastupdated: "2018-06-28"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# SAP HANA on IBM Cloud IaaS 개요
{: #iaas-overview}

IaaS(Infrastructure-as-a-Server) 환경은 데이터 센터, 컴퓨팅, 연결, 스토리지 및 네트워크와 같은 여러 컴포넌트로 구성됩니다. 

## 데이터 센터

북미, 남미, 유럽, 아시아 및 호주 전역에 있는 데이터 센터를 통해 언제 어디서나 필요한 클라우드 리소스를 프로비저닝할 수 있습니다. 각 데이터 센터는 {{site.data.keyword.cloud_notm}} 글로벌 사설 네트워크에 연결되어 있으므로 전세계 어디서나 더 빠르고 효율적으로 데이터를 전송할 수 있습니다.

자세한 정보는 [데이터 센터](https://www.ibm.com/cloud-computing/bluemix/data-centers){: new_window}를 참조하십시오.

## 베어메탈 서버

{{site.data.keyword.baremetal_long}}는 사용자 정의 기능이 제한되어 있는 실제 서버입니다. 이 서버는 사용자 또는 고객 전용으로 사용되고 서버 리소스를 포함한 어떤 파트에서도 다른 {{site.data.keyword.cloud_notm}} 고객과 공유되지 않으며 선택한 운영 체제(OS)를 실행 중인 전체 실제 서버로 프로비저닝됩니다. SAP HANA 오퍼링에 대한 운영 체제는 Red Hat Enterprise Linux 7.4 for SAP HANA, SUSE Linux Enterprise Server 12 SP2 for SAP HANA 및 VMware Server Virtualization 6.5입니다.

베어메탈 서버에서는 사용자 정의가 제한되기 때문에 프로비저닝 시간이 1 - 4시간 단축될 수 있습니다. 빠른 프로비저닝은 경쟁사보다 먼저 앱을 출시하려고 할 때 유용합니다.

SAP 인증 서버에는 RAM 용량과 CPU 수가 사전 구성되어 있으므로 RAM 및 CPU 조합의 배열이 제공됩니다. 주문 프로세스 중이나 서버가 배치된 후 지원 티켓을 통해 이 조합을 변경할 수 *없습니다*.

자세한 정보는 [베어메탈 서버 정보](https://console.bluemix.net/docs/bare-metal/about.html#about-bare-metal-servers)를 참조하십시오. 

## 네트워크 연결

{{site.data.keyword.cloud_notm}} 계정이 설정되면 {{site.data.keyword.cloud_notm}} Virtual Cloud Network에 대한 가상 사설망(VPN) 연결 권한이 자동으로 부여됩니다. 기본적으로 서버에는 공인 및 사설 IP 주소가 있습니다. 개인용 서버로 설정하려는 경우 서버가 프로비저닝된 후 공용 인터페이스를 끄거나 서버를 개인용으로 주문할 수 있습니다. 

{{site.data.keyword.cloud_notm}} 오퍼링을 통해 SAP HANA에 대한 네트워크 요구사항(10Gb 중복 네트워크)이 충족되지만 애플리케이션 시나리오에 따라 특정 대기 시간 및 처리량 핵심성과지표(KPI)가 충족되어야 할 수도 있습니다. SAP HANA 서버를 찾을 데이터 센터 판별 및 최적의 네트워크 연결 솔루션 결정에 대한 자세한 정보는 [네트워크 연결](/docs/infrastructure/sap-hana/hana-considerations.html#network_connectivity) 고려사항을 참조하십시오.

자세한 정보는 [가상 사설망(VPN) 시작하기](https://console.bluemix.net/docs/infrastructure/iaas-vpn/getting-started.html#getting-started-with-virtual-private-networking-vpn-) 및 [*SAP HANA Network Requirements*](https://www.sap.com/documents/2016/08/1cd2c2fb-807c-0010-82c7-eda71af511fa.html) 백서를 참조하십시오.

## 스토리지
{: #storage}

로컬 스토리지는 {{site.data.keyword.baremetal_short}}와 함께 제공되며 {{site.data.keyword.cloud_notm}} 사설 네트워크 가상 LAN(VLAN)을 사용하여 관리자 액세스를 방해하지 않는 동시에 엔터프라이즈급 보안을 제공합니다. SAP HANA 인증 서버의 경우 SAP에서 SAP HANA 인증 기준에 따라 처리량 및 대기 시간 모두에 대해 정의한 KPI를 충족하도록 디자인되고 구성됩니다. 로컬 스토리지에는 SAP HANA 설치 안내서에 정의된 대로 여러 서브파일 시스템의 적절한 크기가 있습니다(`data.log` 및 `shared`). 사용자 파트에서 추가 적응을 수행할 필요가 없습니다.

SAP HANA에 대한 백업 및 복원을 수행하기 위해 선택하는 두 가지 유형의 {{site.data.keyword.cloud_notm}} 스토리지(블록 및 파일)가 있습니다. 두 가지 유형 모두 스토리지 요구사항을 판별하는 데 사용되는 초당 입출력(I/O) 오퍼레이션(IOPS)을 사용합니다. IOPS는 16KB 블록 크기와 50/50 읽기/쓰기 혼합을 기준으로 측정됩니다. 볼륨에서 최대 IOPS를 달성하려면 적절한 네트워크 리소스가 준비되어 있어야 합니다. 다른 고려사항으로는 스토리지 및 호스트 측 외부의 사설 네트워크 사용 및 애플리케이션별 튜닝(예: IP 스택 및 큐 깊이)이 있습니다. 자세한 정보는 [블록 스토리지 시작하기](https://console.bluemix.net/docs/infrastructure/BlockStorage/index.html#getting-started-with-block-storage) 및 [파일 스토리지 시작하기](https://console.bluemix.net/docs/infrastructure/FileStorage/index.html#getting-started-with-file-storage)를 참조하십시오.

또한 디바이스에 대한 빠르고 비용 효율적인 백업 솔루션을 찾고 있는 경우 {{site.data.keyword.cloud_notm}}에서 NAS(Network Attached Storage)를 제공합니다. NAS는 NFS(Network File System)를 통해 마운트할 수 있으며 FTP(File Transfer Protocol)를 통해 Parallels Plesk Panel 및 cPanel@WHM 둘 다와 함께 사용할 수 있습니다.

NAS 스토리지는 어떤 용도로든 사용될 수 있지만 이 경우 SAP HANA 데이터 및 로그 파일용으로 사용되지 *않습니다*. 스토리지가 I/O KPI와 관련된 기준을 충족하지 않습니다. 그러나 이 스토리지는 백업 디바이스 및 기타 모든 유형의 데이터에 사용될 수 있습니다. NFS를 통해 마운트된 경우 SAP HANA에서 데이터 및 로그 파일에 대한 백업 디바이스로 사용될 수 있습니다.  
  
NAS 및 FTP 스토리지는 매월 청구되며 다양한 스토리지 크기로 사용할 수 있습니다. 주로 명령행이나 OS가 설치된 터미널 내에서 또는 {{site.data.keyword.cloud_notm}} 인프라 고객 포털 내의 패널에서 가리킨 후 클릭 상호작용을 통해 NAS 및 FTP 스토리지와 상호작용할 수 있습니다. 고객 포털 내에서 NAS 세부사항 및 사용법을 사용할 수 있지만 명령행, 커널 또는 제어판 외부에서 서비스를 조작할 수는 없습니다.

{{site.data.keyword.cloud_notm}} 환경의 NAS에 대한 자세한 정보는 [NAS 시작하기](https://console.bluemix.net/docs/infrastructure/network-attached-storage/index.html#getting-started-with-nas)를 참조하십시오.

## 배치 및 관리

{{site.data.keyword.cloud_notm}} 고객 계정을 작성한 후 {{site.data.keyword.cloud_notm}} 인프라 고객 포털 또는 API를 통해 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}가 배치됩니다. 고객 포털, API 또는 명령행 인터페이스(CLI)를 통해 이 서버를 관리할 수 있습니다. 자세한 정보는 [베어메탈 서버 정보](https://console.bluemix.net/docs/bare-metal/about.html#about-bare-metal-servers)를 참조하십시오.

## 지원

[{{site.data.keyword.cloud_notm}} 고객 지원](https://console.bluemix.net/docs/support/index.html#getting-customer-support)은 채팅, 전화 및 티켓 기반 지원을 비롯한 다양한 수단을 통해 발생할 수 있는 지원 질문과 문제를 처리합니다. 고객 지원은 모든 {{site.data.keyword.cloud_notm}} 고객에게 무료로 제공되며 매일 제출되는 대부분의 티켓을 다룹니다. 자세한 정보는 [고객 지원 받기](https://console.bluemix.net./docs/support/index.html#getting-customer-support)를 참조하십시오.

{{site.data.keyword.cloud_notm}} IaaS 및 SAP 제품과 관련된 SAP 지원을 통해 계속해서 티켓을 작성할 수도 있습니다. 자세한 정보는 [SAP 지원](https://support.sap.com/en/index.html) 및 [SAP 노트 2414820](https://launchpad.support.sap.com/#/notes/2414820)을 참조하십시오.

## SAP HANA 설치

SAP HANA 소프트웨어는 SAP HANA 설치 인증 과정을 완료한 공인 SAP HANA 설치 관리자가 설치해야 합니다. 자세한 정보는 [SAP HANA 설치 가능자](http://www.saphanacentral.com/p/who-can-install-sap-hana.html)를 참조하십시오.
