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

# 1. ストレージの注文
{: #order_storage}

{{site.data.keyword.blockstoragefull}}、{{site.data.keyword.filestorage_full_notm}}、Network Attached Storage (NAS) の注文は、{{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} のデプロイ後に行います。 

## {{site.data.keyword.cloud_notm}} ストレージの注文
{: #ibm_storage}

[Provisioning and Managing {{site.data.keyword.blockstorageshort}}](https://console.bluemix.net/docs/infrastructure/BlockStorage/provisioning-block_storage.html#provisioning-and-managing-block-storage) か [Provisioning and Managing {{site.data.keyword.filestorage_full_notm}}](https://console.bluemix.net/docs/infrastructure/FileStorage/provisioning-file-storage.html#provisioning-and-managing-ibm-file-storage-for-ibm-cloud) の手順を実行して、バックアップ/リストア用のストレージ・ソリューションを注文してください。ガイドに従って、ストレージのタイプ、注文方法、サーバーへのデプロイ方法を決定するプロセスを進めていけます。

## NAS の注文
{: #order-nas}

データベースのアーカイブ・ログ・ファイルや頻繁なオンライン/オフライン・バックアップのストレージが必要な場合は、サーバーのローカル・ストレージのもう 1 つの重要な拡張機能として NAS ストレージを利用できます。[Ordering NAS/FTP Storage](https://console.bluemix.net/docs/infrastructure/network-attached-storage/index.html#ordering-nas-ftp-storage) のページにアクセスして、NAS の注文とセットアップの方法を確認してください。[Mounting NAS Storage in Linux](https://console.bluemix.net/docs/infrastructure/network-attached-storage/mount-nas-storage-linux.html#mounting-nas-storage-in-linux) も参照して、ネットワーク・ファイル・ストレージ (NFS) を Linux サーバーにマップする方法を確認してください。[NAS ストレージを NFS のデータ・ストアとして VMware ESXi にマップすることも可能です](https://console.bluemix.net/docs/infrastructure/network-attached-storage/connect-nas-storage-windows.html#connecting-to-nas-storage-in-windows)。

## 次のステップ

  [2. 環境の保護](/docs/infrastructure/sap-hana/hana-secure-environment.html)

  [3. ESX ハイパーバイザーへのゲスト OS のインストール (オプション)](/docs/infrastructure/sap-hana/hana-installing-guest-operating-system-VMware-deployments.html)

  [4. SAP ソフトウェア/アプリケーションのダウンロードとインストール](/docs/infrastructure/sap-hana/hana-installing-SAP-landscape.html)
  
  [5. {{site.data.keyword.cloud_notm}} データ・センターへの接続のテスト](/docs/infrastructure/sap-hana/hana-testing-connectivity.html)
