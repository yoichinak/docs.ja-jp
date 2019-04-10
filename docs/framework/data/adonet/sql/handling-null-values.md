---
title: null 値の処理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f18b288f-b265-4bbe-957f-c6833c0645ef
ms.openlocfilehash: 0d200ad35d3ab56bf97114b51b4f7fcc898eecdf
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59332145"
---
# <a name="handling-null-values"></a>null 値の処理
列の値が不明または欠落している場合は、リレーショナル データベースの NULL 値が使用されます。 NULL は空文字列 (文字または日付時刻データ型) でもゼロ値 (数値データ型) でもありません。 ANSI SQL-92 の規格では、すべてのデータ型について NULL は同一でなければならないと規定されているため、すべての NULL が一貫して処理されます。 <xref:System.Data.SqlTypes> 名前空間では、<xref:System.Data.SqlTypes.INullable> インターフェイスを実装することで NULL セマンティクスが提供されます。 <xref:System.Data.SqlTypes> 内の各データ型には、それぞれ独自に `IsNull` プロパティと `Null` 値があり、データ型のインスタンスに割り当てることができます。  
  
> [!NOTE]
>  .NET Framework version 2.0 では、NULL 許容型がサポートされました。この型を使用することで、値型を拡張して基になる型のすべての値を表すことができます。 これらの CLR NULL 許容型は、<xref:System.Nullable> 構造体のインスタンスを表します。 この機能は、値の型がボックスまたはアンボックスされるときに特に有効であり、オブジェクト型との互換性が強化されます。 ANSI SQL の NULL は `null` 参照 (Visual Basic では `Nothing`) と動作が異なるため、CLR NULL 許容型は NULL のデータベースへの格納を意図したものではありません。 データベースの ANSI SQL NULL 値を操作するには、<xref:System.Data.SqlTypes> ではなく <xref:System.Nullable> NULL を使用します。 Visual Basic での null 許容型を参照してください CLR の使用の詳細については[null 許容値型](~/docs/visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)、および c#」をご覧ください[null 許容型を使用して](~/docs/csharp/programming-guide/nullable-types/using-nullable-types.md)します。  
  
## <a name="nulls-and-three-valued-logic"></a>NULL および 3 つの値を持つロジック  
 列定義に NULL 値を許可することで、3 つの値を持つロジックをアプリケーションに定義できます。 比較によって、次の 3 つの条件のうちの 1 つを評価できます。  
  
-   True  
  
-   False  
  
-   不明  
  
 NULL は不明であるとされるため、2 つの NULL 値を相互に比較した場合、同等であるとは見なされません。 算術演算子を使用する式では、オペランドのいずれかが NULL である場合は結果も NULL になります。  
  
## <a name="nulls-and-sqlboolean"></a>NULL および SqlBoolean  
 <xref:System.Data.SqlTypes> 間の比較により、<xref:System.Data.SqlTypes.SqlBoolean> が返されます。 各 `IsNull` の `SqlType` 関数により、<xref:System.Data.SqlTypes.SqlBoolean> が返され、NULL 値の確認に使用できます。 次の truth テーブルは、NULL 値がある場合の AND、OR、および NOT 演算子の機能を示します  (T=true、F=false、U=不明または NULL)。  
  
 ![真理値表](../../../../../docs/framework/data/adonet/sql/media/truthtable-bpuedev11.gif "TruthTable_bpuedev11")  
  
