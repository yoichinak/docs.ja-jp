---
title: '方法 : 拡張メソッドを呼び出す'
ms.date: 07/20/2015
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
ms.openlocfilehash: a19705a8f90833d48869df26a18d19b0ad1488e0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340392"
---
# <a name="how-to-call-an-extension-method-visual-basic"></a>方法: 拡張メソッドを呼び出す (Visual Basic)

Extension methods enable you to add methods to an existing class. After an extension method is declared and brought into scope, you can call it like an instance method of the type that it extends. For more information about how to write an extension method, see [How to: Write an Extension Method](./how-to-write-an-extension-method.md).

 The following instructions refer to extension method `PrintAndPunctuate`, which will display the string instance that invokes it, followed by whatever value is sent in for the second parameter, `punc`.

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

The method must be in scope when it is called.

### <a name="to-call-an-extension-method"></a>To call an extension method

1. Declare a variable that has the data type of the first parameter of the extension method. For `PrintAndPunctuate`, you need a <xref:System.String> variable:

    ```vb
    Dim example = "Ready"
    ```

2. That variable will invoke the extension method, and its value is bound to the first parameter, `aString`. The following calling statement will display `Ready?`.

    ```vb
    example.PrintAndPunctuate("?")
    ```

     Notice that the call to this extension method looks just like a call to any one of the <xref:System.String> instance methods that require one parameter:

    ```vb
    example.EndsWith("dy")
    example.IndexOf("R")
    ```

3. Declare another string variable and call the method again to see that it works with any string.

    ```vb
    Dim example2 = " or not"
    example2.PrintAndPunctuate("!!!")
    ```

     The result this time is: `or not!!!`.

## <a name="example"></a>例
 The following code is a complete example of the creation and use of a simple extension method.

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

- [方法 : 拡張メソッドを作成する](./how-to-write-an-extension-method.md)
- [拡張メソッド](./extension-methods.md)
- [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
