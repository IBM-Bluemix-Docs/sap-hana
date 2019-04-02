---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-26"

keywords: SAP HANA, {{site.data.keyword.baremetal_short}}, {{site.data.keyword.cloud_notm}}, database, application server

subcollection: sap-hana

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

Les tableaux ci-dessous répertorient les configurations {{site.data.keyword.baremetal_long}} disponibles avec l'offre d'infrastructure {{site.data.keyword.cloud}} certifiée SAP. Pour des considérations supplémentaires relatives à l'exécution de SAP HANA dans un environnement virtualisé, voir [Déploiement de serveurs VMware ESXi](/docs/infrastructure/sap-hana?topic=sap-hana-considerations#vmware_server).

## Déchiffrement des noms de serveur
{: #server-names}

Voici un exemple de la manière de déchiffrer les noms de serveur SAP HANA.

| Nom de serveur | Composant de convention de dénomination | Signification |
| --- | --- | --- |
| BI.S2.H8401 | BI | Interface Bluemix |
| | S2 | Série 2 (génération du processeur) |
| | | S1 correspond à Ivy Bridge/Haswell |
| | | S2 correspond à Broadwell |
| | | S3 correspond à Skylake/Kaby Lake |
| | H | Serveur certifié HANA |
| | 8 | Serveur à 8 sockets |
| | 4 | 4 To de RAM |
| | 01 | Numéro de révision (00 correspond au lancement, 01 à la première révision, etc.) |

## BI.S1.H512
{: #512_GB_memory}

| RAID | Composants | Unités | Grappe | Taille |
| --- | --- | --- | --- | --- |
| RAID 1 | 2 x 800 Go s3710 |`hdd0, hdd1` | RAID1-A | 800 Go |
| RAID 10 | 6 x 800 Go s3710 | `hdd2, hdd3, hdd4, hdd5, hdd6, hdd7` | RAID10-B | 550 Go |
| RAID 10 | 6 x 800 Go s3710 | `hdd2, hdd3, hdd4, hdd5, hdd6, hdd7` | RAID-10C | 1851 Go |
| Unité de secours à chaud globale | 1 x 800 Go s3710 | `hdd8` | Unité de secours à chaud globale de 800 Go | 800 Go |

| Grappe | Partition | Nom | Taille (Go) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0,25 |
|   | `/dev/sda2` | `/` | 50 |
|   | `/dev/sda3` | `/usr/sap` | 50 |
|   | `/dev/sda4` | `/hana/shared` | 512 |

| Grappe | Partition | Nom | Taille (Go) |
| --- | --- | --- | --- |
| RAID10-B | `/dev/sdb` |   | 550 |
|   | `/dev/sdb1` | `/hana/log` | `rest` |

| Grappe | Partition | Nom | Taille (Go) |
| --- | --- | --- | --- |
| RAID10-C | `/dev/sdc` |   | 1851 |
|   | `/dev/sdc1` | `/hana/data` | `rest` |


## BI.S1.H1000
{: #1024_GB_memory}

| RAID | Composants | Unités | Grappe | Taille |
| --- | --- | --- | --- | --- |
| RAID 1 | 2 x 800 Go s3710 |`hdd0, hdd1` | RAID1-A | 800 Go |
| RAID 10 | 6 x 800 Go s3710 | `hdd2, hdd3, hdd4, hdd5, hdd6, hdd7` | RAID10-B | 2400 Go |
| RAID 10 | 8 x 800 Go s3710 | `hdd8, hdd9, hdd10, hdd11, hdd12, hdd13, hdd14, hdd15` | RAID-10C | 3200 Go |
| Unité de secours à chaud globale | 1 x 800 Go s3710 | `hdd16` | Unité de secours à chaud globale de 800 Go | 800 Go |

| Grappe | Partition | Nom | Taille (Go) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0,25 |
|   | `/dev/sda2` | `/` | 50 |

| Grappe | Partition | Nom | Taille (Go) |
| --- | --- | --- | --- |
| RAID10-B | `/dev/sdb` |   | 2400 |
|   | `/dev/sdb1` | `/hana/shared` | 1104 |
|   |  | `/hana/log` | `rest` |

| Grappe | Partition | Nom | Taille (Go) |
| --- | --- | --- | --- |
| RAID10-C | `/dev/sdc` |   | 3200 |
|   | `/dev/sdc1` | `/hana/data` | `rest` |


## BI.S2.H4101
{: #H4101}

| RAID | Composants | Unités | Grappe | Taille |
| --- | --- | --- | --- | --- |
| RAID 1 + unité de secours à chaud | 3x 960 Go 5100 |`hdd0, hdd1, hdd2` | RAID1-A | 960 Go |
| RAID 1 + unité de secours à chaud | 3x 3,84 To 5100 | `hdd3, hdd4, hdd5` | RAID1-B | 3,84 To |

| Grappe | Partition | Nom | Taille (Go) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 1.0 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` |
|   | `/dev/sda4` | `/hana/log` |

| Grappe | Partition | Nom | Taille (Go) |
| --- | --- | --- | --- |
| RAID1-B | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 1024 |
|   | `/dev/sdb2` | `/hana/data` | `rest` |

## BI.S2.H4100
{: #H4100}

| RAID | Composants | Unités | Grappe | Taille |
| --- | --- | --- | --- | --- |
| RAID 1 | 2 x 800 Go s3710 | `hdd0, hdd1, hdd2` | RAID1-A | 800 Go |
| RAID 5 | 3 x 800 Go s3710 | `hdd3, hdd4, hdd5, hdd6` | RAID5-B | 1600 Go |
| RAID 5 | 4x 800 Go s3710 | `hdd7, hdd8, hdd9, hdd10, hdd11` | RAID5-C | 2400 Go |
| Unité de secours à chaud dédiée | 1X 800 Go s3710 | `hdd2, hdd6, hdd11` | 800 Go DHS | 800 Go |

| Grappe | Partition | Nom | Taille (Go) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0,25 |
|   | `/dev/sda2` | `/hana/log` | 512 |
|   | `/dev/sda3` | `/` | `rest` |

| Grappe | Partition | Nom | Taille (Go) |
| --- | --- | --- | --- |
| RAID5-B  | `/dev/sdb` |   | 4100 |
|   | `/dev/sdb1` | `/hana/shared` | `rest` |

| Grappe | Partition | Nom | Taille (Go) |
| --- | --- | --- | --- |
| RAID5-C  | `/dev/sdc` |   | 4100 |
|   | `/dev/sdc1` | `/hana/data` | `rest` |


## BI.S2.H4201
{: #4201}

| RAID | Composants | Unités | Grappe | Taille |
| --- | --- | --- | --- | --- |
| RAID 1 + unité de secours à chaud| 3x 960 Go 5100 |`hdd0, hdd1, hdd2` | RAID1-A | 960 Go |
| RAID 10 + unité de secours à chaud | 7x 1,92 To 5100 | `hdd3, hdd4, hdd5, hdd6, hdd7, hdd8, hdd9` | RAID10-B | 5,76 To |

| Grappe | Partition | Nom | Taille (Go) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 1.0 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` | `rest` |

| Grappe | Partition | Nom | Taille (Go) |
| --- | --- | --- | --- |
| RAID10-B | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 1024 |
|   | `/dev/sdb2` | `/hana/data` | `rest` |


## BI.S2.H4200
{: #H4200}

| RAID | Composants | Unités | Grappe | Taille |
| --- | --- | --- | --- | --- |
| RAID 1 | 2 x 800 Go s3710 | `hdd0, hdd1, hdd2` | RAID1-A | 800 Go |
| RAID 5 | 3x 1,2 To s3710 | `hdd3, hdd4, hdd5, hdd6` | RAID5-B | 2,4 To |
| RAID 5 | 5x 1,2 To s3710 | `hdd7, hdd8, hdd9, hdd10, hdd11` | RAID5-C | 4,8 To |
| Unité de secours à chaud dédiée | 1X 800 Go s3710 | `hdd2, hdd6, hdd11` | 800 Go DHS | 800 Go |

| Grappe | Partition | Nom | Taille (Go) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0,25 |
|   | `/dev/sda2` | `/hana/log` | 512 |
|   | `/dev/sda3` | `/` | `rest` |

| Grappe | Partition | Nom | Taille (Go) |
| --- | --- | --- | --- |
| RAID5-B  | `/dev/sdb` |   | 4100 |
|   | `/dev/sdb1` | `/hana/shared` | `rest` |

| Grappe | Partition | Nom | Taille (Go) |
| --- | --- | --- | --- |
| RAID5-C  | `/dev/sdc` |   | 4100 |
|   | `/dev/sdc1` | `/hana/data` | `rest` |


## BI.S1.H2000
{: #2048_GB_memory}

| RAID | Composants | Unités | Grappe | Taille |
| --- | --- | --- | --- | --- |
| RAID 1 | 2 x 800 Go s3710 |`hdd0, hdd1` | RAID1-A | 800 Go |
| RAID 10 | 8 x 800 Go s3710 | `hdd2, hdd3, hdd4, hdd5, hdd6, hdd7, hdd8, hdd9` | RAID10-B | 4800 Go |
| RAID 10 | 106 x 1,2 To s3710 | `hdd10, hdd11, hdd12, hdd15, hdd16, hdd17, hdd18, hdd19, hdd20, hdd21` | RAID-10C | 7200 Go |
| Unité de secours à chaud globale | 1 x 800 Go s3710 | `hdd22` | Unité de secours à chaud globale de 800 Go | 800 Go |
| Unité de secours à chaud RAID 10-C | 1 x 1,2 To s3710 | `hdd23` | Unité de secours à chaud 1,2 To | 1,2 To |

| Grappe | Partition | Nom | Taille (Go) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0,25 |
|   | `/dev/sda2` | `/` | `rest` |

| Grappe | Partition | Nom | Taille (Go) |
| --- | --- | --- | --- |
| RAID10-B | `/dev/sdb` |   | 4800 |
|   | `/dev/sdb1` | `/hana/log` | `rest` |
|   | `/dev/sdb2` | `/hana/shared` | 2200 |

| Grappe | Partition | Nom | Taille (Go) |
| --- | --- | --- | --- |
| RAID10-C | `/dev/sdc` |   | 7200 |
|   | `/dev/sdc1` | `/hana/data` | `rest` |


## BI.S2.H4401
{: #H4401}

| RAID | Composants | Unités | Grappe | Taille |
| --- | --- | --- | --- | --- |
| RAID 1 + unité de secours à chaud | 3x 960 Go 5100 |`hdd0, hdd1, hdd2` | RAID1-A | 960 Go |
| RAID 10 + unité de secours à chaud | 5x 3,84 To 5100 | `hdd3, hdd4, hdd5, hdd6, hdd7` | RAID10-B | 7,68 To |

| Grappe | Partition | Nom | Taille (Go) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 1.0 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` | `rest` |

| Grappe | Partition | Nom | Taille (Go) |
| --- | --- | --- | --- |
| RAID10-B  | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 1024 |
|   | `/dev/sdb2` | `/hana/data` | `rest` |


## BI.S2.H8401
{: #H8401}

| RAID | Composants | Unités | Grappe | Taille |
| --- | --- | --- | --- | --- |
| RAID 1 + unité de secours à chaud| 3x 960 Go 5100 |`hdd0, hdd1, hdd2` | RAID1-A | 960 Go |
| RAID 10 + unité de secours à chaud | 5x 3,84 To 5100 | `hdd3, hdd4, hdd5, hdd6, hdd7` | RAID10-B | 7,68 To |

| Grappe | Partition | Nom | Taille (Go) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 1.0 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` | `rest` |

| Grappe | Partition | Nom | Taille (Go) |
| --- | --- | --- | --- |
| RAID10-B  | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 1024 |
|   | `/dev/sdb2` | `hana/data` | `rest` |


## BI.S2.H4400
{: #4096_GB_memory}

| RAID | Composants | Unités | Grappe | Taille |
| --- | --- | --- | --- | --- |
| RAID 1 | 3 x 800 Go s3710 |`hdd0` | RAID1-A | 800 Go |
| RAID 5 | 6 x 1,2 To s3710 | `hdd1` | RAID5-B | 4100 Go |
| RAID 5 | 9 x 1,2 To s3710 | `hdd2` | RAID-5C | 8400 Go |
| Unité de secours à chaud globale | 1 x 800 Go s3710 | `hdd22` | Unité de secours à chaud globale de 800 Go | 800 Go |

| Grappe | Partition | Nom | Taille (Go) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0,25 |
|   | `/dev/sda2` | `/hana/log` | 512 |
|   | `/dev/sda3` | `/` | `rest` |

| Grappe | Partition | Nom | Taille (Go) |
| --- | --- | --- | --- |
| RAID5-B  | `/dev/sdb` |   | 4100 |
|   | `/dev/sdb1` | `/hana/shared` | `rest` |

| Grappe | Partition | Nom | Taille (Go) |
| --- | --- | --- | --- |
| RAID5-C  | `/dev/sdc` |   | 4100 |
|   | `/dev/sdc1` | `/hana/data` | `rest` |


## BI.S2.H4400
{: #H4400}

| RAID | Composants | Unités | Grappe | Taille |
| --- | --- | --- | --- | --- |
| RAID 1 | 3 x 800 Go s3710 |`hdd0` | RAID1-A | 800 Go |
| RAID 5 | 6 x 1,2 To s3710 | `hdd1` | RAID5-B | 4100 Go |
| RAID 5 | 9 x 1,2 To s3710 | `hdd2` | RAID-5C | 8400 Go |
| Unité de secours à chaud globale | 1 x 800 Go s3710 | `hdd22` | Unité de secours à chaud globale de 800 Go | 800 Go |

| Grappe | Partition | Nom | Taille (Go) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0,25 |
|   | `/dev/sda2` | `/hana/log` | 512 |
|   | `/dev/sda3` | `/` | `rest` |

| Grappe | Partition | Nom | Taille (Go) |
| --- | --- | --- | --- |
| RAID5-B  | `/dev/sdb` |   | 4100 |
|   | `/dev/sdb1` | `/hana/shared` | `rest` |

| Grappe | Partition | Nom | Taille (Go) |
| --- | --- | --- | --- |
| RAID5-C  | `/dev/sdc` |   | 4100 |
|   | `/dev/sdc1` | `/hana/data` | `rest` |



## BI.S2.H8801
{: #H8801}

| RAID | Composants | Unités | Grappe | Taille |
| --- | --- | --- | --- | --- |
| RAID 1 + unité de secours à chaud | 3x 960 Go 5100 |`hdd0, hdd1, hdd2` | RAID1-A | 960 Go |
| RAID 10 + unité de secours à chaud | 7x 3,84 To 5100 | `hdd3, hdd4, hdd5, hdd6, hdd7, hdd8, hdd9` | RAID10-B | 15,36 To |

| Grappe | Partition | Nom | Taille (Go) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 1.0 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` | `rest` |

| Grappe | Partition | Nom | Taille (Go) |
| --- | --- | --- | --- |
| RAID10-B  | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 1024 |
|   | `/dev/sdb2` | `/hana/data` | `rest` |


## BI.S2.H8800
{: #8192_GB_memory}

| RAID | Composants | Unités | Grappe | Taille |
| --- | --- | --- | --- | --- |
| RAID 1 | 2 x 800 Go s3710 | +1 unité de secours à chaud | RAID1-A | 800 Go |
| RAID 5 | 8x 1,2 To S3710 |  | RAID5-B | 8400 Go |
| RAID 5 | 18 x 1,2 To s3710 | +1 unité de secours à chaud | RAID5-C | 20400 Go |

| Grappe | Partition | Nom | Taille (Go) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0,25 |
|   | `/dev/sda2` | `/` | `rest` |

| Grappe | Partition | Nom | Taille (Go) |
| --- | --- | --- | --- |
| RAID5-B | `/dev/sdb` |   | 4800 |
|   | `/dev/sdb1` | `/hana/log` | `rest` |
|   | `/dev/sdb2` | `/hana/shared` | 2200 |

| Grappe | Partition | Nom | Taille (Go) |
| --- | --- | --- | --- |
| RAID5-C | `/dev/sdc` |   | 7200 |
|   | `/dev/sdc1` | `/hana/data` | `rest` |


## BI.S3.H2192
{: #2192_GB_memory}

| RAID | Composants | Unités | Grappe | Taille |
| --- | --- | --- | --- | --- |
| RAID 1 | 2x 960 Go 5100 | `hdd0, hdd1` | RAID1-A | 960 Go |
| RAID 1 | 2x 960 Go 5100 | `hdd2, hdd3` | RAID1-B | 960 Go |
| Unité de secours à chaud globale | 1x 960 Go 5100 | `hdd4` |  |  |

| Grappe | Partition | Nom | Taille (Go) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 50 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` |  |

| Grappe | Partition | Nom | Taille (Go) |
| --- | --- | --- | --- |
| RAID1-B | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 250 |
|   | `/dev\sdb2` | `/hana/data` | `rest` |

## BI.S3.H2384
{: #2384_GB_memory}

| RAID | Composants | Unités | Grappe | Taille |
| --- | --- | --- | --- | --- |
| RAID 1 | 2x 960 Go 5100 |`hdd0, hdd1` | RAID1-A | 960 Go |
| RAID 10 | 4x 960 Go 5100 | `hdd2, hdd3, hdd4, hdd5` | RAID1-B | 1920 Go |
| Unité de secours à chaud globale | 1x 960 Go 5100 | `hdd` |  |  |

| Grappe | Partition | Nom | Taille (Go) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 50 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` |  |

| Grappe | Partition | Nom | Taille (Go) |
| --- | --- | --- | --- |
| RAID1-B | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 500 |
|   | `/dev\sdb2` | `/hana/data` | `rest` |

## VMware
{: #vmware}

Vous êtes chargé de définir les configurations VMware de votre serveur. Vous avez le choix entre trois tailles : 1 To (BI.S2.H4100 (VMware)), 2 To (BI.S2.H4200 (VMware)) et 4 To (BI.S2.4400 (VMware)). Pour plus d'informations sur la configuration de VMware sur vos serveurs Bare Metal certifiés SAP, voir [Architecture Guidelines and Best Practices for Deployments of SAP HANA on VMware vSphere Architecture and Technical Considerations Guide ![Icône de lien externe](../icons/launch-glyph.svg "Icône de lien externe")](https://www.vmware.com/content/dam/digitalmarketing/vmware/en/pdf/whitepaper/sap_hana_on_vmware_vsphere_best_practices_guide-white-paper.pdf){: new_window} (PDF).

## Etapes suivantes

Vous pouvez maintenant commencer à mettre à disposition vos serveurs Bare Metal. Voir [Mise à disposition de votre environnement SAP HANA](/docs/infrastructure/sap-hana?topic=sap-hana-provision_environment#provision_environment) pour les étapes suivantes.
