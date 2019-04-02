---

copyright:
  years: 2017, 2019
lastupdated: "2019-02-26"

keywords: SAP HANA, SAP landscape, {{site.data.keyword.cloud_notm}}

subcollection: sap-hana

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Planejando a sua paisagem do sistema
{: #planning-your-system-landscape}

Uma *paisagem* SAP é um grupo de dois ou mais *sistemas* SAP que geralmente incluem desenvolvimento, qualidade e teste e produção. Um sistema SAP consiste em uma ou mais *instâncias do SAP*, que são um grupo de processos que são iniciados e interrompidos ao mesmo tempo. Para obter mais informações sobre cenários da SAP, consulte [*Arquitetura de referência do SAP Business Suite em Sistemas IBM X6* ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://lenovopress.com/redp5073.pdf){: new_window}.
{: shortdesc}

Há várias configurações possíveis de paisagem, como servidor (tamanho)/armazenamento (tamanho), para todas as soluções SAP no mercado. Essas soluções incluem produtos baseados no SAP NetWeaver, como o [SAP Business Suite ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://open.sap.com/courses/suitehana1){: new_window}, o SAP Business Warehouse e todos os complementos SAP específicos que os servidores na Infraestrutura certificada pela SAP do {{site.data.keyword.cloud}} suportam. Soluções adicionais a serem consideradas são qualquer software de terceiros que possa integrar-se ao SAP.

O SAP HANA pode ser executado como um banco de dados para uma solução baseada em pilha SAP NetWeaver ou como uma entidade independente, dependendo do seu cenário de uso. Para ambos os cenários, a oferta {{site.data.keyword.cloud_notm}} fornece servidores certificados pelo SAP NetWeaver pré-configurados cuja paisagem ao redor pode ser construída de qualquer outro servidor.

Você deseja ser o mais detalhado possível quando determinar o tamanho de seu servidor com base nos aplicativos que planeja executar, potencial crescimento e desempenho. Além disso, considere os requisitos de armazenamento e memória para seus aplicativos. Os sistemas SAP em uma paisagem têm requisitos específicos para conectividade, entre si ou para sistemas externos. Para obter mais informações, veja [Itens a considerar ao planejar sua paisagem do SAP](/docs/infrastructure/sap-hana?topic=sap-hana-considerations#considerations).

A Tabela 1 contém as etapas dentro do processo de planejamento. Use-a para ajudar a construir sua paisagem do SAP de destino.

Tabela 1. Visão geral do processo de planejamento

| Etapa | Detalhes |
| --- | --- |
| 1 | [Obter credenciais do SAP e {{site.data.keyword.cloud_notm}} e criar contas](/docs/infrastructure/sap-hana?topic=sap-hana-get_sap_ibm_credentials#get_sap_ibm_credentials) |
| 2 | [Revise qualquer documentação relevante da SAP e do {{site.data.keyword.cloud_notm}}](/docs/infrastructure/sap-hana?topic=sap-hana-review_doc#review_doc) |
| 3 | [Determinar seus aplicativos SAP](/docs/infrastructure/sap-hana?topic=sap-hana-3-determining-your-sap-applications#3-determining-your-sap-applications) |
| 4 | [Dimensionar o servidor](/docs/infrastructure/sap-hana?topic=sap-hana-size_the_server#size_the_server) |
| 5 | [Determinar sua configuração](/docs/infrastructure/sap-hana?topic=sap-hana-determine_configuration#determine_configuration) |

## Próximas Etapas

Selecione a etapa apropriada na Tabela 1 para começar a planejar sua paisagem do SAP.
