---

copyright:
  years: 2017, 2019
lastupdated: "2019-12-03"

keywords: SAP HANA, {{site.data.keyword.cloud_notm}}, infrastructure, {{site.data.keyword.baremetal_short}}, SAP-certified infrastructure, deployment, BYOL,

subcollection: sap-hana

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}

# 2. Setting up your infrastructure
{: #set_up_infrastructure}

The guidance for setting up your SAP HANA {{site.data.keyword.baremetal_long}}, network, security, storage, and operating system (OS) is in the following section. Consult the [Design Decision Tool](https://github.com/ibm-cloud-architecture/infrastructure-design-decision-tool){: external} or [{{site.data.keyword.cloud_notm}} Support](/docs/get-support?topic=get-support-getting-customer-support#getting-customer-support) for more information.
{:shortdesc}

## Ordering your server
{: #order-server}

The {{site.data.keyword.cloud}} console requires a unique log-in IDs, which is an {{site.data.keyword.IBM_notm}}id. Use the following steps to order your {{site.data.keyword.baremetal_short}}. Additional information can be found under [Building a custom bare metal server](/docs/bare-metal?topic=bare-metal-ordering-baremetal-server#ordering-baremetal-server).

1. Log in to the [{{site.data.keyword.cloud_notm}} console](https://cloud.ibm.com){: external} with your unique credentials.
2. Click **Create resource** > **Compute** > **Infrastructure** > **Bare Metal Server** > **Continue**.
3. Enter the number of servers you are ordering in the **Quantity** field.
4. Enter a **Hostname**, which is a permanent or temporary name for your servers. SAP Hostnames must consist of a maximum of 13 alpha-numeric characters. See [SAP Notes 611361](https://launchpad.support.sap.com/#/611361){: external} and [129997](https://launchpad.support.sap.com/#/129997){: external} for more SAP Hostname details. Click **Information** for formatting specifics.
6. Enter a **Domain**, which is the identification string that defines administrative control within the internet. Click **Information** for formatting specifics.
7. **Billing** defaults to **Monthly**. At this time, 1-year contract and 3-year contract are not available for SAP-certified servers.
8. The data centers displayed under **Location** depend on product availability within a particular data center. Select your data center.
9. Click **All servers** > **SAP certified**. SAP HANA-certified servers are identified with an **.H** under CPU Model.

  For more information on how to decipher the server name, see [Deciphering the server names](/docs/infrastructure/sap-hana?topic=sap-hana-determine_configuration#server-names).
  {: note}

## Configuring your server
{: #configure_server}

Select your SAP-certified server and OS.

1. Select the appropriate SAP HANA-certified server for your workload from the URLs in [Determining your configuration](/docs/infrastructure/sap-hana?topic=sap-hana-determine_configuration).

  The BI.S3.H2192 and BI.S3.H238 servers are also available for **Hourly** billing.
  {: note}

2. **Server**, **RAM**, and your private storage option default based on your server selection and cannot be changed. {{site.data.keyword.IBM_notm}} {{site.data.keyword.blockstorageshort}} for {{site.data.keyword.cloud_notm}} or {{site.data.keyword.filestorage_full_notm}} are ordered after you have ordered your server.
3. Select your **Image** (operating system) from either Red Hat or SUSE and select the specific operating system, or VMware hypervisor for your server.

  If you are bringing your own license (BYOL) for your operating system, select **Other** > **No Operating System**. For more information, see [Bring your own license](#byol).
  {: note}

  If you are using SAP Business One, you need to select one of the [servers](/docs/infrastructure/sap-hana?topic=sap-hana-determine_configuration) that supports it and SUSE 12 SP4 as your image.
  {: note}

## Adding storage disks
{: #adding-storage-disks}

In the next step, you will select the type and number of disks you want to add to your configuration. You can also select different options for Redundant Array of Independent Disks (RAID) storage groups and partitioning layouts on-top of the RAID storage groups. See [About RAID](/docs/bare-metal?topic=bare-metal-bm-raid-levels) or [{{site.data.keyword.cloud_notm}} Support](/docs/get-support?topic=get-support-getting-customer-support#getting-customer-support) for more information.

1. Under **Type**, select the appropriate RAID.
2. **Disks**, **Hot Spare**, and **Disk Media** have default values based on your selection. Select a **Disk Size** that covers the total amount of storage you need.

## Network interface
{: #network-options}

1. Select an **Uplink Port Speed**.
2. Enter values the **VLAN** and **Subnet** fields
3. Leave the default values for all other fields.
4. Review your Order Summary.
5. Select **I read and agree to the following Third-Party Service Agreements**.

  You can create your server, save the order as a quote to provision at a later time, or add the order an estimate, which may include multiple services.
  {: note}

6. Click **Create** to be redirected to the Checkout page after your order has been verified.

You are redirected to a page with your order number. You can print the page, because it's your receipt. A confirmation email with the subject Your _{{site.data.keyword.cloud_notm}} Order ## has been approved_ is be sent to the email address in your profile. This email is notice that your server has been approved and is in the process of being deployed. After it is deployed, another notice is sent notifying you that the server is available and can be managed through the [{{site.data.keyword.cloud_notm}} console](https://cloud.ibm.com/){: external}. You can check Device Details from the {{site.data.keyword.cloud_notm}} console (Menu icon ![Menu icon](../../icons/icon_hamburger.svg) > Resource List > Devices) for a status of the provisioning steps. Click the **Device Name** that matches your device's Hostname and Domain to see its status.

## Bring your own license
{: #byol}

When you have your own operating system license, you install it on your {{site.data.keyword.baremetal_short}} based on the vendor's instructions. For more information, see [The no OS option](/docs/bare-metal?topic=bare-metal-bm-no-os#bm-no-os).

## Next Steps
{: #next-steps-set-up-infrastructure}

You are now ready to begin Managing your {{site.data.keyword.baremetal_short}}. See [Managing your SAP HANA environment](/docs/infrastructure/sap-hana?topic=sap-hana-manage_environment#manage_environment) for your next steps.
