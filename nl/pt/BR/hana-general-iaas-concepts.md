---



copyright:
  years: 2017, 2018
lastupdated: "2018-06-28"


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

Para obter mais informações, veja [Data centers](https://www.ibm.com/cloud-computing/bluemix/data-centers){: new_window}.

## Servidores bare metal

{{site.data.keyword.baremetal_long}} são servidores físicos com recursos de customização limitada. Os servidores são dedicados ao seu uso ou de seu cliente e não compartilhados em nenhuma parte, incluindo recursos do servidor, com outros clientes do {{site.data.keyword.cloud_notm}} e são provisionados como um servidor físico inteiro executando sua escolha de sistema operacional (OS). Os sistemas operacionais para a oferta SAP HANA são Red Hat Enterprise Linux 7.4 for SAP HANA, SUSE Linux Enterprise Server 12 SP2 for SAP HANA e VMware Server Virtualization 6.5.

Como a customização é limitado em servidores bare metal, tempos mais rápidos de fornecimento entre 1 e 4 horas são obtidos. O fornecimento rápido é útil quando você está tentando colocar um app no mercado antes da concorrência.

É oferecida uma matriz de combinações de RAM e CPU, pois os servidores SAP certificados têm uma quantia pré-configurada de RAM e número de CPUs. A combinação *não poderá* mudar durante o processo de solicitação ou por meio de um chamado de suporte depois que os servidores forem implementados.

Para obter mais informações, veja [Sobre servidores bare metal](https://console.bluemix.net/docs/bare-metal/about.html#about-bare-metal-servers). 

## Conectividade de rede

A conectividade de rede privada virtual (VPN) com o {{site.data.keyword.cloud_notm}} Virtual Cloud Network é concedida automaticamente quando sua conta do {{site.data.keyword.cloud_notm}} é configurada. Por padrão, seu servidor tem um endereço IP público e privado. Se você deseja que seu servidor seja privado, é possível desligar a interface pública após o seu servidor ser provisionado ou pedir seu servidor como privado. 

Embora os requisitos de rede para SAP HANA (rede redundante de 10 Gb) sejam preenchidos pela oferta {{site.data.keyword.cloud_notm}}, você pode requerer que alguns KPIs (principais indicadores de desempenho) de latência e rendimento sejam atendidos, dependendo de seu cenário de aplicativo. Para obter mais informações sobre como determinar em qual data center localizar seu servidor SAP HANA e como decidir sobre a melhor solução de conectividade de rede, veja as considerações de [Conectividade de rede](/docs/infrastructure/sap-hana/hana-considerations.html#network_connectivity).

Para obter mais informações, veja [Introdução à rede privada virtual](https://console.bluemix.net/docs/infrastructure/iaas-vpn/getting-started.html#getting-started-with-virtual-private-networking-vpn-) e o White Paper [*Requisitos de rede do SAP HANA*](https://www.sap.com/documents/2016/08/1cd2c2fb-807c-0010-82c7-eda71af511fa.html).

## Storage
{: #storage}

O armazenamento local é fornecido com seus {{site.data.keyword.baremetal_short}} e usa a LAN virtual de rede privada (VLAN) do {{site.data.keyword.cloud_notm}} para ajudar a fornecer segurança de nível corporativo sem obstrução de acesso de administrador. Para os servidores SAP HANA certificados, ele é projetado e configurado para atender aos KPIs definidos pela SAP para o rendimento e a latência em conformidade com os critérios de certificação do SAP HANA. O armazenamento local tem o tamanho relevante dos diferentes sistemas de subarquivo, conforme definido pelo Guia de instalação do SAP HANA (`data.log` e `shared`). Nenhuma adaptação adicional precisa ser feita em sua parte.

Há dois tipos de armazenamento para o {{site.data.keyword.cloud_notm}}, bloco e arquivo, dentre os quais escolher para executar backups e restaurações para o SAP HANA. Ambos os tipos usam input/output operations per second (IOPS), que é usado para determinar as necessidades de armazenamento. O IOPS é medido com base no tamanho de bloco de 16 KB com uma combinação de leitura/gravação 50/50. Para obter o IOPS máximo em um volume, recursos de rede adequados precisam estar no local. Outras considerações incluem uso de rede privada fora do armazenamento e do lado do host e ajustes específicos do aplicativo (por exemplo, pilhas de IP e profundidades da fila). Para obter mais informações, veja [Introdução ao Block Storage](https://console.bluemix.net/docs/infrastructure/BlockStorage/index.html#getting-started-with-block-storage) e [Introdução ao File Storage](https://console.bluemix.net/docs/infrastructure/FileStorage/index.html#getting-started-with-file-storage).

O {{site.data.keyword.cloud_notm}} também oferece o Network Attached Storage (NAS) se você está procurando uma solução de backup rápida e com custo eficiente para seus dispositivos. O NAS pode ser montado por meio do Network File System (NFS) e pode ser usado com o Protocolo de Transferência de Arquivos (FTP) com Parallels Plesk Painel e cPanel@WHM.

O armazenamento NAS pode ser usado para qualquer propósito, mas, neste caso, *não* deve ser usado para os dados ou arquivos de log do SAP HANA. O armazenamento não preenche os critérios sobre KPIs de E/S. No entanto, o armazenamento pode ser usado para dispositivos de backup e todos os outros tipos de dados. Ele pode ser usado pelo SAP HANA como dispositivos de backup para dados e arquivos de log, quando montados por NFS.  
  
O armazenamento NAS e FTP é faturado mensalmente e está disponível em vários tamanhos de armazenamento. É possível interagir primariamente com o seu armazenamento NAS e FTP dentro da linha de comandos ou terminal com o sistema operacional ou por meio de interações apontar-e-clicar nos painéis dentro do portal do cliente de infraestrutura do {{site.data.keyword.cloud_notm}}. No portal do cliente, os detalhes e o uso do NAS podem ser usados, mas o serviço não pode ser manipulado fora da linha de comandos, kernel ou painel de controle.

Para obter mais informações sobre NAS em um ambiente {{site.data.keyword.cloud_notm}}, veja [Introdução ao NAS](https://console.bluemix.net/docs/infrastructure/network-attached-storage/index.html#getting-started-with-nas).

## Implementação e gerenciamento

Os {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} são implementados por meio do portal do cliente de infraestrutura do {{site.data.keyword.cloud_notm}} ou da API depois de criar sua conta do cliente do {{site.data.keyword.cloud_notm}}. Os servidores podem ser gerenciados por meio do portal do cliente, API ou interface da linha de comandos (CLI). Para obter mais informações, veja [Sobre servidores bare metal](https://console.bluemix.net/docs/bare-metal/about.html#about-bare-metal-servers).

## Suporte

O [Suporte ao cliente do {{site.data.keyword.cloud_notm}}](https://console.bluemix.net/docs/support/index.html#getting-customer-support) manipula quaisquer questões e problemas de suporte que possam surgir por meio de vários pontos de venda, incluindo bate-papo, telefone e suporte baseado em chamado. O suporte ao cliente é oferecido sem nenhum custo para todos os clientes do {{site.data.keyword.cloud_notm}} e cobre a maioria dos chamados que são colocados todos os dias. Para obter mais informações, veja [Obtendo suporte ao cliente](https://console.bluemix.net./docs/support/index.html#getting-customer-support).

Também é possível continuar a criar chamados por meio do Suporte SAP que estão relacionados aos seus produtos {{site.data.keyword.cloud_notm}} IaaS e SAP. Para obter mais informações, veja [Suporte SAP](https://support.sap.com/en/index.html) e [Nota SAP 2414820](https://launchpad.support.sap.com/#/notes/2414820).

## Instalando o SAP HANA

O software SAP HANA deve ser instalado por um instalador SAP HANA certificado que concluiu o curso de certificação de instalação do SAP HANA. Para obter mais informações, consulte [Quem pode instalar o SAP HANA?](http://www.saphanacentral.com/p/who-can-install-sap-hana.html).
