---
title: リレーショナル データベースを azure に移行します。
description: Azure クラウドおよび Windows コンテナーで既存の .NET アプリケーションを近代化 |リレーショナル データベースを azure に移行します。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 8cadfc99a4c3d32e24d4a44e8cf4ce17a2ba7a07
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2019
ms.locfileid: "57677553"
---
# <a name="migrate-your-relational-databases-to-azure"></a>リレーショナル データベースを azure に移行します。

ビジョン:Azure では、最も包括的なデータベースの移行を提供します。

Azure では、データベース サーバーを移行するには (純粋なリフト アンド シフト) IaaS Vm に直接または追加の特典、Azure SQL Database に移行できます。 Azure SQL Database マネージ インスタンスと完全なデータベースのサービスとしての-(DBaaS) オプションを提供します。 図 3-1 は、Azure で利用可能な移行パスを複数のリレーショナル データベースには示しています。

![Azure でのデータベース移行パス](./media/image3-1.png)

> **図 3-1.** Azure でのデータベース移行パス

## <a name="when-to-migrate-to-azure-sql-database-managed-instance"></a>Azure SQL Database マネージ インスタンスに移行するときに

ほとんどの場合、Azure SQL Database マネージ インスタンスは、データを Azure に移行する際に考慮する最善の選択肢になります。 SQL Server データベースを移行して、ほぼ 100% 確実にアプリケーションを再設計したり、データまたはデータ アクセス コードを変更する必要はありません必要がありますの場合は、Azure SQL Database のマネージ インスタンスの機能を選択します。

Azure SQL Database マネージ インスタンスは、SQL Server インスタンス レベルの機能の追加要件または標準の Azure SQL データベース (1 つのデータベース モデル) で提供される機能以外の分離要件がある場合に最適なオプションが。 この最後の 1 つは、最も PaaS 指向の選択肢ですが、従来の SQL server の場合と同じ機能を提供していません。 移行では、あつれきを surface 可能性があります。

たとえば、インスタンス レベルの SQL Server 機能の詳細への投資を行った組織が有利 SQL マネージド インスタンスに移行します。 例としてインスタンス レベルの SQL Server 機能の SQL 共通言語ランタイム (CLR) 統合、SQL Server エージェント, やデータベースにまたがるクエリを実行します。 これらの機能のサポートは、標準の Azure SQL Database (単一データベース モデル) でご利用いただけません。

また規制の厳しい業界で動作して、セキュリティのための分離を維持する必要がある組織は、SQL マネージ インスタンス モデルを選択すると便利可能性があります。

Azure SQL database マネージ インスタンスには、次の特徴があります。

- Azure 仮想ネットワーク経由のセキュリティ分離

- Surface とアプリケーションの互換性、これらの機能:

  - SQL Server エージェント、SQL Server Profiler

  - データベースにまたがる参照とクエリ、SQL CLR では、レプリケーション、変更データ キャプチャ (CDC)、および Service Broker

- データベースのサイズを最大 35 TB

- これらの機能の最低限のダウンタイムでの移行:

  - Azure Database Migration Service

  - ネイティブのバックアップと復元、およびログ配布

これらの機能を備えた Azure SQL database では、既存のアプリケーション データベースを移行するときに、マネージ インスタンス モデルでは、PaaS の利点のほぼ 100% for SQL Server。 マネージ インスタンスは、インスタンス レベルの機能を使用して、アプリケーションの設計を変更することがなく引き続き SQL Server 環境です。

マネージ インスタンスは、現在使用している SQL Server、およびクラウドでのネットワーク セキュリティの柔軟性を必要とする企業に最適では可能性があります。 SQL database 向けのプライベート仮想ネットワークをできるようになります。

## <a name="when-to-migrate-to-azure-sql-database"></a>Azure SQL Database に移行するタイミング

前述のように、標準の Azure SQL Database は、完全管理型リレーショナル DBaaS にします。 SQL Database は現在、世界中の 38 のデータ センター間で何百万もの実稼働データベースを管理します。 さまざまなアプリケーションや世界規模での高度なデータ処理を必要とするデータ量の多い最も、ミッション クリティカルなアプリケーションにするために、単純なトランザクション データの管理からのワークロードをサポートします。

そのすべての PaaS 機能のための料金より- とコストの削減が最終的に、移行する標準の Azure SQL Database、"既定では choice"としてそのは basic、standard SQL データベース、およびインスタンスの追加機能がないアプリケーションがある場合。 SQL CLR 統合、SQL Server エージェント、およびデータベースにまたがるクエリを実行するように SQL Server の機能は標準の Azure SQL Database ではサポートされていません。 これらの機能が Azure SQL Database マネージ インスタンス モデルでのみ使用できます。

Azure SQL Database とは、アプリ開発者がビルドされるのみインテリジェント クラウド データベース サービスです。 その場で、マルチ テナント アプリを効率的に配信するためのダウンタイムなしの拡大/縮小する唯一のクラウド データベース サービスです。 最終的には、Azure SQL Database には、お客様はイノベーションに多くの時間が離れるし、市場投入時間、高速化します。 セキュリティで保護されたアプリを構築し、言語と必要なプラットフォームを使用して、SQL database に接続できます。

Azure SQL Database には次の利点があります。

- 学習し、アプリに適応する組み込みのインテリジェンス (機械学習)

- オンデマンドでのデータベースのプロビジョニング

- すべてのワークロード向けのプランの範囲

- 99.99% の可用性 SLA、0 個のメンテナンス

- データ保護のための Geo レプリケーションと復元サービス

