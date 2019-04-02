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


# 5. 确定配置
{: #determine_configuration}

下表列出了可用于 {{site.data.keyword.cloud}} SAP-Certified Infrastructure 产品的 {{site.data.keyword.baremetal_long}} 配置。有关在虚拟环境中运行 SAP HANA 的其他注意事项，请参阅
[VMware ESXi 服务器部署](/docs/infrastructure/sap-hana?topic=sap-hana-considerations#vmware_server)。

## 解码服务器名称
{: #server-names}

以下是关于如何解码 SAP HANA 服务器名称的示例。

|服务器名称|命名约定组成部分| 含义|
| --- | --- | --- |
| BI.S2.H8401 | BI | Bluemix Interface |
| | S2 | 系列 2（处理器生成）|
| | | S1 是 Ivy Bridge/Haswell |
| | | S2 是 Broadwell |
| | | S3 是 Skylake/Kaby Lake |
| | H | HANA 认证的服务器|
| | 8 | 8 套接字服务器|
| |4| 4 TB RAM |
| | 01 | 修订版号（00 是首次发行版，01 是第一次修订，以此类推）|

## BI.S1.H512
{: #512_GB_memory}

| RAID |组件|驱动器|阵列|大小|
| --- | --- | --- | --- | --- |
|RAID 1 |2x 800 GB s3710 |`hdd0, hdd1` |RAID1-A |800 GB |
|RAID 10 |6x 800 GB s3710 |`hdd2, hdd3, hdd4, hdd5, hdd6, hdd7` |RAID10-B |550 GB |
|RAID 10 |6x 800 GB s3710 |`hdd2, hdd3, hdd4, hdd5, hdd6, hdd7` |RAID-10C |1851 GB |
| 全局热备用|1x 800 GB s3710 |`hdd8` |800 GB GHS |800 GB |

|阵列|分区|名称|大小 (GB)|
| --- | --- | --- | --- |
|RAID1-A |`/dev/sda` |   |800 |
|   |`/dev/sda1` |`/boot` | 0.25 |
|   |`/dev/sda2` | `/` |50|
|   |`/dev/sda3` |`/usr/sap` |50|
|   |`/dev/sda4` |`/hana/shared` |512 |

|阵列|分区|名称|大小 (GB)|
| --- | --- | --- | --- |
|RAID10-B |`/dev/sdb` |   |550 |
|   |`/dev/sdb1` |`/hana/log` |`rest` |

|阵列|分区|名称|大小 (GB)|
| --- | --- | --- | --- |
|RAID10-C |`/dev/sdc` |   |1851 |
|   |`/dev/sdc1` |`/hana/data` |`rest` |


## BI.S1.H1000
{: #1024_GB_memory}

| RAID |组件|驱动器|阵列|大小|
| --- | --- | --- | --- | --- |
|RAID 1 |2x 800 GB s3710 |`hdd0, hdd1` |RAID1-A |800 GB |
|RAID 10 |6x 800 GB s3710 |`hdd2, hdd3, hdd4, hdd5, hdd6, hdd7` |RAID10-B |2400 GB |
|RAID 10 |8x 800 GB s3710 |`hdd8, hdd9, hdd10, hdd11, hdd12, hdd13, hdd14, hdd15` |RAID-10C |3200 GB |
| 全局热备用|1x 800 GB s3710 |`hdd16` |800 GB GHS |800 GB |

|阵列|分区|名称|大小 (GB)|
| --- | --- | --- | --- |
|RAID1-A |`/dev/sda` |   |800 |
|   |`/dev/sda1` |`/boot` | 0.25 |
|   |`/dev/sda2` | `/` |50|

|阵列|分区|名称|大小 (GB)|
| --- | --- | --- | --- |
|RAID10-B |`/dev/sdb` |   |2400 |
|   |`/dev/sdb1` |`/hana/shared` |1104 |
|   |  |`/hana/log` |`rest` |

|阵列|分区|名称|大小 (GB)|
| --- | --- | --- | --- |
|RAID10-C |`/dev/sdc` |   |3200 |
|   |`/dev/sdc1` |`/hana/data` |`rest` |


## BI.S2.H4101
{: #H4101}

| RAID |组件|驱动器|阵列|大小|
| --- | --- | --- | --- | --- |
| RAID 1 + 热备用 | 3x 960 GB 5100 |`hdd0, hdd1, hdd2` |RAID1-A | 960 GB |
| RAID 1 + 热备用 | 3x 3.84 TB 5100 | `hdd3, hdd4, hdd5` | RAID1-B | 3.84 TB |

|阵列|分区|名称|大小 (GB)|
| --- | --- | --- | --- |
|RAID1-A |`/dev/sda` |   |  |
|   |`/dev/sda1` |`/boot` | 1.0 |
|   |`/dev/sda2` | `/` | 150 |
|   |`/dev/sda3` |`/usr/sap` |
|   |`/dev/sda4` |`/hana/log` |

|阵列|分区|名称|大小 (GB)|
| --- | --- | --- | --- |
| RAID1-B |`/dev/sdb` |   |  |
|   |`/dev/sdb1` |`/hana/shared` | 1024 |
|   |`/dev/sdb2` |`/hana/data` |`rest` |

## BI.S2.H4100
{: #H4100}

| RAID |组件|驱动器|阵列|大小|
| --- | --- | --- | --- | --- |
|RAID 1 |2x 800 GB s3710 | `hdd0, hdd1, hdd2` |RAID1-A |800 GB |
|RAID 5 |3x 800 GB s3710 | `hdd3, hdd4, hdd5, hdd6` |RAID5-B | 1600 GB |
|RAID 5 | 4x 800 GB s3710 | `hdd7, hdd8, hdd9, hdd10, hdd11` |RAID5-C |2400 GB |
| 专用热备用| 1X 800 GB s3710 | `hdd2, hdd6, hdd11` | 800 GB DHS |800 GB |

|阵列|分区|名称|大小 (GB)|
| --- | --- | --- | --- |
|RAID1-A |`/dev/sda` |   |800 |
|   |`/dev/sda1` |`/boot` | 0.25 |
|   |`/dev/sda2` |`/hana/log` |512 |
|   |`/dev/sda3` | `/` |`rest` |

|阵列|分区|名称|大小 (GB)|
| --- | --- | --- | --- |
|RAID5-B |`/dev/sdb` |   |4100 |
|   |`/dev/sdb1` |`/hana/shared` |`rest` |

|阵列|分区|名称|大小 (GB)|
| --- | --- | --- | --- |
|RAID5-C |`/dev/sdc` |   |4100 |
|   |`/dev/sdc1` |`/hana/data` |`rest` |


## BI.S2.H4201
{: #4201}

| RAID |组件|驱动器|阵列|大小|
| --- | --- | --- | --- | --- |
| RAID 1 + 热备用 | 3x 960 GB 5100 |`hdd0, hdd1, hdd2` |RAID1-A | 960 GB |
| RAID 10 + 热备用 | 7x 1.92 TB 5100 | `hdd3, hdd4, hdd5, hdd6, hdd7, hdd8, hdd9` |RAID10-B | 5.76 TB |

|阵列|分区|名称|大小 (GB)|
| --- | --- | --- | --- |
|RAID1-A |`/dev/sda` |   |  |
|   |`/dev/sda1` |`/boot` | 1.0 |
|   |`/dev/sda2` | `/` | 150 |
|   |`/dev/sda3` |`/usr/sap` | 150 |
|   |`/dev/sda4` |`/hana/log` |`rest` |

|阵列|分区|名称|大小 (GB)|
| --- | --- | --- | --- |
|RAID10-B |`/dev/sdb` |   |  |
|   |`/dev/sdb1` |`/hana/shared` | 1024 |
|   |`/dev/sdb2` |`/hana/data` |`rest` |


## BI.S2.H4200
{: #H4200}

| RAID |组件|驱动器|阵列|大小|
| --- | --- | --- | --- | --- |
|RAID 1 |2x 800 GB s3710 | `hdd0, hdd1, hdd2` |RAID1-A |800 GB |
|RAID 5 | 3x 1.2 TB s3710 | `hdd3, hdd4, hdd5, hdd6` |RAID5-B | 2.4 TB |
|RAID 5 | 5x 1.2 TB s3710 | `hdd7, hdd8, hdd9, hdd10, hdd11` |RAID5-C | 4.8 TB |
| 专用热备用| 1X 800 GB s3710 | `hdd2, hdd6, hdd11` | 800 GB DHS |800 GB |

|阵列|分区|名称|大小 (GB)|
| --- | --- | --- | --- |
|RAID1-A |`/dev/sda` |   |800 |
|   |`/dev/sda1` |`/boot` | 0.25 |
|   |`/dev/sda2` |`/hana/log` |512 |
|   |`/dev/sda3` | `/` |`rest` |

|阵列|分区|名称|大小 (GB)|
| --- | --- | --- | --- |
|RAID5-B |`/dev/sdb` |   |4100 |
|   |`/dev/sdb1` |`/hana/shared` |`rest` |

|阵列|分区|名称|大小 (GB)|
| --- | --- | --- | --- |
|RAID5-C |`/dev/sdc` |   |4100 |
|   |`/dev/sdc1` |`/hana/data` |`rest` |


## BI.S1.H2000
{: #2048_GB_memory}

| RAID |组件|驱动器|阵列|大小|
| --- | --- | --- | --- | --- |
|RAID 1 |2x 800 GB s3710 |`hdd0, hdd1` |RAID1-A |800 GB |
|RAID 10 |8x 800 GB s3710 |`hdd2, hdd3, hdd4, hdd5, hdd6, hdd7, hdd8, hdd9` |RAID10-B |4800 GB |
|RAID 10 |106x 1.2 TB S3710 |`hdd10, hdd11, hdd12, hdd15, hdd16, hdd17, hdd18, hdd19, hdd20, hdd21` |RAID-10C |7200 GB |
| 全局热备用|1x 800 GB S3710 |`hdd22` |800 GB GHS |800 GB |
| RAID 10-C 热备用|1x 1.2 TB S3710 |`hdd23` |1.2 TB 热备用|1.2 TB |

|阵列|分区|名称|大小 (GB)|
| --- | --- | --- | --- |
|RAID1-A |`/dev/sda` |   |800 |
|   |`/dev/sda1` |`/boot` | 0.25 |
|   |`/dev/sda2` | `/` |`rest` |

|阵列|分区|名称|大小 (GB)|
| --- | --- | --- | --- |
|RAID10-B |`/dev/sdb` |   |4800 |
|   |`/dev/sdb1` |`/hana/log` |`rest` |
|   |`/dev/sdb2` |`/hana/shared` |2200 |

|阵列|分区|名称|大小 (GB)|
| --- | --- | --- | --- |
|RAID10-C |`/dev/sdc` |   |7200 |
|   |`/dev/sdc1` |`/hana/data` |`rest` |


## BI.S2.H4401
{: #H4401}

| RAID |组件|驱动器|阵列|大小|
| --- | --- | --- | --- | --- |
| RAID 1 + 热备用 | 3x 960 GB 5100 |`hdd0, hdd1, hdd2` |RAID1-A | 960 GB |
| RAID 10 + 热备用 | 5x 3.84 TB 5100 | `hdd3, hdd4, hdd5, hdd6, hdd7` |RAID10-B | 7.68 TB |

|阵列|分区|名称|大小 (GB)|
| --- | --- | --- | --- |
|RAID1-A |`/dev/sda` |   |  |
|   |`/dev/sda1` |`/boot` | 1.0 |
|   |`/dev/sda2` | `/` | 150 |
|   |`/dev/sda3` |`/usr/sap` | 150 |
|   |`/dev/sda4` |`/hana/log` |`rest` |

|阵列|分区|名称|大小 (GB)|
| --- | --- | --- | --- |
|RAID10-B |`/dev/sdb` |   |  |
|   |`/dev/sdb1` |`/hana/shared` | 1024 |
|   |`/dev/sdb2` |`/hana/data` |`rest` |


## BI.S2.H8401
{: #H8401}

| RAID |组件|驱动器|阵列|大小|
| --- | --- | --- | --- | --- |
| RAID 1 + 热备用 | 3x 960 GB 5100 |`hdd0, hdd1, hdd2` |RAID1-A | 960 GB |
| RAID 10 + 热备用 | 5x 3.84 TB 5100 | `hdd3, hdd4, hdd5, hdd6, hdd7` |RAID10-B | 7.68 TB |

|阵列|分区|名称|大小 (GB)|
| --- | --- | --- | --- |
|RAID1-A |`/dev/sda` |   |  |
|   |`/dev/sda1` |`/boot` | 1.0 |
|   |`/dev/sda2` | `/` | 150 |
|   |`/dev/sda3` |`/usr/sap` | 150 |
|   |`/dev/sda4` |`/hana/log` |`rest` |

|阵列|分区|名称|大小 (GB)|
| --- | --- | --- | --- |
|RAID10-B |`/dev/sdb` |   |  |
|   |`/dev/sdb1` |`/hana/shared` | 1024 |
|   |`/dev/sdb2` | `hana/data` |`rest` |


## BI.S2.H4400
{: #4096_GB_memory}

| RAID |组件|驱动器|阵列|大小|
| --- | --- | --- | --- | --- |
|RAID 1 |3x 800 GB s3710 |`hdd0` |RAID1-A |800 GB |
|RAID 5 |6x 1.2 TB s3710 |`hdd1` |RAID5-B |4100 GB |
|RAID 5 |9x 1.2 TB s3710 |`hdd2` |RAID-5C |8400 GB |
| 全局热备用|1x 800 GB S3710 |`hdd22` |800 GB GHS |800 GB |

|阵列|分区|名称|大小 (GB)|
| --- | --- | --- | --- |
|RAID1-A |`/dev/sda` |   |800 |
|   |`/dev/sda1` |`/boot` | 0.25 |
|   |`/dev/sda2` |`/hana/log` |512 |
|   |`/dev/sda3` | `/` |`rest` |

|阵列|分区|名称|大小 (GB)|
| --- | --- | --- | --- |
|RAID5-B |`/dev/sdb` |   |4100 |
|   |`/dev/sdb1` |`/hana/shared` |`rest` |

|阵列|分区|名称|大小 (GB)|
| --- | --- | --- | --- |
|RAID5-C |`/dev/sdc` |   |4100 |
|   |`/dev/sdc1` |`/hana/data` |`rest` |


## BI.S2.H4400
{: #H4400}

| RAID |组件|驱动器|阵列|大小|
| --- | --- | --- | --- | --- |
|RAID 1 |3x 800 GB s3710 |`hdd0` |RAID1-A |800 GB |
|RAID 5 |6x 1.2 TB s3710 |`hdd1` |RAID5-B |4100 GB |
|RAID 5 |9x 1.2 TB s3710 |`hdd2` |RAID-5C |8400 GB |
| 全局热备用|1x 800 GB S3710 |`hdd22` |800 GB GHS |800 GB |

|阵列|分区|名称|大小 (GB)|
| --- | --- | --- | --- |
|RAID1-A |`/dev/sda` |   |800 |
|   |`/dev/sda1` |`/boot` | 0.25 |
|   |`/dev/sda2` |`/hana/log` |512 |
|   |`/dev/sda3` | `/` |`rest` |

|阵列|分区|名称|大小 (GB)|
| --- | --- | --- | --- |
|RAID5-B |`/dev/sdb` |   |4100 |
|   |`/dev/sdb1` |`/hana/shared` |`rest` |

|阵列|分区|名称|大小 (GB)|
| --- | --- | --- | --- |
|RAID5-C |`/dev/sdc` |   |4100 |
|   |`/dev/sdc1` |`/hana/data` |`rest` |



## BI.S2.H8801
{: #H8801}

| RAID |组件|驱动器|阵列|大小|
| --- | --- | --- | --- | --- |
| RAID 1 + 热备用 | 3x 960 GB 5100 |`hdd0, hdd1, hdd2` |RAID1-A | 960 GB |
| RAID 10 + 热备用 | 7x 3.84 TB 5100 | `hdd3, hdd4, hdd5, hdd6, hdd7, hdd8, hdd9` |RAID10-B | 15.36 TB |

|阵列|分区|名称|大小 (GB)|
| --- | --- | --- | --- |
|RAID1-A |`/dev/sda` |   |  |
|   |`/dev/sda1` |`/boot` | 1.0 |
|   |`/dev/sda2` | `/` | 150 |
|   |`/dev/sda3` |`/usr/sap` | 150 |
|   |`/dev/sda4` |`/hana/log` |`rest` |

|阵列|分区|名称|大小 (GB)|
| --- | --- | --- | --- |
|RAID10-B |`/dev/sdb` |   |  |
|   |`/dev/sdb1` |`/hana/shared` | 1024 |
|   |`/dev/sdb2` |`/hana/data` |`rest` |


## BI.S2.H8800
{: #8192_GB_memory}

| RAID |组件|驱动器|阵列|大小|
| --- | --- | --- | --- | --- |
|RAID 1 |2x 800 GB s3710 |+1 热备用 |RAID1-A |800 GB |
|RAID 5 | 8x 1.2 TB S3710 |  |RAID5-B |8400 GB |
|RAID 5 |18x 1.2 TB S3710 |+1 热备用 |RAID5-C |20400 GB |

|阵列|分区|名称|大小 (GB)|
| --- | --- | --- | --- |
|RAID1-A |`/dev/sda` |   |800 |
|   |`/dev/sda1` |`/boot` | 0.25 |
|   |`/dev/sda2` | `/` |`rest` |

|阵列|分区|名称|大小 (GB)|
| --- | --- | --- | --- |
|RAID5-B |`/dev/sdb` |   |4800 |
|   |`/dev/sdb1` |`/hana/log` |`rest` |
|   |`/dev/sdb2` |`/hana/shared` |2200 |

|阵列|分区|名称|大小 (GB)|
| --- | --- | --- | --- |
|RAID5-C |`/dev/sdc` |   |7200 |
|   |`/dev/sdc1` |`/hana/data` |`rest` |


## BI.S3.H2192
{: #2192_GB_memory}

| RAID |组件|驱动器|阵列|大小|
| --- | --- | --- | --- | --- |
|RAID 1 | 2x 960 GB 5100 |`hdd0, hdd1` |RAID1-A | 960 GB |
|RAID 1 | 2x 960 GB 5100 | `hdd2, hdd3` | RAID1-B | 960 GB |
| 全局热备用| 1x 960 GB 5100 | `hdd4` |  |  |

|阵列|分区|名称|大小 (GB)|
| --- | --- | --- | --- |
|RAID1-A |`/dev/sda` |   |  |
|   |`/dev/sda1` |`/boot` |50|
|   |`/dev/sda2` | `/` | 150 |
|   |`/dev/sda3` |`/usr/sap` | 150 |
|   |`/dev/sda4` |`/hana/log` |  |

|阵列|分区|名称|大小 (GB)|
| --- | --- | --- | --- |
| RAID1-B |`/dev/sdb` |   |  |
|   |`/dev/sdb1` |`/hana/shared` | 250 |
|   | `/dev\sdb2` |`/hana/data` |`rest` |

## BI.S3.H2384
{: #2384_GB_memory}

| RAID |组件|驱动器|阵列|大小|
| --- | --- | --- | --- | --- |
|RAID 1 | 2x 960 GB 5100 |`hdd0, hdd1` |RAID1-A | 960 GB |
|RAID 10 | 4x 960 GB 5100 | `hdd2, hdd3, hdd4, hdd5` | RAID1-B | 1920 GB |
| 全局热备用| 1x 960 GB 5100 | `hdd` |  |  |

|阵列|分区|名称|大小 (GB)|
| --- | --- | --- | --- |
|RAID1-A |`/dev/sda` |   |  |
|   |`/dev/sda1` |`/boot` |50|
|   |`/dev/sda2` | `/` | 150 |
|   |`/dev/sda3` |`/usr/sap` | 150 |
|   |`/dev/sda4` |`/hana/log` |  |

|阵列|分区|名称|大小 (GB)|
| --- | --- | --- | --- |
| RAID1-B |`/dev/sdb` |   |  |
|   |`/dev/sdb1` |`/hana/shared` | 500 |
|   | `/dev\sdb2` |`/hana/data` |`rest` |

## VMware
{: #vmware}

您负责设置服务器的 VMware 相关配置。您可以从三个大小中进行选择：1 TB (BI.S2.H4100 (VMware))、2 TB (BI.S2.H4200 (VMware)) 以及 4 TB (BI.S2.4400 (VMware))。有关在 SAP 认证的
{{site.data.keyword.baremetal_short}} 上配置 VMware 的更多信息，请参阅 [Architecture Guidelines and Best Practices for Deployments of SAP HANA on VMware vSphere Architecture and Technical Considerations Guide ![外部链接图标](../icons/launch-glyph.svg "外部链接图标")](https://www.vmware.com/content/dam/digitalmarketing/vmware/en/pdf/whitepaper/sap_hana_on_vmware_vsphere_best_practices_guide-white-paper.pdf){: new_window} (PDF)。

## 后续步骤

现在，您可以开始供应 {{site.data.keyword.baremetal_short}}。请参阅[供应 SAP HANA 环境](/docs/infrastructure/sap-hana?topic=sap-hana-provision_environment#provision_environment)以获取后续步骤。
