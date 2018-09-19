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

# 5. SAP HANA マルチノードをサポートする IBM Cloud インフラストラクチャーの構成
{: #multi-node-storage}

{{site.data.keyword.cloud_notm}} は、SAP Business Warehouse (SAP BW) や SAP BW/4HANA などのオンライン分析処理 (OLAP) ワークロードのための SAP HANA マルチノード・ストレージをサポートしています。SAP HANA マルチノード向けの {{site.data.keyword.cloud}} ソリューションは最大で 15 + 1 個のノード (15 個のワーカー・ノードのほかに 1 個のスタンバイ) で構成され、1 つのシステムで使用されるメモリーは最大で 30 TB です。

マルチノードでは、複数の SAP HANA ノードによって単一の SAP HANA システムが構築されます。データは、単一のデータベースを形成するこれらのノード間に分散されます。マルチノード構成は、スタンバイ構成によってスケーラビリティーと高可用性をサポートしています。この構成向けの {{site.data.keyword.cloud_notm}} オファリングは、[SAP HANA Tailored Data Center Integration](https://blogs.saphana.com/2015/02/18/sap-hana-tailored-data-center-integration-tdi-overview/) (TDI) に従い、{{site.data.keyword.cloud_notm}} の集中型共有エンタープライズ・ストレージのための SAP-HANA 認定サーバーを使用しています。

*注:* [マルチノード・システムの注文](#ordering)に概要が記載されている構成ガイドラインに従って、SAP HANA TDI の要件を満たし、SAP のサポートを受ける必要があります。

[Sizing SAP HANA](https://help.sap.com/viewer/eb3777d5495d46c5b2fa773206bbfb46/2.0.00/en-US/d4a122a7bb57101493e3f5ca08e6b039.html) に記載されるガイドラインに従い、ご使用のターゲット SAP HANA システムに必要なサイズ (デプロイメントに必要なメモリーとストレージの合計量を含む) を決定してください。サイジングの要件は、SAP HANA マルチノード・システムに必要な SAP HANA ノードの数と、データのホストに必要なストレージを設定するのに役立ちます。

## ネットワーク・トポロジーとストレージ・レイアウトの検討
{: #reviewing-topology}

図 1 は、{{site.data.keyword.cloud_notm}} Infrastructure as a Service SAP HANA TDI のセットアップに必要なネットワーク・トポロジーを示しています。

図 1. IBM Cloud Infrastructure as a Service SAP HANA TDI のネットワーク・トポロジー

![図 1. IBM Cloud Infrastructure as a Service SAP HANA TDI のネットワーク・トポロジー](/images/SAP-BW.png "IBM Cloud Infrastructure as a Service SAP HANA TDI のネットワーク・トポロジー")

## 前提条件のセットアップ
{: #prerequisites}

SAP HANA マルチノードでは、特定のネットワークが正しく機能するようになっている必要があります。ご使用のシステム用に他のコンポーネントを注文する前に、これらのネットワークがデータベース・ノードとともに正しく設定されている必要があります。以下が必要になります。
* クライアント・サイド・ネットワーク。これは、SAP Advanced Business Application Programming (SAP ABAP) アプリケーション・サーバー、SAP HANA Studio クライアント、およびその他のネットワーク・クライアントをマルチノード・システムに接続します。ネットワークのスループットと可用性のオプションは、SAP HANA マルチノード・システムの使用法シナリオによって異なります。ご使用のアプリケーションに必要とされる、SAP HANA データベースとの間のデータ転送量、および可用性の重要パフォーマンス指標 (KPI) を考慮してください。
* ストレージ・ネットワーク。これは、バックエンドの {{site.data.keyword.blockstoragefull}} と {{site.data.keyword.filestorage_full_notm}} への接続に必要です。パフォーマンスと冗長性を最大化するには、Link Aggregation Control Protocol (LACP) による Linux 結合の下に 2 つのインターフェースを備えた 10 GB のネットワークが必要です。SAP HANA のサイジング・ガイドラインから提供されたパフォーマンスの数値がない場合、SAP HANA TDI KPI を満たすことはできません。
* SAP HANA 内部通信用のノード間ネットワーク (ストレージ・ネットワークと同等にセットアップされたもの)。ノード間ネットワークは、ノード間の通信と、操作中にノード間で必要となることがあるデータ転送にのみ使用されます。この必要なネットワーク構成は、LACP による Linux 結合の下にある 2 つの物理的な 10 GB のアダプター上にあります。

## マルチノード・システムの注文
{: #ordering}

SAP で必要とされるパフォーマンスとスループットの KPI を満たすには、ご使用の VLAN、ストレージ、および計算ノードを同じデータ・センター内で注文する必要があります。コンポーネントが複数のデータ・センターに分散していると、SAP でマルチノード・システムがサポートされなくなります。

1. 3 つの異なる VLAN と、4 つのアダプター (プライベートが 2 つとパブリックが 2 つ) を使用するサーバーを注文します。VLAN の注文について詳しくは、[Step 1 Ordering Primary and Public VLANs](https://console.bluemix.net/docs/infrastructure/virtualization/advanced-single-site-vmware-reference-architecturesoftlayer.html#step-1-ordering-primary-public-and-private-vlans) を参照してください。サーバーの注文について詳しくは、[2. インフラストラクチャーのセットアップ](https://console.bluemix.net/docs/infrastructure/sap-hana/hana-setting-up-infrastructure.html#set_up_infrastructure)を参照してください。
2. 初期プライベート VLAN を「ストレージ VLAN」としてセットアップします。
3. {{site.data.keyword.cloud_notm}} サポートを使用して[チケットを開き](https://console.bluemix.net/docs/get-support/howtogetsupport.html#open-ticket)、以下を行います。
   a. パブリック・インターフェースを 2 番目の VLAN に移動する
   b. 3 番目の VLAN (クライアント VLAN) に割り当てるために、さらに 2 つのアダプターを注文する

これで、サイジング作業に基づいていくつかのサーバーが用意され、以下を目的としたネットワークがセットアップされました。
* ストレージをすべてのノードに接続できるようにする
* ストレージの接続後に SAP HANA マルチノード・インストールを実行できるようにする

ご使用のストレージ LAN 接続とノード間接続は、{{site.data.keyword.cloud_notm}} デプロイメントによって構成されます。必ず、双方にフェイルオーバーが構成されている 2 つの 10 GB アダプターを備えた接続を注文するようにしてください。このセットアップにより、Linux 結合と LACP 構成が正しく行われるようになります。不明な点があれば、{{site.data.keyword.cloud_notm}} サポート・チームにご連絡ください。

{{site.data.keyword.IBM_notm}} {{site.data.keyword.blockstorageshort}} (エンデュランス) と {{site.data.keyword.IBM_short}} {{site.data.keyword.filestorage_short}} (パフォーマンス) が満たさなければならない特定のパフォーマンス基準があります。データ・ボリュームの場合、ワーカー・ノードごとに、2 TB のエンデュランス・ストレージ (パフォーマンス KPI は 10 IOPS/GB) が必要です。SAP HANA 共有ストレージとして同じサイズのボリュームがさらに 1 つ必要になりますが、これはすべてのノードで共有されます。

ログ・ボリュームの場合は、ノードごとに、512 GB のパフォーマンス・ストレージ (パフォーマンス KPI は 10 K IOPS) のボリュームが 1 つ必要になります。

[{{site.data.keyword.blockstorageshort}} のプロビジョニングと管理](https://console.bluemix.net/docs/infrastructure/BlockStorage/provisioning-block_storage.html#provisioning-and-managing-block-storage)または[{{site.data.keyword.filestorage_full_notm}} のプロビジョニングと管理](https://console.bluemix.net/docs/infrastructure/FileStorage/provisioning-file-storage.html#provisioning-and-managing-ibm-file-storage-for-ibm-cloud)の手順を実行して、エンデュランスとパフォーマンス用のストレージを注文できます。

## SAP HANA マルチノードの構成
{: #configuring}

SAP HANA 共有ボリューム、およびそれぞれのデータとログのボリュームには、すべてのノードからアクセスできなければなりません。この方法は、[マルチノード・システムの注文](#ordering)で構成したストレージ VLAN 全体からすべてのボリュームにアクセスできることを意味します。関連する各 IP アドレスをリストしないようにする場合は、VLAN の IP サブネット全体からそのボリュームにアクセスできるようにします。

[SAP HANA on NetApp FAS Systems with NFS](https://www.netapp.com/us/media/tr-4290.pdf) のガイダンスに従って、SAP HANA マルチノード・システムを構成します。マウントする各ボリュームについて、以下のネットワーク・ファイル・システム (NFS) のマウント・オプションを使用します。

`/etc/fstab` で `rw,bg,hard,timeo=600,intr,noatime,vers=4,minorversion=1,lock,rsize=1048576,wsize=1048576`。

これらのオプションは、NetApp と {{site.data.keyword.cloud_notm}} でテスト済みです。マウント・オプションや値を変更する計画がある場合は、{{site.data.keyword.cloud_notm}} サポートにご連絡ください。

すべてのノードにすべてのボリュームをマウントすると、マルチノード・サーバーが構成され、SAP HANA マルチノード・データベースをインストールする準備が整います。[SAP HANA Server Installation and Update Guide](https://help.sap.com/viewer/2c1988d620e04368aa4103bf26f17727/2.0.03/en-US) の手順に従って、必要なバージョンの SAP HANA データベースをインストールします。
