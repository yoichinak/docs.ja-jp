---
title: '方法: 拡張メソッドを記述する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: 7a7a9d16d9f69071e9d1dacb0558f7ca92e1d21e
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631027"
---
# <a name="how-to-write-an-extension-method-visual-basic"></a>方法: 拡張メソッドを記述する (Visual Basic)
拡張メソッドを使用すると、既存のクラスにメソッドを追加できます。 拡張メソッドは、そのクラスのインスタンスであるかのように呼び出すことができます。

### <a name="to-define-an-extension-method"></a>拡張メソッドを定義するには

1. Visual Studio で新規または既存の Visual Basic アプリケーションを開きます。

2. 拡張メソッドを定義するファイルの先頭に、次の import ステートメントを追加します。

    ```vb
    Imports System.Runtime.CompilerServices
    ```

3. 新規または既存のアプリケーションのモジュール内で、拡張属性を使用してメソッド定義を開始します。

    ```vb
    <Extension()>
    ```

4. 通常の方法でメソッドを宣言します。ただし、最初のパラメーターの型は、拡張するデータ型である必要があります。

    ```vb
    <Extension()>
    Public Sub SubName (ByVal para1 As ExtendedType, <other parameters>)
         ' < Body of the method >
    End Sub
    ```

## <a name="example"></a>例
 次の例では、モジュール`StringExtensions`で拡張メソッドを宣言しています。 2番目の`Module1`モジュールは`StringExtensions` 、メソッドをインポートして呼び出します。 拡張メソッドが呼び出されたときは、その拡張メソッドがスコープ内にある必要があります。 拡張メソッド`PrintAndPunctuate`は、 <xref:System.String>パラメーターとしてで送信される区切り記号の文字列を文字列インスタンスに表示するメソッドを使用して、クラスを拡張します。
  
```vb
' Declarations will typically be in a separate module.
Imports System.Runtime.CompilerServices

Module StringExtensions
    <Extension()>
    Public Sub PrintAndPunctuate(ByVal aString As String,
                                 ByVal punc As String)
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
  
 メソッドは2つのパラメーターで定義され、1つだけを使用して呼び出されることに注意してください。 メソッド定義内の`aString`最初のパラメーターであるは、メソッド`example`を呼び出すの`String`インスタンスにバインドされます。 この例の出力は次のとおりです。
  
 `Hello?`  
  
 `Hello!!!!`  
  
## <a name="see-also"></a>関連項目

- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [拡張メソッド](./extension-methods.md)
- [Module ステートメント](../../../../visual-basic/language-reference/statements/module-statement.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [Visual Basic 内のスコープ](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
