---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-26"

keywords: SAP HANA, {{site.data.keyword.cloud_notm}}, SAP ABAP, LACP, KPIs,VLANs

subcollection: sap-hana

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}

# 5. Configuration de votre infrastructure IBM Cloud pour la prise en charge d'un système SAP HANA à plusieurs noeuds
{: #multi-node-storage}

{{site.data.keyword.cloud}} prend en charge le stockage à plusieurs noeuds SAP HANA pour les charges de travail de traitement analytique en ligne (OLAP, online analytical processing), telles que SAP BW (SAP Business Warehouse) et SAP BW/4HANA. La solution {{site.data.keyword.cloud_notm}} pour système à plusieurs noeuds SAP HANA peut comprendre jusqu'à 15+1 noeuds (15 noeuds worker, plus un de secours) pour jusqu'à 30 To de mémoire utilisés pour un système.

Avec un système à plusieurs noeuds, plusieurs noeuds SAP HANA constituent un unique système SAP HANA. Les données sont réparties entre ces noeuds, qui forment une unique base de données. La configuration à plusieurs noeuds prend en charge l'évolutivité et la haute disponibilité via la configuration de secours. L'offre {{site.data.keyword.cloud_notm}} pour cette configuration suit les principes [SAP HANA Tailored Data Center Integration ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://blogs.saphana.com/2015/02/18/sap-hana-tailored-data-center-integration-tdi-overview/){: new_window} (TDI) et utilise des serveurs certifiés SAP-HANA {{site.data.keyword.cloud_notm}} pour le stockage d'entreprise partagé centralisé.

Vous devez suivre les instruction de configuration de la rubrique [Commande de votre système à plusieurs noeuds](#ordering) pour répondre aux exigence SAP HANA TDI et garantir la prise en charge par SAP.
{: note}

Suivez les instructions de la rubrique [Dimensionnement du système SAP HANA ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://help.sap.com/viewer/eb3777d5495d46c5b2fa773206bbfb46/2.0.00/en-US/d4a122a7bb57101493e3f5ca08e6b039.html){: new_window} afin de déterminer la taille requise pour votre système SAP HANA cible, y compris la quantité de mémoire et de stockage nécessaire pour votre déploiement. Les exigences liées au dimensionnement vous aident à définir le nombre de noeuds SAP HANA requis pour votre système à plusieurs noeuds SAP HANA ainsi que la quantité de stockage nécessaire pour héberger les données.

## Révision de la topologie de réseau et de l'organisation du stockage
{: #reviewing-topology}

La Figure 1 illustre la topologie de réseau requise pour la configuration SAP HANA TDI de l'infrastructure {{site.data.keyword.cloud_notm}} sous forme de service.

Figure 1. Topologie de réseau SAP HANA TDI de l'infrastructure IBM Cloud sous forme de service

![Figure 1. Topologie de réseau SAP HANA TDI de l'infrastructure IBM Cloud sous forme de service](/images/SAP-BW.png "Topologie de réseau SAP HANA TDI de l'infrastructure IBM Cloud sous forme de service")

## Définition de vos prérequis
{: #prerequisites}

Pour fonctionner, n système SAP HANA à plusieurs noeuds nécessite que certains réseaux soient configurés. Avant de commander d'autres composants pour votre système, vous devez configurer ces réseaux ainsi que les noeuds de base de données. Vous avez besoin des éléments suivants :
* Un réseau côté client, pour la connexion des serveurs d'application SAP ABAP (SAP Advanced Business Application Programming), des clients SAP HANA Studio et autres clients de réseau au système à plusieurs noeuds. Les options de débit et de disponibilité dépendent du scénario d'utilisation de votre système SAP HANA à plusieurs noeuds. Tenez compte de la quantité de données transférées depuis et vers la base de données SAP HANA et des indicateurs clé de performance relatifs à la disponibilité, nécessaires à votre application.
* Un réseau de stockage, requis pour la connexion aux systèmes {{site.data.keyword.blockstoragefull}} et {{site.data.keyword.filestorage_full_notm}} de back-end. Pour optimiser les performances et la redondance, un réseau de 10 Gb doté de deux interfaces sous liaison Linux avec protocole LACP (Link Aggregation Control Protocol) est requis. Si les indices de performance indiqués dans les instructions de dimensionnement SAP HANA ne sont pas respectés, les indicateurs clés de performance de SAP HANA TDI ne peuvent pas être atteints.
* Un réseau entre-nœud pour la communication interne SAP HANA configuré à l'équivalent du réseau de stockage. Le réseau entre-nœud est utilisé uniquement pour la communication entre des noeuds et le transfert de données qui peut s'avérer nécessaire entre les noeuds au cours des opérations. Cette configuration de réseau obligatoire s'appuie sur deux adaptateurs physiques 10 Gb sous liaison Linux avec LACP.

## Commande de votre système à plusieurs noeuds
{: #ordering}

Pour satisfaire aux indicateurs clés de performance de débit et de performance, vous devez commander vos noeuds de traitement et de stockage et vos réseaux locaux virtuels dans le même centre de données. Si vos composants sont répartis entre plusieurs centres de données, SAP ne pendra pas en charge votre système à plusieurs noeuds.

1. Commandez trois réseaux locaux virtuels et serveurs différents avec quatre adaptateurs (deux privés et publics). Pour plus d'informations concernant la commande de réseaux locaux virtuels, voir [Etape 1 Commande de réseaux locaux virtuels principaux et publics](/docs/infrastructure/virtualization?topic=Virtualization-advanced-single-site-vmware-reference-architecture#step-1-ordering-primary-public-and-private-vlans). Pour plus d'informations concernant la commande de vos serveurs, voir [Configuration de votre infrastructure](/docs/infrastructure/sap-hana?topic=sap-hana-set_up_infrastructure#set_up_infrastructure#set_up_infrastructure).
2. Configuration du réseau local virtuel privé initial en tant que "réseau local virtuel de stockage".
3. [Ouvrez un ticket](/docs/get-support?topic=get-support-open-case#open-case) auprès du support {{site.data.keyword.cloud_notm}} pour (a) déplacer les interfaces publiques vers le second réseau local virtuel et (b) commander deux adaptateurs supplémentaires à affecter au troisième réseau local virtuel, qui est le réseau local virtuel du client.

Vous avez maintenant le nombre de serveurs d'après votre travail de dimensionnement et votre réseau est configuré de sorte que
* Le stockage peut être lié à tous les noeuds
* L'installation SAP HANA à plusieurs noeuds peut s'exécuter une fois le stockage lié

Vos connexions de réseau local de stockage et connexions entre-nœud sont configurées par le déploiement {{site.data.keyword.cloud_notm}}. Veillez à commander les connexions avec deux adaptateurs 10 Gb, chacun avec configuration de reprise en ligne. Cette configuration garantit une liaison Linux et une configuration LACP correctes. Si vous avez des questions, contactez l'équipe du support {{site.data.keyword.cloud_notm}}.

Il existe des critères de performance spécifiques que les volumes NFS doivent respecter (voir [Getting started with {{site.data.keyword.filestorage_short}}](/docs/infrastructure/FileStorage?topic=FileStorage-GettingStarted#getting-started-with-ibm-file-storage-for-bluemix) pour plus d'informations). Concernant les volumes `/data/`, sur la base de tests, 2 To de stockage Endurance avec un indicateur clé de performance de 10 IOPS/Go est requis pour chaque noeud worker. Un volume supplémentaire de même taille est requis en tant que volume SAP HANA `/shared/` et sera partagé entre tous les noeuds. Sur la base de tests, le volume `/shared/` doit être un volume de stockage Performance avec 12 IOPS/Go.

Concernant les volumes de journaux, un volume de 512 Go de stockage Performance est requis pour chaque noeud avec un indicateur clé de performance de 10 IOPS/ko.

Vous pouvez suivre la procédure décrite dans [Provisioning and Managing {{site.data.keyword.blockstorageshort}}](/docs/infrastructure/BlockStorage?topic=BlockStorage-orderingthroughConsole#provisioning-and-managing-block-storage) ou dans [Provisioning and Managing {{site.data.keyword.filestorage_full_notm}}](/docs/infrastructure/FileStorage?topic=FileStorage-orderingConsole#orderingConsole) pour commander votre solution de stockage Endurance et Performance.

## Configuration d'un système SAP HANA à plusieurs noeuds
{: #configuring}

Tous les noeuds doivent avoir accès au volume partagé SAP HANA, ainsi qu'à chacun des volumes de données et journal. Cette approche signifie que tous les volumes sont accessibles à l'ensemble du réseau local virtuel de stockage, que vous configurez selon les instructions fournies dans [Commande de votre système à plusieurs noeuds](#ordering). Si vous ne voulez pas répertorier toutes les adresses IP concernées, rendez les volumes accessibles à l'intégralité du sous-réseau IP du réseau local virtuel.

Suivez les instructions de la rubrique [SAP HANA on NetApp FAS Systems with NFS ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.netapp.com/us/media/tr-4290.pdf){: new_window} pour configurer votre système SAP HANA à plusieurs noeuds. Utilisez les options de montage de système NFS (Network File System, système de fichiers réseau) suivantes pour chaque volume à monter :

`rw,bg,hard,timeo=600,intr,noatime,vers=4,minorversion=1,lock,rsize=1048576,wsize=1048576` dans `/etc/fstab`.

Ces options ont été testées par NetApp et {{site.data.keyword.cloud_notm}}. Contactez le support {{site.data.keyword.cloud_notm}} si vous prévoyez de modifier certaines des valeurs ou options de montage.

Une fois tous vos volumes montés sur tous les noeuds, vos serveurs à plusieurs noeuds sont configurés et prêts pour l'installation de la base de données à plusieurs noeuds SAP HANA. Suivez la procédure décrite dans [SAP HANA Server Installation and Update Guide ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://help.sap.com/viewer/2c1988d620e04368aa4103bf26f17727/2.0.03/en-US){: new_window} pour installer une base de données SAP HANA de la version requise.
