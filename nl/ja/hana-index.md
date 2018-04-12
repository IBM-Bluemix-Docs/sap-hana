---



copyright:
  years: 2017, 2018
lastupdated: "2018-03-02"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# IBM Cloud for SAP applications の入門チュートリアル
{: #getting-started}

{{site.data.keyword.IBM_notm}} と SAP は、45 年以上にわたり、さまざまな分野 (ハードウェア、ソフトウェア、クラウド、サービス、ファイナンスなど) でコラボレーションを行ってきました。現在は、世界中の 60 余りの {{site.data.keyword.cloud_notm}} データ・センターを利用して、SAP HANA ソリューションのサポートを組み込んだ {{site.data.keyword.cloud}} インフラストラクチャー製品を最適化するためにコラボレーションを行っています。
{: shortdesc}

このコンテンツでは、{{site.data.keyword.cloud_notm}} で SAP HANA のインフラストラクチャーとサブスクリプションのプロビジョニングとインストールを実行するための推奨事項を取り上げます。これは、SAP HANA の資料に置き換わるものではなく、インストール・プロセスを詳細に説明するものでもありません。インフラストラクチャーの計画とプロビジョニングに役立つ情報を提供し、SAP のインストールを開始できるようにすることを目的としています。SAP のインストール環境 (データベースも含む) は、オンプレミスのインストール環境と変わりません。用意されているインフラストラクチャーに関して、{{site.data.keyword.cloud_notm}} 環境で SAP システムを運用するのに役立つ推奨事項やガイドラインが提供されています。例えば、ネットワークのセットアップやバックアップ・ストレージに関する情報が含まれます。インフラストラクチャー配置後の SAP HANA システムの操作は、他のデータ・センターでの操作と変わりありません。

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
   <td>1. お客様の実装環境に関連した IBM Cloud と SAP のコンテンツの確認</td>
   <td>IBM Cloud を初めて利用するお客様は、計画段階の前に、以下の大切な情報を確認してください。
   <li><a href="https://ibm.com/cloud-computing/">What is IBM Cloud</a></li>
   <li><a href="https://ibm.com/cloud/get-started">Getting started with IBM Cloud</a></li>
   <li><a href="https://www.ibm.com/cloud/bare-metal-servers/sap">SAP Certified Infrastructure on IBM Cloud</a></li>
     
   以下の SAP 資料も役立ちます。     
   <li><a href="https://www.sap.com/products/hana/implementation/resources.html">SAP HANA Installation Guide</a>。インストール・ガイドをダウンロードできます。</li> 
   <li><a href="https://www.sapappsdevelopmentpartnercenter.com/en/faq/program-faqs_2/how-to-receive-an-s-user-to-access-the-s_77/">How to set up an SAP S-user ID</a></li>
   <li><a href="https://help.sap.com/hana/SAP_HANA_Administration_Guide_en.pdf">SAP HANA Administration Guide</a></li>
   <li><a href="https://support.sap.com">SAP Notes</a>。SAP S ユーザー ID が必要です。</li>
   <tr>
   <td>2. IBM Cloud への登録</td>
   <td>IBM Cloud アカウントをセットアップする手順については、<a href="https://console.bluemix.net/docs/admin/adminpublic.html#signing-up-for-ibm-cloud">Signing up for IBM Cloud への登録</a>を参照してください。</td>
 <tr>
   <td>3. IBM Cloud インフラストラクチャー・カスタマー・ポータルへのアクセス</td>
   <td><a href="https://control.softlayer.com">IBM Cloud インフラストラクチャー・カスタマー・ポータル</a>は、すべてのインフラストラクチャー・コンポーネント (コンピュート、接続、ストレージ、ネットワーク、データ・センター) を利用するためのグラフィカル・ゲートウェイです。このカスタマー・ポータルにアクセスするには、<a href="https://console.bluemix.net/docs/customer-portal/getting-started.html#getting-started">IBM ID とパスワード</a>が必要です。</td> 
   <tr>
   <td>4. システム・ランドスケープの計画</td>
   <td>SAP HANA のワークロードをサポートするために、<a href="hana-planning-your-system-landscape.html">システム・ランドスケープの計画</a>に記されている情報を活用して、IBM Cloud 環境の設計/サイジング/プロビジョニングを実行してください。</td>  
 <tr>
   <td>5. システムのプロビジョニング</td>
   <td><a href="hana-provision-environment.html#provision_environment">SAP HANA 環境のプロビジョニング</a>に記されているステップと情報を活用して、IBM Cloud インフラストラクチャーをセットアップしてください。</td>
   <tr>
   <td>6. SAP ランドスケープのインストール</td>
   <td>オンプレミス・サーバーの場合と同じ要領で SAP ランドスケープを IBM Cloud インフラストラクチャーにインストールします。詳細については、<a href="hana-installing-SAP-landscape.htm#install_sap">SAP ソフトウェア/アプリケーションのダウンロードとインストール</a>を参照してください。</td>
   </td>
   </tr>
   </TBODY>
   </table>