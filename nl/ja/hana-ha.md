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


# IBM Cloud 高可用性サポート
{: #ha}

{{site.data.keyword.cloud}} Infrastructure as a Service (IaaS) は、堅固なコンピュート環境に加えて、高可用性 (HA) ソリューションをサポートするオプションのオペレーティング・システム (OS) デプロイメントを提供します。このソリューションは、サポートされる OS のバージョンに基づいています。これについては、[SAP Note 2414097 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://launchpad.support.sap.com/#/notes/2414097){: new_window} で説明されています。HA ソリューションで提供される機能は、デプロイメント時に注文した OS ライセンス、またはライセンス持ち込み (BYOL) などのサード・パーティー・ライセンスで許可された機能に限定されます。デプロイを行う前に、HA の詳細を {{site.data.keyword.cloud_notm}} サポートと相談してください。

SAP のために {{site.data.keyword.cloud_notm}} によってサポートされ、デプロイされるオペレーティング・システムは、以下のとおりです。
* Linux [Red Hat Enterprise Linux (RHEL) または SUSE Enterprise Linux Server (SLES)] は、SAP NetWeaver と SAP HANA HA の両方のソリューションをサポートします。{{site.data.keyword.cloud_notm}} 環境には、少しの制約事項があります。それらについては、[SAP NetWeaver 高可用性構成の概要](#overview-configs)で説明されています。
* Microsoft Windows は、SAP NetWeaver HA ソリューションだけをサポートします (SAP HANA データベースの制約事項のため)。

## SAP NetWeaver 高可用性構成の概要
{: #overview-configs}

SAP サービス用に HA 環境を計画してインストールする方法については、多くの資料で詳しく解説されています。それらの資料には、フェイルオーバー、レプリケーション、スケールアウト、災害復旧 (DR) に関する情報が記載されています。必要に応じて、特定の資料を参照するように記載しています。

{{site.data.keyword.cloud_notm}} によってサポートされる SAP デプロイメント用のすべてのオペレーティング・システムとディストリビューション (Windows、Linux RHEL、および SLES) には、高可用性ソフトウェアと特定の拡張機能が付属しています。以下は、サポートされる OS とディストリビューションです。

* [New Failover Clustering Improvements in Windows Server 2012 and Its Benefits for SAP NetWeaver High Availability ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://blogs.sap.com/2013/10/16/new-failover-clustering-improvements-in-windows-server-2012-and-its-benefits-for-sap-netweaver-high-availability/){: new_window} には、SAP NetWeaver で提供される、Windows OS での Microsoft Windows Server Failover Clustering (WFSC) に基づく説明が記載されています。

* Linux Pacemaker で Linux ベースの HA 環境に SAP NetWeaver をデプロイするためのガイダンスとして、2 つの参照資料があります。
  * SUSE SAP NetWeaver High Availability Cluster 7.40 Setup Guide
  * Deploying Highly Available SAP NetWeaver-based Servers Using Red Hat Enterprise Linux HA add-on with Pacemaker

* [Building High Availability for SAP NetWeaver and SAP HANA on Linux ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://support.sap.com/content/dam/SAAP/SAP_Activate/AGS_70.pdf){: new_window} は、SAP のベスト・プラクティスを示す資料で、主に SAP HANA に注目した技術的な詳しい説明が記載されています。

* [SAP NetWeaver High Availability and Business Continuity in Virtual Environments with VMware and Hyper-V on Microsoft Windows ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.sap.com/documents/2015/07/508b62bc-5b7c-0010-82c7-eda71af511fa.html){: new_window} は、HA を仮想化サーバーに実装する計画を立てる場合の、仮想化に関する事柄を扱っています。

高可用性シナリオのために SAP パートナーによって認証されたその他の高可用性製品については、[High Availability Partner Information ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://wiki.scn.sap.com/wiki/display/SI/High+Availability+Partner+Information){: new_window} を参照してください。
HANA ではない SAP データベースについては、ご使用のデータベースの資料の中で HA フェイルオーバーと DR 構成に関する詳細情報を確認してください。

システム・フェイルオーバーをサポートするためには、通常、Network File System (NFS)/Common Internet File System (CIFS) ストレージへの共有アクセス、または iSCSI ベースの論理固有番号ストレージ (LUNS) への共有アクセスが必要になることに注意してください。DR のようなセットアップをサポートするためには、通常、ローカル・ストレージと何らかのレプリケーション方式をセットで用意することが必要です。オンプレミス・インストールの場合と同様に、デプロイメントを計画するときには、データベース製品のパフォーマンスと待ち時間に関する要件を確認してください。

## その他の指針
{: #extra-guide}

[クォーラム・ベースのストレージ](#quorum)と[ネットワークに関する考慮事項](#network)では、デプロイを行う際に検討する必要のある指針が記載されています。これらのセクションで説明されている考慮事項を除いて、SAP NetWeaver とそのデータベース・システムを HA 環境にインストールする作業は、他のオンプレミス・インストールの作業と異なる点はありません。

### クォーラム・ベースのストレージ
{: #quorum}

{{site.data.keyword.cloud_notm}} IBM Cloud 環境でのセキュリティー上の制限のために、Intelligent Platform Management Interface (IPMI) によるリモート管理デバイスへのネットワーク・アクセスは使用できません。クラスター環境では、クォーラムを常に確保するために、通常は「クラスター・ノードを隔離」するための IPMI ベースのコンポーネントが使用されます。IPMI 対応のデバイスが存在しない場合は、共有ストレージ・デバイスが使用されます。{{site.data.keyword.cloud_notm}} 環境で、共有ストレージ・デバイスは、iSCSI LUN をクォーラム・デバイスとしてサーバーにデプロイすることによって実装されます。例えば、Microsoft クラスター上のファイル共有監視 (FSW) や Linux Pacemaker の Stonith 用のストレージ・ベース・デス (SDB) などがあります。
* Linux 高可用性クラスターの概念について詳しくは、[ここ ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](http://linux-ha.org/wiki/Cluster_Concepts){: new_window} をクリックしてください。
* Windows Server 2012 と Windows Server 2012 R2 でクォーラム・サーバーを構成して管理する方法について詳しくは、[ここ ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://docs.microsoft.com/en-us/windows-server/failover-clustering/manage-cluster-quorum){: new_window} をクリックしてください。

{{site.data.keyword.cloud_notm}} Storage には HA 機能が組み込まれていて、ネットワーク・レイアウトが冗長であるため、共有 iSCSI LUN が 1 つであっても Single Point Of Failure (SPOF) は発生しません。ただし、クラスター製品の仕様により、複数のクォーラム・デバイスが必要になる場合があります。

### ネットワークに関する考慮事項
{: #network}

{{site.data.keyword.cloud_notm}} ベースのインストール済み環境には、以下のいずれかのネットワーク構成があります。
* プライベート・ネットワーク
* パブリック・ネットワーク
* パブリック・ネットワークとプライベート・ネットワーク
* 2 つのプライベート・ネットワーク (特別な要求がある場合)

オンプレミス・インストールのときのように、ハードウェアの物理的な制限に応じて、追加のネットワーク・アダプターを注文できます。この制限は、オンプレミス・インストールの場合と同じです。ハードウェアをデプロイする際に冗長なネットワーク・アダプターを注文すると、ネットワーク・トポロジー全体で SPOF を防止する上で役立ちます。冗長なアダプターは、Link Aggregation Control Protocol (LACP) によるフェイルオーバー構成でセットアップされます。このセットアップにおいて、Linux では結合インターフェースが使用され、Microsoft Windows ではチーム・アダプターが使用されます。これらのアダプターが接続されている {{site.data.keyword.cloud_notm}} スイッチ・インフラストラクチャーは冗長なので、新しい SPOF は発生しません。冗長なインフラストラクチャーは、注文済みの VLAN で使用できます。

DR セットアップでのレプリケーション・シナリオなどのネットワーク要件に応じて、接続しているデバイスの場所、および対象製品に固有の新しいネットワーク要件を確認する必要があります。場合によっては、{{site.data.keyword.cloud_notm}} スナップショット・ストレージ・ベースのレプリケーションにより、要件が満たされることがあります。{{site.data.keyword.cloud_notm}} サポートに問い合わせて、お客様のビジネス・プロセスでの必要に最適なソリューションを判断してください。
