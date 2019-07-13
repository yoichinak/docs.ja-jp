---
title: Entity SQL 言語
ms.date: 03/30/2017
ms.assetid: 9e7d8837-28c5-429d-a824-7bafb59724cf
ms.openlocfilehash: ecbf9bc555594d205281237559037ac2a0e1cdb0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64631706"
---
# <a name="entity-sql-language"></a>Entity SQL 言語
Entity SQL は、ストレージに依存しない SQL と似たクエリ言語です。 Entity SQL を使用すると、オブジェクトとして、または表形式でエンティティ データに対してクエリを実行できます。 次の場合には Entity SQL の使用を検討してください。  
  
- クエリを実行時に動的に作成する必要がある場合。 その場合、実行時に Entity SQL クエリ文字列を作成する代わりに、<xref:System.Data.Objects.ObjectQuery%601> のクエリ ビルダー メソッドを使用することも検討してください。  
  
- モデル定義の一部としてクエリを定義する場合。 データ モデルでは Entity SQL のみがサポートされます。 詳細については、次を参照してください[QueryView 要素 (MSL)。](/ef/ef6/modeling/designer/advanced/edmx/msl-spec#queryview-element-msl)  
  
- EntityClient で <xref:System.Data.EntityClient.EntityDataReader> を使用して行セットとして読み取り専用エンティティ データを返す場合。 詳細については、次を参照してください。 [Entity Framework 用の EntityClient プロバイダー](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)します。  
  
- SQL ベースのクエリ言語に詳しい場合、Entity SQL の使用が最も適切に思われるでしょう。  
  
## <a name="using-entity-sql-with-the-entityclient-provider"></a>Entity SQL と EntityClient プロバイダーの使用  
 Entity SQL を EntityClient プロバイダーと一緒に使用する際の詳細については、次のトピックを参照してください。  
  
 [Entity Framework 用の EntityClient プロバイダー](../../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)  
  
 [方法: EntityConnection の接続文字列を作成します。](../../../../../../docs/framework/data/adonet/ef/how-to-build-an-entityconnection-connection-string.md)  
  
 [方法: PrimitiveType 結果を返すクエリを実行します。](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [方法: StructuralType 結果を返すクエリを実行します。](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [方法: RefType 結果を返すクエリを実行します。](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [方法: 複合型を返すクエリを実行します。](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-complex-types.md)  
  
 [方法: 入れ子になったコレクションを返すクエリを実行します。](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [方法: EntityCommand を使用してパラメーター化 Entity SQL クエリを実行します。](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [方法: EntityCommand を使用してパラメーター化されたストアド プロシージャを実行します。](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [方法: ポリモーフィック クエリを実行します。](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-polymorphic-query.md)  
  
 [方法: リレーションシップをナビゲート、Navigate 演算子](../../../../../../docs/framework/data/adonet/ef/how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="using-entity-sql-with-object-queries"></a>Entity SQL とオブジェクト クエリの使用  
 Entity SQL をオブジェクト クエリと一緒に使用する際の詳細については、次のトピックを参照してください。  
  
 [方法: エンティティ型のオブジェクトを返すクエリを実行します。](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738694(v=vs.100))  
  
 [方法: パラメーター化クエリを実行します。](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738521(v=vs.100))  
  
 [方法: ナビゲーション プロパティを使用してリレーションシップを移動します。](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896321(v=vs.100))  
  
 [方法: ユーザー定義関数を呼び出す](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd490951(v=vs.100))  
  
 [方法: データをフィルター処理します。](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716755(v=vs.100))  
  
 [方法: データの並べ替え](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716784(v=vs.100))  
  
 [方法: データをグループ化](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896341(v=vs.100))  
  
 [方法: 集計データ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716738(v=vs.100))  
  
 [方法: 匿名型オブジェクトを返すクエリを実行します。](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738512(v=vs.100))  
  
 [方法: プリミティブ型のコレクションを返すクエリを実行します。](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738451(v=vs.100))  
  
 [方法: EntityCollection 内の関連オブジェクトをクエリします。](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc716708(v=vs.100))  
  
 [方法: 2 つのクエリの結合を並べ替える](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896299(v=vs.100))  
  
 [方法: クエリ結果 ページ](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))  
  
## <a name="in-this-section"></a>このセクションの内容  
 [Entity SQL の概要](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
  
 [Entity SQL リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
  
## <a name="see-also"></a>関連項目

- [ADO.NET Entity Framework](../../../../../../docs/framework/data/adonet/ef/index.md)
- [言語リファレンス](../../../../../../docs/framework/data/adonet/ef/language-reference/index.md)
