---
title: Entity Framework 用の EntityClient プロバイダー
ms.date: 03/30/2017
ms.assetid: 8c5db787-78e6-4a34-8dc1-188bca0aca5e
ms.openlocfilehash: 70cc5a9aaa22cc563c910f9d250ad4565e34a135
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251600"
---
# <a name="entityclient-provider-for-the-entity-framework"></a>Entity Framework 用の EntityClient プロバイダー
EntityClient プロバイダーは、概念モデルで記述されているデータにアクセスするために Entity Framework アプリケーションで使用するデータ プロバイダーです。 概念モデルの詳細については、「[モデリングとマッピング](modeling-and-mapping.md)」を参照してください。 EntityClient は、他の .NET Framework データ プロバイダーを使用してデータ ソースにアクセスします。 たとえば、EntityClient は、SQL Server データベースにアクセスするときは .NET Framework Data Provider for SQL Server (SqlClient) を使用します。 SqlClient プロバイダーの詳細については、「 [Entity Framework の sqlclient](sqlclient-for-the-entity-framework.md)」を参照してください。 EntityClient プロバイダーは <xref:System.Data.EntityClient> 名前空間で実装されます。  
  
## <a name="managing-connections"></a>接続の管理  
 は[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] 、基になるデータプロバイダーおよびリレーショナルデータベース<xref:System.Data.EntityClient.EntityConnection>にを提供することにより、ストレージ固有の ADO.NET データプロバイダーの上に構築されます。 <xref:System.Data.EntityClient.EntityConnection>オブジェクトを構築するには、必要なモデルとマッピング、さらにストレージ固有のデータプロバイダー名と接続文字列を含むメタデータのセットを参照する必要があります。 <xref:System.Data.EntityClient.EntityConnection>が配置されると、概念モデルから生成されたクラスを使用してエンティティにアクセスできます。  
  
 app.config ファイルの接続文字列を指定できます。  
  
 <xref:System.Data.EntityClient> には、<xref:System.Data.EntityClient.EntityConnectionStringBuilder> クラスも含まれています。 このクラスを使用すると、開発者はこのクラスのプロパティおよびメソッドを使用することによって、正しい構文の接続文字列をプログラムで作成し、既存の接続文字列の解析や再作成を行うことができます。 詳細については、「[方法 :EntityConnection 接続文字列](how-to-build-an-entityconnection-connection-string.md)を作成します。  
  
## <a name="creating-queries"></a>クエリの作成  
 この[!INCLUDE[esql](../../../../../includes/esql-md.md)]言語は、概念エンティティスキーマで直接動作し、継承やリレーションシップなどの Entity Data Model の概念をサポートする、ストレージに依存しない SQL の言語です。 クラスは、エンティティモデルに対し[!INCLUDE[esql](../../../../../includes/esql-md.md)]てコマンドを実行するために使用されます。 <xref:System.Data.EntityClient.EntityCommand> <xref:System.Data.EntityClient.EntityCommand> オブジェクトを構築する場合は、ストアド プロシージャ名またはクエリ テキストを指定できます。 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] は、ストレージ固有のデータ プロバイダーと連携し、汎用的な [!INCLUDE[esql](../../../../../includes/esql-md.md)] をストレージ固有のクエリに変換します。 クエリの記述[!INCLUDE[esql](../../../../../includes/esql-md.md)]の詳細については、「 [Entity SQL 言語](./language-reference/entity-sql-language.md)」を参照してください。  
  
 次の例では<xref:System.Data.EntityClient.EntityCommand> 、オブジェクトを作成[!INCLUDE[esql](../../../../../includes/esql-md.md)]し、クエリテキスト<xref:System.Data.EntityClient.EntityCommand.CommandText%2A?displayProperty=nameWithType>をそのプロパティに割り当てます。 この[!INCLUDE[esql](../../../../../includes/esql-md.md)]クエリでは、概念モデルのリスト価格で並べ替えられた製品を要求します。 次のコードでは、ストレージ モデルが認識されません。  
  
 ```csharp
EntityCommand cmd = conn.CreateCommand();
cmd.CommandText = @"SELECT VALUE p
  FROM AdventureWorksEntities.Product AS p
  ORDER BY p.ListPrice";
```
  
## <a name="executing-queries"></a>クエリの実行  
 クエリを実行すると、そのクエリが解析され、正規コマンド ツリーに変換されます。 すべての後続の処理は、コマンド ツリーで行われます。 コマンドツリーは、 <xref:System.Data.EntityClient>と、基になる .NET Framework データプロバイダー (など<xref:System.Data.SqlClient>) との間の通信手段です。  
  
 概念モデルに対する <xref:System.Data.EntityClient.EntityDataReader> の実行結果は、<xref:System.Data.EntityClient.EntityCommand> によって公開されます。 <xref:System.Data.EntityClient.EntityDataReader> を返すコマンドを実行するには、<xref:System.Data.EntityClient.EntityCommand.ExecuteReader%2A> を呼び出します。 <xref:System.Data.EntityClient.EntityDataReader> は、構造化されたさまざまな結果を記述するための <xref:System.Data.IExtendedDataRecord> を実装します。  
  
## <a name="managing-transactions"></a>トランザクションの管理  
 Entity Framework では、自動トランザクションと明示的トランザクションという 2 つの使用方法があります。 自動トランザクションでは <xref:System.Transactions> 名前空間を使用し、明示的トランザクションでは <xref:System.Data.EntityClient.EntityTransaction> クラスを使用します。  
  
 概念モデルを通じて公開されるデータを更新する[方法については、次を参照してください。Entity Framework](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738523(v=vs.100))でトランザクションを管理します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法: EntityConnection 接続文字列を作成する](how-to-build-an-entityconnection-connection-string.md)  
  
 [方法: PrimitiveType の結果を返すクエリを実行する](how-to-execute-a-query-that-returns-primitivetype-results.md)  
  
 [方法: StructuralType の結果を返すクエリを実行する](how-to-execute-a-query-that-returns-structuraltype-results.md)  
  
 [方法: RefType 結果を返すクエリを実行する](how-to-execute-a-query-that-returns-reftype-results.md)  
  
 [方法: 複合型を返すクエリの実行](how-to-execute-a-query-that-returns-complex-types.md)  
  
 [方法: 入れ子になったコレクションを返すクエリを実行する](how-to-execute-a-query-that-returns-nested-collections.md)  
  
 [方法: EntityCommand を使用してパラメーター化された Entity SQL クエリを実行する](how-to-execute-a-parameterized-entity-sql-query-using-entitycommand.md)  
  
 [方法: EntityCommand を使用してパラメーター化されたストアドプロシージャを実行する](how-to-execute-a-parameterized-stored-procedure-using-entitycommand.md)  
  
 [方法: ポリモーフィックなクエリの実行](how-to-execute-a-polymorphic-query.md)  
  
 [方法: Navigate 演算子を使用したリレーションシップのナビゲート](how-to-navigate-relationships-with-the-navigate-operator.md)  
  
## <a name="see-also"></a>関連項目

- [接続とトランザクションの管理](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896325(v=vs.100))
- [ADO.NET Entity Framework](index.md)
- [言語リファレンス](./language-reference/index.md)
