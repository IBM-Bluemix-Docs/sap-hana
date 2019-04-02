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


# IBM Cloud 高可用性支持
{: #ha}

{{site.data.keyword.cloud}} 基础架构即服务 (IaaS) 提供稳健的计算环境，并且可选择在其上部署支持高可用性 (HA) 解决方案的操作系统。此解决方案基于支持的操作系统版本，该版本在 [SAP Note 2414097 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://launchpad.support.sap.com/#/notes/2414097){: new_window} 中论述。HA 解决方案限于部署随附的已订购操作系统许可证或第三方许可证，例如自带许可证 (BYOL)。部署之前，请务必与 {{site.data.keyword.cloud_notm}} 支持人员讨论 HA 详细信息。

{{site.data.keyword.cloud_notm}} for SAP 支持和部署的操作系统包括：
* Linux [Red Hat Enterprise Linux (RHEL) 或 SUSE Enterprise Linux Server (SLES)]，同时支持 SAP NetWeaver 和 SAP HANA HA 解决方案。{{site.data.keyword.cloud_notm}} 环境中有轻微限制，这在 [SAP NetWeaver 高可用性配置概述](#overview-configs)中论述。
* Microsoft Windows，仅支持 SAP NetWeaver HA 解决方案（由于 SAP HANA 数据库的限制）。

## SAP NetWeaver 高可用性配置概述
{: #overview-configs}

有很多文档提供为 SAP 服务规划和安装 HA 环境的进一步帮助。这些文档包含有关故障转移、复制、扩展以及灾难恢复 (DR) 的信息。在适当的情况下，提供了特定文档的参考。

{{site.data.keyword.cloud_notm}} 支持用于 SAP 部署的所有操作系统和分发版（Windows、Linux RHEL 和 SLES）都随附了高可用性软件和特定扩展。以下是受支持的操作系统和分发版。

* [New Failover Clustering Improvements in Windows Server 2012 and Its Benefits for SAP NetWeaver High Availability ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://blogs.sap.com/2013/10/16/new-failover-clustering-improvements-in-windows-server-2012-and-its-benefits-for-sap-netweaver-high-availability/){: new_window} 根据使用 SAP NetWeaver 的 Windows 操作系统上的 Microsoft Windows Server Failover Clustering (WFSC) 提供了描述。

* 有两个参考指南用于指导如何在使用 Linux Pacemaker 的基于 Linux 的高可用性环境中部署 SAP NetWeaver：
  * SUSE SAP NetWeaver High Availability Cluster 7.40 设置指南
  * 使用 Red Hat Enterprise Linux HA 附加组件和 Pacemaker 部署基于 SAP NetWeaver 的高可用性服务器

* [Building High Availability for SAP NetWeaver and SAP HANA on Linux ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://support.sap.com/content/dam/SAAP/SAP_Activate/AGS_70.pdf){: new_window} 是 SAP 最佳做法文档，提供以 SAP HANA 为中心的深度技术说明。

* [SAP NetWeaver High Availability and Business Continuity in Virtual Environments with VMware and Hyper-V on Microsoft Windows ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.sap.com/documents/2015/07/508b62bc-5b7c-0010-82c7-eda71af511fa.html){: new_window} 涵盖虚拟化方面（如果您计划在虚拟化的服务器上实施 HA）。

有关 SAP 合作伙伴针对高可用性方案认证的更多高可用性产品，请参阅 [High Availability Partner Information ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://wiki.scn.sap.com/wiki/display/SI/High+Availability+Partner+Information){: new_window}。
对于非 HANA SAP 数据库，您的数据库文档中提供有关高可用性故障转移和 DR 配置的更多信息。

请注意，通常需要网络文件系统 (NFS)/通用因特网文件系统 (CIFS) 存储器的共享访问权或者基于 iSCSI 的逻辑唯一数字存储器 (LUNS) 的共享访问权来支持系统故障转移。通常需要将本地存储器与复制方法相结合来支持类似 DR 的设置。与内部部署安装类似，在规划部署时，请检查数据库产品的性能和等待时间要求。

## 补充指南
{: #extra-guide}

[基于定额的存储器](#quorum)和[网络注意事项](#network)提供部署期间需要考虑的指导信息。除了这些部分中概述的注意事项外，在 HA 环境中安装 SAP NetWeaver 及其数据库系统与其他内部部署安装没有什么不同。


### 基于定额的存储器
{: #quorum}

由于 {{site.data.keyword.cloud_notm}} IBM Cloud 环境的安全限制，不提供通过 Intelligent Platform Management Interface (IPMI) 对远程管理设备的基于网络的访问权。集群环境通常使用基于 IPMI 的组件“设定集群节点的围栏”以始终确保定额。没有支持 IPMI 的设备时，将使用共享存储设备。在 {{site.data.keyword.cloud_notm}} 环境中，通过将 iSCSI LUN 作为定额设备部署到服务器来实施共享存储设备。例如，Microsoft 群集上的文件共享见证 (FSW)，以及用于 Linux Pacemaker 的 Stonith 的 storage-based death (SDB)。
* 单击[此处 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](http://linux-ha.org/wiki/Cluster_Concepts){: new_window} 以获取有关 Linux 高可用性集群概念的更多信息。
* 单击[此处 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://docs.microsoft.com/en-us/windows-server/failover-clustering/manage-cluster-quorum){: new_window} 以获取有关配置和管理 Windows Server 2012 和 Windows Server 2012 R2 的定额服务器的更多信息。

{{site.data.keyword.cloud_notm}} Storage 内置了 HA 功能，因此，单个共享 iSCSI LUN 不会引入单个故障点 (SPOF)，因为网络布局是冗余的。但是，集群产品的具体细节可能需要多个定额设备。

### 网络注意事项
{: #network}

基于 {{site.data.keyword.cloud_notm}} 的安装随附以下某个网络配置：
* 专用网络
* 公用网络
* 公用和专用网络
* 两个专用网络（根据特殊需求）

与内部部署安装类似，可以订购额外的网络适配器，具体取决于硬件的物理限制。此限制与内部部署安装的限制相同。在硬件部署期间订购冗余的网络适配器有助于在整个网络拓扑中防止 SPOF。利用链路聚集控制协议 (LACP) 在故障转移配置中设置了冗余适配器。对于 Linux，该设置使用结合界面，而团队适配器用于 Microsoft Windows。这些适配器连接到的 {{site.data.keyword.cloud_notm}} 交换机基础架构是冗余的，因此，不会引入新的 SPOF。订购的 VLAN 可以使用冗余基础架构。

根据网络需求（例如 DR 设置中的复制方案），您必须检查已连接的设备的位置和特定于相关产品的任何新网络需求。在某些情况下，基于 {{site.data.keyword.cloud_notm}} 快照存储器的复制可能会满足您的需求。向 {{site.data.keyword.cloud_notm}} 支持人员核实以确定哪个解决方案最适合您的业务流程需求。
