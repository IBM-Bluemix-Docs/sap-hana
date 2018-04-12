---



copyright:
  years: 2018
lastupdated: "2018-02-23"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}


# 5. Détermination de votre configuration 
{: #determine_configuration}

Les tableaux ci-dessous répertorient les configurations SAP HANA disponibles avec l'offre {{site.data.keyword.cloud}}. Pour des informations supplémentaires relatives à l'exécution de SAP HANA dans un environnement virtualisé, voir [Déploiement de serveurs VMware ESXi](/docs/infrastructure/sap-hana/hana-considerations.html#vmware-server).

## Mémoire SAP HANA de 512 Go 
{: #512_GB_memory}
 
Tableau 1. Configuration de SAP HANA avec une mémoire RAM de 512 Go 

|RAID 1 | 2 x 800 Go s3710 |`hdd0, hdd1` | RAID1-A | 800 Go |
| --- | --- | --- | --- | --- |
| RAID 10 | 6 x 800 Go s3710 | `hdd2, hdd3, hdd4, hdd5, hdd6, hdd7` | RAID10-B | 550 Go |
| RAID 10 | 6 x 800 Go s3710 | `hdd2, hdd3, hdd4, hdd5, hdd6, hdd7` | RAID-10C | 1851 Go |
| Unité de secours à chaud globale | 1 x 800 Go s3710 | `hdd8` | Unité de secours à chaud globale de 800 Go | 800 Go |

| RAID1-A |   |   |   |
| --- | --- | --- | --- |
|   | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0,25 |
|   | `/dev/sda2` | `/` | 50 |
|   | `/dev/sda3` | `/usr/sap` | 50 |
|   | `/dev/sda4` | `/hana/shared` | 512 |

| RAID10-B |   |   |   |
| --- | --- | --- | --- |
|   | `/dev/sdb` |   | 550 |
|   | `/dev/sdb1` | `/hana/log` | `rest` |

| RAID10-C |   |   |   |
| --- | --- | --- | --- |
|   | `/dev/sdc` |   | 1851 |
|   | `/dev/sdc1` | `/hana/data` | `rest` |


## Mémoire SAP HANA de 1024 Go (1 To) 
{: #1024_GB_memory}
 
Tableau 2. Configuration de SAP HANA avec une mémoire RAM de 1024 Go (1 To) 

|RAID 1 | 2 x 800 Go s3710 |`hdd0, hdd1` | RAID1-A | 800 Go |
| --- | --- | --- | --- | --- |
| RAID 10 | 6 x 800 Go s3710 | `hdd2, hdd3, hdd4, hdd5, hdd6, hdd7` | RAID10-B | 2400 Go |
| RAID 10 | 8 x 800 Go s3710 | `hdd8, hdd9, hdd10, hdd11, hdd12, hdd13, hdd14, hdd15` | RAID-10C | 3200 Go |
| Unité de secours à chaud globale | 1 x 800 Go s3710 | `hdd16` | Unité de secours à chaud globale de 800 Go | 800 Go |

| RAID1-A |   |   |   |
| --- | --- | --- | --- |
|   | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0,25 |
|   | `/dev/sda2` | `/` | 50 |

| RAID10-B |   |   |   |
| --- | --- | --- | --- |
|   | `/dev/sdb` |   | 2400 |
|   | `/dev/sdb1` | `/hana/shared` | 1104 |
|   |  | `/hana/log` | `rest` |

| RAID10-C |   |   |   |
| --- | --- | --- | --- |
|   | `/dev/sdc` |   | 3200 |
|   | `/dev/sdc1` | `/hana/data` | `rest` |


## Mémoire SAP HANA de 2048 Go (2 To) 
{: #2048_GB_memory}
 
Tableau 3. Configuration de SAP HANA avec une mémoire RAM de 2048 Go (2 To) 

|RAID 1 | 2 x 800 Go s3710 |`hdd0, hdd1` | RAID1-A | 800 Go |
| --- | --- | --- | --- | --- |
| RAID 10 | 8 x 800 Go s3710 | `hdd2, hdd3, hdd4, hdd5, hdd6, hdd7, hdd8, hdd9` | RAID10-B | 4800 Go |
| RAID 10 | 106 x 1,2 To s3710 | `hdd10, hdd11, hdd12, hdd15, hdd16, hdd17, hdd18, hdd19, hdd20, hdd21` | RAID-10C | 7200 Go |
| Unité de secours à chaud globale | 1 x 800 Go s3710 | `hdd22` | Unité de secours à chaud globale de 800 Go | 800 Go |
| Unité de secours à chaud RAID 10-C | 1 x 1,2 To s3710 | `hdd23` | Unité de secours à chaud 1,2 To | 1,2 To|

| RAID1-A |   |   |   |
| --- | --- | --- | --- |
|   | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0,25 |
|   | `/dev/sda2` | `/` | `Rest` |

| RAID10-B |   |   |   |
| --- | --- | --- | --- |
|   | `/dev/sdb` |   | 4800 |
|   | `/dev/sdb1` | `/hana/log` | `Rest` |
|   | `/dev/sdb2` | `/hana/shared` | 2200 |

| RAID10-C |   |   |   |
| --- | --- | --- | --- |
|   | `/dev/sdc` |   | 7200 |
|   | `/dev/sdc1` | `/hana/data` | `Rest` |


## Mémoire SAP HANA de 4096 Go (4 To)  
{: #4096_GB_memory}
 
Tableau 4. Configuration de SAP HANA avec une mémoire RAM de 4096 Go (4 To)  

|RAID 1 | 3 x 800 Go s3710 |`hdd0` | RAID1-A | 800 Go |
| --- | --- | --- | --- | --- |
| RAID 5 | 6 x 1,2 To s3710 | `hdd1` | RAID5-B | 4100 Go |
| RAID 5 | 9 x 1,2 To s3710 | `hdd2` | RAID-5C | 8400 Go |
|Unité de secours à chaud globale | 1 x 800 Go s3710 | `hdd22` | Unité de secours à chaud globale de 800 Go | 800 Go |

| RAID1-A |   |   |   |
| --- | --- | --- | --- |
|   | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0,25 |
|   | `/dev/sda2` | `/hana/log` | 512 |
|   | `/dev/sda3` | `/` | `rest` |

| RAID5-B |   |   |   |
| --- | --- | --- | --- |
|   | `/dev/sdb` |   | 4100 |
|   | `/dev/sdb1` | `/hana/shared` | `rest` |

| RAID5-C |   |   |   |
| --- | --- | --- | --- |
|   | `/dev/sdc` |   | 4100 |
|   | `/dev/sdc1` | `/hana/data` | `rest` |


## Mémoire SAP HANA de 8192 Go (8 To) 
{: #8192_GB_memory}
 
Tableau 5. Configuration de SAP HANA avec une mémoire RAM de 8192 Go (8 To) 

|RAID 1 | 2 x 800 Go s3710 | +1 unité de secours à chaud | RAID1-A | 800 Go |
| --- | --- | --- | --- | --- |
| RAID 5 | 8 x 1,2 To s3710 |  | RAID5-B | 8400 Go |
| RAID 5 | 18 x 1,2 To s3710 | +1 unité de secours à chaud | RAID5-C | 20400 Go |

| RAID1-A |   |   |   |
| --- | --- | --- | --- |
|   | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0,25 |
|   | `/dev/sda2` | `/` | `rest` |

| RAID5-B |   |   |   |
| --- | --- | --- | --- |
|   | `/dev/sdb` |   | 4800 |
|   | `/dev/sdb1` | `/hana/log` | `rest` |
|   | `/dev/sdb2` | `/hana/shared` | 2200 |

| RAID5-C |   |   |   |
| --- | --- | --- | --- |
|   | `/dev/sdc` |   | 7200 |
|   | `/dev/sdc1` | `/hana/data` | `rest` |

## Etapes suivantes

Vous pouvez maintenant commencer à mettre à disposition vos serveurs Bare Metal. Voir [Mise à disposition de votre environnement SAP HANA](/docs/infrastructure/sap-hana/hana-provision-environment.html) pour les étapes suivantes. 
