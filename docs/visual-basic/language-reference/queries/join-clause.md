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
ms.openlocfilehash: 1a2ec42adb4c41c33cb9e1c09822795c81e3a728
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971300"
---
# <a name="join-clause-visual-basic"></a>Join 句 (Visual Basic)
2 つのコレクションを単一のコレクションに結合します。 結合操作は、一致するキーに基づいて、使用して、`Equals`演算子。  
  
## <a name="syntax"></a>構文  
  
```  
Join element In collection _  
  [ joinClause _ ]   
  [ groupJoinClause ... _ ]   
On key1 Equals key2 [ And key3 Equals key4 [... ]  
```  
  
## <a name="parts"></a>指定項目  
 `element`  
 必須。 結合するコレクションの制御変数。  
  
 `collection`  
 必須。 左側にあるで識別されるコレクションと結合するコレクション、`Join`演算子。 A`Join`句は、別の入れ子にすることができます`Join`句、または、`Group Join`句。  
  
 `joinClause`  
 任意。 1 つ以上の追加`Join`句をさらに、クエリを絞り込みます。  
  
 `groupJoinClause`  
 任意。 1 つ以上の追加`Group Join`句をさらに、クエリを絞り込みます。  
  
 `key1` `Equals` `key2`  
 必須。 結合するコレクションのキーを識別します。 使用する必要があります、`Equals`結合されているコレクションからキーを比較する演算子。 使用して、結合条件を組み合わせることができます、`And`演算子を複数のキーを識別します。 `key1` 左側にあるコレクションから必要があります、`Join`演算子。 `key2` 右側にあるコレクションから必要があります、`Join`演算子。  
  
 結合条件で使用されるキーは、コレクションの 1 つ以上の項目を含む式を指定できます。 ただし、それぞれのキー式では、該当するコレクションの項目のみを含めることができます。  
  
## <a name="remarks"></a>Remarks  
 `Join`句が結合されているコレクションからのキー値と一致する 2 つのコレクションを結合します。 結果のコレクションの左側にある特定のコレクションからの値の任意の組み合わせを含めることができます、`Join`演算子とで識別されるコレクション、`Join`句。 によって指定された条件の結果のみが返されます、`Equals`演算子が満たされています。 これに相当する`INNER JOIN`sql です。  
  
 複数を使用する`Join`1 つのコレクションに 2 つ以上のコレクションを結合するクエリ内の句。  
  
 なしのコレクションを結合する暗黙の結合を行うことができます、`Join`句。 これを行うには、複数`In`内の句、`From`句を指定し、`Where`結合に使用するキー識別句。  
  
 使用することができます、`Group Join`句を単一の階層コレクションに結合します。 これは似ています、 `LEFT OUTER JOIN` sql です。  
  
## <a name="example"></a>例  
 次のコード例では、自分の注文と顧客のリストを結合する暗黙の結合を実行します。  
  
 [!code-vb[VbSimpleQuerySamples#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#13)]  
  
## <a name="example"></a>例  
 次のコード例では、2 つのコレクションを結合を使用して、`Join`句。  
  
 [!code-vb[VbSimpleQuerySamples#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples2.vb#12)]  
  
 この例には、次のような出力が生成されます。  
  
 `winlogon (968), Windows Logon`  
  
 `explorer (2424), File Explorer`  
  
 `cmd (5136), Command Window`  
  
## <a name="example"></a>例  
 次のコード例では、2 つのコレクションを結合を使用して、 `Join` 2 つのキー列と句。  
  
 [!code-vb[VbSimpleQuerySamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples3.vb#17)]  
  
 例では、次のような出力が生成されます。  
  
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
