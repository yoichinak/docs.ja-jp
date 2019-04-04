---
title: Aggregate 句 (Visual Basic)
ms.date: 08/28/2018
f1_keywords:
- vb.QueryAggregateIn
- vb.QueryAggregate
- vb.QueryAggregateInto
helpviewer_keywords:
- Aggregate clause [Visual Basic]
- Aggregate statement [Visual Basic]
- queries [Visual Basic], Aggregate
ms.assetid: 1315a814-5db6-4077-b34b-b141e11cc0eb
ms.openlocfilehash: 21781db637c71abbbe9366bc95b6ee4c89ac2246
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981960"
---
# <a name="aggregate-clause-visual-basic"></a>Aggregate 句 (Visual Basic)
1 つまたは複数の集計関数をコレクションに適用します。  
  
## <a name="syntax"></a>構文  
  
```  
Aggregate element [As type] In collection _  
  [, element2 [As type2] In collection2, [...]]  
  [ clause ]  
  Into expressionList  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`element`|必須。 変数なコレクションの要素を反復処理するために使用します。|  
|`type`|任意。 `element` の型。 型が指定されていない場合の種類`element`から推論されます`collection`します。|  
|`collection`|必須。 操作対象のコレクションを参照します。|  
|`clause`|任意。 1 つまたは複数の句がクエリなど、`Where`集計句に適用するクエリの結果を絞り込むの句。|  
|`expressionList`|必須。 1 つまたは複数コンマで区切られた式のコレクションに適用する集計関数を識別します。 エイリアスは、クエリ結果のメンバー名を指定する集計関数を適用できます。 エイリアスが指定されていない場合は、集計関数の名前が使用されます。 例については、このトピックの後半の集計関数に関するセクションを参照してください。|  
  
## <a name="remarks"></a>Remarks  
 `Aggregate`に集計関数をクエリに含める句を使用できます。 集計関数は、値のセットをチェックし、計算を実行し、1 つの値を返します。 計算された値は、クエリ結果の型のメンバーを使用してアクセスできます。 使用できる標準の集計関数は、 `All`、 `Any`、 `Average`、 `Count`、 `LongCount`、 `Max`、 `Min`、および`Sum`関数。 これらの関数は SQL での集計に精通している開発者にとって馴染みのあります。 このトピックの次のセクションに記述されています。  
  
 クエリ結果の型のフィールドとしてクエリ結果の集計関数の結果が含まれます。 集計値を保持するクエリ結果の型のメンバーの名前を指定する集計関数の結果のエイリアスを指定することができます。 エイリアスが指定されていない場合は、集計関数の名前が使用されます。  
  
 `Aggregate`句は、クエリを開始できるかは、クエリで追加の句として追加できます。 場合、`Aggregate`句がクエリを開始すると、結果は、1 つの値で指定された集計関数の結果では、`Into`句。 複数の集計関数が指定されている場合、`Into`句内の各集計関数の結果を参照する個別のプロパティを 1 つの型を返します、クエリ、`Into`句。 場合、`Aggregate`句をクエリで追加の句として含めると、クエリのコレクションに返される型の各集計関数の結果を参照する個別のプロパティになります、`Into`句。  
  
## <a name="aggregate-functions"></a>集計関数

使用できる標準の集計関数を次に、`Aggregate`句。  
  
### <a name="all"></a>すべて

返します`true`返しますそれ以外の場合、コレクション内のすべての要素。 指定された条件を満たす場合`false`します。 次に例を示します。

 [!code-vb[VbSimpleQuerySamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#5)]

### <a name="any"></a>どれでも可

返します`true`返しますそれ以外の場合、コレクション内の任意の要素が; 指定された条件を満たす場合`false`します。 次に例を示します。

 [!code-vb[VbSimpleQuerySamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#6)]

### <a name="average"></a>平均

コレクション内のすべての要素の平均を計算するか、またはコレクション内のすべての要素に対して指定された式を計算します。 次に例を示します。

 [!code-vb[VbSimpleQuerySamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#7)]

### <a name="count"></a>カウント

コレクション内の要素の数をカウントします。 省略可能なを指定する`Boolean`式、条件を満たすコレクション内の要素の数のみをカウントします。 次に例を示します。

 [!code-vb[VbSimpleQuerySamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#8)]

### <a name="group"></a>グループ化

結果としてグループ化されているクエリの結果を指す、`Group By`または`Group Join`句。 `Group`関数はでのみ有効ですが、`Into`の句、`Group By`または`Group Join`句。 詳細と例については、[By 句のグループ](../../../visual-basic/language-reference/queries/group-by-clause.md)と[Group Join 句](../../../visual-basic/language-reference/queries/group-join-clause.md)を参照してください。

### <a name="longcount"></a>LongCount

コレクション内の要素の数をカウントします。 省略可能なを指定する`Boolean`式、条件を満たすコレクション内の要素の数のみをカウントします。 結果として返します、`Long`します。 例については、次を参照してください。、`Count`集計関数。

### <a name="max"></a>最大

コレクションから最大値を計算またはコレクション内のすべての要素に対して指定された式を計算します。 次に例を示します。

 [!code-vb[VbSimpleQuerySamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#9)]

### <a name="min"></a>最小

コレクションから最小値を計算またはコレクション内のすべての要素に対して指定された式を計算します。 次に例を示します。

 [!code-vb[VbSimpleQuerySamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#10)]

### <a name="sum"></a>Sum

コレクション内のすべての要素の合計を計算するか、またはコレクション内のすべての要素に対して指定された式を計算します。 次に例を示します。

 [!code-vb[VbSimpleQuerySamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#15)]

## <a name="example"></a>例  

次の例は、使用する方法を示します、`Aggregate`句をクエリ結果に集計関数を適用します。  
  
 [!code-vb[VbSimpleQuerySamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#4)]  
  
## <a name="creating-user-defined-aggregate-functions"></a>ユーザー定義集計関数を作成します。

 拡張メソッドを追加することによって、クエリ式で、独自のカスタム集計関数を含めることができます、<xref:System.Collections.Generic.IEnumerable%601>型。 カスタム メソッドを計算または集計関数が参照する列挙可能なコレクションに対して操作を実行できます。 拡張メソッドについて詳しくは、「[拡張メソッド](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)」をご覧ください。  
  
 たとえば、次の例は、数値のコレクションの中央値を計算するカスタムの集計関数を示します。 2 つのオーバー ロードがあります、`Median`拡張メソッド。 最初のオーバー ロードを受け入れると、入力として、型のコレクション`IEnumerable(Of Double)`します。 場合、`Median`型のクエリ フィールドの集計関数が呼び出されます`Double`、このメソッドが呼び出されます。 2 番目のオーバー ロード、`Median`任意のジェネリック型をメソッドに渡すことができます。 ジェネリック オーバー ロード、`Median`メソッドが参照する 2 番目のパラメーターを受け取り、`Func(Of T, Double)`型の対応する値として (コレクション) からの型の値を射影するラムダ式`Double`します。 その他のオーバー ロードに中央値の計算をデリゲートして、`Median`メソッド。 ラムダ式について詳しくは、「[ラムダ式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)」をご覧ください。  
  
 [!code-vb[VbSimpleQuerySamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#18)]  
  
 次の例では、サンプル クエリを呼び出す、`Median`集計関数の型のコレクション`Integer`、型のコレクションと`Double`します。 呼び出すクエリ、`Median`集計関数の種類のコレクションで`Double`のオーバー ロードを呼び出し、`Median`型のコレクションを入力として受け取るメソッドを`Double`します。 呼び出すクエリ、`Median`集計関数の種類のコレクションで`Integer`のジェネリック オーバー ロードを呼び出し、`Median`メソッド。  
  
 [!code-vb[VbSimpleQuerySamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#19)]  
  
## <a name="see-also"></a>関連項目

- [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [クエリ](../../../visual-basic/language-reference/queries/index.md)
- [Select 句](../../../visual-basic/language-reference/queries/select-clause.md)
- [From 句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Where 句](../../../visual-basic/language-reference/queries/where-clause.md)
- [Group By 句](../../../visual-basic/language-reference/queries/group-by-clause.md)
