---
title: リレーショナルデータベースを azure に移行する
description: Azure クラウドおよび Windows コンテナーで既存の .NET アプリケーションを最新化する |リレーショナルデータベースを azure に移行する
ms.date: 04/28/2018
ms.openlocfilehash: 3d4f03e61144bb6a442a50916d7fd024d38ec611
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "69578375"
---
# <a name="migrate-your-relational-databases-to-azure"></a>リレーショナルデータベースを azure に移行する

展望:Azure には、最も包括的なデータベース移行が用意されています。

Azure では、データベースサーバーを IaaS Vm (純粋なリフトアンドシフト) に直接移行することも、Azure SQL Database に移行して追加のメリットを提供することもできます。 Azure SQL Database には、マネージインスタンスと完全なサービスとしてのデータベース (DBaaS) オプションが用意されています。 図3-1 は、Azure で使用できる複数のリレーショナルデータベース移行パスを示しています。

![Azure でのデータベース移行パス](./media/image3-1.png)

> **図 3-1.** Azure でのデータベース移行パス

## <a name="when-to-migrate-to-azure-sql-database-managed-instance"></a>Azure SQL Database Managed Instance に移行する場合

ほとんどの場合、データを Azure に移行する際には、Azure SQL Database Managed Instance をお勧めします。 SQL Server データベースを移行するときに、アプリケーションを再設計したり、データやデータアクセスコードを変更したりする必要がないという約 100% の保証が必要な場合は、Azure SQL Database の Managed Instance 機能を選択します。

Azure SQL Database Managed Instance は、SQL Server インスタンスレベルの機能に対する追加の要件や、標準 Azure SQL Database (単一データベースモデル) で提供される機能を超える分離要件がある場合に最適なオプションです。 最後の1つは、最も PaaS 指向の選択肢ですが、従来の SQL server と同じ機能を提供するわけではありません。 移行が frictions になる可能性があります。

たとえば、インスタンスレベルの SQL Server 機能に対してディープな投資を行った組織は、SQL Managed Instance に移行することでメリットが得られます。 インスタンスレベルの SQL Server 機能の例としては、SQL 共通言語ランタイム (CLR) の統合、SQL Server エージェント、データベース間のクエリなどがあります。 これらの機能のサポートは、standard Azure SQL Database (単一データベースモデル) では使用できません。

高度に規制された業界で運営され、セキュリティのために分離を維持する必要がある組織では、SQL Managed Instance モデルを選択することによってメリットが得られる場合もあります。

Azure SQL Database の Managed Instance には、次の特性があります。

- Azure Virtual Network を使用したセキュリティの分離

- アプリケーション画面の互換性: 次の機能があります。

  - SQL Server エージェントと SQL Server プロファイラー

  - 複数データベースにまたがる参照とクエリ、SQL CLR、レプリケーション、変更データキャプチャ (CDC)、および Service Broker

- 最大 35 TB のデータベースサイズ

- 次の機能を備えた、最小限のダウンタイムの移行。

  - Azure Database Migration Service

  - ネイティブのバックアップと復元、およびログ配布

これらの機能を使用すると、既存のアプリケーションデータベースを Azure SQL Database に移行するときに、Managed Instance モデルは SQL Server の PaaS の利点の約 100% を提供します。 Managed Instance は SQL Server 環境であり、アプリケーションの設計を変更することなく、インスタンスレベルの機能を引き続き使用できます。

Managed Instance は、現在 SQL Server を使用しており、クラウドでのネットワークセキュリティに柔軟性を必要とする企業に最適です。 これは、SQL データベースのプライベート仮想ネットワークのようなものです。

## <a name="when-to-migrate-to-azure-sql-database"></a>Azure SQL Database に移行する場合

前述のように、標準の Azure SQL Database は完全に管理されたリレーショナル DBaaS です。 SQL Database、世界中の38データセンターで、数百万の実稼働データベースを現在管理しています。 これは、単純なトランザクションデータの管理から、グローバルな規模で高度なデータ処理を必要とするデータを大量に消費するミッションクリティカルなアプリケーションを実行するための、さまざまなアプリケーションとワークロードをサポートします。

PaaS の完全な機能により、価格が向上し、最終的にコストが削減されます。 basic、standard SQL database、および追加のインスタンス機能を使用しないアプリケーションがある場合は、標準の Azure SQL Database に移行することをお勧めします。 SQL CLR 統合、SQL Server エージェント、データベース間クエリなどの SQL Server 機能は、標準 Azure SQL Database ではサポートされていません。 これらの機能は、Azure SQL Database Managed Instance モデルでのみ使用できます。

Azure SQL Database は、アプリ開発者向けに構築された唯一のインテリジェントなクラウドデータベースサービスです。 また、マルチテナントアプリを効率的に配信できるように、ダウンタイムを発生させることなく、すぐに拡張できるクラウドデータベースサービスでもあります。 最終的には、Azure SQL Database イノベーションに時間がかかり、市場投入までの時間が短縮されます。 お好みの言語とプラットフォームを使用して、セキュリティで保護されたアプリを構築し、SQL database に接続できます。

Azure SQL Database には、次のような利点があります。

- アプリを学習して適応する組み込みのインテリジェンス (machine learning)

- オンデマンドのデータベースプロビジョニング

- あらゆるワークロードに対応する幅広いプラン

- 99.99% の可用性 SLA、ゼロメンテナンス

