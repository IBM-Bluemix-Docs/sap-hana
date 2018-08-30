---



copyright:
  years: 2018
lastupdated: "2018-08-29"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 5. Configuring your IBM Cloud infrastructure to support SAP HANA multi-node
{: #multi-node-storage}

{{site.data.keyword.cloud_notm}} supports SAP HANA multi-node storage for online analytical processing (OLAP) workloads, such as SAP Business Warehouse (SAP BW) and SAP BW/4HANA. The {{site.data.keyword.cloud}} solution for SAP HANA multi-node consists of up to 15+1 nodes (15 worker nodes, plus one standby) for up to 30 TB of memory used for one system.

With multi-node, multiple SAP HANA nodes build a single SAP HANA system. Data is distributed among these nodes, which form a single database. The multi-node configuration supports scalability and high availability through the standby configuration. The {{site.data.keyword.cloud_notm}} offering for this configuration follows [SAP HANA Tailored Data Center Integration](https://blogs.saphana.com/2015/02/18/sap-hana-tailored-data-center-integration-tdi-overview/) (TDI), and uses {{site.data.keyword.cloud_notm}} SAP-HANA certified servers for centralized, shared enterprise storage.

*Note* that you must follow the configuration guidelines outlined under (Ordering your multi-node system)[#ordering] to fulfill the SAP HANA TDI requirements and be supported by SAP.

Follow the guidelines in [Sizing SAP HANA](https://help.sap.com/viewer/eb3777d5495d46c5b2fa773206bbfb46/2.0.00/en-US/d4a122a7bb57101493e3f5ca08e6b039.html) to determine the required size for your target SAP HANA system, including the total amount of memory and storage required for your deployment. The sizing requirements help you establish the number of SAP HANA nodes required for your SAP HANA multi-node system, and the storage required to host the data.

## Reviewing the network topology and storage layout
{: #reviewing-topology}

Figure 1 shows the network topology required for the {{site.data.keyword.cloud_notm}} Infrastructure as a Service SAP HANA TDI setup.

Figure 1. IBM Cloud Infrastructure as a Service SAP HANA TDI network topology

![Figure 1. IBM Cloud Infrastructure as a Service SAP HANA TDI network topology](/images/SAP-BW.png "IBM Cloud Infrastructure as a Service SAP HANA TDI network topology")

## Setting up your prerequisites
{: #prerequisites}

SAP HANA multi-node requires certain networks be in place to function. Before you order other components of your system, these networks must be set up correctly, together with the database nodes. You need
* A client-side network, which connects the SAP Advanced Business Application Programming (SAP ABAP) application servers, SAP HANA Studio clients, and any other network client to the multi-node system. The network throughput and availability options depend on the usage scenario of your SAP HANA multi-node system. Consider the amount of data transferred from and to the SAP HANA database, and the availability key performance indicators (KPIs), required for your application.
* A storage network, which is required to connect to the back-end {{site.data.keyword.blockstoragefull}} and {{site.data.keyword.filestorage_full_notm}}. To maximize performance and redundancy, a 10 Gb network with two interfaces under Linux bonding with Link Aggregation Control Protocol (LACP) is required. Without the provided performance figures from the SAP HANA sizing guidelines, SAP HANA TDI KPIs can't be met.
* An internode network for SAP HANA internal communication that is set up equivalent to the storage network. The internode network is only used for communication between nodes and the data transfer that might be required between the nodes during operations. This required network configuration is on two physical 10 Gb adapters under Linux bonding with LACP.

## Ordering your multi-node system
{: #ordering}

To meet the performance and throughput KPIs required by SAP, your VLANs, storage, and compute nodes must be ordered in the same data center. If your components are distributed over multiple data centers, SAP will not support your multi-node system.

1. Order three different VLANs and servers with four adapters (two private and two public). For more information on order VLANs, see [Step 1 Ordering Primary and Public VLANs](https://console.bluemix.net/docs/infrastructure/virtualization/advanced-single-site-vmware-reference-architecturesoftlayer.html#step-1-ordering-primary-public-and-private-vlans). For more information on ordering your servers, see [2. Setting up your infrastructure](https://console.bluemix.net/docs/infrastructure/sap-hana/hana-setting-up-infrastructure.html#set_up_infrastructure).
2. Set up the initial private VLAN as a "storage VLAN."
3. [Open a ticket](https://console.bluemix.net/docs/get-support/howtogetsupport.html#open-ticket) with {{site.data.keyword.cloud_notm}} Support to
   a. Move the public interfaces to the second VLAN
   b. Order two more adapters to be assigned to the third VLAN, which is the client VLAN

You now have the number of servers based on your sizing effort, and your network is set up so that
* Storage can be attached to all nodes
* The SAP HANA multi-node installation can be carried out after the storage has been attached

Your storage LAN connections and internode connections are configured by the {{site.data.keyword.cloud_notm}} deployment. Be sure to order the connections with two 10 Gb adapters each with failover configuration. This setup ensures the correct Linux bonding and LACP configuration. Contact the {{site.data.keyword.cloud_notm}} Support team with any questions.

There are specific performance criteria that must be met by {{site.data.keyword.IBM_notm}} {{site.data.keyword.blockstorageshort}} (Endurance) and {{site.data.keyword.IBM_short}} {{site.data.keyword.filestorage_short}} (Performance). For data volumes, 2 TB Endurance storage with a performance KPI of 10 IOPS/GB is required for each worker node. One additional volume of the same size is required as SAP HANA shared storage and will be shared by all nodes.

For log volumes, one 512 GB volume of Performance storage is required for each node with a performance KPI of 10 K IOPS.

You can use the steps under [Provisioning and Managing {{site.data.keyword.blockstorageshort}}](https://console.bluemix.net/docs/infrastructure/BlockStorage/provisioning-block_storage.html#provisioning-and-managing-block-storage) or [Provisioning and Managining {{site.data.keyword.filestorage_full_notm}}](https://console.bluemix.net/docs/infrastructure/FileStorage/provisioning-file-storage.html#provisioning-and-managing-ibm-file-storage-for-ibm-cloud) to order your Endurance and Performance storage.

## Configuring SAP HANA multi-nodes
{: #configuring}

The SAP HANA shared volume, and each of the data and log volumes, must be accessible to all nodes. This approach means all volumes are accessible to the entire storage VLAN, which you configured under [Ordering your multi-node system](#ordering). If you don't want to list each IP address involved, make the volumes accessible to the entire IP subnet of the VLAN.

Follow the guidance in [SAP HANA on NetApp FAS Systems with NFS](https://www.netapp.com/us/media/tr-4290.pdf) to configure your SAP HANA multi-node system. Use the following Network File System (NFS) mount options for each volume to mount:

`rw,bg,hard,timeo=600,intr,noatime,vers=4,minorversion=1,lock,rsize=1048576,wsize=1048576` in `/etc/fstab`.

These options have been tested by NetApp and {{site.data.keyword.cloud_notm}}. Contact {{site.data.keyword.cloud_notm}} Support if you plan to change any of the mount options or values.

After you mount all of your volumes to all the nodes, your multi-node servers are configured and ready to install the SAP HANA multi-node database. Follow the steps in the [SAP HANA Server Installation and Update Guide](https://help.sap.com/viewer/2c1988d620e04368aa4103bf26f17727/2.0.03/en-US) to install an SAP HANA database of your required version.