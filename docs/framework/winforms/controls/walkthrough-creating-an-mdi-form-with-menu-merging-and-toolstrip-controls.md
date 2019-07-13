---
title: 'チュートリアル: メニューのマージと ToolStrip コントロールのある MDI フォームを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripPanel control [Windows Forms]
- MDI [Windows Forms], creating forms
- multiple document interface forms
- MDI forms
- ToolStrip control [Windows Forms]
- MDI forms [Windows Forms], creating
- MDI forms [Windows Forms], walkthroughs
ms.assetid: fbab4221-74af-42d0-bbf4-3c97f7b2e544
ms.openlocfilehash: 5853760231cbece27805923c009d83e16c9b0a5e
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211556"
---
# <a name="walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a>チュートリアル: メニューのマージと ToolStrip コントロールのある MDI フォームを作成する

<xref:System.Windows.Forms?displayProperty=nameWithType> 名前空間は、マルチ ドキュメント インターフェイス (MDI) アプリケーションをサポートし、<xref:System.Windows.Forms.MenuStrip> コントロールはメニューの結合をサポートします。 MDI フォームは、<xref:System.Windows.Forms.ToolStrip> コントロールもサポートします。

このチュートリアルを使用する方法について説明<xref:System.Windows.Forms.ToolStripPanel>を MDI フォームでコントロールできます。 フォームは、子メニューをマージするメニューもサポートしています。 このチュートリアルで、次のタスクを示します。

- Windows フォーム プロジェクトを作成します。

- フォームのメイン メニューを作成します。 メニューの実際の名前は異なります。

- 追加、<xref:System.Windows.Forms.ToolStripPanel>への制御、**ツールボックス**します。

- 子フォームを作成します。

- 配置<xref:System.Windows.Forms.ToolStripPanel>z オーダーでコントロールできます。

メニューのマージと移動をサポートする MDI フォームが完成したら、<xref:System.Windows.Forms.ToolStrip>コントロール。

このトピックのコードを単一のリストとしてコピーするには、「[方法:メニューのマージと ToolStrip コントロールを MDI フォームを作成](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md)です。

## <a name="prerequisites"></a>必須コンポーネント

Visual Studio でこのチュートリアルを完了する必要があります。

## <a name="create-the-project"></a>プロジェクトの作成

