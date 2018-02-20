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

# SAP HANA on IBM Cloud IaaS Overview
{: #iaas-overview}

An Infrastructure-as-a-server (IaaS) environment consists of many components: data center, compute, connectivity, storage, and network. 

## Data centers

With data centers across North and South America, Europe, Asia, and Australia, you can provision cloud resources where (and when) you need them. Each data center is connected to the {{site.data.keyword.cloud_notm}} global private network, making data transfers faster and more efficient anywhere in the world.

For more information, see [Data Centers](https://www.ibm.com/cloud-computing/bluemix/data-centers){: new_window}.

## Bare metal servers

{{site.data.keyword.baremetal_long}} are physical servers with limited customization capabilities. The servers are dedicated for your use, or your customer's, and not shared in any part, including server resources, with other {{site.data.keyword.cloud_notm}} customers, and are provisioned as an entire physical server running your choice of operating system (OS). The OS for the SAP HANA offering is Red Hat Linux for SAP HANA 6.7 OS.

Because customization is limited on bare metal servers, faster provisioning times of between 1 - 4 hours are obtainable. Quick provisioning is helpful when you are trying to get an app to market before the competition.

You are offered an array of RAM and CPU combinations as the SAP-certified servers have a pre-configured amount of RAM and number of CPUs. The combination *cannot* be changed during the ordering process or through a support ticket after servers are deployed.

For more information, see [About bare metal servers](https://console.bluemix.net/docs/bare-metal/index.html#about-bare-metal-servers). 

## Network connectivity

Virtual private network (VPN) connectivity to the {{site.data.keyword.cloud_notm}} Virtual Cloud Network is granted automatically when your {{site.data.keyword.cloud_notm}} account is set up. By default, your server has a public and private IP address. If you want your server to be private, you can either turn off the public interface after your server is provisioned or order your server as private. 

While the network requirements for SAP HANA (10 Gb redundant network) are fulfilled by the {{site.data.keyword.cloud_notm}} offering, you might require certain latency and throughput key performance indicators (KPIs) to be met, depending on your application scenario. For more information on determining which data center to locate your SAP HANA server and deciding on the best network connectivity solution, see [Network connectivity](/docs/infrastructure/sap-hana/hana-considerations.html#network_connectivity) considerations.

For more information, see [Getting started with Virtual Private Networking](https://console.bluemix.net/docs/infrastructure/iaas-vpn/getting-started.html#getting-started-with-virtual-private-networking-vpn-) and the [*SAP HANA Network Requirements*](https://www.sap.com/documents/2016/08/1cd2c2fb-807c-0010-82c7-eda71af511fa.html) white paper.

## Storage
{: #storage}

Local storage is provided with your {{site.data.keyword.baremetal_short}} and uses the {{site.data.keyword.cloud_notm}} private network virtual LAN (VLAN) to help provide enterprise-grade security while not obstructing administrator access. For the SAP HANA-certified servers, it is designed and configured to meet the KPIs defined by SAP for both throughput and latency in compliance with the SAP HANA certification criteria. Local storage has the relevant size of the different subfile systems as defined by the SAP HANA Installation Guide (`data.log` and `shared`). No further adaptation needs to be done on your part.

There are two types of storage for {{site.data.keyword.cloud_notm}}-block and file-from which to choose to perform backups and restores for SAP HANA. Both types use input/output operations per second (IOPS), which are used to determine storage needs. IOPS are measured based on 16 KB block size with a 50/50 read/write mix. To achieve maximum IOPS on a volume, adequate network resources need to be in place. Other considerations include private network usage outside of storage and host side, and application-specific tunings (for example, IP stacks and queue depths). For more information, see [Getting started with Block Storage](https://console.bluemix.net/docs/infrastructure/BlockStorage/index.html#getting-started-with-block-storage) and [Getting started with File Storage](https://console.bluemix.net/docs/infrastructure/FileStorage/index.html#getting-started-with-file-storage).

{{site.data.keyword.cloud_notm}} also offers Network Attached Storage (NAS) if you are looking to for a quick, cost-efficient, backup solution for your devices. NAS can be mounted through the Network File System (NFS) and can be used with File Transfer Protocol (FTP) with both Parallels Plesk Panel and cPanel@WHM.

NAS storage can be used for any purpose, but, in this case, is *not* to be used for SAP HANA data or log files. The storage does not fulfill the criteria regarding I/O KPIs. However, the storage can be used for backup devices and all other kinds of data. It can be used by SAP HANA as backup devices, for data and log files, when mounted through NFS.  
  
NAS and FTP storage are billed monthly and are available in various storage sizes. You can primarily interact with your NAS and FTP storage within the command line or terminal with the OS, or through point-and-click interactions on the panels within the {{site.data.keyword.cloud_notm}} infrastructure customer portal. Within the customer portal, NAS details and usage can be used, but the service cannot be manipulated outside the command line, kernel, or control panel.

For more information on NAS in an {{site.data.keyword.cloud_notm}} environment, see [Getting started with NAS](https://console.bluemix.net/docs/infrastructure/network-attached-storage/index.html#getting-started-with-nas).

## Deployment and management

{{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} are deployed through the {{site.data.keyword.cloud_notm}} infrastructure customer portal or API after you create your {{site.data.keyword.cloud_notm}} customer account. The servers can be managed through the customer portal, API, or command line interface (CLI). For more information, see [About bare metal servers](https://console.bluemix.net/docs/bare-metal/index.html#about-bare-metal-servers).

## Support

[{{site.data.keyword.cloud_notm}} Customer Support](https://console.bluemix.net/docs/support/index.html#getting-customer-support) handles any support questions and issues that might arise through various outlets, including chat, phone, and ticket-based support. Customer support is offered at no cost to all {{site.data.keyword.cloud_notm}} customers and covers most tickets that are placed each day. For more information, see [Getting Customer Support](https://console.bluemix.net./docs/support/index.html#getting-customer-support).

You can also continue to create tickets through SAP Support that are related to your {{site.data.keyword.cloud_notm}} IaaS and SAP products. For more information, see [SAP Support](https://support.sap.com/en/index.html) and [SAP Note 2414820](https://launchpad.support.sap.com/#/notes/2414820).

## Installing SAP HANA

Your SAP HANA software must be installed by a certified SAP HANA installer who has completed the SAP HANA installation certification course. For more information, see [Who Can Install SAP HANA?](http://www.saphanacentral.com/p/who-can-install-sap-hana.html).
