---



copyright:
  years: 2017, 2018
lastupdated: "2010-03-05"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 2. 设置基础架构
{: #set_up_infrastructure}

以下部分中提供了有关设置 SAP HANA {{site.data.keyword.baremetal_long}}、网络、安全性、存储器和操作系统 (OS) 的指导信息。如有任何问题，请联系 [{{site.data.keyword.cloud_notm}} 支持](https://console.bluemix.net/docs/get-support/howtogetsupport.html#getting-customer-support)。

## 订购服务器
{: order-server}

使用以下步骤来订购 {{site.data.keyword.baremetal_short}}。可使用您的唯一凭证在[配置裸机服务器](https://console.bluemix.net/docs/bare-metal/configuring.html#configuring-your-bare-metal-server)下找到更多信息。

1. 使用您的唯一凭证登录到 [{{site.data.keyword.cloud_notm}} 基础架构客户门户网站](https://control.softlayer.com)。
2. 单击“帐户摘要”页面上的**设备**图标。
3. 单击“设备”页面上 {{site.data.keyword.baremetal_short}} 下的**每月**链接。将显示“服务器列表”对话框。
4. “SAP 认证的服务器”位于列表顶部。单击**起步价（按月）**下的超链接，以选择相应服务器，然后将转至“配置/订购”页面。SAP HANA 认证的服务器由 CPU 型号下的 **-H** 标识。  
5. 在**数量**字段中输入要订购的服务器数，然后选择**数据中心**。
6. **服务器**、**RAM**、**操作系统**和专用存储器选项缺省值基于选择的服务器，无法更改。存储器大小设置与带有给定 RAM 量的 SAP HANA 所需大小保持一致。在订购服务器后，即订购了 {{site.data.keyword.IBM_notm}} {{site.data.keyword.blockstorageshort}} for {{site.data.keyword.cloud_notm}} 或 {{site.data.keyword.filestorage_full_notm}} 以及网络连接的存储器 (NAS)。
7. 从 Red Hat 或 Microsoft 选择**操作系统**，然后为服务器选择特定操作系统或 VMware 管理程序。

## 选择服务器选项
{: #select_options}

在下一步中，将选择要添加到配置的磁盘的类型和数量。您还可以针对独立磁盘冗余阵列 (RAID) 存储器组和基于 RAID 存储器组的分区布局选择不同的选项。有关更多信息，请参阅[关于 RAID](https://console.bluemix.net/docs/bare-metal/what-raid.html#about-raid} or [{{site.data.keyword.cloud_notm}} Support](https://console.bluemix.net/docs/get-support/howtogetsupport.html#getting-customer-support)。

1. 在 **SAP 认证的服务器**下，根据计划使用服务器的方式进行选择。可以在[设置裸机服务器](https://console.bluemix.net/docs/bare-metal/configuring.html#setting-up-your-bare-metal-servers)中找到有关每个选项的详细信息。您还可以参阅[设计决策工具](https://github.com/ibm-cloud-architecture/infrastructure-design-decision-tool)（向下滚动到工具）或 [{{site.data.keyword.cloud_notm}} 支持](https://console.bluemix.net/docs/get-support/howtogetsupport.html#getting-customer-support)以获取更多信息
2. 单击页面底部的**添加到订单**。

## 设置高级系统配置
{: #adv_config}

1. 请遵循[高级系统配置](https://console.bluemix.net/docs/bare-metal/configuring.html#advanced-system-configuration)准则，以获取有关**高级系统配置**窗口中的值的帮助。

SAP 主机名必须由最多 13 个字母数字字符组成。有关 SAP 主机名的更多信息，请参阅 [SAP Notes 611361](https://launchpad.support.sap.com/#/611361) 和 [129997](https://launchpad.support.sap.com/#/129997)。 

## 确认您的选择
{: #confirm_selections}

1. 在“结帐”页面上确认您的选择，并单击**云服务条款**和**第三方软件协议**。
2. 向下滚动到“创建帐户：输入帐单”，输入要用于计费的信用卡的**付款类型、姓名和卡号**以及**到期**（日期）。
3. 单击**提交订单**。您将重定向到包含您的订单号的屏幕。可以打印此屏幕，因为它也是您的订单回执。

将向您的个人档案中的电子邮件地址发送一封主题为“您的 _{{site.data.keyword.cloud_notm}} 订单 ## 已核准_”的确认电子邮件。此电子邮件用于通知您该服务器已核准，正在进行部署的过程中。部署之后，会向您发送另一个通知，告知您该服务器可用，可以通过 [{{site.data.keyword.cloud_notm}} 基础架构客户门户网站](https://control.softlayer.com)进行管理。

## 后续步骤

现在，您可以开始“管理 {{site.data.keyword.baremetal_short}}”。请参阅[管理 SAP HANA 环境](/docs/infrastructure/sap-hana/hana-manage-environment.html)。

