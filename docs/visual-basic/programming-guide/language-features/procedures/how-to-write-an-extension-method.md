---
title: '方法 : 拡張メソッドを作成する'
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: 697508f86ff4ff0a89150b65782121395d0fed12
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346013"
---
# <a name="how-to-write-an-extension-method-visual-basic"></a>方法: 拡張メソッドを作成する (Visual Basic)

Extension methods enable you to add methods to an existing class. The extension method can be called as if it were an instance of that class.

### <a name="to-define-an-extension-method"></a>To define an extension method

1. Open a new or existing Visual Basic application in Visual Studio.

2. At the top of the file in which you want to define an extension method, include the following import statement:

    ```vb
    Imports System.Runtime.CompilerServices
    ```

3. Within a module in your new or existing application, begin the method definition with the [`<Extension>`](xref:System.Runtime.CompilerServices.ExtensionAttribute) attribute:

    ```vb
    <Extension()>
    ```

    Note that the `Extension` attribute can only be applied to a method (a `Sub` or `Function` procedure) in a Visual Basic [Module](../../../language-reference/statements/module-statement.md). If you apply it to a method in a `Class` or a `Structure`, the Visual Basic compiler generates error [BC36551](../../../misc/bc36551.md), "Extension methods can be defined only in modules."

4. Declare your method in the ordinary way, except that the type of the first parameter must be the data type you want to extend.

    ```vb
    <Extension()>
    Public Sub SubName(para1 As ExtendedType, <other parameters>)
         ' < Body of the method >
    End Sub
    ```

## <a name="example"></a>例

The following example declares an extension method in module `StringExtensions`. A second module, `Module1`, imports `StringExtensions` and calls the method. The extension method must be in scope when it is called. Extension method `PrintAndPunctuate` extends the <xref:System.String> class with a method that displays the string instance followed by a string of punctuation symbols sent in as a parameter.

```vb
' Declarations will typically be in a separate module.
Imports System.Runtime.CompilerServices

Module StringExtensions
    <Extension()>
    Public Sub PrintAndPunctuate(aString As String, punc As String)
        Console.WriteLine(aString & punc)
    End Sub

End Module
```

```vb
' Import the module that holds the extension method you want to use,
' and call it.

Imports ConsoleApplication2.StringExtensions

Module Module1

    Sub Main()
        Dim example = "Hello"
        example.PrintAndPunctuate("?")
        example.PrintAndPunctuate("!!!!")
    End Sub

End Module
```

Notice that the method is defined with two parameters and called with only one. The first parameter, `aString`, in the method definition is bound to `example`, the instance of `String` that calls the method. この例の出力は次のとおりです。

```console
Hello?
Hello!!!!
```

## <a name="see-also"></a>関連項目

- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [拡張メソッド](extension-methods.md)
- [Module ステートメント](../../../language-reference/statements/module-statement.md)
- [プロシージャのパラメーターと引数](procedure-parameters-and-arguments.md)
- [Scope in Visual Basic](../declared-elements/scope.md)
