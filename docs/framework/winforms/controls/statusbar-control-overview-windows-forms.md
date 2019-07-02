---
title: StatusBar コントロールの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- StatusBar
helpviewer_keywords:
- StatusBar control [Windows Forms], about StatusBar control
- status bars
ms.assetid: b7b9852c-633d-4416-bb2e-94852b989c6c
ms.openlocfilehash: 4e1816ef221641f5ad54fb429442ed43289b592a
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505428"
---
# <a name="statusbar-control-overview-windows-forms"></a>StatusBar コントロールの概要 (Windows フォーム)
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip>と<xref:System.Windows.Forms.ToolStripStatusLabel>コントロールの置換し、する機能を追加、<xref:System.Windows.Forms.StatusBar>と<xref:System.Windows.Forms.StatusBarPanel>を制御しますただし、、<xref:System.Windows.Forms.StatusBar>と<xref:System.Windows.Forms.StatusBarPanel>場合、下位互換性と将来の使用の両方のコントロールが保持されますします。選択します。  
  
 Windows フォーム[StatusBar コントロール](statusbar-control-windows-forms.md)はフォームの領域で、通常、アプリケーションがさまざまな種類のステータス情報を表示できるウィンドウの下部に表示として使用します。 <xref:System.Windows.Forms.StatusBar> コントロールがテキストまたは状態、または一連のプロセスが動作してを示すアニメーションのアイコンを示すアイコンを表示してステータス バー パネルを持つことができます。たとえば、Microsoft Word があることを示すドキュメント保存されます。  
  
## <a name="using-the-statusbar-control"></a>ステータス バー コントロールを使用します。  
 Internet Explorer は、マウスを取り消さない限り、ハイパーリンクときに、ページの URL を示すためにステータス バーを使用します。Microsoft Word での情報がページの場所、セクションの場所、および上書きや変更の追跡などの編集モードVisual Studio を使用してステータス バーをドッキングまたはフローティング、ドッキング可能なウィンドウを操作する方法を示すなどの状況に応じた情報します。  
  
 ステータス バーに設定して、1 つのメッセージを表示することができます、<xref:System.Windows.Forms.StatusBar.ShowPanels%2A>プロパティを`false`(既定値) と設定、<xref:System.Windows.Forms.StatusBar.Text%2A>ステータス バーに表示するテキストをステータス バーのプロパティ。 ステータス バーを設定して、情報の 1 つ以上の種類を表示するパネルに分割することができます、<xref:System.Windows.Forms.StatusBar.ShowPanels%2A>プロパティを`true`を使用して、<xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection.Add%2A>メソッドの<xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [方法: Windows フォームの StatusBar コントロール パネルのクリックを確認します。](determine-which-panel-wf-statusbar-control-was-clicked.md)
