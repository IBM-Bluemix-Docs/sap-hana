---

copyright:
  years: 2017, 2020
lastupdated: "2020-04-22"

keywords: SAP HANA, SAP landscape, {{site.data.keyword.cloud_notm}}

subcollection: sap-hana

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Planning your system landscape
{: #planning-your-system-landscape}

An SAP *landscape* is a group of two or more SAP *systems* that usually include development, quality and test, and production. One SAP system consists of one or more *SAP instances*, which are a group of processes that are started and stopped at the same time. For more information on SAP landscapes, see [*SAP Business Suite on IBM X6 Systems Reference Architecture*)](https://lenovopress.com/redp5073.pdf){: external}.
{: shortdesc}

There are several possible landscape configurations, such as server (size)/storage (size), for all SAP solutions in the market. These solutions include SAP NetWeaver-based products, such as [SAP Business Suite)](https://open.sap.com/courses/suitehana1){: external}, SAP Business Warehouse, and all specific SAP add-ons, which the servers in the {{site.data.keyword.cloud}} SAP-Certified Infrastructure support. Additional solutions to keep in mind are any third-party software that might integrate with SAP.

SAP HANA can run as a database for an SAP NetWeaver stack-based solution or as a standalone entity depending on your usage scenario. For both scenarios, the {{site.data.keyword.cloud_notm}} offering provides preconfigured SAP NetWeaver-certified servers where the landscape around those servers can be built from any other server.

You want to be as detailed as possible when you determine the size of your server based on the applications you plan to run, potential growth, and performance. Additionally, keep in mind your storage and memory requirements for your applications. SAP systems in a landscape have specific requirements for connectivity, either among each other or to external systems. For more information, see [Items to consider when planning your SAP landscape](/docs/sap-hana?topic=sap-hana-considerations#considerations).

Table 1 contains the steps within the planning process. Use it to help build your target SAP landscape.

| Step | Details |
| --- | --- |
| 1 | [Get SAP and {{site.data.keyword.cloud_notm}} credentials and create accounts](/docs/sap-hana?topic=sap-hana-get_sap_ibm_credentials#get_sap_ibm_credentials) |
| 2 | [Review any relevant SAP and {{site.data.keyword.cloud_notm}} documentation](/docs/sap-hana?topic=sap-hana-review_doc#review_doc) |
| 3 | [Determine your SAP applications](/docs/sap-hana?topic=sap-hana-3-determining-your-sap-applications#3-determining-your-sap-applications) |
| 4 | [Size the server](/docs/sap-hana?topic=sap-hana-size_the_server#size_the_server) |
| 5 | [Determine your configuration](/docs/sap-hana?topic=sap-hana-determine_configuration#determine_configuration) |
{: caption="Table 1. Planning process overview" caption-side="top"}

## Next Steps
{: #next-steps-planning-your-system-landscape}

Select the appropriate step in Table 1 to begin planning your SAP landscape.
