---
title: '方法: 変数にアクセスする (Visual Basic)、派生クラスによって非表示'
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- base classes [Visual Basic], accessing elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declared elements [Visual Basic], referencing
- variables [Visual Basic], accessing hidden
ms.assetid: ae21a8ac-9cd4-4fba-a3ec-ecc4321ef93c
ms.openlocfilehash: a97a51d4570d87eaa873fb3152ad810f528dff46
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832178"
---
# <a name="how-to-access-a-variable-hidden-by-a-derived-class-visual-basic"></a>方法: 変数にアクセスする (Visual Basic)、派生クラスによって非表示
派生クラスのコードは、変数にアクセスするときに、コンパイラ通常解決アクセス可能な最も近いバージョンは、アクセス可能なバージョンへの参照を最小限継承の手順との下位にアクセスするクラスからします。 場合は、変数は、派生クラスで定義されているが、コードは、通常の定義にアクセスします。  
  
 派生クラスの変数が、基底クラスの変数をシャドウする場合、基底クラスのバージョンは非表示になります。 ただしで修飾基底クラスの変数にアクセスすることができます、`MyBase`キーワード。  
  
### <a name="to-access-a-base-class-variable-hidden-by-a-derived-class"></a>派生クラスによって非表示に基底クラスの変数にアクセスするには  
  
-   式または代入ステートメント、変数名の前に、`MyBase`キーワードとピリオド (`.`)。  
  
     コンパイラは、変数の基本クラスのバージョンへの参照を解決します。  
  
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
 シャドウされた変数の意図しないバージョンを参照するリスクを削減するには、シャドウされた変数へのすべての参照を完全に修飾することができます。 シャドウ処理には、1 つ以上のバージョンの同じ名前の変数が導入されています。 コード ステートメントは、変数名が参照されているときに、コンパイラの参照が解決されるバージョンは、コード ステートメントの場所と該当する文字列の存在などの要因によって異なります。 これにより、変数の正しくないバージョンを参照するリスクが増加することができます。  
  
## <a name="see-also"></a>関連項目

- [宣言された要素の参照](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Visual Basic におけるシャドウ](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [シャドウとオーバーライドの違い](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [方法: 変数と同じ名前の変数を非表示にします。](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [方法: 継承された変数を非表示にします。](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me、My、MyBase、および MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [継承の基本](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
