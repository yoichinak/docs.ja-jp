---
title: Take 句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTake
helpviewer_keywords:
- Take statement [Visual Basic]
- queries [Visual Basic], Take
- Take clause [Visual Basic]
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
ms.openlocfilehash: 32a4c7fd7f1e2f6fe640f3f53f15579f014759d5
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004716"
---
# <a name="take-clause-visual-basic"></a>Take 句 (Visual Basic)
コレクションの先頭から、指定された数の連続する要素を返します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Take count  
```  
  
## <a name="parts"></a>指定項目  
 `count`  
 必須。 返されるシーケンスの要素数に評価される値または式。  
  
## <a name="remarks"></a>コメント  
 @No__t-0 句を指定すると、クエリでは、結果リストの先頭から指定された数の連続する要素を含めることができます。 含める要素の数は、`count` パラメーターによって指定されます。  
  
 @No__t-1 句を指定した `Take` 句を使用すると、クエリの任意のセグメントからデータの範囲を取得できます。 これを行うには、範囲の最初の要素のインデックスを `Skip` 句に、範囲のサイズを `Take` 句に渡します。 この場合は、`Skip` 句の後に `Take` 句を指定する必要があります。  
  
 クエリで `Take` 句を使用する場合、`Take` の句に意図した結果を含めることができる順序で結果が返されるようにすることも必要になる場合があります。 クエリ結果の順序付けの詳細については、「 [Order By 句](../../../visual-basic/language-reference/queries/order-by-clause.md)」を参照してください。  
  
 指定された条件に応じて、特定の要素のみが返されるように指定するには、`TakeWhile` 句を使用します。  
  
## <a name="example"></a>例  
 次のコード例では、`Skip` 句と共に `Take` 句を使用して、ページ内のクエリからデータを返します。 GetCustomers 関数は、`Skip` 句を使用して、指定された開始インデックス値までリスト内の顧客をバイパスし、`Take` 句を使用して、そのインデックス値から始まる顧客のページを返します。  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a>関連項目

- [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [クエリ](../../../visual-basic/language-reference/queries/index.md)
- [Select 句](../../../visual-basic/language-reference/queries/select-clause.md)
- [From 句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Order By 句](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Take While 句](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [Skip 句](../../../visual-basic/language-reference/queries/skip-clause.md)
