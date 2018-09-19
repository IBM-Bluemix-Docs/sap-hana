---



copyright:
  years: 2017, 2018
lastupdated: "2018-05-30"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Planification du paysage de votre système
{: #planning-your-system-landscape}

Un *paysage* SAP est un groupe de deux *systèmes* SAP ou plus, qui incluent habituellement le développement, la qualité et le test, et la production. Un système SAP se compose d'une ou de plusieurs *instances SAP*, qui constituent des groupes de processus démarrés et arrêtés simultanément. Pour plus d'informations sur les paysages SAP, voir [*SAP Business Suite on IBM X6 Systems Reference Architecture*](https://lenovopress.com/redp5073.pdf). 
{: shortdesc}

Vous pouvez configurer plusieurs aspects du paysage, par exemple la taille du serveur ou la taille du stockage, pour toutes les solutions SAP sur le marché. Ces solutions incluent des produits reposant sur SAP NetWeaver, tels que [SAP Business Suite](https://open.sap.com/courses/suitehana1), SAP Business Warehouse, et tous les modules complémentaires SAP spécifiques, que les serveurs de l'offre d'infrastructure certifiée SAP¨d'{{site.data.keyword.cloud}} prennent en charge. Vous pouvez également garder à l'esprit certaines solutions supplémentaires telles que les logiciels tiers pouvant être intégrés à SAP. 

SAP HANA peut s'exécuter en tant que base de données pour une solution reposant sur une pile SAP NetWeaver ou en tant qu'entité autonome, selon votre scénario d'utilisation. Dans les deux cas, l'offre {{site.data.keyword.cloud_notm}} fournit des serveurs certifiés SAP NetWeaver préconfigurés dont le paysage peut être généré depuis n'importe quel autre serveur.

Soyez aussi précis que possible lorsque vous déterminez la talle de votre serveur en fonction des applications que vous prévoyez d'exécuter, de la croissance potentielle et des performances. De plus, gardez à l'esprit les exigences en matière de stockage et de mémoire pour vos applications. Les systèmes SAP dans un paysage présentent des exigences spécifiques pour la connectivité entre eux ou à des systèmes externes. Pour plus d'informations, voir [Points à prendre en compte lors de la planification de votre paysage SAP](/docs/infrastructure/sap-hana/hana-considerations.html).

Le tableau 1 contient les étapes du processus de planification. Utilisez-le pour générer votre paysage SAP cible.

Tableau 1. Présentation du processus de planification

| Etape | Détails |
| --- | --- |
| 1 | [Obtention des données d'identification SAP et {{site.data.keyword.cloud_notm}} et création de comptes](/docs/infrastructure/sap-hana/hana-get-credentials.html) |
| 2 | [Consultation de la documentation SAP et {{site.data.keyword.cloud_notm}} pertinente](/docs/infrastructure/sap-hana/hana-review-doc.html) |
| 3 | [Identification de vos applications SAP](/docs/infrastructure/sap-hana/hana-determine-apps.html) |
| 4 | [Dimensionnement du serveur](/docs/infrastructure/sap-hana/hana-size-server.html) |
| 5 | [Détermination de votre configuration](/docs/infrastructure/sap-hana/hana-determine-configuration.html) |

## Etapes suivantes

Sélectionnez l'étape approprié dans le tableau 1 pour commencer à planifier votre paysage SAP.
