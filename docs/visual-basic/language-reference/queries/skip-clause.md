---
title: Skip 句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkip
helpviewer_keywords:
- queries [Visual Basic], Skip
- Skip statement [Visual Basic]
- Skip clause [Visual Basic]
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
ms.openlocfilehash: db2d79596895505ddaa7778e831082a94c7ad44e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821102"
---
# <a name="skip-clause-visual-basic"></a>Skip 句 (Visual Basic)
コレクション内の指定された数の要素をバイパスし、残りの要素を返します。  
  
## <a name="syntax"></a>構文  
  
```  
Skip count  
```  
  
## <a name="parts"></a>指定項目  
 `count`  
 必須。 スキップするシーケンスの要素の数に評価される式または値。  
  
## <a name="remarks"></a>Remarks  
 `Skip`句によってクエリ結果一覧の先頭の要素をバイパスし、残りの要素を返します。 スキップする要素の数がで識別される、`count`パラメーター。  
  
 使用することができます、`Skip`句、`Take`句をクエリの任意のセグメントからのデータの範囲を返します。 これを行うには、範囲の最初の要素のインデックスを渡す、`Skip`句とする範囲のサイズ、`Take`句。  
  
 使用すると、`Skip`クエリ句、する必要がありますも結果が可能にする順序で返されるように、`Skip`意図した結果をバイパスする句。 クエリの結果を順序付けの詳細については、[Order By 句](../../../visual-basic/language-reference/queries/order-by-clause.md)を参照してください。  
  
 使用することができます、`SkipWhile`句を指定した条件に応じて、特定の要素だけを無視するかを指定します。  
  
## <a name="example"></a>例  
 次のコード例では、`Skip`句と組み合わせて、`Take`句をページ内のクエリからデータを返します。 `GetCustomers`関数は、`Skip`値、および使用して、指定された開始インデックスを作成するまで、リスト内の顧客をバイパスする句、`Take`句にそのインデックス値から開始のページが返されます。  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a>関連項目

- [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [クエリ](../../../visual-basic/language-reference/queries/index.md)
- [Select 句](../../../visual-basic/language-reference/queries/select-clause.md)
- [From 句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Order By 句](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Skip While 句](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Take 句](../../../visual-basic/language-reference/queries/take-clause.md)
