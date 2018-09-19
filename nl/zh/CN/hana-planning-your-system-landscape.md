---



copyright:
  years: 2017, 2018
lastupdated: "2018-05-30"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 规划系统格局
{: #planning-your-system-landscape}

SAP *格局*是由两个或更多 SAP *系统*组成的组，通常包含开发、质量和测试以及生产。一个 SAP 系统由一个或多个 *SAP 实例*组成，这些实例是同时启动和停止的一组进程。有关 SAP 格局的更多信息，请参阅 [*SAP Business Suite on IBM X6 Systems 参考体系结构*](https://lenovopress.com/redp5073.pdf)。
{: shortdesc}

针对市场中的所有 SAP 解决方案提供了多种可能的格局配置，例如，服务器（大小）/存储器（大小）。这些解决方案包含基于 SAP NetWeaver 的产品，例如 [SAP Business Suite](https://open.sap.com/courses/suitehana1)、SAP Business Warehouse 以及 {{site.data.keyword.cloud}} SAP-Certified Infrastructure 中服务器支持的所有特定 SAP 附加组件。要记住的更多解决方案是任何可能与 SAP 集成的第三方软件。 

SAP HANA 可作为基于 SAP NetWeaver 堆栈的解决方案的数据库或作为独立实体运行，具体取决于您的使用场景。对于这两种场景，{{site.data.keyword.cloud_notm}} 产品提供预先配置的经 SAP NetWeaver 认证的服务器，可从任何其他服务器构建围绕这些服务器的格局。

根据计划运行的应用程序、可能的增长和性能确定服务器的大小时，您会希望信息尽可能详细。此外，请记住应用程序的存储器和内存需求。格局中的 SAP 系统在彼此连接或与外部系统连接时有特定需求。有关更多信息，请参阅[规划 SAP 格局时要考虑的事项](/docs/infrastructure/sap-hana/hana-considerations.html)。

表 1 包含规划过程中的步骤。使用此表可帮助构建目标 SAP 格局。

表 1. 规划过程概述

|步骤 |详细信息 |
| --- | --- |
|1 |[获取 SAP 和 {{site.data.keyword.cloud_notm}} 凭证并创建帐户](/docs/infrastructure/sap-hana/hana-get-credentials.html) |
|2 |[查看任何相关 SAP 和 {{site.data.keyword.cloud_notm}} 文档](/docs/infrastructure/sap-hana/hana-review-doc.html) |
|3 |[确定 SAP 应用程序](/docs/infrastructure/sap-hana/hana-determine-apps.html) |
|4|[设置服务器的大小](/docs/infrastructure/sap-hana/hana-size-server.html) |
|5|[确定配置](/docs/infrastructure/sap-hana/hana-determine-configuration.html) |

## 后续步骤

选择表 1 中的相应步骤以开始规划 SAP 格局。
