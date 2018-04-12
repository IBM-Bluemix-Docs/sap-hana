---



copyright:
  years: 2017, 2018
lastupdated: "2018-02-02"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# IBM Cloud IaaS 上的 SAP HANA 概述
{: #iaas-overview}

“基础架构即服务器”(IaaS) 环境由很多组件组成：数据中心、计算、连接、存储器和网络。 

## 数据中心

通过北美洲、南美洲、欧洲、亚洲和澳大利亚的数据中心，可以根据需要随时随地供应云资源。每个数据中心都连接到 {{site.data.keyword.cloud_notm}} 全球专用网络，使数据在全球任何位置的传输速度更快，效率更高。

有关更多信息，请参阅[数据中心](https://www.ibm.com/cloud-computing/bluemix/data-centers){: new_window}。

## 裸机服务器

{{site.data.keyword.baremetal_long}} 是具有有限定制功能的物理服务器。这些服务器专供您或您的客户使用，不会与其他 {{site.data.keyword.cloud_notm}} 客户共享任何部分（包括服务器资源），并且作为运行所选操作系统 (OS) 的整个物理服务器进行供应。SAP HANA 产品的操作系统是 Red Hat Linux for SAP HANA 6.7 操作系统。

由于裸机服务器上的定制有限，因此可将供应时间缩短为 1 到 4 小时。当您力争先于竞争对手将应用程序推向市场时，快速供应会很有帮助。

由于 SAP 认证的服务器具有预先配置的 RAM 量和 CPU 数量，因此为您提供了一系列 RAM 和 CPU 组合。部署服务器之后，*无法*在订购过程中或通过支持凭单更改组合。

有关更多信息，请参阅[关于裸机服务器](https://console.bluemix.net/docs/bare-metal/index.html#about-bare-metal-servers)。 

## 网络连接

在设置 {{site.data.keyword.cloud_notm}} 帐户时，将自动授权到 {{site.data.keyword.cloud_notm}} Virtual Cloud Network 的虚拟专用网 (VPN) 连接。缺省情况下，服务器具有公共和专用 IP 地址。如果希望服务器为专用服务器，那么可在供应服务器后关闭公共接口，也可以将该服务器作为专用服务器进行订购。 

虽然 {{site.data.keyword.cloud_notm}} 产品满足 SAP HANA 的网络需求（10 Gb 冗余网络），但是根据应用程序场景，可能还需要满足特定等待时间和吞吐量关键性能指标 (KPI)。有关确定放置 SAP HANA 服务器的数据中心和决定最佳网络连接解决方案的更多信息，请参阅[网络连接](/docs/infrastructure/sap-hana/hana-considerations.html#network_connectivity)注意事项。

有关更多信息，请参阅[虚拟专用网入门](https://console.bluemix.net/docs/infrastructure/iaas-vpn/getting-started.html#getting-started-with-virtual-private-networking-vpn-)和 [*SAP HANA Network Requirements*](https://www.sap.com/documents/2016/08/1cd2c2fb-807c-0010-82c7-eda71af511fa.html) 白皮书。

## 存储器
{: #storage}

本地存储器随 {{site.data.keyword.baremetal_short}} 一起提供，它使用 {{site.data.keyword.cloud_notm}} 专用网络虚拟 LAN (VLAN) 来帮助提供企业级安全性，而不阻碍管理员访问。对于 SAP HANA 认证的服务器，本地存储器设计并配置为满足 SAP 依据 SAP HANA 认证条件针对吞吐量和等待时间定义的 KPI。本地存储器具有不同子文件系统的相关大小，如 SAP HANA Installation Guide 所定义（`data.log` 和 `shared`）。您无需执行任何进一步修改。

提供了适用于 {{site.data.keyword.cloud_notm}} 的两种类型的存储器，即块存储器和文件存储器，可选择用于为 SAP HANA 执行备份和复原。这两种类型都使用每秒输入/输出操作数 (IOPS)，这些操作数用于确定存储需求。IOPS 基于 16 KB 块大小（50/50 读/写混合）进行度量。要在卷上实现最大 IOPS，需要有足够的网络资源。其他注意事项包括专用网络在存储器和主机端之外的使用量，以及特定于应用程序的调整（例如，IP 堆栈和队列深度）。有关更多信息，请参阅 [Block Storage 入门](https://console.bluemix.net/docs/infrastructure/BlockStorage/index.html#getting-started-with-block-storage)和 [File Storage 入门](https://console.bluemix.net/docs/infrastructure/FileStorage/index.html#getting-started-with-file-storage)。

如果您希望寻求快速、经济高效的设备备份解决方案，{{site.data.keyword.cloud_notm}} 还提供了网络连接的存储器 (NAS)。NAS 可以通过网络文件系统 (NFS) 进行安装，并且可以用于具有 Parallels Plesk Panel 和 cPanel@WHM 的文件传输协议 (FTP)。

NAS 存储器可用于任何目的，但在此情况下，*不*用于 SAP HANA 数据或日志文件。存储器不满足 I/O KPI 的相关条件。但是，可以将存储器用于备份设备和所有其他种类的数据。当通过 NFS 安装时，SAP HANA 可以将它用作数据和日志文件的备份设备。  
  
NAS 和 FTP 存储器按月计费，并且提供各种存储器大小。您可以主要通过以下方式与 NAS 和 FTP 存储器进行交互：通过操作系统在命令行或终端中，或者在 {{site.data.keyword.cloud_notm}} 基础架构客户门户网站中的面板上通过点击式交互。在客户门户网站中，可以使用 NAS 详细信息和使用情况，但是无法在命令行、内核或控制面板之外处理该服务。

有关 {{site.data.keyword.cloud_notm}} 环境中 NAS 的更多信息，请参阅 [NAS 入门](https://console.bluemix.net/docs/infrastructure/network-attached-storage/index.html#getting-started-with-nas)。

## 部署和管理

创建 {{site.data.keyword.cloud_notm}} 客户帐户后，通过 {{site.data.keyword.cloud_notm}} 基础架构客户门户网站或 API 部署 {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}。可通过客户门户网站、API 或命令行界面 (CLI) 来管理服务器。有关更多信息，请参阅[关于裸机服务器](https://console.bluemix.net/docs/bare-metal/index.html#about-bare-metal-servers)。

## 支持

[{{site.data.keyword.cloud_notm}} 客户支持](https://console.bluemix.net/docs/support/index.html#getting-customer-support)处理在使用各种渠道（包括交谈、电话和基于凭单的支持）期间可能出现的任何支持疑问和问题。客户支持为所有 {{site.data.keyword.cloud_notm}} 客户免费提供，涵盖了每天开具的大多数凭单。有关更多信息，请参阅[获取客户支持](https://console.bluemix.net./docs/support/index.html#getting-customer-support)。

您还可以继续通过与 {{site.data.keyword.cloud_notm}} IaaS 和 SAP 产品相关的 SAP 支持人员来创建凭单。有关更多信息，请参阅 [SAP Support](https://support.sap.com/en/index.html) 和 [SAP Note 2414820](https://launchpad.support.sap.com/#/notes/2414820)。

## 安装 SAP HANA

必须由已完成 SAP HANA 安装认证课程的经认证 SAP HANA 安装人员来安装 SAP HANA 软件。有关更多信息，请参阅 [Who Can Install SAP HANA?](http://www.saphanacentral.com/p/who-can-install-sap-hana.html)。
