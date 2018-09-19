---



copyright:
  years: 2017, 2018
lastupdated: "2010-08-10"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 2. インフラストラクチャーのセットアップ
{: #set_up_infrastructure}

SAP HANA {{site.data.keyword.baremetal_long}}、ネットワーク、セキュリティー、ストレージ、オペレーティング・システム (OS) のセットアップ方法を以下のセクションにまとめます。 不明な点があれば、[{{site.data.keyword.cloud_notm}}サポート](https://console.bluemix.net/docs/get-support/howtogetsupport.html#getting-customer-support)に連絡してください。

## サーバーの注文
{: order-server}

{{site.data.keyword.baremetal_short}} の注文手順を以下にまとめます。 追加情報については、お客様の固有の資格情報を使用して[カスタム・ベアメタル・サーバーの作成](https://console.bluemix.net/docs/bare-metal/baremetal-provision.html#building-a-custom-bare-metal-server)を参照してください。

1. お客様の固有の資格情報を使用して [{{site.data.keyword.cloud_notm}} インフラストラクチャー・カスタマー・ポータル](https://control.softlayer.com)にログインします。
2. 「利用料金の要約」ページで**「アカウント」**>**「注文」**をクリックします。
3. 「デバイス」ページの {{site.data.keyword.baremetal_short}} の下にある**「月単位」**リンクをクリックします。 サーバー・リストが表示されます。SAP 認定サーバーがリストの先頭に示されます。
4. **「月単位の開始価格 (STARTING PRICE PER MONTH)」**の下にあるハイパーリンクをクリックし、対象のサーバーを選択すると、「構成/注文 (Configure/Order)」ページが表示されます。 CPU モデルの下で **-H** 付きで表示されているのが SAP HANA 認定サーバーです。  
5. 注文するサーバーの数を**「数量」**フィールドに入力し、**「データ・センター」**でデータ・センターを選択します。
6. **「サーバー」**、**「RAM」**、プライベート・ストレージ・オプションは、サーバーの選択内容に基づいてデフォルト設定が決まるので、変更できません。サーバーの注文後に、{{site.data.keyword.cloud_notm}} 用の {{site.data.keyword.IBM_notm}} {{site.data.keyword.blockstorageshort}} または {{site.data.keyword.filestorage_full_notm}}、および Network Attached Storage (NAS) を注文します。
7. **「オペレーティング・システム」**で、Red Hat または SUSE を選択し、サーバー用の特定のオペレーティング・システムまたは VMware ハイパーバイザーを選択します。**注**: オペレーティング・システムに関してライセンス持ち込み (BYOL) を行う場合は、**「その他」**>**「オペレーティング・システムなし」**を選択します。詳しくは、[ライセンス持ち込み (BYOL)](#byol) を参照してください。

## サーバー・オプションの選択
{: #select_options}

次のステップでは、構成に追加するディスクのタイプと数を選択します。 RAID (Redundant Array of Independent Disks) ストレージ・グループと RAID ストレージ・グループのパーティショニング・レイアウトに関する他のオプションも選択できます。 詳しくは、[RAID について](https://console.bluemix.net/docs/bare-metal/what-raid.html#about-raid)か、[{{site.data.keyword.cloud_notm}} サポート](https://console.bluemix.net/docs/get-support/howtogetsupport.html#getting-customer-support)を参照してください。

1. **「SAP 認定サーバー (SAP Certified Servers)」**の下で、サーバーの使用方法に基づいてオプションを選択します。 詳しくは、[Design Decision Tool](https://github.com/ibm-cloud-architecture/infrastructure-design-decision-tool) (このツールが表示されるまでスクロールダウンする) または [{{site.data.keyword.cloud_notm}} サポート](https://console.bluemix.net/docs/get-support/howtogetsupport.html#getting-customer-support)を参照してください。
2. ページ下部にある**「注文に追加」**をクリックします。

## 拡張システム構成のセットアップ
{: #adv_config}

1. [拡張システム構成](https://console.bluemix.net/docs/bare-metal/baremetal-provision.html#advanced-server-configuration-options)のガイドラインに沿って、**「拡張システム構成」**ウィンドウの値を設定します。

SAP ホスト名は、最大 13 個の英数字で構成しなければなりません。 SAP ホスト名の詳細については、[SAP Notes 611361](https://launchpad.support.sap.com/#/611361) と [129997](https://launchpad.support.sap.com/#/129997) を参照してください。 

## 選択内容の確認
{: #confirm_selections}

1. 「清算」ページで選択内容を確認し、**「クラウド・サービスの条件 (Cloud Service terms)」**と**「サード・パーティー・ソフトウェア契約 (3rd Party Software Agreement)」**をクリックします。
2. 「アカウントの作成」にスクロールダウンし、**決済タイプ、名前、カード**の情報を入力し、決済用のクレジット・カードの**有効期限** (日付) を入力します。
3. **「注文の送信」**をクリックします。 注文番号の画面にリダイレクトされます。 その画面を印刷してください。それが注文の受領書です。

_{{site.data.keyword.cloud_notm}} の注文 ## が承認されました_という趣旨の件名が付いた確認 E メールがお客様のプロファイルに設定されている E メール・アドレスに送信されます。 この E メールは、お客様のサーバーが承認されてデプロイ・プロセスに入っていることの通知です。 デプロイが完了すると、サーバーが使用可能になり、[{{site.data.keyword.cloud_notm}} インフラストラクチャー・カスタマー・ポータル](https://control.softlayer.com)から管理できるようになったことを知らせる通知が送信されます。

## 個人所有ライセンスの持ち込み
{: #byol}

自分でオペレーティング・システム・ライセンスを所有している場合、ベンダーの指示に基づいて、それを {site.data.keyword.baremetal_short} にインストールします。詳しくは、[OS なしオプション](https://console.bluemix.net/docs/bare-metal/introduction-no-os.html#how-to-install-an-operating-system-on-a-no-os-server-)を参照してください。

## 次のステップ

これで、{{site.data.keyword.baremetal_short}} の管理作業を開始する準備ができました。 [SAP HANA 環境の管理](/docs/infrastructure/sap-hana/hana-manage-environment.html)を参照してください。

