---
title: Null-conditional Operators
ms.date: 10/19/2018
helpviewer_keywords:
- null-conditional operators [Visual Basic]
- ?. operator [Visual Basic]
- ?[] operator [C#]
- ?[] operator [Visual Basic]
ms.openlocfilehash: 003f579a7128bbe2462b7fbe7057de03e61bfbe6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348289"
---
# <a name="-and--null-conditional-operators-visual-basic"></a>?. and ?() null-conditional operators (Visual Basic)

Tests the value of the left-hand operand for null (`Nothing`) before performing a member access (`?.`) or index (`?()`) operation; returns `Nothing` if the left-hand operand evaluates to `Nothing`. Note that in expressions that ordinarily return value types, the null-conditional operator returns a <xref:System.Nullable%601>.

These operators help you write less code to handle null checks, especially when descending into data structures. (例:

```vb
' Nothing if customers is Nothing
Dim length As Integer? = customers?.Length

' Nothing if customers is Nothing
Dim first As Customer = customers?(0)

' Nothing if customers, the first customer, or Orders is Nothing
Dim count As Integer? = customers?(0)?.Orders?.Count()
```

For comparison, the alternative code for the first of these expressions without a null-conditional operator is:

```vb
Dim length As Integer
If customers IsNot Nothing Then
   length = customers.Length
End If
```

Sometimes you need to take an action on an object that may be null, based on the value of a Boolean member on that object (like the Boolean property `IsAllowedFreeShipping` in the following example):

```vb
Dim customer = FindCustomerByID(123) 'customer will be Nothing if not found.

If customer IsNot Nothing AndAlso customer.IsAllowedFreeShipping Then
  ApplyFreeShippingToOrders(customer)
End If
```

You can shorten your code and avoid manually checking for null by using the null-conditional operator as follows:

```vb
Dim customer = FindCustomerByID(123) 'customer will be Nothing if not found.

If customer?.IsAllowedFreeShipping Then ApplyFreeShippingToOrders(customer)
```

Null 条件演算子はショートサーキットです。  If one operation in a chain of conditional member access and index operations returns `Nothing`, the rest of the chain’s execution stops.  In the following example, `C(E)` isn't evaluated if `A`, `B`, or `C` evaluates to `Nothing`.

```vb
A?.B?.C?(E)
```

Another use for null-conditional member access is to invoke delegates in a thread-safe way with much less code.  The following example defines two types, a `NewsBroadcaster` and a `NewsReceiver`. News items are sent to the receiver by the `NewsBroadcaster.SendNews` delegate.

```vb
Public Module NewsBroadcaster
   Dim SendNews As Action(Of String)

   Public Sub Main()
      Dim rec As New NewsReceiver()
      Dim rec2 As New NewsReceiver()
      SendNews?.Invoke("Just in: A newsworthy item...")
   End Sub

   Public Sub Register(client As Action(Of String))
      SendNews = SendNews.Combine({SendNews, client})
   End Sub
End Module

Public Class NewsReceiver
   Public Sub New()
      NewsBroadcaster.Register(AddressOf Me.DisplayNews)
   End Sub

   Public Sub DisplayNews(newsItem As String)
      Console.WriteLine(newsItem)
   End Sub
End Class
```

If there are no elements in the `SendNews` invocation list, the `SendNews` delegate throws a <xref:System.NullReferenceException>. Before null conditional operators, code like the following ensured that the delegate invocation list was not `Nothing`:

```vb
SendNews = SendNews.Combine({SendNews, client})
If SendNews IsNot Nothing Then
   SendNews("Just in...")
End If
```

新しい方法は格段に単純です。

```vb
SendNews = SendNews.Combine({SendNews, client})
SendNews?.Invoke("Just in...")
```

コンパイラが `SendNews` を評価するためのコードを一度しか生成せず、一時変数に結果が保持されるため、新しい方法はスレッド セーフです。 null 条件デリゲート呼び出し構文 `SendNews?(String)` がないため、`Invoke` メソッドを明示的に呼び出す必要があります。

## <a name="see-also"></a>関連項目

- [Operators (Visual Basic)](index.md)
- [Visual Basic のプログラミング ガイド](../../../visual-basic/programming-guide/index.md)
- [Visual Basic の言語リファレンス](../../../visual-basic/language-reference/index.md)
