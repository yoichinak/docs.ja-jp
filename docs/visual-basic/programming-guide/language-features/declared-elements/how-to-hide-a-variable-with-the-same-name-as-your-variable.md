---
title: '方法: 変数 (Visual Basic) と同じ名前の変数を非表示にします。'
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- declarations [Visual Basic], elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declaration statements [Visual Basic], declared elements
- declaring elements [Visual Basic]
- referencing declared elements [Visual Basic]
- declared elements [Visual Basic], referencing
- declared elements [Visual Basic], about declared elements
ms.assetid: e39c0752-f19f-4d2e-a453-00df1b5fc7ee
ms.openlocfilehash: 744c7aed50690d5591d1e8248e121cb66ef39108
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59296187"
---
# <a name="how-to-hide-a-variable-with-the-same-name-as-your-variable-visual-basic"></a>方法: 変数 (Visual Basic) と同じ名前の変数を非表示にします。
変数を非表示にすることができます*シャドウ*は、これによって、同じ名前の変数で再定義します。 2 つの方法で非表示に変数をシャドウすることができます。  
  
-   **スコープによるシャドウします。** その操作は、非表示に変数を格納しているリージョンのサブ領域内で再宣言することによってスコープによるシャドウできます。  
  
-   **継承によるシャドウします。** クラス レベルで非表示にする、変数が定義されている場合、することができます、継承によるシャドウを再度宣言することによって、 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)派生クラスでのキーワード。  
  
## <a name="two-ways-to-hide-a-variable"></a>2 つの変数を非表示にする方法  
  
#### <a name="to-hide-a-variable-by-shadowing-it-through-scope"></a>スコープによるシャドウすることによって、変数を非表示にするには  
  
1. を非表示にする変数を定義するリージョンを特定し、で、変数を使用してを再定義するサブ領域を決定します。  
  
    |変数の領域|再定義が使用可能なサブ地域|  
    |-----------------------|-------------------------------------------|  
    |Module|モジュール内のクラス|  
    |クラス|クラス内のサブクラス<br /><br /> クラス内のプロシージャ|  
  
     再定義できませんそのプロシージャ内のブロックでプロシージャの変数などの、 `If`.。`End If`構築または`For`ループします。  
  
2. 存在しない場合は、サブ領域を作成します。  
  
3. 、地区内では、書き込み、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)シャドウの変数を宣言します。  
  
     サブ領域内のコードは、変数名が参照されているとき、コンパイラは変数のシャドウへの参照を解決します。  
  
     次の例では、シャドウの参照と同様に、スコープによるシャドウを示します。  
  
    ```  
    Module shadowByScope  
        ' The following statement declares num as a module-level variable.  
        Public num As Integer  
        Sub show()  
            ' The following statement declares num as a local variable.  
            Dim num As Integer  
            ' The following statement sets the value of the local variable.  
            num = 2  
            ' The following statement displays the module-level variable.  
            MsgBox(CStr(shadowByScope.num))  
        End Sub  
        Sub useModuleLevelNum()  
            ' The following statement sets the value of the module-level variable.  
            num = 1  
            show()  
        End Sub  
    End Module  
    ```  
  
     前の例は、変数を宣言して`num`モジュール レベルとプロシージャ レベルの両方 (の手順で`show`)。 ローカル変数`num`モジュール レベル変数をシャドウ`num`内`show`ので、ローカル変数が 2 に設定します。 ただし、シャドウをローカル変数がない`num`で、`useModuleLevelNum`プロシージャ。 そのため、`useModuleLevelNum`モジュール レベル変数の値を 1 に設定します。  
  
     `MsgBox`内で呼び出す`show`修飾することにより、シャドウ機構をバイパスする`num`モジュールの名前。 そのため、ローカル変数の代わりに、モジュール レベル変数を表示します。  
  
#### <a name="to-hide-a-variable-by-shadowing-it-through-inheritance"></a>継承によるシャドウすることによって、変数を非表示にするには  
  
1. 必ず、クラスでは、および (プロシージャ) の外側のクラス レベルで非表示にする、変数が宣言されてください。 それ以外の場合継承によるシャドウすることはできません。  
  
2. 既に存在しない場合、変数のクラスから派生したクラスを定義します。  
  
3. 派生クラス内では、書き込み、`Dim`ステートメント、変数を宣言します。 含める、 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)キーワードで宣言します。  
  
     派生クラスのコードは、変数名が参照されていると、コンパイラは、変数への参照を解決します。  
  
     次の例では、継承によるシャドウを示します。 2 つの参照変数のシャドウにアクセスする、シャドウになります。  
  
    ```  
    Public Class shadowBaseClass  
        Public shadowString As String = "This is the base class string."  
    End Class  
    Public Class shadowDerivedClass  
        Inherits shadowBaseClass  
        Public Shadows shadowString As String = "This is the derived class string."  
        Public Sub showStrings()  
            Dim s As String = "Unqualified shadowString: " & shadowString &  
                 vbCrLf & "MyBase.shadowString: " & MyBase.shadowString  
            MsgBox(s)  
        End Sub  
    End Class  
    ```  
  
     前の例は、変数を宣言します`shadowString`基底クラスとその派生クラスでシャドウします。 プロシージャ`showStrings`派生クラスでは、シャドウのバージョンの文字列を表示します。 ときに、名前`shadowString`は修飾されません。 シャドウされたバージョンを次に、表示と`shadowString`で修飾されて、`MyBase`キーワード。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 シャドウ処理には、1 つ以上のバージョンの同じ名前の変数が導入されています。 コード ステートメントは、変数名が参照されているときに、コンパイラの参照が解決されるバージョンは、コード ステートメントの場所と該当する文字列の存在などの要因によって異なります。 これにより、意図しないシャドウされた変数のバージョンを参照するリスクが増加することができます。 このリスクを低くには、シャドウされた変数へのすべての参照を完全に修飾します。  
  
## <a name="see-also"></a>関連項目

- [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Visual Basic におけるシャドウ](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [シャドウとオーバーライドの違い](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [方法: 継承された変数を隠す](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [方法: 派生クラスによって非表示になっている変数にアクセスする](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)
- [オーバーライド](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me、My、MyBase、および MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [継承の基本](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
