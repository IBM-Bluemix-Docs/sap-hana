---



copyright:
  years: 2018
lastupdated: "2018-03-02"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}


# 3. SAP アプリケーションの選定

{{site.data.keyword.baremetal_long}} で実行する SAP ベース・アプリケーションを選定する必要があります。選定時に考えなければならない項目を以下にまとめます。

 * データベースをどのように使用するか。SAP HANA をデプロイするには、2 つの方法があります。1 つ目は、SAP NetWeaver スタックのデータベースとして使用する方法です。その場合は、主にデータ・ソースの役割を果たします。2 つ目は、スタンドアロン・モードで SAP HANA を実行するデプロイメント方式です。その場合は、SAP HANA システムにアプリケーションを直接デプロイします。いずれにしても、サイジング・プロセスやシステム要件や依存項目は、システムの使用方法 (開発/テスト、PoC (概念検証)、実動) によって異なります。
 * アプリケーションをどのように使用するか。開発/テスト用か、それとも実動用か。
 * {{site.data.keyword.cloud_notm}} 仮想プライベート・ネットワーク・サービスで SSL を使用するか、Point-to-Point Tunneling Protocol (PPTP) を使用するか。
  
## 次のステップ

  [4. サーバーのサイジング](/docs/infrastructure/sap-hana/hana-size-server.html)
  
  [5. 構成の選定](/docs/infrastructure/sap-hana/hana-determine-configuration.html)
