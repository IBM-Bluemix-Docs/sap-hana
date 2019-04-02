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


# 5. Determinando sua configuração
{: #determine_configuration}

As tabelas a seguir listam as configurações de {{site.data.keyword.baremetal_long}} disponíveis com a oferta {{site.data.keyword.cloud}} SAP-Certified Infrastructure. Para obter considerações adicionais ao executar o SAP HANA em um ambiente virtualizado, consulte [Implementações do servidor VMware ESXi](/docs/infrastructure/sap-hana?topic=sap-hana-considerations#vmware_server).

## Decifrando os nomes de servidor
{: #server-names}

Aqui está um exemplo de como decifrar os nomes do servidor SAP HANA.

| Nome do servidor | Componente de convenção de nomenclatura | O que significa |
| --- | --- | --- |
| BI.S2.H8401 | BI | Interface do Bluemix |
| | S2 | Série 2 (geração de processador) |
| | | S1 é Ivy Bridge/Haswell |
| | | S2 é Broadwell |
| | | S3 é Skylake/Kaby Lake |
| | u | Servidor certificado por HANA |
| | 8 | Servidor de 8 soquetes |
| | 4 | 4 TB de RAM |
| | 01 | Número de revisão (00 é a ativação, 01 é a primeira revisão e assim por diante) |

## BI.S1.H512
{: #512_GB_memory}

| RAID | Componentes | Unidades | Matriz | Tamanho |
| --- | --- | --- | --- | --- |
| RAID 1 | 2x 800 GB s3710 |`hdd0, hdd1` | RAID1-A | 800 GB |
| RAID 10 | 6x 800 GB s3710 | `hdd2, hdd3, hdd4, hdd5, hdd6, hdd7` | RAID10-B | 550 GB |
| RAID 10 | 6x 800 GB s3710 | `hdd2, hdd3, hdd4, hdd5, hdd6, hdd7` | RAID-10C | 1851 GB |
| Hot spare global | 1x 800 GB s3710 | `hdd8` | 800 GB GHS | 800 GB |

| Matriz | Partição | Nome | Tamanho (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0,25 |
|   | `/dev/sda2` | `/` | 50 |
|   | `/dev/sda3` | `/usr/sap` | 50 |
|   | `/dev/sda4` | `/hana/shared` | 512 |

| Matriz | Partição | Nome | Tamanho (GB) |
| --- | --- | --- | --- |
| RAID10-B | `/dev/sdb` |   | 550 |
|   | `/dev/sdb1` | `/hana/log` | `rest` |

| Matriz | Partição | Nome | Tamanho (GB) |
| --- | --- | --- | --- |
| RAID10-C | `/dev/sdc` |   | 1851 |
|   | `/dev/sdc1` | `/hana/data` | `rest` |


## BI.S1.H1000
{: #1024_GB_memory}

| RAID | Componentes | Unidades | Matriz | Tamanho |
| --- | --- | --- | --- | --- |
| RAID 1 | 2x 800 GB s3710 |`hdd0, hdd1` | RAID1-A | 800 GB |
| RAID 10 | 6x 800 GB s3710 | `hdd2, hdd3, hdd4, hdd5, hdd6, hdd7` | RAID10-B | 2400 GB |
| RAID 10 | 8x 800 GB s3710 | `hdd8, hdd9, hdd10, hdd11, hdd12, hdd13, hdd14, hdd15` | RAID-10C | 3200 GB |
| Hot spare global | 1x 800 GB s3710 | `hdd16` | 800 GB GHS | 800 GB |

| Matriz | Partição | Nome | Tamanho (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0,25 |
|   | `/dev/sda2` | `/` | 50 |

| Matriz | Partição | Nome | Tamanho (GB) |
| --- | --- | --- | --- |
| RAID10-B | `/dev/sdb` |   | 2400 |
|   | `/dev/sdb1` | `/hana/shared` | 1104 |
|   |  | `/hana/log` | `rest` |

| Matriz | Partição | Nome | Tamanho (GB) |
| --- | --- | --- | --- |
| RAID10-C | `/dev/sdc` |   | 3200 |
|   | `/dev/sdc1` | `/hana/data` | `rest` |


## BI.S2.H4101
{: #H4101}

| RAID | Componentes | Unidades | Matriz | Tamanho |
| --- | --- | --- | --- | --- |
| RAID 1 + hot spare | 3x 960 GB 5100 |`hdd0, hdd1, hdd2` | RAID1-A | 960 GB |
| RAID 1 + hot spare | 3x 3,84 TB 5100 | `hdd3, hdd4, hdd5` | RAID1-B | 3,84 TB |

| Matriz | Partição | Nome | Tamanho (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 1,0 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` |
|   | `/dev/sda4` | `/hana/log` |

| Matriz | Partição | Nome | Tamanho (GB) |
| --- | --- | --- | --- |
| RAID1-B | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 1024 |
|   | `/dev/sdb2` | `/hana/data` | `rest` |

## BI.S2.H4100
{: #H4100}

| RAID | Componentes | Unidades | Matriz | Tamanho |
| --- | --- | --- | --- | --- |
| RAID 1 | 2x 800 GB s3710 | `hdd0, hdd1, hdd2` | RAID1-A | 800 GB |
| RAID 5 | 3x 800 GB s3710 | `hdd3, hdd4, hdd5, hdd6` | RAID5-B | 1600 GB |
| RAID 5 | 4x 800 GB s3710 | `hdd7, hdd8, hdd9, hdd10, hdd11` | RAID5-C | 2400 GB |
| Hot spare dedicado | 1X 800 GB s3710 | `hdd2, hdd6, hdd11` | 800 GB DHS | 800 GB |

| Matriz | Partição | Nome | Tamanho (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0,25 |
|   | `/dev/sda2` | `/hana/log` | 512 |
|   | `/dev/sda3` | `/` | `rest` |

| Matriz | Partição | Nome | Tamanho (GB) |
| --- | --- | --- | --- |
| RAID5-B  | `/dev/sdb` |   | 4100 |
|   | `/dev/sdb1` | `/hana/shared` | `rest` |

| Matriz | Partição | Nome | Tamanho (GB) |
| --- | --- | --- | --- |
| RAID5-C  | `/dev/sdc` |   | 4100 |
|   | `/dev/sdc1` | `/hana/data` | `rest` |


## BI.S2.H4201
{: #4201}

| RAID | Componentes | Unidades | Matriz | Tamanho |
| --- | --- | --- | --- | --- |
| RAID 1 + hot spare| 3x 960 GB 5100 |`hdd0, hdd1, hdd2` | RAID1-A | 960 GB |
| RAID 10 + hot spare | 7x 1,92 TB 5100 | `hdd3, hdd4, hdd5, hdd6, hdd7, hdd8, hdd9` | RAID10-B | 5,76 TB |

| Matriz | Partição | Nome | Tamanho (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 1,0 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` | `rest` |

| Matriz | Partição | Nome | Tamanho (GB) |
| --- | --- | --- | --- |
| RAID10-B | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 1024 |
|   | `/dev/sdb2` | `/hana/data` | `rest` |


## BI.S2.H4200
{: #H4200}

| RAID | Componentes | Unidades | Matriz | Tamanho |
| --- | --- | --- | --- | --- |
| RAID 1 | 2x 800 GB s3710 | `hdd0, hdd1, hdd2` | RAID1-A | 800 GB |
| RAID 5 | 3x 1,2 TB s3710 | `hdd3, hdd4, hdd5, hdd6` | RAID5-B | 2,4 TB |
| RAID 5 | 5x 1,2 TB s3710 | `hdd7, hdd8, hdd9, hdd10, hdd11` | RAID5-C | 4.8 TB |
| Hot spare dedicado | 1X 800 GB s3710 | `hdd2, hdd6, hdd11` | 800 GB DHS | 800 GB |

| Matriz | Partição | Nome | Tamanho (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0,25 |
|   | `/dev/sda2` | `/hana/log` | 512 |
|   | `/dev/sda3` | `/` | `rest` |

| Matriz | Partição | Nome | Tamanho (GB) |
| --- | --- | --- | --- |
| RAID5-B  | `/dev/sdb` |   | 4100 |
|   | `/dev/sdb1` | `/hana/shared` | `rest` |

| Matriz | Partição | Nome | Tamanho (GB) |
| --- | --- | --- | --- |
| RAID5-C  | `/dev/sdc` |   | 4100 |
|   | `/dev/sdc1` | `/hana/data` | `rest` |


## BI.S1.H2000
{: #2048_GB_memory}

| RAID | Componentes | Unidades | Matriz | Tamanho |
| --- | --- | --- | --- | --- |
| RAID 1 | 2x 800 GB s3710 |`hdd0, hdd1` | RAID1-A | 800 GB |
| RAID 10 | 8x 800 GB s3710 | `hdd2, hdd3, hdd4, hdd5, hdd6, hdd7, hdd8, hdd9` | RAID10-B | 4800 GB |
| RAID 10 | 106x 1.2 TB S3710 | `hdd10, hdd11, hdd12, hdd15, hdd16, hdd17, hdd18, hdd19, hdd20, hdd21` | RAID-10C | 7200 GB |
| Hot spare global | 1x 800 GB S3710 | `hdd22` | 800 GB GHS | 800 GB |
| Hot spare RAID 10-C | 1x 1,2 TB S3710 | `hdd23` | 1,2 TB Hotspare | 1,2 TB |

| Matriz | Partição | Nome | Tamanho (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0,25 |
|   | `/dev/sda2` | `/` | `rest` |

| Matriz | Partição | Nome | Tamanho (GB) |
| --- | --- | --- | --- |
| RAID10-B | `/dev/sdb` |   | 4800 |
|   | `/dev/sdb1` | `/hana/log` | `rest` |
|   | `/dev/sdb2` | `/hana/shared` | 2200 |

| Matriz | Partição | Nome | Tamanho (GB) |
| --- | --- | --- | --- |
| RAID10-C | `/dev/sdc` |   | 7200 |
|   | `/dev/sdc1` | `/hana/data` | `rest` |


## BI.S2.H4401
{: #H4401}

| RAID | Componentes | Unidades | Matriz | Tamanho |
| --- | --- | --- | --- | --- |
| RAID 1 + hot spare | 3x 960 GB 5100 |`hdd0, hdd1, hdd2` | RAID1-A | 960 GB |
| RAID 10 + hot spare | 5x 3,84 TB 5100 | `hdd3, hdd4, hdd5, hdd6, hdd7` | RAID10-B | 7,68 TB |

| Matriz | Partição | Nome | Tamanho (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 1,0 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` | `rest` |

| Matriz | Partição | Nome | Tamanho (GB) |
| --- | --- | --- | --- |
| RAID10-B  | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 1024 |
|   | `/dev/sdb2` | `/hana/data` | `rest` |


## BI.S2.H8401
{: #H8401}

| RAID | Componentes | Unidades | Matriz | Tamanho |
| --- | --- | --- | --- | --- |
| RAID 1 + hot spare| 3x 960 GB 5100 |`hdd0, hdd1, hdd2` | RAID1-A | 960 GB |
| RAID 10 + hot spare | 5x 3,84 TB 5100 | `hdd3, hdd4, hdd5, hdd6, hdd7` | RAID10-B | 7,68 TB |

| Matriz | Partição | Nome | Tamanho (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 1,0 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` | `rest` |

| Matriz | Partição | Nome | Tamanho (GB) |
| --- | --- | --- | --- |
| RAID10-B  | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 1024 |
|   | `/dev/sdb2` | `hana/data` | `rest` |


## BI.S2.H4400
{: #4096_GB_memory}

| RAID | Componentes | Unidades | Matriz | Tamanho |
| --- | --- | --- | --- | --- |
| RAID 1 | 3x 800 GB s3710 |`hdd0` | RAID1-A | 800 GB |
| RAID 5 | 6x 1,2 TB s3710 | `hdd1` | RAID5-B | 4100 GB |
| RAID 5 | 9x 1,2 TB s3710 | `hdd2` | RAID-5C | 8400 GB |
| Hot spare global | 1x 800 GB S3710 | `hdd22` | 800 GB GHS | 800 GB |

| Matriz | Partição | Nome | Tamanho (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0,25 |
|   | `/dev/sda2` | `/hana/log` | 512 |
|   | `/dev/sda3` | `/` | `rest` |

| Matriz | Partição | Nome | Tamanho (GB) |
| --- | --- | --- | --- |
| RAID5-B  | `/dev/sdb` |   | 4100 |
|   | `/dev/sdb1` | `/hana/shared` | `rest` |

| Matriz | Partição | Nome | Tamanho (GB) |
| --- | --- | --- | --- |
| RAID5-C  | `/dev/sdc` |   | 4100 |
|   | `/dev/sdc1` | `/hana/data` | `rest` |


## BI.S2.H4400
{: #H4400}

| RAID | Componentes | Unidades | Matriz | Tamanho |
| --- | --- | --- | --- | --- |
| RAID 1 | 3x 800 GB s3710 |`hdd0` | RAID1-A | 800 GB |
| RAID 5 | 6x 1,2 TB s3710 | `hdd1` | RAID5-B | 4100 GB |
| RAID 5 | 9x 1,2 TB s3710 | `hdd2` | RAID-5C | 8400 GB |
| Hot spare global | 1x 800 GB S3710 | `hdd22` | 800 GB GHS | 800 GB |

| Matriz | Partição | Nome | Tamanho (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0,25 |
|   | `/dev/sda2` | `/hana/log` | 512 |
|   | `/dev/sda3` | `/` | `rest` |

| Matriz | Partição | Nome | Tamanho (GB) |
| --- | --- | --- | --- |
| RAID5-B  | `/dev/sdb` |   | 4100 |
|   | `/dev/sdb1` | `/hana/shared` | `rest` |

| Matriz | Partição | Nome | Tamanho (GB) |
| --- | --- | --- | --- |
| RAID5-C  | `/dev/sdc` |   | 4100 |
|   | `/dev/sdc1` | `/hana/data` | `rest` |



## BI.S2.H8801
{: #H8801}

| RAID | Componentes | Unidades | Matriz | Tamanho |
| --- | --- | --- | --- | --- |
| RAID 1 + hot spare | 3x 960 GB 5100 |`hdd0, hdd1, hdd2` | RAID1-A | 960 GB |
| RAID 10 + hot spare | 7x 3,84 TB 5100 | `hdd3, hdd4, hdd5, hdd6, hdd7, hdd8, hdd9` | RAID10-B | 15,36 TB |

| Matriz | Partição | Nome | Tamanho (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 1,0 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` | `rest` |

| Matriz | Partição | Nome | Tamanho (GB) |
| --- | --- | --- | --- |
| RAID10-B  | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 1024 |
|   | `/dev/sdb2` | `/hana/data` | `rest` |


## BI.S2.H8800
{: #8192_GB_memory}

| RAID | Componentes | Unidades | Matriz | Tamanho |
| --- | --- | --- | --- | --- |
| RAID 1 | 2x 800 GB s3710 | +1 Hot spare | RAID1-A | 800 GB |
| RAID 5 | 8x 1,2 TB S3710 |  | RAID5-B | 8400 GB |
| RAID 5 | 18x 1,2 TB S3710 | +1 Hot spare | RAID5-C | 20400 GB |

| Matriz | Partição | Nome | Tamanho (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   | 800 |
|   | `/dev/sda1` | `/boot` | 0,25 |
|   | `/dev/sda2` | `/` | `rest` |

| Matriz | Partição | Nome | Tamanho (GB) |
| --- | --- | --- | --- |
| RAID5-B | `/dev/sdb` |   | 4800 |
|   | `/dev/sdb1` | `/hana/log` | `rest` |
|   | `/dev/sdb2` | `/hana/shared` | 2200 |

| Matriz | Partição | Nome | Tamanho (GB) |
| --- | --- | --- | --- |
| RAID5-C | `/dev/sdc` |   | 7200 |
|   | `/dev/sdc1` | `/hana/data` | `rest` |


## BI.S3.H2192
{: #2192_GB_memory}

| RAID | Componentes | Unidades | Matriz | Tamanho |
| --- | --- | --- | --- | --- |
| RAID 1 | 2x 960 GB 5100 | `hdd0, hdd1` | RAID1-A | 960 GB |
| RAID 1 | 2x 960 GB 5100 | `hdd2, hdd3` | RAID1-B | 960 GB |
| Hot spare global | 1x 960 GB 5100 | `hdd4` |  |  |

| Matriz | Partição | Nome | Tamanho (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 50 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` |  |

| Matriz | Partição | Nome | Tamanho (GB) |
| --- | --- | --- | --- |
| RAID1-B | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 250 |
|   | `/dev\sdb2` | `/hana/data` | `rest` |

## BI.S3.H2384
{: #2384_GB_memory}

| RAID | Componentes | Unidades | Matriz | Tamanho |
| --- | --- | --- | --- | --- |
| RAID 1 | 2x 960 GB 5100 |`hdd0, hdd1` | RAID1-A | 960 GB |
| RAID 10 | 4x 960 GB 5100 | `hdd2, hdd3, hdd4, hdd5` | RAID1-B | 1920 GB |
| Hot spare global | 1x 960 GB 5100 | `hdd` |  |  |

| Matriz | Partição | Nome | Tamanho (GB) |
| --- | --- | --- | --- |
| RAID1-A | `/dev/sda` |   |  |
|   | `/dev/sda1` | `/boot` | 50 |
|   | `/dev/sda2` | `/` | 150 |
|   | `/dev/sda3` | `/usr/sap` | 150 |
|   | `/dev/sda4` | `/hana/log` |  |

| Matriz | Partição | Nome | Tamanho (GB) |
| --- | --- | --- | --- |
| RAID1-B | `/dev/sdb` |   |  |
|   | `/dev/sdb1` | `/hana/shared` | 500 |
|   | `/dev\sdb2` | `/hana/data` | `rest` |

## VMware
{: #vmware}

Você é responsável por definir as configurações relacionadas ao VMware para seu servidor. É possível escolher entre três tamanhos: 1 TB (BI.S2.H4100 (VMware)), 2 TB (BI.S2.H4200 (VMware)) e 4 TB (BI.S2.4400 (VMware)). Para obter mais informações sobre configurar o VMware em seu {{site.data.keyword.baremetal_short}} certificado pela SAP, consulte [Diretrizes de arquitetura e melhores práticas para implementações do SAP HANA no Guia de arquitetura e considerações técnicas do VMware vSphere ![Ícone de link externo](../icons/launch-glyph.svg "Ícone de link externo")](https://www.vmware.com/content/dam/digitalmarketing/vmware/en/pdf/whitepaper/sap_hana_on_vmware_vsphere_best_practices_guide-white-paper.pdf){: new_window} (PDF).

## Próximas Etapas

Agora você está pronto para começar a provisionar seus {{site.data.keyword.baremetal_short}}. Veja [Provisionando seu ambiente SAP HANA](/docs/infrastructure/sap-hana?topic=sap-hana-provision_environment#provision_environment) para suas próximas etapas.
