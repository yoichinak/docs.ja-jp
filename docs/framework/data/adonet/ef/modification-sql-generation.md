---
title: 変更 SQL 生成
ms.date: 03/30/2017
ms.assetid: 2188a39d-46ed-4a8b-906a-c9f15e6fefd1
ms.openlocfilehash: 13ed7186981e82d47f00b6a38a4328ed75f527f4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034139"
---
# <a name="modification-sql-generation"></a>変更 SQL 生成

ここでは、SQL:1999 準拠のデータベース プロバイダーのための変更 SQL 生成モジュールを開発する方法について説明します。 このモジュールは、変更コマンド ツリーを適切な SQL INSERT ステートメント、UPDATE ステートメント、または DELETE ステートメントに変換します。

Select ステートメントの SQL 生成の詳細については、次を参照してください。 [SQL 生成](../../../../../docs/framework/data/adonet/ef/sql-generation.md)します。

## <a name="overview-of-modification-command-trees"></a>変更コマンド ツリーの概要

変更 SQL 生成モジュールは、指定された入力 DbModificationCommandTree に基づいて、データベースに固有の変更 SQL ステートメントを生成します。

DbModificationCommandTree は、DbCommandTree から継承される変更 DML 操作 (挿入、更新、または削除操作) のオブジェクト モデル表現です。 DbModificationCommandTree には、次の 3 つの実装があります。

- DbInsertCommandTree

- DbUpdateCommandTree

- DbDeleteCommandTree

DbModificationCommandTree とその実装によって生成される、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]常に単一行の操作を表します。 ここでは、これら 3 つの種類の実装と、.NET Framework Version 3.5 における制約について説明します。

![Diagram](../../../../../docs/framework/data/adonet/ef/media/558ba7b3-dd19-48d0-b91e-30a76415bf5f.gif "558ba7b3-dd19-48d0-b91e-30a76415bf5f")

DbModificationCommandTree には、変更操作のターゲット セットを表す Target プロパティがあります。 入力セットを定義する Target の Expression プロパティは、常に DbScanExpression です。  DbScanExpression は、どちらか、テーブルまたはビューを表すことができます。 または一連のデータ定義クエリ メタデータ プロパティを"Defining Query"、ターゲットの場合は null 以外。

モデル内で定義クエリを使用してセットが定義されているが、対応する変更操作のための関数が指定されていない場合、クエリを表す DbScanExpression は、変更のターゲットとしてプロバイダーにのみ影響を与えます。 プロバイダーによっては、このようなシナリオはサポートされません (たとえば、SqlClient ではサポートされません)。

DbInsertCommandTree は、コマンド ツリーとして表現される、単一行の挿入操作を表します。

```csharp
public sealed class DbInsertCommandTree : DbModificationCommandTree {
   public IList<DbModificationClause> SetClauses { get }
   public DbExpression Returning { get }
}
```

DbUpdateCommandTree は、コマンド ツリーとして表現される、単一行の更新操作を表します。

DbDeleteCommandTree は、コマンド ツリーとして表現される、単一行の削除操作を表します。

### <a name="restrictions-on-modification-command-tree-properties"></a>変更コマンド ツリーのプロパティの制限

変更コマンド ツリーのプロパティに対して、次の情報および制限が適用されます。

#### <a name="returning-in-dbinsertcommandtree-and-dbupdatecommandtree"></a>DbInsertCommandTree および DbUpdateCommandTree の Returning

null 以外の場合、Returning は、コマンドがリーダーを返すことを示します。 null の場合、コマンドは、影響を受けた (挿入または更新された) 行の数を示すスカラー値を返します。

Returning 値は、挿入または更新された行に基づいて返される結果の射影を指定します。 この値は、行を表す DbNewInstanceExpression 型である必要があります。その各引数は、対応する DbModificationCommandTree の Target への参照を表す DbVariableReferenceExpression に対する DbPropertyExpression になります。 Returning プロパティで使用されている DbPropertyExpressions で表されるプロパティは、常にストア生成値または計算値となります。 DbInsertCommandTree では、行が挿入されるテーブルの 1 つ以上のプロパティがストア生成値または計算値として指定されている (ssdl で StoreGeneratedPattern.Identity または StoreGeneratedPattern.Computed とマークされている) 場合、Returning は null ではありません。 DbUpdateCommandTrees では、行が更新されるテーブルの 1 つ以上のプロパティがストア計算値として指定されている (ssdl で StoreGeneratedPattern.Computed とマークされている) 場合、Returning は null ではありません。

#### <a name="setclauses-in-dbinsertcommandtree-and-dbupdatecommandtree"></a>DbInsertCommandTree および DbUpdateCommandTree の SetClauses

SetClauses は、挿入または更新操作を定義する insert set 句または update set 句のリストを指定します。

```
The elements of the list are specified as type DbModificationClause, which specifies a single clause in an insert or update modification operation. DbSetClause inherits from DbModificationClause and specifies the clause in a modification operation that sets the value of a property. Beginning in version 3.5 of the .NET Framework, all elements in SetClauses are of type SetClause.
```

