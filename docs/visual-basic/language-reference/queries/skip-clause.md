---
title: Skip 句
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
ms.openlocfilehash: c582b014bad4fa8fa3165d2b756f4bc955840cfc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349654"
---
# <a name="skip-clause-visual-basic"></a>Skip 句 (Visual Basic)
コレクション内の指定された数の要素をバイパスし、残りの要素を返します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Skip count  
```  
  
## <a name="parts"></a>指定項目  
 `count`  
 必須です。 A value or an expression that evaluates to the number of elements of the sequence to skip.  
  
## <a name="remarks"></a>Remarks  
 The `Skip` clause causes a query to bypass elements at the beginning of a results list and return the remaining elements. The number of elements to skip is identified by the `count` parameter.  
  
 You can use the `Skip` clause with the `Take` clause to return a range of data from any segment of a query. To do this, pass the index of the first element of the range to the `Skip` clause and the size of the range to the `Take` clause.  
  
 When you use the `Skip` clause in a query, you may also need to ensure that the results are returned in an order that will enable the `Skip` clause to bypass the intended results. For more information about ordering query results, see [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
 You can use the `SkipWhile` clause to specify that only certain elements are ignored, depending on a supplied condition.  
  
## <a name="example"></a>例  
 The following code example uses the `Skip` clause together with the `Take` clause to return data from a query in pages. The `GetCustomers` function uses the `Skip` clause to bypass the customers in the list until the supplied starting index value, and uses the `Take` clause to return a page of customers starting from that index value.  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a>関連項目

- [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [クエリ](../../../visual-basic/language-reference/queries/index.md)
- [Select 句](../../../visual-basic/language-reference/queries/select-clause.md)
- [From 句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Order By 句](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Skip While 句](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Take 句](../../../visual-basic/language-reference/queries/take-clause.md)
