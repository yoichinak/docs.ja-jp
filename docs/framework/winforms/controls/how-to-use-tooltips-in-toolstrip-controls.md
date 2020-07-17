---
title: '方法: ToolStrip コントロールにツールヒントを使用する'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], adding tooltips
- toolbars [Windows Forms], adding tooltips
- tooltips [Windows Forms], adding
ms.assetid: c5d86024-a7c5-44ee-8b3f-2daf53d80d3e
ms.openlocfilehash: 3f383b6cccba7825637ea65a0e13280b91b406c9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939734"
---
# <a name="how-to-use-tooltips-in-toolstrip-controls"></a>方法: ToolStrip コントロールにツールヒントを使用する
コントロールの<xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>プロパティを<xref:System.Windows.Forms.ToolTip> <xref:System.Windows.Forms.ToolStrip> に`true`設定することによって、必要なコントロールのを表示できます。  
  
### <a name="to-display-a-tooltip"></a>ツールヒントを表示するには  
  
- `true`コントロールの<xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>プロパティをに設定します。  
  
     の<xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType>既定値は`true`で、と<xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType>の<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType>既定値は`false`です。  
  
### <a name="to-use-the-tooltiptext-property-for-the-tooltip-text-of-a-toolstripbutton"></a>ToolStripButton のツールヒントテキストに ToolTipText プロパティを使用するには  
  
1. `true`ボタンの<xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>プロパティをに設定します。  
  
2. `false`ボタンの<xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType>プロパティをに設定します。  
  
     `true` <xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolStripDropDownButton>既定で<xref:System.Windows.Forms.ToolStripSplitButton>は、、、およびに対してプロパティが使用されます。`AutoToolTip`  
  
     は<xref:System.Windows.Forms.ToolStripButton> 、既定`Text`ではその<xref:System.Windows.Forms.ToolTip>プロパティをテキストに使用します。 でカスタムテキストを表示するには、 <xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolTip>次の手順に従います。  
  
> [!NOTE]
> をまたは<xref:System.Windows.Forms.ToolStripItemDisplayStyle> <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None> に<xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>設定しても、ボタンにテキストは表示されませんが、ツールヒントは表示されます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>
- <xref:System.Windows.Forms.ToolStripButton>
- <xref:System.Windows.Forms.ToolStripDropDownButton>
- <xref:System.Windows.Forms.ToolStripSplitButton>
- [ToolStrip コントロールの概要](toolstrip-control-overview-windows-forms.md)
