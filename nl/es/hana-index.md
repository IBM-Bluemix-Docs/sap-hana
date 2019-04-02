---

copyright:
  years: 2017, 2019
lastupdated: "2019-02-26"

keywords: SAP HANA, {{site.data.keyword.cloud_notm}}

subcollection: sap-hana

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Guía de aprendizaje de iniciación
{: #getting-started}

{{site.data.keyword.IBM_notm}} y SAP llevan más de 45 años colaborando en muchas áreas, incluyendo hardware, software, nube, servicios y finanzas. Ahora colaboran para optimizar los productos de la infraestructura de {{site.data.keyword.cloud}} para incluir soporte para la solución SAP HANA en más de 60 centros de datos de {{site.data.keyword.cloud_notm}} en todo el mundo.
{: shortdesc}

Este contenido le brinda recomendaciones para el suministro y la instalación de la infraestructura de SAP HANA y la suscripción en {{site.data.keyword.cloud_notm}}. No sustituye ninguna documentación de SAP HANA ni pretende ofrecer una descripción completa del proceso de instalación. Su finalidad es ayudarle con la planificación y el suministro de la infraestructura para que pueda iniciar la instalación de SAP. La instalación de SAP (incluyendo la instalación de la base de datos) no varía entre instalaciones para entornos en local. Se proporcionan recomendaciones y directrices para ayudarle a utilizar el sistema SAP en el entorno {{site.data.keyword.cloud_notm}} a partir de la infraestructura proporcionada, por ejemplo configuración de red o almacenamiento de seguridad. La operación del sistema SAP HANA no difiere de su operación en cualquier otro centro de datos después de instalar la infraestructura.

La Tabla 1 contiene los pasos para construir rápidamente la infraestructura de {{site.data.keyword.cloud_notm}}.
<table>
   <CAPTION>Tabla 1. Pasos de inicio rápido</CAPTION>
   <THEAD>
   <TR>
   <th>Tarea</th>
   <th>Detalles</th>
   </TR>
   </THEAD>
   <TBODY>
   <tr>
   <td>1. Lea el contenido de IBM Cloud y SAP relacionado con su implementación</td>
   <td>Si su empresa es nueva en IBM Cloud, la siguiente información puede ser útil y debe leerse antes de la fase de planificación.
   <li><a href="https://ibm.com/cloud-computing/">Qué es IBM Cloud</a></li>
   <li><a href="https://ibm.com/cloud/get-started">Iniciación a IBM Cloud</a></li>
   <li><a href="https://www.ibm.com/cloud/bare-metal-servers/sap">Infraestructura certificada de SAP en IBM Cloud</a></li>

   La siguiente documentación de SAP también le puede resultar útil:     
   <li><a href="https://www.sap.com/products/hana/implementation/resources.html">Guía de instalación de SAP HANA</a>; descargue la guía e instalación</li>
  <li><a href="https://www.youtube.com/watch?v=4wICiRTP8u0/">Cómo crear un ID S-user de SAP</a>. Tenga en cuenta que únicamente los superadministradores o S-users con la autorización necesaria tendrán permitido crear ID S-user.</li>
   <li><a href="https://help.sap.com/hana/SAP_HANA_Administration_Guide_en.pdf">Guía de administración de SAP HANA</a></li>
   <li><a href="https://support.sap.com">Notas de SAP</a>; requiere un ID S-user de SAP</li>
   <tr>
   <td>2. Regístrese en IBM Cloud</td>
   <td>Consulte <a href="https://cloud.ibm.com/docs/account?topic=account-signup#signing-up-for-ibm-cloud">Registro de IBM Cloud</a> para conocer los pasos sobre cómo configurar su cuenta de IBM Cloud.</td>
 <tr>
   <td>3. Acceda al portal de clientes de infraestructura de IBM Cloud</td>
   <td>El <a href="https://control.softlayer.com">portal de clientes de infraestructura de IBM Cloud</a> es su pasarela gráfica a todos los componentes de la infraestructura: cálculo, conectividad, almacenamiento, red y centros de datos. Necesita un <a href="https://console.bluemix.net/docs/customer-portal?topic=customer-portal-getting-started#getting-started">IBMid y contraseña</a> para acceder al portal de clientes.</td>
   <tr>
   <td>4. Planifique su entorno de sistemas</td>
   <td>Utilice la información de <a href="sap-hana?topic=sap-hana-planning-your-system-landscape#planning-your-system-landscape">Planificación de su entorno de sistemas</a> para determinar la arquitectura y el tamaño y suministrar su entorno IBM Cloud para dar soporte a la carga de trabajo de SAP HANA.</td>  
 <tr>
   <td>5. Suministre su sistema</td>
   <td>Utilice los pasos y la información de <a href="sap-hana?topic=sap-hana-provision_environment#provision_environment">Suministro de su entorno SAP HANA</a> para configurar su infraestructura de IBM Cloud.</td>
   <tr>
   <td>6. Instale el entorno SAP</td>
   <td>Instale su entorno SAP en su infraestructura de IBM Cloud como si los servidores estuvieran en local. Consulte <a href="sap-hana?topic=sap-hana-install_sap#install_sap">Descarga e instalación de software y aplicaciones SAP</a> para obtener más información.</td>
   </td>
   </tr>
   </TBODY>
   </table>
