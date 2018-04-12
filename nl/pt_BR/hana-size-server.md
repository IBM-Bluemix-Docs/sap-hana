---



copyright:
  years: 2018
lastupdated: "2018-02-05"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}


# 4. Dimensionando o servidor
{: #size_the_server}

Depois de decidir quais soluções SAP você planeja usar, sua próxima etapa é determinar o número de {{site.data.keyword.baremetal_long}} que precisa para suportar sua paisagem do SAP e assegurar que os servidores estejam corretamente dimensionados.
{: shortdesc}

## Entendendo a metodologia de dimensionamento do SAP
{: #size_method}

O SAP HANA é oferecido no {{site.data.keyword.cloud_notm}} em configurações de um nó único com tamanhos de RAM total de 
  * 512 GB
  * 1024 GB (1 TB)
  * 2048 GB (2 TB)
  * 4096 GB (4 TB)
  * 8192 GB (8 TB)
  
É um banco de dados com colunas que geralmente requer menos espaço para armazenar dados em comparação com um Relation Database Management System (RDMS) baseado em linha tradicional. Os dados podem ser altamente compactados e as proporções de compactação podem variar de 3:1 para mais de 10:1 com base nos dados de origem e banco de dados. 

Você precisa dimensionar corretamente seu servidor *antes* de comprá-lo, porque o dimensionamento é a chave para o sucesso de seu projeto. Requisitos de memória ou armazenamento dimensionados incorretamente podem levar a um upgrade e migração para um servidor maior.

## Acessando o SAP Quick Sizer
{: #quick_sizer}

A memória principal é um dos recursos mais importantes para considerar ao dimensionar um dispositivo certificado pelo SAP HANA. O [*Guia principal do SAP HANA*](https://help.sap.com/doc/e95f6750b0fd10148ea5c6be75016694/2.0.00/en-US/SAP_HANA_Master_Guide_en.pdf) público fornece um ponto de início para tópicos relacionados ao dimensionamento. As informações de [Dimensionando o SAP HANA](https://help.sap.com/viewer/eb3777d5495d46c5b2fa773206bbfb46/2.0.00/en-US/d4a122a7bb57101493e3f5ca08e6b039.html) no guia fornecem orientação sobre como dimensionar seu sistema SAP HANA. Elas apontam os diferentes cenários de instalação e migração para as instalações novas e os sistemas existentes. Há um link para a versão do SAP HANA da ferramenta SAP Quick Sizer (um ID do usuário S do SAP é necessário para acessar a ferramenta). A página também lista as Notas SAP relacionadas ao dimensionamento de seu servidor SAP HANA. 

## Dimensionamento para um ambiente virtualizado
{: #size_virtual}

Para considerações adicionais de dimensionamento ao executar o SAP HANA em um ambiente virtualizado, veja [Implementações do servidor VMware ESXi](/docs/infrastructure/sap-hana/hana-considerations.html#vmware-server) e [*Diretrizes e melhores práticas de arquitetura para implementações do SAP HANA no VMware VSphere: Guia de arquitetura e considerações técnicas*](https://www.vmware.com/content/dam/digitalmarketing/vmware/en/pdf/whitepaper/sap_hana_on_vmware_vsphere_best_practices_guide-white-paper.pdf).

## Próximas Etapas

 [5. Determinando sua configuração](/docs/infrastructure/sap-hana/hana-determine-configuration.html)
