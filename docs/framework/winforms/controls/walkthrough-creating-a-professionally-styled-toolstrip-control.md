---
title: 'チュートリアル: プロフェッショナル スタイルの ToolStrip コントロールの作成'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStripRenderer class [Windows Forms]
- toolbars [Windows Forms], walkthroughs
- ToolStrip control [Windows Forms], creating professionally styled controls
ms.assetid: b52339ae-f1d3-494e-996e-eb455614098a
ms.openlocfilehash: 226e805d0240236899ee0cc290f1060a3b0aa391
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211773"
---
# <a name="walkthrough-creating-a-professionally-styled-toolstrip-control"></a>チュートリアル: プロフェッショナル スタイルの ToolStrip コントロールの作成

アプリケーションを与えることができます<xref:System.Windows.Forms.ToolStrip>から派生した独自のクラスを記述することで、プロフェッショナルな外観と動作を制御、<xref:System.Windows.Forms.ToolStripProfessionalRenderer>型。

このチュートリアルを使用する方法について説明<xref:System.Windows.Forms.ToolStrip>に似た複合コントロールを作成するコントロール、**ナビゲーション ウィンドウ**Microsoft® Outlook® で提供されます。 このチュートリアルで、次のタスクを示します。

- Windows コントロール ライブラリ プロジェクトを作成します。

- StackView コントロールをデザインします。

- カスタム レンダラーの実装。

完了したら、Microsoft Office® XP のコントロールのプロフェッショナルな外観のカスタム クライアントを再利用可能なコントロールがあります。

このトピックのコードを単一のリストとしてコピーするには、「[方法:プロフェッショナル スタイルの ToolStrip コントロールを作成する](how-to-create-a-professionally-styled-toolstrip-control.md)します。

## <a name="prerequisites"></a>必須コンポーネント

Visual Studio でこのチュートリアルを完了する必要があります。

## <a name="create-the-control-library-project"></a>コントロール ライブラリ プロジェクトを作成します。

1. Visual Studio で、という名前の新しい Windows コントロール ライブラリ プロジェクトを作成`StackViewLibrary`です。

2. **ソリューション エクスプ ローラー**、選択した言語に応じて"UserControl1.cs"または「[usercontrol1.vb]」をという名前のソース ファイルを削除することによって、プロジェクトの既定のコントロールを削除します。

     詳細については、「[方法 :削除、削除、および項目を除外](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0ebzhwsk(v=vs.100))します。

3. 新しい追加<xref:System.Windows.Forms.UserControl>項目を**StackViewLibrary**プロジェクト。 新しいソース ファイルの基本の名前を付けます`StackView`します。

## <a name="design-the-stackview-control"></a>StackView コントロールのデザイン

`StackView`コントロールが 1 つの子による複合コントロール<xref:System.Windows.Forms.ToolStrip>コントロール。 複合コントロールの詳細については、次を参照してください。[カスタム コントロールのさまざまな](varieties-of-custom-controls.md)します。

1. **ツールボックス**、ドラッグ、<xref:System.Windows.Forms.ToolStrip>コントロールをデザイン画面。

2. **プロパティ**ウィンドウで、設定、<xref:System.Windows.Forms.ToolStrip>次の表に従って、コントロールのプロパティ。

    |プロパティ|値|
    |--------------|-----------|
    |名前|`stackStrip`|
    |CanOverflow|`false`|
    |ドッキング|<xref:System.Windows.Forms.DockStyle.Bottom>|
    |フォント|`Tahoma, 10pt, style=Bold`|
    |GripStyle|<xref:System.Windows.Forms.ToolStripGripStyle.Hidden>|
    |LayoutStyle|<xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow>|
    |[間隔]|`0, 7, 0, 0`|
    |RenderMode|<xref:System.Windows.Forms.ToolStripRenderMode.Professional>|

3. Windows フォーム デザイナーでクリックして、<xref:System.Windows.Forms.ToolStrip>コントロールの**追加**ボタンをクリックし、追加、<xref:System.Windows.Forms.ToolStripButton>を`stackStrip`コントロール。

4. **プロパティ**ウィンドウで、設定、<xref:System.Windows.Forms.ToolStripButton>次の表に従って、コントロールのプロパティ。

    |プロパティ|値|
    |--------------|-----------|
    |名前|`mailStackButton`|
    |CheckOnClick|true|
    |CheckState|<xref:System.Windows.Forms.CheckState.Checked>|
    |DisplayStyle|<xref:System.Windows.Forms.ToolStripItemDisplayStyle.ImageAndText>|
    |ImageAlign|<xref:System.Drawing.ContentAlignment.MiddleLeft>|
    |ImageScaling|<xref:System.Windows.Forms.ToolStripItemImageScaling.None>|
    |ImageTransparentColor|`238, 238, 238`|
    |余白|`0, 0, 0, 0`|
    |[間隔]|`3, 3, 3, 3`|
    |テキスト|**メール**|
    |TextAlign|<xref:System.Drawing.ContentAlignment.MiddleLeft>|

5. 詳細の 3 つの手順 7.<xref:System.Windows.Forms.ToolStripButton>コントロール。

     コントロールの名前を付けます`calendarStackButton`、 `contactsStackButton`、および`tasksStackButton`します。 値を設定、<xref:System.Windows.Forms.Control.Text%2A>プロパティを**カレンダー**、**連絡先**、および**タスク**、それぞれします。

## <a name="handle-events"></a>イベントの処理

