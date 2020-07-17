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
ms.openlocfilehash: 4d7a49633599aabc96153e4793e50c1a4d6d092d
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666214"
---
# <a name="how-to-add-buttons-to-a-toolbar-control-using-the-designer"></a>方法: デザイナーを使って ToolBar コントロールにボタンを追加する

> [!NOTE]
> <xref:System.Windows.Forms.ToolStrip> コントロールは、<xref:System.Windows.Forms.ToolBar> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.ToolBar> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。

<xref:System.Windows.Forms.ToolBar>コントロールの不可欠な部分は、コントロールに追加するボタンです。 これらは、メニューコマンドに簡単にアクセスできるようにするために使用できます。また、アプリケーションのユーザーインターフェイスの別の領域に配置して、メニュー構造では使用できないコマンドをユーザーに公開することもできます。

次の手順では、 <xref:System.Windows.Forms.ToolBar>コントロールを含むフォームを含む**Windows アプリケーション**プロジェクトが必要です。 このようなプロジェクトの設定の詳細につい[ては、「方法:Windows フォームアプリケーションプロジェクト](/visualstudio/ide/step-1-create-a-windows-forms-application-project)を作成し[、次の操作を行います。Windows フォーム](how-to-add-controls-to-windows-forms.md)にコントロールを追加します。

### <a name="to-add-buttons-at-design-time"></a>デザイン時にボタンを追加するには

1. <xref:System.Windows.Forms.ToolBar> コントロールを選択します。

2. **[プロパティ]** ウィンドウ<xref:System.Windows.Forms.ToolBar.Buttons%2A>で、プロパティをクリックして選択し、**省略記号**(![[Visual Studio のプロパティウィンドウ] の省略記号ボタン ([...]) をクリックして ToolBarButton を開きます。](./media/visual-studio-ellipsis-button.png) **コレクションエディター**。

3. コントロール<xref:System.Windows.Forms.ToolBar>のボタンを追加および削除するには、 **[追加]** ボタンと **[削除]** ボタンを使用します。

4. エディターの右側のペインに表示される **[プロパティ]** ウィンドウで、個々のボタンのプロパティを構成します。 次の表は、考慮する必要があるいくつかの重要なプロパティを示しています。

    |プロパティ|説明|
    |--------------|-----------------|
    |<xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A>|ドロップダウンツールバーボタンに表示するメニューを設定します。 ツールバーボタンの<xref:System.Windows.Forms.ToolBarButton.Style%2A>プロパティをに<xref:System.Windows.Forms.ToolBarButtonStyle.DropDownButton>設定する必要があります。 このプロパティは、 <xref:System.Windows.Forms.ContextMenu>クラスのインスタンスを参照として受け取ります。|
    |<xref:System.Windows.Forms.ToolBarButton.PartialPush%2A>|トグルスタイルのツールバーボタンを部分的にプッシュするかどうかを設定します。 ツールバーボタンの<xref:System.Windows.Forms.ToolBarButton.Style%2A>プロパティをに<xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton>設定する必要があります。|
    |<xref:System.Windows.Forms.ToolBarButton.Pushed%2A>|トグルスタイルのツールバーボタンが現在プッシュ状態になっているかどうかを設定します。 ツールバーボタンの<xref:System.Windows.Forms.ToolBarButton.Style%2A>プロパティは、または<xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton> <xref:System.Windows.Forms.ToolBarButtonStyle.PushButton>に設定する必要があります。|
    |<xref:System.Windows.Forms.ToolBarButton.Style%2A>|ツールバーボタンのスタイルを設定します。 <xref:System.Windows.Forms.ToolBarButtonStyle>列挙体の値のいずれかである必要があります。|
    |<xref:System.Windows.Forms.ToolBarButton.Text%2A>|ボタンによって表示されるテキスト文字列。|
    |<xref:System.Windows.Forms.ToolBarButton.ToolTipText%2A>|ボタンのツールヒントとして表示されるテキスト。|

5. **[OK]** をクリックしてダイアログボックスを閉じ、指定したパネルを作成します。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ToolBar>
- [方法: ツールバーボタンのアイコンを定義する](how-to-define-an-icon-for-a-toolbar-button.md)
- [方法: ツールバーボタンのトリガーメニューイベント](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [ToolBar コントロールの概要](toolbar-control-overview-windows-forms.md)
- [ToolBar コントロール](toolbar-control-windows-forms.md)
