---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-26"

keywords: SAP HANA, SAP applications

subcollection: sap-hana

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}


# 3. 确定 SAP 应用程序

您需要确定计划在 {{site.data.keyword.baremetal_long}} 上运行的基于 SAP 的应用程序。作出决定时要考虑的事项包括：

 * 如何使用数据库？可使用两种方法来部署 SAP HANA。第一种方法是作为 SAP NetWeaver 堆栈的数据库，其中 SAP HANA 主要充当数据源。第二种部署方法是以单机方式运行 SAP HANA，直接在 SAP HANA 系统中部署应用程序。使用任何一种方法，大小设置过程以及其他系统需求和依赖性都可能因系统使用方式（开发和测试、概念证明或生产）的不同而不同。
 * 打算如何使用这些应用程序？是打算用于开发和测试还是生产？
 * 是否使用 {{site.data.keyword.cloud_notm}} 虚拟专用网服务（SSL 或点对点隧道协议 (PPTP)）？

## 后续步骤

  [4. 设置服务器的大小](/docs/infrastructure/sap-hana?topic=sap-hana-size_the_server#size_the_server)

  [5. 确定配置](/docs/infrastructure/sap-hana?topic=sap-hana-determine_configuration#determine_configuration)
