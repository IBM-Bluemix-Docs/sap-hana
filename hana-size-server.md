---

copyright:
  years: 2018, 2019
lastupdated: "2019-11-12"

keywords: SAP HANA, SAP Quick Sizer, {{site.data.keyword.cloud_notm}}, {{site.data.keyword.baremetal_short}}, deployment

subcollection: sap-hana

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}


# 4. Sizing the server
{: #size_the_server}

After you decide which SAP solutions you plan to use, your next step is to determine the number of {{site.data.keyword.baremetal_long}} you need to support your SAP landscape and ensure that the servers are correctly sized.
{: shortdesc}

## Understanding the SAP sizing methodology
{: #size_method}

SAP BW/4HANA is supported in production on single- and multi-node SAP HANA-certified bare metal servers. The servers are available in the following configurations-192 GB, to 1 TB, to 8 TB. It's a columnar database that typically requires less space to store data compared to a traditional row-based Relation Database Management System (RDMS). Data can be highly compressed and compression ratios can range from 3:1 to over 10:1 based on the source data and database.

You need to correctly size your server *before* you purchase it because sizing is key to the success of your project. Improperly sized memory or storage requirements can lead to an upgrade and migration to a larger server.

## Accessing the SAP Quick Sizer
{: #quick_sizer}

Main memory is one of the most important resources to consider when sizing an SAP HANA-certified appliance. The public [*SAP HANA Master Guide*)](https://help.sap.com/doc/e95f6750b0fd10148ea5c6be75016694/2.0.00/en-US/SAP_HANA_Master_Guide_en.pdf){: external} provides a starting point for sizing-related topics. The [Sizing SAP HANA)](https://help.sap.com/viewer/eb3777d5495d46c5b2fa773206bbfb46/2.0.00/en-US/d4a122a7bb57101493e3f5ca08e6b039.html){: external} information within the guide provides guidance on how to sized your SAP HANA system. It points to the different installation and migration scenarios for both greenfield installations and existing systems. There is a link to the SAP HANA version of the SAP Quick Sizer tool (an SAP S-user ID is required to access the tool). The page also lists the SAP Notes related to sizing your SAP  HANA server.

## Sizing for a virtualized environment
{: #size_virtual}

For additional sizing considerations when running SAP HANA in a virtualized environment, see [VMware ESXi server deployments](/docs/infrastructure/sap-hana?topic=sap-hana-considerations#vmware_server) and [*Architecture Guidelines and Best Practices for Deployments of SAP HANA on VMware vSphere Architecture and Technical Considerations Guide*)](https://www.vmware.com/content/dam/digitalmarketing/vmware/en/pdf/whitepaper/sap_hana_on_vmware_vsphere_best_practices_guide-white-paper.pdf){: external}.

## Next Steps

 [5. Determining your configuration](/docs/infrastructure/sap-hana?topic=sap-hana-determine_configuration#determine_configuration)
