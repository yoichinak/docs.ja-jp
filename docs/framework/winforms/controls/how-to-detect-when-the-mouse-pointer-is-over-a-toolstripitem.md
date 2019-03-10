---
title: '方法: マウス ポインターが Toolstripitem を検出します。'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], detecting mouse movement
- ToolStrip control [Windows Forms], detecting mouse movement
- ToolStripItem class [Windows Forms], detecting mouse movement
- mouse [Windows Forms], detecting movement on toolbars
ms.assetid: d38b5082-aba7-4f6c-841b-bd9714e307fd
ms.openlocfilehash: 39173490c31711cca9f26f5f0cb2ab493546dda3
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720814"
---
# <a name="how-to-detect-when-the-mouse-pointer-is-over-a-toolstripitem"></a>方法: マウス ポインターが Toolstripitem を検出します。
マウス ポインターが上を検出するために、次の手順を使用して、<xref:System.Windows.Forms.ToolStripItem>します。  
  
### <a name="to-detect-when-the-pointer-is-over-a-toolstripitem"></a>ポインターが toolstripitem を検出するには  
  
-   使用して、<xref:System.Windows.Forms.ToolStripItem.Selected%2A>をアイテムのプロパティ<xref:System.Windows.Forms.ToolStripItem.CanSelect%2A>は`true`します。  
  
     これによりを同期することから、<xref:System.Windows.Forms.ToolStripItem.MouseEnter>と<xref:System.Windows.Forms.ToolStripItem.MouseLeave>イベント。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripItem.Selected%2A>
- [ToolStrip コントロールの概要](toolstrip-control-overview-windows-forms.md)
