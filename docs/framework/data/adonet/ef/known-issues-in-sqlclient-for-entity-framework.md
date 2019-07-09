---
title: Entity Framework 用の .NET Framework Data Provider for SQL Server (SqlClient) の既知の問題
ms.date: 03/30/2017
ms.assetid: 48fe4912-4d0f-46b6-be96-3a42c54780f6
ms.openlocfilehash: 8cadb234ffc0f00049edd0c09475031eeec275df
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662270"
---
# <a name="known-issues-in-sqlclient-for-entity-framework"></a>Entity Framework 用の .NET Framework Data Provider for SQL Server (SqlClient) の既知の問題
ここでは、.NET Framework Data Provider for SQL Server (SqlClient) に関連する既知の問題について説明します。  
  
## <a name="trailing-spaces-in-string-functions"></a>文字列関数の末尾のスペース  
 SQL Server では、文字列値の末尾のスペースは無視されます。 そのため、文字列の末尾にスペースを挿入すると、予期できない結果が生じたり、場合によってはエラーが発生することもあります。  
  
 文字列の末尾のスペースがある場合は、SQL Server は、文字列をトリミングされないように、末尾に空白文字を追加することを検討してください。 末尾のスペースが不要である場合は、クエリ パイプラインに渡す前にスペースを削除してください。  
  
## <a name="right-function"></a>RIGHT 関数  
 `RIGHT(nvarchar(max)`, 0`)` または `RIGHT(varchar(max)`, 0`)` に、最初の引数として `null` 以外の値を、2 番目の引数として 0 を渡すと、`empty` 文字列の代わりに `NULL` 値が返されます。  
  
## <a name="cross-and-outer-apply-operators"></a>CROSS APPLY 演算子および OUTER APPLY 演算子  
 クロスおよび OUTER APPLY 演算子は、SQL Server 2005 で導入されました。 場合によっては、クエリ パイプラインにより、CROSS APPLY 演算子または OUTER APPLY 演算子を含む Transact-SQL ステートメントが生成されることがあります。 SQL Server 2005 より前のバージョンの SQL Server を含む、一部のバックエンド プロバイダーはこれらの演算子がサポートされないために、これらのバックエンド プロバイダーでこのようなクエリを実行できません。  
  
 CROSS APPLY 演算子または OUTER APPLY 演算子を含むクエリの生成につながる可能性がある一般的なシナリオを次に示します。  
  
- ページングを使用した相関サブクエリ  
  
- 相関サブクエリ全体、またはナビゲーションによって生成されたコレクション全体を対象とした `AnyElement`  
  
- 要素セレクターを受け取るグループ化メソッドを使用する LINQ クエリ  
  
- CROSS APPLY 演算子または OUTER APPLY 演算子が明示的に指定されたクエリ  
  
- REF コンストラクターを引数に取る DEREF コンストラクターを含むクエリ。  
  
## <a name="skip-operator"></a>SKIP 演算子  
 SQL Server 2000 を使用している場合は、非キー列で ORDER BY と共に SKIP を使用と正しくない結果を返す可能性があります。 キー以外の列に重複するデータが存在する場合、指定された数を超える行はスキップされます。 これは SQL Server 2000 の SKIP が変換される方法です。 たとえば、次のクエリでは、5 つを超える行場合はスキップされます`E.NonKeyColumn`重複した値。  
  
```  
SELECT [E] FROM Container.EntitySet AS [E] ORDER BY [E].[NonKeyColumn] DESC SKIP 5L  
```  
  
## <a name="targeting-the-correct-sql-server-version"></a>適切なバージョンの SQL Server を対象としたクエリの実行  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]で指定されている SQL Server のバージョンに基づく TRANSACT-SQL クエリを対象と、`ProviderManifestToken`ストレージ モデル (.ssdl) ファイル内のスキーマ要素の属性です。 このバージョンは、実際に接続する SQL Server のバージョンとは異なる場合があります。 たとえば、SQL Server 2005 を使用している場合でも、皆さん`ProviderManifestToken`属性が 2008年に設定されて、生成された TRANSACT-SQL クエリは、のサーバーで実行されない可能性があります。 たとえば、SQL Server 2008 で導入された新しい日時型を使用するクエリは、SQL Server の以前のバージョンでは実行されません。 SQL Server 2005 を使用している場合でも、皆さん`ProviderManifestToken`属性が 2000年に設定されて、生成された TRANSACT-SQL クエリを小さい最適化された可能性があります、またはクエリがサポートされていないことを示す例外が発生する可能性があります。 詳細については、このトピックの「CROSS APPLY 演算子および OUTER APPLY 演算子」を参照してください。  
  
 データベースの一部の動作は、データベースの互換性レベルの設定に依存します。 場合、`ProviderManifestToken`属性 2005年に設定されて、SQL Server のバージョンが 2005 がデータベースの互換性レベルが「80」(SQL Server 2000) に設定は、TRANSACT-SQL が生成された SQL Server 2005 をターゲットが期日に期待どおりに実行できないこと、互換性レベルの設定。 たとえば、ORDER BY リストの列名とセレクターの列名が一致する場合、順序付けが失われることがあります。  
  
## <a name="nested-queries-in-projection"></a>投影内の入れ子になったクエリ  
 projection 句内の入れ子になったクエリは、サーバーでデカルト積に変換されないことがあります。 SLQ Server など、一部のバック エンド サーバーでこの TempDB テーブルに非常に大きくなる可能性があります。 サーバーのパフォーマンスが低下する可能性があります。  
  
 projection 句内の入れ子になったクエリの例を次に示します。  
  
```  
SELECT c, (SELECT c, (SELECT c FROM AdventureWorksModel.Vendor AS c  ) As Inner2 FROM AdventureWorksModel.JobCandidate AS c  ) As Inner1 FROM AdventureWorksModel.EmployeeDepartmentHistory AS c  
```  
  
## <a name="server-generated-guid-identity-values"></a>サーバー生成の GUID ID 値  
 [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] では、サーバー生成の GUID 型 ID 値がサポートされますが、プロバイダーは、サーバー生成の ID 値を行の挿入後に返す動作をサポートする必要があります。 SQL Server 2005 以降、戻れますサーバー生成 GUID 型を使用して SQL Server データベースで、 [OUTPUT 句](https://go.microsoft.com/fwlink/?LinkId=169400)します。  
  
## <a name="see-also"></a>関連項目

- [Entity Framework 用 SqlClient](../../../../../docs/framework/data/adonet/ef/sqlclient-for-the-entity-framework.md)
- [LINQ to Entities の既知の問題および注意点](../../../../../docs/framework/data/adonet/ef/language-reference/known-issues-and-considerations-in-linq-to-entities.md)
