---
title: Visual Basic におけるシャドウ
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
ms.openlocfilehash: 9ad992a53618fa2f410e0b0fb23886c30136384f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58839393"
---
# <a name="shadowing-in-visual-basic"></a>Visual Basic におけるシャドウ
2 つのプログラミング要素は、同じ名前を共有、うち 1 つが非表示できる、または*シャドウ*、もう 1 つ。 このような場合は、シャドウされた要素は参照できません。代わりに、コードでは、要素名を使用する場合、Visual Basic コンパイラに解決されますがシャドウする要素。  
  
## <a name="purpose"></a>目的  
 シャドウの主な目的、クラスのメンバーの定義を保護することです。 基底クラスには、既に定義されている 1 つとして同じ名前の要素を作成する変更を行うこともできます。 このような場合、`Shadows`するメンバーに解決するのには、クラスを通じて参照修飾子強制的に基本クラスの新しい要素の代わりに定義されました。  
  
## <a name="types-of-shadowing"></a>シャドウの種類  
 要素は、2 つの方法で別の要素をシャドウすることができます。 要素はシャドウ ケースが実現されます、シャドウされた要素を含んでいるリージョンのサブ領域内で宣言できます*スコープによる*します。 派生クラスは、シャドウ ケースは、基底クラスのメンバーを再定義できますまたは*継承によって*します。  
  
### <a name="shadowing-through-scope"></a>スコープによるシャドウ  
 プログラミング要素は、モジュール、クラスまたは構造体が同じ名前でスコープが異なることができます。 狭いスコープを持つ要素が他の要素をシャドウするこの方法で 2 つの要素が宣言されているし、コードが共有されている名前を指す、(ブロック スコープでは、最も狭い)。  
  
 たとえば、モジュールを定義できますを`Public`という名前の変数`temp`、モジュール内のプロシージャもという名前のローカル変数を宣言および`temp`。 参照`temp`プロシージャ内からへの参照中に、ローカル変数にアクセス`temp`から外部プロシージャへのアクセス、`Public`変数。 この場合、プロシージャの変数`temp`モジュール変数のシャドウ`temp`します。  
  
 次の図は、2 つの変数、という名前の両方に`temp`します。 ローカル変数`temp`メンバー変数のシャドウ`temp`独自のプロシージャ内からアクセスするときに`p`します。 ただし、`MyClass`キーワードは、シャドウをバイパスし、メンバー変数にアクセスします。  
  
 ![スコープによるシャドウを示しています。 グラフィック。](./media/shadowing/shadow-scope-diagram.gif)
  
 スコープによるシャドウの例は、次を参照してください。[方法。変数と同じ名前の変数を隠す](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)します。  
  
### <a name="shadowing-through-inheritance"></a>継承によるシャドウ  
 派生クラスでは、基本クラスから継承されたプログラミング要素を再定義を再定義する要素は、元の要素をシャドウします。 その他の種類では、任意の種類の宣言された要素は、または一連のオーバー ロードされた要素をシャドウできます。 たとえば、`Integer`シャドウする変数を`Function`プロシージャ。 別のプロシージャでプロシージャをシャドウする場合は、別のパラメーター リストと異なる戻り値の型を使用できます。  
  
 次の図は、基本クラス`b`と派生クラス`d`から継承する`b`します。 基本クラスという名前のプロシージャを定義する`proc`と派生クラスは、同じ名前の別のプロシージャでシャドウします。 最初の`Call`シャドウ ステートメントにアクセスする`proc`派生クラスでします。 ただし、`MyBase`キーワードは、シャドウをバイパスし、基本クラスのシャドウされたプロシージャにアクセスします。  
  
 ![継承によるシャドウのグラフィック ダイアグラム](./media/shadowing/shadowing-inherit-diagram.gif)  
  
 継承によるシャドウの例は、次を参照してください。[方法。変数と同じ名前の変数を隠す](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)と[方法。継承された変数を非表示に](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)します。  
  
#### <a name="shadowing-and-access-level"></a>シャドウとアクセス レベル  
 シャドウの要素は常に、派生クラスを使用してコードからアクセス可能ではありません。 たとえば、宣言することがあります`Private`します。 このような場合は、シャドウ敗北は、コンパイラが同じ要素への参照を解決する場合がありますは行われません。 この要素は、最小の継承はステップ後方シャドウするクラスからアクセス可能な要素です。 シャドウされた要素が、プロシージャの場合は、解像度は同じ名前のパラメーターの一覧で最も近い利用可能なバージョンを型を返します。  
  
 次の例では、3 つのクラスの継承階層を示します。 各クラスを定義、`Sub`プロシージャ`display`、し、各派生クラスの影、`display`基底クラスのプロシージャです。  
  
```  
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
  
 前の例では、派生クラスで`secondClass`shadows`display`で、`Private`プロシージャ。 ときにモジュール`callDisplay`呼び出し`display`で`secondClass`、呼び出し元のコードが範囲外です`secondClass`ため秘密にアクセスできない`display`プロシージャ。 シャドウは行われず、およびコンパイラが基底クラスへの参照を解決`display`プロシージャ。  
  
 ただし、さらに、派生クラス`thirdClass`宣言`display`として`Public`ため、コードでは、`callDisplay`アクセスできます。  
  
## <a name="shadowing-and-overriding"></a>シャドウとオーバーライド  
 シャドウとオーバーライドを混同しないでください。 どちらも、派生クラスは基底クラスから継承し、1 つの宣言された要素と他の再定義に使用されます。 2 つの重要な違いがあります。 比較については、次を参照してください。[の相違点の間でシャドウとオーバーライド](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)します。  
  
## <a name="shadowing-and-overloading"></a>シャドウとオーバー ロード  
 派生クラスで 1 つ以上の要素と同じ基本クラスの要素をシャドウする場合は、その要素のオーバー ロードされたバージョンがシャドウする要素になります。 詳細については、「 [Procedure Overloading](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)」を参照してください。  
  
## <a name="accessing-a-shadowed-element"></a>シャドウされた要素へのアクセス  
 派生クラスから、要素にアクセスするときに通常の方法、派生クラスの現在のインスタンスを通じて、要素名で修飾して、`Me`キーワード。 修飾基本クラスの要素をアクセスするには、派生クラスが基底クラス内の要素をシャドウする場合、`MyBase`キーワード。  
  
 シャドウされた要素へのアクセスの例は、次を参照してください。[方法。変数にアクセスする派生クラスによって非表示に](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)します。  
  
### <a name="declaration-of-the-object-variable"></a>オブジェクト変数の宣言  
 オブジェクト変数を作成する方法は、派生クラスは、シャドウ要素またはシャドウされた要素にアクセスするかどうかも影響します。 次の例では、派生クラスでは、2 つのオブジェクトを作成しますが、として基本クラスと派生クラスとしてもう 1 つのオブジェクトが宣言されています。  
  
```  
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
  
 前の例では、変数`basObj`基底クラスとして宣言されます。 割り当てを`dervCls`オブジェクトをそれには、拡大変換であるためです。 基底クラスが、変数のシャドウのバージョンにアクセスできませんただし、 `z` 、派生クラスでは、そのため、コンパイラは`basObj.z`元の基本クラスの値にします。  
  
## <a name="see-also"></a>関連項目

- [宣言された要素の参照](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Visual Basic におけるスコープ](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [拡大変換と縮小変換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me、My、MyBase、および MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [継承の基本](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
