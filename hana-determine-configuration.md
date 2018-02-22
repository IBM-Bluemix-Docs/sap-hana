---



copyright:
  years: 2018
lastupdated: "2018-02-06"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}


# 5. Determining your configuration
{: #determine_configuration}

The following tables list the SAP HANA configurations available with the {{site.data.keyword.cloud}} offering. For additional information considerations when running SAP HANA in a virtualized environment, see [VMware ESXi server deployements](/docs/infrastructure/sap-hana/hana-considerations.html#vmware-server).

## 512 GB SAP HANA memory
{: #512_GB_memory}
 
Table 1. SAP HANA 512 GB RAM configuration

|RAID 1 | 2x 800 GB s3710 |`hdd0, hdd1` | RAID1-A | 800 GB |
| --- | --- | --- | --- | --- |
| RAID 10 | 6x 800 GB s3710 | `hdd2, hdd3, hdd4, hdd5, hdd6, hdd7` | RAID10-B | 550 GB |
| RAID 10 | 6x 800 GB s3710 | `hdd2, hdd3, hdd4, hdd5, hdd6, hdd7` | RAID-10C | 1851 GB |
| Global Hotspare | 1x 800 GB s3710 | `hdd8` | 800 GB GHS | 800 GB |

| RAID1-A |   |   |   |
| --- | --- | --- | --- |
|   | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0.25 |
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

| Filesystem | Size | Used | Available | Use % | Mounted on |
| --- | --- | --- | --- | --- | --- |
| `/dev/sda2` | 48 G | 1.9 G | 44 G | 5% | `/` |
| `/dev/sda1` | 477 M | 41 M | 411 M | 9% | `/boot` |
| `/dev/sdc1` | 1.7 T | 69 M | 1.6 T | 1% | `/hana/data` |
| `/dev/sdb1` | 542 G | 70 M | 514 G | 1% | `/hana/log` |
| `/dev/sda6` | 633 G | 70 M | 601 G | 1% | `/hana/shared` |
| `/dev/sda3` | 48 G | 52 M | 46 G | 1% | `/usr/sap` |


## 1024 GB (1 TB) SAP HANA memory
{: #1024_GB_memory}
 
Table 2. SAP HANA 1024 GB (1 TB)  RAM configuration

|RAID 1 | 2x 800 GB s3710 |`hdd0, hdd1` | RAID1-A | 800 GB |
| --- | --- | --- | --- | --- |
| RAID 10 | 6x 800 GB s3710 | `hdd2, hdd3, hdd4, hdd5, hdd6, hdd7` | RAID10-B | 2400 GB |
| RAID 10 | 8x 800 GB s3710 | `hdd8, hdd9, hdd10, hdd11, hdd12, hdd13, hdd14, hdd15` | RAID-10C | 3200 GB |
| Global Hotspare | 1x 800 GB s3710 | `hdd16` | 800 GB GHS | 800 GB |

| RAID1-A |   |   |   |
| --- | --- | --- | --- |
|   | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0.25 |
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

| Filesystem | Size | Used | Available | Use % | Mounted on |
| --- | --- | --- | --- | --- | --- |
| `/dev/sda1` | 239 M | 41 M | 186 M | 18% | `/boot` |
| `/dev/sdc1` | 2.9 T | 72 M | 2.8 T | 1% | `/hana/data` |
| `/dev/sdb2` | 1.2 T | 71 M | 1.1 T | 1% | `/hana/log` |
| `/dev/sda1` | 1.1 T | 71 M | 1004 G | 1% | `/hana/shared` |


## 2048 GB (2 TB) SAP HANA memory
{: #2048_GB_memory}
 
Table 3. SAP HANA 2048 GB (2 TB) RAM configuration

|RAID 1 | 2x 800 GB s3710 |`hdd0, hdd1` | RAID1-A | 800 GB |
| --- | --- | --- | --- | --- |
| RAID 10 | 8x 800 GB s3710 | `hdd2, hdd3, hdd4, hdd5, hdd6, hdd7, hdd8, hdd9` | RAID10-B | 4800 GB |
| RAID 10 | 106x 1.2 TB S3710 | `hdd10, hdd11, hdd12, hdd15, hdd16, hdd17, hdd18, hdd19, hdd20, hdd21` | RAID-10C | 7200 GB |
| Global Hotspare | 1x 800 GB S3710 | `hdd22` | 800 GB GHS | 800 GB |
| RAID 10-C Hotspare | 1x 1.2 TB S3710 | `hdd23` | 1.2 TB Hotspare | 1.2 TB |

| RAID1-A |   |   |   |
| --- | --- | --- | --- |
|   | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0.25 |
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

| Filesystem | Size | Used | Available | Use % | Mounted on |
| --- | --- | --- | --- | --- | --- |
| `/dev/sda1` | 239 M | 41 M | 186 M | 18% | `/boot` |
| `/dev/sdc1` | 6.5 T | 53 M | 6.2 T | 1% | `/hana/data` |
| `/dev/sdb2` | 2.3 T | 73 M | 2.2 T | 1% | `/hana/log` |
| `/dev/sdb1` | 2.1 T | 73 M | 2.0 T | 1% | `/hana/shared` |


## 4096 GB (4 TB) SAP HANA memory 
{: #4096_GB_memory}
 
Table 4. SAP HANA 4096 GB (4 TB) RAM configuration 

|RAID 1 | 3x 800 GB s3710 |`hdd0` | RAID1-A | 800 GB |
| --- | --- | --- | --- | --- |
| RAID 5 | 6x 1.2 TB s3710 | `hdd1` | RAID5-B | 4100 GB |
| RAID 5 | 9x 1.2 TB s3710 | `hdd2` | RAID-5C | 8400 GB |
|Global Hotspare | 1x 800 GB S3710 | `hdd22` | 800 GB GHS | 800 GB |

| RAID1-A |   |   |   |
| --- | --- | --- | --- |
|   | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0.25 |
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

| Filesystem | Size | Used | Available | Use % | Mounted on |
| --- | --- | --- | --- | --- | --- |
|  |  |  |  |  |  |
|  |  |  |  |  |  |
|  |  |  |  |  |  |
|  |  |  |  |  |  |
|  |  |  |  |  |  |
|  |  |  |  |  |  |


## 8192 GB (8 TB) SAP HANA memory
{: #8192_GB_memory}
 
Table 5. SAP HANA 8192 GB (8 TB) RAM configuration

|RAID 1 | 2x 800 GB s3710 | +1 Hotspare | RAID1-A | 800 GB |
| --- | --- | --- | --- | --- |
| RAID 5 | 8x 1.2 tB S3710 |  | RAID5-B | 8400 GB |
| RAID 5 | 18x 1.2 TB S3710 | +1 Hotspare | RAID5-C | 20400 GB |

| RAID1-A |   |   |   |
| --- | --- | --- | --- |
|   | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0.25 |
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

| Filesystem | Size | Used | Available | Use % | Mounted on |
| --- | --- | --- | --- | --- | --- |
| `/dev/sda2` | 48 G | 1.9 G | 44 G | 5% | `/` |
| `/dev/sda1` | 239 M | 41 M | 186 M | 18% | `/boot` |
| `/dev/sdc1` | 6.5 T | 53 M | 6.2 T | 1% | `/hana/data` |
| `/dev/sdb2` | 2.3 T | 73 M | 2.2 T | 1% | `/hana/log` |
| `/dev/sdb1` | 2.1 T | 73 M | 2.0 T | 1% | `/hana/shared` |

## Next Steps

You are now ready to begin Provisioning your {{site.data.keyword.baremetal_short}}. See [Provisioning your SAP HANA environment](/docs/infrastructure/sap-hana/hana-provision-environment.html) for your next steps.
