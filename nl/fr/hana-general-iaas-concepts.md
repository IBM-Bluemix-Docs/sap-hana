---



copyright:
  years: 2017, 2018
lastupdated: "2018-06-28"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Présentation de l'infrastructure sous forme de services (IaaS) SAP HANA on IBM Cloud
{: #iaas-overview}

Un environnement d'infrastructure sous forme de services (IaaS) est constitué de plusieurs composants : centre de données, calcul, connectivité, stockage et réseau. 

## Centres de données

Avec des centres de données se trouvant en Amérique du Nord et en Amérique du Sud, en Europe, en Asie et en Australie, vous pouvez mettre à disposition des ressources de cloud partout où vous en avez besoin (et à tout moment). Chaque centre de données est connecté au réseau privé global d'{{site.data.keyword.cloud_notm}}, ce qui permet des transferts de données plus rapides et plus efficaces, partout dans le monde.

Pour plus d'informations, voir la page sur les [centres de données](https://www.ibm.com/cloud-computing/bluemix/data-centers){: new_window}.

## Serveurs Bare Metal

Les serveurs IBM Bare Metal sont des serveurs physiques dont les fonctions de personnalisation sont limitées. Ils sont dédiés à votre utilisation ou à celle de vos clients et aucun de leurs composants, notamment les ressources serveur, n'est partagé avec d'autres clients {{site.data.keyword.cloud_notm}}. Ils sont mis à disposition en tant que serveurs physiques entiers exécutant le système d'exploitation de votre choix. Les systèmes d'exploitation pour l'offre SAP HANA sont Red Hat Enterprise Linux 7.4 for SAP HANA, SUSE Linux Enterprise Server 12 SP2 for SAP HANA et VMware Server Virtualization 6.5.

Etant donné que la personnalisation est limitée sur les serveurs Bare Metal, des temps de mise à disposition plus rapides compris entre 1 et 4 heures sont possibles. La mise à disposition rapide est utile lorsque vous essayez de mettre une application sur le marché avant vos concurrents.

Vous disposez d'un ensemble de combinaisons de mémoire RAM et d'unités centrales car les serveurs certifiés SAP présentent une quantité de mémoire RAM et un nombre d'unités centrales préconfigurés. La combinaison *ne peut pas* être changée au cours du processus de commande ou via un ticket de demande de service une fois les serveurs déployés.

Pour plus d'informations, voir [About bare metal servers](https://console.bluemix.net/docs/bare-metal/about.html#about-bare-metal-servers). 

## Connectivité du réseau

La connectivité du réseau privé virtuel au réseau cloud virtuel d'{{site.data.keyword.cloud_notm}} est accordée automatiquement lorsque votre compte {{site.data.keyword.cloud_notm}} est configuré. Par défaut, votre serveur possède une adresse IP publique et une adresse IP privée. Si vous voulez que votre serveur soit privé, vous pouvez désactiver l'interface publique une fois votre serveur mis à disposition ou commander votre serveur en tant que serveur privé. 

Alors que les exigences réseau pour SAP HANA (réseau redondant de 10 Go) sont remplies par l'offre {{site.data.keyword.cloud_notm}}, il se peut que vous deviez satisfaire certains indicateurs clés de performance relatifs au temps d'attente et au débit, en fonction de votre scénario d'application. Pour plus d'informations permettant de déterminer dans quel centre de données placer votre serveur SAP HANA et de choisir la meilleure solution de connectivité du réseau, voir les remarques relatives à la [connectivité du réseau](/docs/infrastructure/sap-hana/hana-considerations.html#network_connectivity).

Pour plus d'informations, voir [Getting started with Virtual Private Networking](https://console.bluemix.net/docs/infrastructure/iaas-vpn/getting-started.html#getting-started-with-virtual-private-networking-vpn-) et le livre blanc [*SAP HANA Network Requirements*](https://www.sap.com/documents/2016/08/1cd2c2fb-807c-0010-82c7-eda71af511fa.html).

## Stockage
{: #storage}

Un stockage local est fourni avec vos serveurs Bare Metal ; il utilise le réseau local virtuel privé d'{{site.data.keyword.cloud_notm}} pour assurer une sécurité au niveau de l'entreprise sans empêcher l'accès administrateur. Pour les serveurs certifiés SAP HANA, il a été conçu et est configuré pour satisfaire les indicateurs clés de performance définis par SAP pour le débit et le temps d'attente, conformément aux critères de certification SAP. Le stockage local possède la taille pertinente des différents systèmes de sous-fichiers, telle que définie dans le guide d'installation de SAP HANA (`data.log` et `shared`). Aucune autre adaptation n'est requise de votre part.

Vous pouvez choisir entre deux types de stockage pour {{site.data.keyword.cloud_notm}} pour effectuer des sauvegardes et des restaurations pour SAP HANA. Les deux types utilisent des opérations d'entrée-sortie par seconde, qui permettent de déterminer les besoins en matière de stockage. Celles-ci sont mesurées en fonction d'une taille de bloc de 16 ko, avec une distribution égale entre les entrées et les sorties. Pour pouvoir effectuer le nombre maximal d'opérations d'entrée-sortie sur un volume, les ressources réseau adéquates doivent être disponibles. Vous devez également prendre en compte l'utilisation du réseau privé hors du stockage et hors côté hôte, ainsi que les réglages propres à l'application (par exemple les piles IP et les profondeurs de file d'attente). Pour plus d'informations, voir [About Block Storage](https://console.bluemix.net/docs/infrastructure/BlockStorage/index.html#getting-started-with-block-storage) et [Getting started with File Storage](https://console.bluemix.net/docs/infrastructure/FileStorage/index.html#getting-started-with-file-storage).

{{site.data.keyword.cloud_notm}} propose également le stockage NAS (Network Attached Storage), qui est intéressant si vous recherchez une solution de sauvegarde rapide et économique pour vos périphériques. Le stockage NAS peut être monté par le biais du système NFS et être utilisé avec le protocole FTP, avec Parallels Plesk Panel et cPanel@WHM.

Le stockage NAS peut être utilisé à n'importe quelle fin, mais dans ce cas, il ne doit *pas* être utilisé pour les données ou les fichiers journaux SAP HANA. Il ne remplit pas les critères des indicateurs clés de performance relatifs aux entrées-sorties. Toutefois, il peut être utilisé pour les unités de secours et d'autres types de données. Il peut être utilisé par SAP HANA en tant qu'unités de secours, pour les données et les fichiers journaux, lorsqu'il est monté via le système NFS.  
  
Les stockages NAS et FTP sont facturés tous les mois et disponibles dans différentes tailles. Vous pouvez interagir avec vos stockages NAS et FTP principalement depuis la ligne de commande ou un terminal du système d'exploitation, ou par le biais d'interactions de type "pointer-cliquer" dans les panneaux, sur le portail client de l'infrastructure {{site.data.keyword.cloud_notm}}. Sur ce portail client, vous pouvez consulter les détails et l'utilisation du stockage NAS, mais le service ne peut pas être manipulé hors de la ligne de commande, du noyau ou du panneau de configuration.

Pour plus d'informations sur le stockage NAS dans un environnement {{site.data.keyword.cloud_notm}}, voir [Getting started with NAS](https://console.bluemix.net/docs/infrastructure/network-attached-storage/index.html#getting-started-with-nas).

## Déploiement et gestion

Les serveurs Bare Metal d'{{site.data.keyword.cloud_notm}} sont déployés via le portail client de l'infrastructure {{site.data.keyword.cloud_notm}} ou l'API une fois que vous avez créé votre compte client {{site.data.keyword.cloud_notm}}. Ils peuvent être gérés par le biais du portail client, de l'API ou de l'interface de ligne de commande. Pour plus d'informations, voir [About bare metal servers](https://console.bluemix.net/docs/bare-metal/about.html#about-bare-metal-servers).

## Support

[Le support client d'{{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/support/index.html#getting-customer-support) traite toutes les demandes d'assistance et les problèmes pouvant survenir via divers canaux, notamment par chat, téléphone ou ticket de demande de service. Le support client est proposé gratuitement à tous les clients d'{{site.data.keyword.cloud_notm}} et traite la plupart des tickets de demande de service ouverts chaque jour. Pour plus d'informations, voir [Comment obtenir l'aide dont j'ai besoin ?](https://console.bluemix.net./docs/support/index.html#getting-customer-support).

Vous pouvez aussi continuer de créer via le support SAP des tickets de demande de service liés à vos produits SAP et à votre infrastructure sous forme de services (IaaS) {{site.data.keyword.cloud_notm}}. Pour plus d'informations, voir le [portail de support SAP](https://support.sap.com/en/index.html) et la [note SAP 2414820](https://launchpad.support.sap.com/#/notes/2414820).

## Installation de SAP HANA

Vos logiciels SAP HANA doivent être installés par un responsable de l'installation SAP HANA agréé qui a suivi le programme de certification pour l'installation de SAP HANA. Pour plus d'informations, voir [Who Can Install SAP HANA?](http://www.saphanacentral.com/p/who-can-install-sap-hana.html).
