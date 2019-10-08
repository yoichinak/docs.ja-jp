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
ms.openlocfilehash: 184077f2689eb64e4373d407913eefcc03b795c2
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005723"
---
# <a name="group-join-clause-visual-basic"></a>Group Join 句 (Visual Basic)
2 つのコレクションを、単一の階層コレクションに結合します。 結合操作は、一致するキーに基づいています。  
  
## <a name="syntax"></a>構文  
  
```vb  
Group Join element [As type] In collection _  
  On key1 Equals key2 [ And key3 Equals key4 [... ] ] _  
  Into expressionList  
```  
  
## <a name="parts"></a>指定項目  
  
|項目|定義|  
|---|---|  
|`element`|必須。 結合されているコレクションのコントロール変数。|  
|`type`|任意。 `element` の型。 @No__t-0 が指定されていない場合、`element` の型は `collection` から推論されます。|  
|`collection`|必須。 @No__t-0 演算子の左辺にあるコレクションと結合するコレクションです。 @No__t-0 句は、`Join` 句、または別の `Group Join` 句で入れ子にすることができます。|  
|`key1` `Equals` `key2`|必須。 結合されているコレクションのキーを識別します。 @No__t-0 演算子を使用して、結合されているコレクションのキーを比較する必要があります。 複数のキーを識別するには、`And` 演算子を使用して結合条件を結合します。 @No__t-0 パラメーターは、`Join` 演算子の左側のコレクションのものである必要があります。 @No__t-0 パラメーターは、`Join` 演算子の右側にあるコレクションのものである必要があります。<br /><br /> 結合条件で使用されるキーは、コレクションの複数の項目を含む式にすることができます。 ただし、各キー式には、それぞれのコレクションの項目だけを含めることができます。|  
|`expressionList`|必須。 コレクションの要素のグループを集計する方法を識別する1つ以上の式。 グループ化された結果のメンバー名を特定するには、`Group` キーワード (`<alias> = Group`) を使用します。 グループに適用する集計関数を含めることもできます。|  
  
## <a name="remarks"></a>コメント  
 @No__t-0 句は、結合されているコレクションのキー値の一致に基づいて2つのコレクションを結合します。 結果のコレクションには、最初のコレクションのキー値に一致する2番目のコレクションの要素のコレクションを参照するメンバーを含めることができます。 2番目のコレクションのグループ化された要素に適用する集計関数を指定することもできます。 集計関数の詳細については、「 [Aggregate 句](../../../visual-basic/language-reference/queries/aggregate-clause.md)」を参照してください。  
  
 たとえば、マネージャーのコレクションや従業員のコレクションなどを検討します。 両方のコレクションの要素には、特定のマネージャーに報告する従業員を識別する ManagerID プロパティがあります。 結合操作の結果には、各マネージャーと、一致する ManagerID 値を持つ従業員の結果が含まれます。 @No__t 0 操作の結果には、マネージャーの完全な一覧が含まれます。 各マネージャーの結果には、特定のマネージャーに一致した従業員の一覧を参照するメンバーが含まれます。  
  
 @No__t 0 操作によって生成されるコレクションには、`From` 句で識別されたコレクションの値と、`Group Join` 句の `Into` 句で識別された式の任意の組み合わせを含めることができます。 @No__t-0 句の有効な式の詳細については、「 [Aggregate 句](../../../visual-basic/language-reference/queries/aggregate-clause.md)」を参照してください。  
  
 @No__t 0 の操作は、`Group Join` 演算子の左側で特定されたコレクションからすべての結果を返します。 これは、結合されているコレクションに一致するものがない場合でも同様です。 これは、SQL の @no__t 0 に似ています。  
  
 @No__t-0 句を使用して、コレクションを1つのコレクションにまとめることができます。 これは、SQL の @no__t 0 に相当します。  
  
## <a name="example"></a>例  
 次のコード例では、`Group Join` 句を使用して2つのコレクションを結合します。  
  
 [!code-vb[VbSimpleQuerySamples#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#14)]  
  
## <a name="see-also"></a>関連項目

- [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [クエリ](../../../visual-basic/language-reference/queries/index.md)
- [Select 句](../../../visual-basic/language-reference/queries/select-clause.md)
- [From 句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Join 句](../../../visual-basic/language-reference/queries/join-clause.md)
- [Where 句](../../../visual-basic/language-reference/queries/where-clause.md)
- [Group By 句](../../../visual-basic/language-reference/queries/group-by-clause.md)
