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
ms.openlocfilehash: 50a53cd45cc428541c90fbf82089518be2212fae
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004809"
---
# <a name="aggregate-clause-visual-basic"></a>Aggregate 句 (Visual Basic)
1つまたは複数の集計関数をコレクションに適用します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Aggregate element [As type] In collection _  
  [, element2 [As type2] In collection2, [...]]  
  [ clause ]  
  Into expressionList  
```  
  
## <a name="parts"></a>指定項目  
  
|項目|定義|  
|---|---|  
|`element`|必須。 コレクションの要素を反復処理するために使用される変数。|  
|`type`|任意。 `element` の型。 型が指定されていない場合、`element` の型は `collection` から推論されます。|  
|`collection`|必須。 操作対象のコレクションを参照します。|  
|`clause`|任意。 集計句または句をに適用するためにクエリ結果を絞り込むための、`Where` 句などの1つ以上のクエリ句。|  
|`expressionList`|必須。 コレクションに適用する集計関数を識別する1つ以上のコンマ区切りの式。 集計関数に別名を適用して、クエリ結果のメンバー名を指定できます。 別名が指定されていない場合は、集計関数の名前が使用されます。 例については、このトピックで後述する「集計関数について」を参照してください。|  
  
## <a name="remarks"></a>コメント  
 @No__t-0 句を使用すると、クエリに集計関数を含めることができます。 集計関数は、一連の値に対してチェックと計算を実行し、1つの値を返します。 クエリ結果の型のメンバーを使用すると、計算された値にアクセスできます。 使用できる標準の集計関数は、@no__t 0、`Any`、`Average`、`Count`、@no__t 4、`Max`、`Min`、および `Sum` 関数です。 これらの関数は、SQL の集計に精通している開発者にとってはよく知られています。 これらの詳細については、このトピックの次のセクションで説明します。  
  
 集計関数の結果は、クエリ結果の型のフィールドとしてクエリ結果に含まれます。 集計関数の結果に別名を指定して、集計値を保持するクエリ結果の型のメンバーの名前を指定できます。 別名が指定されていない場合は、集計関数の名前が使用されます。  
  
 @No__t-0 句は、クエリを開始するか、クエリに追加の句として含めることができます。 @No__t-0 句によってクエリが開始された場合、結果は、`Into` 句に指定された集計関数の結果である単一の値になります。 @No__t-0 句に複数の集計関数が指定されている場合、クエリは、`Into` 句の各集計関数の結果を参照する個別のプロパティを持つ1つの型を返します。 @No__t-0 句がクエリに追加の句として含まれている場合、クエリコレクションで返される型には、`Into` 句の各集計関数の結果を参照する個別のプロパティがあります。  
  
## <a name="aggregate-functions"></a>集計関数

次に示すのは、`Aggregate` 句と共に使用できる標準の集計関数です。  
  
### <a name="all"></a>All

コレクション内のすべての要素が指定された条件を満たす場合は `true` を返します。それ以外の場合は `false` を返します。 以下に例を示します。

 [!code-vb[VbSimpleQuerySamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#5)]

### <a name="any"></a>Any

コレクション内のいずれかの要素が指定された条件を満たす場合は `true` を返します。それ以外の場合は `false` を返します。 以下に例を示します。

 [!code-vb[VbSimpleQuerySamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#6)]

### <a name="average"></a>平均

コレクション内のすべての要素の平均値を計算するか、コレクション内のすべての要素に対して指定された式を計算します。 以下に例を示します。

 [!code-vb[VbSimpleQuerySamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#7)]

### <a name="count"></a>Count

コレクション内の要素の数をカウントします。 条件を満たすコレクション内の要素の数のみをカウントするように、オプションの `Boolean` 式を指定することができます。 以下に例を示します。

 [!code-vb[VbSimpleQuerySamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#8)]

### <a name="group"></a>グループ

@No__t-0 または `Group Join` 句の結果としてグループ化されたクエリ結果を参照します。 @No__t-0 関数は、`Group By` または `Group Join` 句の `Into` 句でのみ有効です。 詳細と例については、「 [Group By 句](../../../visual-basic/language-reference/queries/group-by-clause.md)と[group Join 句](../../../visual-basic/language-reference/queries/group-join-clause.md)」を参照してください。

### <a name="longcount"></a>LongCount

コレクション内の要素の数をカウントします。 条件を満たすコレクション内の要素の数のみをカウントするように、オプションの `Boolean` 式を指定することができます。 結果を @no__t 0 として返します。 例については、「`Count` 集計関数」を参照してください。

### <a name="max"></a>Max

コレクションから最大値を計算するか、コレクション内のすべての要素に対して指定された式を計算します。 以下に例を示します。

 [!code-vb[VbSimpleQuerySamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#9)]

### <a name="min"></a>Min

コレクションから最小値を計算するか、コレクション内のすべての要素に対して指定された式を計算します。 以下に例を示します。

 [!code-vb[VbSimpleQuerySamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#10)]

### <a name="sum"></a>Sum

コレクション内のすべての要素の合計を計算するか、コレクション内のすべての要素に対して指定された式を計算します。 以下に例を示します。

 [!code-vb[VbSimpleQuerySamples#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#15)]

## <a name="example"></a>例  

次の例では、`Aggregate` 句を使用して、クエリ結果に集計関数を適用する方法を示します。  
  
 [!code-vb[VbSimpleQuerySamples#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#4)]  
  
## <a name="creating-user-defined-aggregate-functions"></a>ユーザー定義集計関数の作成

 @No__t-0 型に拡張メソッドを追加することで、独自のカスタム集計関数をクエリ式に含めることができます。 カスタムメソッドは、集計関数を参照した列挙可能なコレクションに対して計算または操作を実行できます。 拡張メソッドについて詳しくは、「[拡張メソッド](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)」をご覧ください。  
  
 たとえば、次の例は、数値のコレクションの中央値を計算するカスタム集計関数を示しています。 @No__t-0 拡張メソッドの2つのオーバーロードがあります。 1つ目のオーバーロードは、入力として `IEnumerable(Of Double)` 型のコレクションを受け入れます。 @No__t-0 集計関数が @no__t 型のクエリフィールドに対して呼び出されると、このメソッドが呼び出されます。 @No__t-0 メソッドの2番目のオーバーロードには、任意のジェネリック型を渡すことができます。 @No__t-0 メソッドの汎用的なオーバーロードは、`Func(Of T, Double)` ラムダ式を参照する2番目のパラメーターを受け取ります。このパラメーターは、コレクションの型の値を、型 `Double` の対応する値として射影します。 次に、中央値の計算を `Median` メソッドの他のオーバーロードにデリゲートします。 ラムダ式について詳しくは、「[ラムダ式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)」をご覧ください。  
  
 [!code-vb[VbSimpleQuerySamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#18)]  
  
 次の例では、型が @no__t のコレクションに対して `Median` 集計関数を呼び出すサンプルクエリと、`Double` 型のコレクションを呼び出します。 型 `Double` のコレクションで `Median` 集計関数を呼び出すクエリは、型 `Double` のコレクションを入力として受け入れる、`Median` メソッドのオーバーロードを呼び出します。 型 `Integer` のコレクションに対して `Median` 集計関数を呼び出すクエリは、`Median` メソッドのジェネリックオーバーロードを呼び出します。  
  
 [!code-vb[VbSimpleQuerySamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/UserDefinedAggregates.vb#19)]  
  
## <a name="see-also"></a>関連項目

- [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [クエリ](../../../visual-basic/language-reference/queries/index.md)
- [Select 句](../../../visual-basic/language-reference/queries/select-clause.md)
- [From 句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Where 句](../../../visual-basic/language-reference/queries/where-clause.md)
- [Group By 句](../../../visual-basic/language-reference/queries/group-by-clause.md)
