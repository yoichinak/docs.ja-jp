---
title: '方法: 派生クラスによって非表示になっている変数にアクセスする'
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- base classes [Visual Basic], accessing elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declared elements [Visual Basic], referencing
- variables [Visual Basic], accessing hidden
ms.assetid: ae21a8ac-9cd4-4fba-a3ec-ecc4321ef93c
ms.openlocfilehash: 276cb1411c66e1f7205507a1b1053cc8642c7cb0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345407"
---
# <a name="how-to-access-a-variable-hidden-by-a-derived-class-visual-basic"></a>方法: 派生クラスによって非表示になっている変数にアクセスする (Visual Basic)

派生クラスのコードで変数にアクセスすると、コンパイラでは、通常、最も近いアクセス可能なバージョン、つまり、アクセスするクラスからさかのぼって最も少ない派生ステップでアクセス可能なバージョンに参照が解決されます。 変数が派生クラスに定義されている場合、コードでは通常、その定義にアクセスします。

派生クラス変数で基底クラスの変数をシャドウする場合、基底クラスのバージョンが隠されます。 ただし、`MyBase` キーワードを使用して修飾することによって、基底クラスの変数にアクセスできます。

### <a name="to-access-a-base-class-variable-hidden-by-a-derived-class"></a>派生クラスによって隠された基底クラスの変数にアクセスするには

- 式または代入ステートメントで、変数名の前に `MyBase` キーワードとピリオド (`.`) を指定します。

    コンパイラでは、変数の基底クラス バージョンに参照が解決されます。

    次の例に、継承によるシャドウ処理を示しています。 それによって、2 つの参照が作成されます。シャドウする変数にアクセスするものと、シャドウ処理をバイパスするものです。

    ```vb
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

    前の例では、基底クラスで `shadowString` 変数を宣言し、派生クラスでそれをシャドウしています。 派生クラスのプロシージャ `showStrings` では、名前 `shadowString` が修飾されていない場合に、文字列のシャドウしているバージョンが表示されます。 さらに、`shadowString` が `MyBase` キーワードで修飾されている場合は、シャドウされたバージョンが表示されます。

## <a name="robust-programming"></a>信頼性の高いプログラミング

シャドウされた変数の意図しないバージョンを参照するリスクを低減するために、シャドウされた変数へのすべての参照を完全修飾することができます。 シャドウによって、同じ名前の変数の複数のバージョンが取り込まれます。 コード ステートメントで変数名を参照する場合、コンパイラによる参照の解決先のバージョンは、コード ステートメントの場所や修飾文字列の存在などの要因によって異なります。 これにより、変数の誤ったバージョンを参照するリスクが高まる可能性があります。

## <a name="see-also"></a>関連項目

- [宣言された要素の参照](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Visual Basic におけるシャドウ](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [シャドウとオーバーライドの違い](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [方法: 自分で宣言した変数と同じ名前の変数を隠す](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [方法: 継承された変数を隠す](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me、My、MyBase、および MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [継承の基本](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
