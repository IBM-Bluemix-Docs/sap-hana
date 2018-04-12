---



copyright:
  years: 2017, 2018
lastupdated: "2018-02-05"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Points à prendre en compte lors de la planification de votre paysage SAP 
{: #considerations}

Les systèmes SAP dans un paysage ont des exigences spécifiques relatives à la connectivité, entre eux ou à des systèmes externes. Vous devez également penser à un stockage externe pour votre paysage et aux tâches à effectuer si vous décidez de déployer VMware sur votre serveur. 

## Connectivité du réseau
{: #network_connectivity}

Le [réseau {{site.data.keyword.cloud_notm}}](/docs/infrastructure/sap-hana/hana-about.html#ibm_cloud_network) fournissait un aperçu de l'approche d'{{site.data.keyword.cloud}} concernant la connectivité du réseau. Les problèmes liés à la connectivité du réseau peuvent entraîner des délais considérables pour votre projet si vous ne procédez pas à la planification correctement, quelle que soit la façon dont vous prévoyez d'utiliser votre système.  

En général, vous disposez de deux choix d'interface pour vos serveurs {{site.data.keyword.cloud_notm}} mis à disposition dans l'infrastructure sous forme de services (IaaS). Le premier choix est une interface externe possédant une adresse IP publique. Le deuxième est une interface interne fournie avec une .adresse IP privée. conformément à la demande de commentaires (RFC) 1918. Vous pouvez également choisir une interface interne unique avec une .adresse IP privée.. Il se peut que l'adresse IP externe soit plus facile à utiliser, mais elle présente un risque, même si un pare-feu de base est installé et préconfiguré. 

La deuxième option accède au réseau privé virtuel d'{{site.data.keyword.cloud_notm}} par le biais du portail {{site.data.keyword.cloud_notm}} Infrastructure Customer Portal, ou déploie un périphérique de sécurité dans votre paysage. Les périphériques de sécurité sont proposés pour les pare-feux, la conversion d'adresse réseau, l'accès au réseau privé virtuel et d'autres fonctions de réseau. Nous recommandons à votre service de gestion du réseau de parler à un membre de l'équipe de [support {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/get-support/howtogetsupport.html#getting-customer-support) une fois que vous avez déterminé l'agencement de votre paysage et la connectivité requise sur la couche de l'application SAP. 

### Réseaux locaux virtuels 
{: #vlans}

Si vous voulez séparer différents types de trafic réseau dans votre paysage, vous pouvez commander d'autres réseaux locaux virtuels. Gardez à l'esprit que les réseaux locaux virtuels supplémentaires ne permettent qu'une séparation du trafic et n'améliorent pas les performances. En général, SAP recommande d'utiliser des réseaux de 10 Go pour le trafic entre ses serveurs d'applications et les bases de données SAP HANA, et pour les autres clients SAP HAN, comme SAP Business Intelligence. Si vous voulez séparer l'accès administratif à votre serveur SAP HANA des autres clients, commandez un autre réseau local virtuel pour votre paysage. Vous pouvez aussi séparer le trafic via le réseau public et le réseau privé, car les liaisons en amont "physiques" ne sont pas prises en charge par {{site.data.keyword.cloud_notm}}. Suivez les recommandations de SAP pour [SAP HANA Tailored Data Center Integration (TDI)](https://blogs.saphana.com/2015/02/18/sap-hana-tailored-data-center-integration-tdi-overview/).

L'accès via un réseau privé virtuel et l'accès rapide permettent un accès transparent à vos instances SAP HANA depuis SAP HANA Studio. 

## Stockage externe
{: #external_storage}

En plus du stockage local, vous pouvez avoir besoin de davantage de stockage externe pour effectuer des sauvegardes. Dans ce cas, vous pouvez commander un stockage par blocs ou un stockage NAS (Network Attached Storage) comme décrit dans [Stockage](/docs/infrastructure/sap-hana/hana-general-iaas-concepts.html#storage). Etant donné que les données du stockage par blocs ou du système de fichiers réseau (NFS) supplémentaires sont transférées par le biais des mêmes adaptateurs physiques que le reste du trafic réseau, prenez en compte l'impact généré.  

Pour le stockage externe, il est important de calculer les exigences de votre projet avant de choisir une solution de stockage. Si vous devez restaurer un système SAP HANA, les opérations d'entrée-sortie par seconde de votre stockage ont un impact considérable sur votre créneau de restauration. Les créneaux de sauvegarde ne sont pas aussi critiques avec SAP HANA car toutes les sauvegardes sont des sauvegardes en ligne, quelle que soit la configuration de SAP HANA. 

Par exemple, avec {{site.data.keyword.cloud_notm}} {{site.data.keyword.blockstorageshort}}, vous pouvez prévoir une restauration d'environ 12 To de SAP HANA à la vitesse maximale. Vous devez créer trois unités de stockage physiques (numéros d'unité logique iSCSI de stockage par blocs) car la taille maximale par unité est 4 To. Vous pouvez lier ces trois unités avec le gestionnaire de volume logique de Linux et créer une unité logique de 12 To.  

Les 12 To vous permettent d'effectuer 3 x 10 opérations d'entrée-sortie par seconde et par gigaoctet, c'est-à-dire un total de 122880 opérations d'entrée-sortie par seconde et par gigaoctet à 16 ko. Ainsi, vous disposez d'un temps de restauration d'1,875 gigaoctet par seconde ou d'un temps de restauration total de moins de deux heures. Etant donné que la mesure des opérations d'entrée-sortie par seconde est effectuée avec une distribution égale entre les lectures et les écritures, vous pouvez considérer ces nombres comme limite inférieure pour les performances de restauration. Il est conseillé d'effectuer des tests de sauvegarde et de restauration si vous dépendez d'un créneau de restauration particulier. 

{{site.data.keyword.cloud_notm}}{{site.data.keyword.blockstorageshort}}, {{site.data.keyword.filestorage_full_notm}} et NAS peuvent servir d'espace de sauvegarde ou de stockage pour les composants logiciels supplémentaires qui sont installés sur votre serveur. Toutefois, {{site.data.keyword.cloud_notm}} Storage et NSA ne peuvent pas être utilisés comme stockage pour SAP HANA car ces options ne répondent pas aux critères des indicateurs clés de performance. 

Pour plus d'informations, voir [About {{site.data.keyword.blockstorageshort}}](https://console.bluemix.net/docs/infrastructure/BlockStorage/index.html#getting-started-with-block-storage) et [Getting started with {{site.data.keyword.filestorage_full_notm}}](https://console.bluemix.net/docs/infrastructure/FileStorage/index.html#getting-started-with-file-storage).

## Scénarios de haute disponibilité et de reprise après incident 
{: #ha_dr}

L'environnement {{site.data.keyword.cloud_notm}} ne prend en charge aucun scénario de haute disponibilité préconfiguré. Cependant, il vous autorise à implémenter des solutions à haute disponibilité pour SAP HANA par le biais d'extensions de haute disponibilité Red Hat Enterprise Linux, par exemple sur site. 

La réplication du système SAP HANA peut être configurée avec une reprise en ligne automatisée d'un serveur sur une réplique. Consultez la documentation SAP relative à la réplication du système pour déterminer le mode de réplication le plus adapté à votre scénario d'application et votre niveau de résilience en cas d'incident. Selon le mode de réplication, des indicateurs clés de performance différents doivent être satisfaits. Prenez connaissance des recommandations de SAP sur le débit du réseau et le temps d'attente afin de déterminer le débit requis et le temps d'attente maximal pour le mode de fonctionnement de votre choix. La topologie de réseau d'{{site.data.keyword.cloud_notm}} doit pouvoir servir toutes les configurations requises. Prenez contact avec le support {{site.data.keyword.cloud_notm}} afin de déterminer la configuration optimale pour votre scénario si vous n'êtes pas sûr de vous ou si vous voulez que votre site de reprise après incident se trouve dans un centre de données différent pour optimiser la résilience en cas d'incident. 

Sachez que les environnements évolutifs SAP HANA (à plusieurs noeuds) sont encore en cours d'évaluation. En d'autres termes, un noeud de secours pour SAP HANA n'est actuellement pas une option dans un environnement {{site.data.keyword.cloud_notm}}. 

Pour plus d'informations sur la réplication du système, le débit du réseau et le temps d'attente, voir 
  * [How To Perform System Replication for SAP HANA](https://www.sap.com/documents/2013/10/26c02b58-5a7c-0010-82c7-eda71af511fa.html)
  * [Network Required for SAP HANA System Replication](https://www.sap.com/documents/2014/06/babb2b55-5a7c-0010-82c7-eda71af511fa.html)

Pour plus d'informations sur la configuration des extensions de cluster à haute disponibilité pour votre système d'exploitation Linux, voir 
  * [SAP HANA system replication in pacemaker cluster dans le guide de configuration RHEL](https://access.redhat.com/articles/1466063)
  * [SAP HANA SR Performance Optimized Scenario](https://www.suse.com/docrep/documents/ir8w88iwu7/suse_linux_enterprise_server_for_sap_applications_12_sp1.pdf)

## Déploiement de serveurs VMware ESXi 
{: #vmware_server}

Tous les serveurs dans l'offre {{site.data.keyword.cloud_notm}} SAP HANA sont certifiés pour VMware ESX, ce qui rend SAP HANA déployable sur les machines virtuelles. Si un serveur est commandé avec VMware ESX, il est déployé avec une instance ESX configurée de base préinstallée ; aucune machine virtuelle n'est déployée. Sachez que vous êtes en charge du déploiement du système d'exploitation invité approprié dans un déploiement ESX. Suivez les instructions présentées dans la note SAP 2414820 afin de choisir une version de système d'exploitation prise en charge avec SAP HANA dans {{site.data.keyword.cloud_notm}}. 

Le processus de dimensionnement pour un déploiement ESX diffère de celui d'un déploiement de serveur Bare Metal. Suivez les recommandations figurant dans le manuel *Architecture Guidelines and Best Practices for Deployments of SAP HANA on VMware vSphere Architecture and Technical Considerations Guide*. Vous devez calculer la surcharge pour la couche de virtualisation en suivant les règles présentées dans ce manuel. Une fois que le système d'exploitation invité est déployé sur une machine virtuelle, vérifiez que les indicateurs clés de performance de SAP HANA TDI sont satisfaits. Consultez la note SAP 1943937 pour des détails sur le test de l'environnement pour vérifier sa conformité aux prérequis du support SAP. Ceux-ci doivent être satisfaits pour chaque machine virtuelle déployée sur un serveur spécifique. 

Vous devez respecter plusieurs autres règles définies par SAP pour déployer SAP HANA dans un environnement virtualisé. Dans un environnement de production, respectez les restrictions mises en évidence dans la note SAP 1995460. La note SAP 2024433 décrit les règles lorsque plusieurs machines virtuelles coexistent sur un serveur. 

Pour plus d'informations, voir la documentation suivante :
  * [La note SAP 2414820](https://launchpad.support.sap.com/#/notes/2414820)
  * [*Le manuel Architecture Guidelines and Best Practices for Deployments of SAP HANA on VMware vSphere Architecture and Technical Considerations Guide*](https://www.vmware.com/content/dam/digitalmarketing/vmware/en/pdf/whitepaper/sap_hana_on_vmware_vsphere_best_practices_guide-white-paper.pdf)
  * [La note SAP 1943937](https://launchpad.support.sap.com/#/notes/1943937)
  * [La foire aux questions de SAP HANA Tailored Data Center Integration](https://www.sap.com/documents/2016/05/e8705aae-717c-0010-82c7-eda71af511fa.html)
  * [La note SAP 1995460](https://launchpad.support.sap.com/#/notes/1995460)
  * [La note SAP 2024433](https://launchpad.support.sap.com/#/notes/2024433)
  * [L'article SAP HANA Tailored Data Center Integration (TDI) Overview](https://blogs.saphana.com/2015/02/18/sap-hana-tailored-data-center-integration-tdi-overview/)
