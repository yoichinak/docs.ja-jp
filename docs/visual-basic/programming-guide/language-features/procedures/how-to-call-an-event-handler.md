---
title: 'How to: Call an Event Handler'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- event handlers [Visual Basic], calling
- event handlers
- procedures [Visual Basic], event handlers
- procedures [Visual Basic], calling
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
ms.openlocfilehash: 0c626a9ad92fe2cd0ea117a9abdd2965a09df2ea
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340428"
---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a>方法 : Visual Basic でイベント ハンドラーを呼び出す

An *event* is an action or occurrence — such as a mouse click or a credit limit exceeded — that is recognized by some program component, and for which you can write code to respond. An *event handler* is the code you write to respond to an event.

 An event handler in Visual Basic is a `Sub` procedure. However, you do not normally call it the same way as other `Sub` procedures. Instead, you identify the procedure as a handler for the event. You can do this either with a [Handles](../../../language-reference/statements/handles-clause.md) clause and a [WithEvents](../../../language-reference/modifiers/withevents.md) variable, or with an [AddHandler Statement](../../../language-reference/statements/addhandler-statement.md). Using a `Handles` clause is the default way to declare an event handler in Visual Basic. This is the way the event handlers are written by the designers when you program in the integrated development environment (IDE). The `AddHandler` statement is suitable for raising events dynamically at run time.

 When the event occurs, Visual Basic automatically calls the event handler procedure. Any code that has access to the event can cause it to occur by executing a [RaiseEvent Statement](../../../language-reference/statements/raiseevent-statement.md).

 You can associate more than one event handler with the same event. In some cases you can dissociate a handler from an event. 詳細については、「[イベント](../events/index.md)」を参照してください。

### <a name="to-call-an-event-handler-using-handles-and-withevents"></a>To call an event handler using Handles and WithEvents

1. Make sure the event is declared with an [Event Statement](../../../language-reference/statements/event-statement.md).

2. Declare an object variable at module or class level, using the [WithEvents](../../../language-reference/modifiers/withevents.md) keyword. The `As` clause for this variable must specify the class that raises the event.

3. In the declaration of the event-handling `Sub` procedure, add a [Handles](../../../language-reference/statements/handles-clause.md) clause that specifies the `WithEvents` variable and the event name.

4. When the event occurs, Visual Basic automatically calls the `Sub` procedure. Your code can use a `RaiseEvent` statement to make the event occur.

     The following example defines an event and a `WithEvents` variable that refers to the class that raises the event. The event-handling `Sub` procedure uses a `Handles` clause to specify the class and event it handles.

     [!code-vb[VbVbcnProcedures#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#4)]

### <a name="to-call-an-event-handler-using-addhandler"></a>To call an event handler using AddHandler

1. Make sure the event is declared with an `Event` statement.

2. Execute an [AddHandler Statement](../../../language-reference/statements/addhandler-statement.md) to dynamically connect the event-handling `Sub` procedure with the event.

3. When the event occurs, Visual Basic automatically calls the `Sub` procedure. Your code can use a `RaiseEvent` statement to make the event occur.

     The following example defines a `Sub` procedure to handle the <xref:System.Windows.Forms.Form.Closing> event of a form. It then uses the [AddHandler Statement](../../../language-reference/statements/addhandler-statement.md) to associate the `catchClose` procedure as an event handler for <xref:System.Windows.Forms.Form.Closing>.

     [!code-vb[VbVbcnProcedures#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#5)]

     You can dissociate an event handler from an event by executing the [RemoveHandler Statement](../../../language-reference/statements/removehandler-statement.md).

## <a name="see-also"></a>関連項目

- [手順](index.md)
- [Sub プロシージャ](sub-procedures.md)
- [Sub ステートメント](../../../language-reference/statements/sub-statement.md)
- [AddressOf 演算子](../../../language-reference/operators/addressof-operator.md)
- [方法 : プロシージャを作成する](how-to-create-a-procedure.md)
- [方法 : 値を返さないプロシージャを呼び出す](how-to-call-a-procedure-that-does-not-return-a-value.md)
