---
title: Return ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Return
helpviewer_keywords:
- Return statement [Visual Basic], syntax
- control flow [Visual Basic], returning control to expressions
- Return statement [Visual Basic]
- expressions [Visual Basic], returning control to
ms.assetid: ac86e7f0-5a67-42c3-9834-0e0381efa3ec
ms.openlocfilehash: af49ea95d7f9d01072190ac3ccf6ba2f1041347e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957672"
---
# <a name="return-statement-visual-basic"></a>Return ステートメント (Visual Basic)
`Function` 、`Sub`、、、または`Operator`プロシージャを呼び出したコードに制御を返します。 `Set` `Get`  
  
## <a name="syntax"></a>構文  
  
```  
Return  
-or-  
Return expression  
```  
  
## <a name="part"></a>パーツ  
 `expression`  
 `Function` 、`Get`、または`Operator`プロシージャで必要です。 呼び出し元のコードに返される値を表す式。  
  
## <a name="remarks"></a>Remarks  
 `Exit Sub` `Exit Property`または`Set`プロシージャ`expression`では、ステートメントはまたはステートメントと同じであり、指定することはできません。`Return` `Sub`  
  
 `Function` `expression`、 、また`Operator`はプロシージャでは、ステートメントにを含め、プロシージャの戻り値の型に変換可能なデータ型に評価する必要があります。`expression` `Return` `Get` または`Get`プロシージャでは、プロシージャ名に式を代入して戻り値として使用し、ステートメント`Exit Function`または`Exit Property`ステートメントを実行する方法もあります。 `Function` プロシージャでは、を使用`Return expression`する必要があります。 `Operator`  
  
 同じ手順で、必要`Return`な数だけステートメントを含めることができます。  
  
> [!NOTE]
> `Finally`ブロック内のコードは、 `Try`または`Return` `Catch`ブロック内のステートメントが検出された後、 `Return`そのステートメントが実行される前に実行されます。 ステートメント`Return`を`Finally`ブロックに含めることはできません。  
  
## <a name="example"></a>例  
 次の例では`Return` 、ステートメントを複数回使用して、プロシージャが他の操作を行う必要がない場合に、呼び出し元のコードに戻ります。  
  
 [!code-vb[VbVbalrStatements#53](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#53)]  
  
## <a name="see-also"></a>関連項目

- [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Get ステートメント](../../../visual-basic/language-reference/statements/get-statement.md)
- [Set ステートメント](../../../visual-basic/language-reference/statements/set-statement.md)
- [Operator ステートメント](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)
- [Exit ステートメント](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Try...Catch...Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