Property は、更新する必要があるプロパティを指定します。 これは常に、対応する DbModificationCommandTree の Target への参照を表す、DbVariableReferenceExpression に対する DbPropertyExpression です。

Value は、プロパティを更新するための新しい値を指定します。 DbConstantExpression 型または DbNullExpression 型を使用できます。

#### <a name="predicate-in-dbupdatecommandtree-and-dbdeletecommandtree"></a>DbUpdateCommandTree および DbDeleteCommandTree の Predicate

Predicate は、ターゲット コレクションのどのメンバーを更新または削除する必要があるかを判定するために使用される述語を指定します。 これは、DbExpressions の次のサブセットから構成される式ツリーです。

- Equals 型の DbComparisonExpression、右辺の子、DbPropertyExpression として以下に制限されていると、左辺の子は DbConstantExpression です。

- DbConstantExpression

- 以下として制限 DbPropertyExpression で DbIsNullExpression

- 対応する DbModificationCommandTree の Target への参照を表す、DbVariableReferenceExpression に対する DbPropertyExpression。

- DbAndExpression。

- DbNotExpression

- DbOrExpression。

## <a name="modification-sql-generation-in-the-sample-provider"></a>サンプル プロバイダーでの変更 SQL 生成

[Entity Framework サンプル プロバイダー](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0)をサポートする ADO.NET データ プロバイダーのコンポーネントを示して、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]します。 このサンプルは、SQL Server 2005 データベースを対象としており、System.Data.SqlClient ADO.NET 2.0 データ プロバイダーの最上位にラッパーとして実装されます。

SQL Generation\DmlSqlGenerator.cs ファイル内にあるサンプル プロバイダーの変更 SQL 生成モジュールは、DbModificationCommandTree を入力として受け取り、単一の変更 SQL ステートメントを生成します。この後に、DbModificationCommandTree によって指定された場合にリーダーを返す SELECT ステートメントが続く場合もあります。 生成されたコマンドの構造は、対象の SQL Server データベースの影響を受けます。

### <a name="helper-classes-expressiontranslator"></a>ヘルパー クラス。ExpressionTranslator

ExpressionTranslator は、DbExpression 型のすべての変更コマンド ツリー プロパティのための一般的な軽量のトランスレーターです。 このトランスレーターは、変更コマンド ツリーのプロパティを制限する式の型の変換のみをサポートし、特定の制約を考慮して構築されています。

以降では、特定の式の型へのアクセスについて説明します (重要度の低い変換を含むノードは省略しています)。

### <a name="dbcomparisonexpression"></a>DbComparisonExpression

preserveMemberValues を true に設定して ExpressionTranslator を構築したときに、右辺の定数が (DbNullExpression ではなく) DbConstantExpression である場合、左辺のオペランド (DbPropertyExpressions) が DbConstantExpression に関連付けられます。 これは、返される Select ステートメントを、影響を受けた行を識別するために生成する必要がある場合に使用されます。

### <a name="dbconstantexpression"></a>DbConstantExpression

アクセスされる定数のそれぞれに対して、パラメーターが作成されます。

### <a name="dbpropertyexpression"></a>DbPropertyExpression

DbPropertyExpression のインスタンスが常に入力テーブルを表す場合、生成によって別名が作成される状況を除き (テーブル変数が使用されたときの更新シナリオでのみこの状況が発生します)、入力に別名を指定する必要はありません。変換には既定でプロパティ名が使用されます。

## <a name="generating-an-insert-sql-command"></a>挿入 SQL コマンドの生成

サンプル プロバイダーで指定されている DbInsertCommandTree に対して生成される挿入コマンドは、以下に示す 2 つの挿入テンプレートのどちらかに基づいています。

1 つ目のテンプレートには、SetClauses のリストの値を受け取って挿入を実行するコマンドと、挿入された行の Returning プロパティが null 以外の場合にその Returning プロパティで指定されたプロパティを返す SELECT ステートメントが含まれています。 述語要素"\@ @ROWCOUNT > 0" は行が挿入された場合は true。 述語要素"keyMemberI = keyValueI &#124; scope_identity()"図形は、"keyMemberI = scope_identity()"keyMemberI がストア生成キーの場合 scope_identity() では、identity (に挿入された最後の id 値を返すためにのみ列のストア生成)。

```sql
-- first insert Template
INSERT <target>   [ (setClauseProperty0, .. setClausePropertyN)]
VALUES (setClauseValue0, .. setClauseValueN) |  DEFAULT VALUES

[SELECT <returning>
 FROM <target>
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]
```

2 番目のテンプレートが必要となるのは、挿入操作で行の挿入を指定するとき、主キーがストア生成値であるが整数型ではないために、scope_identity() でそのキーを使用できない場合です。 このテンプレートは、複合ストア生成キーがある場合にも使用されます。

```sql
-- second insert template
DECLARE @generated_keys TABLE [(keyMember0, … keyMemberN)

INSERT <target>   [ (setClauseProperty0, .. setClausePropertyN)]
 OUTPUT inserted.KeyMember0, …, inserted.KeyMemberN INTO @generated_keys
 VALUES (setClauseValue0, .. setClauseValueN) |  DEFAULT VALUES

[SELECT <returning_over_t>
 FROM @generated_keys  AS g
JOIN <target> AS t ON g.KeyMember0 = t.KeyMember0 AND … g.KeyMemberN = t.KeyMemberN
 WHERE @@ROWCOUNT > 0
```

