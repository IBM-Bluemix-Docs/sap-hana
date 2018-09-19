---



copyright:
  years: 2017, 2018
lastupdated: "2018-05-30"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# システム・ランドスケープの計画
{: #planning-your-system-landscape}

SAP *ランドスケープ*とは、2 つ以上の SAP *システム*を 1 つのグループとしてまとめたものです。SAP システムには通常、開発環境、品質テスト環境、実動環境が含まれます。 1 つの SAP システムは、1 つ以上の *SAP インスタンス*で構成されています。SAP インスタンスとは、同時に開始/停止するいくつかのプロセスをまとめたグループです。 SAP ランドスケープの詳細については、[*SAP Business Suite on IBM X6 Systems Reference Architecture*](https://lenovopress.com/redp5073.pdf) を参照してください。 
{: shortdesc}

市場のすべての SAP ソリューションに対して、サーバー (サイズ)/ストレージ (サイズ) など、考えられるいくつかのランドスケープ構成があります。 これらのソリューションには、[SAP Business Suite](https://open.sap.com/courses/suitehana1)、SAP Business Warehouse、すべての固有の SAP アドオンなどの SAP NetWeaver ベースの製品が含まれます。これらの製品は、{{site.data.keyword.cloud}} SAP-Certified Infrastructure に属するサーバーでサポートされます。SAP との統合が可能なサード・パーティー・ソフトウェアも、検討の対象のソリューションとして入ってきます。 

SAP HANA は、使用シナリオに応じて、SAP NetWeaver スタック・ベース・ソリューションのデータベースとして使用することも、スタンドアロン・エンティティーとして使用することもできます。 {{site.data.keyword.cloud_notm}} オファリングには、事前構成された SAP NetWeaver 認定サーバーが用意されているので、どちらのシナリオでも、認定サーバーを中心としたランドスケープを他のどのサーバーからも構築することが可能です。

サーバーのサイズを決める時には、実行するアプリケーションや拡張の可能性やパフォーマンスなどの情報に基づいて、できる限り厳密に見積もりを行うようにしてください。 さらに、アプリケーションのストレージ要件とメモリー所要量も考慮に入れる必要があります。 ランドスケープ内の SAP システムでは、内部のシステム間の接続についても、外部システムとの接続についても、独特の要件があります。 詳細については、[SAP ランドスケープの計画時の注意点](/docs/infrastructure/sap-hana/hana-considerations.html)を参照してください。

計画プロセスのステップを表 1 にまとめます。 ターゲット SAP ランドスケープの構築時に役立ててください。

表 1. 計画プロセスの概要

| ステップ | 詳細 |
| --- | --- |
| 1 | [SAP と {{site.data.keyword.cloud_notm}} の資格情報の取得とアカウントの作成](/docs/infrastructure/sap-hana/hana-get-credentials.html) |
| 2 | [SAP と {{site.data.keyword.cloud_notm}} の関連資料の確認](/docs/infrastructure/sap-hana/hana-review-doc.html) |
| 3 | [SAP アプリケーションの選定](/docs/infrastructure/sap-hana/hana-determine-apps.html) |
| 4 | [サーバーのサイジング](/docs/infrastructure/sap-hana/hana-size-server.html) |
| 5 | [構成の選定](/docs/infrastructure/sap-hana/hana-determine-configuration.html) |

## 次のステップ

表 1 の該当ステップを選択して、SAP ランドスケープの計画を開始します。
