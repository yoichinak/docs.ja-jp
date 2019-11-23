---
title: Take While 句
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
ms.openlocfilehash: 23b7c84a9f896161a66059fcb1f30753d3b863d5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347111"
---
# <a name="take-while-clause-visual-basic"></a>Take While 句 (Visual Basic)
指定された条件が `true` である限り、コレクションの要素を含むようにし、残りの要素をバイパスします。  
  
## <a name="syntax"></a>構文  
  
```vb  
Take While expression  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`expression`|必須です。 An expression that represents a condition to test elements for. The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.|  
  
## <a name="remarks"></a>Remarks  
 The `Take While` clause includes elements from the start of a query result until the supplied `expression` returns `false`. After the `expression` returns `false`, the query will bypass all remaining elements. The `expression` is ignored for the remaining results.  
  
 The `Take While` clause differs from the `Where` clause in that the `Where` clause can be used to include all elements from a query that meet a particular condition. The `Take While` clause includes elements only until the first time that the condition is not satisfied. The `Take While` clause is most useful when you are working with an ordered query result.  
  
## <a name="example"></a>例  
 The following code example uses the `Take While` clause to retrieve results until the first customer without any orders is found.  
  
 [!code-vb[VbSimpleQuerySamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#2)]  
  
## <a name="see-also"></a>関連項目

- [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [クエリ](../../../visual-basic/language-reference/queries/index.md)
- [Select 句](../../../visual-basic/language-reference/queries/select-clause.md)
- [From 句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Take 句](../../../visual-basic/language-reference/queries/take-clause.md)
- [Skip While 句](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [WHERE 句](../../../visual-basic/language-reference/queries/where-clause.md)
