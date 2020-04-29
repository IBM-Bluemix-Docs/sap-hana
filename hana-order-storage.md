---

copyright:
  years: 2018, 2020
lastupdated: "2020-22"

keywords: SAP HANA, {{site.data.keyword.cloud_notm}} storage, {{site.data.keyword.blockstorageshort}}, {{site.data.keyword.filestorage_full_notm}}

subcollection: sap-hana

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 1. Ordering storage
{: #order_storage}

{{site.data.keyword.blockstoragefull}} and {{site.data.keyword.filestorage_full_notm}} are ordered after you deploy your {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}.
{:shortdesc}

## Ordering {{site.data.keyword.cloud_notm}} storage
{: #ibm_storage}

{{site.data.keyword.cloud_notm}} storage LUNS ({{site.data.keyword.blockstorageshort}}) and volumes ({{site.data.keyword.filestorage_full_notm}}) can be provisioned with two options - Endurance and Performance. Endurance tiers feature pre-defined performance levels and other features, such as [snapshot](/docs/BlockStorage?topic=BlockStorage-snapshots) and replication. A custom Performance environment is built with allocated input/output/operations per second (IOPS) between 100 and 1,000.

[Getting started with Block Storage](/docs/BlockStorage?topic=BlockStorage-getting-started) and [Getting started with File Storage](/docs/FileStorage?topic=FileStorage-getting-started) provides you with provisioning considerations, how to submit your order (if you didn't order when you originally provisioned your server), and connecting to and managing your new storage.

Use the following links to learn more about {{site.data.keyword.blockstorageshort}} and {{site.data.keyword.filestorage_full_notm}}:
* [Learn about {{site.data.keyword.blockstorageshort}}](/docs/BlockStorage?topic=BlockStorage-About)
* [Learn about {{site.data.keyword.filestorage_full_notm}}](/docs/FileStorage?topic=FileStorage-about)

Provisioning steps can be found under
* [Ordering Block Storage through the Console](/docs/BlockStorage?topic=BlockStorage-orderingthroughConsole)
* [Ordering File Storage through the Console](/docs/FileStorage?topic=FileStorage-getting-started&topic-FileStorage-orderConsole#submitting-your-order)

## Next Steps
{: #next-steps-order-storage}

  [2. Securing your environment](/docs/sap-hana?topic=sap-hana-secure_environment#secure_environment)

  [3. Installing your guest OS on the ESX hypervisor (optional)](/docs/sap-hana?topic=sap-hana-install_guest_os#install_guest_os)

  [4. Downloading and installing SAP software and applications](/docs/sap-hana?topic=sap-hana-install_sap#install_sap)

  [5. Configuring your IBM Cloud infrastructure to support SAP HANA multi-node](/docs/sap-hana?topic=sap-hana-multi-node-storage#multi-node-storage)
