---

copyright:
  years: 2017, 2019
lastupdated: "2019-02-28"

keywords: SAP HANA, {{site.data.keyword.cloud_notm}}, infrastructure, {{site.data.keyword.baremetal_short}}, SAP-certified infrastructure, deployment, BYOL,

subcollection: sap-hana

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}
{:note: .note}

# 2. Configurando a sua infraestrutura
{: #set_up_infrastructure}

A orientação para configurar {{site.data.keyword.baremetal_long}}, rede, segurança, armazenamento e sistema operacional (OS) do SAP HANA está na seção a seguir. Entre em contato com o [Suporte do {{site.data.keyword.cloud_notm}}](/docs/get-support?topic=get-support-getting-customer-support#getting-customer-support) com quaisquer perguntas.

## Pedindo seu servidor
{: order-server}

Use as etapas a seguir para pedir seus {{site.data.keyword.baremetal_short}}. Informações adicionais podem ser localizadas em [Construindo um servidor bare metal customizado](/docs/bare-metal?topic=bare-metal-ordering-baremetal-server#ordering-baremetal-server).

1. Efetue login no [portal do cliente de infraestrutura do {{site.data.keyword.cloud_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://control.softlayer.com){: new_window} com suas credenciais exclusivas.
2. Clique em **Conta** > **Fazer um pedido** na página Resumo da conta.
3. Clique no link **Mensal** em {{site.data.keyword.baremetal_short}} na página Dispositivos. A Lista de servidores aparece; os Servidores Certificados pela SAP estão na parte superior da lista.
4. Clique no hiperlink sob **PREÇO INICIAL POR MÊS** para selecionar o servidor apropriado e ser levado para a página Configurar/Pedir. Os servidores certificados pelo SAP HANA são identificados com um **-H** sob Modelo de CPU.  

Os servidores BI.S3.H2192 e BI.S3.H238 também estão disponíveis para faturamento **Horário**.
{: note}

5. Insira o número de servidores que você está pedindo no campo **Quantidade** e selecione seu **Data center**.
6. **Servidor**, **RAM** e sua opção de armazenamento privado são padronizados com base em sua seleção do servidor e não podem ser mudados. O {{site.data.keyword.IBM_notm}} {{site.data.keyword.blockstorageshort}} for {{site.data.keyword.cloud_notm}} ou {{site.data.keyword.filestorage_full_notm}} e o Network Attached Storage (NAS) serão pedidos depois que você tiver pedido seu servidor.
7. Selecione seu **Sistema operacional** Red Hat ou SUSE e selecione o sistema operacional específico ou hypervisor VMware para seu servidor.

Se você estiver trazendo sua própria licença (BYOL) para seu sistema operacional, selecione **Outro** > **Nenhum sistema operacional**. Para obter mais informações, consulte [Traga sua própria licença](#byol).
{ :note}

## Selecionar suas opções do servidor
{: #select_options}

Na próxima etapa, você selecionará o tipo e o número de discos que deseja incluir em sua configuração. Também será possível selecionar opções diferentes para grupos de armazenamentos Redundant Array of Independent Disks (RAID) e layouts de particionamento em cima dos grupos de armazenamentos RAID. Para obter mais informações, consulte [Sobre o RAID](/docs/bare-metal?topic=bare-metal-about-raid#about-raid) ou [Suporte do {{site.data.keyword.cloud_notm}}](/docs/get-support?topic=get-support-getting-customer-support#getting-customer-support).

1. Em **Servidores certificados SAP**, faça sua seleção com base em como você planeja usar seu servidor. Consulte a [Design Decision Tool ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://github.com/ibm-cloud-architecture/infrastructure-design-decision-tool){: new_window} (role para baixo até a ferramenta) ou [Suporte do {{site.data.keyword.cloud_notm}}](/docs/get-support?topic=get-support-getting-customer-support#getting-customer-support) para obter mais informações
2. Clique em **Incluir na ordem** na parte inferior da página.

## Definindo configurações do sistema avançado
{: #adv_config}

1. Siga as diretrizes de [Configuração do sistema avançado](/docs/bare-metal?topic=bare-metal-ordering-baremetal-server#ordering-baremetal-server) para obter ajuda com os valores na janela **Configuração do sistema avançado**.

Os nomes de host SAP devem ter no máximo 13 caracteres alfanuméricos. Para obter mais informações sobre o nome do host da SAP, consulte [Notas da SAP 611361 ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://launchpad.support.sap.com/#/611361){: new_window} e [129997 ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://launchpad.support.sap.com/#/129997){: new_window}.

## Confirmando suas seleções
{: #confirm_selections}

1. Confirme suas seleções na página Check-out e clique em **Termos de serviço de nuvem** e **Contrato de software de terceiros**.
2. Role para baixo para Criar conta: inserir faturamento e insira o **Tipo de pagamento, nome, cartão** e **Expiração** (data) para o cartão de crédito a ser usado para faturamento.
3. Clique em **Enviar ordem**. Você é redirecionado para uma tela com seu número de ordem. É possível imprimir a tela porque ela também é seu recibo de ordem.

Um e-mail de confirmação com o assunto _Sua ordem do {{site.data.keyword.cloud_notm}} ## foi aprovada_ é enviado para o endereço de e-mail em seu perfil. Esse e-mail é um aviso de que seu servidor foi aprovado e está no processo de ser implementado. Após ele ser implementado, outro aviso será enviado notificando de que o servidor está disponível e pode ser gerenciado por meio do portal do cliente de infraestrutura do [{{site.data.keyword.cloud_notm}} ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://control.softlayer.com){: new_window}.

## Bring Your Own License
{: #byol}

Quando você tiver sua própria licença do sistema operacional, instale-a no {{site.data.keyword.baremetal_short}} com base nas instruções do fornecedor. Para obter mais informações, consulte [A opção Nenhum S.O.](/docs/bare-metal?topic=bare-metal-bm-no-os#bm-no-os).

## Próximas Etapas

Agora você está pronto para começar a gerenciar seus {{site.data.keyword.baremetal_short}}. Consulte [Gerenciando seu ambiente do SAP HANA](/docs/infrastructure/sap-hana?topic=sap-hana-manage_environment#manage_environment) para suas próximas etapas.
