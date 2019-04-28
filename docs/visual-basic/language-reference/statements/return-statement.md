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
ms.openlocfilehash: 7f8ec0456576133d37dd19b5c0f8878a7ac57dab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783904"
---
# <a name="return-statement-visual-basic"></a>Return ステートメント (Visual Basic)
呼び出したコードに制御が戻ります、 `Function`、 `Sub`、 `Get`、 `Set`、または`Operator`プロシージャ。  
  
## <a name="syntax"></a>構文  
  
```  
Return  
-or-  
Return expression  
```  
  
## <a name="part"></a>パーツ  
 `expression`  
 必要な`Function`、 `Get`、または`Operator`プロシージャ。 呼び出し元のコードに返される値を表す式です。  
  
## <a name="remarks"></a>Remarks  
 `Sub`または`Set`プロシージャ、`Return`ステートメントは、`Exit Sub`または`Exit Property`ステートメントと`expression`を指定しないでください。  
  
 `Function`、 `Get`、または`Operator`、プロシージャ、`Return`ステートメントを含める必要があります`expression`、および`expression`プロシージャの戻り値の型に変換できるデータ型に評価される必要があります。 `Function`または`Get`プロシージャ、また、ある別の戻り値として処理するために、プロシージャ名に式を代入し、実行する方法、`Exit Function`または`Exit Property`ステートメント。 `Operator`使用する必要がありますプロシージャ、`Return expression`します。  
  
 多くとして含めることができます`Return`同じプロシージャ内に適切なステートメント。  
  
> [!NOTE]
>  コードを`Finally`ブロックを実行した後、`Return`内のステートメントを`Try`または`Catch`ブロックは、発生したが、その前に`Return`ステートメントを実行します。 A`Return`でステートメントを含めることができません、`Finally`ブロックします。  
  
## <a name="example"></a>例  
 次の例では、`Return`ステートメント、プロシージャが他に行うがあるない場合に、呼び出し元のコードに戻るに何度もします。  
  
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
