---
title: Function プロシージャ (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Function procedures
- return values [Visual Basic], function procedures
- Visual Basic code, procedures
- procedures [Visual Basic], calling
- procedures [Visual Basic], Function procedures
- syntax [Visual Basic], function procedures
ms.assetid: 1b9f632c-553b-4cb6-920a-ded117ead8c0
ms.openlocfilehash: 568489d6034316e895cd999801241fa995aadefa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834245"
---
# <a name="function-procedures-visual-basic"></a>Function プロシージャ (Visual Basic)
A`Function`手順は、一連の Visual Basic のステートメントで囲まれた、`Function`と`End Function`ステートメント。 `Function`プロシージャは、タスクを実行し、呼び出し元のコードにコントロールを返します。 コントロールが返されたときにも、呼び出し元のコードに値を返します。  
  
 以降後の最初の実行可能ステートメントでは、プロシージャの呼び出し、そのステートメントを実行するには、毎回、`Function`ステートメントと最初の終了`End Function`、 `Exit Function`、または`Return`ステートメントが発生しました。  
  
 定義することができます、`Function`プロシージャでは、モジュール、クラスまたは構造体。 `Public`どこからでも呼び出すことを意味する既定では、モジュール、クラス、またはで定義された構造体にアクセスできるアプリケーションでします。  
  
 A`Function`プロシージャは、定数、変数、または、呼び出し元のコードに渡される式などの引数をとることができます。  
  
## <a name="declaration-syntax"></a>宣言の構文  
 宣言の構文、`Function`手順のとおりです。  
  
```vb  
[Modifiers] Function FunctionName [(ParameterList)] As ReturnType  
    [Statements]  
End Function  
```  
  
 *修飾子*アクセス レベルとオーバー ロード、オーバーライド、共有、およびシャドウ処理に関する情報を指定できます。 詳細については、次を参照してください。[関数ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)します。  
  
 各パラメーターのと同じ方法を宣言する[Sub プロシージャ](./sub-procedures.md)します。  
  
### <a name="data-type"></a>データの種類  
 すべて`Function`手順では、データ型が、同じすべての変数は。 このデータ型がで指定された、`As`句、`Function`ステートメント、およびその関数が呼び出し元のコードに返す値のデータ型を決定します。 次の宣言の例では、これについて説明します。  
  
```vb  
Function yesterday() As Date  
End Function  
  
Function findSqrt(ByVal radicand As Single) As Single  
End Function  
```  
  
 詳細についてを参照してください「パーツ」[関数ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)します。  
  
## <a name="returning-values"></a>値を返す  
 値を`Function`プロシージャが呼び出し元のコードには、戻り値と呼ばれるを送信します。 プロシージャでは、2 つの方法のいずれかでこの値が返されます。  
  
-   使用して、`Return`返し、戻り値を指定するステートメントを呼び出し元のプログラムをすぐに制御します。 次に例を示します。  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement immediately transfers control back  
    ' to the calling code and returns the value of Expression.  
    Return Expression  
End Function  
```  
  
-   プロシージャの 1 つまたは複数のステートメントで、独自の関数名に値を割り当てます。 まで呼び出し元のプログラムに制御が戻らない、`Exit Function`または`End Function`ステートメントが実行されます。 次に例を示します。  
  
```vb  
Function FunctionName [(ParameterList)] As ReturnType  
    ' The following statement does not transfer control back to the calling code.  
    FunctionName = Expression  
    ' When control returns to the calling code, Expression is the return value.  
End Function  
```  
  
 関数名に、戻り値を割り当てることの利点は、コントロールを返さないこと、プロシージャからが検出されるまで、`Exit Function`または`End Function`ステートメント。 これにより、暫定値を割り当てるし、必要に応じて後で調整することができます。  
  
 値を返す方法についての詳細については、次を参照してください。[関数ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)します。 配列を返す方法については、次を参照してください。[配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)します。  
  
## <a name="calling-syntax"></a>呼び出し構文  
 呼び出す、`Function`名前と引数の代入ステートメントまたは式の右側にあるいずれかを含めることによってプロシージャ。 省略可能でないすべての引数の値を指定する必要があり、引数リストをかっこで囲む必要があります。 引数が指定されていない場合、かっこを省略することができます。  
  
 呼び出しの構文を`Function`手順のとおりです。  
  
 *lvalue*  `=`  *functionname* `[(` *argumentlist* `)]`  
  
 `If ((` *functionname* `[(` *argumentlist* `)] / 3) <=`  *expression* `) Then`  
  
 呼び出すと、`Function`手順がありません、戻り値を使用します。 そうでない場合は、関数のすべての操作が実行されは、戻り値は無視されます。 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> この方法で呼ばれます。  
  
### <a name="illustration-of-declaration-and-call"></a>宣言と呼び出しの図  
 次`Function`プロシージャは、最長の辺またはの他の 2 つの辺の値を指定された直角三角形の斜辺を計算します。  
  
 [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
 次の例では、一般的な呼び出しを`hypotenuse`します。  
  
 [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>関連項目

- [プロシージャ](./index.md)
- [Sub プロシージャ](./sub-procedures.md)
- [Property プロシージャ](./property-procedures.md)
- [演算子プロシージャ](./operator-procedures.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [Function ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)
- [方法: 値を返すプロシージャを作成します。](./how-to-create-a-procedure-that-returns-a-value.md)
- [方法: プロシージャから値を返す](./how-to-return-a-value-from-a-procedure.md)
- [方法: 値を返すプロシージャを呼び出す](./how-to-call-a-procedure-that-returns-a-value.md)
