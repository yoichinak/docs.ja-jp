---
title: Join 句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryJoinIn
- vb.QueryJoin
- vb.QueryJoinOn
helpviewer_keywords:
- queries [Visual Basic], Join
- Join statement [Visual Basic]
- Join clause [Visual Basic]
ms.assetid: 6dd37936-b27c-4e00-98ad-154b23f4de64
ms.openlocfilehash: 8eab7db00515f55b086b5e1beddd149f966cb27a
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72001936"
---
# <a name="join-clause-visual-basic"></a>Join 句 (Visual Basic)
2 つのコレクションを単一のコレクションに結合します。 結合操作は、一致するキーに基づいており、`Equals` 演算子を使用します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Join element In collection _  
  [ joinClause _ ]   
  [ groupJoinClause ... _ ]   
On key1 Equals key2 [ And key3 Equals key4 [... ]  
```  
  
## <a name="parts"></a>指定項目  
 `element`  
 必須。 結合されているコレクションのコントロール変数。  
  
 `collection`  
 必須。 @No__t-0 演算子の左側で指定されているコレクションと結合するコレクション。 @No__t-0 句は、別の `Join` 句、または `Group Join` 句で入れ子にすることができます。  
  
 `joinClause`  
 任意。 クエリをさらに絞り込むための1つ以上の `Join` 句。  
  
 `groupJoinClause`  
 任意。 クエリをさらに絞り込むための1つ以上の `Group Join` 句。  
  
 `key1` `Equals` `key2`  
 必須。 結合されているコレクションのキーを識別します。 @No__t-0 演算子を使用して、結合されているコレクションのキーを比較する必要があります。 複数のキーを識別するには、`And` 演算子を使用して結合条件を結合します。 `key1` は、`Join` 演算子の左側のコレクションのものである必要があります。 `key2` は、`Join` 演算子の右側にあるコレクションのものである必要があります。  
  
 結合条件で使用されるキーは、コレクションの複数の項目を含む式にすることができます。 ただし、各キー式には、それぞれのコレクションの項目だけを含めることができます。  
  
## <a name="remarks"></a>コメント  
 @No__t-0 句は、結合されているコレクションのキー値の一致に基づいて2つのコレクションを結合します。 結果のコレクションには、`Join` 演算子の左側で指定されたコレクションと、`Join` 句で識別されたコレクションの値の任意の組み合わせを含めることができます。 クエリから返されるのは、`Equals` 演算子によって指定された条件を満たす結果だけです。 これは、SQL の @no__t 0 に相当します。  
  
 クエリで複数の @no__t 句を使用すると、複数のコレクションを1つのコレクションに結合できます。  
  
 暗黙の結合を実行して、`Join` 句を指定せずにコレクションを結合することができます。 これを行うには、`From` 句に複数の `In` 句を含め、結合に使用するキーを識別する `Where` 句を指定します。  
  
 @No__t-0 句を使用して、コレクションを1つの階層コレクションにまとめることができます。 これは、SQL の @no__t 0 に似ています。  
  
## <a name="example"></a>例  
 次のコード例では、暗黙的な結合を実行して顧客のリストと注文を結合します。  
  
 [!code-vb[VbSimpleQuerySamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#13)]  
  
## <a name="example"></a>例  
 次のコード例では、`Join` 句を使用して2つのコレクションを結合します。  
  
 [!code-vb[VbSimpleQuerySamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples2.vb#12)]  
  
 この例では、次のような出力が生成されます。  
  
 `winlogon (968), Windows Logon`  
  
 `explorer (2424), File Explorer`  
  
 `cmd (5136), Command Window`  
  
## <a name="example"></a>例  
 次のコード例では、2つのキー列を持つ `Join` 句を使用して2つのコレクションを結合します。  
  
 [!code-vb[VbSimpleQuerySamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples3.vb#17)]  
  
 この例では、次のような出力が生成されます。  
  
 `winlogon (968), Windows Logon, Priority = 13`  
  
 `cmd (700), Command Window, Priority = 8`  
  
 `explorer (2424), File Explorer, Priority = 8`  
  
## <a name="see-also"></a>関連項目

- [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [クエリ](../../../visual-basic/language-reference/queries/index.md)
- [Select 句](../../../visual-basic/language-reference/queries/select-clause.md)
- [From 句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Group Join 句](../../../visual-basic/language-reference/queries/group-join-clause.md)
- [Where 句](../../../visual-basic/language-reference/queries/where-clause.md)
