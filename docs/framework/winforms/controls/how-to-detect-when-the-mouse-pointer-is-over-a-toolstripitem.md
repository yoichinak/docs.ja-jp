---
title: '方法: マウス ポインターが ToolStripItem 上にあることを検出する'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], detecting mouse movement
- ToolStrip control [Windows Forms], detecting mouse movement
- ToolStripItem class [Windows Forms], detecting mouse movement
- mouse [Windows Forms], detecting movement on toolbars
ms.assetid: d38b5082-aba7-4f6c-841b-bd9714e307fd
ms.openlocfilehash: 09fd9f2f9b8cc44b6c04b829bf2854bea4aa8cf7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054264"
---
# <a name="how-to-detect-when-the-mouse-pointer-is-over-a-toolstripitem"></a>方法: マウス ポインターが ToolStripItem 上にあることを検出する
マウス ポインターが上を検出するために、次の手順を使用して、<xref:System.Windows.Forms.ToolStripItem>します。  
  
### <a name="to-detect-when-the-pointer-is-over-a-toolstripitem"></a>ポインターが toolstripitem を検出するには  
  
- 使用して、<xref:System.Windows.Forms.ToolStripItem.Selected%2A>をアイテムのプロパティ<xref:System.Windows.Forms.ToolStripItem.CanSelect%2A>は`true`します。  
  
     これによりを同期することから、<xref:System.Windows.Forms.ToolStripItem.MouseEnter>と<xref:System.Windows.Forms.ToolStripItem.MouseLeave>イベント。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripItem.Selected%2A>
- [ToolStrip コントロールの概要](toolstrip-control-overview-windows-forms.md)
