---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-26"

keywords: SAP HANA, SAP Quick Sizer, {{site.data.keyword.cloud_notm}}, {{site.data.keyword. baremetal_short}}, deployment

subcollection: sap-hana

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}


# 4. 设置服务器的大小
{: #size_the_server}

决定计划使用的 SAP 解决方案之后，接下来的步骤是确定支持 SAP 格局所需的 {{site.data.keyword.baremetal_long}} 数量并确保正确设置了这些服务器的大小。
{: shortdesc}

## 了解 SAP 大小设置方法
{: #size_method}

在具备以下 RAM 总大小的单节点配置中的 {{site.data.keyword.cloud_notm}} 上提供了 SAP HANA：
  * 512 GB
  * 1024 GB (1 TB)
  * 2048 GB (2 TB)
  * 4096 GB (4 TB)
  * 6144 GB (6 TB)
  * 8192 GB (8 TB)
  * 12288 GB (12 TB)

这是列式数据库，与传统的基于行的关系数据库管理系统 (RDMS) 相比，存储数据所需空间通常更少。数据可高度压缩，压缩比率范围从 3:1 到超过 10:1（基于源数据和数据库）。

您需要在购买服务器*之前*正确设置服务器的大小，因为大小设置对于项目成功至关重要。大小不正确的内存或存储器需求可能导致升级并迁移至更大的服务器。

## 访问 SAP Quick Sizer
{: #quick_sizer}

在设置 SAP HANA 认证的设备的大小时，主存储器是需要考虑的最重要资源之一。公开的 [*SAP HANA Master Guide* ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://help.sap.com/doc/e95f6750b0fd10148ea5c6be75016694/2.0.00/en-US/SAP_HANA_Master_Guide_en.pdf){: new_window} 提供与大小设置相关的主题的起点。此指南中的 [Sizing SAP HANA ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://help.sap.com/viewer/eb3777d5495d46c5b2fa773206bbfb46/2.0.00/en-US/d4a122a7bb57101493e3f5ca08e6b039.html){: new_window} 信息提供有关如何设置 SAP HANA 系统大小的指导。它指向绿地模式安装和现有系统的不同安装和迁移场景。有一个指向 SAP HANA 版本的 SAP Quick Sizer 工具的链接（需要 SAP S 用户标识以访问该工具）。该页面还列出了与设置 SAP HANA 服务器大小相关的 SAP Note。

## 设置虚拟环境的大小
{: #size_virtual}

有关在虚拟环境中运行 SAP HANA 时的其他大小设置注意事项，请参阅 [VMware ESXi 服务器部署](/docs/infrastructure/sap-hana?topic=sap-hana-considerations#vmware_server)和 [*Architecture Guidelines and Best Practices for Deployments of SAP HANA on VMware vSphere Architecture and Technical Considerations Guide* ![外部链接图标](../../icons/launch-glyph.svg "外部链接图标")](https://www.vmware.com/content/dam/digitalmarketing/vmware/en/pdf/whitepaper/sap_hana_on_vmware_vsphere_best_practices_guide-white-paper.pdf){: new_window}。

## 后续步骤

 [5. 确定配置](/docs/infrastructure/sap-hana?topic=sap-hana-determine_configuration#determine_configuration)
