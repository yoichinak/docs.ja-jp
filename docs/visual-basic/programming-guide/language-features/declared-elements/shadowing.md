---
title: シャドウ
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], shadowing
- overriding, and shadowing
- shadowing
- duplicate names [Visual Basic]
- shadowing, by inheritance
- declared elements [Visual Basic], referencing
- shadowing, by scope
- declared elements [Visual Basic], hiding
- naming conflicts, shadowing
- declared elements [Visual Basic], shadowing
- shadowing, and overriding
- scope [Visual Basic], shadowing
- Shadows keyword [Visual Basic], about
- objects [Visual Basic], names
- names [Visual Basic], shadowing
ms.assetid: 54bb4c25-12c4-4181-b4a0-93546053964e
ms.openlocfilehash: 20a33478f622fca6d3183772f53dcb3e72f79409
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266886"
---
# <a name="shadowing-in-visual-basic"></a>Visual Basic におけるシャドウ
2 つのプログラミング要素が同じ名前を共有する場合、そのうちの 1 つが隠れたり *、シャドウ*したりできます。 このような場合、シャドウされた要素は参照できません。代わりに、コードで要素名を使用すると、Visual Basic コンパイラは要素をシャドウする要素に解決します。  
  
## <a name="purpose"></a>目的  
 シャドウの主な目的は、クラス メンバーの定義を保護することです。 基本クラスは、既に定義した要素と同じ名前の要素を作成する変更を受ける場合があります。 この場合、修飾子は`Shadows`、クラスを通じて参照を新しい基本クラスの要素ではなく、定義したメンバーに解決するように強制します。  
  
## <a name="types-of-shadowing"></a>シャドウの種類  
 要素は、2 つの異なる方法で別の要素をシャドウできます。 シャドウ要素は、シャドウされた要素を含む領域のサブ領域内で宣言*できます。* または、派生クラスは基本クラスのメンバーを再定義*できます。*  
  
### <a name="shadowing-through-scope"></a>スコープを通じてシャドウ  
 同じモジュール、クラス、または構造体内のプログラミング要素の名前は同じでスコープが異なる可能性があります。 2 つの要素がこの方法で宣言され、コードが共有する名前を参照する場合、スコープが狭い要素は他の要素をシャドウします (ブロック スコープは最も狭くなります)。  
  
 たとえば、モジュールは という名前`Public``temp`の変数を定義でき、モジュール内のプロシージャは、 という名前`temp`のローカル変数も宣言できます。 プロシージャ内`temp`からの参照はローカル変数にアクセスし、プロシージャの外部`temp`からの参照は変数にアクセス`Public`します。 この場合、プロシージャ変数は`temp`モジュール変数`temp`をシャドウします。  
  
 次の図は、 という 2`temp`つの変数を示しています。 ローカル変数`temp`は、独自のプロシージャ`temp``p`内からアクセスすると、メンバー変数をシャドウします。 ただし、キーワード`MyClass`はシャドウをバイパスし、メンバー変数にアクセスします。  
  
 ![スコープを通じてシャドウを表示するグラフィック。](./media/shadowing/shadow-scope-diagram.gif)
  
 スコープを使用してシャドウを行う例については、「[方法 : 変数と同じ名前の変数を非表示にする](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)」を参照してください。  
  
### <a name="shadowing-through-inheritance"></a>継承によるシャドウ  
 派生クラスが基本クラスから継承されたプログラミング要素を再定義する場合、再定義する要素は元の要素をシャドウします。 宣言された要素、またはオーバーロードされた要素のセットを、他の型でシャドウできます。 たとえば、変数は`Integer`プロシージャを`Function`シャドウできます。 別のプロシージャでプロシージャをシャドウする場合は、別のパラメーター リストと別の戻り値の型を使用できます。  
  
 次の図は、基底`b`クラスと、`d`を`b`継承する派生クラスを示しています。 基本クラスは という名前`proc`のプロシージャを定義し、派生クラスは同じ名前の別のプロシージャを使用してそのプロシージャをシャドウします。 最初`Call`のステートメントは、派生クラスの`proc`シャドウにアクセスします。 ただし、この`MyBase`キーワードはシャドウをバイパスし、基本クラスのシャドウされたプロシージャにアクセスします。  
  
 ![継承によるシャドウのグラフィック ダイアグラム](./media/shadowing/shadowing-inherit-diagram.gif)  
  
 継承によるシャドウの例については、「 方法[: 変数と同じ名前の変数を非表示にする](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)」および「[方法 : 継承された変数を非表示にする](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)」を参照してください。  
  
