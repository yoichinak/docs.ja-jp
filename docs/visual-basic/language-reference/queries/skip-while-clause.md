---
title: Skip While 句
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
ms.openlocfilehash: 47703e445865435f5bf5312c3fe41833ac21aa3f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333138"
---
# <a name="skip-while-clause-visual-basic"></a>Skip While 句 (Visual Basic)
指定された条件が `true` である限り、コレクションの要素をバイパスし、残りの要素を返します。  
  
## <a name="syntax"></a>構文  
  
```vb  
Skip While expression  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`expression`|必須です。 次の要素をテストするための条件を表す式。 式は、`Boolean` 値または同等の機能 (`Boolean` として評価される `Integer` など) を返す必要があります。|  
  
## <a name="remarks"></a>Remarks  
 `Skip While` 句では、クエリ結果の先頭から、指定された `expression` で `false` が返されるまでの要素がバイパスされます。 `expression` で `false` が返されると、クエリが残りのすべての要素を返します。 残りの結果に対して、`expression` は無視されます。  
  
 `Skip While` 句は、`Where` 句を使用して、特定の条件を満たしていないすべての要素をクエリから除外できるという点で、`Where` 句と異なります。 `Skip While` 句では、初めて条件が満たされなくなったときまでの要素が除外されます。 `Skip While` 句は、順序付けされたクエリ結果を操作する場合に最も役立ちます。  
  
 `Skip` 句を使用して、クエリ結果の先頭から特定の数の結果をバイパスできます。  
  
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
- [WHERE 句](../../../visual-basic/language-reference/queries/where-clause.md)
