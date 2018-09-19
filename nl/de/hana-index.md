---



copyright:
  years: 2017, 2018
lastupdated: "2018-08-10"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Lernprogramm zur Einführung
{: #getting-started}

Schon seit über 45 Jahren arbeiten {{site.data.keyword.IBM_notm}} und SAP in vielen Bereichen zusammen, darunter Hardware, Software, Cloud, Services und Finanzierung. Jetzt arbeiten sie gemeinsam an der Optimierung der {{site.data.keyword.cloud}}-Infrastruktur-Produkte, um in den über 60 {{site.data.keyword.cloud_notm}}-Rechenzentren weltweit eine Unterstützung für die SAP HANA-Lösung einzubeziehen.
{: shortdesc}

In diesem Abschnitt erhalten Sie Empfehlungen zur Bereitstellung und Installation der SAP HANA-Infrastruktur und zur Subskription für {{site.data.keyword.cloud_notm}}. Er ersetzt keine SAP HANA-Dokumentation und soll auch keine vollständige Beschreibung des Installationsprozesses darstellen. Sein Zweck ist es, Ihnen bei der Infrastrukturplanung und -bereitstellung zu helfen, sodass Sie mit Ihrer SAP-Installation beginnen können. Die SAP-Installation (einschließlich Datenbankinstallation) unterscheidet sich nicht von der für On-Premises-Umgebungen. Die Empfehlungen und Anleitungen sollen Ihnen hinsichtlich der bereitgestellten Infrastruktur helfen, Ihr SAP-System in der {{site.data.keyword.cloud_notm}}-Umgebung zu betreiben, z. B. für Netzkonfigurationen oder Sicherungen. Der Betrieb des SAP HANA-Systems unterscheidet sich nicht von dem Betrieb in anderen Rechenzentren, nachdem die Infrastruktur einmal eingerichtet ist.

Tabelle 1 enthält die Schritte, mit denen Sie Ihre {{site.data.keyword.cloud_notm}}-Infrastruktur schnell aufbauen können.
<table>
   <CAPTION>Tabelle 1. Schritte für den Schnelleinstieg</CAPTION>
   <THEAD>
   <TR>
   <th>Task</th>
   <th>Details</th>
   </TR>
   </THEAD>
   <TBODY>
   <tr>
   <td>1. Die Abschnitte zu IBM Cloud und SAP lesen, die sich auf Ihre Implementierung beziehen </td>
   <td>Wenn Ihre Organisation neu bei IBM Cloud ist, können die folgenden Informationen hilfreich sein, die noch vor der Planungsphase gelesen werden sollten.
   <li><a href="https://ibm.com/cloud-computing/">Was ist IBM Cloud?</a></li>
   <li><a href="https://ibm.com/cloud/get-started">Einführung in IBM Cloud</a></li>
   <li><a href="https://www.ibm.com/cloud/bare-metal-servers/sap">SAP-zertifizierte Infrastruktur in IBM Cloud</a></li>
     
   Zusätzlich könnte folgende SAP-Dokumentation hilfreich sein:     
   <li><a href="https://www.sap.com/products/hana/implementation/resources.html">SAP HANA-Installationshandbuch</a>; laden Sie das Installationshandbuch herunter</li> 
   <li><a href="https://www.sapappsdevelopmentpartnercenter.com/en/faq/program-faqs_2/how-to-receive-an-s-user-to-access-the-s_77/">Vorgehensweise zum Einrichten einer SAP S-Benutzer-ID</a></li>
   <li><a href="https://help.sap.com/hana/SAP_HANA_Administration_Guide_en.pdf">SAP HANA-Administrationshandbuch</a></li>
   <li><a href="https://support.sap.com">SAP-Hinweise</a>; erfordern eine SAP S-Benutzer-ID</li>
   <tr>
   <td>2. Bei IBM Cloud registrieren</td>
   <td>Unter <a href="https://console.bluemix.net/docs/admin/adminpublic.html#signing-up-for-ibm-cloud">Bei IBM Cloud registrieren</a> finden Sie Schritte zur Einrichtung Ihres IBM Cloud-Kontos.</td>
 <tr>
   <td>3. Auf das Kundenportal der IBM Cloud-Infrastruktur zugreifen</td>
   <td>Das <a href="https://control.softlayer.com">Kundenportal der IBM Cloud-Infrastruktur</a> ist das grafische Gateway zu allen Ihren Infrastrukturkomponenten: Computer, Konnektivität, Speihcer Netz und Rechenzentren. Für den Zugriff auf das Kundenportal benötigen Sie <a href="https://console.bluemix.net/docs/customer-portal/getting-started.html#getting-started">IBM-ID und Kennwort</a>.</td> 
   <tr>
   <td>4. Systemumgebung planen</td>
   <td>Gehen Sie anhand der Informationen in <a href="hana-planning-your-system-landscape.html">Systemumgebung planen</a> vor, um die IBM Cloud-Umgebung für die Unterstützung Ihrer SAP HANA-Workload zu konstruieren, dimensionieren und bereitzustellen.</td>  
 <tr>
   <td>5. System bereitstellen</td>
   <td>Gehen Sie anhand der Schritte und Informationen in <a href="hana-provision-environment.html#provision_environment">SAP HANA-Umgebung bereitstellen</a> vor, um Ihre IBM Cloud-Infrastruktur einzurichten.</td>
   <tr>
   <td>6. SAP-Umgebung installieren</td>
   <td>Die SAP-Umgebung wird in gleicher Weise in Ihrer IBM Cloud-Infrastruktur installiert wie die Server vor Ort. Weitere Informationen finden Sie unter <a href="hana-installing-SAP-landscape.html#install_sap">SAP-Software und -anwendungen herunterladen und installieren</a>.</td>
   </td>
   </tr>
   </TBODY>
   </table>
