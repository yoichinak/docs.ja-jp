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
ms.translationtype: HT
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
 必須です。 スキップするシーケンスの要素数に評価される値または式。  
  
## <a name="remarks"></a>Remarks  
 `Skip` 句を使用すると、クエリは結果リストの先頭の要素をバイパスし、残りの要素を返します。 スキップする要素の数は `count` パラメーターによって識別されます。  
  
 `Take` 句と共に `Skip` 句を使用すると、クエリの任意のセグメントからのデータの範囲を返すことができます。 これを行うには、範囲の最初の要素のインデックスを `Skip` 句に渡し、範囲のサイズを `Take` 句に渡します。  
  
 クエリで `Skip` 句を使用する場合は、`Skip` 句で目的の結果がバイパスされるような順番で、結果が返されるようにする必要がある場合もあります。 クエリ結果の順序付けの詳細については、「[Order By 句](../../../visual-basic/language-reference/queries/order-by-clause.md)」を参照してください。  
  
 指定した条件に応じて、特定の要素のみが無視されるように指定するには、`SkipWhile` 句を使用できます。  
  
## <a name="example"></a>例  
 次のコード例では、`Take` 句と共に `Skip` 句を使用して、ページ内のクエリからのデータを返しています。 `GetCustomers` 関数は、`Skip` 句を使用して、指定した開始インデックス値までリスト内の顧客をバイパスし、`Take` 句を使用して、そのインデックス値から始まる顧客のページを返します。  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a>関連項目

- [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [クエリ](../../../visual-basic/language-reference/queries/index.md)
- [Select 句](../../../visual-basic/language-reference/queries/select-clause.md)
- [From 句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Order By 句](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Skip While 句](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Take 句](../../../visual-basic/language-reference/queries/take-clause.md)
