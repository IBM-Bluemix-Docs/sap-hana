---

copyright:
  years: 2017, 2019
lastupdated: "2019-06-04"

keywords: SAP HANA, network connectivity, VLANs, external storage, high availability, highly available, disaster recovery, HA, DR, VLANs,

subcollection: sap-hana

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Items to consider when planning your SAP landscape
{: #considerations}

The SAP systems in a landscape have specific requirements for connectivity, either among each other or to external systems. You also need to think about external storage for your landscape, and what to do if you decide to deploy VMware on your server.

## Network connectivity
{: #network_connectivity}

[{{site.data.keyword.cloud_notm}} network](/docs/infrastructure/sap-hana?topic=sap-hana-about_ibmcloud_for_sap#ibm_cloud_network) provided an overview of the {{site.data.keyword.cloud}} approach to network connectivity. Issues with network connectivity can cause significant delays for your project if you do not plan appropriately, regardless of how you plan to use your system.

In general, you have two interface choices for your IaaS-provisioned {{site.data.keyword.cloud_notm}} servers—the first is an external interface with a public IP. The second is an internal interface that is provided with a “private IP” in compliance with Request for Comment (RFC) 1918. You can also choose a single internal interface with a “private IP.” The external IP might be easier to use, but there is a potential risk, even though a basic firewall is installed and preconfigured.

The second option accesses the {{site.data.keyword.cloud_notm}} Virtual Private Network (VPN) through the {{site.data.keyword.cloud_notm}} infrastructure customer portal, or deploys a security device into your landscape. The security devices are offered for firewalls, network address conversion, VPN access, and other network functions. It is advised that your networking department speak with [{{site.data.keyword.cloud_notm}} Support](/docs/get-support?topic=get-support-getting-customer-support#getting-customer-support) after the layout of your landscape and the connectivity that is required on the SAP application layer are determined.

### VLANs
{: #vlans}

If you want to separate different types of network traffic in your landscape, you can order more virtual LANs (VLANs). Keep in mind that the additional VLANs only lead to traffic segregation, not increased performance. SAP generally recommends using 10 Gb networks for traffic between its application servers and SAP HANA databases, and for other SAP HANA clients, such as SAP Business Intelligence. If you want to segregate administrative access to your SAP HANA server from other clients, you should order another VLAN for your landscape. Another option is to separate the traffic through the public and private network, since further "physical" uplinks are not supported by {{site.data.keyword.cloud_notm}}. Follow the recommendations by SAP for [SAP HANA Tailored Data Center Integration (TDI))](https://blogs.saphana.com/2015/02/18/sap-hana-tailored-data-center-integration-tdi-overview/){: external}.

Access through VPN, as well as access from a jump box, allows transparent access to your SAP HANA instances from SAP HANA Studio.

## External storage
{: #external_storage}

In addition to the local storage, you might require more external storage to perform backups. For these requirements, you can order block storage or Network Attached Storage (NAS) as described in [Storage](/docs/infrastructure/sap-hana?topic=sap-hana-iaas-overview#storage). Since extra block storage and Network File System (NFS) data is transferred through the same physical adapters as all other network traffic, the impact needs to be kept in mind.

For external storage, it's important to calculate your project requirements before deciding on a storage solution. If you need to restore an SAP HANA system, then the IOPS of your storage have a significant influence on your restore window. Backup windows are not as critical with SAP HANA since all backups are online backups no matter how you configure SAP HANA.

For example, using {{site.data.keyword.cloud_notm}} {{site.data.keyword.blockstorageshort}}, you can calculate for an approximate 12 TB restore of SAP HANA at a maximum speed. You must create three physical storage devices (block storage iSCSI LUNs) because the maximum size per device is 4 TB. You can create a stripe over these three devices with the Linux Logical Volume Manager and create one logical device of 12 TB.

The 12 TB allows you 3x10 IOPS/GB, which is a total of 122,880 IOPS/GB at 16 KB. This gives you a restore time of 1.875 GB per second, or a total restore time of below 2 hours. Since the measurement for the IOPS is taken at a 50/50 distribution of read and write, you can consider the numbers as a lower boundary of restore performance. It is advisable to perform backup and restore tests if you rely on a certain restore window.

Both {{site.data.keyword.cloud_notm}} {{site.data.keyword.blockstorageshort}}, {{site.data.keyword.filestorage_full_notm}}, or NAS can serve as either backup space or as storage for additional software components that are installed on your server. {{site.data.keyword.cloud_notm}} Storage and NSA cannot, however, be used as storage for SAP HANA because these options do not fulfill the KPI criteria.

For more information, see [Getting started with {{site.data.keyword.blockstorageshort}}](/docs/infrastructure/BlockStorage?topic=BlockStorage-getting-started#getting-started) and [Getting started with {{site.data.keyword.filestorage_full_notm}}](/docs/infrastructure/FileStorage?topic=FileStorage-getting-started#getting-started).

## High availability and disaster recover scenarios
{: #ha_dr}

The {{site.data.keyword.cloud_notm}} environment does not support any preconfigured high availability (HA) scenarios. It does, however, let you implement HA solutions for SAP HANA through Red Hat Enterprise Linux HA extensions, such as an on-premises case.

SAP HANA system replication can be configured with an automated fail-over from one server to a replica. Follow the SAP documentation on system replication to determine the replication mode that best fits your application scenario and your level of disaster resilience. Depending on the replication mode, different network KPIs need to be fulfilled. Consult SAP recommendations on the network throughput and latency to determine the required throughput and maximum latency for your operation mode of choice. The {{site.data.keyword.cloud_notm}} network topology should be able to serve all the required configurations. Contact {{site.data.keyword.cloud_notm}} Support to determine the optimal setup for your scenario if you're not sure or if you want your disaster recovery site in a different data center to achieve maximum disaster resilience.

Be aware that SAP HANA Scale-Out (multi node) environments are still under evaluation. In other words, a standby-node for SAP HANA is not a current option in an {{site.data.keyword.cloud_notm}} environment.

For more information on high availability and disaster recovery, see [{{site.data.keyword.cloud_notm}} high-availability support](/docs/infrastructure/sap-hana?topic=sap-hana-ha#ha), and [Disaster recovery](/docs/infrastructure/sap-reference-architecture?topic=sap-reference-architecture-recommendations#dr).

For more information on system replication, and network throughput and latency, see
  * [How To Perform System Replication for SAP HANA)](https://www.sap.com/documents/2013/10/26c02b58-5a7c-0010-82c7-eda71af511fa.html){: external}
  * [Network Required for SAP HANA System Replication)](https://www.sap.com/documents/2014/06/babb2b55-5a7c-0010-82c7-eda71af511fa.html){: external}

For more information on setting up the HA cluster extensions for your Linux operating system, see
  * [Automated SAP HANA System Replication with Pacemaker on RHEL Setup Guide)](https://access.redhat.com/articles/1466063){: external}
  * [SAP HANA SR Performance Optimized Scenario](https://www.suse.com/docrep/documents/ir8w88iwu7/suse_linux_enterprise_server_for_sap_applications_12_sp1.pdf){: external}

## VMware ESXi server deployments
{: #vmware_server}

All of the servers in the {{site.data.keyword.cloud_notm}} SAP HANA offering are certified for VMware ESX, which makes SAP HANA deployable on virtual machines (VMs). If a server is ordered with VMware ESX, it's deployed with a preinstalled, basic configured ESX instance; no VM is deployed. Be aware that you are responsible for deploying the correct guest operating system in an ESX-based deployment. Follow the instructions defined in SAP Note 2414820 to choose an operating system version supported with SAP HANA on {{site.data.keyword.cloud_notm}}.

The sizing process for an ESX-based deployment differs from that of a bare metal server deployment. Follow the recommendations in *Architecture Guidelines and Best Practices for Deployments of SAP HANA on VMware vSphere Architecture and Technical Considerations Guide*. Overhead for the virtualization layer needs to be calculated, following the rules in the *Architecture...and Considerations Guide*. After the guest operating system is deployed on a VM, make sure that SAP HANA TDI KPIs are met. Check SAP Note 1943937 for details on testing the environment for compliance with SAP Support's prerequisites. The prerequisites need to be completed for every VM deployed on a specific server.

Several other SAP-defined rules must be followed to deploy SAP HANA in a virtualized environment. For production, follow the restrictions that are outlined in SAP Note 1995460. SAP Note 2024433 describes the rules for multiple VMs on one server.

For more information, see the following documentation:
  * [SAP Note 2414820](https://launchpad.support.sap.com/#/notes/2414820){: external}
  * [*Architecture Guidelines and Best Practices for Deployments of SAP HANA on VMware vSphere Architecture and Technical Considerations Guide*)](https://www.vmware.com/content/dam/digitalmarketing/vmware/en/pdf/whitepaper/sap_hana_on_vmware_vsphere_best_practices_guide-white-paper.pdf){: external}
  * [SAP Note 1943937](https://launchpad.support.sap.com/#/notes/1943937){: external}
  * [SAP HANA Tailored Data Center Integration Frequently Asked Questions)](https://www.sap.com/documents/2016/05/e8705aae-717c-0010-82c7-eda71af511fa.html){: external}
  * [SAP Note 1995460](https://launchpad.support.sap.com/#/notes/1995460){: external}
  * [SAP Note 2024433](https://launchpad.support.sap.com/#/notes/2024433){: external}
  * [SAP HANA Tailored Data Center Intgration (TDI) Overview)](https://blogs.saphana.com/2015/02/18/sap-hana-tailored-data-center-integration-tdi-overview/){: external}
