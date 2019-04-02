---

copyright:
  years: 2017, 2019
lastupdated: "2019-02-26"

keywords: SAP HANA, {{site.data.keyword.cloud_notm}}

subcollection: sap-hana

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# 入門チュートリアル
{: #getting-started}

{{site.data.keyword.IBM_notm}} と SAP は、45 年以上にわたり、さまざまな分野 (ハードウェア、ソフトウェア、クラウド、サービス、ファイナンスなど) でコラボレーションを行ってきました。 現在は、{{site.data.keyword.cloud}}  インフラストラクチャー製品を最適化して、世界中の 60 を超える {{site.data.keyword.cloud_notm}} データ・センターでの SAP HANA ソリューションのサポートを組み込むためにコラボレーションを行っています。
{: shortdesc}

このコンテンツでは、{{site.data.keyword.cloud_notm}} で SAP HANA のインフラストラクチャーとサブスクリプションのプロビジョニングとインストールを実行するための推奨事項を取り上げます。 これは、SAP HANA の資料に置き換わるものではなく、インストール・プロセスを詳細に説明するものでもありません。 インフラストラクチャーの計画とプロビジョニングに役立つ情報を提供し、SAP のインストールを開始できるようにすることを目的としています。 SAP のインストール環境 (データベースも含む) は、オンプレミスのインストール環境と変わりません。 用意されているインフラストラクチャーに関して、{{site.data.keyword.cloud_notm}} 環境で SAP システムを運用するのに役立つ推奨事項やガイドラインが提供されています。例えば、ネットワークのセットアップやバックアップ・ストレージに関する情報が含まれます。 インフラストラクチャー配置後の SAP HANA システムの操作は、他のデータ・センターでの操作と変わりありません。

{{site.data.keyword.cloud_notm}} インフラストラクチャーを短時間で構築するのに役立つステップを表 1 にまとめます。
<table>
   <CAPTION>表 1. クイック・スタート・ステップ</CAPTION>
   <THEAD>
   <TR>
   <th>タスク</th>
   <th>詳細</th>
   </TR>
   </THEAD>
   <TBODY>
   <tr>
   <td>1. お客様の実装に関連する IBM Cloud と SAP の内容を読む</td>
   <td>お客様の組織で初めて IBM Cloud を利用する場合は、以下の情報が役立つ可能性があります。計画段階の前に、この情報を確認してください。
   <li><a href="https://ibm.com/cloud-computing/">What is IBM Cloud</a></li>
   <li><a href="https://ibm.com/cloud/get-started">Getting started with IBM Cloud</a></li>
   <li><a href="https://www.ibm.com/cloud/bare-metal-servers/sap">SAP Certified Infrastructure on IBM Cloud</a></li>

   以下の SAP 資料も役立ちます。     
   <li><a href="https://www.sap.com/products/hana/implementation/resources.html">SAP HANA Installation Guide</a>。インストール・ガイドをダウンロードできます。</li>
  <li><a href="https://www.youtube.com/watch?v=4wICiRTP8u0/">How to create an SAP S-user ID</a>。S ユーザー ID を作成できるのは、スーパー管理者または必要な権限を持つ S ユーザーだけです。</li>
   <li><a href="https://help.sap.com/hana/SAP_HANA_Administration_Guide_en.pdf">SAP HANA Administration Guide</a></li>
   <li><a href="https://support.sap.com">SAP Notes</a>。SAP S ユーザー ID が必要です。</li>
   <tr>
   <td>2. IBM Cloud への登録</td>
   <td>IBM Cloud アカウントをセットアップする手順については、<a href="https://cloud.ibm.com/docs/account?topic=account-signup#signing-up-for-ibm-cloud">Signing up for IBM Cloud への登録</a>を参照してください。</td>
 <tr>
   <td>3. IBM Cloud インフラストラクチャー・カスタマー・ポータルへのアクセス</td>
   <td><a href="https://control.softlayer.com">IBM Cloud インフラストラクチャー・カスタマー・ポータル</a>は、すべてのインフラストラクチャー・コンポーネント (コンピュート、接続、ストレージ、ネットワーク、データ・センター) を利用するためのグラフィカル・ゲートウェイです。 このカスタマー・ポータルにアクセスするには、<a href="https://console.bluemix.net/docs/customer-portal?topic=customer-portal-getting-started#getting-started">IBM ID とパスワード</a>が必要です。</td>
   <tr>
   <td>4. システム・ランドスケープの計画</td>
   <td>SAP HANA のワークロードをサポートするために、<a href="sap-hana?topic=sap-hana-planning-your-system-landscape#planning-your-system-landscape">システム・ランドスケープの計画</a>に記されている情報を活用して、IBM Cloud 環境の設計/サイジング/プロビジョニングを実行してください。</td>  
 <tr>
   <td>5. システムのプロビジョニング</td>
   <td><a href="sap-hana?topic=sap-hana-provision_environment#provision_environment">SAP HANA 環境のプロビジョニング</a>に記されているステップと情報を活用して、IBM Cloud インフラストラクチャーをセットアップしてください。</td>
   <tr>
   <td>6. SAP ランドスケープのインストール</td>
   <td>サーバーがオンプレミスである場合と同じ要領で SAP ランドスケープを IBM Cloud インフラストラクチャーにインストールします。 詳細については、<a href="sap-hana?topic=sap-hana-install_sap#install_sap">SAP ソフトウェア/アプリケーションのダウンロードとインストール</a>を参照してください。</td>
   </td>
   </tr>
   </TBODY>
   </table>