#### <a name="shadowing-and-access-level"></a>シャドウとアクセス レベル  
 シャドウ要素は、派生クラスを使用するコードから常にアクセスできるわけではありません。 たとえば、それが宣言`Private`されている場合があります。 このような場合、シャドウは負け、コンパイラはシャドウが存在しなかった場合と同じ要素への参照を解決します。 この要素は、シャドウイング クラスから戻る最も少ない派生ステップでアクセス可能な要素です。 シャドウされた要素がプロシージャの場合、解決方法は、同じ名前、パラメーター リスト、および戻り値の型を持つ最も近いアクセス可能なバージョンに対する解決です。  
  
 次の例は、3 つのクラスの継承階層を示しています。 各クラスは`Sub`プロシージャ`display`を定義し、各派生`display`クラスは基本クラス内のプロシージャをシャドウします。  
  
```vb  
Public Class firstClass  
    Public Sub display()  
        MsgBox("This is firstClass")  
    End Sub  
End Class  
Public Class secondClass  
    Inherits firstClass  
    Private Shadows Sub display()  
        MsgBox("This is secondClass")  
    End Sub  
End Class  
Public Class thirdClass  
    Inherits secondClass  
    Public Shadows Sub display()  
        MsgBox("This is thirdClass")  
    End Sub  
End Class  
Module callDisplay  
    Dim first As New firstClass  
    Dim second As New secondClass  
    Dim third As New thirdClass  
    Public Sub callDisplayProcedures()  
        ' The following statement displays "This is firstClass".  
        first.display()  
        ' The following statement displays "This is firstClass".  
        second.display()  
        ' The following statement displays "This is thirdClass".  
        third.display()  
    End Sub  
End Module  
```  
  
 前の例では、派生クラス`secondClass`のシャドウ`display`とプロシージャの`Private`使用。 モジュール`callDisplay`が`display`で`secondClass`呼び出されると、呼`secondClass`び出し元のコード`display`は外部にあるため、プライベート プロシージャにアクセスできません。 シャドウ処理は敗北し、コンパイラは基本クラス`display`のプロシージャへの参照を解決します。  
  
 ただし、さらに派生`thirdClass`クラスは`display``Public`として宣言するため、 の`callDisplay`コードからアクセスできます。  
  
## <a name="shadowing-and-overriding"></a>シャドウとオーバーライド  
 シャドウとオーバーライドを混同しないでください。 両方とも、派生クラスが基本クラスから継承し、宣言された要素を別の要素で再定義するときに使用されます。 しかし、両者には大きな違いがあります。 比較については、「[シャドウとオーバーライドの違い](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)」を参照してください。  
  
## <a name="shadowing-and-overloading"></a>シャドウとオーバーロード  
 派生クラス内の複数の要素を使用して同じ基本クラス要素をシャドウすると、シャドウする要素はその要素のオーバーロードされたバージョンになります。 詳細については、「 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)」を参照してください。  
  
## <a name="accessing-a-shadowed-element"></a>シャドウされた要素へのアクセス  
 派生クラスから要素にアクセスする場合、通常は、`Me`その派生クラスの現在のインスタンスを通じて、要素名をキーワードで修飾します。 派生クラスが基本クラスの要素をシャドウする場合は、キーワードで修飾することで基本クラスの要素に`MyBase`アクセスできます。  
  
 シャドウされた要素にアクセスする例については、「 方法[: 派生クラスによって非表示になっている変数にアクセス](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)する 」を参照してください。  
  
### <a name="declaration-of-the-object-variable"></a>オブジェクト変数の宣言  
 オブジェクト変数の作成方法は、派生クラスがシャドウする要素またはシャドウされた要素のいずれにアクセスするかにも影響を与えます。 次の例では、派生クラスから 2 つのオブジェクトを作成しますが、一方のオブジェクトは基本クラスとして宣言され、もう 1 つのオブジェクトは派生クラスとして宣言されます。  
  
```vb  
Public Class baseCls  
    ' The following statement declares the element that is to be shadowed.  
    Public z As Integer = 100  
End Class  
Public Class dervCls  
    Inherits baseCls  
    ' The following statement declares the shadowing element.  
    Public Shadows z As String = "*"  
End Class  
Public Class useClasses  
    ' The following statement creates the object declared as the base class.  
    Dim basObj As baseCls = New dervCls()  
    ' Note that dervCls widens to its base class baseCls.  
    ' The following statement creates the object declared as the derived class.  
    Dim derObj As dervCls = New dervCls()  
    Public Sub showZ()
    ' The following statement outputs 100 (the shadowed element).  
        MsgBox("Accessed through base class: " & basObj.z)  
    ' The following statement outputs "*" (the shadowing element).  
        MsgBox("Accessed through derived class: " & derObj.z)  
    End Sub  
End Class  
```  
  
 前の例では、変数`basObj`は基本クラスとして宣言されています。 オブジェクトを`dervCls`オブジェクトに割り当てることは、拡大変換を構成するため有効です。 ただし、基本クラスは、派生クラス内の変数`z`のシャドウバージョンにアクセスできないため、コンパイラは元の基本クラス`basObj.z`の値に解決されます。  
  
## <a name="see-also"></a>関連項目

- [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Visual Basic におけるスコープ](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me、My、MyBase、および MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [継承の基本](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
