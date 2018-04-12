---



copyright:
  years: 2018
lastupdated: "2018-03-02"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}


# 3. Identification de vos applications SAP 

Vous devez identifier les applications SAP que vous prévoyez d'exécuter sur vos serveurs IBM Bare Metal. Pour ce faire, répondez aux questions suivantes : 

 * Comment prévoyez-vous d'utiliser la base de données ? SAP HANA peut être déployé de deux façons. La première consiste à déployer SAP HANA en tant que base de données d'une pile SAP NetWeaver, qui servira principalement de source de données. Le deuxième mode de déploiement consiste à exécuter SAP HANA en mode autonome avec des applications déployées directement sur le système SAP HANA. Dans les deux cas, le processus de dimensionnement ainsi que d'autres exigences système et dépendances peuvent différer en fonction de la façon dont vous utilisez votre système (développement et test, démonstration de faisabilité ou production). 
 * Comment prévoyez-vous d'utiliser les applications ? Voulez-vous les utiliser pour le développement et le test ou la production ? 
 * Utilisez-vous un protocole SSL de réseau privé virtuel {{site.data.keyword.cloud_notm}} ou un protocole PPTP (Point-to-Point Tunneling) ? 
  
## Etapes suivantes

  [4. Dimensionnement du serveur](/docs/infrastructure/sap-hana/hana-size-server.html)
  
  [5. Détermination de votre configuration](/docs/infrastructure/sap-hana/hana-determine-configuration.html)
