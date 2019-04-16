---

copyright:
  years: 2017, 2019
lastupdated: "2019-02-26"

keywords: SAP HANA, {{site.data.keyword.cloud_notm}}, {{site.data.keywords.baremetal_short}}, data centers, VPN,

subcollection: sap-hana

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Visão geral do SAP HANA no IBM Cloud IaaS
{: #iaas-overview}

Um ambiente Infrastructure-as-a-server (IaaS) consiste em vários componentes: data center, cálculo, conectividade, armazenamento e rede.

## Datacenters

Com data centers ao redor do Norte e América do Sul, Europa, Ásia e Austrália, será possível provisionar recursos em nuvem onde (e quando) você precisar deles. Cada data center é conectado à rede privada global do {{site.data.keyword.cloud_notm}}, fazendo transferências de dados de modo mais rápido e eficiente em qualquer lugar no mundo.

Para obter mais informações, consulte [Data centers ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.ibm.com/cloud-computing/bluemix/data-centers){: new_window}.

## Servidores bare metal

{{site.data.keyword.baremetal_long}} são servidores físicos com recursos de customização limitada. Os servidores são dedicados ao seu uso ou de seu cliente e não compartilhados em nenhuma parte, incluindo recursos do servidor, com outros clientes do {{site.data.keyword.cloud_notm}} e são provisionados como um servidor físico inteiro executando sua escolha de sistema operacional (OS). Os sistemas operacionais para a oferta SAP HANA são Red Hat Enterprise Linux 7.4 for SAP HANA, SUSE Linux Enterprise Server 12 SP2 for SAP HANA e VMware Server Virtualization 6.5.

Como a customização é limitado em servidores bare metal, tempos mais rápidos de fornecimento entre 1 e 4 horas são obtidos. O fornecimento rápido é útil quando você está tentando colocar um app no mercado antes da concorrência.

É oferecida uma matriz de combinações de RAM e CPU, pois os servidores SAP certificados têm uma quantia pré-configurada de RAM e número de CPUs. A combinação *não poderá* mudar durante o processo de solicitação ou por meio de um chamado de suporte depois que os servidores forem implementados.

Para obter mais informações, veja [Sobre servidores bare metal](/docs/bare-metal?topic=bare-metal-about#about).

## Conectividade de rede

A conectividade de rede privada virtual (VPN) com o {{site.data.keyword.cloud_notm}} Virtual Cloud Network é concedida automaticamente quando sua conta do {{site.data.keyword.cloud_notm}} é configurada. Por padrão, seu servidor tem um endereço IP público e privado. Se você deseja que seu servidor seja privado, é possível desligar a interface pública após o seu servidor ser provisionado ou pedir seu servidor como privado.

Embora os requisitos de rede para SAP HANA (rede redundante de 10 Gb) sejam preenchidos pela oferta {{site.data.keyword.cloud_notm}}, você pode requerer que alguns KPIs (principais indicadores de desempenho) de latência e rendimento sejam atendidos, dependendo de seu cenário de aplicativo. Para obter mais informações sobre como determinar em qual data center localizar seu servidor SAP HANA e como decidir sobre a melhor solução de conectividade de rede, veja as considerações de [Conectividade de rede](/docs/infrastructure/sap-hana?topic=sap-hana-considerations#network_connectivity).

Para obter mais informações, consulte [Introdução às redes privadas virtuais](/docs/infrastructure/iaas-vpn?topic=VPN-gettingstarted-with-virtual-private-networking#gettingstarted-with-virtual-private-networking) e o White Paper [*Requisitos de rede do SAP HANA* ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.sap.com/documents/2016/08/1cd2c2fb-807c-0010-82c7-eda71af511fa.html){: new_window}.

## Storage
{: #storage}

O armazenamento local é fornecido com seus {{site.data.keyword.baremetal_short}} e usa a LAN virtual de rede privada (VLAN) do {{site.data.keyword.cloud_notm}} para ajudar a fornecer segurança de nível corporativo sem obstrução de acesso de administrador. Para os servidores SAP HANA certificados, ele é projetado e configurado para atender aos KPIs definidos pela SAP para o rendimento e a latência em conformidade com os critérios de certificação do SAP HANA. O armazenamento local tem o tamanho relevante dos diferentes sistemas de subarquivo, conforme definido pelo Guia de instalação do SAP HANA (`data.log` e `shared`). Nenhuma adaptação adicional precisa ser feita em sua parte.

Há dois tipos de armazenamento para o {{site.data.keyword.cloud_notm}}, bloco e arquivo, dentre os quais escolher para executar backups e restaurações para o SAP HANA. Ambos os tipos usam input/output operations per second (IOPS), que é usado para determinar as necessidades de armazenamento. O IOPS é medido com base no tamanho de bloco de 16 KB com uma combinação de leitura/gravação 50/50. Para obter o IOPS máximo em um volume, recursos de rede adequados precisam estar no local. Outras considerações incluem uso de rede privada fora do armazenamento e do lado do host e ajustes específicos do aplicativo (por exemplo, pilhas de IP e profundidades da fila). Para obter mais informações, veja [Introdução ao Block Storage](/docs/infrastructure/BlockStorage?topic=BlockStorage-getting-started#getting-started) e [Introdução ao File Storage](/docs/infrastructure/FileStorage?topic=FileStorage-getting-started#getting-started).

## Implementação e gerenciamento

Os {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} são implementados por meio do portal do cliente de infraestrutura do {{site.data.keyword.cloud_notm}} ou da API depois de criar sua conta do cliente do {{site.data.keyword.cloud_notm}}. Os servidores podem ser gerenciados por meio do portal do cliente, API ou interface da linha de comandos (CLI). Para obter mais informações, veja [Sobre servidores bare metal](/docs/bare-metal?topic=bare-metal-about#about).

## Suporte

O [Suporte ao cliente do {{site.data.keyword.cloud_notm}}](/docs/get-support?topic=get-support-getting-customer-support#getting-customer-support) trata de quaisquer perguntas e problemas de suporte que possam surgir por meio de várias formas, incluindo bate-papo, telefone e suporte baseado em chamado. O suporte ao cliente é oferecido sem nenhum custo para todos os clientes do {{site.data.keyword.cloud_notm}} e cobre a maioria dos chamados que são colocados todos os dias. Para obter mais informações, veja [Obtendo suporte ao cliente](/docs/get-support?topic=get-support-getting-customer-support#getting-customer-support).

Também é possível continuar a criar chamados por meio do Suporte SAP que estão relacionados aos seus produtos {{site.data.keyword.cloud_notm}} IaaS e SAP. Para obter mais informações, consulte o [Suporte da SAP ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://support.sap.com/en/index.html){: new_window} e a [Nota da SAP 2414820 ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://launchpad.support.sap.com/#/notes/2414820){: new_window}.

## Instalando o SAP HANA

O software SAP HANA deve ser instalado por um instalador SAP HANA certificado que concluiu o curso de certificação de instalação do SAP HANA. Para obter mais informações, consulte [Quem pode instalar o SAP HANA? ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://www.saphanacentral.com/p/who-can-install-sap-hana.html){: new_window}.
