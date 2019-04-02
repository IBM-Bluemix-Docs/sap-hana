---

copyright:
  years: 2017, 2019
lastupdated: "2019-02-26"

keywords: SAP HANA, SAP landscape, {{site.data.keyword.cloud_notm}}

subcollection: sap-hana

---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:table: .aria-labeledby="caption"}

# システム・ランドスケープの計画
{: #planning-your-system-landscape}

SAP *ランドスケープ*とは、2 つ以上の SAP *システム*を 1 つのグループとしてまとめたものです。SAP システムには通常、開発環境、品質テスト環境、実動環境が含まれます。 1 つの SAP システムは、1 つ以上の *SAP インスタンス*で構成されています。SAP インスタンスとは、同時に開始/停止するいくつかのプロセスをまとめたグループです。 SAP ランドスケープについて詳しくは、[*SAP Business Suite on IBM X6 Systems Reference Architecture* ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://lenovopress.com/redp5073.pdf){: new_window} を参照してください。
{: shortdesc}

市場のすべての SAP ソリューションに対して、サーバー (サイズ)/ストレージ (サイズ) など、考えられるいくつかのランドスケープ構成があります。 これらのソリューションには、[SAP Business Suite ![外部リンク・アイコン](../../icons/launch-glyph.svg "外部リンク・アイコン")](https://open.sap.com/courses/suitehana1){: new_window}、SAP Business Warehouse、すべての固有の SAP アドオンなどの SAP NetWeaver ベースの製品が含まれます。これらの製品は、{{site.data.keyword.cloud}} SAP-Certified Infrastructure に属するサーバーでサポートされます。SAP との統合が可能なサード・パーティー・ソフトウェアも、検討の対象のソリューションとして入ってきます。

SAP HANA は、使用シナリオに応じて、SAP NetWeaver スタック・ベース・ソリューションのデータベースとして使用することも、スタンドアロン・エンティティーとして使用することもできます。 {{site.data.keyword.cloud_notm}} オファリングには、事前構成された SAP NetWeaver 認定サーバーが用意されているので、どちらのシナリオでも、認定サーバーを中心としたランドスケープを他のどのサーバーからも構築することが可能です。

サーバーのサイズを決める時には、実行するアプリケーションや拡張の可能性やパフォーマンスなどの情報に基づいて、できる限り厳密に見積もりを行うようにしてください。 さらに、アプリケーションのストレージ要件とメモリー所要量も考慮に入れる必要があります。 ランドスケープ内の SAP システムでは、内部のシステム間の接続についても、外部システムとの接続についても、独特の要件があります。 詳細については、[SAP ランドスケープの計画時の注意点](/docs/infrastructure/sap-hana?topic=sap-hana-considerations#considerations)を参照してください。

計画プロセスのステップを表 1 にまとめます。 ターゲット SAP ランドスケープの構築時に役立ててください。

表 1. 計画プロセスの概要

| ステップ | 詳細 |
| --- | --- |
| 1 | [SAP と {{site.data.keyword.cloud_notm}} の資格情報の取得とアカウントの作成](/docs/infrastructure/sap-hana?topic=sap-hana-get_sap_ibm_credentials#get_sap_ibm_credentials) |
| 2 | [SAP と {{site.data.keyword.cloud_notm}} の関連資料の確認](/docs/infrastructure/sap-hana?topic=sap-hana-review_doc#review_doc) |
| 3 | [SAP アプリケーションの選定](/docs/infrastructure/sap-hana?topic=sap-hana-3-determining-your-sap-applications#3-determining-your-sap-applications) |
| 4 | [サーバーのサイジング](/docs/infrastructure/sap-hana?topic=sap-hana-size_the_server#size_the_server) |
| 5 | [構成の選定](/docs/infrastructure/sap-hana?topic=sap-hana-determine_configuration#determine_configuration) |

## 次のステップ

表 1 の該当ステップを選択して、SAP ランドスケープの計画を開始します。
