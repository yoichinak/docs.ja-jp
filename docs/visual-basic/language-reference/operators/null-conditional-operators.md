---
title: Null 条件演算子 (Visual Basic)
ms.date: 10/19/2018
helpviewer_keywords:
- null-conditional operators [Visual Basic]
- ?. operator [Visual Basic]
- ?[] operator [C#]
- ?[] operator [Visual Basic]
ms.openlocfilehash: 4815fe7ad337634cfb56127fbd24a47a37fdd74b
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/06/2019
ms.locfileid: "65062946"
---
# <a name="-and--null-conditional-operators-visual-basic"></a>?. そして。() null 条件演算子 (Visual Basic)

Null の左側のオペランドの値をテスト (`Nothing`) メンバー アクセスを実行する前に (`?.`) またはインデックス (`?()`); の操作を返します。`Nothing`に左側のオペランドが評価された場合`Nothing`します。 通常の値の型を返す式、null 条件演算子が返されます、<xref:System.Nullable%601>します。

これらの演算子を使用して、データ構造を下って場合は特に、null のチェックを処理するには、少ないコードを記述するのに役立ちます。 例えば:

```vb
' Nothing if customers is Nothing  
Dim length As Integer? = customers?.Length  

' Nothing if customers is Nothing
Dim first As Customer = customers?(0)

' Nothing if customers, the first customer, or Orders is Nothing
Dim count As Integer? = customers?(0)?.Orders?.Count()   
```

比較については、null 条件演算子を使用せず、これらの式の最初の代替のコードは次のとおりです。

```vb
Dim length As Integer
If customers IsNot Nothing Then
   length = customers.Length
End If
```

可能性のある null の場合、そのオブジェクトのブール型のメンバーの値に基づいてオブジェクトの操作の実行に必要がある場合があります (などのブール型プロパティ`IsAllowedFreeShipping`次の例)。

```vb
  Dim customer = FindCustomerByID(123) 'customer will be Nothing if not found.
  
  If customer IsNot Nothing AndAlso customer.IsAllowedFreeShipping Then
   ApplyFreeShippingToOrders(customer)
  End If
```

コードを短くし、次のように、null 条件演算子を使用して、手動での null チェックを回避できます。

```vb
 Dim customer = FindCustomerByID(123) 'customer will be Nothing if not found.
 
 If customer?.IsAllowedFreeShipping Then ApplyFreeShippingToOrders(customer)
```

Null 条件演算子はショートサーキットです。  条件付きメンバー アクセスおよびインデックス操作のチェーン内の 1 つの操作を返す場合`Nothing`残りのチェーンの実行が停止します。  次の例では、`C(E)`場合は評価されません`A`、 `B`、または`C`に評価される`Nothing`します。

```vb
A?.B?.C?(E);
```

Null 条件メンバー アクセスの別の用途では、はるかに少ないコードでスレッド セーフな方法でデリゲートを呼び出します。  次の例は、2 つの型を定義、`NewsBroadcaster`と`NewsReceiver`します。 ニュース項目によって、受信側に送信されます、`NewsBroadcaster.SendNews`を委任します。

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

内の要素がない場合、`SendNews`呼び出しリスト、`SendNews`デリゲートがスローされます、<xref:System.NullReferenceException>します。 Null 条件演算子では、前にコードのデリゲートの呼び出しリストがありませんが、次のことを確認するよう`Nothing`:

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

- [演算子 (Visual Basic)](index.md)
- [Visual Basic プログラミング ガイド](../../../visual-basic/programming-guide/index.md)
- [Visual Basic の言語リファレンス](../../../visual-basic/language-reference/index.md)
