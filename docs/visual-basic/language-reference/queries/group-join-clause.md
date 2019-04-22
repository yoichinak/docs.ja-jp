---
title: Group Join 句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryGroupJoinIn
- vb.QueryGroupJoinOn
- vb.QueryGroupJoin
- vb.QueryGroupJoinInto
helpviewer_keywords:
- Group Join clause [Visual Basic]
- Group Join statement [Visual Basic]
- queries [Visual Basic], Group Join
ms.assetid: 37dbf79c-7b5c-421b-bbb7-dadfd2b92a1c
ms.openlocfilehash: 3da4ca2db299a65b2c0f1fa259bbaabe4f53aa33
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58821960"
---
# <a name="group-join-clause-visual-basic"></a>Group Join 句 (Visual Basic)
2 つのコレクションを、単一の階層コレクションに結合します。 結合操作は、一致するキーに基づきます。  
  
## <a name="syntax"></a>構文  
  
```  
Group Join element [As type] In collection _  
  On key1 Equals key2 [ And key3 Equals key4 [... ] ] _  
  Into expressionList  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`element`|必須。 結合するコレクションの制御変数。|  
|`type`|省略可能です。 `element` の型。 ない場合は`type`を指定の種類`element`から推論されます`collection`します。|  
|`collection`|必須。 左側にある上にあるコレクションと結合するコレクション、`Group Join`演算子。 A`Group Join`に句を入れ子にすることができます、`Join`句または別の`Group Join`句。|  
|`key1` `Equals` `key2`|必須。 結合するコレクションのキーを識別します。 使用する必要があります、`Equals`結合されているコレクションからキーを比較する演算子。 使用して、結合条件を組み合わせることができます、`And`演算子を複数のキーを識別します。 `key1`の左側にあるコレクションからパラメーターがある必要があります、`Join`演算子。 `key2`の右側にあるコレクションからパラメーターがある必要があります、`Join`演算子。<br /><br /> 結合条件で使用されるキーは、コレクションの 1 つ以上の項目を含む式を指定できます。 ただし、それぞれのキー式では、該当するコレクションの項目のみを含めることができます。|  
|`expressionList`|必須。 コレクションから要素のグループの集計方法を識別する 1 つまたは複数の式。 グループ化した結果のメンバー名を識別するために使用して、`Group`キーワード (`<alias> = Group`)。 グループに適用する集計関数を含めることもできます。|  
  
## <a name="remarks"></a>Remarks  
 `Group Join`句が結合されているコレクションからのキー値と一致する 2 つのコレクションを結合します。 結果のコレクションには、最初のコレクションからキー値に一致する 2 番目のコレクションから要素のコレクションを参照するメンバーを含めることができます。 2 番目のコレクションのグループ化された要素に適用する集計関数を指定することもできます。 集計関数の詳細については、次を参照してください。 [Aggregate 句](../../../visual-basic/language-reference/queries/aggregate-clause.md)します。  
  
 たとえば、マネージャーのコレクションと、従業員のコレクションに検討してください。 両方のコレクションから要素では、特定の管理者に報告する従業員を識別する ManagerID プロパティがあります。 結合操作の結果には、各マネージャーと従業員 ManagerID 値が一致する結果が含まれます。 結果、`Group Join`操作には、マネージャーの完全な一覧にが含まれます。 各管理者の結果は、特定のマネージャーと一致する従業員の一覧を参照したメンバーになります。  
  
 結果のコレクションを`Group Join`操作がで識別されるコレクションからの値の任意の組み合わせを含めることができます、`From`句と、式で識別される、`Into`の句、`Group Join`句。 有効な式の詳細については、`Into`句を参照してください[Aggregate 句](../../../visual-basic/language-reference/queries/aggregate-clause.md)します。  
  
 A`Group Join`操作ではすべての結果を返しますの左側にある特定のコレクションから、`Group Join`演算子。 これは、結合するコレクション内の一致がない場合でも当てはまります。 これは似ています、 `LEFT OUTER JOIN` sql です。  
  
 使用することができます、`Join`句を 1 つのコレクションをコレクションに結合します。 これに相当する`INNER JOIN`sql です。  
  
## <a name="example"></a>例  
 次のコード例では、2 つのコレクションを結合を使用して、`Group Join`句。  
  
 [!code-vb[VbSimpleQuerySamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#14)]  
  
## <a name="see-also"></a>関連項目

- [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [クエリ](../../../visual-basic/language-reference/queries/index.md)
- [Select 句](../../../visual-basic/language-reference/queries/select-clause.md)
- [From 句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Join 句](../../../visual-basic/language-reference/queries/join-clause.md)
- [Where 句](../../../visual-basic/language-reference/queries/where-clause.md)
- [Group By 句](../../../visual-basic/language-reference/queries/group-by-clause.md)
