---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-26"

keywords: SAP HANA, {{site.data.keyword.cloud_notm}}, high availability, highly available, SPOF, VLANs, HA, DR, disaster recovery, SAP NetWeaver

subcollection: sap-hana

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}


# Prise en charge de la haute disponibilité IBM Cloud
{: #ha}

L'infrastructure sous forme de service (IaaS) {{site.data.keyword.cloud}} met à votre disposition un environnement de calcul robuste avec un déploiement de système d'exploitation optionnel au niveau supérieur qui prend en charge des solutions de haute disponibilité. La solution s'appuie sur la version de système d'exploitation prise en charge, détaillée dans la [Note SAP 2414097 ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://launchpad.support.sap.com/#/notes/2414097){: new_window}. La solution à haute disponibilité est retreinte aux licences de système d'exploitation fournies avec votre déploiement ou à des licences de tiers, par exemple, votre propre licence (BYOL). Veillez à discuter en détails de la solution à haute disponibilité avec le support {{site.data.keyword.cloud_notm}} avant de procéder au déploiement.

Les systèmes d'exploitation pris en charge et déployés par {{site.data.keyword.cloud_notm}} pour SAP sont les suivants :
* Linux [Red Hat Enterprise Linux (RHEL) ou SUSE Enterprise Linux Server (SLES)] qui prennent en charge des solutions à haute disponibilité SAP NetWeaver et SAP HANA. Les restrictions mineures applicables dans cet environnement {{site.data.keyword.cloud_notm}} sont détaillées dans la section [Présentation des configurations à haute disponibilité SAP NetWeaver](#overview-configs).
* Microsoft Windows qui prend uniquement en charge la solution à haute disponibilité SAP NetWeaver (en raison des restrictions liées à la base de données SAP HANA).

## Présentation des configurations à haute disponibilité SAP NetWeaver
{: #overview-configs}

De nombreux documents fournissent une aide détaillée concernant la planification et l'installation d'un environnement haute disponibilité pour des services SAP. Ces documents incluent des informations relatives au basculement, à la réplication, à l'évolution/réduction et à la reprise après incident. Des références à certains de ces documents sont fournies le cas échéant.

Tous les systèmes d'exploitation et distributions pris en charge par {{site.data.keyword.cloud_notm}} pour un déploiement SAP (Windows, Linux RHEL et SLES) sont livrés avec un logiciel haute disponibilité et des extensions spécifiques. Voici les systèmes d'exploitation et les distributions pris en charge.

* [New Failover Clustering Improvements in Windows Server 2012 and Its Benefits for SAP NetWeaver High Availability ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://blogs.sap.com/2013/10/16/new-failover-clustering-improvements-in-windows-server-2012-and-its-benefits-for-sap-netweaver-high-availability/){: new_window} fournit une description basée sur la mise en cluster de basculement de Microsoft Windows Server Failover Clustering (WFSC, Microsoft Windows Server Failover Clustering) sur le système d'exploitation Windows avec SAP NetWeaver.

* Il existe deux documents de référence qui donnent des conseils concernant le déploiement de SAP NetWeaver dans un environnement haute disponibilité basé sur Linux avec Linux Pacemaker :
  * SUSE SAP NetWeaver High Availability Cluster 7.40 Setup Guide
  * Deploying Highly Available SAP NetWeaver-based Servers Using Red Hat Enterprise Linux HA add-on with Pacemaker

* [Building High Availability for SAP NetWeaver and SAP HANA on Linux ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://support.sap.com/content/dam/SAAP/SAP_Activate/AGS_70.pdf){: new_window} est un document relatif aux meilleures pratiques SAP qui fournit une description technique détaillée essentiellement axée sur SAP HANA.

* [SAP NetWeaver High Availability and Business Continuity in Virtual Environments with VMware and Hyper-V on Microsoft Windows ![Icône de lien externe ](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.sap.com/documents/2015/07/508b62bc-5b7c-0010-82c7-eda71af511fa.html){: new_window} qui traite de la virtualisation si vous prévoyez d'implémenter la haute disponibilité sur des serveurs virtuels.

Pour d'autres produits de haute disponibilité certifiés par des partenaires SAP pour des scénarios de haute disponibilité, voir [High Availability Partner Information ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://wiki.scn.sap.com/wiki/display/SI/High+Availability+Partner+Information){: new_window}.
Pour les bases de données autres que HANA SAP, des informations supplémentaires sur le basculement haute disponibilité et les configurations de reprise sur incident sont disponibles dans la documentation relative à votre base de données.

L'accès partagé à un stockage système NFS (Network File System)/CIFS (Common Internet File System) ou à des numéros d'unité logique (LUN, Logical Unique Number) iSCSI est généralement nécessaire pour prendre en charge le basculement du système. Un stockage local, combiné à une méthode de réplication, est en général requis pour prendre en charge une configuration de type reprise sur incident. Comme pour les installations sur site, vérifiez les exigences en matière de performances et de temps d'attente du produit de base de données lorsque vous planifiez votre déploiement.

## Conseils supplémentaires
{: #extra-guide}

Les sections [Stockage basé sur le quorum ](#quorum) et [Considérations relatives aux réseaux](#network) donnent des conseils dont vous devez tenir compte lors de votre déploiement. Outre les considérations exposées dans ces sections, l'installation de SAP NetWeaver et de son système de base de données dans un environnement haute disponibilité est similaire aux autres installations sur site.

### Stockage basé sur le quorum
{: #quorum}

En raison de restrictions liées à la sécurité dans l'environnement {{site.data.keyword.cloud_notm}}, l'accès via le réseau à des périphériques de gestion à distance à l'aide de l'interface IPMI (Intelligent Platform Management Interface) n'est pas disponible. Les environnements de cluster utilisent généralement des composants IPMI pour le “clôturage des noeuds de cluster” de manière à garantir le quorum. En l'absence de périphérique IPMI, des périphériques de stockage partagés sont utilisés. Dans un environnement {{site.data.keyword.cloud_notm}}, les périphériques de stockage partagés sont implémentés en déployant un numéro d'unité logique iSCSI sur vos serveurs en tant que périphérique quorum. Par exemple, un système de partage de fichiers témoins (File Share Witness, FSW) sur un cluster Microsoft, pour SDB (Storage-Based Death, mort liée au stockage) et pour la technique Stonith de Linux Pacemaker.
* Cliquez [ici ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](http://linux-ha.org/wiki/Cluster_Concepts){: new_window} pour plus d'informations sur les concepts de cluster à haute disponibilité Linux.
* Cliquez [ici ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://docs.microsoft.com/en-us/windows-server/failover-clustering/manage-cluster-quorum){: new_window} pour plus d'informations sur la configuration et la gestion des serveurs quorum pour Windows Server 2012 et Windows Server 2012 R2.

{{site.data.keyword.cloud_notm}} Storage dispose de fonctions haute disponibilité intégrées de sorte qu'un unique numéro d'unité logique iSCSI partagé n'introduit aucun point de défaillance unique car votre topologie de réseau est redondante. Toutefois, les spécificités de votre produit de cluster peuvent nécessiter plusieurs périphériques quorum.

### Considérations relatives aux réseaux
{: #network}

Une installation basée sur {{site.data.keyword.cloud_notm}} est fournie avec l'une des configurations réseau suivantes :
* Réseau privé
* Réseau public
* Réseaux public et privé
* Deux réseaux privés (exclusivement sur demande)

Comme pour les installations sur site, des adaptateurs de réseau supplémentaires peuvent être commandés en fonction des restrictions physiques du matériel. La restriction est la même pour les installations sur site. Commander des adaptateurs de réseau supplémentaires lors des déploiements de matériel permet d'éviter la présence d'un point de défaillance unique au sein de votre topologie de réseau. Les adaptateurs redondants sont installés dans une configuration de reprise en ligne avec LACP (Link Aggregation Control Protocol). Pour Linux, la configuration fait appel à des interfaces de liaison, et des adaptateurs d'association sont utilisés pour Microsoft Windows. L'infrastructure de commutateur {{site.data.keyword.cloud_notm}} à laquelle ces adaptateurs sont connectés est redondante de sorte qu'aucun nouveau point de défaillance unique n'est introduit. Cette infrastructure redondante peut être utilisée par les réseaux locaux virtuels commandés.

En fonction des exigences réseau, telles que les scénarios de réplication dans une configuration de reprise sur incident, vous devez vérifier l'emplacement des périphériques connectés et les éventuelles exigences réseau propres au produit concerné. Dans certains cas, la réplication basée sur le stockage d'image instantanée {{site.data.keyword.cloud_notm}} peut répondre à vos exigences. Vérifiez auprès du support {{site.data.keyword.cloud_notm}} quelle solution est la mieux adaptée à vos besoins en matière de processus métier.
