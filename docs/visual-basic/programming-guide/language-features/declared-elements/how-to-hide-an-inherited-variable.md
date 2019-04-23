---
title: '方法: 継承された変数 (Visual Basic) を非表示にします。'
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declaration statements [Visual Basic], declared elements
- referencing declared elements [Visual Basic]
- declared elements [Visual Basic], referencing
- declared elements [Visual Basic], about declared elements
- variables [Visual Basic], hiding inherited
ms.assetid: 765728d9-7351-4a30-999d-b5f34f024412
ms.openlocfilehash: ee147ecd00b88b538ace32844c42ac9c5022b2ef
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59331703"
---
# <a name="how-to-hide-an-inherited-variable-visual-basic"></a>方法: 継承された変数 (Visual Basic) を非表示にします。
派生クラスでは、その基底クラスのすべての定義を継承します。 基底クラスの要素として、同じ名前を使用して変数を定義する場合は、非表示にできます、または*シャドウ*、派生クラスで、変数を定義するときにその基本クラスの要素。 これを行う場合、シャドウ機構を明示的にバイパスしない限り、派生クラスのコード、変数にアクセスします。  
  
 継承された変数を非表示にするもう 1 つの理由は、基底クラスのリビジョンから保護するためです。 基底クラスには、継承している要素を変更する変更を行うこともできます。 この場合、`Shadows`修飾子は基底クラス要素への代わりに、変数に解決する派生クラスからの参照。  
  
### <a name="to-hide-an-inherited-variable"></a>継承された変数を非表示にするには  
  
1. (プロシージャ) の外側のクラス レベルで非表示にする、変数が宣言されていることを確認します。 それ以外の場合非表示にする必要はありません。  
  
2. 派生クラス内で作成、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)変数を宣言します。 継承された変数のと同じ名前を使用します。  
  
3. 含める、 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)キーワードで宣言します。  
  
     派生クラスのコードは、変数名が参照されていると、コンパイラは、変数への参照を解決します。  
  
     次の例では、継承された変数のシャドウを示します。  
  
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

- [宣言された要素の参照](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Visual Basic におけるシャドウ](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [シャドウとオーバーライドの違い](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [方法: 変数と同じ名前の変数を非表示にします。](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [方法: 派生クラスによって非表示に変数にアクセスします。](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me、My、MyBase、および MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [継承の基本](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
