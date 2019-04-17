---

copyright:
  years: 2017, 2019
lastupdated: "2019-02-28"

keywords: SAP HANA, {{site.data.keyword.cloud_notm}}, infrastructure, {{site.data.keyword.baremetal_short}}, SAP-certified infrastructure, deployment, BYOL,

subcollection: sap-hana

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}

# 2. Setting up your infrastructure
{: #set_up_infrastructure}

The guidance for setting up your SAP HANA {{site.data.keyword.baremetal_long}}, network, security, storage, and operating system (OS) are in the following section. Contact [{{site.data.keyword.cloud_notm}} Support](/docs/get-support?topic=get-support-getting-customer-support#getting-customer-support) with any questions.

## Ordering your server
{: order-server}

Use the following steps to order your {{site.data.keyword.baremetal_short}}. Additional information can be found under [Building a custom bare metal server](/docs/bare-metal?topic=bare-metal-ordering-baremetal-server#ordering-baremetal-server).

1. Log in to the [{{site.data.keyword.cloud_notm}} infrastructure customer portal ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com){: new_window} with your unique credentials.
2. Click **Account** > **Place an Order** on the Account Summary page.
3. Click the **Monthly** link under {{site.data.keyword.baremetal_short}} on the Devices page. The Server List appears; the SAP Certified Servers are at the top of the list.
4. Click the hyperlink under **STARTING PRICE PER MONTH** to select the appropriate server and be taken to the Configure/Order page. SAP HANA-certified servers are identified with an **-H** under CPU Model.  

The BI.S3.H2192 and BI.S3.H238 servers are also available for **Hourly** billing.
{: note}

5. Enter the number of servers you are ordering in the **Quantity** field and select your **Data Center**.
6. **Server**, **RAM**, and your private storage option default based on your server selection and cannot be changed. {{site.data.keyword.IBM_notm}} {{site.data.keyword.blockstorageshort}} for {{site.data.keyword.cloud_notm}} or {{site.data.keyword.filestorage_full_notm}}, and Network Attached Storage (NAS) are ordered after you have ordered your server.
7. Select your **Operating System** from either Red Hat or SUSE and select the specific operating system, or VMware hypervisor for your server.

If you are bringing your own license (BYOL) for your operating system, select **Other** > **No Operating System**. For more information, see [Bring your own license](#byol).
{ :note}

## Selecting your server options
{: #select_options}

In the next step, you will select the type and number of disks you want to add to your configuration. You can also select different options for Redundant Array of Independent Disks (RAID) storage groups and partitioning layouts on-top of the RAID storage groups. For more information, see [About RAID](/docs/bare-metal?topic=bare-metal-about-raid#about-raid) or [{{site.data.keyword.cloud_notm}} Support](/docs/get-support?topic=get-support-getting-customer-support#getting-customer-support).

1. Under **SAP Certified Servers**, make your selection based on how you plan to use your server. Consult the [Design Decision Tool ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://github.com/ibm-cloud-architecture/infrastructure-design-decision-tool){: new_window} (scroll down to the tool) or [{{site.data.keyword.cloud_notm}} Support](/docs/get-support?topic=get-support-getting-customer-support#getting-customer-support) for more information
2. Click **Add to order** at the bottom of the page.

## Setting up Advanced System Configurations
{: #adv_config}

1. Follow the [Advanced System Configuration](/docs/bare-metal?topic=bare-metal-ordering-baremetal-server#ordering-baremetal-server) guidelines for help with the values in the **Advanced System Configuration** window.

SAP host names must consist of a maximum of 13 alpha-numeric characters. For more information on SAP host name, see [SAP Notes 611361 ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://launchpad.support.sap.com/#/611361){: new_window} and [129997 ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://launchpad.support.sap.com/#/129997){: new_window}.

## Confirming your selections
{: #confirm_selections}

1. Confirm your selections on the Checkout page and click **Cloud Service terms** and **3rd Party Software Agreement**.
2. Scroll down to Create Account: Enter Billing and enter the **Payment Type, Name, Card**, and **Expiration** (date) for the credit card to be used for billing.
3. Click **Submit Order**. You are redirected to a screen with your order number. You can print the screen because it is also your order receipt.

A confirmation email with the subject Your _{{site.data.keyword.cloud_notm}} Order ## has been approved_ is sent to the email address in your profile. This email is notice that your server has been approved and is in the process of being deployed. After it is deployed, another notice is sent notifying you that the server is available and can be managed through the [{{site.data.keyword.cloud_notm}} infrastructure customer portal ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://control.softlayer.com){: new_window}.

## Bring your own license
{: #byol}

When you have your own operating system license, you install it on your {{site.data.keyword.baremetal_short}} based on the vendor's instructions. For more information, see [The no OS option](/docs/bare-metal?topic=bare-metal-bm-no-os#bm-no-os).

## Next Steps

You are now ready to begin Managing your {{site.data.keyword.baremetal_short}}. See [Managing your SAP HANA environment](/docs/infrastructure/sap-hana?topic=sap-hana-manage_environment#manage_environment) for your next steps.
