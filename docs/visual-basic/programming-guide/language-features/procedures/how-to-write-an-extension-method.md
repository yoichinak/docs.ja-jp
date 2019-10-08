---
title: '方法: 拡張メソッドを記述する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: d01596d50db8ba1078e8ac82caa951418645c977
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004615"
---
# <a name="how-to-write-an-extension-method-visual-basic"></a>方法: 拡張メソッドを記述する (Visual Basic)

拡張メソッドを使用すると、既存のクラスにメソッドを追加できます。 拡張メソッドは、そのクラスのインスタンスであるかのように呼び出すことができます。

### <a name="to-define-an-extension-method"></a>拡張メソッドを定義するには

1. Visual Studio で新規または既存の Visual Basic アプリケーションを開きます。

2. 拡張メソッドを定義するファイルの先頭に、次の import ステートメントを追加します。

    ```vb
    Imports System.Runtime.CompilerServices
    ```

3. 新規または既存のアプリケーションのモジュール内で、 [`<Extension>`](xref:System.Runtime.CompilerServices.ExtensionAttribute)属性を使用してメソッド定義を開始します。

    ```vb
    <Extension()>
    ```
 
   @No__t-0 属性は、Visual Basic[モジュール](../../../language-reference/statements/module-statement.md)内のメソッド (`Sub` または `Function` プロシージャ) にのみ適用できます。 @No__t 0 または `Structure` のメソッドに適用した場合、Visual Basic コンパイラによってエラー [BC36551](../../../misc/bc36551.md)が生成されます。 "拡張メソッドはモジュール内でのみ定義できます。"

4. 通常の方法でメソッドを宣言します。ただし、最初のパラメーターの型は、拡張するデータ型である必要があります。

    ```vb
    <Extension()>
    Public Sub SubName(para1 As ExtendedType, <other parameters>)
         ' < Body of the method >
    End Sub
    ```

## <a name="example"></a>例

 次の例では、モジュール `StringExtensions` の拡張メソッドを宣言しています。 2番目のモジュール (@no__t 0) は `StringExtensions` をインポートし、メソッドを呼び出します。 拡張メソッドが呼び出されたときは、その拡張メソッドがスコープ内にある必要があります。 拡張メソッド `PrintAndPunctuate` は、文字列インスタンスを表示するメソッドを使用して <xref:System.String> クラスを拡張し、パラメーターとしてに送信される区切り記号の文字列を続けます。
  
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
  
 メソッドは2つのパラメーターで定義され、1つだけを使用して呼び出されることに注意してください。 メソッド定義内の最初のパラメーターである @no__t 0 は、メソッドを呼び出す `String` のインスタンス @no__t にバインドされます。 この例の出力は次のとおりです。
  
 ```console
 Hello?
 Hello!!!!
 ```
  
## <a name="see-also"></a>関連項目

- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [拡張メソッド](extension-methods.md)
- [Module ステートメント](../../../language-reference/statements/module-statement.md)
- [プロシージャのパラメーターと引数](procedure-parameters-and-arguments.md)
- [Visual Basic 内のスコープ](../declared-elements/scope.md)
