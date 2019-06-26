---

copyright:
  years: 2017, 2019
lastupdated: "2019-006-26"

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

The guidance for setting up your SAP HANA {{site.data.keyword.baremetal_long}}, network, security, storage, and operating system (OS) are in the following section. Contact [{{site.data.keyword.cloud_notm}} Support](/docs/get-support?topic=get-support-getting-customer-support#getting-customer-support) with any questions.

## Ordering your server
{: #order-server}

You have two options to get to provision your {{site.data.keyword.baremetal_short}}. The first is through the [{{site.data.keyword.cloud}} console](#using-console) and the second is through the [{{site.data.keyword.slportal}}](#using-portal). The console and the {{site.data.keyword.cloud}} infrastructure customer portal require unique log-in IDs, which is an {{site.data.keyword.IBM_notm}}id. Use the following steps to order your {{site.data.keyword.baremetal_short}}. Additional information can be found under [Building a custom bare metal server](/docs/bare-metal?topic=bare-metal-ordering-baremetal-server#ordering-baremetal-server).

## Provisioning your {{site.data.keyword.baremetal_short}} using the {{site.data.keyword.cloud_notm}} console
{: #using-console}

1. Log in to the [{{site.data.keyword.cloud_notm}} console](https://cloud.ibm.com/){: external} with your unique credentials.
2. Click **Create resource** > **Compute** > **Bare Metal Server** > **Continue**.
3. Enter the number of servers you are ordering in the **Quantity** field and select your **Location**, which is your data center.
4. Click **All servers** > **SAP certified**.
5. Select the appropriate SAP HANA-certified server for your workload. SAP HANA-certified servers are identified with an **-H** under CPU Model. For more information on how to decipher the server name, see [Deciphering the server names](/docs/infrastructure/sap-hana?topic=sap-hana-determine_configuration#server-names).

The BI.S3.H2192 and BI.S3.H238 servers are also available for **Hourly** billing.
{: note}

6. **Server**, **RAM**, and your private storage option default based on your server selection and cannot be changed. {{site.data.keyword.IBM_notm}} {{site.data.keyword.blockstorageshort}} for {{site.data.keyword.cloud_notm}} or {{site.data.keyword.filestorage_full_notm}}, and Network Attached Storage (NAS) are ordered after you have ordered your server.
7. Select your **Operating System** from either Red Hat or SUSE and select the specific operating system, or VMware hypervisor for your server.

If you are bringing your own license (BYOL) for your operating system, select **Other** > **No Operating System**. For more information, see [Bring your own license](#byol).
{ :note}

## Provisioning your {{site.data.keyword.baremetal_short}} using the {{site.data.keyword.slportal}}
{: #using-portal}

1. Log in to the [{{site.data.keyword.cloud_notm}} infrastructure customer portal](https://control.softlayer.com){: external} with your unique credentials.
2. Click **Account** > **Place an Order** on the Account Summary page.
3. Click the **Monthly** link under {{site.data.keyword.baremetal_short}} on the Devices page.
4. Click the hyperlink under **STARTING PRICE PER MONTH** to select the appropriate SAP HANA-certified server and be taken to the Configure/Order page. SAP HANA-certified servers are identified with an **-H** under CPU Model. For more information on how to decipher the server name, see [Deciphering the server names](/docs/infrastructure/sap-hana?topic=sap-hana-determine_configuration#server-names). 

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

1. Under **SAP Certified Servers**, make your selection based on how you plan to use your server. Consult the [Design Decision Tool](https://github.com/ibm-cloud-architecture/infrastructure-design-decision-tool){: external} or [{{site.data.keyword.cloud_notm}} Support](/docs/get-support?topic=get-support-getting-customer-support#getting-customer-support) for more information
2. Click **Add to order** at the bottom of the page.

## Setting up Advanced System Configurations
{: #adv_config}

1. Follow the [Advanced System Configuration](/docs/bare-metal?topic=bare-metal-ordering-baremetal-server#ordering-baremetal-server) guidelines for help with the values in the **Advanced System Configuration** window.

SAP host names must consist of a maximum of 13 alpha-numeric characters. For more information on SAP host name, see [SAP Notes 611361)](https://launchpad.support.sap.com/#/611361){: external} and [129997)](https://launchpad.support.sap.com/#/129997){: external}.

## Confirming your selections
{: #confirm_selections}

1. Confirm your selections on the Checkout page and click **Cloud Service terms** and **3rd Party Software Agreement**.
2. Scroll down to Create Account: Enter Billing and enter the **Payment Type, Name, Card**, and **Expiration** (date) for the credit card to be used for billing.
3. Click **Submit Order**. You are redirected to a screen with your order number. You can print the screen because it is also your order receipt.

A confirmation email with the subject Your _{{site.data.keyword.cloud_notm}} Order ## has been approved_ is sent to the email address in your profile. This email is notice that your server has been approved and is in the process of being deployed. After it is deployed, another notice is sent notifying you that the server is available and can be managed through the [{{site.data.keyword.cloud_notm}} infrastructure customer portal)](https://control.softlayer.com){: external}.

## Bring your own license
{: #byol}

When you have your own operating system license, you install it on your {{site.data.keyword.baremetal_short}} based on the vendor's instructions. For more information, see [The no OS option](/docs/bare-metal?topic=bare-metal-bm-no-os#bm-no-os).

## Next Steps

You are now ready to begin Managing your {{site.data.keyword.baremetal_short}}. See [Managing your SAP HANA environment](/docs/infrastructure/sap-hana?topic=sap-hana-manage_environment#manage_environment) for your next steps.
