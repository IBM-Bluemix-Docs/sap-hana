---



copyright:
  years: 2018
lastupdated: "2018-06-11"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}


# 5. 決定配置
{: #determine_configuration}

下列各表列出 {{site.data.keyword.cloud}} SAP 認證基礎架構供應項目所提供的 {{site.data.keyword.baremetal_long}} 配置。如需在虛擬化環境中執行 SAP HANA 時的其他考量，請參閱 [VMware ESXi 伺服器部署](/docs/infrastructure/sap-hana/hana-considerations.html#vmware-server)。

## B1.S1.H512
{: #512_GB_memory}
 
| RAID |元件|磁碟機|陣列|大小|
| --- | --- | --- | --- | --- |
|RAID 1 |2x 800 GB s3710 |`hdd0, hdd1` |RAID1-A |800 GB |
|RAID 10 |6x 800 GB s3710 |`hdd2, hdd3, hdd4, hdd5, hdd6, hdd7` |RAID10-B |550 GB |
|RAID 10 |6x 800 GB s3710 |`hdd2, hdd3, hdd4, hdd5, hdd6, hdd7` |RAID-10C |1851 GB |
|廣域緊急備用    |1x 800 GB s3710 |`hdd8` |800 GB GHS |800 GB |

|陣列|分割區|名稱|大小 (GB) |
| --- | --- | --- | --- |
|RAID1-A |`/dev/sda` |   |800 |
|   |`/dev/sda1` |`/boot` |0.25 |
|   |`/dev/sda2` | `/` |50 |
|   |`/dev/sda3` |`/usr/sap` |50 |
|   |`/dev/sda4` |`/hana/shared` |512 |

|陣列|分割區|名稱|大小 (GB) |
| --- | --- | --- | --- |
|RAID10-B |`/dev/sdb` |   |550 |
|   |`/dev/sdb1` |`/hana/log` |`rest` |

|陣列|分割區|名稱|大小 (GB) |
| --- | --- | --- | --- |
|RAID10-C |`/dev/sdc` |   |1851 |
|   |`/dev/sdc1` |`/hana/data` |`rest` |


## B1.S1.H1000
{: #1024_GB_memory}

| RAID |元件|磁碟機|陣列|大小|
| --- | --- | --- | --- | --- |
|RAID 1 |2x 800 GB s3710 |`hdd0, hdd1` |RAID1-A |800 GB |
|RAID 10 |6x 800 GB s3710 |`hdd2, hdd3, hdd4, hdd5, hdd6, hdd7` |RAID10-B |2400 GB |
|RAID 10 |8x 800 GB s3710 |`hdd8, hdd9, hdd10, hdd11, hdd12, hdd13, hdd14, hdd15` |RAID-10C |3200 GB |
|廣域緊急備用    |1x 800 GB s3710 |`hdd16` |800 GB GHS |800 GB |

|陣列|分割區|名稱|大小 (GB) |
| --- | --- | --- | --- |
|RAID1-A |`/dev/sda` |   |800 |
|   |`/dev/sda1` |`/boot` |0.25 |
|   |`/dev/sda2` | `/` |50 |

|陣列|分割區|名稱|大小 (GB) |
| --- | --- | --- | --- |
|RAID10-B |`/dev/sdb` |   |2400 |
|   |`/dev/sdb1` |`/hana/shared` |1104 |
|   |  |`/hana/log` |`rest` |

|陣列|分割區|名稱|大小 (GB) |
| --- | --- | --- | --- |
|RAID10-C |`/dev/sdc` |   |3200 |
|   |`/dev/sdc1` |`/hana/data` |`rest` |


## B1.S2.H4101
{: #H4101}

| RAID |元件|磁碟機|陣列|大小|
| --- | --- | --- | --- | --- |
| RAID 1 + 緊急備用| 3x 960 GB 5100 |`hdd0, hdd1, hdd2` |RAID1-A | 960 GB |
| RAID 1 + 緊急備用| 3x 3.84 TB 5100 | `hdd3, hdd4, hdd5` | RAID1-B | 3.84 TB |

|陣列|分割區|名稱|大小 (GB) |
| --- | --- | --- | --- |
|RAID1-A |`/dev/sda` |   |  |
|   |`/dev/sda1` |`/boot` | 1.0 |
|   |`/dev/sda2` | `/` | 150 |
|   |`/dev/sda3` |`/usr/sap` |
|   |`/dev/sda4` |`/hana/log` |

|陣列|分割區|名稱|大小 (GB) |
| --- | --- | --- | --- |
| RAID1-B |`/dev/sdb` |   |  |
|   |`/dev/sdb1` |`/hana/shared` | 1024 |
|   |`/dev/sdb2` |`/hana/data` |`rest` |

## B1.S2.H4100
{: #H4100}

| RAID |元件|磁碟機|陣列|大小|
| --- | --- | --- | --- | --- |
|RAID 1 |2x 800 GB s3710 | `hdd0, hdd1, hdd2` |RAID1-A |800 GB |
|RAID 5 |3x 800 GB s3710 | `hdd3, hdd4, hdd5, hdd6` |RAID5-B | 1600 GB |
|RAID 5 | 4x 800 GB s3710 | `hdd7, hdd8, hdd9, hdd10, hdd11` |RAID5-C |2400 GB |
|專用緊急備用| 1X 800 GB s3710 | `hdd2, hdd6, hdd11` | 800 GB DHS |800 GB |

|陣列|分割區|名稱|大小 (GB) |
| --- | --- | --- | --- |
|RAID1-A |`/dev/sda` |   |800 |
|   |`/dev/sda1` |`/boot` |0.25 |
|   |`/dev/sda2` |`/hana/log` |512 |
|   |`/dev/sda3` | `/` |`rest` |

|陣列|分割區|名稱|大小 (GB) |
| --- | --- | --- | --- |
|RAID5-B |`/dev/sdb` |   |4100 |
|   |`/dev/sdb1` |`/hana/shared` |`rest` |

|陣列|分割區|名稱|大小 (GB) |
| --- | --- | --- | --- |
|RAID5-C |`/dev/sdc` |   |4100 |
|   |`/dev/sdc1` |`/hana/data` |`rest` |


## B1.S2.H4201
{: #4201}

| RAID |元件|磁碟機|陣列|大小|
| --- | --- | --- | --- | --- |
| RAID 1 + 緊急備用| 3x 960 GB 5100 |`hdd0, hdd1, hdd2` |RAID1-A | 960 GB |
| RAID 10 + 緊急備用| 7x 1.92 TB 5100 | `hdd3, hdd4, hdd5, hdd6, hdd7, hdd8, hdd9` |RAID10-B | 5.76 TB |

|陣列|分割區|名稱|大小 (GB) |
| --- | --- | --- | --- |
|RAID1-A |`/dev/sda` |   |  |
|   |`/dev/sda1` |`/boot` | 1.0 |
|   |`/dev/sda2` | `/` | 150 |
|   |`/dev/sda3` |`/usr/sap` | 150 |
|   |`/dev/sda4` |`/hana/log` |`rest` |

|陣列|分割區|名稱|大小 (GB) |
| --- | --- | --- | --- |
|RAID10-B |`/dev/sdb` |   |  |
|   |`/dev/sdb1` |`/hana/shared` | 1024 |
|   |`/dev/sdb2` |`/hana/data` |`rest` |


## B1.S2.H4200
{: #H4200}

| RAID |元件|磁碟機|陣列|大小|
| --- | --- | --- | --- | --- |
|RAID 1 |2x 800 GB s3710 | `hdd0, hdd1, hdd2` |RAID1-A |800 GB |
|RAID 5 | 3x 1.2 TB s3710 | `hdd3, hdd4, hdd5, hdd6` |RAID5-B | 2.4 TB |
|RAID 5 | 5x 1.2 TB s3710 | `hdd7, hdd8, hdd9, hdd10, hdd11` |RAID5-C | 4.8 TB |
|專用緊急備用| 1X 800 GB s3710 | `hdd2, hdd6, hdd11` | 800 GB DHS |800 GB |

|陣列|分割區|名稱|大小 (GB) |
| --- | --- | --- | --- |
|RAID1-A |`/dev/sda` |   |800 |
|   |`/dev/sda1` |`/boot` |0.25 |
|   |`/dev/sda2` |`/hana/log` |512 |
|   |`/dev/sda3` | `/` |`rest` |

|陣列|分割區|名稱|大小 (GB) |
| --- | --- | --- | --- |
|RAID5-B |`/dev/sdb` |   |4100 |
|   |`/dev/sdb1` |`/hana/shared` |`rest` |

|陣列|分割區|名稱|大小 (GB) |
| --- | --- | --- | --- |
|RAID5-C |`/dev/sdc` |   |4100 |
|   |`/dev/sdc1` |`/hana/data` |`rest` |


## B1.S1.H2000
{: #2048_GB_memory}
 
| RAID |元件|磁碟機|陣列|大小|
| --- | --- | --- | --- | --- |
|RAID 1 |2x 800 GB s3710 |`hdd0, hdd1` |RAID1-A |800 GB |
|RAID 10 |8x 800 GB s3710 |`hdd2, hdd3, hdd4, hdd5, hdd6, hdd7, hdd8, hdd9` |RAID10-B |4800 GB |
|RAID 10 |106x 1.2 TB S3710 |`hdd10, hdd11, hdd12, hdd15, hdd16, hdd17, hdd18, hdd19, hdd20, hdd21` |RAID-10C |7200 GB |
|廣域緊急備用    |1x 800 GB S3710 |`hdd22` |800 GB GHS |800 GB |
|RAID 10-C 緊急備用 |1x 1.2 TB S3710 |`hdd23` |1.2 TB 緊急備用 |1.2 TB |

|陣列|分割區|名稱|大小 (GB) |
| --- | --- | --- | --- |
|RAID1-A |`/dev/sda` |   |800 |
|   |`/dev/sda1` |`/boot` |0.25 |
|   |`/dev/sda2` | `/` |`Rest` |

|陣列|分割區|名稱|大小 (GB) |
| --- | --- | --- | --- |
|RAID10-B |`/dev/sdb` |   |4800 |
|   |`/dev/sdb1` |`/hana/log` |`Rest` |
|   |`/dev/sdb2` |`/hana/shared` |2200 |

|陣列|分割區|名稱|大小 (GB) |
| --- | --- | --- | --- |
|RAID10-C |`/dev/sdc` |   |7200 |
|   |`/dev/sdc1` |`/hana/data` |`Rest` |


## B1.S2.H4401
{: #H4401}
 
| RAID |元件|磁碟機|陣列|大小|
| --- | --- | --- | --- | --- |
| RAID 1 + 緊急備用| 3x 960 GB 5100 |`hdd0, hdd1, hdd2` |RAID1-A | 960 GB |
| RAID 10 + 緊急備用| 5x 3.84 TB 5100 | `hdd3, hdd4, hdd5, hdd6, hdd7` |RAID10-B | 7.68 TB |

|陣列|分割區|名稱|大小 (GB) |
| --- | --- | --- | --- |
|RAID1-A |`/dev/sda` |   |  |
|   |`/dev/sda1` |`/boot` | 1.0 |
|   |`/dev/sda2` | `/` | 150 |
|   |`/dev/sda3` |`/usr/sap` | 150 |
|   |`/dev/sda4` | '/hana/log` | `rest` |

|陣列|分割區|名稱|大小 (GB) |
| --- | --- | --- | --- |
|RAID10-B |`/dev/sdb` |   |  |
|   |`/dev/sdb1` |`/hana/shared` | 1024 |
|   |`/dev/sdb2` |`/hana/data` |`rest` |


## B1.S2.H8401
{: #H8401}
 
| RAID |元件|磁碟機|陣列|大小|
| --- | --- | --- | --- | --- |
| RAID 1 + 緊急備用| 3x 960 GB 5100 |`hdd0, hdd1, hdd2` |RAID1-A | 960 GB |
| RAID 10 + 緊急備用| 5x 3.84 TB 5100 | `hdd3, hdd4, hdd5, hdd6, hdd7` |RAID10-B | 7.68 TB |

|陣列|分割區|名稱|大小 (GB) |
| --- | --- | --- | --- |
|RAID1-A |`/dev/sda` |   |  |
|   |`/dev/sda1` |`/boot` | 1.0 |
|   |`/dev/sda2` | `/` | 150 |
|   |`/dev/sda3` |`/usr/sap` | 150 |
|   |`/dev/sda4` |`/hana/log` |`rest` |

|陣列|分割區|名稱|大小 (GB) |
| --- | --- | --- | --- |
|RAID10-B |`/dev/sdb` |   |  |
|   |`/dev/sdb1` |`/hana/shared` | 1024 |
|   |`/dev/sdb2` | `hana/data` |`rest` |


## B1.S2.H4400
{: #4096_GB_memory}
 
| RAID |元件|磁碟機|陣列|大小|
| --- | --- | --- | --- | --- |
|RAID 1 |3x 800 GB s3710 |`hdd0` |RAID1-A |800 GB |
|RAID 5 |6x 1.2 TB s3710 |`hdd1` |RAID5-B |4100 GB |
|RAID 5 |9x 1.2 TB s3710 |`hdd2` |RAID-5C |8400 GB |
|廣域緊急備用    |1x 800 GB S3710 |`hdd22` |800 GB GHS |800 GB |

|陣列|分割區|名稱|大小 (GB) |
| --- | --- | --- | --- |
|RAID1-A |`/dev/sda` |   |800 |
|   |`/dev/sda1` |`/boot` |0.25 |
|   |`/dev/sda2` |`/hana/log` |512 |
|   |`/dev/sda3` | `/` |`rest` |

|陣列|分割區|名稱|大小 (GB) |
| --- | --- | --- | --- |
|RAID5-B |`/dev/sdb` |   |4100 |
|   |`/dev/sdb1` |`/hana/shared` |`rest` |

|陣列|分割區|名稱|大小 (GB) |
| --- | --- | --- | --- |
|RAID5-C |`/dev/sdc` |   |4100 |
|   |`/dev/sdc1` |`/hana/data` |`rest` |


## B1.S2.H4400
{: #H4400}
 
| RAID |元件|磁碟機|陣列|大小|
| --- | --- | --- | --- | --- |
|RAID 1 |3x 800 GB s3710 |`hdd0` |RAID1-A |800 GB |
|RAID 5 |6x 1.2 TB s3710 |`hdd1` |RAID5-B |4100 GB |
|RAID 5 |9x 1.2 TB s3710 |`hdd2` |RAID-5C |8400 GB |
|廣域緊急備用    |1x 800 GB S3710 |`hdd22` |800 GB GHS |800 GB |

|陣列|分割區|名稱|大小 (GB) |
| --- | --- | --- | --- |
|RAID1-A |`/dev/sda` |   |800 |
|   |`/dev/sda1` |`/boot` |0.25 |
|   |`/dev/sda2` |`/hana/log` |512 |
|   |`/dev/sda3` | `/` |`rest` |

|陣列|分割區|名稱|大小 (GB) |
| --- | --- | --- | --- |
|RAID5-B |`/dev/sdb` |   |4100 |
|   |`/dev/sdb1` |`/hana/shared` |`rest` |

|陣列|分割區|名稱|大小 (GB) |
| --- | --- | --- | --- |
|RAID5-C |`/dev/sdc` |   |4100 |
|   |`/dev/sdc1` |`/hana/data` |`rest` |



## B1.S2.H8801
{: #H8801}
 
| RAID |元件|磁碟機|陣列|大小|
| --- | --- | --- | --- | --- |
| RAID 1 + 緊急備用| 3x 960 GB 5100 |`hdd0, hdd1, hdd2` |RAID1-A | 960 GB |
| RAID 10 + 緊急備用| 7x 3.84 TB 5100 | `hdd3, hdd4, hdd5, hdd6, hdd7, hdd8, hdd9` |RAID10-B | 15.36 TB |

|陣列|分割區|名稱|大小 (GB) |
| --- | --- | --- | --- |
|RAID1-A |`/dev/sda` |   |  |
|   |`/dev/sda1` |`/boot` | 1.0 |
|   |`/dev/sda2` | `/` | 150 |
|   |`/dev/sda3` |`/usr/sap` | 150 |
|   |`/dev/sda4` |`/hana/log` |`rest` |

|陣列|分割區|名稱|大小 (GB) |
| --- | --- | --- | --- |
|RAID10-B |`/dev/sdb` |   |  |
|   |`/dev/sdb1` |`/hana/shared` | 1024 |
|   |`/dev/sdb2` |`/hana/data` |`rest` |


## B1.S2.H8800
{: #8192_GB_memory}
 
| RAID |元件|磁碟機|陣列|大小|
| --- | --- | --- | --- | --- |
|RAID 1 |2x 800 GB s3710 |+1 緊急備用 |RAID1-A |800 GB |
|RAID 5 | 8x 1.2 TB S3710 |  |RAID5-B |8400 GB |
|RAID 5 |18x 1.2 TB S3710 |+1 緊急備用 |RAID5-C |20400 GB |

|陣列|分割區|名稱|大小 (GB) |
| --- | --- | --- | --- |
|RAID1-A |`/dev/sda` |   |800 |
|   |`/dev/sda1` |`/boot` |0.25 |
|   |`/dev/sda2` | `/` |`rest` |

|陣列|分割區|名稱|大小 (GB) |
| --- | --- | --- | --- |
|RAID5-B |`/dev/sdb` |   |4800 |
|   |`/dev/sdb1` |`/hana/log` |`rest` |
|   |`/dev/sdb2` |`/hana/shared` |2200 |

|陣列|分割區|名稱|大小 (GB) |
| --- | --- | --- | --- |
|RAID5-C |`/dev/sdc` |   |7200 |
|   |`/dev/sdc1` |`/hana/data` |`rest` |


## VMware
{: #vmware}

您負責設定伺服器的 VMware 相關配置。您可以從三種大小進行選擇：1 TB (B1.S2.H4100 (VMware))、2 TB (B1.S2.H4200 (VMware)) 及 4 TB (B1.S2.4400 (VMware))。如需在 SAP 認證 {{site.data.keyword.baremetal_short}} 上配置 VMware 的相關資訊，請參閱 [Architecture Guidelines and Best Practices for Deployments of SAP HANA on VMware vSphere Architecture and Technical Considerations Guide](https://www.vmware.com/content/dam/digitalmarketing/vmware/en/pdf/whitepaper/sap_hana_on_vmware_vsphere_best_practices_guide-white-paper.pdf) (PDF)。

## 後續步驟

您現在已準備好開始佈建 {{site.data.keyword.baremetal_short}}。如需後續步驟，請參閱[佈建 SAP HANA 環境](/docs/infrastructure/sap-hana/hana-provision-environment.html)。
