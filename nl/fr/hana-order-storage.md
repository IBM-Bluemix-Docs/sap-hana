---



copyright:
  years: 2018
lastupdated: "2018-02-12"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 1. Commande de stockage 
{: #order_storage}

Vous commandez {{site.data.keyword.blockstoragefull}}, {{site.data.keyword.filestorage_full_notm}} et Network Attached Storage (NAS) après le déploiement de vos serveurs Bare Metal {{site.data.keyword.cloud_notm}}.  

## Commande de stockage {{site.data.keyword.cloud_notm}} 
{: #ibm_storage}

Vous pouvez suivre les étapes décrites dans [Provisioning and Managing {{site.data.keyword.blockstorageshort}}](https://console.bluemix.net/docs/infrastructure/BlockStorage/provisioning-block_storage.html#provisioning-and-managing-block-storage) ou [Provisioning and Managing {{site.data.keyword.filestorage_full_notm}}](https://console.bluemix.net/docs/infrastructure/FileStorage/provisioning-file-storage.html#provisioning-and-managing-ibm-file-storage-for-ibm-cloud) pour commander votre solution de stockage pour la sauvegarde et la restauration. Vous serez guidé pour choisir le type de stockage à utiliser, savoir comment le commander et savoir comment le déployer sur votre serveur. 

## Commande de stockage NAS 
{: #order-nas}

Le stockage NAS peut constituer une autre extension intéressante du stockage local de votre serveur si vous avez besoin de stockage pour les fichiers journaux archivés de votre base de données ou des sauvegardes en ligne et hors ligne fréquentes. Visitez la page [Ordering NAS/FTP Storage](https://console.bluemix.net/docs/infrastructure/network-attached-storage/index.html#ordering-nas-ftp-storage) pour commander et configurer un stockage NAS. De plus, consultez la rubrique [Mounting NAS Storage in Linux](https://console.bluemix.net/docs/infrastructure/network-attached-storage/mount-nas-storage-linux.html#mounting-nas-storage-in-linux) pour apprendre à mapper le stockage de fichiers réseau (NFS) à votre serveur Linux. [Le stockage NAS peut également être mappé à VMware ESXi en tant que magasin de données via NFS](https://console.bluemix.net/docs/infrastructure/network-attached-storage/connect-nas-storage-windows.html#connecting-to-nas-storage-in-windows).

## Etapes suivantes

  [2. Sécurisation de votre environnement](/docs/infrastructure/sap-hana/hana-secure-environment.html)

  [3. Installation de votre système d'exploitation invité sur l'hyperviseur ESX (facultatif) ](/docs/infrastructure/sap-hana/hana-installing-guest-operating-system-VMware-deployments.html)

  [4. Téléchargement et installation des logiciels et des applications SAP](/docs/infrastructure/sap-hana/hana-installing-SAP-landscape.html)
  
  [5. Test de la connectivité à votre centre de données {{site.data.keyword.cloud_notm}}](/docs/infrastructure/sap-hana/hana-testing-connectivity.html)
