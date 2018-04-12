---



copyright:
  years: 2017, 2018
lastupdated: "2010-03-05"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 2. インフラストラクチャーのセットアップ
{: #set_up_infrastructure}

SAP HANA {{site.data.keyword.baremetal_long}}、ネットワーク、セキュリティー、ストレージ、オペレーティング・システム (OS) のセットアップ方法を以下のセクションにまとめます。不明な点があれば、[{{site.data.keyword.cloud_notm}}サポート](https://console.bluemix.net/docs/get-support/howtogetsupport.html#getting-customer-support)に連絡してください。

## サーバーの注文
{: order-server}

{{site.data.keyword.baremetal_short}} の注文手順を以下にまとめます。お客様の固有の資格情報を使用して、[ベア・メタル・サーバーの構成](https://console.bluemix.net/docs/bare-metal/configuring.html#configuring-your-bare-metal-server)にアクセスすると、追加情報が得られます。

1. お客様の固有の資格情報を使用して [{{site.data.keyword.cloud_notm}} インフラストラクチャー・カスタマー・ポータル](https://control.softlayer.com)にログインします。
2. 「利用料金の要約」ページの**「デバイス」**アイコンをクリックします。
3. 「デバイス」ページの {{site.data.keyword.baremetal_short}} の下にある**「月単位」**リンクをクリックします。「サーバー・リスト」ダイアログ・ボックスが表示されます。
4. リストの先頭に SAP 認定サーバーがあります。**「月単位の開始価格 (STARTING PRICE PER MONTH)」**の下にあるハイパーリンクをクリックし、対象のサーバーを選択すると、「構成/注文 (Configure/Order)」ページが表示されます。CPU モデルの下で **-H** 付きで表示されているのが SAP HANA 認定サーバーです。  
5. 注文するサーバーの数を**「数量」**フィールドに入力し、お客様の**データ・センター**を選択します。
6. お客様の選択したサーバーに基づいて、**サーバー**、**RAM**、**オペレーティング・システム**、お客様の専用ストレージのオプションがデフォルトで設定されます。変更はできません。ストレージのサイジングは、一定量の RAM で必要になる SAP HANA のサイズと一致します。サーバーの注文後に、{{site.data.keyword.cloud_notm}} 用の {{site.data.keyword.IBM_notm}} {{site.data.keyword.blockstorageshort}} または {{site.data.keyword.filestorage_full_notm}}、および Network Attached Storage (NAS) を注文します。
7. **オペレーティング・システム**として Red Hat か Microsoft を選択し、お客様のサーバーで使用するオペレーティング・システムか VMware ハイパーバイザーを選択します。

## サーバー・オプションの選択
{: #select_options}

次のステップでは、構成に追加するディスクのタイプと数を選択します。RAID (Redundant Array of Independent Disks) ストレージ・グループと RAID ストレージ・グループのパーティショニング・レイアウトに関する他のオプションも選択できます。詳細については、[RAID について](https://console.bluemix.net/docs/bare-metal/what-raid.html#about-raid} or [{{site.data.keyword.cloud_notm}} Support](https://console.bluemix.net/docs/get-support/howtogetsupport.html#getting-customer-support)を参照してください。

1. **「SAP 認定サーバー (SAP Certified Servers)」**の下で、サーバーの使用方法に基づくオプションを選択します。各オプションの詳細については、[ベア・メタル・サーバーのセットアップ](https://console.bluemix.net/docs/bare-metal/configuring.html#setting-up-your-bare-metal-servers)を参照してください。[Design Decision Tool](https://github.com/ibm-cloud-architecture/infrastructure-design-decision-tool) (該当ツールにスクロールダウン) や [{{site.data.keyword.cloud_notm}}サポート](https://console.bluemix.net/docs/get-support/howtogetsupport.html#getting-customer-support)でも詳細を確認できます。
2. ページ下部にある**「注文に追加」**をクリックします。

## 拡張システム構成のセットアップ
{: #adv_config}

1. [拡張システム構成](https://console.bluemix.net/docs/bare-metal/configuring.html#advanced-system-configuration)のガイドラインに沿って、**「拡張システム構成」**ウィンドウの値を設定します。

SAP ホスト名は、最大 13 個の英数字で構成しなければなりません。SAP ホスト名の詳細については、[SAP Notes 611361](https://launchpad.support.sap.com/#/611361) と [129997](https://launchpad.support.sap.com/#/129997) を参照してください。 

## 選択内容の確認
{: #confirm_selections}

1. 「清算」ページで選択内容を確認し、**「クラウド・サービスの条件 (Cloud Service terms)」**と**「サード・パーティー・ソフトウェア契約 (3rd Party Software Agreement)」**をクリックします。
2. 「アカウントの作成」にスクロールダウンし、**決済タイプ、名前、カード**の情報を入力し、決済用のクレジット・カードの**有効期限** (日付) を入力します。
3. **「注文の送信」**をクリックします。注文番号の画面にリダイレクトされます。その画面を印刷してください。それが注文の受領書です。

_{{site.data.keyword.cloud_notm}} の注文 ## が承認されました_という趣旨の件名が付いた確認 E メールがお客様のプロファイルに記されている E メール・アドレスに送信されます。この E メールは、お客様のサーバーが承認されてデプロイ・プロセスに入っていることの通知です。デプロイが完了すると、サーバーが使用可能になったので [{{site.data.keyword.cloud_notm}} インフラストラクチャー・カスタマー・ポータル](https://control.softlayer.com)から管理できる、という趣旨の通知が送信されます。

## 次のステップ

これで、{{site.data.keyword.baremetal_short}} の管理作業を開始する準備ができました。[SAP HANA 環境の管理](/docs/infrastructure/sap-hana/hana-manage-environment.html)を参照してください。

