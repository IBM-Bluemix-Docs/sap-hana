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

# SAP ランドスケープの計画時の考慮事項
{: #considerations}

ランドスケープ内の SAP システムでは、内部のシステム間の接続についても、外部システムとの接続についても、固有の要件があります。 ランドスケープの外部ストレージについても考慮する必要があります。サーバーに VMware をデプロイする場合は、行うべき作業についても考慮が必要です。

## ネットワーク接続
{: #network_connectivity}

[{{site.data.keyword.cloud_notm}} ネットワーク](/docs/infrastructure/sap-hana?topic=sap-hana-about_ibmcloud_for_sap#ibm_cloud_network)で、{{site.data.keyword.cloud}} 方式のネットワーク接続の概要を確認できます。 システムの使用方法に関係なく、ネットワーク接続を適切に計画していないと、その問題が原因になってプロジェクトが大きく遅れるおそれがあります。

一般に、IaaS 方式でプロビジョニングする {{site.data.keyword.cloud_notm}} サーバーのインターフェースについては、2 つのオプションがあります。1 つ目は、パブリック IP を使用する外部インターフェースです。 2 つ目は、Request for Comment (RFC) 1918 に準拠したプライベート IP を使用する内部インターフェースです。 プライベート IP を使用する単一の内部インターフェースを選択することも可能です。 外部 IP の方が使いやすいかもしれませんが、こちらは基本的なファイアウォールがインストールされていて事前に構成されていても、潜在的なリスクがあります。

2 つ目のオプションの場合は、{{site.data.keyword.cloud_notm}} インフラストラクチャー・カスタマー・ポータルから {{site.data.keyword.cloud_notm}} 仮想プライベート・ネットワーク (VPN) にアクセスするか、お客様のランドスケープにセキュリティー・デバイスをデプロイすることになります。 ファイアウォール、ネットワーク・アドレス変換、VPN アクセス、その他のネットワーク機能用に、セキュリティー・デバイスが提供されています。 ランドスケープのレイアウトや SAP アプリケーション層で必要な接続が確定した後に、お客様のネットワーキング部門のスタッフが [{{site.data.keyword.cloud_notm}}サポート](/docs/get-support?topic=get-support-getting-customer-support#getting-customer-support)と話し合うことをお勧めします。

### VLAN
{: #vlans}

ランドスケープ内の異なるタイプのネットワーク・トラフィックを区別する場合は、追加の仮想 LAN (VLAN) を注文できます。 ただし、VLAN を追加したとしても、トラフィックの分離が可能になるだけで、パフォーマンスが向上するわけではありません。 SAP では通常、アプリケーション・サーバーと SAP HANA データベースの間のトラフィックや、SAP Business Intelligence などの他の SAP HANA クライアントのトラフィックのために、10 Gb のネットワークを使用することを推奨しています。 SAP HANA サーバーへの管理アクセスを他のクライアントから分離する場合は、ランドスケープで使用する VLAN をもう 1 つ注文する必要があります。 もう 1 つのオプションは、パブリック・ネットワークのトラフィックとプライベート・ネットワークのトラフィックを分離することです。それ以上の「物理」アップリンクは、{{site.data.keyword.cloud_notm}} ではサポートされていません。 [SAP HANA Tailored Data Center Integration (TDI) ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://blogs.saphana.com/2015/02/18/sap-hana-tailored-data-center-integration-tdi-overview/){: new_window} で SAP の推奨事項を確認して実行してください。

VPN によるアクセスでもジャンプボックスからのアクセスでも、SAP HANA Studio から SAP HANA インスタンスに透過的にアクセスすることが可能です。

## 外部ストレージ
{: #external_storage}

ローカル・ストレージのほかに、バックアップを実行するための外部ストレージがさらに必要になることもあります。 その要件がある場合は、ブロック・ストレージか Network Attached Storage (NAS) を注文できます ([ストレージ](/docs/infrastructure/sap-hana?topic=sap-hana-iaas-overview#storage)を参照)。 追加のブロック・ストレージとネットワーク・ファイル・システム (NFS) のデータは、他のすべてのネットワーク・トラフィックと同じ物理アダプターで転送されるので、その影響を考慮に入れておく必要があります。

外部ストレージについては、プロジェクト要件を計算してからストレージ・ソリューションを決定することが重要になります。 SAP HANA システムをリストアする必要がある場合、ストレージの IOPS によってリストア時間枠が大きな影響を受けます。 バックアップ時間枠は、SAP HANA にとってそれほど重要ではありません。SAP HANA の構成方法とは無関係に、すべてのバックアップがオンライン・バックアップになるからです。

例えば、{{site.data.keyword.cloud_notm}} {{site.data.keyword.blockstorageshort}} を使用する場合は、最大速度での SAP HANA のリストアを約 12 TB として計算できます。 デバイスごとの最大サイズは 4 TB なので、3 つの物理ストレージ・デバイス (ブロック・ストレージ iSCSI LUN) を作成する必要があります。 Linux 論理ボリューム・マネージャーを使用してその 3 つのデバイスでストライプを構成し、12 TB の論理デバイスを 1 つ作成することも可能です。

12 TB では、3x10 IOPS/GB が可能になります。つまり、合計 122,880 IOPS/GB (16 KB) です。 その場合のリストア時間は、1 秒あたり 1.875 GB になり、合計リストア時間は 2 時間未満になります。 IOPS の測定値は、読み取りと書き込みの配分比率が 50/50 であることを前提にしているので、この数値をリストア・パフォーマンスの下限と見なせます。 特定のリストア時間枠に依存する場合は、バックアップとリストアのテストを実行することをお勧めします。

{{site.data.keyword.cloud_notm}} {{site.data.keyword.blockstorageshort}}、{{site.data.keyword.filestorage_full_notm}}、NAS のいずれも、バックアップ・スペースとしての役割と、サーバーにインストールする追加のソフトウェア・コンポーネントのストレージとしての役割の両方を果たせます。 ただし、{{site.data.keyword.cloud_notm}} ストレージと NSA を SAP HANA のストレージとして使用することはできません。どちらのオプションも KPI の基準を満たしていないからです。

詳細については、[Getting started with {{site.data.keyword.blockstorageshort}}](/docs/infrastructure/BlockStorage?topic=BlockStorage-GettingStarted#GettingStarted) と [Getting started with {{site.data.keyword.filestorage_full_notm}}](/docs/infrastructure/FileStorage?topic=FileStorage-GettingStarted#getting-started-with-file-storage) を参照してください。

## 高可用性と災害復旧のシナリオ
{: #ha_dr}

{{site.data.keyword.cloud_notm}} 環境には、事前構成の高可用性 (HA) シナリオのサポートはありません。 それでも、Red Hat Enterprise Linux HA 拡張機能を使用して SAP HANA の HA ソリューションを実装することは可能です (オンプレミスの場合など) 。

サーバーからレプリカへの自動フェイルオーバー機能を備えた、SAP HANA システムの複製を構成できます。 システムの複製に関する SAP 資料を参照し、お客様のアプリケーション・シナリオと災害回復力レベルに最適なレプリケーション・モードを選定してください。 複製モードによっては、別のネットワーク KPI に対応することが必要になります。 ネットワークのスループットと待ち時間に関する SAP の推奨事項を参照し、お客様が選択した動作モードで必要なスループットと最大待ち時間を決定してください。 {{site.data.keyword.cloud_notm}} のネットワーク・トポロジーで、必要なすべての構成に対応できるようにする必要があります。 不明な点がある場合や、災害回復力を最大化するために別のデータ・センターを災害復旧サイトにしたい場合は、{{site.data.keyword.cloud_notm}} サポートに連絡して、お客様のシナリオに最適なセットアップを決定してください。

SAP HANA のスケールアウト (マルチノード) 環境は、まだ評価段階であることにご注意ください。 つまり、SAP HANA のスタンバイ・ノードは、{{site.data.keyword.cloud_notm}} 環境の現行オプションではありません。

高可用性と災害復旧について詳しくは、[{{site.data.keyword.cloud_notm}} 高可用性サポート](/docs/infrastructure/sap-hana?topic=sap-hana-ha#ha)と[災害復旧](/docs/infrastructure/sap-reference-architecture?topic=sap-reference-architecture-recommendations#dr)を参照してください。

システムの複製やネットワークのスループットと待ち時間の詳細については、以下の資料を参照してください。
  * [How To Perform System Replication for SAP HANA ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.sap.com/documents/2013/10/26c02b58-5a7c-0010-82c7-eda71af511fa.html){: new_window}
  * [Network Required for SAP HANA System Replication ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.sap.com/documents/2014/06/babb2b55-5a7c-0010-82c7-eda71af511fa.html){: new_window}

Linux オペレーティング・システムに対応した HA クラスター拡張機能のセットアップについて詳しくは、以下の資料を参照してください。
  * [Automated SAP HANA System Replication with Pacemaker on RHEL Setup Guide ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://access.redhat.com/articles/1466063){: new_window}
  * [SAP HANA SR Performance Optimized Scenario ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.suse.com/docrep/documents/ir8w88iwu7/suse_linux_enterprise_server_for_sap_applications_12_sp1.pdf){: new_window}

## VMware ESXi サーバー・デプロイメント
{: #vmware_server}

{{site.data.keyword.cloud_notm}} SAP HANA オファリングに含まれているすべてのサーバーは、VMware ESX 用として認定されているので、SAP HANA を仮想マシン (VM) にデプロイすることも可能です。 VMware ESX をサーバーを一緒に注文すると、プリインストールの基本構成 ESX インスタンスがデプロイされて届きます。VM はデプロイされていません。 ESX ベース・デプロイメントに正しいゲスト・オペレーティング・システムをデプロイする作業は、お客様が行うことになります。 SAP Note 2414820 で定められている手順を実行し、SAP HANA on {{site.data.keyword.cloud_notm}} でサポートされているバージョンのオペレーティング・システムを選択してください。

ESX ベース・デプロイメントのサイジング・プロセスは、ベア・メタル・サーバー・デプロイメントのプロセスとは異なります。 *Architecture Guidelines and Best Practices for Deployments of SAP HANA on VMware vSphere Architecture and Technical Considerations Guide* に記されている推奨事項に従ってください。 *Architecture...and Considerations Guide* に記されているルールに沿って、仮想化層のオーバーヘッドを計算する必要があります。 VM にゲスト・オペレーティング・システムをデプロイしたら、SAP HANA の TDI KPI に適合しているかどうかを確認してください。 環境が SAP サポートの前提条件に準拠しているかどうかをテストする詳しい方法については、SAP Note 1943937 を確認してください。 サーバーにデプロイしたすべての VM で前提条件を満たす必要があります。

仮想化環境に SAP HANA をデプロイする場合は、SAP が定めた他のいくつかの規則に従うことも必要です。 実動環境の場合は、SAP Note 1995460 に概説されている制約事項を守ってください。 SAP Note 2024433 には、1 つのサーバーに複数の VM をデプロイする場合のルールが記されています。

詳細については、以下の資料を参照してください。
  * [SAP Note 2414820 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://launchpad.support.sap.com/#/notes/2414820){: new_window}
  * [*Architecture Guidelines and Best Practices for Deployments of SAP HANA on VMware vSphere Architecture and Technical Considerations Guide* ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.vmware.com/content/dam/digitalmarketing/vmware/en/pdf/whitepaper/sap_hana_on_vmware_vsphere_best_practices_guide-white-paper.pdf){: new_window}
  * [SAP Note 1943937 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://launchpad.support.sap.com/#/notes/1943937){: new_window}
  * [SAP HANA Tailored Data Center Integration Frequently Asked Questions ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://www.sap.com/documents/2016/05/e8705aae-717c-0010-82c7-eda71af511fa.html){: new_window}
  * [SAP Note 1995460 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://launchpad.support.sap.com/#/notes/1995460){: new_window}
  * [SAP Note 2024433 ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://launchpad.support.sap.com/#/notes/2024433){: new_window}
  * [SAP HANA Tailored Data Center Intgration (TDI) Overview ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://blogs.saphana.com/2015/02/18/sap-hana-tailored-data-center-integration-tdi-overview/){: new_window}
