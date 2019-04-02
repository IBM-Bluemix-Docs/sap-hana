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

# Tutorial de Introdução
{: #getting-started}

{{site.data.keyword.IBM_notm}} e SAP estão colaborando por mais de 45 anos em múltiplas áreas, incluindo hardware, software, nuvem, serviços e finanças. Elas estão agora colaborando para otimizar os produtos de infraestrutura do {{site.data.keyword.cloud}} para incluir suporte para a solução SAP HANA nos mais de 60 data centers do {{site.data.keyword.cloud_notm}} no mundo todo.
{: shortdesc}

Este conteúdo fornece recomendações para o fornecimento e a instalação da infraestrutura e assinatura do SAP HANA no {{site.data.keyword.cloud_notm}}. Ele não substitui qualquer documentação do SAP HANA nem é destinado a dar uma descrição integral do processo de instalação. Seu propósito é ajudar com o planejamento e fornecimento de infraestrutura para que seja possível iniciar a sua instalação do SAP. A instalação do SAP (incluindo a instalação do banco de dados) não varia de instalações para ambientes no local. As recomendações e diretrizes são fornecidas para ajudá-lo a operar seu sistema SAP no ambiente {{site.data.keyword.cloud_notm}} com relação à infraestrutura fornecida, por exemplo, a configuração de rede ou armazenamento de backup. A operação do sistema SAP HANA não difere de sua operação em qualquer outro data center após a infraestrutura estar em vigor.

A Tabela 1 contém etapas para ajudá-lo a ter sua infraestrutura do {{site.data.keyword.cloud_notm}} construída rapidamente.
<table>
   <CAPTION>Tabela 1. Etapas de iniciação rápida</CAPTION>
   <THEAD>
   <TR>
   <th>Atividade</th>
   <th>Detalhes</th>
   </TR>
   </THEAD>
   <TBODY>
   <tr>
   <td>1. Ler o conteúdo do IBM Cloud e da SAP que está relacionado à sua implementação</td>
   <td>Se a sua organização é nova para o IBM Cloud, as informações a seguir podem ser úteis e devem ser lidas antes da fase de planejamento.
   <li><a href="https://ibm.com/cloud-computing/">O que é IBM Cloud?</a></li>
   <li><a href="https://ibm.com/cloud/get-started">Introdução ao IBM Cloud</a></li>
   <li><a href="https://www.ibm.com/cloud/bare-metal-servers/sap">Infraestrutura certificada pelo SAP no IBM Cloud</a></li>

   Você também pode achar útil a documentação do SAP a seguir:     
   <li><a href="https://www.sap.com/products/hana/implementation/resources.html">Guia de instalação do SAP HANA</a>; faça download do guia de instalação</li>
  <li><a href="https://www.youtube.com/watch?v=4wICiRTP8u0/">Como criar um ID de usuário S da SAP</a>. Observe que apenas administradores ou usuários S com a autorização necessária têm permissão para criar IDs de usuário S.</li>
   <li><a href="https://help.sap.com/hana/SAP_HANA_Administration_Guide_en.pdf">Guia de Administração do SAP HANA</a></li>
   <li><a href="https://support.sap.com">Notas SAP</a>; requer um ID do usuário S do SAP</li>
   <tr>
   <td>2. Inscrever-se para o IBM Cloud</td>
   <td>Consulte <a href="https://cloud.ibm.com/docs/account?topic=account-signup#signing-up-for-ibm-cloud">Inscrevendo-se para o IBM Cloud</a> para obter as etapas sobre como configurar sua conta do IBM Cloud.</td>
 <tr>
   <td>3. Acessar o portal do cliente de infraestrutura do IBM Cloud</td>
   <td>O <a href="https://control.softlayer.com">portal do cliente de infraestrutura do IBM Cloud</a> é o seu gateway gráfico para todos os componentes de infraestrutura, cálculo, conectividade, armazenamento, rede e data centers. Você precisa de um <a href="https://console.bluemix.net/docs/customer-portal?topic=customer-portal-getting-started#getting-started">IBMid e senha</a> para acessar o portal do cliente.</td>
   <tr>
   <td>4. Planejar sua paisagem do sistema</td>
   <td>Use as informações em <a href="sap-hana?topic=sap-hana-planning-your-system-landscape#planning-your-system-landscape">Planejando sua paisagem do sistema</a> para projetar, dimensionar e provisionar o ambiente do IBM Cloud para suportar a carga de trabalho do SAP HANA.</td>  
 <tr>
   <td>5. Provisionar seu sistema</td>
   <td>Use as etapas e informações em <a href="sap-hana?topic=sap-hana-provision_environment#provision_environment">Provisionando seu ambiente SAP HANA</a> para configurar a infraestrutura do IBM Cloud.</td>
   <tr>
   <td>6. Instalar a paisagem da SAP</td>
   <td>Você instala a sua paisagem do SAP em sua infraestrutura do IBM Cloud da mesma forma como se os servidores estivessem no local. Veja <a href="sap-hana?topic=sap-hana-install_sap#install_sap">Fazendo download e instalando software e aplicativos SAP</a> para obter mais informações.</td>
   </td>
   </tr>
   </TBODY>
   </table>