- Azure SQL Database の特定時点に復元機能

- ハイブリッドや移行など、SQL Server 2016 との互換性

標準の Azure SQL Database は、Azure SQL Database マネージ インスタンスよりも近い PaaS のためです。 管理されたクラウドからより多くのメリットになるために、標準の Azure SQL Database を優先します。 ただし、Azure SQL Database が正規の主な相違点と、オンプレミスの SQL Server インスタンス。 によって、既存のアプリケーションのデータベースの要件、および enterprise の要件とポリシー、その可能性がありますできない最適な選択肢、クラウドへの移行を計画する場合。

## <a name="when-to-move-your-original-rdbms-to-a-vm-iaas"></a>場合に、元の RDBMS を VM (IaaS) に移動するには

移行オプションの 1 つは、元のリレーショナル データベース管理システム (RDBMS) では、Oracle、IBM DB2、MySQL、PostgreSQL、または SQL Server を含む Azure VM で実行されているようなサーバーを移動します。 最小限の変更、またはまったく変更せずにクラウドへの移行を最速をまったく必要とする既存のアプリケーションがある場合は、クラウドで IaaS への直接の移行が公正なオプションにあります。 すべてのクラウドの利点を活用するために最善の方法ができない可能性がありますが、最も高速な初期パスである可能性があります。

現時点では、Microsoft Azure がサポートする最大[331 の別のデータベース サーバー](https://azuremarketplace.microsoft.com/en-us/marketplace/apps/category/databases?page=1&subcategories=databases-all) IaaS Vm としてデプロイします。 SQL Server、Oracle、MySQL、PostgreSQL、および IBM DB2 の場合のような一般的な RDBMS および MongoDB、Cassandra、DataStax、MariaDB、Cloudera などの他の多くの NoSQL データベースが含まれます。

> [!NOTE]
> 移動するは、RDBMS に Azure VM (IaaS のため)、データをクラウドに移行する最も簡単な方法があります、このアプローチには、(データベース管理者および IT プロフェッショナル) は、IT チームにかなりの投資が必要があります。 企業のチームは、設定および高可用性、ディザスター リカバリー、および SQL Server の修正プログラムを管理することができる必要があります。 このコンテキストでは、完全な管理者権限を持つ、カスタマイズされた環境も必要です。

## <a name="when-to-migrate-to-sql-server-as-a-vm-iaas"></a>VM (IaaS) として SQL Server へ移行するタイミング

いくつかのケースもする必要がある通常の VM と SQL Server への移行である可能性があります。 シナリオの例では、SQL Server Reporting Services を使用する必要があるかどうかです。 ほとんどの場合、Azure SQL Database マネージ インスタンスを提供できますすべての SQL Server VM への移行、最後の手段を試すために、オンプレミスの SQL server から移行する必要があります。

## <a name="use-azure-database-migration-service-to-migrate-your-relational-databases-to-azure"></a>Azure Database Migration Service を使用して、リレーショナル データベースを Azure に移行するには 

ターゲット データベースが Azure SQL Database、Azure SQL Database マネージ インスタンス、または Azure VM 上の SQL Server であるかどうかを Azure に SQL Server、Oracle、MySQL などのリレーショナル データベースを移行するのに Azure Database Migration Service を使用することができます。

評価がレポートで、自動化されたワークフローでは、データベースを移行する前にする必要がある変更を説明します。 準備ができたら、サービスは、ソース データベースを Azure に移行します。

元の RDBMS を変更するたびに再テストする必要があります。 また、SQL 文またはテストの結果に応じて、アプリケーション内のオブジェクト リレーショナル マッピング (ORM) コードを変更する必要があります。

その他のデータベース (IBM DB2 など) があり、リフト アンド シフトのアプローチを選択した場合より複雑なデータ移行を実行する意思がないを引き続き Azure では、IaaS Vm としてこれらのデータベースを使用する可能性があります。 複雑なデータ移行は、新しいスキーマとさまざまなプログラミング ライブラリで別のデータベース型に移行するため、追加の作業が必要です。

Azure Database Migration Service を使用してデータベースを移行する方法については、[Azure SQL Database マネージ インスタンスと Azure Database Migration Service を迅速にクラウドに](https://channel9.msdn.com/Events/Build/2017/P4008)を参照してください。

## <a name="additional-resources"></a>その他の技術情報

- **クラウド SQL Server オプションを選択します。Azure SQL Database (PaaS) または Azure VM (IaaS) 上の SQL Server**

    [https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas](https://docs.microsoft.com/azure/sql-database/sql-database-paas-vs-sql-server-iaas)

- **Azure SQL DB マネージ インスタンスとデータベース移行サービスで迅速にクラウドに**

    [https://channel9.msdn.com/Events/Build/2017/P4008](https://channel9.msdn.com/Events/Build/2017/P4008)

- **SQL Server データベースのクラウド内の SQL Database への移行**

    [https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate](https://docs.microsoft.com/azure/sql-database/sql-database-cloud-migrate)

- **Azure SQL Database**

    [https://azure.microsoft.com/services/sql-database/?v=16.50](https://azure.microsoft.com/services/sql-database/?v=16.50)

- **Virtual machines における SQL Server**

    [https://azure.microsoft.com/services/virtual-machines/sql-server/](https://azure.microsoft.com/services/virtual-machines/sql-server/)

> [!div class="step-by-step"]
> [前へ](lift-and-shift-existing-apps-azure-iaas.md)
> [次へ](modernize-existing-apps-to-cloud-optimized/index.md)
