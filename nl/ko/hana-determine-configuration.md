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


# 5. 구성 판별
{: #determine_configuration}

다음 표에는 {{site.data.keyword.cloud}} SAP 인증 인프라 오퍼링에서 사용 가능한 {{site.data.keyword.baremetal_long}} 구성이 나열되어 있습니다. 가상화된 환경에서 SAP HANA를 실행하는 경우 추가 고려사항은 [VMware ESXi 서버 배치](/docs/infrastructure/sap-hana/hana-considerations.html#vmware-server)를 참조하십시오.

## B1.S1.H512
{: #512_GB_memory}
 
| RAID | 컴포넌트 | 드라이브 | 어레이 |크기 |
| --- | --- | --- | --- | --- |
|RAID 1 |2x 800GB s3710 |`hdd0, hdd1` |RAID1-A |800GB |
|RAID 10 |6x 800GB s3710 |`hdd2, hdd3, hdd4, hdd5, hdd6, hdd7` |RAID10-B |550GB |
|RAID 10 |6x 800GB s3710 |`hdd2, hdd3, hdd4, hdd5, hdd6, hdd7` |RAID-10C |1,851GB |
|글로벌 핫 스페어 |1x 800GB s3710 |`hdd8` |800GB GHS |800GB |

| 어레이 | 파티션 |이름 | 크기(GB) |
| --- | --- | --- | --- |
|RAID1-A |`/dev/sda` |   |800 |
|   |`/dev/sda1` |`/boot` |0.25 |
|   |`/dev/sda2` | `/` |50 |
|   |`/dev/sda3` |`/usr/sap` |50 |
|   |`/dev/sda4` |`/hana/shared` |512 |

| 어레이 | 파티션 |이름 | 크기(GB) |
| --- | --- | --- | --- |
|RAID10-B |`/dev/sdb` |   |550 |
|   |`/dev/sdb1` |`/hana/log` |`rest` |

| 어레이 | 파티션 |이름 | 크기(GB) |
| --- | --- | --- | --- |
|RAID10-C |`/dev/sdc` |   |1,851 |
|   |`/dev/sdc1` |`/hana/data` |`rest` |


## B1.S1.H1000
{: #1024_GB_memory}

| RAID | 컴포넌트 | 드라이브 | 어레이 |크기 |
| --- | --- | --- | --- | --- |
|RAID 1 |2x 800GB s3710 |`hdd0, hdd1` |RAID1-A |800GB |
|RAID 10 |6x 800GB s3710 |`hdd2, hdd3, hdd4, hdd5, hdd6, hdd7` |RAID10-B |2,400GB |
|RAID 10 |8x 800GB s3710 |`hdd8, hdd9, hdd10, hdd11, hdd12, hdd13, hdd14, hdd15` |RAID-10C |3,200GB |
|글로벌 핫 스페어 |1x 800GB s3710 |`hdd16` |800GB GHS |800GB |

| 어레이 | 파티션 |이름 | 크기(GB) |
| --- | --- | --- | --- |
|RAID1-A |`/dev/sda` |   |800 |
|   |`/dev/sda1` |`/boot` |0.25 |
|   |`/dev/sda2` | `/` |50 |

| 어레이 | 파티션 |이름 | 크기(GB) |
| --- | --- | --- | --- |
|RAID10-B |`/dev/sdb` |   |2,400 |
|   |`/dev/sdb1` |`/hana/shared` |1,104 |
|   |  |`/hana/log` |`rest` |

| 어레이 | 파티션 |이름 | 크기(GB) |
| --- | --- | --- | --- |
|RAID10-C |`/dev/sdc` |   |3,200 |
|   |`/dev/sdc1` |`/hana/data` |`rest` |


## B1.S2.H4101
{: #H4101}

| RAID | 컴포넌트 | 드라이브 | 어레이 |크기 |
| --- | --- | --- | --- | --- |
| RAID 1 + 핫 스페어 | 3x 960GB 5100 |`hdd0, hdd1, hdd2` |RAID1-A | 960GB |
| RAID 1 + 핫 스페어 | 3x 3.84TB 5100 | `hdd3, hdd4, hdd5` | RAID1-B | 3.84TB |

| 어레이 | 파티션 |이름 | 크기(GB) |
| --- | --- | --- | --- |
|RAID1-A |`/dev/sda` |   |  |
|   |`/dev/sda1` |`/boot` | 1.0 |
|   |`/dev/sda2` | `/` | 150 |
|   |`/dev/sda3` |`/usr/sap` |
|   |`/dev/sda4` |`/hana/log` |

| 어레이 | 파티션 |이름 | 크기(GB) |
| --- | --- | --- | --- |
| RAID1-B |`/dev/sdb` |   |  |
|   |`/dev/sdb1` |`/hana/shared` | 1024 |
|   |`/dev/sdb2` |`/hana/data` |`rest` |

## B1.S2.H4100
{: #H4100}

| RAID | 컴포넌트 | 드라이브 | 어레이 |크기 |
| --- | --- | --- | --- | --- |
|RAID 1 |2x 800GB s3710 | `hdd0, hdd1, hdd2` |RAID1-A |800GB |
|RAID 5 |3x 800GB s3710 | `hdd3, hdd4, hdd5, hdd6` |RAID5-B | 1600GB |
|RAID 5 | 4x 800GB s3710 | `hdd7, hdd8, hdd9, hdd10, hdd11` |RAID5-C |2,400GB |
| 전용 핫 스페어 | 1X 800GB s3710 | `hdd2, hdd6, hdd11` | 800GB DHS |800GB |

| 어레이 | 파티션 |이름 | 크기(GB) |
| --- | --- | --- | --- |
|RAID1-A |`/dev/sda` |   |800 |
|   |`/dev/sda1` |`/boot` |0.25 |
|   |`/dev/sda2` |`/hana/log` |512 |
|   |`/dev/sda3` | `/` |`rest` |

| 어레이 | 파티션 |이름 | 크기(GB) |
| --- | --- | --- | --- |
|RAID5-B  |`/dev/sdb` |   |4,100 |
|   |`/dev/sdb1` |`/hana/shared` |`rest` |

| 어레이 | 파티션 |이름 | 크기(GB) |
| --- | --- | --- | --- |
|RAID5-C  |`/dev/sdc` |   |4,100 |
|   |`/dev/sdc1` |`/hana/data` |`rest` |


## B1.S2.H4201
{: #4201}

| RAID | 컴포넌트 | 드라이브 | 어레이 |크기 |
| --- | --- | --- | --- | --- |
| RAID 1 + 핫 스페어 | 3x 960GB 5100 |`hdd0, hdd1, hdd2` |RAID1-A | 960GB |
| RAID 10 + 핫 스페어 | 7x 1.92TB 5100 | `hdd3, hdd4, hdd5, hdd6, hdd7, hdd8, hdd9` |RAID10-B | 5.76TB |

| 어레이 | 파티션 |이름 | 크기(GB) |
| --- | --- | --- | --- |
|RAID1-A |`/dev/sda` |   |  |
|   |`/dev/sda1` |`/boot` | 1.0 |
|   |`/dev/sda2` | `/` | 150 |
|   |`/dev/sda3` |`/usr/sap` | 150 |
|   |`/dev/sda4` |`/hana/log` |`rest` |

| 어레이 | 파티션 |이름 | 크기(GB) |
| --- | --- | --- | --- |
|RAID10-B |`/dev/sdb` |   |  |
|   |`/dev/sdb1` |`/hana/shared` | 1024 |
|   |`/dev/sdb2` |`/hana/data` |`rest` |


## B1.S2.H4200
{: #H4200}

| RAID | 컴포넌트 | 드라이브 | 어레이 |크기 |
| --- | --- | --- | --- | --- |
|RAID 1 |2x 800GB s3710 | `hdd0, hdd1, hdd2` |RAID1-A |800GB |
|RAID 5 | 3x 1.2TB s3710 | `hdd3, hdd4, hdd5, hdd6` |RAID5-B | 2.4TB |
|RAID 5 | 5x 1.2TB s3710 | `hdd7, hdd8, hdd9, hdd10, hdd11` |RAID5-C | 4.8TB |
| 전용 핫 스페어 | 1X 800GB s3710 | `hdd2, hdd6, hdd11` | 800GB DHS |800GB |

| 어레이 | 파티션 |이름 | 크기(GB) |
| --- | --- | --- | --- |
|RAID1-A |`/dev/sda` |   |800 |
|   |`/dev/sda1` |`/boot` |0.25 |
|   |`/dev/sda2` |`/hana/log` |512 |
|   |`/dev/sda3` | `/` |`rest` |

| 어레이 | 파티션 |이름 | 크기(GB) |
| --- | --- | --- | --- |
|RAID5-B  |`/dev/sdb` |   |4,100 |
|   |`/dev/sdb1` |`/hana/shared` |`rest` |

| 어레이 | 파티션 |이름 | 크기(GB) |
| --- | --- | --- | --- |
|RAID5-C  |`/dev/sdc` |   |4,100 |
|   |`/dev/sdc1` |`/hana/data` |`rest` |


## B1.S1.H2000
{: #2048_GB_memory}
 
| RAID | 컴포넌트 | 드라이브 | 어레이 |크기 |
| --- | --- | --- | --- | --- |
|RAID 1 |2x 800GB s3710 |`hdd0, hdd1` |RAID1-A |800GB |
|RAID 10 |8x 800GB s3710 |`hdd2, hdd3, hdd4, hdd5, hdd6, hdd7, hdd8, hdd9` |RAID10-B |4,800GB |
|RAID 10 |106x 1.2TB S3710 |`hdd10, hdd11, hdd12, hdd15, hdd16, hdd17, hdd18, hdd19, hdd20, hdd21` |RAID-10C |7,200GB |
|글로벌 핫 스페어 |1x 800GB S3710 |`hdd22` |800GB GHS |800GB |
|RAID 10-C 핫 스페어 |1x 1.2TB S3710 |`hdd23` |1.2TB 핫 스페어 |1.2TB |

| 어레이 | 파티션 |이름 | 크기(GB) |
| --- | --- | --- | --- |
|RAID1-A |`/dev/sda` |   |800 |
|   |`/dev/sda1` |`/boot` |0.25 |
|   |`/dev/sda2` | `/` |`Rest` |

| 어레이 | 파티션 |이름 | 크기(GB) |
| --- | --- | --- | --- |
|RAID10-B |`/dev/sdb` |   |4,800 |
|   |`/dev/sdb1` |`/hana/log` |`Rest` |
|   |`/dev/sdb2` |`/hana/shared` |2,200 |

| 어레이 | 파티션 |이름 | 크기(GB) |
| --- | --- | --- | --- |
|RAID10-C |`/dev/sdc` |   |7,200 |
|   |`/dev/sdc1` |`/hana/data` |`Rest` |


## B1.S2.H4401
{: #H4401}
 
| RAID | 컴포넌트 | 드라이브 | 어레이 |크기 |
| --- | --- | --- | --- | --- |
| RAID 1 + 핫 스페어 | 3x 960GB 5100 |`hdd0, hdd1, hdd2` |RAID1-A | 960GB |
| RAID 10 + 핫 스페어 | 5x 3.84TB 5100 | `hdd3, hdd4, hdd5, hdd6, hdd7` |RAID10-B | 7.68TB |

| 어레이 | 파티션 |이름 | 크기(GB) |
| --- | --- | --- | --- |
|RAID1-A |`/dev/sda` |   |  |
|   |`/dev/sda1` |`/boot` | 1.0 |
|   |`/dev/sda2` | `/` | 150 |
|   |`/dev/sda3` |`/usr/sap` | 150 |
|   |`/dev/sda4` | '/hana/log` | `rest` |

| 어레이 | 파티션 |이름 | 크기(GB) |
| --- | --- | --- | --- |
|RAID10-B  |`/dev/sdb` |   |  |
|   |`/dev/sdb1` |`/hana/shared` | 1024 |
|   |`/dev/sdb2` |`/hana/data` |`rest` |


## B1.S2.H8401
{: #H8401}
 
| RAID | 컴포넌트 | 드라이브 | 어레이 |크기 |
| --- | --- | --- | --- | --- |
| RAID 1 + 핫 스페어 | 3x 960GB 5100 |`hdd0, hdd1, hdd2` |RAID1-A | 960GB |
| RAID 10 + 핫 스페어 | 5x 3.84TB 5100 | `hdd3, hdd4, hdd5, hdd6, hdd7` |RAID10-B | 7.68TB |

| 어레이 | 파티션 |이름 | 크기(GB) |
| --- | --- | --- | --- |
|RAID1-A |`/dev/sda` |   |  |
|   |`/dev/sda1` |`/boot` | 1.0 |
|   |`/dev/sda2` | `/` | 150 |
|   |`/dev/sda3` |`/usr/sap` | 150 |
|   |`/dev/sda4` |`/hana/log` |`rest` |

| 어레이 | 파티션 |이름 | 크기(GB) |
| --- | --- | --- | --- |
|RAID10-B  |`/dev/sdb` |   |  |
|   |`/dev/sdb1` |`/hana/shared` | 1024 |
|   |`/dev/sdb2` | `hana/data` |`rest` |


## B1.S2.H4400
{: #4096_GB_memory}
 
| RAID | 컴포넌트 | 드라이브 | 어레이 |크기 |
| --- | --- | --- | --- | --- |
|RAID 1 |3x 800GB s3710 |`hdd0` |RAID1-A |800GB |
|RAID 5 |6x 1.2TB s3710 |`hdd1` |RAID5-B |4,100GB |
|RAID 5 |9x 1.2TB s3710 |`hdd2` |RAID-5C |8,400GB |
|글로벌 핫 스페어 |1x 800GB S3710 |`hdd22` |800GB GHS |800GB |

| 어레이 | 파티션 |이름 | 크기(GB) |
| --- | --- | --- | --- |
|RAID1-A |`/dev/sda` |   |800 |
|   |`/dev/sda1` |`/boot` |0.25 |
|   |`/dev/sda2` |`/hana/log` |512 |
|   |`/dev/sda3` | `/` |`rest` |

| 어레이 | 파티션 |이름 | 크기(GB) |
| --- | --- | --- | --- |
|RAID5-B  |`/dev/sdb` |   |4,100 |
|   |`/dev/sdb1` |`/hana/shared` |`rest` |

| 어레이 | 파티션 |이름 | 크기(GB) |
| --- | --- | --- | --- |
|RAID5-C  |`/dev/sdc` |   |4,100 |
|   |`/dev/sdc1` |`/hana/data` |`rest` |


## B1.S2.H4400
{: #H4400}
 
| RAID | 컴포넌트 | 드라이브 | 어레이 |크기 |
| --- | --- | --- | --- | --- |
|RAID 1 |3x 800GB s3710 |`hdd0` |RAID1-A |800GB |
|RAID 5 |6x 1.2TB s3710 |`hdd1` |RAID5-B |4,100GB |
|RAID 5 |9x 1.2TB s3710 |`hdd2` |RAID-5C |8,400GB |
|글로벌 핫 스페어 |1x 800GB S3710 |`hdd22` |800GB GHS |800GB |

| 어레이 | 파티션 |이름 | 크기(GB) |
| --- | --- | --- | --- |
|RAID1-A |`/dev/sda` |   |800 |
|   |`/dev/sda1` |`/boot` |0.25 |
|   |`/dev/sda2` |`/hana/log` |512 |
|   |`/dev/sda3` | `/` |`rest` |

| 어레이 | 파티션 |이름 | 크기(GB) |
| --- | --- | --- | --- |
|RAID5-B  |`/dev/sdb` |   |4,100 |
|   |`/dev/sdb1` |`/hana/shared` |`rest` |

| 어레이 | 파티션 |이름 | 크기(GB) |
| --- | --- | --- | --- |
|RAID5-C  |`/dev/sdc` |   |4,100 |
|   |`/dev/sdc1` |`/hana/data` |`rest` |



## B1.S2.H8801
{: #H8801}
 
| RAID | 컴포넌트 | 드라이브 | 어레이 |크기 |
| --- | --- | --- | --- | --- |
| RAID 1 + 핫 스페어 | 3x 960GB 5100 |`hdd0, hdd1, hdd2` |RAID1-A | 960GB |
| RAID 10 + 핫 스페어 | 7x 3.84TB 5100 | `hdd3, hdd4, hdd5, hdd6, hdd7, hdd8, hdd9` |RAID10-B | 15.36TB |

| 어레이 | 파티션 |이름 | 크기(GB) |
| --- | --- | --- | --- |
|RAID1-A |`/dev/sda` |   |  |
|   |`/dev/sda1` |`/boot` | 1.0 |
|   |`/dev/sda2` | `/` | 150 |
|   |`/dev/sda3` |`/usr/sap` | 150 |
|   |`/dev/sda4` |`/hana/log` |`rest` |

| 어레이 | 파티션 |이름 | 크기(GB) |
| --- | --- | --- | --- |
|RAID10-B  |`/dev/sdb` |   |  |
|   |`/dev/sdb1` |`/hana/shared` | 1024 |
|   |`/dev/sdb2` |`/hana/data` |`rest` |


## B1.S2.H8800
{: #8192_GB_memory}
 
| RAID | 컴포넌트 | 드라이브 | 어레이 |크기 |
| --- | --- | --- | --- | --- |
|RAID 1 |2x 800GB s3710 |+1 핫 스페어 |RAID1-A |800GB |
|RAID 5 | 8x 1.2TB S3710 |  |RAID5-B |8,400GB |
|RAID 5 |18x 1.2TB S3710 |+1 핫 스페어 |RAID5-C |20,400GB |

| 어레이 | 파티션 |이름 | 크기(GB) |
| --- | --- | --- | --- |
|RAID1-A |`/dev/sda` |   |800 |
|   |`/dev/sda1` |`/boot` |0.25 |
|   |`/dev/sda2` | `/` |`rest` |

| 어레이 | 파티션 |이름 | 크기(GB) |
| --- | --- | --- | --- |
|RAID5-B |`/dev/sdb` |   |4,800 |
|   |`/dev/sdb1` |`/hana/log` |`rest` |
|   |`/dev/sdb2` |`/hana/shared` |2,200 |

| 어레이 | 파티션 |이름 | 크기(GB) |
| --- | --- | --- | --- |
|RAID5-C |`/dev/sdc` |   |7,200 |
|   |`/dev/sdc1` |`/hana/data` |`rest` |


## VMware
{: #vmware}

서버에 대한 VMware 관련 구성을 설정해야 합니다. 세 가지 크기, 1TB(B1.S2.H4100(VMware)), 2TB(B1.S2.H4200(VMware)) 및 4TB(B1.S2.4400(VMware)) 중에서 선택할 수 있습니다. SAP 인증 {{site.data.keyword.baremetal_short}}에서 VMware를 구성하는 데 대한 자세한 정보는 [Architecture Guidelines and Best Practices for Deployments of SAP HANA on VMware vSphere Architecture and Technical Considerations Guide](https://www.vmware.com/content/dam/digitalmarketing/vmware/en/pdf/whitepaper/sap_hana_on_vmware_vsphere_best_practices_guide-white-paper.pdf)(PDF)를 참조하십시오.

## 다음 단계

이제 {{site.data.keyword.baremetal_short}}의 프로비저닝을 시작할 준비가 되었습니다. 다음 단계는 [SAP HANA 환경 프로비저닝](/docs/infrastructure/sap-hana/hana-provision-environment.html)을 참조하십시오.
