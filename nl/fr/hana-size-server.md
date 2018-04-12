---



copyright:
  years: 2018
lastupdated: "2018-02-05"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}


# 4. Dimensionnement du serveur 
{: #size_the_server}

Une fois que vous avez choisi les solutions SAP à utiliser, l'étape suivante consiste à déterminer le nombre de serveurs IBM Bare Metal dont vous avez besoin pour prendre en charge votre paysage SAP et garantir un dimensionnement approprié des serveurs.
{: shortdesc}

## Comprendre la méthodologie de dimensionnement de SAP 
{: #size_method}

SAP HANA est disponible dans {{site.data.keyword.cloud_notm}} dans des configurations à noeud unique avec une taille totale de mémoire RAM de  
  * 512 Go
  * 1024 Go (1 To)
  * 2048 Go (2 To)
  * 4096 Go (4 To)
  * 8192 Go (8 To)
  
Il s'agit d'une base de données composée de colonnes qui requiert généralement moins d'espace pour stocker les données qu'un système de gestion de base de données relationnelle traditionnel reposant sur des lignes. Les données peuvent être hautement compressées et les rapports de compression peuvent être compris entre 3:1 et 10:1 en fonction des données source et de la base de données.  

Vous devez dimensionner correctement votre serveur *avant* de l'acheter, car le dimensionnement est la clé du succès de votre projet. Des exigences de mémoire ou de stockage mal dimensionnées peuvent mener à une mise à jour et à une migration vers un serveur plus grand. 

## Accès à l'outil Quick Sizer de SAP 
{: #quick_sizer}

La mémoire principale est l'une des ressources les plus importantes à prendre en compte lors du dimensionnement d'un dispositif certifié SAP HANA. Le manuel public [*SAP HANA Master Guide*](https://help.sap.com/doc/e95f6750b0fd10148ea5c6be75016694/2.0.00/en-US/SAP_HANA_Master_Guide_en.pdf) contient des rubriques relatives au dimensionnement et constitue un bon point de départ. La rubrique [Sizing SAP HANA](https://help.sap.com/viewer/eb3777d5495d46c5b2fa773206bbfb46/2.0.00/en-US/d4a122a7bb57101493e3f5ca08e6b039.html) dans ce guide contient des conseils relatifs au dimensionnement de votre système SAP HANA. Elle présente différents scénarios d'installation et de migration pour les nouvelles installations et les systèmes existants. Elle comporte un lien vers la version SAP HANA de l'outil Quick Sizer de SAP (un ID utilisateur SAP S est requis pour accéder à l'outil). Elle répertorie également les notes SAP relatives au dimensionnement de votre serveur SAP HANA.  

## Dimensionnement d'un environnement virtualisé 
{: #size_virtual}

Pour des remarques complémentaires sur le dimensionnement lors de l'exécution de SAP HANA dans un environnement virtualisé, voir [Déploiement de serveurs VMware ESXi](/docs/infrastructure/sap-hana/hana-considerations.html#vmware-server) et le manuel [*Architecture Guidelines and Best Practices for Deployments of SAP HANA on VMware vSphere Architecture and Technical Considerations Guide*](https://www.vmware.com/content/dam/digitalmarketing/vmware/en/pdf/whitepaper/sap_hana_on_vmware_vsphere_best_practices_guide-white-paper.pdf).

## Etapes suivantes

 [5. Détermination de votre configuration](/docs/infrastructure/sap-hana/hana-determine-configuration.html)
