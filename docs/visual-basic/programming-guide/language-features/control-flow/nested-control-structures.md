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
ms.openlocfilehash: c016722332dafa3d3be91a1e9e98cc0ce9a49717
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58835194"
---
# <a name="nested-control-structures-visual-basic"></a>入れ子になった制御構造 (Visual Basic)
たとえば他のコントロール ステートメント内のコントロール ステートメントを配置することができます、`If...Then...Else`ブロック内で、`For...Next`ループします。 別のコントロール ステートメントの内側に配置する制御ステートメントはモード*入れ子になった*します。  
  
## <a name="nesting-levels"></a>入れ子のレベル  
 Visual Basic での制御構造は、複数のレベルにネストできます。 一般的に、それぞれのインデントして入れ子になった構造体を読みやすくすることをお勧めします。 統合開発環境 (IDE) のエディターを使用して、この自動的に行います。  
  
 次の例では、プロシージャ`sumRows`マトリックスの行ごとの正の要素をまとめて追加します。  
  
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
  
 前の例では、最初の`Next`ステートメント終了内部`For`ループし、最後`Next`外側のステートメントを閉じます`For`ループします。  
  
 同様に、入れ子になった`If`、ステートメント、`End If`ステートメントが自動的に適用する前に、最も近い`If`ステートメント。 入れ子になった`Do`で同様に、最も内側のループが`Loop`ステートメントの内側に一致する`Do`ステートメント。  
  
> [!NOTE]
>  多くの制御構造のキーワードをクリックすると、すべての構造のキーワードが強調表示されます。 クリックすると、`If`で、`If...Then...Else`構築のすべてのインスタンス`If`、 `Then`、 `ElseIf`、 `Else`、および`End If`構築では強調表示されます。 次または前の強調表示されているキーワードに移動するには、CTRL と shift キーを押しながら下方向キーまたは CTRL + SHIFT キーを押しながら上方向キーを押します。  
  
## <a name="nesting-different-kinds-of-control-structures"></a>さまざまな種類の制御構造の入れ子  
 別の種類内のコントロール構造体の 1 つの種類を入れ子にすることができます。 次の例では、`With`ブロック内で、`For Each`ループを入れ子になった`If`ブロック内で、`With`ブロックします。  
  
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
 制御構造を重ねることはできません。 つまり、入れ子になった構造を完全に次の最も内側の構造内で含める必要があります。 たとえば、次の配置が無効ですので、`For`内部の前にループが終了した`With`ブロックを終了します。  
  
 ![無効な入れ子の例を示す図。](./media/nested-control-structures/example-invalid-nesting.gif) 
  
 Visual Basic コンパイラでは、このような重複する制御構造を検出し、コンパイル時エラーを通知します。  
  
## <a name="see-also"></a>関連項目

- [制御フロー](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [条件判断構造](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [ループ構造](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [その他の制御構造](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