### <a name="understanding-the-ansinulls-option"></a>ANSI_NULLS オプションについて  
 <xref:System.Data.SqlTypes> ANSI_NULLS オプションでは、SQL Server で設定されている場合と同じセマンティクスを提供します。 すべての算術演算子 (+、-、*、/、%)、ビットごとの演算子 (~、&、 &#124;)、ほとんどの関数が null の場合は、オペランドまたは引数のいずれかが null 以外に、プロパティ、戻って`IsNull`します。  
  
 ANSI sql-92 標準がサポートしていません*columnName* WHERE 句で NULL を = です。 SQL Server では、ANSI_NULLS オプションによって、データベース内の既定の NULL 値と、NULL 値に対する比較の評価の両方が制御されます。 ANSI_NULLS がオン (既定) である場合、IS NULL 演算子を NULL 値のテストを行う式で使用する必要があります。 たとえば次の比較では、ANSI_NULLS がオンである場合、常に不明となります。  
  
```  
colname > NULL  
```  
  
 NULL 値を含む変数との比較でも不明となります。  
  
```  
colname > @MyVariable  
```  
  
 NULL 値をテストするには、IS NULL または IS NOT NULL 述語を使用します。 これにより WHERE 句が複雑になる場合があります。 たとえば、AdventureWorks Customer テーブル内の TerritoryID 列では、NULL 値が許可されています。 SELECT ステートメントによってその他の値と合わせて NULL 値もテストされる場合は、IS NULL 述語を含める必要があります。  
  
```  
SELECT CustomerID, AccountNumber, TerritoryID  
FROM AdventureWorks.Sales.Customer  
WHERE TerritoryID IN (1, 2, 3)  
   OR TerritoryID IS NULL  
```  
  
 SQL Server で ANSI_NULLS をオフに設定すると、等値演算子を使用する式を作成し、NULL 値と比較できます。 ただし、別の接続からその接続に対して NULL オプションを設定することを防ぐことはできません。 IS NULL を使用した NULL 値のテストは、接続の ANSI_NULLS 設定にかかわらず、常に動作します。  
  
 `DataSet` では、ANSI_NULLS をオフに設定することはできません。<xref:System.Data.SqlTypes> における NULL 値の処理については、常に ANSI SQL-92 標準に準拠します。  
  
## <a name="assigning-null-values"></a>NULL 値の割り当て  
 NULL 値は特殊であり、ストレージおよび割り当てのセマンティクスは、システムおよびストレージ システムの種類によって異なります。 `Dataset` は、異なる種類のシステムおよびストレージ システムで使用できるように設計されています。  
  
 このセクションでは、異なる種類のシステム上にある <xref:System.Data.DataColumn> の <xref:System.Data.DataRow> に NULL 値を割り当てるための NULL セマンティクスについて説明します。  
  
 `DBNull.Value`  
 この割り当ては、任意の型の `DataColumn` で有効です。 その型が `INullable` を実装している場合は、`DBNull.Value` が厳密に型指定された適切な NULL 値に強制的に変換されます。  
  
 `SqlType.Null`  
 すべての <xref:System.Data.SqlTypes> データ型で `INullable` を実装します。 暗黙的なキャスト演算子を使用して、厳密に型指定された NULL 値を列のデータ型に変換できる場合は、割り当てが行われます。 変換できない場合は、無効なキャスト例外がスローされます。  
  
 `null`  
 特定の `DataColumn` データ型について 'null' が有効であった場合、`DbNull.Value` 型 (`Null`) に関連付けられている、適切な `INullable` または `SqlType.Null` に強制的に変換されます。  
  
 `derivedUdt.Null`  
 UDT 列の場合、NULL 値は常に `DataColumn` に関連付けられている型に基づいて格納されます。 `DataColumn` に関連付けられている UDT が `INullable` を実装せず、サブクラスで実装される場合を考えます。 この場合、派生クラスに関連付けられた厳密に型指定された NULL 値が割り当てられていれば、NULL ストレージが常に DataColumn のデータ型と一致するため、型指定されていない `DbNull.Value` として格納されます。  
  
> [!NOTE]
>  `Nullable<T>` または <xref:System.Nullable> 構造体は、現在 `DataSet` ではサポートされていません。  
  
### <a name="multiple-column-row-assignment"></a>複数列 (行) の割り当て  
 `DataTable.Add`、 `DataTable.LoadDataRow`、またはそのまま使用する他の Api、<xref:System.Data.DataRow.ItemArray%2A>行にマップを取得する、DataColumn の既定値に ' null' にマップします。 配列内のオブジェクトに `DbNull.Value` またはその厳密に型指定された値が含まれる場合は、上記と同じ規則が適用されます。  
  
 さらに、`DataRow.["columnName"]` の NULL 値割り当てのインスタンスには、次の規則が適用されます。  
  
1. 既定の*既定*値は`DbNull.Value`が適切な厳密に厳密に型指定された null 列に null 値が型指定された点を除いてすべて。  
  
2. XML ファイルへのシリアル化中に NULL 値が書き出されることはありません ("xsi:nil" と同じ)。  
  
3. 既定値を含む NULL 以外のすべての値は、常に XML へのシリアル化中に書き出されます。 これは、NULL 値 (xsi:nil) が明示的で既定値が暗黙的である、XSD/XML セマンティクスとは異なります (XML にない場合は、検証パーサーが関連付けられた XSD スキーマから取得します)。 逆に `DataTable` では、NULL 値が暗黙的で、既定値が明示的になります。  
  
4. XML 入力から読み取られた各行の欠落している列値にはすべて、NULL が割り当てられます。 <xref:System.Data.DataTable.NewRow%2A> または類似のメソッドを使用して作成された行には、DataColumn の既定値が割り当てられます。  
  
5. <xref:System.Data.DataRow.IsNull%2A> メソッドは、`true` と `DbNull.Value` のどちらに対しても `INullable.Null` を返します。  
  
## <a name="assigning-null-values"></a>NULL 値の割り当て  
 任意の <xref:System.Data.SqlTypes> インスタンスの既定値は NULL です。  
  
 <xref:System.Data.SqlTypes> の NULL 値は型固有であり、`DbNull` などの 1 つの値で表すことはできません。 NULL 値の確認には、`IsNull` プロパティを使用します。  
  
 NULL 値は、次のコード サンプルに示すように <xref:System.Data.DataColumn> に割り当てることができます。 NULL 値は、例外をトリガーすることなく `SqlTypes` 変数に直接割り当てることができます。  
  
### <a name="example"></a>例  
 次のコード サンプルでは、<xref:System.Data.DataTable> および <xref:System.Data.SqlTypes.SqlInt32> として定義される 2 つの列を持つ <xref:System.Data.SqlTypes.SqlString> が作成されます。 このコードでは既知の値の行が 1 行、NULL 値の行が 1 行追加され、<xref:System.Data.DataTable> を通じて反復処理されます。これにより値が変数に割り当てられ、コンソール ウィンドウに出力が表示されます。  
  
 [!code-csharp[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.IsNull#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.IsNull/VB/source.vb#1)]  
  
 この例を実行すると、次の結果が表示されます。  
  
```  
isColumnNull=False, ID=123, Description=Side Mirror  
isColumnNull=True, ID=Null, Description=Null  
```  
  
## <a name="comparing-null-values-with-sqltypes-and-clr-types"></a>NULL 値と SqlTypes および CLR 型との比較  
 NULL 値を比較する場合は、`Equals` メソッドによって <xref:System.Data.SqlTypes> で NULL 値を評価する方法と、CLR 型を使用する方法との違いを理解することが重要です。 すべての<xref:System.Data.SqlTypes>`Equals`メソッドが null 値を評価するためにデータベース セマンティクスを使用: null のいずれかまたは両方の値が null の場合の比較となります。 その一方で、2 つの `Equals` に対して CLR <xref:System.Data.SqlTypes> メソッドを使用した場合は、両方が NULL であれば true が得られます。 これは、CLR `String.Equals` メソッドなどのインスタンス メソッドを使用した場合と、`SqlString.Equals` などの静的/共有メソッドを使用した場合の違いを反映しています。  
  
 次のコード サンプルでは、`SqlString.Equals` メソッドと `String.Equals` メソッドにそれぞれ NULL 値のペアを渡し、次に空の文字列のペアを渡した場合の、各メソッドの結果の違いを示します。  
  
 [!code-csharp[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTypes.CompareNulls#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTypes.CompareNulls/VB/source.vb#1)]  
  
 このコードを実行すると、次の出力が生成されます。  
  
```  
SqlString.Equals shared/static method:  
  Two nulls=Null  
  
String.Equals instance method:  
  Two nulls=True  
  
SqlString.Equals shared/static method:  
  Two empty strings=True  
  
String.Equals instance method:  
  Two empty strings=True   
```  
  
## <a name="see-also"></a>関連項目

- [SQL Server データ型と ADO.NET](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
