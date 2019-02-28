---
title: Continue ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.continue
helpviewer_keywords:
- Continue statement [Visual Basic]
- loops, transferring to next iteration
ms.assetid: 3ad00103-358b-4af3-a3a8-1b9ea0e995d3
ms.openlocfilehash: 7aa0bda9c87553a5c9dae38517b5d546f782bed0
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974082"
---
# <a name="continue-statement-visual-basic"></a>Continue ステートメント (Visual Basic)
ループの次の反復処理に直ちに制御を転送します。  
  
## <a name="syntax"></a>構文  
  
```  
Continue { Do | For | While }  
```  
  
## <a name="remarks"></a>Remarks  
 転送できます内で、 `Do`、 `For`、または`While`ループの次のイテレーションをループします。 パスに転送するのと同じですが、ループ条件テストをすぐに制御、`For`または`While`ステートメント、または、`Do`または`Loop`ステートメントを含む、`Until`または`While`句。  
  
 使用することができます`Continue`転送を許可するループ内で任意の位置。 コントロールの転送を許可する規則と同じ、 [GoTo ステートメント](../../../visual-basic/language-reference/statements/goto-statement.md)します。  
  
 たとえば、ループ処理が完全に含まれて、`Try`ブロック、`Catch`ブロック、または`Finally`ブロックを使用することができます`Continue`ループの外に転送します。 場合、その一方で、 `Try`.`End Try`ループ内で構造体が含まれている、使用することはできません`Continue`の制御を転送する、`Finally`ブロックとすることができます、転送に使用のうち、`Try`または`Catch`ブロックの完全に転送する場合にのみ、`Try`...`End Try`構造体。  
  
 たとえば、同じ型の入れ子になったループがあるかどうか、`Do`内に別のループ`Do`ループ、`Continue Do`最も内側の次の反復処理するステートメントをスキップします`Do`それを含んでいるループ。 使用することはできません`Continue`同じ種類の外側のループの次の反復処理をスキップします。  
  
 たとえば、さまざまな種類の入れ子になったループがあるかどうか、`Do`内でループを`For`ループに進んで、ループの次のイテレーションを使用して`Continue Do`または`Continue For`。  
  
## <a name="example"></a>例  
 次のコード例では、`Continue While`除数がゼロの場合は、配列の次の列をスキップするステートメント。 `Continue While`内では、`For`ループします。 転送先、`While col < lastcol`ステートメントでは、最も内側の次のイテレーションである`While`ループが含まれている`For`ループします。  
  
 [!code-vb[VbVbalrStatements#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#14)]  
  
## <a name="see-also"></a>関連項目
- [Do...Loop ステートメント](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [For...Next ステートメント](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [While...End While ステートメント](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Try...Catch...Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
