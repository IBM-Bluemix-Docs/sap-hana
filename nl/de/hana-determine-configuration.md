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


# 5. Konfiguration festlegen
{: #determine_configuration}

In der folgenden Tabelle sind die SAP HANA-Konfigurationen aufgeführt, die mit dem {{site.data.keyword.cloud}}-Angebot verfügbar sind. Weitere Informationen und zu berücksichtigende Aspekte für die Ausführung von SAP HANA in einer virtualisierten Umgebung finden Sie unter [VMware ESXi-Serverbereitstellungen](/docs/infrastructure/sap-hana/hana-considerations.html#vmware-server).

## SAP HANA-Speicher von 512 GB
{: #512_GB_memory}
 
Tabelle 1. Konfiguration von SAP HANA mit 512 GB RAM

|RAID 1 | 2x 800 GB s3710 |`hdd0, hdd1` | RAID1-A | 800 GB |
| --- | --- | --- | --- | --- |
| RAID 10 | 6x 800 GB s3710 | `hdd2, hdd3, hdd4, hdd5, hdd6, hdd7` | RAID10-B | 550 GB |
| RAID 10 | 6x 800 GB s3710 | `hdd2, hdd3, hdd4, hdd5, hdd6, hdd7` | RAID-10C | 1851 GB |
| Globale Hot-Spare-Einheit | 1x 800 GB s3710 | `hdd8` | 800 GB GHS | 800 GB |

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


## SAP-Speicher von 1024 GB (1 TB)
{: #1024_GB_memory}
 
Tabelle 2. SAP HANA-Konfiguration für 1024 GB (1 TB) RAM

|RAID 1 | 2x 800 GB s3710 |`hdd0, hdd1` | RAID1-A | 800 GB |
| --- | --- | --- | --- | --- |
| RAID 10 | 6x 800 GB s3710 | `hdd2, hdd3, hdd4, hdd5, hdd6, hdd7` | RAID10-B | 2400 GB |
| RAID 10 | 8x 800 GB s3710 | `hdd8, hdd9, hdd10, hdd11, hdd12, hdd13, hdd14, hdd15` | RAID-10C | 3200 GB |
| Globale Hot-Spare-Einheit | 1x 800 GB s3710 | `hdd16` | 800 GB GHS | 800 GB |

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


## SAP HANA-Speicher von 2048 GB (2 TB)
{: #2048_GB_memory}
 
Tabelle 3. SAP HANA-Konfiguration mit 2048 GB (2 TB) RAM

|RAID 1 | 2x 800 GB s3710 |`hdd0, hdd1` | RAID1-A | 800 GB |
| --- | --- | --- | --- | --- |
| RAID 10 | 8x 800 GB s3710 | `hdd2, hdd3, hdd4, hdd5, hdd6, hdd7, hdd8, hdd9` | RAID10-B | 4800 GB |
| RAID 10 | 106x 1.2 TB S3710 | `hdd10, hdd11, hdd12, hdd15, hdd16, hdd17, hdd18, hdd19, hdd20, hdd21` | RAID-10C | 7200 GB |
| Globale Hot-Spare-Einheit | 1x 800 GB S3710 | `hdd22` | 800 GB GHS | 800 GB |
| RAID 10-C Hotspare | 1x 1,2 TB S3710 | `hdd23` | 1,2 TB Hotspare | 1,2 TB |

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


## SAP HANA-Speicher mit 4096 GB (4 TB) 
{: #4096_GB_memory}
 
Tabelle 4. SAP HANA-Konfiguration mit 4096 GB (4 TB) RAM 

|RAID 1 | 3x 800 GB s3710 |`hdd0` | RAID1-A | 800 GB |
| --- | --- | --- | --- | --- |
| RAID 5 | 6x 1,2 TB s3710 | `hdd1` | RAID5-B | 4100 GB |
| RAID 5 | 9x 1,2 TB s3710 | `hdd2` | RAID-5C | 8400 GB |
|Globale Hot-Spare-Einheit | 1x 800 GB S3710 | `hdd22` | 800 GB GHS | 800 GB |

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


## SAP HANA-Speicher mit 8192 GB (8 TB)
{: #8192_GB_memory}
 
Tabelle 5. SAP HANA-Konfiguration mit 8192 GB (8 TB) RAM

|RAID 1 | 2x 800 GB s3710 | +1 Hotspare | RAID1-A | 800 GB |
| --- | --- | --- | --- | --- |
| RAID 5 | 8x 1,2 tB S3710 |  | RAID5-B | 8400 GB |
| RAID 5 | 18x 1,2 TB S3710 | +1 Hotspare | RAID5-C | 20400 GB |

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

## Nächste Schritte

Sie sind jetzt bereit, mit der Bereitstellung Ihrer {{site.data.keyword.baremetal_short}} zu beginnen. Die nächsten Schritte finden Sie in [SAP HANA-Umgebung bereitstellen](/docs/infrastructure/sap-hana/hana-provision-environment.html).
