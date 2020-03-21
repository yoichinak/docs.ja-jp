---
title: クエリの基本操作
ms.date: 07/20/2015
helpviewer_keywords:
- data sources [LINQ in Visual Basic]
- Join clause [LINQ in Visual Basic]
- ordering data [LINQ in Visual Basic]
- projections [LINQ in Visual Basic]
- LINQ [Visual Basic], query operations
- Order By clause [LINQ in Visual Basic]
- joining data [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], basic operations
- selecting data [LINQ in Visual Basic]
- Group By clause [LINQ in Visual Basic]
- grouping data [LINQ in Visual Basic]
- Select clause [LINQ in Visual Basic]
ms.assetid: 1146f6d0-fcb8-4f4d-8223-c9db52620d21
ms.openlocfilehash: efae72c65ad67b4a1b157b67dcc4d4d65f31f77b
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266379"
---
# <a name="basic-query-operations-visual-basic"></a>基本的なクエリ操作 (Visual Basic)
このトピックでは、Visual Basic での統合言語クエリ (LINQ) 式の概要と、クエリで実行する一般的な種類の操作の概要を示します。 詳細については、次のトピックを参照してください。  
  
 [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [クエリ](../../../../visual-basic/language-reference/queries/index.md)  
  
 [チュートリアル: Visual Basic でクエリを記述する](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a>データ ソースの指定 (元)  
 LINQ クエリでは、最初にクエリを実行するデータ ソースを指定します。 したがって、クエリ`From`内の句が常に最初に来ます。 クエリ演算子は、ソースの種類に基づいて結果を選択し、その結果を形成します。  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 句`From`では、データ ソース`customers`、および*範囲変数*、`cust`を指定します。 範囲変数はループ反復変数に似ていますが、クエリ式では実際の反復は発生しません。 クエリを実行する場合、多くの場合ループ`For Each`を使用して、範囲変数は、 の`customers`連続する各要素への参照として機能します。 `cust` の型はコンパイラで推論できるため、明示的に指定する必要はありません。 明示的な型指定の有無にかかわらず作成されるクエリの例については、「[クエリ操作での型の関係 (Visual Basic)」](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md)を参照してください。  
  
 Visual Basic で句を`From`使用する方法の詳細については、「 From 句 」を[参照](../../../../visual-basic/language-reference/queries/from-clause.md)してください。  
  
## <a name="filtering-data-where"></a>データのフィルタリング (場所)  
 おそらく最も一般的なクエリ操作は、ブール式の形式でフィルターを適用します。 クエリは、式が true である要素のみを返します。 句`Where`は、フィルタ処理を実行するために使用されます。 フィルターは、結果のシーケンスに含めるデータ ソース内の要素を指定します。 次の例では、ロンドンに住所を持つ顧客のみが含まれています。  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 などの論理演算子を使用して`And`、`Or`句内のフィルター式を`Where`組み合わせることができます。 たとえば、ロンドン出身で、名前が Devon である顧客のみを返す場合は、次のコードを使用します。  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"
```  
  
 ロンドンまたはパリから顧客を返すには、次のコードを使用します。  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"
```  
  
 Visual Basic で句を`Where`使用する方法の詳細については[、「WHERE 句](../../../../visual-basic/language-reference/queries/where-clause.md)」を参照してください。  
  
## <a name="ordering-data-order-by"></a>データの順序 (発注順)  
 多くの場合、返されたデータを特定の順序に並べ替えるのが便利です。 句`Order By`は、返されたシーケンス内の要素が、指定された 1 つまたは複数のフィールドに並べ替えられます。 たとえば、次のクエリは、プロパティに基づいて結果`Name`を並べ替えます。 文字列`Name`であるため、返されるデータはアルファベット順に A から Z に並べ替えられます。  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 結果を逆の順序 (Z から A) で並び替えるには、`Order By...Descending` 句を使用します。 デフォルトは、`Ascending`指定も`Ascending`指定`Descending`もされていない場合です。  
  
 Visual Basic で句を`Order By`使用する方法の詳細については、「[句の順序](../../../../visual-basic/language-reference/queries/order-by-clause.md)」を参照してください。  
  
## <a name="selecting-data-select"></a>データの選択 (選択)  
 句`Select`は、返される要素の形式と内容を指定します。 たとえば、結果が完全な`Customer`オブジェクト、1 つの`Customer`プロパティ、プロパティのサブセット、さまざまなデータ ソースのプロパティの組み合わせ、または計算に基づく新しい結果の種類で構成されるかどうかを指定できます。 `Select` 句でソース要素のコピー以外のものを生成する場合、その操作は*投影*と呼ばれます。  
  
 完全な`Customer`オブジェクトで構成されるコレクションを取得するには、範囲変数自体を選択します。  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 `Customer`インスタンスが多数のフィールドを持つ大きなオブジェクトで、取得するオブジェクトが名前だけである場合は、次の例`cust.Name`に示すように を選択できます。 ローカル型推論では、結果の型がオブジェクトのコレクションから文字列の`Customer`コレクションに変更されることを認識します。  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 データ ソースから複数のフィールドを選択するには、次の 2 つの選択肢があります。  
  
- 句で`Select`、結果に含めるフィールドを指定します。 コンパイラは、これらのフィールドをプロパティとして持つ匿名型を定義します。 詳細については、「[匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)」を参照してください。  
  
     次の例で返される要素は匿名型のインスタンスであるため、コード内の他の場所で名前で型を参照することはできません。 コンパイラが指定した型の名前に、通常の Visual Basic コードでは無効な文字が含まれています。 次の例では、 クエリによって返されるコレクション内の要素`londonCusts4`は、匿名型のインスタンスです。  
  
     [!code-vb[VbLINQBasicOps#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#6)]  
  
     または  
  
- 結果に含める特定のフィールドを含む名前付きの型を定義し、その型のインスタンスを作成して、句内`Select`で初期化します。 このオプションは、返されるコレクションの外部で個々の結果を使用する必要がある場合、またはメソッド呼び出しでパラメーターとして渡す必要がある場合にのみ使用します。 次の例`londonCusts5`のタイプは、IEnumerable(ネームフォンの)です。  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 Visual Basic で句を使用`Select`する方法の詳細については、「[句の選択](../../../../visual-basic/language-reference/queries/select-clause.md)」を参照してください。  
  
## <a name="joining-data-join-and-group-join"></a>結合データ (結合およびグループ結合)  
 句内の複数のデータ ソースを`From`組み合わせる方法はいくつかあります。 たとえば、次のコードでは 2 つのデータ ソースを使用し、両方のプロパティを結果に暗黙的に結合します。 このクエリでは、母音で始まる姓の学生が選択されます。  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
> このコードは、「[方法 : アイテムのリストを作成する」で作成した学生のリストを](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)使用して実行できます。  
  
 キーワード`Join`は、SQL の`INNER JOIN`と同じです。 2 つのコレクションの要素間で一致するキー値に基づいて 2 つのコレクションを結合します。 クエリは、一致するキー値を持つコレクション要素のすべてまたは一部を返します。 たとえば、次のコードは、前の暗黙的な結合のアクションを複製します。  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 `Group Join`コレクションを 1 つの階層コレクションに結合し、SQL`LEFT JOIN`の a と同じようにします。 詳細については、「[結合句](../../../../visual-basic/language-reference/queries/join-clause.md)と[グループ結合句](../../../../visual-basic/language-reference/queries/group-join-clause.md)」を参照してください。  
  
## <a name="grouping-data-group-by"></a>データのグループ化 (グループ化)  
 句を`Group By`追加して、要素の 1 つ以上のフィールドに従ってクエリ結果の要素をグループ化できます。 たとえば、次のコードは、クラスの年で生徒をグループ化します。  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 「[方法: アイテム](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)のリストを作成する」で作成した学生のリストを使用してこのコードを実行すると`For Each`、ステートメントの出力は次のようになります。  
  
 年: ジュニア  
  
 タッカー,マイケル  
  
 ガルシア,ヒューゴ  
  
 ガルシア,デブラ  
  
 タッカー,ランス  
  
 年: シニア  
  
 オメルチェンコ(スヴェトラーナ)  
  
 大田,美智子  
  
 ファクーリ(ファディ)  
  
 風(高輝)  
  
 アダムス,テリー  
  
 年: 新入生  
  
 モルテンセン(スヴェン)  
  
 ガルシア,セザール  
  
 次のコードに示すバリエーションは、クラス年を並べ替え、毎年の生徒に姓で注文します。  
  
 [!code-vb[VbLINQBasicOps#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#12)]  
  
 の詳細については、「`Group By`句[でグループ化](../../../../visual-basic/language-reference/queries/group-by-clause.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Collections.Generic.IEnumerable%601>
- [Visual Basic の LINQ の概要](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [クエリ](../../../../visual-basic/language-reference/queries/index.md)
- [標準クエリ演算子の概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
