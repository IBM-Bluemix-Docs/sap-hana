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


# 5. 구성 판별
{: #determine_configuration}

다음 표에는 {{site.data.keyword.cloud}} 오퍼링에 사용 가능한 SAP HANA 구성이 나열되어 있습니다. 가상화된 환경에서 SAP HANA를 실행하는 경우 추가 정보 고려사항은 [VMware ESXi 서버 배치](/docs/infrastructure/sap-hana/hana-considerations.html#vmware-server)를 참조하십시오.

## 512GB SAP HANA 메모리
{: #512_GB_memory}
 
표 1. SAP HANA 512GB RAM 구성

|RAID 1 | 2x 800GB s3710 |`hdd0, hdd1` | RAID1-A | 800GB |
| --- | --- | --- | --- | --- |
| RAID 10 | 6x 800GB s3710 | `hdd2, hdd3, hdd4, hdd5, hdd6, hdd7` | RAID10-B | 550GB |
| RAID 10 | 6x 800GB s3710 | `hdd2, hdd3, hdd4, hdd5, hdd6, hdd7` | RAID-10C | 1,851GB |
| 글로벌 핫 스페어 | 1x 800GB s3710 | `hdd8` | 800GB GHS | 800GB |

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
|   | `/dev/sdc` |   | 1,851 |
|   | `/dev/sdc1` | `/hana/data` | `rest` |


## 1,024GB(1TB) SAP HANA 메모리
{: #1024_GB_memory}
 
표 2. SAP HANA 1,024GB(1TB) RAM 구성

|RAID 1 | 2x 800GB s3710 |`hdd0, hdd1` | RAID1-A | 800GB |
| --- | --- | --- | --- | --- |
| RAID 10 | 6x 800GB s3710 | `hdd2, hdd3, hdd4, hdd5, hdd6, hdd7` | RAID10-B | 2,400GB |
| RAID 10 | 8x 800GB s3710 | `hdd8, hdd9, hdd10, hdd11, hdd12, hdd13, hdd14, hdd15` | RAID-10C | 3,200GB |
| 글로벌 핫 스페어 | 1x 800GB s3710 | `hdd16` | 800GB GHS | 800GB |

| RAID1-A |   |   |   |
| --- | --- | --- | --- |
|   | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0.25 |
|   | `/dev/sda2` | `/` | 50 |

| RAID10-B |   |   |   |
| --- | --- | --- | --- |
|   | `/dev/sdb` |   | 2,400 |
|   | `/dev/sdb1` | `/hana/shared` | 1,104 |
|   |  | `/hana/log` | `rest` |

| RAID10-C |   |   |   |
| --- | --- | --- | --- |
|   | `/dev/sdc` |   | 3,200 |
|   | `/dev/sdc1` | `/hana/data` | `rest` |


## 2,048GB(2TB) SAP HANA 메모리
{: #2048_GB_memory}
 
표 3. SAP HANA 2,048GB(2TB) RAM 구성

|RAID 1 | 2x 800GB s3710 |`hdd0, hdd1` | RAID1-A | 800GB |
| --- | --- | --- | --- | --- |
| RAID 10 | 8x 800GB s3710 | `hdd2, hdd3, hdd4, hdd5, hdd6, hdd7, hdd8, hdd9` | RAID10-B | 4,800GB |
| RAID 10 | 106x 1.2TB S3710 | `hdd10, hdd11, hdd12, hdd15, hdd16, hdd17, hdd18, hdd19, hdd20, hdd21` | RAID-10C | 7,200GB |
| 글로벌 핫 스페어 | 1x 800GB S3710 | `hdd22` | 800GB GHS | 800GB |
| RAID 10-C 핫 스페어 | 1x 1.2TB S3710 | `hdd23` | 1.2TB 핫 스페어 | 1.2TB |

| RAID1-A |   |   |   |
| --- | --- | --- | --- |
|   | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0.25 |
|   | `/dev/sda2` | `/` | `Rest` |

| RAID10-B |   |   |   |
| --- | --- | --- | --- |
|   | `/dev/sdb` |   | 4,800 |
|   | `/dev/sdb1` | `/hana/log` | `Rest` |
|   | `/dev/sdb2` | `/hana/shared` | 2,200 |

| RAID10-C |   |   |   |
| --- | --- | --- | --- |
|   | `/dev/sdc` |   | 7,200 |
|   | `/dev/sdc1` | `/hana/data` | `Rest` |


## 4,096GB(4TB) SAP HANA 메모리 
{: #4096_GB_memory}
 
표 4. SAP HANA 4,096GB(4TB) RAM 구성 

|RAID 1 | 3x 800GB s3710 |`hdd0` | RAID1-A | 800GB |
| --- | --- | --- | --- | --- |
| RAID 5 | 6x 1.2TB s3710 | `hdd1` | RAID5-B | 4,100GB |
| RAID 5 | 9x 1.2TB s3710 | `hdd2` | RAID-5C | 8,400GB |
|글로벌 핫 스페어 | 1x 800GB S3710 | `hdd22` | 800GB GHS | 800GB |

| RAID1-A |   |   |   |
| --- | --- | --- | --- |
|   | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0.25 |
|   | `/dev/sda2` | `/hana/log` | 512 |
|   | `/dev/sda3` | `/` | `rest` |

| RAID5-B |   |   |   |
| --- | --- | --- | --- |
|   | `/dev/sdb` |   | 4,100 |
|   | `/dev/sdb1` | `/hana/shared` | `rest` |

| RAID5-C |   |   |   |
| --- | --- | --- | --- |
|   | `/dev/sdc` |   | 4,100 |
|   | `/dev/sdc1` | `/hana/data` | `rest` |


## 8,192GB(8TB) SAP HANA 메모리
{: #8192_GB_memory}
 
표 5. SAP HANA 8,192GB(8TB) RAM 구성

|RAID 1 | 2x 800GB s3710 | +1 핫 스페어 | RAID1-A | 800GB |
| --- | --- | --- | --- | --- |
| RAID 5 | 8x 1.2TB S3710 |  | RAID5-B | 8,400GB |
| RAID 5 | 18x 1.2TB S3710 | +1 핫 스페어 | RAID5-C | 20,400GB |

| RAID1-A |   |   |   |
| --- | --- | --- | --- |
|   | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0.25 |
|   | `/dev/sda2` | `/` | `rest` |

| RAID5-B |   |   |   |
| --- | --- | --- | --- |
|   | `/dev/sdb` |   | 4,800 |
|   | `/dev/sdb1` | `/hana/log` | `rest` |
|   | `/dev/sdb2` | `/hana/shared` | 2,200 |

| RAID5-C |   |   |   |
| --- | --- | --- | --- |
|   | `/dev/sdc` |   | 7,200 |
|   | `/dev/sdc1` | `/hana/data` | `rest` |

## 다음 단계

이제 {{site.data.keyword.baremetal_short}}의 프로비저닝을 시작할 준비가 되었습니다. 다음 단계는 [SAP HANA 환경 프로비저닝](/docs/infrastructure/sap-hana/hana-provision-environment.html)을 참조하십시오.
