---
title: Handles 句には、含んでいる型またはその基本型の 1 つで定義した WithEvents 変数が必要です。
ms.date: 07/20/2015
f1_keywords:
- vbc30506
- bc30506
helpviewer_keywords:
- BC30506
ms.assetid: 5b66f6a8-f050-4e03-a57f-a64e85f80cb5
ms.openlocfilehash: 191415408f607d0ff768e50c41fa9b3c4405a688
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582826"
---
# <a name="handles-clause-requires-a-withevents-variable-defined-in-the-containing-type-or-one-of-its-base-types"></a>Handles 句には、含んでいる型またはその基本型の 1 つで定義した WithEvents 変数が必要です。

@No__t_1 句に `WithEvents` 変数が指定されていません。 プロシージャ宣言の最後にある `Handles` キーワードは、`WithEvents` キーワードを使用して宣言されたオブジェクト変数によって発生するイベントを処理します。

**エラー ID:** BC30506

## <a name="to-correct-this-error"></a>このエラーを解決するには

必要な `WithEvents` 変数を指定します。

## <a name="example"></a>例

次の例では、Visual Basic は、 [WithEvents](../modifiers/withevents.md)キーワードが <xref:System.Timers.Timer?displayProperty=nameWithType> インスタンスの定義で使用されていないため、コンパイラエラー `BC30506` を生成します。

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

次の例は、`_timer1` 変数が `WithEvents` キーワードで定義されているため、正常にコンパイルされます。

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
