---
title: '方法: 拡張メソッド (Visual Basic) を作成します。'
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: 00d62d275f7afc06e066a375dc1ffcd74b23c9ed
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666002"
---
# <a name="how-to-write-an-extension-method-visual-basic"></a>方法: 拡張メソッド (Visual Basic) を作成します。
拡張メソッドを使用すると、既存のクラスにメソッドを追加できます。 そのクラスのインスタンスの場合と同様、拡張メソッドを呼び出すことができます。  
  
### <a name="to-define-an-extension-method"></a>拡張メソッドを定義するには  
  
1. Visual Studio では、新規または既存の Visual Basic アプリケーションを開きます。  
  
2. 拡張メソッドを定義するファイルの上部にある次の import ステートメントを含めます。  
  
    ```  
    Imports System.Runtime.CompilerServices  
    ```  
  
3. 新規または既存のアプリケーションで、モジュール内には、拡張機能属性を持つメソッドの定義を開始します。  
  
    ```  
    <Extension()>  
    ```  
  
4. 最初のパラメーターの型が拡張するデータ型にする必要がありますが、通常の方法で、メソッドを宣言します。  
  
    ```  
    <Extension()>   
    Public Sub subName (ByVal para1 As ExtendedType, <other parameters>)  
         ' < Body of the method >  
    End Sub  
    ```  
  
## <a name="example"></a>例  
 次の例では、モジュールの拡張メソッドを宣言する`StringExtensions`します。 2 番目のモジュール`Module1`、インポート`StringExtensions`メソッドを呼び出します。 呼び出されると、拡張メソッドがスコープ内にする必要があります。 拡張メソッド`PrintAndPunctuate`拡張、<xref:System.String>文字列インスタンスを表示するメソッドを持つクラスが続けてでパラメーターとして送信される区切り記号の文字列。  
  
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
  
 メソッドが 2 つのパラメーターで定義され、1 つだけということに注意してください。 最初のパラメーターでは、`aString`に、メソッドの定義がバインドされている`example`のインスタンス`String`メソッドを呼び出します。 この例の出力は次のとおりです。  
  
 `Hello?`  
  
 `Hello!!!!`  
  
## <a name="see-also"></a>関連項目

- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [拡張メソッド](./extension-methods.md)
- [Module ステートメント](../../../../visual-basic/language-reference/statements/module-statement.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [Visual Basic におけるスコープ](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
