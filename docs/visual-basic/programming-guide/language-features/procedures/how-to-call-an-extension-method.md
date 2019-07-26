---
title: '方法: 拡張メソッド (Visual Basic) を呼び出す'
ms.date: 07/20/2015
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
ms.openlocfilehash: f2058162ab939d2619d7255c884d88c35ee63715
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512671"
---
# <a name="how-to-call-an-extension-method-visual-basic"></a>方法: 拡張メソッド (Visual Basic) を呼び出す

拡張メソッドを使用すると、既存のクラスにメソッドを追加できます。 拡張メソッドが宣言され、スコープ内に入ると、拡張された型のインスタンスメソッドのように呼び出すことができます。 拡張メソッドを記述する方法の詳細については[、「方法:拡張メソッド](./how-to-write-an-extension-method.md)を記述します。

 次の手順では、拡張`PrintAndPunctuate`メソッドについて説明します`punc`。拡張メソッドは、それを呼び出す文字列インスタンスを表示し、その後、2番目のパラメーターのに送信される任意の値を示します。

```vb
Imports System.Runtime.CompilerServices

Module StringExtensions
    <Extension()>
    Public Sub PrintAndPunctuate(ByVal aString As String,
                                 ByVal punc As String)
        Console.WriteLine(aString & punc)
    End Sub

End Module
```

メソッドが呼び出されるときは、そのメソッドがスコープ内にある必要があります。

### <a name="to-call-an-extension-method"></a>拡張メソッドを呼び出すには

1. 拡張メソッドの最初のパラメーターのデータ型を持つ変数を宣言します。 では、 <xref:System.String>変数が必要です。 `PrintAndPunctuate`

    ```vb
    Dim example = "Ready"
    ```

2. その変数は拡張メソッドを呼び出し、その値は最初のパラメーターで`aString`あるにバインドされます。 次の呼び出しステートメントが表示`Ready?`されます。

    ```vb
    example.PrintAndPunctuate("?")
    ```

     この拡張メソッドへの呼び出しは、1つのパラメーターを必要とするいずれか<xref:System.String>のインスタンスメソッドの呼び出しと同じように見えます。

    ```vb
    example.EndsWith("dy")
    example.IndexOf("R")
    ```

3. 別の文字列変数を宣言し、メソッドを再度呼び出して、任意の文字列で動作することを確認します。

    ```vb
    Dim example2 = " or not"
    example2.PrintAndPunctuate("!!!")
    ```

     この時間は次のよう`or not!!!`になります。

## <a name="example"></a>例
 次のコードは、単純な拡張メソッドの作成と使用の完全な例です。

```vb
Imports System.Runtime.CompilerServices
Imports ConsoleApplication1.StringExtensions

Module Module1

    Sub Main()

        Dim example = "Hello"
        example.PrintAndPunctuate(".")
        example.PrintAndPunctuate("!!!!")

        Dim example2 = "Goodbye"
        example2.PrintAndPunctuate("?")
    End Sub

    <Extension()>
    Public Sub PrintAndPunctuate(ByVal aString As String,
                                 ByVal punc As String)
        Console.WriteLine(aString & punc)
    End Sub
End Module

' Output:
' Hello.
' Hello!!!!
' Goodbye?
```

## <a name="see-also"></a>関連項目

- [方法: 拡張メソッドを記述する](./how-to-write-an-extension-method.md)
- [拡張メソッド](./extension-methods.md)
- [Visual Basic 内のスコープ](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
