---
title: ラムダ式はこのイベント ハンドラーから削除されません
ms.date: 07/20/2015
f1_keywords:
- bc42326
- vbc42326
helpviewer_keywords:
- BC42326
ms.assetid: 63214dc6-0112-4245-8ebf-7c9e8f5a5782
ms.openlocfilehash: 20e83306925e91e579aca52f2e7c209c8c686dee
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58817616"
---
# <a name="lambda-expression-will-not-be-removed-from-this-event-handler"></a>ラムダ式はこのイベント ハンドラーから削除されません
ラムダ式は、このイベント ハンドラーからは削除されません。 変数にラムダ式を割り当てるし、変数の追加し、削除イベントを使用します。  
  
 イベント ハンドラーでラムダ式を使用している場合は、意図した動作が見えないがあります。 同じ場合でも、コンパイラはラムダ式定義ごとに、新しいメソッドを生成します。 そのため、次のコードが表示されます`False`します。  
  
```vb  
Module Module1  
  
    Sub Main()  
        Dim fun1 As ChangeInteger = Function(p As Integer) p + 1  
        Dim fun2 As ChangeInteger = Function(p As Integer) p + 1  
        Console.WriteLine(fun1 = fun2)  
    End Sub  
  
    Delegate Function ChangeInteger(ByVal x As Integer) As Integer  
  
End Module  
```  
  
 イベント ハンドラーでラムダ式を使用している場合、予期しない結果が発生する可能性があります。 次の例では、ラムダ式の追加によって`AddHandler`では削除されません、`RemoveHandler`ステートメント。  
  
```vb  
Module Module1  
  
    Event ProcessInteger(ByVal x As Integer)  
  
    Sub Main()  
  
        ' The following line adds one listener to the event.  
        AddHandler ProcessInteger, Function(m As Integer) m  
  
        ' The following statement searches the current listeners   
        ' for a match to remove. However, this lambda is not the same  
        ' as the previous one, so nothing is removed.  
        RemoveHandler ProcessInteger, Function(m As Integer) m  
  
    End Sub  
End Module  
```  
  
 既定では、このメッセージは警告です。 警告を表示しない方法や、警告をエラーとして扱う方法の詳細については、「 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)」を参照してください。  
  
 **エラー ID:** BC42326  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   警告を回避し、ラムダ式を削除する変数にラムダ式を割り当てるし、両方で、変数を使用して、`AddHandler`と`RemoveHandler`ステートメントは、次の例に示すようにします。  
  
```vb  
Module Module1  
  
    Event ProcessInteger(ByVal x As Integer)  
  
    Dim PrintHandler As ProcessIntegerEventHandler  
  
    Sub Main()  
  
        ' Assign the lambda expression to a variable.  
        PrintHandler = Function(m As Integer) m  
  
        ' Use the variable to add the listener.  
        AddHandler ProcessInteger, PrintHandler  
  
        ' Use the variable again when you want to remove the listener.  
        RemoveHandler ProcessInteger, PrintHandler  
  
    End Sub  
End Module  
```  
  
## <a name="see-also"></a>関連項目

- [ラムダ式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [厳密でないデリゲート変換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [イベント](../../../visual-basic/programming-guide/language-features/events/index.md)
