---
title: '方法: 拡張メソッド (Visual Basic) を呼び出す'
ms.date: 07/20/2015
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
ms.openlocfilehash: 2543694e6bf8da5b67ecaccc92633a8448154063
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58837131"
---
# <a name="how-to-call-an-extension-method-visual-basic"></a>方法: 拡張メソッド (Visual Basic) を呼び出す
拡張メソッドを使用すると、既存のクラスにメソッドを追加できます。 拡張メソッドが宣言され、スコープに取り込む後、は、拡張する型のインスタンス メソッドのように呼び出すことができます。 拡張メソッドを記述する方法の詳細については、次を参照してください。[方法。拡張メソッドを記述](./how-to-write-an-extension-method.md)します。  
  
 次の手順は、拡張メソッドを参照してください`PrintAndPunctuate`、2 番目のパラメーターに渡される文字列インスタンスを呼び出した後にどのような値が表示されますが`punc`します。  
  
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
  
 メソッドは、呼び出された場合、スコープ内にする必要があります。  
  
### <a name="to-call-an-extension-method"></a>拡張メソッドを呼び出す  
  
1.  拡張メソッドの最初のパラメーターのデータ型を持つ変数を宣言します。 `PrintAndPunctuate`、する必要があります、<xref:System.String>変数。  
  
    ```  
    Dim example = "Ready"  
    ```  
  
2.  変数が、拡張メソッドを呼び出し、その値が最初のパラメーターにバインドされている`aString`します。 次のステートメントの呼び出しが表示されます`Ready?`します。  
  
    ```  
    example.PrintAndPunctuate("?")  
    ```  
  
     この拡張メソッドの呼び出しは単に注意してくださいなどのいずれかを呼び出し、<xref:System.String>インスタンス メソッドを 1 つのパラメーターを必要とします。  
  
    ```  
    example.EndsWith("dy")  
    example.IndexOf("R")  
    ```  
  
3.  もう 1 つの文字列変数を宣言し、任意の文字列で動作するかを確認するには、もう一度メソッドを呼び出します。  
  
    ```  
    Dim example2 = " or not"  
    example2.PrintAndPunctuate("!!!")  
    ```  
  
     この時間になります:`or not!!!`します。  
  
## <a name="example"></a>例  
 次のコード作成の完全な例を単純な拡張メソッドを使用します。  
  
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

- [方法: 拡張メソッドを作成します。](./how-to-write-an-extension-method.md)
- [拡張メソッド](./extension-methods.md)
- [Visual Basic におけるスコープ](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
