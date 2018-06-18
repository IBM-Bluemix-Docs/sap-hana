---



copyright:
  years: 2018
lastupdated: "2018-02-12"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 1. Pedindo armazenamento
{: #order_storage}

O {{site.data.keyword.blockstoragefull}}, o {{site.data.keyword.filestorage_full_notm}} e o Network Attached Storage (NAS) são pedidos depois de implementar seus {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}}. 

## Pedindo armazenamento do {{site.data.keyword.cloud_notm}}
{: #ibm_storage}

É possível usar as etapas em [Provisionando e gerenciando o {{site.data.keyword.blockstorageshort}}](https://console.bluemix.net/docs/infrastructure/BlockStorage/provisioning-block_storage.html#provisioning-and-managing-block-storage) ou [Provisionando e gerenciando o {{site.data.keyword.filestorage_full_notm}}](https://console.bluemix.net/docs/infrastructure/FileStorage/provisioning-file-storage.html#provisioning-and-managing-ibm-file-storage-for-ibm-cloud) para pedir sua solução de armazenamento de backup e restauração. Você é guiado pelo processo de decidir qual tipo de armazenamento usar, como pedi-lo e como implementá-lo em seu servidor.

## Pedindo o NAS
{: #order-nas}

O armazenamento NAS pode ser outra extensão de valor do armazenamento local de seu servidor se você precisar de armazenamento para arquivos de log arquivado do seu banco de dados ou backups on-line e off-line frequentes. Visite [Pedindo armazenamento NAS/FTP](https://console.bluemix.net/docs/infrastructure/network-attached-storage/index.html#ordering-nas-ftp-storage) para pedir e configurar o NAS. Além disso, referencie [Montando o armazenamento NAS no Linux](https://console.bluemix.net/docs/infrastructure/network-attached-storage/mount-nas-storage-linux.html#mounting-nas-storage-in-linux) para ver como mapear o network file storage (NFS) para seu servidor Linux. [O armazenamento NAS também pode ser mapeado para o VMware ESXi como um armazenamento de dados por meio do NFS](https://console.bluemix.net/docs/infrastructure/network-attached-storage/connect-nas-storage-windows.html#connecting-to-nas-storage-in-windows).

## Próximas Etapas

  [2. Assegurando seu ambiente](/docs/infrastructure/sap-hana/hana-secure-environment.html)

  [3. Instalando seu S.O. guest no hypervisor ESX (opcional)](/docs/infrastructure/sap-hana/hana-installing-guest-operating-system-VMware-deployments.html)

  [4. Fazendo download e instalando softwares e aplicativos SAP](/docs/infrastructure/sap-hana/hana-installing-SAP-landscape.html)
  
  [5. Testando a conectividade com o seu data center do {{site.data.keyword.cloud_notm}}](/docs/infrastructure/sap-hana/hana-testing-connectivity.html)
