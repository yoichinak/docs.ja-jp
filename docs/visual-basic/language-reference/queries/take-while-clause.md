---
title: Take While 句 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
ms.openlocfilehash: fe6ee470698504bc0434930cc9aa6de712e04254
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004674"
---
# <a name="take-while-clause-visual-basic"></a>Take While 句 (Visual Basic)
指定された条件が `true` である限り、コレクションの要素を含むようにし、残りの要素をバイパスします。  
  
## <a name="syntax"></a>構文  
  
```vb  
Take While expression  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|Definition|  
|---|---|  
|`expression`|必須。 テスト要素の条件を表す式。 式は、`Boolean` 値または同等の機能 (`Boolean`として評価される `Integer` など) を返す必要があります。|  
  
## <a name="remarks"></a>コメント  
 `Take While` 句には、指定された `expression` が `false`を返すまで、クエリ結果の先頭からの要素が含まれます。 `expression` が `false`を返した後、クエリは残りのすべての要素をバイパスします。 残りの結果については、`expression` は無視されます。  
  
 `Take While` 句は、特定の条件を満たすクエリのすべての要素を含めるために `Where` 句を使用できるという点で、`Where` 句とは異なります。 `Take While` 句には、最初に条件が満たされない限り、要素が含まれます。 `Take While` 句は、順序付けられたクエリ結果を操作する場合に最も役立ちます。  
  
## <a name="example"></a>例  
 次のコード例では、`Take While` 句を使用して、注文のない最初の顧客が見つかるまで結果を取得します。  
  
 [!code-vb[VbSimpleQuerySamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#2)]  
  
## <a name="see-also"></a>参照

- [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [クエリ](../../../visual-basic/language-reference/queries/index.md)
- [Select 句](../../../visual-basic/language-reference/queries/select-clause.md)
- [From 句](../../../visual-basic/language-reference/queries/from-clause.md)
- [Take 句](../../../visual-basic/language-reference/queries/take-clause.md)
- [Skip While 句](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [WHERE 句](../../../visual-basic/language-reference/queries/where-clause.md)
