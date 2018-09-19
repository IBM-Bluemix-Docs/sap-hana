---



copyright:
  years: 2017, 2018
lastupdated: "2010-08-10"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 2. Configuration de votre infrastructure
{: #set_up_infrastructure}

La section ci-dessous contient des conseils pour la configuration de vos serveurs IBM Bare Metal SAP HANA, du réseau, de la sécurité, du stockage et du système d'exploitation. Prenez contact avec le [support {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/get-support/howtogetsupport.html#getting-customer-support) pour toute question.

## Commande de votre serveur
{: order-server}

Suivez les étapes ci-dessous pour commander vos serveurs Bare Metal. Vous trouverez des informations supplémentaires dans la rubrique relative à la [génération d'un serveur bare metal personnalisé](https://console.bluemix.net/docs/bare-metal/baremetal-provision.html#building-a-custom-bare-metal-server) à l'aide de vos données d'identification uniques.

1. Connectez-vous au [portail client de l'infrastructure {{site.data.keyword.cloud_notm}}](https://control.softlayer.com) avec vos données d'identification uniques.
2. Cliquez sur **Compte** > **Passer une commande** dans la page Récapitulatif du compte.
3. Cliquez sur le lien **Au mois** sous les serveurs Bare Metal dans la page Devices. La liste des serveurs s'affiche avec les serveurs certifiés SAP en début de liste.
4. Cliquez sur l'hyperlien sous **Prix de départ par mois** pour sélectionner le serveur approprié et accéder à la page de configuration/commande. Les serveurs certifiés SAP HANA sont signalés par les caractères **-H** sous Modèle d'UC.  
5. Entrez le nombre de serveurs que vous commandez dans la zone **Quantité** et sélectionnez votre centre de données dans **Centre de données**.
6. Les zones **Serveur** et **RAM** ainsi que votre option de stockage privé sont associées aux valeurs par défaut en fonction de votre sélection de serveur et ne peuvent pas être changées. Vous commandez votre stockage {{site.data.keyword.IBM_notm}} {{site.data.keyword.blockstorageshort}} for {{site.data.keyword.cloud_notm}} ou {{site.data.keyword.filestorage_full_notm}} et Network Attached Storage (NAS) après avoir commandé votre serveur.
7. Sélectionnez votre système d'exploitation dans **Système d'exploitation** (Red Hat ou SUSE), puis sélectionnez le système d'exploitation spécifique ou l'hyperviseur VMware pour votre serveur. **Remarque** : si vous apportez votre propre licence (BYOL) pour votre système d'exploitation, sélectionnez **Autre** > **Sans système d'exploitation**. Pour plus d'informations, voir la rubrique [Apport de votre propre licence](#byol).

## Sélection de vos options de serveur
{: #select_options}

Au cours de l'étape suivante, vous allez sélectionner le type et le nombre de disques à ajouter à votre configuration. Vous pouvez aussi sélectionner des options différentes pour les groupes de stockage RAID (Redundant Array of Independent Disks) et les agencements de partition sur les groupes de stockage RAID. Pour plus d'informations, voir [A propos de RAID](https://console.bluemix.net/docs/bare-metal/what-raid.html#about-raid) ou [Support {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/get-support/howtogetsupport.html#getting-customer-support).

1. Sous **Serveurs certifiés SAP**, effectuez votre sélection en fonction de la façon dont vous prévoyez d'utiliser votre serveur. Consultez la page consacrée à l'[outil de décision de conception](https://github.com/ibm-cloud-architecture/infrastructure-design-decision-tool) (faites défiler la page jusqu'à l'outil) ou le [Support {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/get-support/howtogetsupport.html#getting-customer-support) pour plus d'informations.
2. Cliquez sur **Ajouter à la commande** au bas de la page.

## Définition de configurations système avancées
{: #adv_config}

1. Suivez les instructions présentées dans la rubrique [Advanced System Configuration](https://console.bluemix.net/docs/bare-metal/baremetal-provision.html#advanced-server-configuration-options) pour de l'aide relative aux valeurs figurant dans la fenêtre **Configuration système avancée**.

Les noms d'hôte SAP ne doivent pas comporter plus de 12 caractères alphanumériques. Pour plus d'informations sur les noms d'hôte SAP, voir les [notes SAP 611361](https://launchpad.support.sap.com/#/611361) et [129997](https://launchpad.support.sap.com/#/129997). 

## Confirmation de vos sélections
{: #confirm_selections}

1. Confirmez vos sélections dans la page Payer et cliquez sur **Conditions des services Cloud** et l'**accord relatif aux logiciels tiers**.
2. Faites défiler la page jusqu'à la section Créer un compte : entrez les informations de facturation ainsi que le **type de paiement, le nom, la carte** et la **date d'expiration** de la carte de crédit à utiliser.
3. Cliquez sur **Soumettre commande**. Vous êtes redirigé vers un écran affichant votre numéro de commande. Vous pouvez l'imprimer car il s'agit également de l'accusé de réception de la commande.

Un courrier électronique de confirmation dont l'objet est _Votre commande {{site.data.keyword.cloud_notm}} ## a été approuvée_ est envoyé à l'adresse électronique indiquée dans votre profil. Il indique que votre serveur a été approuvé et qu'il est sur le point d'être déployé. Une fois le serveur déployé, un autre avis indiquant que le serveur est disponible et qu'il peut être géré via le [portail client de l'infrastructure {{site.data.keyword.cloud_notm}}](https://control.softlayer.com) vous est envoyé.

## Apport de votre propre licence
{: #byol}

Lorsque vous disposez de votre propre licence de système d'exploitation, installez-le sur votre serveur {site.data.keyword.baremetal_short} en suivant les instructions du fournisseur. Pour plus d'informations, voir l'option [Sans système d'exploitation](https://console.bluemix.net/docs/bare-metal/introduction-no-os.html#how-to-install-an-operating-system-on-a-no-os-server-).

## Etapes suivantes

Vous pouvez maintenant commencer à gérer vos serveurs Bare Metal. Voir [Gestion de votre environnement SAP HANA](/docs/infrastructure/sap-hana/hana-manage-environment.html).

