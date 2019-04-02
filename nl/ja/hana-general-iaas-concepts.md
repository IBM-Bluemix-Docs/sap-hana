---

copyright:
  years: 2017, 2019
lastupdated: "2019-02-26"

keywords: SAP HANA, {{site.data.keyword.cloud_notm}}, {{site.data.keywords.baremetal_short}}, data centers, VPN,

subcollection: sap-hana

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

詳しくは、[Data Centers ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.ibm.com/cloud-computing/bluemix/data-centers){: new_window} を参照してください。

## ベア・メタル・サーバー

{{site.data.keyword.baremetal_long}} は、カスタマイズ機能が限定されている物理サーバーです。 このサーバーはお客様専用またはお客様の顧客専用で、{{site.data.keyword.cloud_notm}} の他のお客様とは (サーバー・リソースも含めて) どの部分も共有されません。お客様が選択したオペレーティング・システム (OS) を実行する物理サーバー全体としてプロビジョニングされます。 SAP HANA オファリング向けのオペレーティング・システムは、Red Hat Enterprise Linux 7.4 for SAP HANA、SUSE Linux Enterprise Server 12 SP2 for SAP HANA、および VMware Server Virtualization 6.5 です。

ベア・メタル・サーバーではカスタマイズ機能が限定されているので、プロビジョニングにかかる時間が短くなっています (1 時間から 4 時間程度です)。 このような高速プロビジョニングは、競合他社に先駆けてアプリケーションを市場に送り出すのに役立ちます。

SAP 認証サーバーでは、RAM の量と CPU の数が事前に設定されていて、RAM と CPU の組み合わせが各種用意されています。 注文プロセスでも、サーバー・デプロイ後のサポート・チケットでも、その組み合わせを変更することは*できません*。

詳細については、[ベア・メタル・サーバーについて](/docs/bare-metal?topic=bare-metal-about#about)を参照してください。

## ネットワーク接続

{{site.data.keyword.cloud_notm}} アカウントがセットアップされると、{{site.data.keyword.cloud_notm}} 仮想クラウド・ネットワークへの仮想プライベート・ネットワーク (VPN) 接続が自動的に許可されます。 サーバーにはデフォルトで、パブリック IP アドレスとプライベート IP アドレスがあります。 サーバーをプライベートにする場合は、サーバーのプロビジョニング後にパブリック・インターフェースをオフにするか、サーバーをプライベートとして注文してください。

SAP HANA のネットワーク要件 (10 Gb 冗長ネットワーク) は、{{site.data.keyword.cloud_notm}} オファリングによって実現されますが、アプリケーションのシナリオによっては、待ち時間とスループットに関する一定の重要パフォーマンス指標 (KPI) を満たすことが必要になる場合もあります。 SAP HANA サーバーを配置するデータ・センターと最適なネットワーク接続ソリューションを選定するための詳細情報については、[ネットワーク接続](/docs/infrastructure/sap-hana?topic=sap-hana-considerations#network_connectivity)の注意点を参照してください。

詳しくは、[仮想プライベート・ネットワーキング (VPN) の概要](/docs/infrastructure/iaas-vpn?topic=VPN-getting-started-with-virtual-private-networking-vpn-#getting-started-with-virtual-private-networking-vpn-)および [*SAP HANA Network Requirements* ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.sap.com/documents/2016/08/1cd2c2fb-807c-0010-82c7-eda71af511fa.html){: new_window} のホワイト・ペーパーを参照してください。

## ストレージ
{: #storage}

{{site.data.keyword.baremetal_short}} には、ローカル・ストレージが用意されています。ローカル・ストレージでは、{{site.data.keyword.cloud_notm}} のプライベート・ネットワーク仮想 LAN (VLAN) を使用するので、管理者権限を妨害しないエンタープライズ・グレードのセキュリティーを実現することが可能になります。 SAP HANA 認定サーバーの場合、ローカル・ストレージは、スループットと待ち時間について SAP が定めた KPI に、SAP HANA 認定基準に準拠して適合する設計/構成になっています。 ローカル・ストレージには、各サブファイル・システム (`data.log` と `shared`) に対応するサイズがあり、それぞれのサイズが SAP HANA Installation Guide で定められています。 お客様の側でそれ以上の調整を行う必要はありません。

{{site.data.keyword.cloud_notm}} には、2 種類のストレージ (ブロックとファイル) があります。SAP HANA のバックアップとリストアのためにどちらかのストレージを選択できます。 どちらのタイプの場合も、IOPS (1 秒あたりの入出力操作) に基づいてストレージ必要量を判別します。 IOPS の計測は、16 KB ブロック・サイズと 50/50 の読み取り/書き込み混合比率に基づいています。 1 つのボリュームで最大の IOPS を達成するために、適切なネットワーク・リソースを用意する必要があります。 その他の注意点としては、ストレージやホスト・サイドの外部でのプライベート・ネットワーク使用量や、アプリケーション固有の調整 (IP スタックやキュー項目数など) があります。 詳細については、[Getting started with Block Storage](/docs/infrastructure/BlockStorage?topic=BlockStorage-GettingStarted#GettingStarted) と [Getting started with File Storage](/docs/infrastructure/FileStorage?topic=FileStorage-GettingStarted#getting-started-with-file-storage) を参照してください。

## デプロイメントと管理

{{site.data.keyword.cloud_notm}} カスタマー・アカウントを作成してから、{{site.data.keyword.cloud_notm}} のインフラストラクチャー・カスタマー・ポータルか API を使用して {{site.data.keyword.cloud_notm}} {{site.data.keyword.baremetal_short}} をデプロイします。 サーバーの管理は、カスタマー・ポータル、API、コマンド・ライン・インターフェース (CLI) のいずれかによって実行できます。 詳細については、[ベア・メタル・サーバーについて](/docs/bare-metal?topic=bare-metal-about#about)を参照してください。

## サポート

[{{site.data.keyword.cloud_notm}}カスタマー・サポート](/docs/get-support?topic=get-support-getting-customer-support#getting-customer-support)は、さまざまな方法 (チャット、電話、チケット・ベースのサポートなど) で、サポートに関する問い合わせや問題に対応しています。 ほとんどのチケットを 1 日以内にカバーしています。{{site.data.keyword.cloud_notm}} のすべてのお客様がカスタマー・サポートを無料で利用できます。 詳細については、[必要なサポートを利用するには](/docs/get-support?topic=get-support-getting-customer-support#getting-customer-support)を参照してください。

SAP サポートでお客様の {{site.data.keyword.cloud_notm}} IaaS や SAP 製品に関連したチケットを今後も作成できます。 詳しくは、[SAP Support ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://support.sap.com/en/index.html){: new_window} および [SAP Note 2414820 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://launchpad.support.sap.com/#/notes/2414820){: new_window} を参照してください。

## SAP HANA のインストール

SAP HANA ソフトウェアは、SAP HANA インストールの認定コースを修了した認定 SAP HANA インストーラーがインストールする必要があります。 詳しくは、[Who Can Install SAP HANA? ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://www.saphanacentral.com/p/who-can-install-sap-hana.html){: new_window} を参照してください。
