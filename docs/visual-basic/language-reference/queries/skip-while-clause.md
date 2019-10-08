---
title: Skip While 句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
ms.openlocfilehash: 7f37a6fa1c9ba7fdf7978ac6853e4c2985bf72e7
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004698"
---
# <a name="skip-while-clause-visual-basic"></a>Skip While 句 (Visual Basic)
指定された条件が `true` である限り、コレクションの要素をバイパスし、残りの要素を返します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Skip While expression  
```  
  
## <a name="parts"></a>指定項目  
  
|項目|定義|  
|---|---|  
|`expression`|必須。 テスト要素の条件を表す式。 式は、@no__t 0 の値または同等の関数を返す必要があります。たとえば、`Boolean` として評価される `Integer` などです。|  
  
## <a name="remarks"></a>コメント  
 @No__t-0 句は、指定された `expression` が `false` を返すまで、クエリ結果の先頭からの要素をバイパスします。 @No__t-0 `false` を返します。このクエリは、残りのすべての要素を返します。 残りの結果については、`expression` は無視されます。  
  
 @No__t-0 句は `Where` 句とは異なり、`Where` 句を使用して、特定の条件を満たさないクエリからすべての要素を除外することができます。 @No__t-0 句では、最初に条件が満たされない限り、要素は除外されます。 @No__t-0 句は、順序付けられたクエリ結果を操作する場合に最も役立ちます。  
  
 @No__t-0 句を使用すると、クエリ結果の先頭から特定の数の結果をバイパスできます。  
  
## <a name="example"></a>例  
 次のコード例では、`Skip While` 句を使用して、米国の最初の顧客が見つかるまで結果をバイパスします。  
  
 [!code-vb[VbSimpleQuerySamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#3)]  
  
## <a name="see-also"></a>関連項目

- [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [クエリ](../../../visual-basic/language-reference/queries/index.md)
- [Select 句](../../../visual-basic/language-reference/queries/select-clause.md)
- [From 句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Skip 句](../../../visual-basic/language-reference/queries/skip-clause.md)
- [Take While 句](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [Where 句](../../../visual-basic/language-reference/queries/where-clause.md)