- データ保護のための Geo レプリケーションと復元サービス

- Azure SQL Database ポイントインタイムリストア機能

- ハイブリッドおよび移行を含む SQL Server 2016 との互換性

標準 Azure SQL Database は、Azure SQL Database Managed Instance よりも PaaS に近いです。 管理されたクラウドからさらに利点を得られるため、標準の Azure SQL Database をお勧めします。 ただし、Azure SQL Database には、通常の SQL Server インスタンスとオンプレミスのインスタンスの主な違いがいくつかあります。 既存のアプリケーションのデータベース要件、およびエンタープライズの要件とポリシーによっては、クラウドへの移行を計画するときに最適な選択肢とは言えない場合があります。

## <a name="when-to-move-your-original-rdbms-to-a-vm-iaas"></a>元の RDBMS を VM (IaaS) に移行する場合

移行オプションの1つは、Oracle、IBM DB2、MySQL、PostgreSQL、SQL Server など、元のリレーショナルデータベース管理システム (RDBMS) を、Azure VM 上で実行されている同様のサーバーに移動することです。 最小限の変更でクラウドへの移行を最速で行う必要がある既存のアプリケーションがある場合、またはまったく変更を加えていない場合は、クラウドで IaaS に直接移行することが公正な選択肢となる可能性があります。 クラウドの利点をすべて活用するのは最善の方法ではないかもしれませんが、ほとんどの場合、最速の初期パスです。

現時点では、Microsoft Azure は、IaaS Vm としてデプロイされた最大[331 の異なるデータベースサーバー](https://azuremarketplace.microsoft.com/marketplace/apps/category/databases?page=1&subcategories=databases-all)をサポートしています。 これには、SQL Server、Oracle、MySQL、PostgreSQL、IBM DB2 などの一般的な RDBMS や、MongoDB、Cassandra、DataNoSQL x、MariaDB、Cloudera などの他の多くのデータベースが含まれます。

> [!NOTE]
> RDBMS を Azure VM に移動する方法は、データをクラウドに移行する最速の方法である場合があります (IaaS であるため)。この方法では、IT チーム (データベース管理者および IT プロフェッショナル) に多大な投資を行う必要があります。 エンタープライズチームは、SQL Server の高可用性、ディザスターリカバリー、修正プログラムの適用をセットアップして管理できる必要があります。 また、このコンテキストには、完全な管理者権限を持つカスタマイズされた環境も必要です。

## <a name="when-to-migrate-to-sql-server-as-a-vm-iaas"></a>VM として SQL Server に移行する場合 (IaaS)

通常の VM として SQL Server に移行する必要がある場合もあります。 例として、SQL Server Reporting Services を使用する必要がある場合が挙げられます。 ただし、ほとんどの場合、Azure SQL Database Managed Instance は、オンプレミスの SQL server から移行するために必要なすべてを提供できます。そのため、SQL Server VM への移行は、最後の手段として行う必要があります。

## <a name="use-azure-database-migration-service-to-migrate-your-relational-databases-to-azure"></a>Azure Database Migration Service を使用してリレーショナルデータベースを Azure に移行する 

Azure Database Migration Service を使用して、SQL Server、Oracle、MySQL などのリレーショナルデータベースを Azure に移行することができます。これは、ターゲットデータベースが Azure VM 上で Azure SQL Database、Azure SQL Database Managed Instance、SQL Server のいずれであるかに関係ありません。

自動ワークフローと評価レポートを使用すると、データベースを移行する前に必要な変更を行うことができます。 準備が整うと、サービスはソースデータベースを Azure に移行します。

元の RDBMS を変更するたびに、再テストが必要になる場合があります。 また、テスト結果に応じて、アプリケーションの SQL 文またはオブジェクトリレーショナルマッピング (ORM) コードを変更することが必要になる場合もあります。

他のデータベース (IBM DB2 など) があり、リフトアンドシフトアプローチを選択した場合は、より複雑なデータ移行を実行する場合を除き、これらのデータベースを Azure の IaaS Vm として引き続き使用することをお勧めします。 より複雑なデータ移行では、新しいスキーマと異なるプログラミングライブラリを使用して別の種類のデータベースに移行するため、追加の作業が必要になります。

Azure Database Migration Service を使用してデータベースを移行する方法については、「 [Azure SQL Database Managed Instance と Azure Database Migration Service を使用したクラウドへの迅速なアクセス](https://channel9.msdn.com/Events/Build/2017/P4008)」を参照してください。

## <a name="additional-resources"></a>その他の技術情報

- **クラウド SQL Server オプションを選択してください:Azure VM (IaaS) での Azure SQL Database (PaaS) または SQL Server**

    <https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas>

- **Azure SQL DB Managed Instance と Database Migration Service により、クラウドに迅速にアクセスできます**

    <https://channel9.msdn.com/Events/Build/2017/P4008>

- **SQL Server データベースのクラウド内の SQL Database への移行**

    <https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate>

- **Azure SQL Database**

    <https://azure.microsoft.com/services/sql-database/?v=16.50>

- **仮想マシンでの SQL Server**

    <https://azure.microsoft.com/services/virtual-machines/sql-server/>

> [!div class="step-by-step"]
> [前へ](lift-and-shift-existing-apps-azure-iaas.md)
> [次へ](modernize-existing-apps-to-cloud-optimized/index.md)
