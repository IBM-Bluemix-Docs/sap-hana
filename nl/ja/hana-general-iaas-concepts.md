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

# SAP HANA on IBM Cloud IaaS の概要
{: #iaas-overview}

Infrastructure as a Server (IaaS) 環境は、さまざまなコンポーネント (データ・センター、コンピュート、接続性、ストレージ、ネットワーク) で構成されています。 

## データ・センター

南北アメリカ、ヨーロッパ、アジア、オーストラリアのデータ・センターを利用して、必要な場所で (必要な時に) クラウド・リソースをプロビジョニングできます。 各データ・センターは {{site.data.keyword.cloud_notm}} のグローバルなプライベート・ネットワークに接続されているので、世界のどこからでも効率的にデータを高速転送できます。

詳細については、[データ・センター](https://www.ibm.com/cloud-computing/bluemix/data-centers){: new_window}を参照してください。

## ベア・メタル・サーバー

{{site.data.keyword.baremetal_long}} は、カスタマイズ機能が限定されている物理サーバーです。 このサーバーはお客様専用またはお客様の顧客専用で、{{site.data.keyword.cloud_notm}} の他のお客様とは (サーバー・リソースも含めて) どの部分も共有されません。お客様が選択したオペレーティング・システム (OS) を実行する物理サーバー全体としてプロビジョニングされます。 SAP HANA オファリング向けのオペレーティング・システムは、Red Hat Enterprise Linux 7.4 for SAP HANA、SUSE Linux Enterprise Server 12 SP2 for SAP HANA、および VMware Server Virtualization 6.5 です。

ベア・メタル・サーバーではカスタマイズ機能が限定されているので、プロビジョニングにかかる時間が短くなっています (1 時間から 4 時間程度です)。 このような高速プロビジョニングは、競合他社に先駆けてアプリケーションを市場に送り出すのに役立ちます。

SAP 認証サーバーでは、RAM の量と CPU の数が事前に設定されていて、RAM と CPU の組み合わせが各種用意されています。 注文プロセスでも、サーバー・デプロイ後のサポート・チケットでも、その組み合わせを変更することは*できません*。

詳細については、[ベア・メタル・サーバーについて](https://console.bluemix.net/docs/bare-metal/about.html#about-bare-metal-servers)を参照してください。 

## ネットワーク接続

{{site.data.keyword.cloud_notm}} アカウントがセットアップされると、{{site.data.keyword.cloud_notm}} 仮想クラウド・ネットワークへの仮想プライベート・ネットワーク (VPN) 接続が自動的に許可されます。 サーバーにはデフォルトで、パブリック IP アドレスとプライベート IP アドレスがあります。 サーバーをプライベートにする場合は、サーバーのプロビジョニング後にパブリック・インターフェースをオフにするか、サーバーをプライベートとして注文してください。 

SAP HANA のネットワーク要件 (10 Gb 冗長ネットワーク) は、{{site.data.keyword.cloud_notm}} オファリングによって実現されますが、アプリケーションのシナリオによっては、待ち時間とスループットに関する一定の重要パフォーマンス指標 (KPI) を満たすことが必要になる場合もあります。 SAP HANA サーバーを配置するデータ・センターと最適なネットワーク接続ソリューションを選定するための詳細情報については、[ネットワーク接続](/docs/infrastructure/sap-hana/hana-considerations.html#network_connectivity)の注意点を参照してください。

詳細については、[Getting started with Virtual Private Networking](https://console.bluemix.net/docs/infrastructure/iaas-vpn/getting-started.html#getting-started-with-virtual-private-networking-vpn-) と [*SAP HANA Network Requirements*](https://www.sap.com/documents/2016/08/1cd2c2fb-807c-0010-82c7-eda71af511fa.html) のホワイト・ペーパーを参照してください。

## ストレージ
{: #storage}

{{site.data.keyword.baremetal_short}} には、ローカル・ストレージが用意されています。ローカル・ストレージでは、{{site.data.keyword.cloud_notm}} のプライベート・ネットワーク仮想 LAN (VLAN) を使用するので、管理者権限を妨害しないエンタープライズ・グレードのセキュリティーを実現することが可能になります。 SAP HANA 認定サーバーの場合、ローカル・ストレージは、スループットと待ち時間について SAP が定めた KPI に、SAP HANA 認定基準に準拠して適合する設計/構成になっています。 ローカル・ストレージには、各サブファイル・システム (`data.log` と `shared`) に対応するサイズがあり、それぞれのサイズが SAP HANA Installation Guide で定められています。 お客様の側でそれ以上の調整を行う必要はありません。

{{site.data.keyword.cloud_notm}} には、2 種類のストレージ (ブロックとファイル) があります。SAP HANA のバックアップとリストアのためにどちらかのストレージを選択できます。 どちらのタイプの場合も、IOPS (1 秒あたりの入出力操作) に基づいてストレージ必要量を判別します。 IOPS の計測は、16 KB ブロック・サイズと 50/50 の読み取り/書き込み混合比率に基づいています。 1 つのボリュームで最大の IOPS を達成するために、適切なネットワーク・リソースを用意する必要があります。 その他の注意点としては、ストレージやホスト・サイドの外部でのプライベート・ネットワーク使用量や、アプリケーション固有の調整 (IP スタックやキュー項目数など) があります。 詳細については、[Getting started with Block Storage](https://console.bluemix.net/docs/infrastructure/BlockStorage/index.html#getting-started-with-block-storage) と [Getting started with File Storage](https://console.bluemix.net/docs/infrastructure/FileStorage/index.html#getting-started-with-file-storage) を参照してください。

デバイスのバックアップのためにコスト効率の高い高速のソリューションを探している場合は、{{site.data.keyword.cloud_notm}} の Network Attached Storage (NAS) を利用できます。 NAS は、ネットワーク・ファイル・システム (NFS) にマウントすることも、Parallels Plesk Panel や cPanel@WHM のファイル転送プロトコル (FTP) で使用することもできます。

NAS ストレージはどんな目的のためにも使用できますが、この場合に限って言えば、SAP HANA のデータ・ファイルやログ・ファイルのためには使用*しないでください*。 このストレージは、入出力 KPI の基準に適合していません。 ただし、このストレージをバックアップ・デバイスとして使用したり、他のすべての種類のデータのために使用したりするのは可能です。 NFS にマウントした場合は、SAP HANA でも、バックアップ・デバイスとして使用したり、データ・ファイルやログ・ファイルのために使用したりして構いません。  
  
NAS と FTP のストレージは月次払いになっていて、さまざまなストレージ・サイズがあります。 NAS と FTP のストレージの操作は、主に OS のコマンド・ラインやターミナルから実行できます。{{site.data.keyword.cloud_notm}} インフラストラクチャー・カスタマー・ポータルのパネルでポイント操作やクリック操作によって利用することも可能です。 カスタマー・ポータルでは、NAS の詳細情報や使用状況を確認できますが、コマンド・ラインやカーネルやコントロール・パネルの外部でこのサービスを操作することはできません。

{{site.data.keyword.cloud_notm}} 環境で NAS を使用するための詳細情報については、[Getting started with NAS](https://console.bluemix.net/docs/infrastructure/network-attached-storage/index.html#getting-started-with-nas) を参照してください。

## デプロイメントと管理

{{site.data.keyword.cloud_notm}} カスタマー・アカウントを作成してから、{{site.data.keyword.cloud_notm}} のインフラストラクチャー・カスタマー・ポータルか API を使用して {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} をデプロイします。 サーバーの管理は、カスタマー・ポータル、API、コマンド・ライン・インターフェース (CLI) のいずれかによって実行できます。 詳細については、[ベア・メタル・サーバーについて](https://console.bluemix.net/docs/bare-metal/about.html#about-bare-metal-servers)を参照してください。

## サポート

[{{site.data.keyword.cloud_notm}}カスタマー・サポート](https://console.bluemix.net/docs/support/index.html#getting-customer-support)は、さまざまな方法 (チャット、電話、チケット・ベースのサポートなど) で、サポートに関する問い合わせや問題に対応しています。 ほとんどのチケットを 1 日以内にカバーしています。{{site.data.keyword.cloud_notm}} のすべてのお客様がカスタマー・サポートを無料で利用できます。 詳細については、[必要なサポートを利用するには](https://console.bluemix.net./docs/support/index.html#getting-customer-support)を参照してください。

SAP サポートでお客様の {{site.data.keyword.cloud_notm}} IaaS や SAP 製品に関連したチケットを今後も作成できます。 詳細については、[SAP Support](https://support.sap.com/en/index.html) と [SAP Note 2414820](https://launchpad.support.sap.com/#/notes/2414820) を参照してください。

## SAP HANA のインストール

SAP HANA ソフトウェアは、SAP HANA インストールの認定コースを修了した認定 SAP HANA インストーラーがインストールする必要があります。 詳細については、[Who Can Install SAP HANA?](http://www.saphanacentral.com/p/who-can-install-sap-hana.html) を参照してください。