1. Visual Studio と呼ばれる Windows アプリケーション プロジェクトを作成**mdi フォーム**(**ファイル** > **新規** > **プロジェクト**  >  **Visual C#** または**Visual Basic** > **クラシック デスクトップ** >  **Windows フォーム アプリケーション**)。

2. Windows フォーム デザイナーでフォームを選択します。

3. [プロパティ] ウィンドウでの値を設定、<xref:System.Windows.Forms.Form.IsMdiContainer%2A>に`true`します。

## <a name="create-the-main-menu"></a>メイン メニューを作成します。

親 MDI フォームには、メイン メニューが含まれています。 メイン メニューがという名前の項目の 1 つの menu**ウィンドウ**します。 **ウィンドウ**メニュー項目を子フォームを作成することができます。 子フォームのメニュー項目は、メイン メニューにマージされます。

1. **ツールボックス**、ドラッグ、<xref:System.Windows.Forms.MenuStrip>コントロールをフォームにします。

2. 追加、<xref:System.Windows.Forms.ToolStripMenuItem>を<xref:System.Windows.Forms.MenuStrip>を制御し、名前を**ウィンドウ**します。

3. <xref:System.Windows.Forms.MenuStrip> コントロールを選択します。

4. [プロパティ] ウィンドウでの値を設定、<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>プロパティを`ToolStripMenuItem1`します。

5. 追加するサブ項目、**ウィンドウ**メニュー項目と、名前、サブ項目**新規**します。

6. [プロパティ] ウィンドウで次のようにクリックします。**イベント**します。

7. ダブルクリックして、<xref:System.Windows.Forms.ToolStripItem.Click>イベント。

     Windows フォーム デザイナーのイベント ハンドラーの生成、<xref:System.Windows.Forms.ToolStripItem.Click>イベント。

8. イベント ハンドラーに次のコードを挿入します。

     [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#2)]

## <a name="add-the-toolstrippanel-control-to-the-toolbox"></a>ToolStripPanel コントロールをツールボックスに追加します。

使用すると<xref:System.Windows.Forms.MenuStrip>コントロールを MDI フォームが必要で、<xref:System.Windows.Forms.ToolStripPanel>コントロール。 追加する必要があります、<xref:System.Windows.Forms.ToolStripPanel>への制御、**ツールボックス**Windows フォーム デザイナーで、MDI フォームを作成します。

1. 開く、**ツールボックス**、 をクリックし、**すべての Windows フォーム** タブを使用できる Windows フォーム コントロールを表示します。

2. ショートカット メニューを右クリックして**アイテムの選択**します。

3. **ツールボックス アイテムの選択** ダイアログ ボックスで、下にスクロール、**名前**列が表示されるまで**ToolStripPanel**します。

4. チェック ボックスをオン**ToolStripPanel**、 をクリックし、 **OK**。

     <xref:System.Windows.Forms.ToolStripPanel>コントロールに表示され、**ツールボックス**します。

## <a name="create-a-child-form"></a>子フォームを作成します。

この手順では、独自に持つ別の子フォーム クラスを定義します<xref:System.Windows.Forms.MenuStrip>コントロール。 このフォームのメニュー項目は、親フォームのマージされます。

1. という名前の新しいフォームを追加`ChildForm`をプロジェクトにします。

     詳細については、「[方法 :Windows フォーム プロジェクトを追加する](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/y2xxdce3(v=vs.100))します。

2. **ツールボックス**、ドラッグ、<xref:System.Windows.Forms.MenuStrip>子フォームにコントロール。

3. をクリックして、<xref:System.Windows.Forms.MenuStrip>コントロールのスマート タグ グリフ (![スマート タグ グリフ](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph"))、し、**アイテムの編集**します。

4. **Items コレクション エディター**  ダイアログ ボックスで、新しい追加<xref:System.Windows.Forms.ToolStripMenuItem>という名前の**ChildMenuItem**子メニューにします。

     詳細については、次を参照してください。 [ToolStrip Items コレクション エディター](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233643(v=vs.100))します。

## <a name="test-the-form"></a>フォームをテストします。

1. キーを押して**F5**をコンパイルして、フォームを実行します。

2. をクリックして、**ウィンドウ**メニューを開き、クリックしてメニュー項目**新規**します。

     新しい子フォームは、フォームの MDI クライアント領域に作成されます。 子フォームのメニューは、メイン メニューにマージされます。

3. 子フォームを閉じます。

     子フォームのメニューは、メイン メニューから削除されます。

4. クリックして**新規**何回か。

     子フォームが自動的に下に表示されます、**ウィンドウ**メニュー項目のため、<xref:System.Windows.Forms.MenuStrip>コントロールの<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>プロパティが割り当てられます。

## <a name="add-toolstrip-support"></a>ToolStrip のサポートを追加します。

この手順で、4 つを追加、 <xref:System.Windows.Forms.ToolStrip> MDI 親フォームのコントロール。 各<xref:System.Windows.Forms.ToolStrip>内でコントロールを追加、<xref:System.Windows.Forms.ToolStripPanel>コントロールで、フォームの端にドッキングされます。

1. **ツールボックス**、ドラッグ、<xref:System.Windows.Forms.ToolStripPanel>コントロールをフォームにします。

2. <xref:System.Windows.Forms.ToolStripPanel>コントロールが選択されている場合、ダブルクリックして、<xref:System.Windows.Forms.ToolStrip>を制御、**ツールボックス**します。

     A<xref:System.Windows.Forms.ToolStrip>でコントロールを作成、<xref:System.Windows.Forms.ToolStripPanel>コントロール。

3. <xref:System.Windows.Forms.ToolStripPanel> コントロールを選択します。

4. [プロパティ] ウィンドウでのコントロールの値を変更<xref:System.Windows.Forms.Control.Dock%2A>プロパティを<xref:System.Windows.Forms.DockStyle.Left>します。

     <xref:System.Windows.Forms.ToolStripPanel>メイン メニューの下に、フォームの左側にドッキングを制御します。 MDI クライアント領域のサイズに合わせて、<xref:System.Windows.Forms.ToolStripPanel>コントロール。

5. 手順 1. ~ 4. を繰り返します。

     新しいドッキング<xref:System.Windows.Forms.ToolStripPanel>フォームの上部をコントロールします。

     <xref:System.Windows.Forms.ToolStripPanel>コントロールがメインのメニューの下には、最初の右側にドッキングされている<xref:System.Windows.Forms.ToolStripPanel>コントロール。 この手順は、正しく配置の z オーダーの重要性を示しています。<xref:System.Windows.Forms.ToolStripPanel>コントロール。

6. さらに 2 つの手順 1. ~ 4. を繰り返します<xref:System.Windows.Forms.ToolStripPanel>コントロール。

     新しいドッキング<xref:System.Windows.Forms.ToolStripPanel>右、フォームの下部にあるコントロール。

## <a name="arrange-toolstrippanel-controls-by-z-order"></a>ToolStripPanel コントロールを Z オーダーによる配置します。

位置、ドッキングされた<xref:System.Windows.Forms.ToolStripPanel>MDI フォーム上のコントロールは、z オーダーでコントロールの位置によって決まります。 ドキュメント アウトライン ウィンドウでコントロールの z オーダーを簡単に配置できます。

1. **ビュー**  メニューのをクリックして**その他の Windows**、 をクリックし、**ドキュメント アウトライン**します。

     配置、<xref:System.Windows.Forms.ToolStripPanel>前の手順からのコントロールは非標準です。 これは、z オーダーが正しくありません。 ドキュメント アウトライン ウィンドウを使用すると、コントロールの z オーダーを変更できます。

2. ドキュメント アウトライン ウィンドウで、次のように選択します。 **ToolStripPanel4**します。

3. 下向きの矢印ボタンをクリックするまで繰り返し、 **ToolStripPanel4**はリストの下部に。

     **ToolStripPanel4**コントロールが他のコントロールの下に、フォームの下部にドッキングされています。

4. 選択**ToolStripPanel2**します。

5. 一覧で 3 つ目のコントロールを配置する 1 回の下向きの矢印ボタンをクリックします。

     **ToolStripPanel2**コントロールとその他のコントロールの上のメイン メニューの下には、フォームの上部にドッキングします。

6. さまざまなコントロール、**ドキュメント アウトライン**ウィンドウし、z オーダーで別の位置に移動します。 Z オーダーのドッキングされたコントロールの配置への影響に注意してください。 CTRL + Z を使用して、または**を元に戻す**上、**編集**変更を元に戻す メニュー。

## <a name="checkpoint---test-your-form"></a>チェックポイント - フォームをテストします。

1. キーを押して**F5**をコンパイルして、フォームを実行します。

2. グリップをクリックして、<xref:System.Windows.Forms.ToolStrip>を制御し、フォーム上の別の位置にコントロールをドラッグします。

     ドラッグすることができます、<xref:System.Windows.Forms.ToolStrip>から 1 つのコントロール<xref:System.Windows.Forms.ToolStripPanel>を別のコントロール。

## <a name="next-steps"></a>次の手順

このチュートリアルで MDI 親フォームを作成した<xref:System.Windows.Forms.ToolStrip>コントロールとメニューのマージします。 使用することができます、<xref:System.Windows.Forms.ToolStrip>の他のさまざまな目的のコントロール ファミリ。

- ショートカット メニューを使用してコントロールを作成<xref:System.Windows.Forms.ContextMenuStrip>です。 詳細については、次を参照してください。 [ContextMenu コンポーネントの概要](contextmenu-component-overview-windows-forms.md)します。

- 標準のメニューが自動的に設定されたフォームを作成します。 詳細については、「[チュートリアル:フォームに標準メニュー項目を用意する](walkthrough-providing-standard-menu-items-to-a-form.md)します。

- 与える、<xref:System.Windows.Forms.ToolStrip>プロフェッショナルな外観を制御します。 詳細については、「[方法 :アプリケーションの ToolStrip レンダラーを設定](how-to-set-the-toolstrip-renderer-for-an-application.md)します。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [方法: MDI 親フォームを作成する](../advanced/how-to-create-mdi-parent-forms.md)
- [方法: MDI 子フォームを作成する](../advanced/how-to-create-mdi-child-forms.md)
- [方法: MDI ドロップダウン メニューに MenuStrip を挿入します。](how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms.md)
- [ToolStrip コントロール](toolstrip-control-windows-forms.md)
