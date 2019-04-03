---
title: Where 句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryWhere
helpviewer_keywords:
- Where statement [Visual Basic]
- queries [Visual Basic], Where
- Where clause [Visual Basic]
ms.assetid: 48b5c2c5-3181-429c-8545-894296798c89
ms.openlocfilehash: 5632e69039baebb3d1f1fd90c04586d9e50fe40f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834505"
---
# <a name="where-clause-visual-basic"></a>Where 句 (Visual Basic)
クエリのフィルター処理条件を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
Where condition  
```  
  
## <a name="parts"></a>指定項目  
 `condition`  
 必須。 コレクション内の現在の項目の値が出力コレクションに含めるかどうかを決定する式。 式を評価する必要があります、`Boolean`値またはと同等の`Boolean`値。 条件の評価が場合`True`要素は、クエリの結果に含まれる以外、それ以外の場合、クエリ結果から要素を除外します。  
  
## <a name="remarks"></a>Remarks  
 `Where`句では、特定の条件を満たす要素のみを選択してクエリのデータをフィルター処理することができます。 要素の値を持つが、`Where`句を評価する`True`クエリの結果に含まれるその他の要素が除外されます。 使用される式を`Where`に句を評価する必要があります、`Boolean`またはと同等の`Boolean`、整数に評価されるなど`False`その値が 0 の場合。 複数の式を組み合わせることができます、`Where`句などの論理演算子を使用して、 `And`、 `Or`、 `AndAlso`、 `OrElse`、 `Is`、および`IsNot`します。  
  
 既定では、アクセスされるまでクエリ式は評価されません-たとえばがのときにデータ バインドまたはで反復されたり、`For`ループします。 結果として、`Where`句は、クエリがアクセスされるまでは評価されません。 外部で使用されるクエリに値があるかどうか、`Where`句で、適切な値が使用されるように、`Where`句、クエリの実行時にします。 クエリの実行の詳細については、次を参照してください。[書き込みで初めて Your の LINQ クエリ](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md)します。  
  
 内の関数を呼び出すことができます、`Where`句をコレクション内の現在の要素から計算または値に対して操作を実行します。 関数を呼び出して、`Where`句アクセスされた場合の代わりに定義がときにすぐに実行するクエリが発生することができます。 クエリの実行の詳細については、次を参照してください。[書き込みで初めて Your の LINQ クエリ](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md)します。  
  
## <a name="example"></a>例  
 次のクエリ式は、`From`範囲変数を宣言する句`cust`各`Customer`オブジェクト、`customers`コレクション。 `Where`句では、範囲変数を使用して、指定されたリージョンからお客様に、出力を制限します。 `For Each`ループは、クエリ結果の各顧客の会社名を表示します。  
  
 [!code-vb[VbSimpleQuerySamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#23)]  
  
## <a name="example"></a>例  
 次の例では`And`と`Or`の論理演算子、`Where`句。  
  
 [!code-vb[VbSimpleQuerySamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#31)]  
  
## <a name="see-also"></a>関連項目

- [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [クエリ](../../../visual-basic/language-reference/queries/index.md)
- [From 句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Select 句](../../../visual-basic/language-reference/queries/select-clause.md)
- [For Each...Next ステートメント](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
