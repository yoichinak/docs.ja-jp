---
title: 'チュートリアル: 標準メニュー項目をフォームに用意する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- menu items [Windows Forms], standard
- toolbars [Windows Forms], walkthroughs
- StatusStrip control [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: dac37d98-589e-4d6d-9673-6437e8943122
ms.openlocfilehash: ebfacadfee3ea069359a72ea0402751e9e6280d7
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211505"
---
# <a name="walkthrough-providing-standard-menu-items-to-a-form"></a>チュートリアル: 標準メニュー項目をフォームに用意する

フォームの標準のメニューを <xref:System.Windows.Forms.MenuStrip> コントロールに提供できます。

このチュートリアルを使用する方法について説明する<xref:System.Windows.Forms.MenuStrip>標準メニューを作成するコントロール。 フォームは、ユーザーがメニュー項目を選択したときにも応答します。 このチュートリアルで、次のタスクを示します。

- Windows フォーム プロジェクトを作成します。

- 標準メニューを作成します。

- 作成、<xref:System.Windows.Forms.StatusStrip>コントロール。

- メニュー項目の選択を処理します。

標準のメニューにメニュー項目の選択内容を表示するフォームが完了したら、<xref:System.Windows.Forms.StatusStrip>コントロール。

このトピックのコードを単一のリストとしてコピーするには、「[方法:フォームに標準メニュー項目を提供](how-to-provide-standard-menu-items-to-a-form.md)します。

## <a name="prerequisites"></a>必須コンポーネント

Visual Studio でこのチュートリアルを完了する必要があります。

## <a name="create-the-project"></a>プロジェクトの作成

1. Visual Studio と呼ばれる Windows アプリケーション プロジェクトを作成**StandardMenuForm** (**ファイル** > **新規** > **プロジェクト**  >  **Visual C#** または**Visual Basic** > **クラシック デスクトップ** >  **Windows フォーム アプリケーション**)。

2. Windows フォーム デザイナーでフォームを選択します。

## <a name="create-a-standard-menu"></a>標準のメニューを作成します。

Windows フォーム デザイナーで自動的に設定できる、<xref:System.Windows.Forms.MenuStrip>標準メニュー項目を制御します。

1. **ツールボックス**、ドラッグ、<xref:System.Windows.Forms.MenuStrip>コントロールをフォームにします。

2. をクリックして、<xref:System.Windows.Forms.MenuStrip>コントロールのスマート タグ グリフ (![スマート タグ グリフ](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) を選択および**標準項目の挿入**します。

     <xref:System.Windows.Forms.MenuStrip>標準メニュー項目コントロールに設定します。

3. をクリックして、**ファイル**メニュー項目をその既定のメニュー項目と対応するアイコンを参照してください。

## <a name="create-a-statusstrip-control"></a>StatusStrip コントロールを作成します。

使用して、 <xref:System.Windows.Forms.StatusStrip> Windows フォーム アプリケーションの状態を表示するコントロール。 現在の例では、ユーザーが選択したメニュー項目の表示、<xref:System.Windows.Forms.StatusStrip>コントロール。

1. **ツールボックス**、ドラッグ、<xref:System.Windows.Forms.StatusStrip>コントロールをフォームにします。

     <xref:System.Windows.Forms.StatusStrip>コントロールが自動的にフォームの下部にドッキングします。

2. をクリックして、<xref:System.Windows.Forms.StatusStrip>コントロールのドロップダウン ボタンと選択**StatusLabel**を追加する、<xref:System.Windows.Forms.ToolStripStatusLabel>への制御、<xref:System.Windows.Forms.StatusStrip>コントロール。

## <a name="handle-item-selection"></a>項目の選択を処理します。

処理、<xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>イベント、ユーザーがメニュー項目を選択するときに応答します。

1. をクリックして、**ファイル**メニュー項目の作成で作成した標準メニュー セクション。

2. **[プロパティ]** ウィンドウで、**[イベント]** をクリックします。

3. ダブルクリックして、<xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>イベント。

     Windows フォーム デザイナーのイベント ハンドラーの生成、<xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked>イベント。

4. イベント ハンドラーに次のコードを挿入します。

     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#3)]

5. 挿入、`UpdateStatus`ユーティリティ メソッドの定義をフォームに設定します。

     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#2)]

## <a name="checkpoint--test-your-form"></a>チェックポイントのフォームをテストします。

1. キーを押して**F5**をコンパイルして、フォームを実行します。

2. をクリックして、**ファイル**メニュー項目、メニューを開きます。

3. **ファイル**メニューで、これを選択する項目のいずれかをクリックします。

     <xref:System.Windows.Forms.StatusStrip>コントロールは、選択した項目を表示します。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、標準メニューを持つフォームを作成しました。 使用することができます、<xref:System.Windows.Forms.ToolStrip>の他のさまざまな目的のコントロール ファミリ。

- ショートカット メニューを使用してコントロールを作成<xref:System.Windows.Forms.ContextMenuStrip>です。 詳細については、次を参照してください。 [ContextMenu コンポーネントの概要](contextmenu-component-overview-windows-forms.md)します。

- ドッキングのマルチ ドキュメント インターフェイス (MDI) フォームを作成する<xref:System.Windows.Forms.ToolStrip>コントロール。 詳細については、「[チュートリアル:メニューのマージと ToolStrip コントロールを MDI フォームを作成する](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md)します。

- 与える、<xref:System.Windows.Forms.ToolStrip>プロフェッショナルな外観を制御します。 詳細については、「[方法 :アプリケーションの ToolStrip レンダラーを設定](how-to-set-the-toolstrip-renderer-for-an-application.md)します。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [MenuStrip コントロール](menustrip-control-windows-forms.md)
