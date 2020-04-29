---

copyright:
  years: 2018, 2020
lastupdated: "2020-04-20"

keywords: SAP HANA, SAP applications

subcollection: sap-hana

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}


# 3. Determining your SAP applications

You need to determine which SAP-based applications you plan to run on your {{site.data.keyword.baremetal_long}}. Items to consider when making your determination include:

 * How will the database be used? There are two ways that SAP HANA can be deployed. The first is as a database to an SAP NetWeaver stack, where it primarily serves as a data source. The second deployment method is to run SAP HANA in a standalone mode with applications deployed directly in the SAP HANA system. Either way, the sizing process, and other system requirements and dependencies might differ based on how you use your system (development and testing, proof of concept, or production).
 * How do you intend to use the applications? Is the intended use for development and testing, or production?
 * Do you use an {{site.data.keyword.cloud_notm}} Virtual Private Network service?

## Next Steps
{: #next-steps-determin-apps}

  [4. Sizing the server](/docs/sap-hana?topic=sap-hana-size_the_server#size_the_server)

  [5. Determining your configuration](/docs/sap-hana?topic=sap-hana-determine_configuration#determine_configuration)
