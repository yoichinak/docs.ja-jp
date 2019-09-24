---
title: '方法: Visual Basic でイベントハンドラーを呼び出す'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- event handlers [Visual Basic], calling
- event handlers
- procedures [Visual Basic], event handlers
- procedures [Visual Basic], calling
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
ms.openlocfilehash: a9e090e83b180686ccb832aa6efb314c7e0fcc9a
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216620"
---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a>方法: Visual Basic でイベントハンドラーを呼び出す

*イベント*は、何らかのプログラムコンポーネントによって認識されるアクションまたは発生 (たとえば、マウスクリックやクレジットの制限を超えた場合) で、応答するコードを記述できます。 イベント*ハンドラー*は、イベントに応答するために記述するコードです。

 Visual Basic のイベントハンドラーは`Sub`プロシージャです。 ただし、通常、他の`Sub`プロシージャと同じ方法で呼び出すことはありません。 代わりに、プロシージャをイベントのハンドラーとして指定します。 これは、 [Handles](../../../language-reference/statements/handles-clause.md)句と[WithEvents](../../../language-reference/modifiers/withevents.md)変数、または[AddHandler ステートメント](../../../language-reference/statements/addhandler-statement.md)を使用して行うことができます。 句の`Handles`使用は、Visual Basic でイベントハンドラーを宣言する既定の方法です。 これは、統合開発環境 (IDE: integrated development environment) でプログラミングするときに、デザイナーによってイベントハンドラーが記述される方法です。 ステートメント`AddHandler`は、実行時にイベントを動的に発生させるために適しています。

 イベントが発生すると、Visual Basic によってイベントハンドラープロシージャが自動的に呼び出されます。 イベントにアクセスできるコードでは、 [RaiseEvent ステートメント](../../../language-reference/statements/raiseevent-statement.md)を実行することによってイベントが発生する可能性があります。

 複数のイベントハンドラーを同じイベントに関連付けることができます。 場合によっては、イベントからハンドラーの関連付けを解除できます。 詳細については、「[イベント](../events/index.md)」を参照してください。

### <a name="to-call-an-event-handler-using-handles-and-withevents"></a>ハンドルと WithEvents を使用してイベントハンドラーを呼び出すには

1. イベントが[イベントステートメント](../../../language-reference/statements/event-statement.md)を使用して宣言されていることを確認します。

2. [WithEvents](../../../language-reference/modifiers/withevents.md)キーワードを使用して、モジュールまたはクラスレベルでオブジェクト変数を宣言します。 この`As`変数の句では、イベントを発生させるクラスを指定する必要があります。

3. イベント処理`Sub`プロシージャの宣言で、 `WithEvents`変数とイベント名を指定する[Handles](../../../language-reference/statements/handles-clause.md)句を追加します。

4. イベントが発生すると、Visual Basic によっ`Sub`てプロシージャが自動的に呼び出されます。 コードでは、ステートメント`RaiseEvent`を使用してイベントを発生させることができます。

     次の例では、イベントを`WithEvents`定義し、イベントを発生させるクラスを参照する変数を定義します。 イベント処理`Sub`プロシージャは、句を`Handles`使用して、処理するクラスとイベントを指定します。

     [!code-vb[VbVbcnProcedures#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#4)]

### <a name="to-call-an-event-handler-using-addhandler"></a>AddHandler を使用してイベントハンドラーを呼び出すには

1. イベントが`Event`ステートメントで宣言されていることを確認します。

2. [AddHandler ステートメント](../../../language-reference/statements/addhandler-statement.md)を実行して、イベント処理`Sub`プロシージャをイベントに動的に接続します。

3. イベントが発生すると、Visual Basic によっ`Sub`てプロシージャが自動的に呼び出されます。 コードでは、ステートメント`RaiseEvent`を使用してイベントを発生させることができます。

     次の例では`Sub` 、フォームの<xref:System.Windows.Forms.Form.Closing>イベントを処理するプロシージャを定義します。 次に、 [AddHandler ステートメント](../../../language-reference/statements/addhandler-statement.md)を使用して`catchClose` 、プロシージャをの<xref:System.Windows.Forms.Form.Closing>イベントハンドラーとして関連付けます。

     [!code-vb[VbVbcnProcedures#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#5)]

     [RemoveHandler ステートメント](../../../language-reference/statements/removehandler-statement.md)を実行すると、イベントからイベントハンドラーの関連付けを解除できます。

## <a name="see-also"></a>関連項目

- [手順](index.md)
- [Sub プロシージャ](sub-procedures.md)
- [Sub ステートメント](../../../language-reference/statements/sub-statement.md)
- [AddressOf 演算子](../../../language-reference/operators/addressof-operator.md)
- [方法: プロシージャを作成する](how-to-create-a-procedure.md)
- [方法: 値を返さないプロシージャを呼び出す](how-to-call-a-procedure-that-does-not-return-a-value.md)
