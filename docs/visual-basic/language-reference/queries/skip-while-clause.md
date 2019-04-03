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
ms.openlocfilehash: 3d6caeb1938e8e53e8ec2575f740cd5e49496f62
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839900"
---
# <a name="skip-while-clause-visual-basic"></a>Skip While 句 (Visual Basic)
指定された条件が `true` である限り、コレクションの要素をバイパスし、残りの要素を返します。  
  
## <a name="syntax"></a>構文  
  
```  
Skip While expression  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`expression`|必須。 要素をテストするための条件を表す式。 式を返す必要があります、`Boolean`値またはそれと同等の機能など、`Integer`として評価される、`Boolean`します。|  
  
## <a name="remarks"></a>Remarks  
 `Skip While`句まで、指定されたクエリ結果の先頭から要素をバイパスする`expression`返します`false`します。 後`expression`返します`false`クエリは、残りのすべての要素を返します。 `expression`残りの結果は無視されます。  
  
 `Skip While`句とは異なります、`Where`句を`Where`を特定の条件を満たさないクエリからすべての要素を除外する句を使用できます。 `Skip While`句は、条件が満たされていませんが、初めてまでのみ要素を除外します。 `Skip While`句は、順序付けられたクエリ結果を使用しているときに最も役立ちます。  
  
 使用してクエリ結果の先頭からの結果の特定の数をバイパスできる、`Skip`句。  
  
## <a name="example"></a>例  
 次のコード例では、`Skip While`米国から最初の顧客が見つかるまで、結果をバイパスする句。  
  
 [!code-vb[VbSimpleQuerySamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#3)]  
  
## <a name="see-also"></a>関連項目

- [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [クエリ](../../../visual-basic/language-reference/queries/index.md)
- [Select 句](../../../visual-basic/language-reference/queries/select-clause.md)
- [From 句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Skip 句](../../../visual-basic/language-reference/queries/skip-clause.md)
- [Take While 句](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [Where 句](../../../visual-basic/language-reference/queries/where-clause.md)
