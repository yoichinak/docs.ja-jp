---
title: '方法: 変数と同じ名前の変数を非表示にします (Visual Basic)'
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
ms.openlocfilehash: 487e0a15ba6b52f92ab39fe0bae4ab15fa92707f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629989"
---
# <a name="how-to-hide-a-variable-with-the-same-name-as-your-variable-visual-basic"></a>方法: 変数と同じ名前の変数を非表示にします (Visual Basic)

変数を非表示にするには、その変数を同じ名前の変数で再定義することによって、その変数を*シャドウ*することができます。 非表示にする変数は、次の2つの方法でシャドウすることができます。

- **スコープによるシャドウ処理。** スコープを通じてシャドウするには、非表示にする変数が含まれている領域のサブ領域内で再宣言します。

- **継承によるシャドウ処理。** 非表示にする変数がクラスレベルで定義されている場合は、派生クラスで[Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)キーワードを使用して再宣言することで、継承によってシャドウできます。

## <a name="two-ways-to-hide-a-variable"></a>変数を非表示にする2つの方法

#### <a name="to-hide-a-variable-by-shadowing-it-through-scope"></a>スコープを使用して変数をシャドウすることによって変数を非表示にするには

1. 非表示にする変数を定義するリージョンを決定し、変数で再定義するサブ領域を決定します。

    |変数の領域|再定義に使用できるサブ領域|
    |-----------------------|-------------------------------------------|
    |Module|モジュール内のクラス|
    |クラス|クラス内のサブクラスです。<br /><br /> クラス内のプロシージャ|

    再定義できませんそのプロシージャ内のブロックでプロシージャの変数などの、 `If`...`End If`構築または`For`ループします。

2. サブ領域がまだ存在しない場合は作成します。

3. サブ領域内で、シャドウする変数を宣言する[Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)を記述します。

    サブ領域内のコードが変数名を参照すると、コンパイラはシャドウしている変数への参照を解決します。

    次の例は、スコープを使用したシャドウ処理と、シャドウをバイパスする参照を示しています。

    ```vb
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

    前の例では、 `num`モジュールレベルとプロシージャレベル (プロシージャ`show`内) の両方で変数を宣言しています。 ローカル変数`num`は内`show`のモジュールレベル変数`num`をシャドウするため、ローカル変数は2に設定されます。 ただし、この`num` `useModuleLevelNum`プロシージャには、シャドウするローカル変数はありません。 したがって`useModuleLevelNum` 、では、モジュールレベル変数の値が1に設定されます。

    内`MsgBox` `num`の呼び出しは、モジュール名で修飾することによって、シャドウ機構をバイパスします。 `show` そのため、ローカル変数の代わりにモジュールレベルの変数が表示されます。

#### <a name="to-hide-a-variable-by-shadowing-it-through-inheritance"></a>継承によって変数をシャドウして非表示にするには

1. 非表示にする変数がクラスで宣言されていること、およびクラスレベル (プロシージャの外側) で宣言されていることを確認してください。 それ以外の場合、継承によってシャドウを行うことはできません。

2. 変数がまだ存在しない場合は、そのクラスから派生したクラスを定義します。

3. 派生クラス内で、変数を`Dim`宣言するステートメントを記述します。 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)キーワードを宣言に含めます。

    派生クラスのコードが変数名を参照すると、コンパイラは変数への参照を解決します。

    次の例は、継承によるシャドウ処理を示しています。 2つの参照が作成されます。1つはシャドウを行う変数にアクセスし、もう1つはシャドウ処理をバイパスします。

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

    前の例では、 `shadowString`基底クラスの変数を宣言し、派生クラスでその変数をシャドウしています。 派生クラス`showStrings`のプロシージャは、名前`shadowString`が修飾されていない場合に、文字列のシャドウバージョンを表示します。 次に、が`shadowString` `MyBase`キーワードで修飾されている場合に、シャドウされたバージョンを表示します。

## <a name="robust-programming"></a>信頼性の高いプログラミング

シャドウでは、同じ名前の変数の複数のバージョンが導入されます。 コードステートメントが変数名を参照する場合、コンパイラが参照を解決するバージョンは、コードステートメントの場所や修飾文字列の存在などの要因によって異なります。 これにより、シャドウされた変数の意図しないバージョンを参照するリスクが増加する可能性があります。 シャドウされた変数へのすべての参照を完全に修飾することで、そのリスクを軽減することができます。

## <a name="see-also"></a>関連項目

- [宣言された要素の参照](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Visual Basic でのシャドウ処理](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [シャドウとオーバーライドの違い](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [方法: 継承された変数の非表示](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [方法: 派生クラスによって非表示にされている変数へのアクセス](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me、My、MyBase、および MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [継承の基本](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
