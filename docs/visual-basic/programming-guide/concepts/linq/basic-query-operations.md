---
title: 基本的なクエリ操作 (Visual Basic)
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
ms.openlocfilehash: 141040a715487b3cbcfff1c3b9969a0869c8a3d8
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/01/2019
ms.locfileid: "57201711"
---
# <a name="basic-query-operations-visual-basic"></a>基本的なクエリ操作 (Visual Basic)
このトピックで説明を簡単に紹介[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]Visual Basic、およびいくつかのクエリを実行する操作の一般的な種類の式。 詳細については、次のトピックを参照してください。  
  
 [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
  
 [クエリ](../../../../visual-basic/language-reference/queries/index.md)  
  
 [チュートリアル: Visual Basic におけるクエリの作成](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)  
  
## <a name="specifying-the-data-source-from"></a>(From) データ ソースを指定します。  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]のクエリでは、まず、クエリを実行するデータ ソースを指定します。 そのため、`From`クエリ句は常に最初は。 クエリ演算子は、選択し、図形のソースの種類に基づく結果。  
  
 [!code-vb[VbLINQBasicOps#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#1)]  
  
 `From`句は、データ ソースを指定`customers`、および*範囲変数*、`cust`します。 範囲変数は、クエリ式では、実際の反復は発生しませんが、ループの反復変数のようなは。 クエリが実行されると、多くの場合を使用して、`For Each`ループ、連続する各要素への参照として範囲変数`customers`します。 `cust` の型はコンパイラで推論できるため、明示的に指定する必要はありません。 明示的な型指定なしで記述されたクエリの例については、次を参照してください。[クエリ操作 (Visual Basic) での型の関係](../../../../visual-basic/programming-guide/concepts/linq/type-relationships-in-query-operations.md)します。  
  
 使用する方法についての詳細、 `From` Visual basic での句を参照してください[句から](../../../../visual-basic/language-reference/queries/from-clause.md)します。  
  
## <a name="filtering-data-where"></a>データのフィルター処理 (場所)  
 おそらく、最も一般的なクエリ操作では、ブール式の形式でフィルターを適用するは。 クエリは、式が true の要素のみを返します。 A`Where`句を使用して、フィルター処理を実行します。 フィルターは、結果のシーケンスに含めるデータ ソース内のどの要素を指定します。 次の例では、住所がロンドンを持つお客様のみが含まれます。  
  
 [!code-vb[VbLINQBasicOps#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#2)]  
  
 などの論理演算子を使用することができます`And`と`Or`のフィルター式を結合する、`Where`句。 たとえば、ロンドンし、名前を持つ、デボン顧客のみを返すには、次のコードを使用します。  
  
```vb  
Where cust.City = "London" And cust.Name = "Devon"   
```  
  
 ロンドンまたはパリにある顧客を返すには、次のコードを使用します。  
  
```vb  
Where cust.City = "London" Or cust.City = "Paris"   
```  
  
 使用する方法についての詳細、 `Where` Visual basic での句を参照してください[Where 句](../../../../visual-basic/language-reference/queries/where-clause.md)します。  
  
## <a name="ordering-data-order-by"></a>データ (Order By) の並べ替え  
 多くの場合は、特定の順序に返されるデータを並べ替えると便利です。 `Order By`句には、指定されたフィールドで並べ替えるに返されたシーケンスで要素が発生します。 たとえば、次のクエリがに基づいて結果を並べ替えます、`Name`プロパティ。 `Name`文字列では、a ~ Z、返されるデータは、アルファベット順に並べ替えられます。  
  
 [!code-vb[VbLINQBasicOps#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#3)]  
  
 結果を逆の順序 (Z から A) で並び替えるには、`Order By...Descending` 句を使用します。 既定値は`Ascending`がいずれも`Ascending`も`Descending`を指定します。  
  
 使用する方法についての詳細、 `Order By` Visual basic での句を参照してください[Order By 句](../../../../visual-basic/language-reference/queries/order-by-clause.md)します。  
  
## <a name="selecting-data-select"></a>データ (選択) を選択します。  
 `Select`句は、フォームと返される要素の内容を指定します。 完全な結果はで構成されているかどうかを指定するたとえば、`Customer`オブジェクト、1 つにすぎません`Customer`計算に基づいて、プロパティ、プロパティのサブセット、さまざまなデータ ソース、または新しい結果の種類からのプロパティの組み合わせ。 `Select` 句でソース要素のコピー以外のものを生成する場合、その操作は*投影*と呼ばれます。  
  
 完全なから成るコレクションを取得する`Customer`オブジェクト、範囲変数自体を選択します。  
  
 [!code-vb[VbLINQBasicOps#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#4)]  
  
 場合、`Customer`インスタンスは、ラージ オブジェクトを持つ多くのフィールドと名前を取得することだけですを選択できます`cust.Name`次の例のようにします。 ローカル型推論のコレクションから結果の型が変更される`Customer`オブジェクトを文字列のコレクション。  
  
 [!code-vb[VbLINQBasicOps#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#5)]  
  
 データ ソースから複数のフィールドを選択するには、2 つの選択肢があります。  
  
-   `Select`句では、結果に含めるフィールドを指定します。 コンパイラは、それらのフィールドとしてそのプロパティを含む匿名型を定義します。 詳細については、「[匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)」を参照してください。  
  
     次の例で返される要素は、匿名型のインスタンスであるため、参照できません型に名前で別の場所、コード内。 コンパイラの指定、型名には、通常の Visual Basic コードでは無効な文字が含まれています。 次の例では、クエリでは、によって返されるコレクション内の要素で`londonCusts4`匿名型のインスタンスであります。  
  
     [!code-vb[VbLINQBasicOps#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#6)]  
  
     - または -  
  
-   結果に含まれるを作成し、型のインスタンスを初期化する特定のフィールドを含む名前付きの型を定義、`Select`句。 これらは、返される、コレクションの外部の個別の結果を使用する必要がある場合にのみ、またはメソッドの呼び出しでパラメーターとして渡すことがある場合は、このオプションを使用します。 型`londonCusts5`次の例では、IEnumerable (Of NamePhone)。  
  
     [!code-vb[VbLINQBasicOps#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#7)]  
  
     [!code-vb[VbLINQBasicOps#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#8)]  
  
 使用する方法についての詳細、 `Select` Visual basic での句を参照してください[Select 句](../../../../visual-basic/language-reference/queries/select-clause.md)します。  
  
## <a name="joining-data-join-and-group-join"></a>結合のデータ (結合やグループ結合)  
 複数のデータ ソースを組み合わせることができます、`From`いくつかの方法で句。 たとえば、次のコードでは、2 つのデータ ソースを使用して、暗黙的に結果にこれらの両方からのプロパティを結合します。 クエリでは、母音で始まる最後名前受講者を選択します。  
  
 [!code-vb[VbLINQBasicOps#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#9)]  
  
> [!NOTE]
>  作成した受講者の一覧で、このコードを実行することができます[方法。項目の一覧を作成](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)です。  
  
 `Join`キーワードは、 `INNER JOIN` sql です。 これは、2 つのコレクション内の要素間の一致するキー値に基づいて 2 つのコレクションを結合します。 クエリでは、キーの値が一致するコレクションの要素のすべてまたは一部を返します。 たとえば、次のコードでは、前の暗黙の結合のアクションが重複しています。  
  
 [!code-vb[VbLINQBasicOps#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#10)]  
  
 `Group Join` 同じようにコレクションを 1 つの階層コレクションを組み合わせて、 `LEFT JOIN` sql です。 詳細については、次を参照してください。 [Join 句](../../../../visual-basic/language-reference/queries/join-clause.md)と[Group Join 句](../../../../visual-basic/language-reference/queries/group-join-clause.md)します。  
  
## <a name="grouping-data-group-by"></a>データのグループ化 (Group By)  
 追加することができます、`Group By`要素の 1 つまたは複数のフィールドに従ってのクエリ結果内の要素をグループ化する句。 たとえば、次のコードでは、クラス年ごと学生をグループ化します。  
  
 [!code-vb[VbLINQBasicOps#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#11)]  
  
 作成した受講者のリストを使用してこのコードを実行するかどうかは[方法。リストの項目を作成](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)からの出力、`For Each`ステートメントは。  
  
 年。Junior  
  
 Tucker です、Michael  
  
 Garcia、Hugo  
  
 Garcia、Debra  
  
 Lance、tucker です。  
  
 年。シニア  
  
 Omelchenko、Svetlana  
  
 田山、Michiko  
  
 Fakhouri、Fadi  
  
 Feng、ある Hanying  
  
 Terry Adams は、  
  
 年。今  
  
 Mortensen、Sven  
  
 Garcia、Cesar  
  
 次のコードに示すように、バリエーションの 1 つは、並べ替え、クラスの年を姓で各年度、受講者を並べ替えます。  
  
 [!code-vb[VbLINQBasicOps#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQBasicOps/VB/Class1.vb#12)]  
  
 詳細については`Group By`を参照してください[By 句のグループ](../../../../visual-basic/language-reference/queries/group-by-clause.md)します。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Collections.Generic.IEnumerable%601>
- [Visual Basic の LINQ の概要](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [クエリ](../../../../visual-basic/language-reference/queries/index.md)
- [標準クエリ演算子の概要 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
