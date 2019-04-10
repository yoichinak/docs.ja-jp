---
title: '方法: Windows フォーム内の ToolStrip 項目の間隔と配置を変更する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], aligning items
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], aligning items
ms.assetid: cd483466-0f49-43df-addf-e2b5fcd64027
ms.openlocfilehash: bed943466348447e30947c170e27027f324342c6
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59323175"
---
# <a name="how-to-change-the-spacing-and-alignment-of-toolstrip-items-in-windows-forms"></a>方法: Windows フォーム内の ToolStrip 項目の間隔と配置を変更する
<xref:System.Windows.Forms.ToolStrip>コントロールがサイズ変更の間隔などのレイアウト機能を完全にサポート<xref:System.Windows.Forms.ToolStripItem>で相互に比較した、コントロールの配置を制御、<xref:System.Windows.Forms.ToolStrip>とに関連するコントロールの間の間隔、<xref:System.Windows.Forms.ToolStrip>します。  
  
 の既定値、<xref:System.Windows.Forms.ToolStripItem.AutoSize%2A>プロパティは`true`、設定しない限り、コントロールは自動的に規模、<xref:System.Windows.Forms.ToolStripItem.AutoSize%2A>プロパティを`false`します。  
  
### <a name="to-manually-size-a-toolstripitem"></a>ToolStripItem を手動で調整するには  
  
1. 設定、<xref:System.Windows.Forms.ToolStripItem.AutoSize%2A>プロパティを`false`に関連付けられたコントロール。  
  
    ```vb  
    ToolStripButton1.AutoSize = False  
    ```  
  
    ```csharp  
    toolStripButton1.AutoSize = false;  
    ```  
  
2. 設定、<xref:System.Windows.Forms.ToolStripItem.Size%2A>プロパティに関連付けられている希望どおり<xref:System.Windows.Forms.ToolStripItem>します。  
  
### <a name="to-set-the-spacing-of-a-toolstripitem"></a>ToolStripItem の間隔を設定するには  
  
1. (ピクセル単位) で、目的の値を挿入、<xref:System.Windows.Forms.ToolStripItem.Margin%2A>関連するコントロールのプロパティ。  
  
     値、<xref:System.Windows.Forms.ToolStripItem.Margin%2A>プロパティは、この順序で項目と隣接する項目間の間隔を指定します。左、上、右、下。  
  
    ```vb  
    ToolStripTextBox1.Margin = New System.Windows.Forms.Padding _  
        (3, 0, 3, 0)  
    ```  
  
    ```csharp  
    toolStripTextBox1.Margin = new System.Windows.Forms.Padding   
        (3, 0, 3, 0);  
    ```  
  
### <a name="to-align-a-toolstripitem-to-the-right-side-of-the-toolstrip"></a>コマンド バーの右側に ToolStripItem を配置するには  
  
1. 設定、<xref:System.Windows.Forms.ToolStripItem.Alignment%2A>プロパティを<xref:System.Windows.Forms.ToolStripItemAlignment.Right>に関連付けられたコントロール。 既定では、<xref:System.Windows.Forms.ToolStripItem.Alignment%2A>に設定されている<xref:System.Windows.Forms.ToolStripItemAlignment.Left>の左側にあるコントロールを配置する、<xref:System.Windows.Forms.ToolStrip>します。  
  
    ```vb  
    ToolStripSplitButton1.Alignment = _  
        System.Windows.Forms.ToolStripItemAlignment.Right  
    ```  
  
    ```csharp  
    toolStripSplitButton1.Alignment =   
        System.Windows.Forms.ToolStripItemAlignment.Right;  
    ```  
  
### <a name="to-arrange-toolstrip-items-on-the-toolstrip"></a>コマンド バーの ToolStrip 項目を配置するには  
  
-   設定、<xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A>プロパティの値を<xref:System.Windows.Forms.ToolStripLayoutStyle>します。  
  
    ```vb  
    ToolStripDropDown1.LayoutStyle = _  
        System.Windows.Forms.ToolStripLayoutStyle.Flow  
    ```  
  
    ```csharp  
    toolStripDropDown1.LayoutStyle =   
        System.Windows.Forms.ToolStripLayoutStyle.Flow;  
    ```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.Control.Layout>
- <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>
- <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>
- <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>
- <xref:System.Windows.Forms.ToolStripItem.Placement%2A>
- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>
- [ToolStrip コントロールの概要](toolstrip-control-overview-windows-forms.md)
- [ToolStrip コントロールのアーキテクチャ](toolstrip-control-architecture.md)
- [ToolStrip テクノロジの概要](toolstrip-technology-summary.md)
