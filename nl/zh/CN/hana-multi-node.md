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
{:table: .aria-labeledby="caption"}

# 5. 配置 IBM Cloud 基础架构以支持 SAP HANA 多节点
{: #multi-node-storage}

{{site.data.keyword.cloud_notm}} 支持将 SAP HANA 多节点存储器用于联机分析处理 (OLAP) 工作负载，如 SAP Business Warehouse (SAP BW) 和 SAP BW/4HANA。针对 SAP HANA 多节点的 {{site.data.keyword.cloud}} 解决方案最多由 15+1 个节点构成（15 个工作程序节点加一个备用节点），最多有 30 TB 内存用于系统。

利用多节点，多个 SAP HANA 节点可构建一个 SAP HANA 系统。数据分布在这些节点中，构成单个数据库。多节点配置通过备用配置支持可扩展性和高可用性。针对此配置的 {{site.data.keyword.cloud_notm}} 产品遵循 [SAP HANA Tailored Data Center Integration](https://blogs.saphana.com/2015/02/18/sap-hana-tailored-data-center-integration-tdi-overview/) (TDI)，并使用 {{site.data.keyword.cloud_notm}} SAP-HANA 认证的服务器来实现集中、共享的企业存储。

*注*：必须遵循[订购多节点系统](#ordering)下的配置准则以满足 SAP HANA TDI 需求并受 SAP 支持。

遵循 [调整 SAP HANA 的大小](https://help.sap.com/viewer/eb3777d5495d46c5b2fa773206bbfb46/2.0.00/en-US/d4a122a7bb57101493e3f5ca08e6b039.html)中的准则以根据目标 SAP HANA 系统确定需要的大小，包括部署所需的内存和存储总量。调整大小需求可帮助您确定您的 SAP HANA 多节点系统所需的 SAP HANA 节点数，以及托管数据所需的存储器。

## 复查网络拓扑和存储布局
{: #reviewing-topology}

图 1 显示 {{site.data.keyword.cloud_notm}} Infrastructure as a Service SAP HANA TDI 设置所需的网络拓扑。

图 1. IBM Cloud Infrastructure as a Service SAP HANA TDI 网络拓扑

![图 1. IBM Cloud Infrastructure as a Service SAP HANA TDI 网络拓扑](/images/SAP-BW.png "IBM Cloud Infrastructure as a Service SAP HANA TDI 网络拓扑")

## 设置必备软件
{: #prerequisites}

SAP HANA 多节点需要存在特定网络并发挥功能。在订购其他系统组件之前，必须先正确设置这些网络，还有数据库节点。您需要
* 客户端网络，将 SAP Advanced Business Application Programming (SAP ABAP) 应用程序服务器、SAP HANA Studio 客户机以及其他网络客户机连接到多节点系统。网络吞吐量和可用性选项取决于 SAP 多节点系统的使用方案。考虑应用程序需要的传入、传出 SAP HANA 数据库的数据量，以及可用性关键性能指标 (KPI)。
* 存储网络，需要用于连接后端 {{site.data.keyword.blockstoragefull}} 和 {{site.data.keyword.filestorage_full_notm}}。要实现性能和冗余最大化，需要具有两个接口的 10 GB 网络位于 Linux 与 Link Aggregation Control Protocol (LACP) 绑定之下。如果没有提供来自 SAP HANA 调整大小准则的性能图，就无法满足 SAP HANA TDI KPI。
* 用于 SAP HANA 内部通信的节点间网络，设置为存储网络的等同项。节点间网络仅用于操作过程中可能需要的节点间通信和数据传输。此所需网络配置位于 Linux 与 LACP 绑定之下的两个物理 10 GB 适配器上。

## 订购多节点系统
{: #ordering}

要满足 SAP 要求的性能和吞吐量 KPI，必须在同一个数据中心订购 VLAN、存储器和计算节点。如果组件分布在多个数据中心内，SAP 不会支持多节点系统。

1. 订购三个不同的 VLAN 以及带四个适配器的服务器（两个专用、两个公共）。有关订购 VLAN 的更多信息，请参阅[步骤 1 订购主 VLAN 和公共 VLAN](https://console.bluemix.net/docs/infrastructure/virtualization/advanced-single-site-vmware-reference-architecturesoftlayer.html#step-1-ordering-primary-public-and-private-vlans)。有关订购服务器的更多信息，请参阅[ 2. 设置基础架构](https://console.bluemix.net/docs/infrastructure/sap-hana/hana-setting-up-infrastructure.html#set_up_infrastructure)。
2. 设置初始专用 VLAN 作为“存储 VLAN”。
3. 向 {{site.data.keyword.cloud_notm}} 支持[提交凭单](https://console.bluemix.net/docs/get-support/howtogetsupport.html#open-ticket)以
   a. 将公共接口移动到第二个 VLAN
   b. 再订购两个适配器以分配给第三个 VLAN（即，客户机 VLAN）

现在，您的服务器数是依据调整大小情况确定的，而网络设置是为了
* 可以将存储器连接到所有节点
* 可以在连接存储器后执行 SAP HANA 多节点安装

您的存储 LAN 连接和节点间连接是由 {{site.data.keyword.cloud_notm}} 部署配置的。请确保订购的连接具有两个 10 GB 适配器，每个都有故障转移配置。此设置可确保正确的 Linux 绑定和 LACP 配置。如有任何问题，请联系 {{site.data.keyword.cloud_notm}} 支持团队。

{{site.data.keyword.IBM_notm}} {{site.data.keyword.blockstorageshort}} (Endurance) 和 {{site.data.keyword.IBM_short}} {{site.data.keyword.filestorage_short}} (Performance) 必须满足特定的性能条件。对于数据量，每个工作程序节点需要性能 KPI 为 10 IOPS/GB 的 2 TB Endurance 存储器。还需要另一个大小相同的卷作为 SAP HANA 共享存储，并由所有节点共享。

对于日志卷，每个节点需要一个 512 GB 的 Performance 存储卷，其性能 KPI 为 10 K IOPS。

您可以执行[供应和管理 {{site.data.keyword.blockstorageshort}}](https://console.bluemix.net/docs/infrastructure/BlockStorage/provisioning-block_storage.html#provisioning-and-managing-block-storage) 或[供应和管理 {{site.data.keyword.filestorage_full_notm}}](https://console.bluemix.net/docs/infrastructure/FileStorage/provisioning-file-storage.html#provisioning-and-managing-ibm-file-storage-for-ibm-cloud) 下的步骤，以订购 Endurance 和 Performance 存储。

## 配置 SAP HANA 多节点
{: #configuring}

SAP HANA 共享卷以及每个数据和日志卷都必须是所有节点都可访问的。这就意味着整个存储 VLAN 都可以访问所有卷，它是您在[订购多节点系统](#ordering)下配置的。如果您不想列出涉及到的每个 IP 地址，请将卷设置为让该 VLAN 的整个 IP 子网都可访问。

按照 [SAP HANA on NetApp FAS Systems with NFS](https://www.netapp.com/us/media/tr-4290.pdf) 中的指南来配置 SAP HANA 多节点系统。针对每个卷使用以下 Network File System (NFS) 装配选项来装配：

`/etc/fstab` 中的 `rw,bg,hard,timeo=600,intr,noatime,vers=4,minorversion=1,lock,rsize=1048576,wsize=1048576`。

这些选项已经过 NetApp 和 {{site.data.keyword.cloud_notm}} 测试。如果计划更改任何装配选项或值，请联系 {{site.data.keyword.cloud_notm}} 支持。

在将所有卷都装配到所有节点上之后，多节点配置完成，已准备就绪可安装 SAP HANA 多节点数据库。按照 [SAP HANA 服务器安装和更新指南](https://help.sap.com/viewer/2c1988d620e04368aa4103bf26f17727/2.0.03/en-US)中的步骤安装所需版本的 SAP HANA 数据库。
