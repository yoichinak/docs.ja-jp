---
title: '方法: デザイナーを使って ToolBar コントロールにボタンを追加する'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding separators
- examples [Windows Forms], toolbars
- ToolBar control [Windows Forms], adding drop-down menus
ms.assetid: d9ce3040-3e21-4e2d-80ae-b430982b2db8
ms.openlocfilehash: 133190426229a10ed6f637293326c229e808bfdb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59084025"
---
# <a name="how-to-add-buttons-to-a-toolbar-control-using-the-designer"></a>方法: デザイナーを使って ToolBar コントロールにボタンを追加する
> [!NOTE]
>  
  <xref:System.Windows.Forms.ToolStrip> コントロールは、<xref:System.Windows.Forms.ToolBar> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.ToolBar> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。  
  
 不可欠な部分、<xref:System.Windows.Forms.ToolBar>コントロールは、ボタンを追加します。 メニュー コマンドに簡単にアクセスを提供するこれらを使用できますか、または、メニュー構造では使用できないユーザーにコマンドを公開するアプリケーションのユーザー インターフェイスの別の領域に配置することができます。  
  
 次の手順が必要です、 **Windows アプリケーション**プロジェクトが含まれているフォームを<xref:System.Windows.Forms.ToolBar>コントロール。 このようなプロジェクトの設定の詳細については、次を参照してください。[方法。Windows フォーム アプリケーション プロジェクトを作成](/visualstudio/ide/step-1-create-a-windows-forms-application-project)と[方法。Windows フォームにコントロールを追加](how-to-add-controls-to-windows-forms.md)します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="to-add-buttons-at-design-time"></a>デザイン時にボタンを追加するには  
  
1.  <xref:System.Windows.Forms.ToolBar> コントロールを選択します。  
  
2.  **プロパティ**ウィンドウで、をクリックして、<xref:System.Windows.Forms.ToolBar.Buttons%2A>プロパティを選択し、クリックして、**省略記号**(![VisualStudioEllipsesButton スクリーン ショット](../media/vbellipsesbutton.png "vbEllipsesButton")) ボタンをクリックする、**ツールバー ・ ボタン コレクション エディター**します。  
  
3.  使用して、**追加**と**削除**ボタンの追加し、削除 ボタンから、<xref:System.Windows.Forms.ToolBar>コントロール。  
  
4.  各ボタンのプロパティを構成、**プロパティ**エディターの右側にあるペインに表示されるウィンドウ。 次の表では、考慮すべき重要なプロパティを示します。  
  
    |プロパティ|説明|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A>|ドロップダウン ツール バー ボタンに表示されるメニューを設定します。 ツール バー ボタンの<xref:System.Windows.Forms.ToolBarButton.Style%2A>にプロパティを設定する必要があります<xref:System.Windows.Forms.ToolBarButtonStyle.DropDownButton>します。 このプロパティは、のインスタンスを受け取り、<xref:System.Windows.Forms.ContextMenu>クラスとして参照します。|  
    |<xref:System.Windows.Forms.ToolBarButton.PartialPush%2A>|トグル スタイルのツール バー ボタンが部分的に押されているかどうかを設定します。 ツール バー ボタンの<xref:System.Windows.Forms.ToolBarButton.Style%2A>にプロパティを設定する必要があります<xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton>します。|  
    |<xref:System.Windows.Forms.ToolBarButton.Pushed%2A>|トグル スタイルのツール バー ボタンが押された状態では現在あるかどうかを設定します。 ツール バー ボタンの<xref:System.Windows.Forms.ToolBarButton.Style%2A>にプロパティを設定する必要があります<xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton>または<xref:System.Windows.Forms.ToolBarButtonStyle.PushButton>します。|  
    |<xref:System.Windows.Forms.ToolBarButton.Style%2A>|ツール バー ボタンのスタイルを設定します。 内の値のいずれかを指定する必要があります、<xref:System.Windows.Forms.ToolBarButtonStyle>列挙体。|  
    |<xref:System.Windows.Forms.ToolBarButton.Text%2A>|ボタンによって表示される文字列。|  
    |<xref:System.Windows.Forms.ToolBarButton.ToolTipText%2A>|ボタンのツールヒントとして表示されるテキスト。|  
  
5.  をクリックして**OK**をダイアログ ボックスを閉じて、指定したパネルを作成します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ToolBar>
- [方法: ツール バー ボタンのアイコンを定義する](how-to-define-an-icon-for-a-toolbar-button.md)
- [方法: ツール バー ボタンのメニュー イベントをトリガーする](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [ToolBar コントロールの概要](toolbar-control-overview-windows-forms.md)
- [ToolBar コントロール](toolbar-control-windows-forms.md)
