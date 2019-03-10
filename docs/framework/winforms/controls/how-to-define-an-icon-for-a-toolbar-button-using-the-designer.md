---
title: '方法: デザイナーを使用してツール バー ボタンのアイコンを定義します。'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], adding icons to buttons
- examples [Windows Forms], toolbars
- images [Windows Forms], toolbar buttons
- buttons [Windows Forms], images
- icons [Windows Forms], toolbar buttons
- ToolBar control [Windows Forms], adding icons to buttons
ms.assetid: d848f38e-67f2-49d4-8e88-01c845c06c02
ms.openlocfilehash: 2099738d5b666aa305d678c962c0b203d3ab67b2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57717740"
---
# <a name="how-to-define-an-icon-for-a-toolbar-button-using-the-designer"></a>方法: デザイナーを使用してツール バー ボタンのアイコンを定義します。
> [!NOTE]
>  
  <xref:System.Windows.Forms.ToolStrip> コントロールは、<xref:System.Windows.Forms.ToolBar> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.ToolBar> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。  
  
 <xref:System.Windows.Forms.ToolBar> ボタンは、ユーザーがそれらに含まれるを簡単に識別のアイコンを表示できません。 これは画像を追加することによって実現、<xref:System.Windows.Forms.ImageList>コンポーネントと関連付けること、<xref:System.Windows.Forms.ToolBar>コントロール。  
  
 次の手順が必要です、 **Windows アプリケーション**プロジェクトが含まれているフォームを<xref:System.Windows.Forms.ToolBar>コントロールと<xref:System.Windows.Forms.ImageList>コンポーネント。 このようなプロジェクトの設定の詳細については、次を参照してください。[方法。Windows フォーム アプリケーション プロジェクトを作成](/visualstudio/ide/step-1-create-a-windows-forms-application-project)と[方法。Windows フォームにコントロールを追加](how-to-add-controls-to-windows-forms.md)します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="to-set-an-icon-for-a-toolbar-button-at-design-time"></a>デザイン時にツール バー ボタンのアイコンを設定するには  
  
1.  イメージを追加、<xref:System.Windows.Forms.ImageList>コンポーネント。 詳細については、「[方法 :デザイナーを使って ImageList イメージを追加または](how-to-add-or-remove-imagelist-images-with-the-designer.md)します。  
  
2.  選択、<xref:System.Windows.Forms.ToolBar>フォーム上のコントロール。  
  
3.  **プロパティ**ウィンドウで、設定、<xref:System.Windows.Forms.ToolBar>コントロールの<xref:System.Windows.Forms.ToolBar.ImageList%2A>プロパティを<xref:System.Windows.Forms.ImageList>コンポーネント。  
  
4.  をクリックして、<xref:System.Windows.Forms.ToolBar>コントロールの<xref:System.Windows.Forms.ToolBar.Buttons%2A>プロパティを選択し、省略記号ボタンをクリックします (![VisualStudioEllipsesButton スクリーン ショット](../media/vbellipsesbutton.png "vbEllipsesButton")) ボタンを**ツールバー ・ ボタン コレクション エディター**します。  
  
5.  使用して、**追加**にボタンを追加するボタン、<xref:System.Windows.Forms.ToolBar>コントロール。  
  
6.  **プロパティ**ウィンドウの右側にあるペインに表示される、**ツールバー ・ ボタン コレクション エディター**、設定、<xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A>一覧で、値の 1 つは、各ツール バー ボタンのプロパティを追加したイメージの描画、<xref:System.Windows.Forms.ImageList>コンポーネント。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.ToolBar>
- [方法: ツール バー ボタンのメニュー イベントのトリガー](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [ToolBar コントロール](toolbar-control-windows-forms.md)
- [ImageList コンポーネント](imagelist-component-windows-forms.md)
