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


# 5. 構成の選定
{: #determine_configuration}

{{site.data.keyword.cloud}} SAP-Certified Infrastructure オファリングで使用できる {{site.data.keyword.baremetal_long}} 構成を以下の表にまとめます。 仮想化環境で SAP HANA を実行する場合のその他の考慮事項については、[VMware ESXi サーバー・デプロイメント](/docs/infrastructure/sap-hana?topic=sap-hana-considerations#vmware_server)を参照してください。

## サーバー名の復号
{: #server-names}

以下は SAP HANA サーバー名を復号する方法を示す例です。

| サーバー名 | 命名規則コンポーネント | 意味 |
| --- | --- | --- |
| BI.S2.H8401 | BI | Bluemix Interface |
| | S2 | Series 2 (プロセッサー生成) |
| | | S1 は Ivy Bridge/Haswell |
| | | S2 は Broadwell |
| | | S3 は Skylake/Kaby Lake |
| | H | HANA 認証サーバー |
| | 8 | 8 ソケット・サーバー |
| | 4 | 4 TB RAM |
| | 01 | リビジョン番号 (00 はランチ時、01 は第 1 リビジョン、など) |

## BI.S1.H512
{: #512_GB_memory}

| RAID | コンポーネント | ドライブ | アレイ | サイズ |
| --- | --- | --- | --- | --- |
| RAID 1 | 2x 800 GB s3710 |`hdd0、hdd1` | RAID1-A | 800 GB |
| RAID 10 | 6x 800 GB s3710 | `hdd2、hdd3、hdd4、hdd5、hdd6、hdd7` | RAID10-B | 550 GB |
| RAID 10 | 6x 800 GB s3710 | `hdd2、hdd3、hdd4、hdd5、hdd6、hdd7` | RAID-10C | 1851 GB |
| グローバル・ホット・スペア | 1x 800 GB s3710 | `hdd8` | 800 GB GHS | 800 GB |

| アレイ | パーティション | 名前 | サイズ (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0.25 |
|   | `/dev/sda2` | `/` | 50 |
|   | `/dev/sda3` | `/usr/sap` | 50 |
|   | `/dev/sda4` | `/hana/shared` | 512 |

| アレイ | パーティション | 名前 | サイズ (GB) |
| --- | --- | --- | --- |
| RAID10-B | `/dev/sdb` |   | 550 |
|   | `/dev/sdb1` | `/hana/log` | `rest` |

| アレイ | パーティション | 名前 | サイズ (GB) |
| --- | --- | --- | --- |
| RAID10-C | `/dev/sdc` |   | 1851 |
|   | `/dev/sdc1` | `/hana/data` | `rest` |


## BI.S1.H1000
{: #1024_GB_memory}

| RAID | コンポーネント | ドライブ | アレイ | サイズ |
| --- | --- | --- | --- | --- |
| RAID 1 | 2x 800 GB s3710 |`hdd0、hdd1` | RAID1-A | 800 GB |
| RAID 10 | 6x 800 GB s3710 | `hdd2、hdd3、hdd4、hdd5、hdd6、hdd7` | RAID10-B | 2400 GB |
| RAID 10 | 8x 800 GB s3710 | `hdd8、hdd9、hdd10、hdd11、hdd12、hdd13、hdd14、hdd15` | RAID-10C | 3200 GB |
| グローバル・ホット・スペア | 1x 800 GB s3710 | `hdd16` | 800 GB GHS | 800 GB |

| アレイ | パーティション | 名前 | サイズ (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0.25 |
|   | `/dev/sda2` | `/` | 50 |

| アレイ | パーティション | 名前 | サイズ (GB) |
| --- | --- | --- | --- |
| RAID10-B | `/dev/sdb` |   | 2400 |
|   | `/dev/sdb1` | `/hana/shared` | 1104 |
|   |  | `/hana/log` | `rest` |

| アレイ | パーティション | 名前 | サイズ (GB) |
| --- | --- | --- | --- |
| RAID10-C | `/dev/sdc` |   | 3200 |
|   | `/dev/sdc1` | `/hana/data` | `rest` |


## BI.S2.H4101
{: #H4101}

| RAID | コンポーネント | ドライブ | アレイ | サイズ |
| --- | --- | --- | --- | --- |
| RAID 1 + ホット・スペア | 3x 960 GB 5100 |`hdd0、hdd1、hdd2` | RAID1-A | 960 GB |
| RAID 1 + ホット・スペア | 3x 3.84 TB 5100 | `hdd3、hdd4、hdd5` | RAID1-B | 3.84 TB |

| アレイ | パーティション | 名前 | サイズ (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 1.0 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` |
|   | `/dev/sda4` | `/hana/log` |

| アレイ | パーティション | 名前 | サイズ (GB) |
| --- | --- | --- | --- |
| RAID1-B | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 1024 |
|   | `/dev/sdb2` | `/hana/data` | `rest` |

## BI.S2.H4100
{: #H4100}

| RAID | コンポーネント | ドライブ | アレイ | サイズ |
| --- | --- | --- | --- | --- |
| RAID 1 | 2x 800 GB s3710 | `hdd0、hdd1、hdd2` | RAID1-A | 800 GB |
| RAID 5 | 3x 800 GB s3710 | `hdd3、hdd4、hdd5、hdd6` | RAID5-B | 1600 GB |
| RAID 5 | 4x 800 GB s3710 | `hdd7、hdd8、hdd9、hdd10、hdd11` | RAID5-C | 2400 GB |
| 専用ホット・スペア | 1X 800 GB s3710 | `hdd2、hdd6、hdd11` | 800 GB DHS | 800 GB |

| アレイ | パーティション | 名前 | サイズ (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0.25 |
|   | `/dev/sda2` | `/hana/log` | 512 |
|   | `/dev/sda3` | `/` | `rest` |

| アレイ | パーティション | 名前 | サイズ (GB) |
| --- | --- | --- | --- |
| RAID5-B  | `/dev/sdb` |   | 4100 |
|   | `/dev/sdb1` | `/hana/shared` | `rest` |

| アレイ | パーティション | 名前 | サイズ (GB) |
| --- | --- | --- | --- |
| RAID5-C  | `/dev/sdc` |   | 4100 |
|   | `/dev/sdc1` | `/hana/data` | `rest` |


## BI.S2.H4201
{: #4201}

| RAID | コンポーネント | ドライブ | アレイ | サイズ |
| --- | --- | --- | --- | --- |
| RAID 1 + ホット・スペア| 3x 960 GB 5100 |`hdd0、hdd1、hdd2` | RAID1-A | 960 GB |
| RAID 10 + ホット・スペア | 7x 1.92 TB 5100 | `hdd3、hdd4、hdd5、hdd6、hdd7、hdd8、hdd9` | RAID10-B | 5.76 TB |

| アレイ | パーティション | 名前 | サイズ (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 1.0 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` | `rest` |

| アレイ | パーティション | 名前 | サイズ (GB) |
| --- | --- | --- | --- |
| RAID10-B | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 1024 |
|   | `/dev/sdb2` | `/hana/data` | `rest` |


## BI.S2.H4200
{: #H4200}

| RAID | コンポーネント | ドライブ | アレイ | サイズ |
| --- | --- | --- | --- | --- |
| RAID 1 | 2x 800 GB s3710 | `hdd0、hdd1、hdd2` | RAID1-A | 800 GB |
| RAID 5 | 3x 1.2 TB s3710 | `hdd3、hdd4、hdd5、hdd6` | RAID5-B | 2.4 TB |
| RAID 5 | 5x 1.2 TB s3710 | `hdd7、hdd8、hdd9、hdd10、hdd11` | RAID5-C | 4.8 TB |
| 専用ホット・スペア | 1X 800 GB s3710 | `hdd2、hdd6、hdd11` | 800 GB DHS | 800 GB |

| アレイ | パーティション | 名前 | サイズ (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0.25 |
|   | `/dev/sda2` | `/hana/log` | 512 |
|   | `/dev/sda3` | `/` | `rest` |

| アレイ | パーティション | 名前 | サイズ (GB) |
| --- | --- | --- | --- |
| RAID5-B  | `/dev/sdb` |   | 4100 |
|   | `/dev/sdb1` | `/hana/shared` | `rest` |

| アレイ | パーティション | 名前 | サイズ (GB) |
| --- | --- | --- | --- |
| RAID5-C  | `/dev/sdc` |   | 4100 |
|   | `/dev/sdc1` | `/hana/data` | `rest` |


## BI.S1.H2000
{: #2048_GB_memory}

| RAID | コンポーネント | ドライブ | アレイ | サイズ |
| --- | --- | --- | --- | --- |
| RAID 1 | 2x 800 GB s3710 |`hdd0、hdd1` | RAID1-A | 800 GB |
| RAID 10 | 8x 800 GB s3710 | `hdd2、hdd3、hdd4、hdd5、hdd6、hdd7、hdd8、hdd9` | RAID10-B | 4800 GB |
| RAID 10 | 106x 1.2 TB S3710 | `hdd10、hdd11、hdd12、hdd15、hdd16、hdd17、hdd18、hdd19、hdd20、hdd21` | RAID-10C | 7200 GB |
| グローバル・ホット・スペア | 1x 800 GB S3710 | `hdd22` | 800 GB GHS | 800 GB |
| RAID 10-C ホット・スペア | 1x 1.2 TB S3710 | `hdd23` | 1.2 TB ホット・スペア | 1.2 TB |

| アレイ | パーティション | 名前 | サイズ (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0.25 |
|   | `/dev/sda2` | `/` | `rest` |

| アレイ | パーティション | 名前 | サイズ (GB) |
| --- | --- | --- | --- |
| RAID10-B | `/dev/sdb` |   | 4800 |
|   | `/dev/sdb1` | `/hana/log` | `rest` |
|   | `/dev/sdb2` | `/hana/shared` | 2200 |

| アレイ | パーティション | 名前 | サイズ (GB) |
| --- | --- | --- | --- |
| RAID10-C | `/dev/sdc` |   | 7200 |
|   | `/dev/sdc1` | `/hana/data` | `rest` |


## BI.S2.H4401
{: #H4401}

| RAID | コンポーネント | ドライブ | アレイ | サイズ |
| --- | --- | --- | --- | --- |
| RAID 1 + ホット・スペア | 3x 960 GB 5100 |`hdd0、hdd1、hdd2` | RAID1-A | 960 GB |
| RAID 10 + ホット・スペア | 5x 3.84 TB 5100 | `hdd3、hdd4、hdd5、hdd6、hdd7` | RAID10-B | 7.68 TB |

| アレイ | パーティション | 名前 | サイズ (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 1.0 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` | `rest` |

| アレイ | パーティション | 名前 | サイズ (GB) |
| --- | --- | --- | --- |
| RAID10-B  | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 1024 |
|   | `/dev/sdb2` | `/hana/data` | `rest` |


## BI.S2.H8401
{: #H8401}

| RAID | コンポーネント | ドライブ | アレイ | サイズ |
| --- | --- | --- | --- | --- |
| RAID 1 + ホット・スペア| 3x 960 GB 5100 |`hdd0、hdd1、hdd2` | RAID1-A | 960 GB |
| RAID 10 + ホット・スペア | 5x 3.84 TB 5100 | `hdd3、hdd4、hdd5、hdd6、hdd7` | RAID10-B | 7.68 TB |

| アレイ | パーティション | 名前 | サイズ (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 1.0 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` | `rest` |

| アレイ | パーティション | 名前 | サイズ (GB) |
| --- | --- | --- | --- |
| RAID10-B  | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 1024 |
|   | `/dev/sdb2` | `hana/data` | `rest` |


## BI.S2.H4400
{: #4096_GB_memory}

| RAID | コンポーネント | ドライブ | アレイ | サイズ |
| --- | --- | --- | --- | --- |
| RAID 1 | 3x 800 GB s3710 |`hdd0` | RAID1-A | 800 GB |
| RAID 5 | 6x 1.2 TB s3710 | `hdd1` | RAID5-B | 4100 GB |
| RAID 5 | 9x 1.2 TB s3710 | `hdd2` | RAID-5C | 8400 GB |
| グローバル・ホット・スペア | 1x 800 GB S3710 | `hdd22` | 800 GB GHS | 800 GB |

| アレイ | パーティション | 名前 | サイズ (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0.25 |
|   | `/dev/sda2` | `/hana/log` | 512 |
|   | `/dev/sda3` | `/` | `rest` |

| アレイ | パーティション | 名前 | サイズ (GB) |
| --- | --- | --- | --- |
| RAID5-B  | `/dev/sdb` |   | 4100 |
|   | `/dev/sdb1` | `/hana/shared` | `rest` |

| アレイ | パーティション | 名前 | サイズ (GB) |
| --- | --- | --- | --- |
| RAID5-C  | `/dev/sdc` |   | 4100 |
|   | `/dev/sdc1` | `/hana/data` | `rest` |


## BI.S2.H4400
{: #H4400}

| RAID | コンポーネント | ドライブ | アレイ | サイズ |
| --- | --- | --- | --- | --- |
| RAID 1 | 3x 800 GB s3710 |`hdd0` | RAID1-A | 800 GB |
| RAID 5 | 6x 1.2 TB s3710 | `hdd1` | RAID5-B | 4100 GB |
| RAID 5 | 9x 1.2 TB s3710 | `hdd2` | RAID-5C | 8400 GB |
| グローバル・ホット・スペア | 1x 800 GB S3710 | `hdd22` | 800 GB GHS | 800 GB |

| アレイ | パーティション | 名前 | サイズ (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0.25 |
|   | `/dev/sda2` | `/hana/log` | 512 |
|   | `/dev/sda3` | `/` | `rest` |

| アレイ | パーティション | 名前 | サイズ (GB) |
| --- | --- | --- | --- |
| RAID5-B  | `/dev/sdb` |   | 4100 |
|   | `/dev/sdb1` | `/hana/shared` | `rest` |

| アレイ | パーティション | 名前 | サイズ (GB) |
| --- | --- | --- | --- |
| RAID5-C  | `/dev/sdc` |   | 4100 |
|   | `/dev/sdc1` | `/hana/data` | `rest` |



## BI.S2.H8801
{: #H8801}

| RAID | コンポーネント | ドライブ | アレイ | サイズ |
| --- | --- | --- | --- | --- |
| RAID 1 + ホット・スペア | 3x 960 GB 5100 |`hdd0、hdd1、hdd2` | RAID1-A | 960 GB |
| RAID 10 + ホット・スペア | 7x 3.84 TB 5100 | `hdd3、hdd4、hdd5、hdd6、hdd7、hdd8、hdd9` | RAID10-B | 15.36 TB |

| アレイ | パーティション | 名前 | サイズ (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 1.0 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` | `rest` |

| アレイ | パーティション | 名前 | サイズ (GB) |
| --- | --- | --- | --- |
| RAID10-B  | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 1024 |
|   | `/dev/sdb2` | `/hana/data` | `rest` |


## BI.S2.H8800
{: #8192_GB_memory}

| RAID | コンポーネント | ドライブ | アレイ | サイズ |
| --- | --- | --- | --- | --- |
| RAID 1 | 2x 800 GB s3710 | +1 ホット・スペア | RAID1-A | 800 GB |
| RAID 5 | 8x 1.2 TB S3710 |  | RAID5-B | 8400 GB |
| RAID 5 | 18x 1.2 TB S3710 | +1 ホット・スペア | RAID5-C | 20400 GB |

| アレイ | パーティション | 名前 | サイズ (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0.25 |
|   | `/dev/sda2` | `/` | `rest` |

| アレイ | パーティション | 名前 | サイズ (GB) |
| --- | --- | --- | --- |
| RAID5-B | `/dev/sdb` |   | 4800 |
|   | `/dev/sdb1` | `/hana/log` | `rest` |
|   | `/dev/sdb2` | `/hana/shared` | 2200 |

| アレイ | パーティション | 名前 | サイズ (GB) |
| --- | --- | --- | --- |
| RAID5-C | `/dev/sdc` |   | 7200 |
|   | `/dev/sdc1` | `/hana/data` | `rest` |


## BI.S3.H2192
{: #2192_GB_memory}

| RAID | コンポーネント | ドライブ | アレイ | サイズ |
| --- | --- | --- | --- | --- |
| RAID 1 | 2x 960 GB 5100 | `hdd0、hdd1` | RAID1-A | 960 GB |
| RAID 1 | 2x 960 GB 5100 | `hdd2、hdd3` | RAID1-B | 960 GB |
| グローバル・ホット・スペア | 1x 960 GB 5100 | `hdd4` |  |  |

| アレイ | パーティション | 名前 | サイズ (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 50 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` |  |

| アレイ | パーティション | 名前 | サイズ (GB) |
| --- | --- | --- | --- |
| RAID1-B | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 250 |
|   | `/dev\sdb2` | `/hana/data` | `rest` |

## BI.S3.H2384
{: #2384_GB_memory}

| RAID | コンポーネント | ドライブ | アレイ | サイズ |
| --- | --- | --- | --- | --- |
| RAID 1 | 2x 960 GB 5100 |`hdd0、hdd1` | RAID1-A | 960 GB |
| RAID 10 | 4x 960 GB 5100 | `hdd2、hdd3、hdd4、hdd5` | RAID1-B | 1920 GB |
| グローバル・ホット・スペア | 1x 960 GB 5100 | `hdd` |  |  |

| アレイ | パーティション | 名前 | サイズ (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 50 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` |  |

| アレイ | パーティション | 名前 | サイズ (GB) |
| --- | --- | --- | --- |
| RAID1-B | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 500 |
|   | `/dev\sdb2` | `/hana/data` | `rest` |

## VMware
{: #vmware}

ご使用のサーバー用に VMware 関連の構成をセットアップする必要があります。 1 TB (BI.S2.H4100 (VMware))、2 TB (BI.S2.H4200 (VMware))、4 TB (BI.S2.4400 (VMware)) の 3 つのサイズから選択できます。ご使用の SAP 認定 {{site.data.keyword.baremetal_short}} での VMware の構成について詳しくは、[Architecture Guidelines and Best Practices for Deployments of SAP HANA on VMware vSphere Architecture and Technical Considerations Guide ![外部リンク・アイコン](../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.vmware.com/content/dam/digitalmarketing/vmware/en/pdf/whitepaper/sap_hana_on_vmware_vsphere_best_practices_guide-white-paper.pdf){: new_window} (PDF) を参照してください。

## 次のステップ

これで、{{site.data.keyword.baremetal_short}} のプロビジョニングを開始する準備ができました。 [SAP HANA 環境のプロビジョニング](/docs/infrastructure/sap-hana?topic=sap-hana-provision_environment#provision_environment)で次のステップを確認してください。
