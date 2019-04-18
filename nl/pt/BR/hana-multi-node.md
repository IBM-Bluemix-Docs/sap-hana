---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-26"

keywords: SAP HANA, {{site.data.keyword.cloud_notm}}, SAP ABAP, LACP, KPIs,VLANs

subcollection: sap-hana

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}

# 5. Configurando sua infraestrutura do IBM Cloud para suportar o multinó do SAP HANA
{: #multi-node-storage}

O {{site.data.keyword.cloud}} suporta armazenamento de multinó do SAP HANA para cargas de trabalho de processamento analítico on-line (OLAP), como SAP Business Warehouse (SAP BW) e SAP BW/4HANA. A solução {{site.data.keyword.cloud_notm}} para multinó do SAP HANA consiste em até 15 + 1 nós (15 nós do trabalhador, mais um de espera) para até 30 TB de memória usada para um sistema.

Com multinó, múltiplos nós do SAP HANA constroem um único sistema SAP HANA. Os dados são distribuídos entre esses nós, que formam um único banco de dados. A configuração de multinó suporta escalabilidade e alta disponibilidade por meio da configuração de espera. A oferta do {{site.data.keyword.cloud_notm}} para essa configuração segue a [SAP HANA Tailored Data Center Integration ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://blogs.saphana.com/2015/02/18/sap-hana-tailored-data-center-integration-tdi-overview/){: new_window} (TDI) e usa servidores certificados pelo SAP HANA do {{site.data.keyword.cloud_notm}} para armazenamento corporativo compartilhado e centralizado.

Deve-se seguir as diretrizes de configuração descritas em [Pedindo seu sistema multinós](#ordering) para preencher os requisitos de TDI do SAP HANA e ter o suporte da SAP.
{: note}

Siga as diretrizes em [Dimensionando o SAP HANA ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://help.sap.com/viewer/eb3777d5495d46c5b2fa773206bbfb46/2.0.00/en-US/d4a122a7bb57101493e3f5ca08e6b039.html){: new_window} para determinar o tamanho necessário para seu sistema SAP HANA de destino, incluindo a quantia total de memória e armazenamento necessários para sua implementação. Os requisitos de dimensionamento ajudam a estabelecer o número de nós do SAP HANA necessários para o sistema de multinó do SAP HANA e o armazenamento necessário para hospedar os dados.

## Revisando a topologia de rede e o layout de armazenamento
{: #reviewing-topology}

A Figura 1 mostra a topologia de rede necessária para a configuração do SAP HANA TDI da infraestrutura como serviço do {{site.data.keyword.cloud_notm}}.

Figura 1. Topologia de rede do SAP HANA TDI da infraestrutura como serviço do IBM Cloud

![Figura 1. Topologia de rede do SAP HANA TDI da infraestrutura como serviço do IBM Cloud](/images/SAP-BW.png "Topologia de rede do SAP HANA TDI da infraestrutura como serviço do IBM Cloud")

## Configurando seus pré-requisitos
{: #prerequisites}

O multinó do SAP HANA requer que determinadas redes estejam instaladas para funcionar. Antes de pedir outros componentes de seu sistema, essas redes devem ser configuradas corretamente, juntamente com os nós de banco de dados. Você precisa
* Uma rede do lado do cliente, que conecta os servidores de aplicativos SAP Advanced Business Application Programming (SAP ABAP), clientes SAP HANA Studio e qualquer outro cliente de rede ao sistema de multinó. As opções de rendimento e disponibilidade de rede dependem do cenário de uso do sistema de multinó do SAP HANA. Considere os principais indicadores de desempenho (KPIs) de disponibilidade e a quantia de dados transferidos do banco de dados SAP HANA e para ele que são necessários para seu aplicativo.
* Uma rede de armazenamento, que é necessária para se conectar ao {{site.data.keyword.blockstoragefull}} e ao {{site.data.keyword.filestorage_full_notm}} de backend. Para maximizar o desempenho e a redundância, uma rede de 10 Gb com duas interfaces sob a ligação do Linux ao Link Aggregation Control Protocol (LACP) é necessária. Sem as figuras de desempenho fornecidas das diretrizes de dimensionamento do SAP HANA, os KPIs do SAP HANA TDI não podem ser atendidos.
* Uma rede entre nós para comunicação interna do SAP HANA que é configurada de forma equivalente à rede de armazenamento. A rede entre nós é usada somente para comunicação entre nós e a transferência de dados que pode ser necessária entre os nós durante as operações. Essa configuração de rede necessária está em dois adaptadores físicos de 10 Gb sob a ligação do Linux ao LACP.

## Pedindo seu sistema de multinó
{: #ordering}

Para atender aos KPIs de desempenho e rendimento requeridos pela SAP, suas VLANs, armazenamento e nós de cálculo devem ser pedidos no mesmo data center. Se seus componentes forem distribuídos em múltiplos data centers, a SAP não suportará o sistema de multinó.

1. Peça três VLANs e servidores diferentes com quatro adaptadores (dois privados e dois públicos). Para obter mais informações sobre pedido de VLANs, veja [Etapa 1 Pedindo VLANs primárias e públicas](/docs/infrastructure/virtualization?topic=Virtualization-advanced-single-site-vmware-reference-architecture#step-1-ordering-primary-public-and-private-vlans). Para obter mais informações sobre pedir seus servidores, consulte [Configurando sua infraestrutura](/docs/infrastructure/sap-hana?topic=sap-hana-set_up_infrastructure#set_up_infrastructure#set_up_infrastructure).
2. Configure a VLAN privada inicial como uma "VLAN de armazenamento".
3. [Abra um chamado](/docs/get-support?topic=get-support-open-case#open-case) com o Suporte {{site.data.keyword.cloud_notm}} para (a) mover as interfaces públicas para a segunda VLAN e (b) pedir que mais dois adaptadores sejam designados à terceira VLAN, que é a VLAN do cliente.

Agora você tem o número de servidores com base em seu esforço de dimensionamento, e sua rede está configurada para que
* O armazenamento possa ser conectado a todos os nós
* A instalação de multinó do SAP HANA possa ser realizada após o armazenamento ter sido anexado

Suas conexões LAN de armazenamento e as conexões entre nós são configuradas pela implementação do {{site.data.keyword.cloud_notm}}. Certifique-se de pedir cada conexão com dois adaptadores de 10 Gb com configuração de failover. Essa configuração assegura a ligação correta do Linux e a configuração LACP. Entre em contato com a equipe de Suporte do {{site.data.keyword.cloud_notm}} caso tenha quaisquer perguntas.

Há critérios de desempenho específicos que devem ser atendidos pelos volumes do Network File System (NFS) conectados (consulte [Introdução ao {{site.data.keyword.filestorage_short}}](/docs/infrastructure/FileStorage?topic=FileStorage-getting-started#getting-started) para obter mais informações). Para volumes `/data/`, com base em teste, o armazenamento do Endurance de 2 TB com um KPI de desempenho de 10 IOPS/GB é necessário para cada nó do trabalhador. Um volume adicional do mesmo tamanho é necessário como um volume do SAP HANA `/shared/` e será compartilhado por todos os nós. Com base no teste, o volume `/shared/` deve ser um volume de armazenamento de desempenho com 12 IOPS/GB.

Para volumes de log, um volume de 512 GB de armazenamento do Performance é necessário para cada nó com um KPI de desempenho de IOPS de 10 K.

É possível usar as etapas em [Provisionando e gerenciando o {{site.data.keyword.blockstorageshort}}](/docs/infrastructure/BlockStorage?topic=BlockStorage-getting-started#getting-started) ou [Provisionando e gerenciando o {{site.data.keyword.filestorage_full_notm}}](/docs/infrastructure/FileStorage?topic=FileStorage-orderingConsole#orderingConsole) para pedir seu armazenamento do Endurance e de desempenho.

## Configurando multinós do SAP HANA
{: #configuring}

O volume compartilhado do SAP HANA, e cada um dos volumes de dados e de log, deve estar acessível a todos os nós. Essa abordagem significa que todos os volumes estão acessíveis para toda a VLAN de armazenamento, que você configurou em [Pedindo seu sistema de multinó](#ordering). Se você não desejar listar cada endereço IP envolvido, torne os volumes acessíveis para a sub-rede IP inteira da VLAN.

Siga a orientação em [SAP HANA em sistemas NetApp FAS com NFS ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.netapp.com/us/media/tr-4290.pdf){: new_window} para configurar seu sistema multinós do SAP HANA. Use as opções de montagem do Network File System (NFS) a seguir para cada volume a ser montado:

`rw,bg,hard,timeo=600,intr,noatime,vers=4,minorversion=1,lock,rsize=1048576,wsize=1048576` em `/etc/fstab`.

Essas opções foram testadas pelo NetApp e {{site.data.keyword.cloud_notm}}. Entre em contato com o Suporte do {{site.data.keyword.cloud_notm}} se você planeja mudar qualquer uma das opções de montagem ou valores.

Depois de montar todos os seus volumes para todos os nós, seus servidores de multinó estão configurados e prontos para instalar o banco de dados de multinó do SAP HANA. Siga as etapas no [Guia de instalação e atualização do servidor SAP HANA ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://help.sap.com/viewer/2c1988d620e04368aa4103bf26f17727/2.0.03/en-US){: new_window} para instalar um banco de dados SAP HANA em sua versão necessária.