サンプル プロバイダーに含まれるモデルの使用例を次に示します。 この例では、DbInsertCommandTree から挿入コマンドを生成しています。

次のコードは、Category を挿入します。

```csharp
using (NorthwindEntities northwindContext = new NorthwindEntities()) {
   Category c = new Category();
   c.CategoryName = "Test Category";
   c.Description = "A new category for testing";
   northwindContext.AddObject("Categories", c);
   northwindContext.SaveChanges();
}
```

このコードでは、プロバイダーに渡される次のコマンド ツリーを生成します。

```
DbInsertCommandTree
|_Parameters
|_Target : 'target'
| |_Scan : dbo.Categories
|_SetClauses
| |_DbSetClause
| | |_Property
| | | |_Var(target).CategoryName
| | |_Value
| |   |_'Test Category'
| |_DbSetClause
| | |_Property
| | | |_Var(target).Description
| | |_Value
| |   |_'A new category for testing'
| |_DbSetClause
|   |_Property
|   | |_Var(target).Picture
|   |_Value
|     |_null
|_Returning
  |_NewInstance : Record['CategoryID'=Edm.Int32]
    |_Column : 'CategoryID'
      |_Var(target).CategoryID
```

サンプル プロバイダーによって生成されるストア コマンドは、次の SQL ステートメントです。

```sql
insert [dbo].[Categories]([CategoryName], [Description], [Picture])
values (@p0, @p1, null)
select [CategoryID]
from [dbo].[Categories]
where @@ROWCOUNT > 0 and [CategoryID] = scope_identity()
```

## <a name="generating-an-update-sql-command"></a>更新 SQL コマンドの生成

指定された DbUpdateCommandTree に対して、以下に示すテンプレートに基づいて、更新コマンドが生成されます。

```sql
-- UPDATE Template
UPDATE <target>
SET setClauseProperty0 = setClauseValue0, .. setClausePropertyN = setClauseValueN  | @i = 0
WHERE <predicate>

[SELECT <returning>
 FROM <target>
 WHERE @@ROWCOUNT > 0 AND keyMember0 = keyValue0 AND .. keyMemberI =  keyValueI | scope_identity()  .. AND  keyMemberN = keyValueN]
```

Set 句が偽の set 句 ("@i = 0") set 句が指定されていない場合にのみです。 これは、ストア計算列が再計算されるようにするためです。

Returning プロパティが null でない場合にのみ、SELECT ステートメントが生成され、Returning プロパティに指定されたプロパティが返されます。

次の例では、サンプル プロバイダーに含まれるモデルを使用して、更新コマンドを生成します。

次のユーザー コードは、Category を更新します。

```csharp
using (NorthwindEntities northwindContext = new NorthwindEntities()) {
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "Test Category").First();
   c.CategoryName = "New test name";
   northwindContext.SaveChanges();
}
```

このユーザー コードは、プロバイダーに渡される次のコマンド ツリーを生成します。

```
DbUpdateCommandTree
|_Parameters
|_Target : 'target'
| |_Scan : dbo.Categories
|_SetClauses
| |_DbSetClause
|   |_Property
|   | |_Var(target).CategoryName
|   |_Value
|     |_'New test name'
|_Predicate
| |_
|   |_Var(target).CategoryID
|   |_=
|   |_10
|_Returning
```

サンプル プロバイダーによって、次のストア コマンドが生成されます。

```sql
update [dbo].[Categories]
set [CategoryName] = @p0
where ([CategoryID] = @p1)
```

### <a name="generating-a-delete-sql-command"></a>削除 SQL コマンドの生成

指定された DbDeleteCommandTree に対して、以下に示すテンプレートに基づいて、削除コマンドが生成されます。

```sql
-- DELETE Template
DELETE <target>
WHERE <predicate>
```

次の例では、サンプル プロバイダーに含まれるモデルを使用して、削除コマンドを生成します。

次のユーザー コードは、Category を削除します。

```csharp
using (NorthwindEntities northwindContext = new NorthwindEntities()) {
   Category c = northwindContext.Categories.Where(i => i.CategoryName == "New test name").First();
   northwindContext.DeleteObject(c);
   northwindContext.SaveChanges();
}
```

このユーザー コードは、プロバイダーに渡される次のコマンド ツリーを生成します。

```
DbDeleteCommandTree
|_Parameters
|_Target : 'target'
| |_Scan : dbo.Categories
|_Predicate
  |_
    |_Var(target).CategoryID
    |_=
    |_10
```

サンプル プロバイダーによって、次のストア コマンドが生成されます。

```sql
delete [dbo].[Categories]
where ([CategoryID] = @p0)
```

## <a name="see-also"></a>関連項目

- [Entity Framework データ プロバイダーの作成](../../../../../docs/framework/data/adonet/ef/writing-an-ef-data-provider.md)
