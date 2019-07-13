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
ms.openlocfilehash: cb109eaf43fee19b77ac690492b85919c9d78301
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054394"
---
# <a name="take-clause-visual-basic"></a>Take 句 (Visual Basic)
コレクションの先頭から、指定された数の連続する要素を返します。  
  
## <a name="syntax"></a>構文  
  
```  
Take count  
```  
  
## <a name="parts"></a>指定項目  
 `count`  
 必須。 返すシーケンスの要素の数に評価される式または値。  
  
## <a name="remarks"></a>Remarks  
 `Take`句によってクエリを指定された数結果一覧の先頭からの連続する要素にはが含まれます。 含まれる要素の数がで指定された、`count`パラメーター。  
  
 使用することができます、`Take`句、`Skip`句をクエリの任意のセグメントからのデータの範囲を返します。 これを行うには、範囲の最初の要素のインデックスを渡す、`Skip`句とする範囲のサイズ、`Take`句。 ここで、`Take`後句を指定する必要があります、`Skip`句。  
  
 使用すると、`Take`クエリ句、する必要がありますも結果が可能にする順序で返されるように、`Take`に目的の結果に含める句。 クエリの結果を順序付けの詳細については、次を参照してください。 [Order By 句](../../../visual-basic/language-reference/queries/order-by-clause.md)します。  
  
 使用することができます、`TakeWhile`句を指定した条件に応じて特定の要素のみを返すことを指定します。  
  
## <a name="example"></a>例  
 次のコード例では、`Take`句と組み合わせて、`Skip`句をページ内のクエリからデータを返します。 GetCustomers 関数は、`Skip`値、および使用して、指定された開始インデックスを作成するまで、リスト内の顧客をバイパスする句、`Take`句にそのインデックス値から開始のページが返されます。  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a>関連項目

- [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [クエリ](../../../visual-basic/language-reference/queries/index.md)
- [Select 句](../../../visual-basic/language-reference/queries/select-clause.md)
- [From 句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Order By 句](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Take While 句](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [Skip 句](../../../visual-basic/language-reference/queries/skip-clause.md)
