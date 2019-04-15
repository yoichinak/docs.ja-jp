---
title: '方法: ContextMenuStrip のオープン イベントを処理する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ContextMenuStrip control [Windows Forms]
- context menus [Windows Forms], event handling
- ToolStrip control [Windows Forms]
- event handling [Windows Forms], context menus
- shortcut menus [Windows Forms], event handling
ms.assetid: b661b3dd-7815-4cc2-a1aa-a9a391ab3427
ms.openlocfilehash: 3001480959ef90cb31048cbcf70aeff1632979fb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170718"
---
# <a name="how-to-handle-the-contextmenustrip-opening-event"></a>方法: ContextMenuStrip のオープン イベントを処理する
動作をカスタマイズすることができます、<xref:System.Windows.Forms.ContextMenuStrip>コントロールを処理することによって、<xref:System.Windows.Forms.ToolStripDropDown.Opening>イベント。  
  
## <a name="example"></a>例  
 次のコード例は、処理する方法を示します、<xref:System.Windows.Forms.ToolStripDropDown.Opening>イベント。 イベント ハンドラーを動的に項目を追加、<xref:System.Windows.Forms.ContextMenuStrip>コントロール。 完全なコード例では、次を参照してください。[方法。ToolStrip の項目を動的に追加](how-to-add-toolstrip-items-dynamically.md)します。  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#42)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#42)]  
  
 設定、<xref:System.ComponentModel.CancelEventArgs.Cancel%2A?displayProperty=nameWithType>プロパティを`true`メニューを開かないようにします。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.ComponentModel.CancelEventArgs.Cancel%2A>
- <xref:System.Windows.Forms.ToolStripDropDown>
- [ToolStrip コントロール](toolstrip-control-windows-forms.md)
