---
title: StatusBar コントロールの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
ms.openlocfilehash: bd58d4c70e3a3c88e57fe242957f669d1944fd71
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964431"
---
# <a name="statusbar-control-overview-windows-forms"></a>StatusBar コントロールの概要 (Windows フォーム)
> [!IMPORTANT]
> <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.StatusBarPanel> <xref:System.Windows.Forms.StatusBar>コントロール<xref:System.Windows.Forms.StatusStrip>と<xref:System.Windows.Forms.ToolStripStatusLabel>コントロールは、および<xref:System.Windows.Forms.StatusBarPanel>コントロールに対して、機能の置き換えと追加を行います。ただし、コントロールとコントロールは、下位互換性と将来の使用の両方のために保持されます。し.  
  
 Windows フォーム[StatusBar コントロール](statusbar-control-windows-forms.md)は、フォーム上で通常はウィンドウの下部に表示される領域として使用されます。この領域では、アプリケーションはさまざまな種類の状態情報を表示できます。 <xref:System.Windows.Forms.StatusBar>コントロールには、状態を示すためにテキストまたはアイコンを表示するステータスバーパネル、またはプロセスが動作していることを示すアニメーション内の一連のアイコンがあります。たとえば、Microsoft Word では、ドキュメントが保存されていることを示しています。  
  
## <a name="using-the-statusbar-control"></a>StatusBar コントロールの使用  
 Internet Explorer は、ハイパーリンク上でマウスがロールオーバーしたときに、ステータスバーを使用してページの URL を示します。Microsoft Word では、ページの場所、セクションの場所、および上書きやリビジョンの追跡などの編集モードに関する情報が提供されます。また、Visual Studio はステータスバーを使用して、ドッキングされたウィンドウをドッキングまたはフローティングとして操作する方法を示すなど、状況に応じた情報を提供します。  
  
 ステータスバーに1つのメッセージを表示するには、 <xref:System.Windows.Forms.StatusBar.ShowPanels%2A>プロパティを`false` ( <xref:System.Windows.Forms.StatusBar.Text%2A>既定値) に設定し、ステータスバーのプロパティをステータスバーに表示するテキストに設定します。 ステータスバーをパネルに分割して複数の種類の情報を表示するには、 <xref:System.Windows.Forms.StatusBar.ShowPanels%2A>プロパティを`true`に設定し<xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A> 、の<xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>メソッドを使用します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [方法: Windows フォーム StatusBar コントロールでクリックされたパネルを確認する](determine-which-panel-wf-statusbar-control-was-clicked.md)
