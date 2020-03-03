---
title: '方法: デザイナーを使って ToolBar ボタンのアイコンを定義する'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], adding icons to buttons
- examples [Windows Forms], toolbars
- images [Windows Forms], toolbar buttons
- buttons [Windows Forms], images
- icons [Windows Forms], toolbar buttons
- ToolBar control [Windows Forms], adding icons to buttons
ms.assetid: d848f38e-67f2-49d4-8e88-01c845c06c02
ms.openlocfilehash: 49e93f12bebbf409e6b3a06634556b9103c85f44
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666204"
---
# <a name="how-to-define-an-icon-for-a-toolbar-button-using-the-designer"></a>方法: デザイナーを使って ToolBar ボタンのアイコンを定義する

> [!NOTE]
> <xref:System.Windows.Forms.ToolStrip> コントロールは、<xref:System.Windows.Forms.ToolBar> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.ToolBar> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。

<xref:System.Windows.Forms.ToolBar>ボタンは、ユーザーが簡単に識別できるように、それらの中にアイコンを表示できます。 これは、 <xref:System.Windows.Forms.ImageList>コンポーネントにイメージを追加し、 <xref:System.Windows.Forms.ToolBar>コントロールに関連付けることによって実現されます。

次の手順では、 <xref:System.Windows.Forms.ToolBar>コントロールと<xref:System.Windows.Forms.ImageList>コンポーネントを含むフォームを含む**Windows アプリケーション**プロジェクトが必要です。 このようなプロジェクトの設定の詳細につい[ては、「方法:Windows フォームアプリケーションプロジェクト](/visualstudio/ide/step-1-create-a-windows-forms-application-project)を作成し[、次の操作を行います。Windows フォーム](how-to-add-controls-to-windows-forms.md)にコントロールを追加します。

### <a name="to-set-an-icon-for-a-toolbar-button-at-design-time"></a>デザイン時にツールバーボタンのアイコンを設定するには

1. <xref:System.Windows.Forms.ImageList>コンポーネントにイメージを追加します。 詳細については、「[方法 :デザイナー](how-to-add-or-remove-imagelist-images-with-the-designer.md)を使用して ImageList イメージを追加または削除します。

2. フォーム上のコントロールを選択します。 <xref:System.Windows.Forms.ToolBar>

3. **[プロパティ]** ウィンドウで、 <xref:System.Windows.Forms.ToolBar>コントロール<xref:System.Windows.Forms.ImageList>の<xref:System.Windows.Forms.ToolBar.ImageList%2A>プロパティをコンポーネントに設定します。

4. ![](./media/visual-studio-ellipsis-button.png)コントロールの<xref:System.Windows.Forms.ToolBar.Buttons%2A>プロパティをクリックして選択し、省略記号 ([Visual Studio のプロパティウィンドウ] の省略記号ボタン ([...]) をクリックして ToolBarButton Collection エディターを開きます。 <xref:System.Windows.Forms.ToolBar>

5. <xref:System.Windows.Forms.ToolBar>コントロールにボタンを追加するには、 **[追加]** ボタンを使用します。

6. **ToolBarButton Collection エディター**の右側にあるペインに表示される [ <xref:System.Windows.Forms.ToolBarButton.ImageIndex%2A> **プロパティ**] ウィンドウで、各ツールバーボタンのプロパティを、リスト内の値のいずれかに設定します。これは、 <xref:System.Windows.Forms.ImageList>コンポーネント。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ToolBar>
- [方法: ツールバーボタンのトリガーメニューイベント](how-to-trigger-menu-events-for-toolbar-buttons.md)
- [ToolBar コントロール](toolbar-control-windows-forms.md)
- [ImageList コンポーネント](imagelist-component-windows-forms.md)
