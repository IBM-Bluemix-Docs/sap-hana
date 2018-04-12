---



copyright:
  years: 2018
lastupdated: "2018-02-12"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 1. 스토리지 주문
{: #order_storage}

{{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}를 배치한 후 {{site.data.keyword.blockstoragefull}}, {{site.data.keyword.filestorage_full_notm}} 및 NAS(Network Attached Storage)가 주문됩니다. 

## {{site.data.keyword.cloud_notm}} 스토리지 주문
{: #ibm_storage}

[{{site.data.keyword.blockstorageshort}} 프로비저닝 및 관리](https://console.bluemix.net/docs/infrastructure/BlockStorage/provisioning-block_storage.html#provisioning-and-managing-block-storage) 또는 [{{site.data.keyword.filestorage_full_notm}} 프로비저닝 및 관리](https://console.bluemix.net/docs/infrastructure/FileStorage/provisioning-file-storage.html#provisioning-and-managing-ibm-file-storage-for-ibm-cloud) 아래의 단계를 사용하여 백업 및 복원 스토리지 솔루션을 주문할 수 있습니다. 사용할 스토리지 유형, 주문 방법 및 서버에 배치하는 방법을 결정하는 프로세스가 안내됩니다.

## NAS 주문
{: #order-nas}

데이터베이스의 아카이브된 로그 파일 또는 빈번한 온라인 및 오프라인 백업을 위한 스토리지가 필요한 경우 NAS 스토리지는 서버 로컬 스토리지의 다른 가치 있는 확장일 수 있습니다. NAS를 주문하고 설정하려면 [NAS/FTP 스토리지 주문](https://console.bluemix.net/docs/infrastructure/network-attached-storage/index.html#ordering-nas-ftp-storage)을 방문하십시오. 
또한 NFS(Network File Storage)를 Linux 서버에 맵핑하는 방법을 확인하려면 [Linux에서 NAS 스토리지 마운트](https://console.bluemix.net/docs/infrastructure/network-attached-storage/mount-nas-storage-linux.html#mounting-nas-storage-in-linux)를 참조하십시오. [NFS를 통해 NAS 스토리지를 VMware ESXi에 데이터 저장소로 맵핑할 수도 있습니다](https://console.bluemix.net/docs/infrastructure/network-attached-storage/connect-nas-storage-windows.html#connecting-to-nas-storage-in-windows).

## 다음 단계

  [2. 환경 보안](/docs/infrastructure/sap-hana/hana-secure-environment.html)

  [3. ESX 하이퍼바이저에 게스트 OS 설치(선택사항)](/docs/infrastructure/sap-hana/hana-installing-guest-operating-system-VMware-deployments.html)

  [4. SAP 소프트웨어 및 애플리케이션 다운로드 및 설치](/docs/infrastructure/sap-hana/hana-installing-SAP-landscape.html)
  
  [5. {{site.data.keyword.cloud_notm}} 데이터 센터에 대한 연결 테스트](/docs/infrastructure/sap-hana/hana-testing-connectivity.html)
