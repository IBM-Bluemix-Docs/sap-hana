---



copyright:
  years: 2018
lastupdated: "2018-02-05"


---

{:shortdesc: .shortdesc}
{:codeblock: .codeblock}
{:screen: .screen}
{:new_window: target="_blank"}
{:pre: .pre}
{:tip: .tip}
{:table: .aria-labeledby="caption"}


# 4. サーバーのサイジング
{: #size_the_server}

使用する SAP ソリューションを選定したら、次のステップとして、SAP ランドスケープをサポートするのに必要な {{site.data.keyword.baremetal_long}} の数を見極め、サーバーのサイズ設定が適切であるようにします。
{: shortdesc}

## SAP のサイジング方法
{: #size_method}

SAP HANA は、単一ノード構成の {{site.data.keyword.cloud_notm}} で提供されています。合計 RAM サイズは以下のようになります。 
  * 512 GB
  * 1024 GB (1 TB)
  * 2048 GB (2 TB)
  * 4096 GB (4 TB)
  * 8192 GB (8 TB)
  
これはカラム型データベースであり、従来の行ベースのリレーショナル・データベース管理システム (RDMS) と比較して、通常はデータを保管するのに必要なスペースが少なくて済みます。データの圧縮率が高いので、ソース・データとデータベース・データのサイズの比率が 3:1 から 10:1 を超えるほどになります。 

サーバーを購入する*前に*、サイズを正確に見積もる必要があります。サイジングがプロジェクト成功の鍵となるためです。メモリーのサイズやストレージ要件の見積もりが間違っていると、さらに大きなサーバーへのアップグレードやマイグレーションが必要になる可能性があります。

## SAP Quick Sizer へのアクセス
{: #quick_sizer}

SAP HANA 認定アプライアンスのサイジングの検討で最も重要になるリソースの 1 つがメイン・メモリーです。サイジング関連のトピックの開始点として、公開されている [*SAP HANA Master Guide*](https://help.sap.com/doc/e95f6750b0fd10148ea5c6be75016694/2.0.00/en-US/SAP_HANA_Master_Guide_en.pdf) を参照してください。そのガイドに記されている [Sizing SAP HANA](https://help.sap.com/viewer/eb3777d5495d46c5b2fa773206bbfb46/2.0.00/en-US/d4a122a7bb57101493e3f5ca08e6b039.html) の情報が SAP HANA システムのサイジングに関する指針になります。新規インストールと既存システムのマイグレーションの両方に関連する、さまざまなシナリオが取り上げられています。SAP HANA 版の SAP Quick Sizer ツールへのリンクもあります (ツールを使用するには SAP S ユーザー ID が必要です)。また、そのページには SAP HANA サーバーのサイジングに関連した SAP Note のリストも記載されています。 

## 仮想化環境でのサイジング
{: #size_virtual}

仮想化環境で SAP HANA を実行する場合のサイジングの注意点については、[VMware ESXi サーバー・デプロイメント](/docs/infrastructure/sap-hana/hana-considerations.html#vmware-server)と
[*Architecture Guidelines and Best Practices for Deployments of SAP HANA on VMware vSphere Architecture and Technical Considerations Guide*](https://www.vmware.com/content/dam/digitalmarketing/vmware/en/pdf/whitepaper/sap_hana_on_vmware_vsphere_best_practices_guide-white-paper.pdf) を参照してください。

## 次のステップ

 [5. 構成の選定](/docs/infrastructure/sap-hana/hana-determine-configuration.html)
