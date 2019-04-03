---
title: '方法: Visual Basic でイベント ハンドラーを呼び出す'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- event handlers [Visual Basic], calling
- event handlers
- procedures [Visual Basic], event handlers
- procedures [Visual Basic], calling
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
ms.openlocfilehash: dd21f80e4b3892cbd9db901b619ecff98f6b70bd
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837768"
---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a>方法: Visual Basic でイベント ハンドラーを呼び出す
*イベント*操作または発生は、-クリックやクレジットの上限を超えたマウスなど、応答するコードを記述でき、いくつかのプログラム コンポーネントによってを認識するは。 *イベント ハンドラー*イベントに応答を記述するコードに示します。  
  
 Visual Basic でイベント ハンドラーは、`Sub`プロシージャ。 ただし、呼び出すことはありません通常、同じ方法他`Sub`プロシージャ。 代わりに、イベントのハンドラーとしてプロシージャを識別します。 こうことで、[処理](../../../../visual-basic/language-reference/statements/handles-clause.md)句と[WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md)変数、または、 [AddHandler ステートメント](../../../../visual-basic/language-reference/statements/addhandler-statement.md)します。 使用して、`Handles`句は、既定の方法が Visual Basic でイベント ハンドラーを宣言します。 これは、イベント ハンドラーは、統合開発環境 (IDE) でプログラミングするときに、デザイナーによって書き込まれる方法です。 `AddHandler`ステートメントは実行時に動的にイベントを発生させるために適しています。  
  
 イベントが発生すると、Visual Basic は自動的にイベント ハンドラーのプロシージャを呼び出します。 イベントにアクセスできる任意のコードを実行することによって発生する可能性を[RaiseEvent ステートメント](../../../../visual-basic/language-reference/statements/raiseevent-statement.md)します。  
  
 同じイベントでは、1 つ以上のイベント ハンドラーを関連付けることができます。 場合によっては、イベントからハンドラーを切り離すこともできます。 詳細については、「[イベント](../../../../visual-basic/programming-guide/language-features/events/index.md)」を参照してください。  
  
### <a name="to-call-an-event-handler-using-handles-and-withevents"></a>ハンドルと WithEvents を使用して、イベント ハンドラーを呼び出す  
  
1.  でイベントが宣言されていることを確認、 [Event ステートメント](../../../../visual-basic/language-reference/statements/event-statement.md)します。  
  
2.  レベルを使用して、モジュールまたはクラスでオブジェクト変数を宣言、 [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md)キーワード。 `As`この変数は、イベントを発生させるクラスを指定する必要があります。  
  
3.  イベント処理の宣言で`Sub`プロシージャを追加、[処理](../../../../visual-basic/language-reference/statements/handles-clause.md)句を指定する、`WithEvents`変数、およびイベント名。  
  
4.  Visual Basic を自動的に呼び出して、イベントの発生時に、`Sub`プロシージャ。 コードを使用できます、`RaiseEvent`イベントで発生するステートメント。  
  
     次の例では、イベントを定義して、`WithEvents`イベントを発生させるクラスを参照する変数。 イベント処理`Sub`プロシージャは、`Handles`クラスとイベントの処理を指定する句。  
  
     [!code-vb[VbVbcnProcedures#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#4)]  
  
### <a name="to-call-an-event-handler-using-addhandler"></a>AddHandler を使用して、イベント ハンドラーを呼び出す  
  
1.  でイベントが宣言されていることを確認、`Event`ステートメント。  
  
2.  実行、 [AddHandler ステートメント](../../../../visual-basic/language-reference/statements/addhandler-statement.md)イベント処理を動的に接続する`Sub`イベントにプロシージャ。  
  
3.  Visual Basic を自動的に呼び出して、イベントの発生時に、`Sub`プロシージャ。 コードを使用できます、`RaiseEvent`イベントで発生するステートメント。  
  
     次の例では、定義、`Sub`を処理する手順、<xref:System.Windows.Forms.Form.Closing>フォームのイベント。 次を使用して、 [AddHandler ステートメント](../../../../visual-basic/language-reference/statements/addhandler-statement.md)に関連付ける、`catchClose`のイベント ハンドラーとプロシージャ<xref:System.Windows.Forms.Form.Closing>します。  
  
     [!code-vb[VbVbcnProcedures#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#5)]  
  
     実行することによって、イベントからイベント ハンドラーの関連付けを解除することができます、 [RemoveHandler ステートメント](../../../../visual-basic/language-reference/statements/removehandler-statement.md)します。  
  
## <a name="see-also"></a>関連項目

- [プロシージャ](./index.md)
- [Sub プロシージャ](./sub-procedures.md)
- [Sub ステートメント](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [AddressOf 演算子](../../../../visual-basic/language-reference/operators/addressof-operator.md)
- [方法: プロシージャを作成します。](./how-to-create-a-procedure.md)
- [方法: 値を返さないプロシージャを呼び出す](./how-to-call-a-procedure-that-does-not-return-a-value.md)
