---

copyright:
  years: 2017, 2019
lastupdated: "2019-02-26"

keywords: SAP HANA, network connectivity, VLANs, external storage, high availability, highly available, disaster recovery, HA, DR, VLANs,

subcollection: sap-hana

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 规划 SAP 格局时要考虑的事项
{: #considerations}

格局中的 SAP 系统在彼此的连接或与外部系统的连接方面存在特定需求。针对格局，还需要考虑外部存储器，以及决定在服务器上部署 VMware 时要执行的操作。

## 网络连接
{: #network_connectivity}

[{{site.data.keyword.cloud_notm}} 网络](/docs/infrastructure/sap-hana?topic=sap-hana-about_ibmcloud_for_sap#ibm_cloud_network)提供 {{site.data.keyword.cloud}} 网络连接方法的概述。如果未正确规划，那么不管您计划如何使用系统，网络连接问题都可能会导致项目严重延迟。

通常，针对 IaaS 供应的 {{site.data.keyword.cloud_notm}} 服务器，您有两个接口选项：第一个是具有公共 IP 的外部接口。第二个是内部接口，提供了“专用 IP”，符合请求评论 (Request for Comment, RFC) 1918。也可以选择具有“专用 IP”的单个内部接口。外部 IP 可能更易于使用，但存在潜在风险，尽管已安装并预先配置基本防火墙。

第二个选项通过 {{site.data.keyword.cloud_notm}} 基础架构客户门户网站访问 {{site.data.keyword.cloud_notm}} 虚拟专用网 (VPN)，或者将安全设备部署到您的格局中。针对防火墙、网络地址转换、VPN 访问和其他网络功能提供了安全设备。建议在确定格局布局以及 SAP 应用程序层上所需的连接后，让您的网络部门与 [{{site.data.keyword.cloud_notm}} 支持人员](/docs/get-support?topic=get-support-getting-customer-support#getting-customer-support)联系和交流。

### VLAN
{: #vlans}

如果要在格局中隔离不同类型的网络流量，那么可订购更多虚拟 LAN (VLAN)。请记住，采用更多 VLAN 仅可以隔离流量，而不会提高性能。SAP 通常建议将 10 Gb 网络用于其应用程序服务器和 SAP HANA 数据库之间的流量，以及用于其他 SAP HANA 客户机，例如 SAP Business Intelligence。如果要将 SAP HANA 服务器的管理访问权与其他客户机隔离，那么应该为您的格局订购另一个 VLAN。另一个选项是通过公用和专用网络分隔流量，因为 {{site.data.keyword.cloud_notm}} 不支持进一步的“物理”上行链路。请遵循 SAP 针对 [SAP HANA Tailored Data Center Integration (TDI) ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://blogs.saphana.com/2015/02/18/sap-hana-tailored-data-center-integration-tdi-overview/){: new_window} 的建议。

通过 VPN 访问以及从跳转盒访问将允许从 SAP HANA Studio 对 SAP HANA 实例进行透明访问。

## 外部存储器
{: #external_storage}

除本地存储器外，您可能还需要更多外部存储器来执行备份。对于这些需求，可以如[存储器](/docs/infrastructure/sap-hana?topic=sap-hana-iaas-overview#storage)中所述，订购块存储器或网络连接的存储器 (NAS)。由于额外的块存储器和网络文件系统 (NFS) 数据通过与所有其他网络流量相同的物理适配器来传输，因此需要牢记影响。

对于外部存储器，请务必在决定存储解决方案之前计算项目需求。如果需要复原 SAP HANA 系统，那么存储器的 IOPS 会对复原窗口产生重大影响。由于所有备份都是联机备份，与 SAP HANA 配置方式无关，因此备份窗口对于 SAP HANA 不那么重要。

例如，使用 {{site.data.keyword.cloud_notm}} {{site.data.keyword.blockstorageshort}}，可按最大速度计算 SAP HANA 的大约 12 TB 复原。由于每个设备的最大大小为 4 TB，因此必须创建三个物理存储设备（块存储器 iSCSI LUN）。您可以使用 Linux 逻辑卷管理器在这三个设备上创建条带，并创建一个 12 TB 的逻辑设备。

12 TB 提供 3x10 IOPS/GB，总计为 122,880 IOPS/GB，以 16 KB 为单位。这可实现 1.875 GB/秒的复原时间，或者低于 2 小时的总复原时间。由于按 50/50 读写分配来获取 IOPS 度量，因此可将数字视为复原性能的下限。如果您依赖某个特定复原窗口，那么建议执行备份和复原测试。

{{site.data.keyword.cloud_notm}} {{site.data.keyword.blockstorageshort}} 和 {{site.data.keyword.filestorage_full_notm}} 或 NAS 可充当备份空间或服务器上安装的其他软件组件的存储器。但是，{{site.data.keyword.cloud_notm}} 存储器和 NSA 无法用作 SAP HANA 的存储器，因为这些选项不符合 KPI 条件。

有关更多信息，请参阅 [{{site.data.keyword.blockstorageshort}}](/docs/infrastructure/BlockStorage?topic=BlockStorage-GettingStarted#GettingStarted) 入门和 [{{site.data.keyword.filestorage_full_notm}} 入门](/docs/infrastructure/FileStorage?topic=FileStorage-GettingStarted#getting-started-with-file-storage)。

## 高可用性和灾难恢复场景
{: #ha_dr}

{{site.data.keyword.cloud_notm}} 环境不支持任何预先配置的高可用性 (HA) 场景。但是，允许通过 Red Hat Enterprise Linux HA 扩展（例如，内部部署用例）来为 SAP HANA 实施 HA 解决方案。

可以为 SAP HANA 系统复制配置从一台服务器到副本的自动故障转移。请遵循有关系统复制的 SAP 文档来确定最适合您的应用程序场景和灾难弹性级别的复制方式。根据复制方式，需要实现不同的网络 KPI。请参阅有关网络吞吐量和等待时间的 SAP 建议，以确定首选操作方式所需的吞吐量和最长等待时间。{{site.data.keyword.cloud_notm}} 网络拓扑应该能够处理所有必需的配置。如果不确定或者想要灾难恢复站点位于不同的数据中心以实现最大灾难弹性，请联系 {{site.data.keyword.cloud_notm}} 支持人员以确定您的场景的最佳设置。

请注意，SAP HANA Scale-Out（多节点）环境仍在评估中。换句话说，SAP HANA 的备用节点不是 {{site.data.keyword.cloud_notm}} 环境中的当前选项。

有关高可用性和灾难恢复的更多信息，请参阅[{{site.data.keyword.cloud_notm}}高可用性支持](/docs/infrastructure/sap-hana?topic=sap-hana-ha#ha)和[灾难恢复](/docs/infrastructure/sap-reference-architecture?topic=sap-reference-architecture-recommendations#dr)。

有关系统复制以及网络吞吐量和等待时间的更多信息，请参阅
  * [How To Perform System Replication for SAP HANA ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.sap.com/documents/2013/10/26c02b58-5a7c-0010-82c7-eda71af511fa.html){: new_window}
  * [Network Required for SAP HANA System Replication ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.sap.com/documents/2014/06/babb2b55-5a7c-0010-82c7-eda71af511fa.html){: new_window}

有关为 Linux 操作系统设置 HA 集群扩展的更多信息，请参阅
  * [Automated SAP HANA System Replication with Pacemaker on RHEL Setup Guide ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://access.redhat.com/articles/1466063){: new_window}
  * [SAP HANA SR Performance Optimized Scenario ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.suse.com/docrep/documents/ir8w88iwu7/suse_linux_enterprise_server_for_sap_applications_12_sp1.pdf){: new_window}

## VMware ESXi 服务器部署
{: #vmware_server}

{{site.data.keyword.cloud_notm}} SAP HANA 产品中的所有服务器都已通过 VMware ESX 认证，这使 SAP HANA 可部署在虚拟机 (VM) 上。如果某个服务器是随 VMware ESX 一起订购的，那么该服务器将通过预安装、基本配置的 ESX 实例进行部署；不会部署任何 VM。请注意，您负责在基于 ESX 的部署中部署正确的访客操作系统。遵循 SAP Note 2414820 中定义的指示信息以选择 {{site.data.keyword.cloud_notm}} 上的 SAP HANA 支持的操作系统版本。

基于 ESX 的部署的大小设置过程与裸机服务器部署不同。请遵循 *Architecture Guidelines and Best Practices for Deployments of SAP HANA on VMware vSphere Architecture and Technical Considerations Guide* 中的建议。需要遵循 *Architecture...and Considerations Guide* 中的规则来计算虚拟化层的开销。在 VM 上部署访客操作系统后，确保满足 SAP HANA TDI KPI。请检查 SAP Note 1943937 以获取有关测试环境的 SAP 支持先决条件合规性的详细信息。对于部署在特定服务器上的每个 VM，都需要完成这些先决条件。

必须遵循 SAP 定义的其他多条规则以在虚拟环境中部署 SAP HANA。对于生产，请遵循 SAP Note 1995460 中概述的限制。SAP Note 2024433 描述一台服务器上多个 VM 的规则。

有关更多信息，请参阅以下文档：
  * [SAP Note 2414820 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://launchpad.support.sap.com/#/notes/2414820){: new_window}
  * [*Architecture Guidelines and Best Practices for Deployments of SAP HANA on VMware vSphere Architecture and Technical Considerations Guide* ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.vmware.com/content/dam/digitalmarketing/vmware/en/pdf/whitepaper/sap_hana_on_vmware_vsphere_best_practices_guide-white-paper.pdf){: new_window}
  * [SAP Note 1943937 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://launchpad.support.sap.com/#/notes/1943937){: new_window}
  * [SAP HANA Tailored Data Center Integration Frequently Asked Questions ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.sap.com/documents/2016/05/e8705aae-717c-0010-82c7-eda71af511fa.html){: new_window}
  * [SAP Note 1995460 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://launchpad.support.sap.com/#/notes/1995460){: new_window}
  * [SAP Note 2024433 ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://launchpad.support.sap.com/#/notes/2024433){: new_window}
  * [SAP HANA Tailored Data Center Intgration (TDI) Overview ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://blogs.saphana.com/2015/02/18/sap-hana-tailored-data-center-integration-tdi-overview/){: new_window}
