---



copyright:
  years: 2018
lastupdated: "2018-08-29"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 5. Configurando sua infraestrutura do IBM Cloud para suportar o multinó do SAP HANA
{: #multi-node-storage}

O {{site.data.keyword.cloud_notm}} suporta armazenamento de multinó do SAP HANA para cargas de trabalho de processamento analítico on-line (OLAP), como SAP Business Warehouse (SAP BW) e SAP BW/4HANA. A solução {{site.data.keyword.cloud}} para multinó do SAP HANA consiste em até 15 + 1 nós (15 nós do trabalhador, mais um de espera) para até 30 TB de memória usada para um sistema.

Com multinó, múltiplos nós do SAP HANA constroem um único sistema SAP HANA. Os dados são distribuídos entre esses nós, que formam um único banco de dados. A configuração de multinó suporta escalabilidade e alta disponibilidade por meio da configuração de espera. A oferta {{site.data.keyword.cloud_notm}} para essa configuração segue o [SAP HANA Tailored Data Center Integration](https://blogs.saphana.com/2015/02/18/sap-hana-tailored-data-center-integration-tdi-overview/) (TDI) e usa os servidores certificados pelo SAP HANA do {{site.data.keyword.cloud_notm}} para armazenamento corporativo centralizado e compartilhado.

*Note* que se deve seguir as diretrizes de configuração descritas em [Pedindo seu sistema de multinó](#ordering) para preencher os requisitos do SAP HANA TDI e ter o suporte da SAP.

Siga as diretrizes em [Dimensionando o SAP HANA](https://help.sap.com/viewer/eb3777d5495d46c5b2fa773206bbfb46/2.0.00/en-US/d4a122a7bb57101493e3f5ca08e6b039.html) para determinar o tamanho necessário para o sistema SAP HANA de destino, incluindo a quantia total de memória e armazenamento necessários para sua implementação. Os requisitos de dimensionamento ajudam a estabelecer o número de nós do SAP HANA necessários para o sistema de multinó do SAP HANA e o armazenamento necessário para hospedar os dados.

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

1. Peça três VLANs e servidores diferentes com quatro adaptadores (dois privados e dois públicos). Para obter mais informações sobre pedido de VLANs, veja [Etapa 1 Pedindo VLANs primárias e públicas](https://console.bluemix.net/docs/infrastructure/virtualization/advanced-single-site-vmware-reference-architecturesoftlayer.html#step-1-ordering-primary-public-and-private-vlans). Para obter mais informações sobre como pedir seus servidores, veja [2. Configurando sua infraestrutura](https://console.bluemix.net/docs/infrastructure/sap-hana/hana-setting-up-infrastructure.html#set_up_infrastructure).
2. Configure a VLAN privada inicial como uma "VLAN de armazenamento".
3. [Abra um chamado](https://console.bluemix.net/docs/get-support/howtogetsupport.html#open-ticket) com o Suporte do {{site.data.keyword.cloud_notm}} para
   a. Mover as interfaces públicas para a segunda VLAN
   b. Pedir mais dois adaptadores para serem designados à terceira VLAN, que é a VLAN do cliente

Agora você tem o número de servidores com base em seu esforço de dimensionamento, e sua rede está configurada para que
* O armazenamento possa ser conectado a todos os nós
* A instalação de multinó do SAP HANA possa ser realizada após o armazenamento ter sido anexado

Suas conexões LAN de armazenamento e as conexões entre nós são configuradas pela implementação do {{site.data.keyword.cloud_notm}}. Certifique-se de pedir cada conexão com dois adaptadores de 10 Gb com configuração de failover. Essa configuração assegura a ligação correta do Linux e a configuração LACP. Entre em contato com a equipe de Suporte do {{site.data.keyword.cloud_notm}} caso tenha quaisquer perguntas.

Há critérios de desempenho específicos que devem ser atendidos pelo {{site.data.keyword.IBM_notm}} {{site.data.keyword.blockstorageshort}} (Endurance) e pelo {{site.data.keyword.IBM_short}} {{site.data.keyword.filestorage_short}} (Performance). Para volumes de dados, o armazenamento do Endurance de 2 TB com um KPI de desempenho de 10 IOPS/GB é necessário para cada nó do trabalhador. Um volume adicional do mesmo tamanho é necessário como armazenamento compartilhado do SAP HANA e será compartilhado por todos os nós.

Para volumes de log, um volume de 512 GB de armazenamento do Performance é necessário para cada nó com um KPI de desempenho de IOPS de 10 K.

É possível usar as etapas em [Provisionando e gerenciando o {{site.data.keyword.blockstorageshort}}](https://console.bluemix.net/docs/infrastructure/BlockStorage/provisioning-block_storage.html#provisioning-and-managing-block-storage) ou [Provisionando e gerenciando o {{site.data.keyword.filestorage_full_notm}}](https://console.bluemix.net/docs/infrastructure/FileStorage/provisioning-file-storage.html#provisioning-and-managing-ibm-file-storage-for-ibm-cloud) para pedir seu armazenamento do Endurance e Performance.

## Configurando multinós do SAP HANA
{: #configuring}

O volume compartilhado do SAP HANA, e cada um dos volumes de dados e de log, deve estar acessível a todos os nós. Essa abordagem significa que todos os volumes estão acessíveis para toda a VLAN de armazenamento, que você configurou em [Pedindo seu sistema de multinó](#ordering). Se você não desejar listar cada endereço IP envolvido, torne os volumes acessíveis para a sub-rede IP inteira da VLAN.

Siga a orientação em [SAP HANA em sistemas NetApp FAS com NFS](https://www.netapp.com/us/media/tr-4290.pdf) para configurar o sistema de multinó do SAP HANA. Use as opções de montagem do Network File System (NFS) a seguir para cada volume a ser montado:

`rw,bg,hard,timeo=600,intr,noatime,vers=4,minorversion=1,lock,rsize=1048576,wsize=1048576` em `/etc/fstab`.

Essas opções foram testadas pelo NetApp e {{site.data.keyword.cloud_notm}}. Entre em contato com o Suporte do {{site.data.keyword.cloud_notm}} se você planeja mudar qualquer uma das opções de montagem ou valores.

Depois de montar todos os seus volumes para todos os nós, seus servidores de multinó estão configurados e prontos para instalar o banco de dados de multinó do SAP HANA. Siga as etapas no [Guia de instalação e atualização do SAP HANA Server](https://help.sap.com/viewer/2c1988d620e04368aa4103bf26f17727/2.0.03/en-US) para instalar um banco de dados do SAP HANA de sua versão requerida.
