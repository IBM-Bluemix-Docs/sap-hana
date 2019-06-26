---

copyright:
  years: 2018, 2019
lastupdated: "2019-06-04"

keywords: SAP HANA, {{site.data.keyword.cloud_notm}}, high availability, highly available, SPOF, VLANs, HA, DR, disaster recovery, SAP NetWeaver

subcollection: sap-hana

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:table: .aria-labeledby="caption"}


# IBM Cloud high-availability support
{: #ha}

The {{site.data.keyword.cloud}} Infrastructure as a Service (IaaS) offers you a robust compute environment with an optional operating system (OS) deployment on top that supports high availability (HA) solutions. The solution is based on the supported OS version, which is discussed in [SAP Note 2414097](https://launchpad.support.sap.com/#/notes/2414097){: external}. The HA solution is restricted to the ordered OS licenses that come with your deployment, or third-party licenses, such as bring your own license (BYOL). Be sure to discuss HA details with {{site.data.keyword.cloud_notm}} Support before your deployment.

The operating systems supported and deployed by {{site.data.keyword.cloud_notm}} for SAP are
* Linux [Red Hat Enterprise Linux (RHEL) or SUSE Enterprise Linux Server (SLES] supports both SAP NetWeaver and SAP HANA HA solutions. There are minor restrictions in the {{site.data.keyword.cloud_notm}} environment, which are discussed in [Overview of SAP NetWeaver high-availability configurations](#overview-configs).
* Microsoft Windows supports SAP NetWeaver HA solution only (because of SAP HANA database restrictions).

## Overview of SAP NetWeaver high-availability configurations
{: #overview-configs}

There are numerous documents that provide in-depth help on planning and installing an HA environment for SAP services. The documents include information on failover, replication, scale-out, and disaster recovery (DR). References to certain documents are provided where appropriate.

All the operating systems and distributions supported by {{site.data.keyword.cloud_notm}} for an SAP deployment (Windows, Linux RHEL, and SLES) come with high-availability software and specific extensions. Following are the supported OS and distributions.

* [New Failover Clustering Improvements in Windows Server 2012 and Its Benefits for SAP NetWeaver High Availability](https://blogs.sap.com/2013/10/16/new-failover-clustering-improvements-in-windows-server-2012-and-its-benefits-for-sap-netweaver-high-availability/){: external} provides a description based on Microsoft Windows Server Failover Clustering (WFSC) on the Windows OS with SAP NetWeaver.

* There are two references for guidance on deploying SAP NetWeaver in a Linux-based HA environment with Linux Pacemaker:
  * SUSE SAP NetWeaver High Availability Cluster 7.40 Setup Guide
  * Deploying Highly Available SAP NetWeaver-based Servers Using Red Hat Enterprise Linux HA add-on with Pacemaker

* [Building High Availability for SAP NetWeaver and SAP HANA on Linux ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://support.sap.com/content/dam/SAAP/SAP_Activate/AGS_70.pdf){: external} is an SAP best-practice document and provides an in-depth technical description with a strong focus on SAP HANA.

* [SAP NetWeaver High Availability and Business Continuity in Virtual Environments with VMware and Hyper-V on Microsoft Windows](https://www.sap.com/documents/2015/07/508b62bc-5b7c-0010-82c7-eda71af511fa.html){: external} covers the virtualization aspects if you’re planning to implement HA on virtualized servers.

For more high-availability products certified by SAP partners for high-availability scenarios, see [High Availability Partner Information](https://wiki.scn.sap.com/wiki/display/SI/High+Availability+Partner+Information){: external}.
For non-HANA SAP databases, more information on HA fail-over, and DR configurations, is available in your database documentation.

Note that shared access to Network File System (NFS)/Common Internet File System (CIFS) storage, or shared access to iSCSI-based logical unique number storage (LUNS), is usually required to support system failover. Local storage, combined with a replication method, is usually required to support a DR-like setup. As with on-premises installations, check the performance and latency requirements of the database product when planning your deployment.

## Extra guidance
{: #extra-guide}

[Quorum-based storage](#quorum) and [Network considerations](#network) provide guidance that you need to consider during your deployment. Apart from the considerations outlined in these sections, installing SAP NetWeaver and its database system in an HA environment doesn’t differ from other on-premises installations.

### Quorum-based storage
{: #quorum}

Because of security restrictions in the {{site.data.keyword.cloud_notm}} IBM Cloud environment, network-based access to remote management devices through the Intelligent Platform Management Interface (IPMI) isn’t available. Cluster environments typically use IPMI-based components for the “fencing of cluster nodes” to always ensure a quorum. In the absence of an IPMI-enabled device, shared storage devices are used. In an {{site.data.keyword.cloud_notm}} environment, shared storage devices are implemented by deploying an iSCSI LUN to your servers as a quorum device. For example, a File Share Witness (FSW) on a Microsoft Cluster, and for storage-based death (SDB) for Linux Pacemaker's Stonith.
* Click [here](http://linux-ha.org/wiki/Cluster_Concepts){: external} for more information on Linux High Availability Cluster Concepts.
* Click [here](https://docs.microsoft.com/en-us/windows-server/failover-clustering/manage-cluster-quorum){: external} for more information on configuring and managing quorum servers for Windows Server 2012 and Windows Server 2012 R2.

{{site.data.keyword.cloud_notm}} Storage has built-in HA capabilities, so a single shared iSCSI LUN won’t introduce a Single Point Of Failure (SPOF) because your network layout is redundant. However, the specifics of your cluster product might require multiple quorum devices.

### Network considerations
{: #network}

An {{site.data.keyword.cloud_notm}}-based installation comes with one of the following network configurations:
* Private network
* Public network
* Public and private networks
* Two private networks (on special demand)

Like on-premises installations, extra network adapters can be ordered depending on the physical restrictions of the hardware. The restriction is the same for on-premises installations. Ordering redundant network adapters during hardware deployments helps prevent  SPOF across your network topology. Redundant adapters are set up in a failover configuration with Link Aggregation Control Protocol (LACP). For Linux, the setup uses bonding interfaces, and teaming adapters are used for Microsoft Windows. The {{site.data.keyword.cloud_notm}} switch infrastructure these adapters are connected to is redundant, so no new SPOFs are introduced. The redundant infrastructure can be used by the ordered VLANs.

Depending on the network requirements, such as replication scenarios in a DR setup, you must check the location of the connected devices and any new network requirements specific to the product in question. In some cases, the {{site.data.keyword.cloud_notm}} snapshot storage-based replication might fulfill your requirements. Check with {{site.data.keyword.cloud_notm}} Support to determine which solution works best for your business process needs.
