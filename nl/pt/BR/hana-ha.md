---

copyright:
  years: 2018, 2019
lastupdated: "2019-02-26"

keywords: SAP HANA, {{site.data.keyword.cloud_notm}}, high availability, highly available, SPOF, VLANs, HA, DR, disaster recovery, SAP NetWeaver

subcollection: sap-hana

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}


# Suporte de alta disponibilidade do IBM Cloud
{: #ha}

A infraestrutura como serviço (IaaS) do {{site.data.keyword.cloud}} oferece a você um ambiente de cálculo robusto, além de uma implementação de sistema operacional (S.O.) opcional que suporta soluções de alta disponibilidade (HA). A solução é baseada na versão de S.O. suportada, que é discutida em [Nota da SAP 2414097 ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://launchpad.support.sap.com/#/notes/2414097){: new_window}. A solução de alta disponibilidade está restrita às licenças de S.O. pedidas que vêm com sua implementação ou às licenças de terceiros, como Bring your own license (BYOL). Certifique-se de discutir detalhes sobre a alta disponibilidade com o Suporte do {{site.data.keyword.cloud_notm}} antes de sua implementação.

Os sistemas operacionais suportados e implementados pelo {{site.data.keyword.cloud_notm}} for SAP são
* O Linux [Red Hat Enterprise Linux (RHEL) ou SUSE Enterprise Linux Server (SLES)], que suporta ambas as soluções de alta disponibilidade: SAP NetWeaver e SAP HANA. Há restrições menores no ambiente do {{site.data.keyword.cloud_notm}}, que são discutidas em [Visão geral das configurações de alta disponibilidade do SAP NetWeaver](#overview-configs).
* O Microsoft Windows, que suporta somente a solução de alta disponibilidade SAP NetWeaver (devido às restrições do banco de dados SAP HANA).

## Visão geral das configurações de alta disponibilidade do SAP NetWeaver
{: #overview-configs}

Há inúmeros documentos que fornecem ajuda aprofundada sobre o planejamento e a instalação de um ambiente de alta disponibilidade para serviços SAP. Os documentos incluem informações sobre failover, replicação, ampliação e recuperação de desastre (DR). As referências a certos documentos são fornecidas onde apropriado.

Todos os sistemas operacionais e distribuições suportados pelo {{site.data.keyword.cloud_notm}} para uma implementação SAP (Windows, Linux RHEL e SLES) vêm com software de alta disponibilidade e extensões específicas. O S.O. e as distribuições suportados são apresentados a seguir.

* [Nova melhorias de armazenamento em cluster failover no Windows Server 2012 e seus benefícios para o SAP NetWeaver High Availability ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://blogs.sap.com/2013/10/16/new-failover-clustering-improvements-in-windows-server-2012-and-its-benefits-for-sap-netweaver-high-availability/){: new_window} fornece uma descrição com base no Microsoft Windows Server Failover Clustering (WFSC) no S.O. Windows com SAP NetWeaver.

* Há duas referências para orientação sobre a implementação do SAP NetWeaver em um ambiente de alta disponibilidade baseado em Linux com o Linux Pacemaker:
  * Guia de configuração do SUSE SAP NetWeaver High Availability Cluster 7.40
  * Implementando servidores baseados no SAP NetWeaver altamente disponíveis usando o complemento de alta disponibilidade do Red Hat Enterprise Linux com o Pacemaker

* [Construindo a alta disponibilidade para SAP NetWeaver e SAP HANA no Linux ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://support.sap.com/content/dam/SAAP/SAP_Activate/AGS_70.pdf){: new_window} é um documento de melhor prática da SAP e fornece uma descrição técnica aprofundada com um forte foco no SAP HANA.

* [Alta disponibilidade do SAP NetWeaver e continuidade de negócios em ambientes virtualizados com VMware e Hyper-V no Microsoft Windows ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://www.sap.com/documents/2015/07/508b62bc-5b7c-0010-82c7-eda71af511fa.html){: new_window} abrange os aspectos da virtualização caso você esteja planejando implementar a alta disponibilidade nos servidores virtualizados.

Para obter mais produtos de alta disponibilidade certificados por parceiros SAP para cenários de alta disponibilidade, consulte [Informações do parceiro de alta disponibilidade ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://wiki.scn.sap.com/wiki/display/SI/High+Availability+Partner+Information){: new_window}.
Para bancos de dados não SAP HANA, mais informações sobre failover de alta disponibilidade e configurações de DR estão disponíveis em sua documentação do banco de dados.

Observe que o acesso compartilhado ao armazenamento do Network File System (NFS)/Common Internet File System (CIFS) ou o acesso compartilhado a logical unique number storage (LUNS) baseado em iSCSI geralmente é necessário para suportar o failover do sistema. O armazenamento local, combinado com um método de replicação, geralmente é necessário para suportar uma configuração semelhante a DR. Assim como com instalações no local, verifique os requisitos de desempenho e latência do produto do banco de dados ao planejar sua implementação.

## Orientação extra
{: #extra-guide}

[Armazenamento baseado em quorum](#quorum) e [Considerações de rede](#network) fornecem orientação de que você precisa considerar durante sua implementação. Além das considerações descritas nessas seções, instalar o SAP NetWeaver e seu sistema de banco de dados em um ambiente de alta disponibilidade não difere de outras instalações no local.

### Armazenamento baseado em quorum
{: #quorum}

Devido a restrições de segurança no ambiente do {{site.data.keyword.cloud_notm}} IBM Cloud, o acesso baseado em rede a dispositivos de gerenciamento remoto por meio da Intelligent Platform Management Interface (IPMI) não está disponível. Os ambientes em cluster geralmente usam componentes baseados em IPMI para o “fence de nós do cluster” para sempre assegurar um quorum. Na falta de um dispositivo ativado para IPMI, os dispositivos de armazenamento compartilhado são usados. Em um ambiente do {{site.data.keyword.cloud_notm}}, os dispositivos de armazenamento compartilhado são implementados implementando um LUN do iSCSI a seus servidores como um dispositivo de quorum. Por exemplo, uma testemunha de compartilhamento de arquivos (FSW) em um Microsoft Cluster e para storage-based death (SDB) para Stonith do Linux Pacemaker.
* Clique [aqui ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](http://linux-ha.org/wiki/Cluster_Concepts){: new_window} para obter mais informações sobre Conceitos de cluster de alta disponibilidade.
* Clique [aqui ![Ícone de link externo](../../icons/launch-glyph.svg "Ícone de link externo")](https://docs.microsoft.com/en-us/windows-server/failover-clustering/manage-cluster-quorum){: new_window} para obter mais informações sobre configurar e gerenciar servidores de quorum para Windows Server 2012 e Windows Server 2012 R2.

O {{site.data.keyword.cloud_notm}} Storage possui recursos de alta disponibilidade integrados, portanto, um único LUN de iSCSI compartilhado não introduzirá um Ponto único de falha (SPOF), pois seu layout de rede é redundante. Entretanto, as especificações de seu produto de cluster podem requerer múltiplos dispositivos de quorum.

### Considerações sobre a Rede
{: #network}

Uma instalação baseada em {{site.data.keyword.cloud_notm}} vem com uma das configurações de rede a seguir:
* Rede privada
* Rede Pública
* Redes públicas e privadas
* Duas redes privadas (sob demanda especial)

Como instalações no local, os adaptadores de rede extras podem ser pedidos dependendo das restrições físicas do hardware. A restrição é a mesma para instalações no local. O pedido de adaptadores de rede redundantes durante implementações de hardware ajuda a evitar o SPOF em sua topologia de rede. Os adaptadores redundantes são configurados em uma configuração de failover com Link Aggregation Control Protocol (LACP). Para o Linux, a configuração usa interfaces de ligação, e os adaptadores de equipes são usados para o Microsoft Windows. A infraestrutura de comutador do {{site.data.keyword.cloud_notm}} à qual esses adaptadores estão conectados é redundante, portanto, nenhum novo SPOF é introduzido. A infraestrutura redundante pode ser usada pelas VLANs pedidas.

Dependendo dos requisitos de rede, como cenários de replicação em uma configuração de DR, deve-se verificar o local dos dispositivos conectados e quaisquer novos requisitos de rede específicos ao produto em questão. Em alguns casos, a replicação baseada em armazenamento da captura instantânea do {{site.data.keyword.cloud_notm}} pode preencher os requisitos. Verifique com o Suporte do {{site.data.keyword.cloud_notm}} para determinar qual solução melhor funciona para suas necessidades de processo de negócios.
