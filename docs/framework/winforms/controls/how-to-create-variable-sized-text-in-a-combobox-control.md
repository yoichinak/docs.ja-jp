---
title: '方法: コンボ ボックス コントロールにサイズ設定されたテキストを作成します。'
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- text [Windows Forms], drawing in combo boxes
- examples [Windows Forms], ComboBox control
- combo boxes [Windows Forms], drawing text
- ComboBox control [Windows Forms], examples [C#]
- ComboBox control [Windows Forms], drawing custom text
ms.assetid: ce39b9ea-e626-49fe-bd5a-f567f6d157df
ms.openlocfilehash: b55a6b66416aa79427035abdfbc19d1b0e21d94e
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707795"
---
# <a name="how-to-create-variable-sized-text-in-a-combobox-control"></a>方法: コンボ ボックス コントロールにサイズ設定されたテキストを作成します。
この例は、内のテキストのカスタム描画を<xref:System.Windows.Forms.ComboBox>コントロール。 項目が、特定の条件を満たしている場合は、大きいフォントで描画され、赤になっています。  
  
## <a name="example"></a>例  
  
```vb  
Private Sub ComboBox1_MeasureItem(ByVal sender As Object, ByVal e As _  
System.Windows.Forms.MeasureItemEventArgs) Handles ComboBox1.MeasureItem  
    Dim bFont As New Font("Arial", 8, FontStyle.Bold)  
    Dim lFont As New Font("Arial", 12, FontStyle.Bold)  
    Dim siText As SizeF  
  
    If ComboBox1.Items().Item(e.Index) = "Two" Then  
        siText = e.Graphics.MeasureString(ComboBox1.Items().Item(e.Index), _  
lFont)  
    Else  
        siText = e.Graphics.MeasureString(ComboBox1.Items().Item(e.Index), bFont)  
    End If  
  
    e.ItemHeight = siText.Height  
    e.ItemWidth = siText.Width  
End Sub  
  
Private Sub ComboBox1_DrawItem(ByVal sender As Object, ByVal e As _  
System.Windows.Forms.DrawItemEventArgs) Handles ComboBox1.DrawItem  
    Dim g As Graphics = e.Graphics  
    Dim bFont As New Font("Arial", 8, FontStyle.Bold)  
    Dim lFont As New Font("Arial", 12, FontStyle.Bold)  
  
    If ComboBox1.Items().Item(e.Index) = "Two" Then  
        g.DrawString(ComboBox1.Items.Item(e.Index), lfont, Brushes.Red, _  
e.Bounds.X, e.Bounds.Y)  
    Else  
        g.DrawString(ComboBox1.Items.Item(e.Index), bFont, Brushes.Black, e.Bounds.X, e.Bounds.Y)  
    End If  
End Sub  
```  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   Windows フォームです。  
  
-   A<xref:System.Windows.Forms.ComboBox>という名前のコントロール`ListBox1`で 3 つの項目を含む、<xref:System.Windows.Forms.ComboBox.Items%2A>プロパティ。 この例では、3 つの項目の名前は`"One", Two", and Three"`します。 <xref:System.Windows.Forms.ComboBox.DrawMode%2A>プロパティの`ComboBox1`に設定する必要があります<xref:System.Windows.Forms.DrawMode.OwnerDrawVariable>します。  
  
    > [!NOTE]
    >  この手法も適用できます、<xref:System.Windows.Forms.ListBox>コントロール-代わりに使用することができます、<xref:System.Windows.Forms.ListBox>の<xref:System.Windows.Forms.ComboBox>します。  
  
-   
  <xref:System.Windows.Forms?displayProperty=nameWithType> 名前空間と <xref:System.Drawing?displayProperty=nameWithType> 名前空間への参照。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.ComboBox.DrawItem>
- <xref:System.Windows.Forms.DrawItemEventArgs>
- <xref:System.Windows.Forms.ComboBox.MeasureItem>
- [組み込みのオーナー描画サポートを備えたコントロール](controls-with-built-in-owner-drawing-support.md)
- [ListBox コントロール](listbox-control-windows-forms.md)
- [ComboBox コントロール](combobox-control-windows-forms.md)
