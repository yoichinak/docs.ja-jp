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
ms.openlocfilehash: c8f6e51b5ab8242ba8253a04160c40e59fce0088
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648197"
---
# <a name="walkthrough-creating-an-explorer-style-interface-with-the-listview-and-treeview-controls-using-the-designer"></a>チュートリアル: デザイナーを使用した、ListView コントロールと TreeView コントロールを含むエクスプローラー スタイルのインターフェイスの作成
Visual Studio の利点の 1 つは、時間の短い形式で本格的な Windows フォーム アプリケーションを作成する機能です。 一般的なシナリオがユーザー インターフェイス (UI) で作成して<xref:System.Windows.Forms.ListView>と<xref:System.Windows.Forms.TreeView>Windows オペレーティング システムの Windows エクスプ ローラーの機能のようなコントロール。 Windows エクスプ ローラーは、ユーザーのコンピューター上のファイルとフォルダーの階層構造を表示します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="to-create-the-form-containing-a-listview-and-treeview-control"></a>ListView、TreeView コントロールを含むフォームを作成するには  
  
1. **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。  
  
2. **新しいプロジェクト** ダイアログ ボックスで、次の操作を行います。  
  
    1. カテゴリでいずれかを選択**Visual Basic**または**Visual c#** します。  
  
    2. テンプレートの一覧で選択**Windows フォーム アプリケーション**します。  
  
3. **[OK]** をクリックします。 新しい Windows フォーム プロジェクトが作成されます。  
  
4. 追加、<xref:System.Windows.Forms.SplitContainer>コントロールをフォームにし、設定、<xref:System.Windows.Forms.SplitContainer.Dock%2A>プロパティを<xref:System.Windows.Forms.DockStyle.Fill>します。  
  
5. 追加、<xref:System.Windows.Forms.ImageList>という名前の`imageList1`フォームと 2 つのイメージを追加する [プロパティ] ウィンドウを使用する: フォルダーのイメージとその順序で、ドキュメントのイメージ。  
  
6. 追加、<xref:System.Windows.Forms.TreeView>という名前のコントロール`treeview1`をフォームに配置の左側にある、<xref:System.Windows.Forms.SplitContainer>コントロール。 [プロパティ] ウィンドウで`treeView1`次の操作を行います。  
  
    1. <xref:System.Windows.Forms.Control.Dock%2A> プロパティを <xref:System.Windows.Forms.DockStyle.Fill>に設定します。  
  
    2. 
  <xref:System.Windows.Forms.TreeView.ImageList%2A> プロパティを `imagelist1.` に設定します。  
  
7. 追加、<xref:System.Windows.Forms.ListView>という名前のコントロール`listView1`をフォームの右側の上に移動し、<xref:System.Windows.Forms.SplitContainer>コントロール。 [プロパティ] ウィンドウで`listview1`次の操作を行います。  
  
    1. <xref:System.Windows.Forms.Control.Dock%2A> プロパティを <xref:System.Windows.Forms.DockStyle.Fill>に設定します。  
  
    2. <xref:System.Windows.Forms.ListView.View%2A> プロパティを <xref:System.Windows.Forms.View.Details>に設定します。  
  
    3. 省略記号をクリックして、ColumnHeader コレクション エディターを開きます (![VisualStudioEllipsesButton スクリーン ショット](../media/vbellipsesbutton.png "vbEllipsesButton")) で、<xref:System.Windows.Forms.ListView.Columns%2A>プロパティ**します。** 3 つの列を追加し、設定、<xref:System.Windows.Forms.ColumnHeader.Text%2A>プロパティを`Name`、 `Type`、および`Last Modified`、それぞれします。 **[OK]** をクリックしてダイアログ ボックスを閉じます。  
  
    4. 
  <xref:System.Windows.Forms.ListView.SmallImageList%2A> プロパティを `imageList1.` に設定します。  
  
8. データを読み込むコードを実装、<xref:System.Windows.Forms.TreeView>ノードおよびサブノードにします。 
  `Form1` クラスに次のコードを追加します。  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#1)]  
  
9. 前のコードでは、System.IO 名前空間を使用するため、適切な using の追加または、フォームの上部にあるステートメントをインポートします。  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#4)]  
  
10. フォームのコンス トラクターの前の手順からのセットアップ メソッドを呼び出すまたは<xref:System.Windows.Forms.Form.Load>イベント処理メソッド。 このコードをフォームのコンス トラクターに追加します。  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#2)]  
  
11. 処理、<xref:System.Windows.Forms.TreeView.NodeMouseClick>イベントを`treeview1` **、** を設定するコードを実装し、`listview1`ノードのコンテンツ ノードがクリックされたときに使用します。 
  `Form1` クラスに次のコードを追加します。  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#3)]  
  
     C# を使用している場合があることを確認、<xref:System.Windows.Forms.TreeView.NodeMouseClick>イベントのイベント処理メソッドに関連付けられています。 このコードをフォームのコンス トラクターに追加します。  
  
     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#5)]  
  
## <a name="testing-the-application"></a>アプリケーションのテスト  
 フォームをテストして、期待どおりに動作することを確認します。  
  
#### <a name="to-test-the-form"></a>フォームをテストするには  
  
- F5 キーを押してアプリケーションを実行します。  
  
     含む分割フォームが表示されます、<xref:System.Windows.Forms.TreeView>左側にある、プロジェクト ディレクトリを表示するコントロールと<xref:System.Windows.Forms.ListView>3 つの列の右側にあるコントロール。 走査することができます、<xref:System.Windows.Forms.TreeView>ディレクトリのノードを選択して、<xref:System.Windows.Forms.ListView>は選択したディレクトリの内容が格納されます。  
  
## <a name="next-steps"></a>次の手順  
 このアプリケーションは、使用できる方法の例を示します<xref:System.Windows.Forms.TreeView>と<xref:System.Windows.Forms.ListView>化を制御します。 これらのコントロールの詳細については、次のトピックを参照してください。  
  
- [方法: TreeView コントロールまたは ListView コントロール (Windows フォーム) にカスタム情報を追加します。](add-custom-information-to-a-treeview-or-listview-control-wf.md)  
  
- [方法: ListView コントロールに検索機能を追加します。](how-to-add-search-capabilities-to-a-listview-control.md)  
  
- [方法: ショートカット メニューを TreeView ノードにアタッチします。](how-to-attach-a-shortcut-menu-to-a-treeview-node.md)  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.TreeView>
- [ListView コントロール](listview-control-windows-forms.md)
- [方法: 追加して、Windows フォーム TreeView コントロールでノードを削除](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [方法: Windows フォーム ListView コントロールで項目追加および削除](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [方法: Windows フォーム ListView コントロールに列を追加します。](how-to-add-columns-to-the-windows-forms-listview-control.md)
