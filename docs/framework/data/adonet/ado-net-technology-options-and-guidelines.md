---
title: ADO.NET テクノロジのオプションとガイドライン
ms.date: 03/30/2017
ms.assetid: c8577281-38e6-4ce5-b036-572039a4c3d8
ms.openlocfilehash: 0d0e8f7bd779ce7a8290594887630dd192301fe1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212532"
---
# <a name="adonet-technology-options-and-guidelines"></a>ADO.NET テクノロジのオプションとガイドライン
ADO.NET データ プラットフォームは、概念エンティティ データ モデルに対してプログラムを作成できるようにして、開発者に必要とされるコード作成と保守作業の量を減らすための、複数のリリースにわたる戦略です。 このプラットフォームには、ADO.NET Entity Framework と関連技術が含まれています。  
  
## <a name="entity-framework"></a>Entity Framework  
 ADO.NET Entity Framework は、開発者がリレーショナル ストレージ スキーマに対して直接プログラムを作成するのではなく、概念アプリケーション モデルに対してプログラムを作成して、データ アクセス アプリケーションを作成できるように設計されています。 その目的は、データ指向アプリケーションに必要なコードの量と保守作業の量を減らすことです。 詳細については、次を参照してください。 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)します。  
  
### <a name="entity-data-model-edm"></a>Entity Data Model (EDM)  
 エンティティ データ モデル (EDM) は、アプリケーション データをエンティティとリレーションシップの集合として定義するデザイン仕様です。 このモデルのデータは、アプリケーションの境界を越えたオブジェクト リレーショナル マッピングとデータ プログラミング機能をサポートします。  
  
### <a name="object-services"></a>オブジェクト サービス  
 Object Services を使用すると、プログラマが一連の共通言語ランタイム (CLR) クラスを介して概念モデルを操作できるようになります。 これらのクラスは、概念モデルから自動的に生成することも、概念モデルの構造を反映するように別途開発することもできます。 Object Services は、状態の管理、変更の追跡、ID の解決、リレーションシップの読み込みとナビゲート、オブジェクト変更のデータベースへの反映、Entity SQL のクエリ作成サポートなどのサービスを含む、エンティティ フレームワークに対するインフラストラクチャ サポートも提供します。 詳細は、[Object Services の概要 (Entity Framework)](https://docs.microsoft.com/previous-versions/bb386871(v=vs.100)) をご覧ください。  
  
### <a name="linq-to-entities"></a>LINQ to Entities  
 LINQ to Entities は、LINQ の式と標準クエリ演算子を使用することにより、Entity Framework オブジェクト コンテキストに対して厳密に型指定されたクエリを作成できるようにする統合言語クエリ (LINQ) の実装です。 LINQ to Entities を使用すると、開発者は Microsoft SQL Server とサードパーティ データベース間の非常に柔軟なオブジェクト リレーショナル マッピングを使用して、概念モデルを操作できます。 詳細については、次を参照してください。 [LINQ to Entities](../../../../docs/framework/data/adonet/ef/language-reference/linq-to-entities.md)します。  
  
### <a name="entity-sql"></a>Entity SQL  
 Entity SQL は、エンティティ データ モデルを操作するように設計されたテキスト ベースのクエリ言語です。 Entity SQL は、継承、複合型、明示的リレーションシップなどの高レベルのモデル概念を使用したクエリ用のコンストラクトを含む SQL 言語の一種です。 Entity SQL は、Object Services で直接使用することもできます。 詳細については、次を参照してください。 [Entity SQL 言語](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)します。  
  
### <a name="entityclient"></a>EntityClient  
 EntityClient は、エンティティ データ モデルを操作するために使用する新しい .NET Framework データ プロバイダーです。 EntityClient は、<xref:System.Data.EntityClient.EntityConnection> を返す <xref:System.Data.EntityClient.EntityCommand> および <xref:System.Data.EntityClient.EntityDataReader> オブジェクトを公開するための .NET Framework データ プロバイダーのパターンに従います。 EntityClient は Entity SQL 言語と共に使用でき、ストレージ固有のデータ プロバイダーに対する柔軟なマッピングを提供します。 詳細については、次を参照してください。 [Entity Framework 用の EntityClient プロバイダー](./ef/entityclient-provider-for-the-entity-framework.md)します。  
  
### <a name="entity-data-model-tools"></a>Entity Data Model ツール  
 Entity Framework には、EDM アプリケーションの構築を容易にするためのコマンド ライン ツール、ウィザード、およびデザイナーが用意されています。 EntityDataSource コントロールでは、EDM に基づくデータ バインドのシナリオがサポートされています。 EntityDataSource コントロールのプログラミング サーフェイスは、Visual Studio の他のデータ ソース コントロールに似ています。 詳細については、次を参照してください。 [ADO.NET Entity Data Model ツール](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))します。  
  
## <a name="linq-to-sql"></a>LINQ to SQL  
 LINQ to SQL は、.NET Framework のクラスを使用して SQL Server データベースをモデル化するオブジェクト リレーショナル マッピング (OR/M) の実装です。 LINQ to SQL では、LINQ を使用してデータベースのクエリを実行するだけでなく、そのデータベースのデータを更新、挿入、および削除することができます。 LINQ to SQL では、トランザクション、ビュー、およびストアド プロシージャをサポートし、データ検証ルールとビジネス ロジック ルールをデータ モデルに簡単に統合するための方法を提供します。 オブジェクト リレーショナル デザイナー (O/R デザイナー) を使用して、データベース内のオブジェクトに基づくエンティティ クラスと関連付けのモデル化を実行できます。 詳しくは、「[Visual Studio の LINQ to SQL ツール](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)」をご覧ください。  
  
## <a name="wcf-data-services"></a>WCF Data Services  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Web またはイントラネット上のデータ サービスをデプロイします。 データは、エンティティ データ モデルの仕様に従ってエンティティおよびリレーションシップとして構成されます。 このモデルで展開されるデータは、標準 HTTP プロトコルによってアドレス指定可能です。 詳細については、「[WCF Data Services 4.5](../../../../docs/framework/data/wcf/index.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [ADO.NET の概要](../../../../docs/framework/data/adonet/ado-net-overview.md)
- [ADO.NET の新機能](../../../../docs/framework/data/adonet/whats-new.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
