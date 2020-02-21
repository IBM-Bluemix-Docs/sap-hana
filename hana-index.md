---

copyright:
  years: 2017, 2020
lastupdated: "2020-02-21"

keywords: SAP HANA, {{site.data.keyword.cloud_notm}}

subcollection: sap-hana

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:external: target="_blank" .external}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Getting started with SAP HANA on IBM Cloud
{: #getting-started}

{{site.data.keyword.IBM}} and SAP have been collaborating for over 45 years in multiple areas, including hardware, software, cloud, services, and finance. They are now collaborating to optimize the {{site.data.keyword.cloud}} infrastructure products to include support for the SAP HANA solution in the more than 60 {{site.data.keyword.cloud_notm}} data centers worldwide.
{: shortdesc}

This content provides you with recommendations for the provisioning and installation of the SAP HANA infrastructure and subscription on {{site.data.keyword.cloud_notm}}. It does not replace any SAP HANA documentation nor is it intended to give a full description of the installation process. Its purpose is to help you with infrastructure planning and provisioning so you can begin your SAP installation. The SAP installation (including database installation) does not vary from installations for on-premises environments. Recommendations and guidelines are provided to help you operate your SAP system in the {{site.data.keyword.cloud_notm}} environment regarding the infrastructure provided, for example, network setup or back up storage. The operation of the SAP HANA system does not differ from its operation in any other data center after the infrastructure is in place.

Table 1 contains steps to help you get your {{site.data.keyword.cloud_notm}} infrastructure built quickly.
<table>
   <CAPTION align="bottom">Table 1. Quick start steps</CAPTION>
   <THEAD>
   <TR>
   <th>Task</th>
   <th>Details</th>
   </TR>
   </THEAD>
   <TBODY>
   <tr>
   <td>1. Read IBM Cloud and SAP content that is related to your implementation</td>
   <td>If your organization is new to IBM Cloud, the following information can be useful and should be read before your planning phase.
   <li><a href="https://www.ibm.com/cloud">What is IBM Cloud</a></li>
   <li><a href="https://www.ibm.com/cloud/get-started">Get started with IBM Cloud</a></li>
   <li><a href="https://www.ibm.com/cloud/sap/certified-infrastructure">SAP wokloads on IBM Cloud</a></li>

   You might also find the following SAP documentation useful:     
   <li><a href="https://www.sap.com/products/hana/implementation/resources.html">SAP HANA Installation Guide</a>; download the installation guide</li>
  <li><a href="https://www.youtube.com/watch?v=4wICiRTP8u0/">How to create an SAP S-user ID</a>. Note that only super administrators or S-users with the required authorization are allowed to create S-user IDs.</li>
   <li><a href="https://help.sap.com/viewer/product/SAP_HANA_PLATFORM/2.0.04/en-US">SAP HANA Administration Guide for SAP HANA Platform</a></li>
   <li><a href="https://support.sap.com/en/index.html">SAP Notes</a>; requires an SAP S-user ID</li>
   <tr>
   <td>2. Sign up for IBM Cloud</td>
   <td>See <a href="https://cloud.ibm.com/docs/account?topic=account-signup#signing-up-for-ibm-cloud">Signing up for IBM Cloud</a> for the steps on how to set up your IBM Cloud account.</td>
 <tr>
   <td>3. Access the IBM Cloud console</td>
   <td>The <a href="https://cloud.ibm.com">IBM Cloud console</a> is your graphical gateway to all your infrastructure components-compute, connectivity, storage, network, and data centers. You need an <a href="https://cloud.ibm.com/docs/account?topic=account-signup#signing-up-for-ibm-cloud">IBMid and password</a> to access the customer portal.</td>
   <tr>
   <td>4. Plan your system landscape</td>
   <td>Use the information in <a href="sap-hana?topic=sap-hana-planning-your-system-landscape#planning-your-system-landscape">Planning your system landscape</a> to architect, size, and provision your IBM Cloud environment to support your SAP HANA workload.</td>  
 <tr>
   <td>5. Provision your system</td>
   <td>Use the steps and information in <a href="sap-hana?topic=sap-hana-provision_environment#provision_environment">Provisioning your SAP HANA environment</a> to set up your IBM Cloud infrastructure.</td>
   <tr>
   <td>6. Install SAP landscape</td>
   <td>You install your SAP landscape on your IBM Cloud infrastructure the same as if the servers were on premises. See <a href="sap-hana?topic=sap-hana-install_sap#install_sap">Downloading and installing SAP software and applications</a> for more information.</td>
   </td>
   </tr>
   </TBODY>
   </table>
