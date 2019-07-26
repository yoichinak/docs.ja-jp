---
title: Handles 句には、含んでいる型またはその基本型の 1 つで定義した WithEvents 変数が必要です。
ms.date: 07/20/2015
f1_keywords:
- vbc30506
- bc30506
helpviewer_keywords:
- BC30506
ms.assetid: 5b66f6a8-f050-4e03-a57f-a64e85f80cb5
ms.openlocfilehash: 04c94d3d32660d1a186a9bb377c49a53e1451be6
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512740"
---
# <a name="handles-clause-requires-a-withevents-variable-defined-in-the-containing-type-or-one-of-its-base-types"></a>Handles 句には、含んでいる型またはその基本型の 1 つで定義した WithEvents 変数が必要です。
句に変数が`WithEvents`指定されていません。 `Handles` プロシージャ宣言の最後にある`WithEvents` キーワードを使用すると、キーワードを使用して宣言されたオブジェクト変数によって生成されるイベントを処理できます。`Handles`
  
 **エラー ID:** BC30506

## <a name="to-correct-this-error"></a>このエラーを解決するには
  
- 必要な`WithEvents`変数を指定します。
  
## <a name="example"></a>例

次の例では、Visual Basic、 `BC30506` [WithEvents](../modifiers/withevents.md)キーワードが<xref:System.Timers.Timer?displayProperty=nameWithType>インスタンスの定義で使用されていないため、コンパイラエラーが生成されます。

```vb
Imports System.Timers

Module Module1
    Private _timer1 As New Timer() With {.Interval = 1000, .Enabled = True}
    
    Sub Main()
        Console.WriteLine("Press any key to start the timer...")
        Console.ReadKey()
        _timer1.Start()
        Console.ReadKey()
    End Sub

    Private Sub Timer1_Tick(sender As Object, args As EventArgs) Handles _timer1.Elapsed
        Console.WriteLine("Press any key to terminate...")
    End Sub
End Module
```

次の例は、 `_timer1` `WithEvents`キーワードを使用して変数が定義されているため、正常にコンパイルされます。

```vb
Imports System.Timers

Module Module1
    Private WithEvents _timer1 As New Timer() With {.Interval = 1000}

    Sub Main()
        Console.WriteLine("Press any key to start the timer...")
        Console.ReadKey()
        _timer1.Start()
        Console.ReadKey()
    End Sub

    Private Sub Timer1_Tick(sender As Object, args As EventArgs) Handles _timer1.Elapsed
        Console.WriteLine("Press any key to terminate...")
    End Sub

End Module
```

## <a name="see-also"></a>関連項目

- [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)
