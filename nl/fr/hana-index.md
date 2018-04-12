---



copyright:
  years: 2017, 2018
lastupdated: "2018-03-02"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Tutoriel d'initiation à IBM Cloud for SAP Applications 
{: #getting-started}

{{site.data.keyword.IBM_notm}} et SAP collaborent depuis plus de 45 ans dans de nombreux domaines, notamment le matériel, les logiciels, le cloud, les services et la finance. A présent, ils travaillent ensemble pour optimiser les produits {{site.data.keyword.cloud}} Infrastructure et inclure la prise en charge de la solution SAP HANA dans la soixantaine de centres de données {{site.data.keyword.cloud_notm}} qui existent dans le monde.
{: shortdesc}

Cette rubrique contient des recommandations relatives à la mise à disposition et à l'installation de l'infrastructure SAP HANA et à l'abonnement à {{site.data.keyword.cloud_notm}}. Elle ne remplace pas la documentation de SAP HANA et ne décrit pas le processus d'installation dans son intégralité. Elle a pour but de vous assister lorsque vous planifiez votre infrastructure et la mettez à disposition, pour que vous puissiez lancer l'installation de SAP. Celle-ci (avec l'installation de la base de données) est identique aux installations pour les environnements locaux. Des recommandations et des instructions vous aident à utiliser votre système SAP dans l'environnement {{site.data.keyword.cloud_notm}} avec l'infrastructure fournie, par exemple pour procéder à une configuration du réseau ou à un stockage de sauvegarde. Le fonctionnement du système SAP HANA n'est pas différent de son fonctionnement dans un autre centre de données une fois que l'infrastructure est en place. 

Le tableau 1 contient des étapes permettant de générer votre produit {{site.data.keyword.cloud_notm}} Infrastructure rapidement. 
<table>
   <CAPTION>Tableau 1. Etapes de démarrage rapide </CAPTION>
   <THEAD>
   <TR>
   <th>Tâche </th>
   <th>Détails</th>
   </TR>
   </THEAD>
   <TBODY>
   <tr>
   <td>1. Lisez le contenu d'IBM Cloud et de SAP relatif à votre implémentation </td>
   <td>Si votre organisation découvre IBM Cloud, les informations ci-dessous peuvent être utiles et il est recommandé de les lire avant la phase de planification.
<li><a href="https://ibm.com/cloud-computing/">Qu'est-ce qu'IBM Cloud ?</a></li>
   <li><a href="https://ibm.com/cloud/get-started">Get started with IBM Cloud</a></li>
   <li><a href="https://www.ibm.com/cloud/bare-metal-servers/sap">SAP-certified Infrastructure dans IBM Cloud</a></li>
     
   La documentation SAP suivante peut également vous être utile :     
   <li><a href="https://www.sap.com/products/hana/implementation/resources.html">SAP HANA Installation Guide</a> ; téléchargez le guide d'installation </li> 
   <li><a href="https://www.sapappsdevelopmentpartnercenter.com/en/faq/program-faqs_2/how-to-receive-an-s-user-to-access-the-s_77/">How to access restricted content e.g. learning materials and events on the SAP PartnerEdge Portal?</a></li>
   <li><a href="https://help.sap.com/hana/SAP_HANA_Administration_Guide_en.pdf">SAP HANA Administration Guide</a></li>
   <li><a href="https://support.sap.com">Notes SAP</a> ; requiert un ID utilisateur SAP S </li>
   <tr>
   <td>2. Inscrivez-vous à IBM Cloud</td>
   <td>Voir <a href="https://console.bluemix.net/docs/admin/adminpublic.html#signing-up-for-ibm-cloud">Signing up for IBM Cloud</a> pour les étapes à suivre pour configurer votre compte IBM Cloud. </td>
 <tr>
   <td>3. Accédez au portail IBM Cloud Infrastructure Customer Portal. </td>
   <td>Le portail <a href="https://control.softlayer.com">IBM Cloud Infrastructure Customer Portal</a> constitue votre passerelle graphique vers vos composants d'infrastructure (calcul, connectivité, stockage, réseau et centres de données). Vous avez besoin d'un <a href="https://console.bluemix.net/docs/customer-portal/getting-started.html#getting-started">IBMid et d'un mot de passe</a> pour accéder au portail client. </td> 
   <tr>
   <td>4. Planifiez le paysage de votre système </td>
   <td>Servez-vous des informations présentées dans la rubrique <a href="hana-planning-your-system-landscape.html">Planification du paysage de votre système</a> pour créer l'architecture de votre environnement IBM Cloud, le dimensionner et le mettre à disposition en vue de la prise en charge de votre charge de travail SAP HANA. </td>  
 <tr>
   <td>5. Mettez à disposition votre système </td>
   <td>Suivez les étapes et servez-vous des informations présentées dans la rubrique <a href="hana-provision-environment.html#provision_environment">Mise à disposition de votre système SAP HANA</a> pour configurer votre produit IBM Cloud Infrastructure. </td>
   <tr>
   <td>6. Installez le paysage SAP </td>
   <td>Vous installez votre paysage SAP dans votre produit IBM Cloud Infrastructure de la même façon que si vos serveurs se trouvaient sur site. Voir <a href="hana-installing-SAP-landscape.htm#install_sap">Téléchargement et installation des logiciels et des applications SAP</a> pour plus d'informations. </td>
   </td>
   </tr>
   </TBODY>
   </table>
