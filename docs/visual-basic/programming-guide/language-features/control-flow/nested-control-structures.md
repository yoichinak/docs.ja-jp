---
title: 入れ子になった制御構造 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, control flow
- control structures [Visual Basic], nested
- conditional statements [Visual Basic], nested
- statements [Visual Basic], control flow
- control flow [Visual Basic], nested control statements
- structures [Visual Basic], nested control
- nested control statements [Visual Basic]
ms.assetid: cf60b061-65d9-44a8-81f2-b0bdccd23a05
ms.openlocfilehash: f559bf603605873f1b9155e9a96cb367e5420343
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941686"
---
# <a name="nested-control-structures-visual-basic"></a>入れ子になった制御構造 (Visual Basic)
制御ステートメントは、 `If...Then...Else` `For...Next`ループ内のブロックなど、他のコントロールステートメント内に配置できます。 別の control ステートメント内に配置された control ステートメントは、*入れ子になっ*ていると言います。  
  
## <a name="nesting-levels"></a>入れ子のレベル  
 Visual Basic の制御構造は、必要な数のレベルに入れ子にすることができます。 入れ子構造体を読みやすくするには、それぞれの本文をインデントするのが一般的です。 これは、統合開発環境 (IDE) エディターによって自動的に行われます。  
  
 次の例では、プロシージャ`sumRows`によって、マトリックスの各行の正の要素が追加されます。  
  
```vb
Public Sub sumRows(ByVal a(,) As Double, ByRef r() As Double)  
    Dim i, j As Integer  
    For i = 0 To UBound(a, 1)  
        r(i) = 0  
        For j = 0 To UBound(a, 2)  
            If a(i, j) > 0 Then  
                r(i) = r(i) + a(i, j)  
            End If  
        Next j  
    Next i  
End Sub  
```  
  
 前の例では、最初`Next`のステートメントは内側`For`のループを閉じ`Next` 、最後のステートメント`For`は外側のループを閉じます。  
  
 同様に、入れ子`If`になった`End If`ステートメントでは、ステートメントは最も`If`近い先行するステートメントに自動的に適用されます。 入れ子`Do`になったループは同様の方法で動作`Loop`し、最も内側`Do`のステートメントが最も内側のステートメントに一致します。  
  
> [!NOTE]
> 多くの制御構造では、キーワードをクリックすると、構造内のすべてのキーワードが強調表示されます。 たとえば、 `If...Then...Else`構築をクリック`If`すると、、 `Then` `ElseIf`、、 `Else`、および`If` `End If`のすべてのインスタンスが構築されます。 次または前の強調表示されたキーワードに移動するには、CTRL + SHIFT + ↓キーを押すか、CTRL + SHIFT + 上方向キーを押します。  
  
## <a name="nesting-different-kinds-of-control-structures"></a>さまざまな種類の制御構造の入れ子  
 1つの種類のコントロール構造を別の種類に入れ子にすることができます。 次の例では`With` 、ブロック内`For Each`のブロックを`If`使用して`With` 、ループと入れ子になったブロックをブロック内に配置します。  
  
```vb
For Each ctl As System.Windows.Forms.Control In Me.Controls  
    With ctl  
        .BackColor = System.Drawing.Color.Yellow  
        .ForeColor = System.Drawing.Color.Black  
        If .CanFocus Then  
            .Text = "Colors changed"  
            If Not .Focus() Then  
                ' Insert code to process failed focus.  
            End If  
        End If  
    End With  
Next ctl  
```  
  
## <a name="overlapping-control-structures"></a>重複する制御構造  
 制御構造を重ねることはできません。 つまり、入れ子構造は、次の最も内側の構造体内に完全に含まれている必要があります。 たとえば、次の配置は無効です。これ`For`は、内部`With`ブロックが終了する前にループが終了するためです。  
  
 ![無効な入れ子の例を示す図。](./media/nested-control-structures/example-invalid-nesting.gif) 
  
 Visual Basic コンパイラは、このような重複する制御構造を検出し、コンパイル時エラーを通知します。  
  
## <a name="see-also"></a>関連項目

- [制御フロー](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [条件判断構造](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [ループ構造](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [その他の制御構造](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
