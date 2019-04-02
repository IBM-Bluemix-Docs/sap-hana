---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-26"

keywords: SAP HANA, SAP applications

subcollection: sap-hana

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}


# 3. Determinando seus aplicativos SAP

Você precisa determinar quais aplicativos baseados em SAP você planeja executar em seus {{site.data.keyword.baremetal_long}}. Itens a considerar ao fazer sua determinação incluem:

 * Como o banco de dados será usado? Há duas maneiras pelas quais o SAP HANA pode ser implementado. A primeira é como um banco de dados para uma pilha SAP NetWeaver, em que atua principalmente como uma origem de dados. O segundo método de implementação é executar o SAP HANA em um modo independente com aplicativos implementados diretamente no sistema SAP HANA. De qualquer forma, o processo de dimensionamento e outros requisitos do sistema e dependências podem diferir com base em como você usa seu sistema (desenvolvimento e teste, prova de conceito ou produção).
 * Como você pretende usar os aplicativos? É o uso desejado para desenvolvimento e teste ou produção?
 * Você usa um serviço de Rede Privada Virtual SSL ou Protocolo de Tunelamento Ponto a Ponto (PPTP) do {{site.data.keyword.cloud_notm}}?

## Próximas Etapas

  [4. Dimensionando o servidor](/docs/infrastructure/sap-hana?topic=sap-hana-size_the_server#size_the_server)

  [5. Determinando sua configuração](/docs/infrastructure/sap-hana?topic=sap-hana-determine_configuration#determine_configuration)
