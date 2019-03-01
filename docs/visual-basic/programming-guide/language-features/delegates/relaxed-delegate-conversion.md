---
title: 厳密でないデリゲート変換 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions [Visual Basic], relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
ms.openlocfilehash: 96941754f17326893437cdcf83c588880e010cc0
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979509"
---
# <a name="relaxed-delegate-conversion-visual-basic"></a>厳密でないデリゲート変換 (Visual Basic)
厳密でないデリゲート変換を使用すると、そのシグネチャが同一でない場合でも sub や関数をデリゲートやハンドラーに割り当てることができます。 そのため、デリゲートへのバインドは既にメソッドの呼び出しは許可されているバインディングで一貫性のあるになります。  
  
## <a name="parameters-and-return-type"></a>パラメーターと戻り値の型  
 正確なシグネチャの一致の代わりに厳密でない変換が必要です、次の条件が満たされているときに`Option Strict`に設定されている`On`:  
  
-   各デリゲート パラメーターのデータ型から割り当てられている関数の対応するパラメーターのデータ型への拡大変換が存在する必要がありますまたは`Sub`します。 次の例では、デリゲート`Del1`1 つのパラメーター、`Integer`します。 パラメーター`m`式で割り当てられたラムダから拡大変換がある対象のデータ型である必要があります`Integer`など`Long`または`Double`します。  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#2)]  
  
     縮小変換が許可される場合にのみ`Option Strict`に設定されている`Off`します。  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#8)]  
  
-   割り当て済みの関数の戻り値の型から反対方向に拡大変換が存在する必要がありますまたは`Sub`デリゲートの戻り値の型にします。 次の例については、各割り当てられているラムダ式の本体に拡大変換をデータ型に評価する必要があります`Integer`戻り値の型のため、`del1`は`Integer`します。  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#3)]  
  
 場合`Option Strict`に設定されている`Off`制限の拡大が双方向で削除します。  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#4)]  
  
## <a name="omitting-parameter-specifications"></a>パラメーターの指定を省略します。  
 厳密でないデリゲートでは、割り当てられているメソッドのパラメーターの仕様を完全に省略することもできます。  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#5)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#6)]  
  
 いくつかのパラメーターを指定して他のユーザーを省略できませんに注意してください。  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#15)]  
  
 パラメーターを省略する機能は、いくつかの複雑なパラメーターが含まれて、イベント ハンドラーを定義するような状況で役立ちます。 いくつかのイベント ハンドラーの引数は使用されません。 代わりに、ハンドラーによって、コントロールをイベントが登録されているし、引数を無視の状態が直接アクセスします。 厳密でないデリゲートを使用すると、ときにあいまいさの結果はありません、このような宣言の引数を省略できます。 次の例では、完全に指定されたメソッドで`OnClick`として書き直す`RelaxedOnClick`します。  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a>AddressOf 例  
 ラムダ式は、型の関係を簡単に参照してください、前の例で使用されます。 ただし、同じリラクゼーションを使用するデリゲートの割り当ての許可`AddressOf`、 `Handles`、または`AddHandler`します。  
  
 次の例では、機能`f1`、 `f2`、 `f3`、および`f4`すべてに代入できる`Del1`します。  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#7)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#9)]  
  
 次の例は有効な場合にのみ`Option Strict`に設定されている`Off`します。  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#14)]  
  
## <a name="dropping-function-returns"></a>関数の戻り値を削除します。  
 厳密でないデリゲート変換は、機能を割り当てることができます、`Sub`デリゲート、事実上、関数の戻り値を無視します。 ただし、割り当てることはできません、`Sub`を関数デリゲート。 次の例では、関数のアドレスで`doubler`に割り当てられている`Sub`委任`Del3`します。  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#10)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#11)]  
  
## <a name="see-also"></a>関連項目
- [ラムダ式](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [拡大変換と縮小変換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [デリゲート](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [方法: Visual Basic での別のプロシージャに渡す](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [ローカル型の推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
