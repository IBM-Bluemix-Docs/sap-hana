---

copyright:
  years: 2017, 2020
lastupdated: "2020-04-22"

keywords: SAP HANA, {{site.data.keyword.cloud_notm}}, {{site.data.keyword.baremetal_short}}, data centers, VPN,

subcollection: sap-hana

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}

# SAP HANA on IBM Cloud IaaS Overview
{: #iaas-overview}

An Infrastructure-as-a-service (IaaS) environment consists of many components: data center, compute, connectivity, storage, and network.
{:shortdesc}

## Data centers
{: #data-centers}

With data centers across North and South America, Europe, Asia, and Australia, you can provision cloud resources where (and when) you need them. Each data center is connected to the {{site.data.keyword.cloud}} global private network, making data transfers faster and more efficient anywhere in the world.

View the network map for more information, see [Data Centers)](https://www.ibm.com/cloud/data-centers/){: external}.

## Bare metal servers
{: #bare-metal-servers}

{{site.data.keyword.baremetal_long}} are physical servers with limited customization capabilities. The servers are dedicated for your use, or your customer's, and not shared in any part, including server resources, with other {{site.data.keyword.cloud_notm}} customers, and are provisioned as an entire physical server running your choice of operating system (OS). The SAP HANA on {{site.data.keyword.cloud_notm}} offering consists of {{site.data.keyword.baremetal_short}} with the following operating systems:
* Red Hat Enterprise Linux 7.4 for SAP HANA
* SUSE Linux Enterprise Server 12 SP2 for SAP HANA
* VMware Server Virtualization 6.5

Because customization is limited on bare metal servers, faster provisioning times of between 1 - 4 hours are obtainable. Quick provisioning is helpful when you are trying to get an app to market before the competition.

You are offered an array of RAM and CPU combinations as the SAP-certified servers have a pre-configured amount of RAM and number of CPUs. The combination *cannot* be changed during the ordering process or through a support ticket after servers are deployed.

For more information, see [IBM Bare Metal Servers](https://www.ibm.com/cloud/bare-metal-servers){: external}.

SAP BW/4HANA is supported in production on single- and multi-node SAP HANA-certified bare metal servers. The servers are available in the following configurations-192 GB, to 1 TB, to 8 TB.
{: note}

## Network connectivity
{: #network-connectivity}

Virtual private network (VPN) connectivity to the {{site.data.keyword.cloud_notm}} Virtual Cloud Network is granted automatically when your {{site.data.keyword.cloud_notm}} account is set up. By default, your server has a public and private IP address. If you want your server to be private, you can either turn off the public interface after your server is provisioned or order your server as private.

While the network requirements for SAP HANA (10 Gb redundant network) are fulfilled by the {{site.data.keyword.cloud_notm}} offering, you might require certain latency and throughput key performance indicators (KPIs) to be met, depending on your application scenario. For more information on determining which data center to locate your SAP HANA server and deciding on the best network connectivity solution, see [Network connectivity](/docs/sap-hana?topic=sap-hana-considerations#network_connectivity) considerations.

For more information, see [Getting started with Virtual Private Networking](/docs/iaas-vpn?topic=VPN-getting-started) and the [*SAP HANA Network Requirements*)](https://www.sap.com/documents/2016/08/1cd2c2fb-807c-0010-82c7-eda71af511fa.html){: external} white paper.

## Storage
{: #storage}

Local storage is provided with your {{site.data.keyword.baremetal_short}} and uses the {{site.data.keyword.cloud_notm}} private network virtual LAN (VLAN) to help provide enterprise-grade security while not obstructing administrator access. For the SAP HANA-certified servers, it is designed and configured to meet the KPIs defined by SAP for both throughput and latency in compliance with the SAP HANA certification criteria. Local storage has the relevant size of the different subfile systems as defined by the SAP HANA Installation Guide (`data.log` and `shared`). No further adaptation needs to be done on your part.

There are two types of storage for {{site.data.keyword.cloud_notm}}-block and file-from which to choose to perform backups and restores for SAP HANA. Both types use input/output operations per second (IOPS), which are used to determine storage needs. IOPS are measured based on 16 KB block size with a 50/50 read/write mix. To achieve maximum IOPS on a volume, adequate network resources need to be in place. Other considerations include private network usage outside of storage and host side, and application-specific tunings (for example, IP stacks and queue depths). For more information, see [Getting started with Block Storage](/docs/BlockStorage?topic=BlockStorage-getting-started#getting-started) and [Getting started with File Storage](/docs/FileStorage?topic=FileStorage-getting-started#getting-started).

## Deployment and management
{: #deployment-and-management}

{{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} are deployed through the {{site.data.keyword.cloud_notm}} customer portal or API after you create your {{site.data.keyword.cloud_notm}} customer account. The servers can be managed through the customer portal, API, or command line interface (CLI). For more information, see [IVM Bare Metal Servers](https://www.ibm.com/cloud/bare-metal-servers){: external}.

## Support
{: #support}

[{{site.data.keyword.cloud_notm}} Customer Support](/docs/get-support?topic=get-support-getting-customer-support#getting-customer-support) handles any support questions and cases that might arise through various outlets, including chat, phone, and case-based support. Customer support is offered at no cost to all {{site.data.keyword.cloud_notm}} customers and covers most cases that are placed each day. For more information, see [Getting Customer Support](/docs/get-support?topic=get-support-getting-customer-support#getting-customer-support).

You can also continue to create tickets through SAP Support that are related to your {{site.data.keyword.cloud_notm}} IaaS and SAP products. For more information, see [SAP Support)](https://support.sap.com/en/index.html){: external} and [SAP Note 2414820)](https://launchpad.support.sap.com/#/notes/2414820){: external}.

## Installing SAP HANA
{: #installing-sap-hana}

You must have a current license for the SAP HANA database if you are a bring-your-own-license customer, specifically verifying access to the SAP HANA Platform Edition media.

Your SAP HANA software should be installed by a certified SAP HANA installer who has completed the SAP HANA installation certification course. For more information, see [SAP Support)](https://support.sap.com/en/index.html){: external}.
