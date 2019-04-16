---

copyright:
  years: 2017, 2019
lastupdated: "2019-02-26"

keywords: SAP HANA, network connectivity, VLANs, external storage, high availability, highly available, disaster recovery, HA, DR, VLANs,

subcollection: sap-hana

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# Itens a considerar ao planejar sua paisagem do SAP
{: #considerations}

Os sistemas SAP em uma paisagem têm requisitos específicos para conectividade, seja entre si ou para sistemas externos. Você também precisa pensar sobre armazenamento externo para sua paisagem e o que fazer se decidir implementar o VMware em seu servidor.

## Conectividade de rede
{: #network_connectivity}

A [rede do {{site.data.keyword.cloud_notm}} ](/docs/infrastructure/sap-hana?topic=sap-hana-about_ibmcloud_for_sap#ibm_cloud_network) forneceu uma visão geral da abordagem do {{site.data.keyword.cloud}} para a conectividade de rede. Os problemas com a conectividade de rede podem causar atrasos significativos para seu projeto se você não planejar adequadamente, independentemente de como planeja usar seu sistema.

Em geral, você tem duas opções de interface para seus servidores {{site.data.keyword.cloud_notm}} provisionados pelo IaaS - a primeira é uma interface externa com um IP público. A segunda é uma interface interna que é fornecida com um “IP privado” em conformidade com a Solicitação de Comentários (RFC) 1918. Também é possível escolher uma única interface interna com um “IP privado”. O IP externo pode ser mais fácil de usar, mas há um risco potencial, embora um firewall básico seja instalado e pré-configurado.

A segunda opção acessa a Rede Privada Virtual (VPN) do {{site.data.keyword.cloud_notm}} por meio do portal do cliente de infraestrutura do {{site.data.keyword.cloud_notm}} ou implementa um dispositivo de segurança em sua paisagem. Os dispositivos de segurança são oferecidos para firewalls, conversão de endereço de rede, acesso de VPN e outras funções de rede. É aconselhável que seu departamento de rede fale com o [Suporte do {{site.data.keyword.cloud_notm}}](/docs/get-support?topic=get-support-getting-customer-support#getting-customer-support) após a determinação do layout de seu cenário e da conectividade requerida na camada do aplicativo SAP.

### VLANs
{: #vlans}

Se você deseja separar diferentes tipos de tráfego de rede em sua paisagem, é possível pedir mais LANs virtuais (VLANs). Tenha em mente que as VLANs adicionais somente levam à segregação de tráfego, sem aumentar o desempenho. A SAP geralmente recomenda usar redes de 10 Gb para o tráfego entre seus servidores de aplicativos e bancos de dados SAP HANA e para outros clientes SAP HANA, como SAP Business Intelligence. Se você deseja segregar o acesso administrativo para seu servidor SAP HANA de outros clientes, é necessário pedir outra VLAN para sua paisagem. Outra opção é separar o tráfego por meio da rede pública e privada, pois uplinks "físicos" adicionais não são suportados pelo {{site.data.keyword.cloud_notm}}. Siga as recomendações da SAP para o [SAP HANA Tailored Data Center Integration (TDI) ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://blogs.saphana.com/2015/02/18/sap-hana-tailored-data-center-integration-tdi-overview/){: new_window}.

O acesso por meio de VPN, bem como o acesso por meio de um jump box, permite acesso transparente às suas instâncias do SAP HANA por meio do SAP HANA Studio.

## Armazenamento externo
{: #external_storage}

Além do armazenamento local, você pode requerer mais armazenamento externo para executar backups. Para esses requisitos, é possível pedir armazenamento de bloco ou Network Attached Storage (NAS) conforme descrito em [Armazenamento](/docs/infrastructure/sap-hana?topic=sap-hana-iaas-overview#storage). Como dados extras de bloco de armazenamento e de Network File System (NFS) são transferidos por meio dos mesmos adaptadores físicos que todos os outros tráfegos de rede, o impacto precisa ser considerado.

Para armazenamento externo, é importante calcular seus requisitos do projeto antes de decidir sobre uma solução de armazenamento. Se você precisar restaurar um sistema SAP HANA, o IOPS de seu armazenamento terá uma influência significativa na janela de restauração. As janelas de backup não são tão críticas com o SAP HANA porque todos os backups são backups on-line, não importa como você configura o SAP HANA.

Por exemplo, usando o {{site.data.keyword.cloud_notm}} {{site.data.keyword.blockstorageshort}}, é possível calcular para uma restauração aproximada de 12 TB do SAP HANA em uma velocidade máxima. Deve-se criar três dispositivos de armazenamento físico (LUNs iSCSI de armazenamento de bloco) porque o tamanho máximo por dispositivo é 4 TB. É possível criar uma faixa nesses três dispositivos com o Gerenciador de Volume Lógico Linux e criar um dispositivo lógico de 12 TB.

Os 12 TB permitem 3x10 IOPS/GB, que é um total de 122.880 IOPS/GB em 16 KB. Isso fornece a você um tempo de restauração de 1,875 GB por segundo ou um tempo de restauração total abaixo de 2 horas. Como a medida para o IOPS é tomada em uma distribuição 50/50 de leitura e gravação, é possível considerar os números como um limite inferior de desempenho de restauração. É aconselhável executar testes de backup e restauração se você conta com uma determinada janela de restauração.

O {{site.data.keyword.cloud_notm}} {{site.data.keyword.blockstorageshort}}, o {{site.data.keyword.filestorage_full_notm}} ou o NAS podem servir como um espaço de backup ou como armazenamento para componentes de software adicionais que são instalados em seu servidor. O {{site.data.keyword.cloud_notm}} Storage e o NSA não podem, no entanto, ser usados como armazenamento para o SAP HANA porque essas opções não cumprem os critérios de KPI.

Para obter mais informações, veja [Introdução ao {{site.data.keyword.blockstorageshort}}](/docs/infrastructure/BlockStorage?topic=BlockStorage-getting-started#getting-started) e [Introdução ao {{site.data.keyword.filestorage_full_notm}}](/docs/infrastructure/FileStorage?topic=FileStorage-getting-started#getting-started).

## Cenários de alta disponibilidade e recuperação de desastre
{: #ha_dr}

O ambiente {{site.data.keyword.cloud_notm}} não suporta nenhum cenário pré-configurado de alta disponibilidade (HA). No entanto, ele permite implementar soluções HA para SAP HANA por meio de extensões HA do Red Hat Enterprise Linux, como um caso no local.

A replicação do sistema SAP HANA pode ser configurada com um failover automatizado de um servidor para uma réplica. Siga a documentação SAP na replicação do sistema para determinar o modo de replicação que melhor se ajusta ao seu cenário de aplicativo e seu nível de resiliência de desastre. Dependendo do modo de replicação, diferentes KPIs de rede precisam ser preenchidos. Consulte as recomendações SAP sobre o rendimento de rede e a latência para determinar o rendimento necessário e a latência máxima para o modo de operação de sua escolha. A topologia de rede do {{site.data.keyword.cloud_notm}} deve ser capaz de entregar todas as configurações necessárias. Entre em contato com o Suporte do {{site.data.keyword.cloud_notm}} para determinar a configuração ideal para seu cenário se você não tiver certeza ou se desejar que seu site de recuperação de desastre em um data center diferente alcance resiliência máxima de desastre.

Os ambientes de Ampliação do SAP HANA (multinó) ainda estão sob avaliação. Em outras palavras, um nó de espera para SAP HANA não é uma opção atual em um ambiente {{site.data.keyword.cloud_notm}}.

Para obter mais informações sobre alta disponibilidade e recuperação de desastre, consulte [Suporte de alta disponibilidade do {{site.data.keyword.cloud_notm}}](/docs/infrastructure/sap-hana?topic=sap-hana-ha#ha) e [Recuperação de desastre](/docs/infrastructure/sap-reference-architecture?topic=sap-reference-architecture-recommendations#dr).

Para obter mais informações sobre a replicação do sistema e o rendimento e latência de rede, veja
  * [Como executar a replicação do sistema para o SAP HANA ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.sap.com/documents/2013/10/26c02b58-5a7c-0010-82c7-eda71af511fa.html){: new_window}
  * [Rede necessária para a replicação do sistema SAP HANA ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.sap.com/documents/2014/06/babb2b55-5a7c-0010-82c7-eda71af511fa.html){: new_window}

Para obter mais informações sobre como configurar as extensões de cluster de HA para seu sistema operacional Linux, veja
  * [Replicação do sistema SAP HANA automatizada com o Pacemaker no Guia de configuração do RHEL ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://access.redhat.com/articles/1466063){: new_window}
  * [Cenário otimizado de desempenho do SR do SAP HANA ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.suse.com/docrep/documents/ir8w88iwu7/suse_linux_enterprise_server_for_sap_applications_12_sp1.pdf){: new_window}

## Implementações do servidor VMware ESXi
{: #vmware_server}

Todos os servidores na oferta {{site.data.keyword.cloud_notm}} SAP HANA são certificados para VMware ESX, que torna o SAP HANA implementável em máquinas virtuais (VMs). Se um servidor for pedido com o VMware ESX, ele será implementado com uma instância ESX configurada básica e pré-instalada; nenhuma VM será implementada. Você é responsável por implementar o sistema operacional guest correto em uma implementação baseada em ESX. Siga as instruções definidas na Nota SAP 2414820 para escolher uma versão do sistema operacional suportada com o SAP HANA no {{site.data.keyword.cloud_notm}}.

O processo de dimensionamento para uma implementação baseada em ESX difere daquele da implementação do servidor bare metal. Siga as recomendações em *Diretrizes e melhores práticas de arquitetura para implementações do SAP HANA no VMware vSphere: Guia de arquitetura e considerações técnicas*. A sobrecarga para a camada de virtualização precisa ser calculada, seguindo as regras no *Arquitetura...e guia de considerações*. Após o sistema operacional guest ser implementado em uma VM, certifique-se de que os KPIs TDI do SAP HANA sejam atendidos. Verifique a Nota SAP 1943937 para obter detalhes sobre como testar o ambiente para conformidade com os pré-requisitos do Suporte SAP. Os pré-requisitos precisam ser concluídos para cada VM implementado em um servidor específico.

Várias outras regras definidas pela SAP devem ser seguidas para implementar o SAP HANA em um ambiente virtualizado. Para produção, siga as restrições que são descritas na Nota SAP 1995460. A Nota SAP 2024433 descreve as regras para múltiplas VMs em um servidor.

Para obter mais informações, veja a documentação a seguir:
  * [Nota da SAP 2414820 ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://launchpad.support.sap.com/#/notes/2414820){: new_window}
  * [*Diretrizes de arquitetura e melhores práticas para implementações do Guia de arquitetura e considerações técnicas do SAP HANA no VMware vSphere* ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.vmware.com/content/dam/digitalmarketing/vmware/en/pdf/whitepaper/sap_hana_on_vmware_vsphere_best_practices_guide-white-paper.pdf){: new_window}
  * [Nota da SAP 1943937 ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://launchpad.support.sap.com/#/notes/1943937){: new_window}
  * [Perguntas mais frequentes do SAP HANA Tailored Data Center Integration![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.sap.com/documents/2016/05/e8705aae-717c-0010-82c7-eda71af511fa.html){: new_window}
  * [Nota da SAP 1995460 ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://launchpad.support.sap.com/#/notes/1995460){: new_window}
  * [Nota da SAP 2024433 ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://launchpad.support.sap.com/#/notes/2024433){: new_window}
  * [Visão geral do SAP HANA Tailored Data Center Integration (TDI) ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://blogs.saphana.com/2015/02/18/sap-hana-tailored-data-center-integration-tdi-overview/){: new_window}
