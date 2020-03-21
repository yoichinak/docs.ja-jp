---
title: 入れ子になった制御構造
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
ms.openlocfilehash: b696c79cd3cada4416b3f4b6cdf96f00b89a5a0a
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266925"
---
# <a name="nested-control-structures-visual-basic"></a>入れ子になった制御構造 (Visual Basic)
制御ステートメントは、ループ内のブロックなど、他の`If...Then...Else`制御ステートメント内に`For...Next`配置できます。 別の制御ステートメント内に置かれた制御ステートメントは *、 ネストされていると*言います。  
  
## <a name="nesting-levels"></a>ネストレベル  
 Visual Basic のコントロール構造は、必要な数のレベルに入れ子にすることができます。 ネストされた構造体を、それぞれの構造体の本文をインデントすることで、読みやすくするのが一般的です。 統合開発環境 (IDE) エディターは、自動的にこれを行います。  
  
 次の例では、行列の`sumRows`各行の正の要素を加算します。  
  
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
  
 前の例では、`Next`最初のステートメントが内部`For`ループを閉じ、最後`Next`のステートメントが外側`For`のループを閉じます。  
  
 同様に、ネストされた`If`ステートメントでは、ステートメント`End If`は最も近い前`If`のステートメントに自動的に適用されます。 入れ`Do`子になったループは、最も内側のステートメントと一`Loop`致するステートメントで、`Do`同様の方法で動作します。  
  
> [!NOTE]
> 多くの制御構造では、キーワードをクリックすると、その構造内のすべてのキーワードが強調表示されます。 たとえば`If`、`If...Then...Else`建設中にクリックすると、建設中の`If`、 `Then`、、、`Else``End If``ElseIf`および のすべてのインスタンスが強調表示されます。 次または前の強調表示されたキーワードに移動するには、Ctrl キーを押しながら Shift キーを押しながら下方向キーを押すか、Ctrl キーを押しながら Shift キーを押しながら上方向キーを押します。  
  
## <a name="nesting-different-kinds-of-control-structures"></a>異なる種類の制御構造のネスト  
 ある種類の制御構造を別の種類の中に入れ子にすることができます。 次の例では、`With`ループ内の`For Each`ブロックとブロック内`If`のネストされた`With`ブロックを使用します。  
  
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
  
## <a name="overlapping-control-structures"></a>コントロール構造の重複  
 制御構造を重ねることはできません。 つまり、入れ子になった構造体は、次の最も内側の構造体内に完全に含まれている必要があります。 たとえば、内部`With`ブロックが終了する前にループ`For`が終了するため、次の配置は無効です。  
  
 ![無効な入れ子の例を示す図。](./media/nested-control-structures/example-invalid-nesting.gif)
  
 Visual Basic コンパイラは、このような重複する制御構造を検出し、コンパイル時エラーを通知します。  
  
## <a name="see-also"></a>関連項目

- [制御フロー](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [条件判断構造](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [ループ構造](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [その他の制御構造](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