2 つのイベントは必ず、`StackView`コントロールが正しく動作します。 処理、<xref:System.Windows.Forms.UserControl.Load>コントロールを正しく配置するイベントです。 処理、<xref:System.Windows.Forms.ToolStripItem.Click>ごとにイベント<xref:System.Windows.Forms.ToolStripButton>提供する、`StackView`のような状態の動作を制御、<xref:System.Windows.Forms.RadioButton>コントロール。

1. Windows フォーム デザイナーで、選択、`StackView`コントロール。

2. **[プロパティ]** ウィンドウで、**[イベント]** をクリックします。

3. Load イベントをダブルクリックして、`StackView_Load`イベント ハンドラー。

4. 
  `StackView_Load` イベント ハンドラーで、次のコードをコピーして貼り付けます。

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#3)]

5. Windows フォーム デザイナーで、選択、`mailStackButton`コントロール。

6. **[プロパティ]** ウィンドウで、**[イベント]** をクリックします。

7. クリック イベントをダブルクリックします。

     Windows フォーム デザイナーで生成する、`mailStackButton_Click`イベント ハンドラー。

8. 名前の変更、`mailStackButton_Click`イベント ハンドラーを`stackButton_Click`します。

     詳細については、次を参照してください。[コード シンボルのリファクタリングの名前を変更](/visualstudio/ide/reference/rename)します。

9. 次のコードを挿入、`stackButton_Click`イベント ハンドラー。

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#4)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#4)]

10. Windows フォーム デザイナーで、選択、`calendarStackButton`コントロール。

11. **プロパティ**ウィンドウのクリック イベントを設定、`stackButton_Click`イベント ハンドラー。

12. 手順 10 および 11 for、`contactsStackButton`と`tasksStackButton`コントロール。

## <a name="define-icons"></a>アイコンを定義します。

各`StackView`ボタンに関連付けられているアイコンがあります。 便宜上、各アイコンは、Base64 でエンコードされた文字列としての前に逆シリアル化する、<xref:System.Drawing.Bitmap>これから作成されます。 運用環境でリソースとしてビットマップ データを格納して、Windows フォーム デザイナーで、アイコンが表示されます。 詳細については、「[方法 :Windows フォームに背景画像の追加](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/dff9f95f(v=vs.100))します。

1. コード エディターには、次のコードを挿入、`StackView`クラスの定義。 このコードでのビットマップは初期化、<xref:System.Windows.Forms.ToolStripButton>アイコン。

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#2)]

2. 呼び出しを追加、`InitializeImages`メソッドで、`StackView`クラスのコンス トラクター。

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]

## <a name="implement-a-custom-renderer"></a>カスタム レンダラーを実装します。

ほとんどの要素をカスタマイズすることができます、`StackView`から派生したクラスを実装する、コントロール、<xref:System.Windows.Forms.ToolStripRenderer>クラス。 この手順では、実装、<xref:System.Windows.Forms.ToolStripProfessionalRenderer>グリップをカスタマイズおよび用のグラデーション背景を描画するクラスを<xref:System.Windows.Forms.ToolStripButton>コントロール。

1. 次のコードを挿入、`StackView`定義を制御します。

     定義、`StackRenderer`クラスでオーバーライドされます、 <xref:System.Windows.Forms.ToolStripRenderer.RenderGrip>、 <xref:System.Windows.Forms.ToolStripRenderer.RenderToolStripBorder>、および<xref:System.Windows.Forms.ToolStripRenderer.RenderButtonBackground>カスタムの外観を生成するメソッド。

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#10)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#10)]

2. `StackView`コントロールのコンス トラクターの新しいインスタンスを作成、`StackRenderer`クラスし、このインスタンスに割り当てる、`stackStrip`コントロールの<xref:System.Windows.Forms.ToolStrip.Renderer%2A>プロパティ。

     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]

## <a name="test-the-stackview-control"></a>StackView コントロールをテストします。

`StackView`コントロールから派生、<xref:System.Windows.Forms.UserControl>クラス。 そのため、コントロールをテストできます、 **UserControl Test Container**します。 詳細については、「[方法 :UserControl の実行時の動作をテスト](how-to-test-the-run-time-behavior-of-a-usercontrol.md)します。

1. キーを押して**F5** 、プロジェクトをビルドし、開始、 **UserControl Test Container**します。

2. ボタンの上にポインターを移動、`StackView`を制御して、選択した状態の外観を表示するボタンをクリックします。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、Office XP のコントロールのプロフェッショナルな外観のカスタム クライアントを再利用可能なコントロールを作成しました。 使用することができます、<xref:System.Windows.Forms.ToolStrip>の他のさまざまな目的のコントロール ファミリ。

- ショートカット メニューを使用してコントロールを作成<xref:System.Windows.Forms.ContextMenuStrip>です。 詳細については、次を参照してください。 [ContextMenu コンポーネントの概要](contextmenu-component-overview-windows-forms.md)します。

- 自動的に設定された標準メニューには、フォームを作成します。 詳細については、「[チュートリアル:フォームに標準メニュー項目を用意する](walkthrough-providing-standard-menu-items-to-a-form.md)します。

- ドッキングのマルチ ドキュメント インターフェイス (MDI) フォームを作成する<xref:System.Windows.Forms.ToolStrip>コントロール。 詳細については、「[方法 :メニューのマージと ToolStrip コントロールを MDI フォームを作成](how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md)です。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [ToolStrip コントロール](toolstrip-control-windows-forms.md)
- [方法: フォームに標準メニュー項目を提供します。](how-to-provide-standard-menu-items-to-a-form.md)
