---
title: '方法: フォームの端に合わせてコントロールを配置する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dock property [Windows Forms], aligning controls (using code)
- forms [Windows Forms], aligning controls
- controls [Windows Forms], aligning on forms
- custom controls [Windows Forms], docking using code
ms.assetid: 5994cb59-242b-4e75-bd0e-62879c34d702
ms.openlocfilehash: beb8881dbd2aedaefe66510c2942ce6c082b9729
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59329974"
---
# <a name="how-to-align-a-control-to-the-edges-of-forms"></a>方法: フォームの端に合わせてコントロールを配置する
<xref:System.Windows.Forms.Control.Dock%2A> プロパティを設定することにより、フォームの端に合わせてコントロールを配置することができます。 このプロパティは、フォーム内のコントロールの場所を指定します。 <xref:System.Windows.Forms.Control.Dock%2A> プロパティには次の値のいずれかを設定できます。  
  
|設定|コントロールへの影響|  
|-------------|----------------------------|  
|<xref:System.Windows.Forms.DockStyle.Bottom>|フォームの下部にドッキングします。|  
|<xref:System.Windows.Forms.DockStyle.Fill>|フォームの残りの全スペースを埋めます。|  
|<xref:System.Windows.Forms.DockStyle.Left>|フォームの左側にドッキングします。|  
|<xref:System.Windows.Forms.DockStyle.None>|どこにもドッキングせず、その <xref:System.Windows.Forms.Control.Location%2A> プロパティで指定された位置に表示されます。|  
|<xref:System.Windows.Forms.DockStyle.Right>|フォームの右側にドッキングします。|  
|<xref:System.Windows.Forms.DockStyle.Top>|フォームの上部にドッキングします。|  
  
 Visual Studio では、この機能のデザイン時サポートがあります。  
  
### <a name="to-set-the-dock-property-for-your-control-at-run-time"></a>実行時にコントロールの Dock プロパティを設定するには  
  
1. コードで <xref:System.Windows.Forms.Control.Dock%2A> プロパティを適切な値に設定します。  
  
    ```vb  
    ' To set the Dock property internally.  
    Me.Dock = DockStyle.Top  
    ' To set the Dock property from another object.  
    UserControl1.Dock = DockStyle.Top  
    ```  
  
    ```csharp  
    // To set the Dock property internally.  
    this.Dock = DockStyle.Top;  
    // To set the Dock property from another object.  
    UserControl1.Dock = DockStyle.Top;  
    ```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>
- [.NET Framework を使用したカスタム Windows フォーム コントロールの開発](developing-custom-windows-forms-controls.md)
- [方法: FlowLayoutPanel コントロールで子コントロールを固定およびドッキングする](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [方法: TableLayoutPanel コントロールで子コントロールを固定およびドッキングする](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [AutoSize プロパティの概要](autosize-property-overview.md)
