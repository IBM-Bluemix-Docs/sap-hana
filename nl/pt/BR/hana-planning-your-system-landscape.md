---



copyright:
  years: 2017, 2018
lastupdated: "2018-02-05"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Planejando a sua paisagem do sistema
{: #planning-your-system-landscape}

Uma *paisagem* SAP é um grupo de dois ou mais *sistemas* SAP que geralmente incluem desenvolvimento, qualidade e teste e produção. Um sistema SAP consiste em uma ou mais *instâncias do SAP*, que são um grupo de processos que são iniciados e interrompidos ao mesmo tempo. Para obter mais informações sobre paisagens SAP, veja [*SAP Business Suite na arquitetura de referência de sistemas IBM X6*](https://lenovopress.com/redp5073.pdf).
{: shortdesc}

Há várias configurações possíveis de paisagem, como servidor (tamanho)/armazenamento (tamanho), para todas as soluções SAP no mercado. Essas soluções incluem produtos baseados no SAP NetWeaver, como [SAP Business Suite](https://open.sap.com/courses/suitehana1), SAP Business Warehouse e todos os complementos específicos do SAP, que os servidores na oferta {{site.data.keyword.cloud}} for SAP Applications suportam. Soluções adicionais a serem consideradas são qualquer software de terceiros que possa integrar-se ao SAP. 

O SAP HANA pode ser executado como um banco de dados para uma solução baseada em pilha SAP NetWeaver ou como uma entidade independente, dependendo do seu cenário de uso. Para ambos os cenários, a oferta {{site.data.keyword.cloud_notm}} fornece servidores certificados pelo SAP NetWeaver pré-configurados cuja paisagem ao redor pode ser construída de qualquer outro servidor.

Você deseja ser o mais detalhado possível quando determinar o tamanho de seu servidor com base nos aplicativos que planeja executar, potencial crescimento e desempenho. Além disso, considere os requisitos de armazenamento e memória para seus aplicativos. Os sistemas SAP em uma paisagem têm requisitos específicos para conectividade, entre si ou para sistemas externos. Para obter mais informações, veja [Itens a considerar ao planejar sua paisagem do SAP](/docs/infrastructure/sap-hana/hana-considerations.html).

A Tabela 1 contém as etapas dentro do processo de planejamento. Use-a para ajudar a construir sua paisagem do SAP de destino.

Tabela 1. Visão geral do processo de planejamento

| Etapa | Detalhes |
| --- | --- |
| 1 | [Obter credenciais do SAP e {{site.data.keyword.cloud_notm}} e criar contas](/docs/infrastructure/sap-hana/hana-get-credentials.html) |
| 2 | [Revisar qualquer documentação relevante do SAP e {{site.data.keyword.cloud_notm}}](/docs/infrastructure/sap-hana/hana-review-doc.html) |
| 3 | [Determinar seus aplicativos SAP](/docs/infrastructure/sap-hana/hana-determine-apps.html) |
| 4 | [Dimensionar o servidor](/docs/infrastructure/sap-hana/hana-size-server.html) |
| 5 | [Determinar sua configuração](/docs/infrastructure/sap-hana/hana-determine-configuration.html) |

## Próximas Etapas

Selecione a etapa apropriada na Tabela 1 para começar a planejar sua paisagem do SAP.
