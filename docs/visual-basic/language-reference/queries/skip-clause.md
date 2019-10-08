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
ms.openlocfilehash: e52de186e1475bfabd02821a0cd2384d8350eed3
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004768"
---
# <a name="skip-clause-visual-basic"></a>Skip 句 (Visual Basic)
コレクション内の指定された数の要素をバイパスし、残りの要素を返します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Skip count  
```  
  
## <a name="parts"></a>指定項目  
 `count`  
 必須。 スキップするシーケンスの要素数に評価される値または式。  
  
## <a name="remarks"></a>コメント  
 @No__t-0 句を使用すると、クエリは結果リストの先頭にある要素をバイパスし、残りの要素を返します。 スキップする要素の数は、`count` パラメーターによって識別されます。  
  
 @No__t-1 句を指定した `Skip` 句を使用すると、クエリの任意のセグメントからデータの範囲を取得できます。 これを行うには、範囲の最初の要素のインデックスを `Skip` 句に、範囲のサイズを `Take` 句に渡します。  
  
 クエリで `Skip` 句を使用する場合は、`Skip` の句で意図した結果をバイパスできる順序で結果が返されるようにすることも必要になる場合があります。 クエリ結果の順序付けの詳細については、「 [Order By 句](../../../visual-basic/language-reference/queries/order-by-clause.md)」を参照してください。  
  
 指定された条件に応じて、特定の要素のみを無視するように指定するには、`SkipWhile` 句を使用します。  
  
## <a name="example"></a>例  
 次のコード例では、`Take` 句と共に `Skip` 句を使用して、ページ内のクエリからデータを返します。 @No__t-0 関数は、`Skip` 句を使用して、指定された開始インデックス値までリスト内の顧客をバイパスし、`Take` 句を使用して、そのインデックス値から始まる顧客のページを返します。  
  
 [!code-vb[VbSimpleQuerySamples#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#1)]  
  
## <a name="see-also"></a>関連項目

- [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [クエリ](../../../visual-basic/language-reference/queries/index.md)
- [Select 句](../../../visual-basic/language-reference/queries/select-clause.md)
- [From 句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Order By 句](../../../visual-basic/language-reference/queries/order-by-clause.md)
- [Skip While 句](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [Take 句](../../../visual-basic/language-reference/queries/take-clause.md)
