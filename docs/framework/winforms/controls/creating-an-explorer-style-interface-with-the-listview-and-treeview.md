---
title: 'チュートリアル: デザイナーを使用した、ListView コントロールと TreeView コントロールを含むエクスプローラー スタイルのインターフェイスの作成'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Explorer-style applications [Windows Forms], walkthroughs
- TreeView control [Windows Forms], ListView controls used with
- ListView control [Windows Forms], TreeView controls used with
- Explorer-style applications
- TreeView control [Windows Forms], using for explorer-style interface
- ListView control [Windows Forms], explorer style interface
- ListView control [Windows Forms], explorer-style interface
ms.assetid: 9e5e7721-19e2-4890-b273-a43589fe99ff
ms.openlocfilehash: d80f8e3bc729689b274af520bc37fda8417b0407
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658569"
---
# <a name="walkthrough-creating-an-explorer-style-interface-with-the-listview-and-treeview-controls-using-the-designer"></a>チュートリアル: デザイナーを使用した、ListView コントロールと TreeView コントロールを含むエクスプローラー スタイルのインターフェイスの作成

Visual Studio の利点の1つは、プロフェッショナルな外観の Windows フォームアプリケーションを短時間で作成できることです。 一般的なシナリオでは、windows オペレーティングシステムの windows エクスプローラー <xref:System.Windows.Forms.ListView>機能<xref:System.Windows.Forms.TreeView>に似たコントロールとコントロールを使用して、ユーザーインターフェイス (UI) を作成します。 エクスプローラーには、ユーザーのコンピューター上のファイルとフォルダーの階層構造が表示されます。

### <a name="to-create-the-form-containing-a-listview-and-treeview-control"></a>ListView コントロールと TreeView コントロールを含むフォームを作成するには

1. **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。

2. **[新しいプロジェクト]** ダイアログボックスで、次の操作を行います。

    1. カテゴリ で、 **Visual Basic** または **ビジュアルC#**  を選択します。

    2. テンプレートの一覧で、 **[Windows フォームアプリケーション]** を選択します。

3. **[OK]** をクリックします。 新しい Windows フォームプロジェクトが作成されます。

4. フォームに<xref:System.Windows.Forms.SplitContainer.Dock%2A> <xref:System.Windows.Forms.DockStyle.Fill>コントロールを追加し、そのプロパティをに設定します。 <xref:System.Windows.Forms.SplitContainer>

5. という名前`imageList1`のをフォームに追加し、プロパティウィンドウを使用して2つのイメージ (フォルダーイメージとドキュメントイメージ) をこの順序で追加します。 <xref:System.Windows.Forms.ImageList>

6. という<xref:System.Windows.Forms.TreeView>名前`treeview1`のコントロールをフォームに追加し、 <xref:System.Windows.Forms.SplitContainer>コントロールの左側に配置します。 の`treeView1`プロパティウィンドウで、次の操作を行います。

    1. <xref:System.Windows.Forms.Control.Dock%2A> プロパティを <xref:System.Windows.Forms.DockStyle.Fill>に設定します。

    2. <xref:System.Windows.Forms.TreeView.ImageList%2A> プロパティを `imagelist1.` に設定します。

7. という<xref:System.Windows.Forms.ListView>名前`listView1`のコントロールをフォームに追加し、 <xref:System.Windows.Forms.SplitContainer>コントロールの右側に配置します。 の`listview1`プロパティウィンドウで、次の操作を行います。

    1. <xref:System.Windows.Forms.Control.Dock%2A> プロパティを <xref:System.Windows.Forms.DockStyle.Fill>に設定します。

    2. <xref:System.Windows.Forms.ListView.View%2A> プロパティを <xref:System.Windows.Forms.View.Details> に設定します。

    3. [![ ] <xref:System.Windows.Forms.ListView.Columns%2A>プロパティの省略記号 (省略記号ボタン ([...] プロパティウィンドウ](./media/visual-studio-ellipsis-button.png)) をクリックして、columnheader コレクションエディターを開きます。 3つの列を追加<xref:System.Windows.Forms.ColumnHeader.Text%2A>し、それぞれ`Type`のプロパティ`Last Modified`を、、およびに`Name`それぞれ設定します。 **[OK]** をクリックしてダイアログ ボックスを閉じます。

    4. <xref:System.Windows.Forms.ListView.SmallImageList%2A> プロパティを `imageList1.` に設定します。

8. ノードとサブノードを<xref:System.Windows.Forms.TreeView>に設定するコードを実装します。 `Form1` クラスに次のコードを追加します。

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#1)]

9. 前のコードでは System.IO 名前空間を使用しているため、フォームの先頭に適切な using ステートメントまたは import ステートメントを追加します。

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#4)]

10. フォームのコンストラクターまたは<xref:System.Windows.Forms.Form.Load>イベント処理メソッドで、前の手順の設定メソッドを呼び出します。 このコードをフォームコンストラクターに追加します。

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#2)]

11. <xref:System.Windows.Forms.TreeView.NodeMouseClick>の `listview1`イベントを処理し、ノードがクリックされたときにノードの内容を設定するコードを実装します。 `treeview1` `Form1` クラスに次のコードを追加します。

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#3)]

     を使用C#している場合は、イベント処理<xref:System.Windows.Forms.TreeView.NodeMouseClick>メソッドにイベントが関連付けられていることを確認してください。 このコードをフォームコンストラクターに追加します。

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#5)]

## <a name="testing-the-application"></a>アプリケーションのテスト

フォームをテストして、期待どおりに動作することを確認します。

#### <a name="to-test-the-form"></a>フォームをテストするには

- F5 キーを押してアプリケーションを実行します。

     左側にプロジェクトディレクトリを表示する<xref:System.Windows.Forms.TreeView>コントロール<xref:System.Windows.Forms.ListView>と、右側に3つの列があるコントロールを含む分割フォームが表示されます。 を走査<xref:System.Windows.Forms.TreeView>するには、ディレクトリノードを選択し<xref:System.Windows.Forms.ListView>ます。には、選択したディレクトリの内容が設定されます。

## <a name="next-steps"></a>次の手順

このアプリケーションでは、を使用<xref:System.Windows.Forms.TreeView>して制御する方法の例を示して<xref:System.Windows.Forms.ListView>います。 これらのコントロールの詳細については、次のトピックを参照してください。

- [方法: TreeView コントロールまたは ListView コントロールにカスタム情報を追加する (Windows フォーム)](add-custom-information-to-a-treeview-or-listview-control-wf.md)

- [方法: ListView コントロールに検索機能を追加する](how-to-add-search-capabilities-to-a-listview-control.md)

- [方法: ショートカットメニューを TreeView ノードにアタッチする](how-to-attach-a-shortcut-menu-to-a-treeview-node.md)

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.TreeView>
- [ListView コントロール](listview-control-windows-forms.md)
- [方法: Windows フォーム TreeView コントロールを使用してノードを追加および削除する](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [方法: Windows フォーム ListView コントロールを使用して項目を追加および削除する](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [方法: Windows フォーム ListView コントロールに列を追加する](how-to-add-columns-to-the-windows-forms-listview-control.md)
