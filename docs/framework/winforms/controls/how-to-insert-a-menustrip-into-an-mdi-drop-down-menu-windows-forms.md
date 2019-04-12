---
title: '方法: MenuStrip を MDI ドロップダウン メニュー (Windows フォーム) に挿入します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip control [Windows Forms], inserting
- MenuStrip control [Windows Forms], merging
- MDI [Windows Forms], merging menu items
ms.assetid: 0fad444e-26d9-49af-8860-044d9c10d608
ms.openlocfilehash: 1b41699d8da1c99705f6796105dab6f3ab1d727d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59341635"
---
# <a name="how-to-insert-a-menustrip-into-an-mdi-drop-down-menu-windows-forms"></a>方法: MenuStrip を MDI ドロップダウン メニュー (Windows フォーム) に挿入します。
アプリケーションの中には、マルチ ドキュメント インターフェイス (MDI) 子ウィンドウの種類が MDI 親ウィンドウと異なるものがあります。 たとえば、MDI 親がスプレッドシートで、MDI 子がグラフの場合があります。 そのような場合は、異なる種類の MDI 子ウィンドウがアクティブになったときに、MDI 子メニューの内容で MDI 親メニューの内容を更新する必要があります。  
  
 次の手順を使用して、 <xref:System.Windows.Forms.Form.IsMdiContainer%2A>、 <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>、 <xref:System.Windows.Forms.MergeAction>、および<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>MDI 子メニューからメニュー項目のグループを MDI 親メニューのドロップダウン部分に挿入するプロパティ。 MDI 子ウィンドウを閉じると、挿入されたメニュー項目が MDI 親から削除します。  
  
### <a name="to-insert-a-menustrip-into-an-mdi-drop-down-menu"></a>MDI ドロップダウン メニューに MenuStrip を挿入するには  
  
1. フォームを作成し、その <xref:System.Windows.Forms.Form.IsMdiContainer%2A> プロパティを `true` に設定します。  
  
2. <xref:System.Windows.Forms.MenuStrip> を `Form1` に追加し、<xref:System.Windows.Forms.MenuStrip> の <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> プロパティを `true` に設定します。  
  
3. トップレベルのメニュー項目を追加、`Form1`<xref:System.Windows.Forms.MenuStrip>設定とその<xref:System.Windows.Forms.Control.Text%2A>プロパティを`&File`します。  
  
4. 3 つのサブメニュー項目を追加、`&File`メニュー項目とその<xref:System.Windows.Forms.ToolStripItem.Text%2A>プロパティを`&Open`、`&Import from`と`E&xit`。  
  
5. 2 つのサブメニュー項目を追加、`&Import from`サブメニュー項目とその<xref:System.Windows.Forms.ToolStripItem.Text%2A>プロパティを`&Word`と`&Excel`します。  
  
6. プロジェクトにフォームを追加して、<xref:System.Windows.Forms.MenuStrip>を設定し、フォーム、<xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>のプロパティ、`Form2`<xref:System.Windows.Forms.MenuStrip>に`true`します。  
  
7. トップレベルのメニュー項目を追加、`Form2`<xref:System.Windows.Forms.MenuStrip>設定とその<xref:System.Windows.Forms.ToolStripItem.Text%2A>プロパティを`&File`します。  
  
8. サブメニュー項目を追加、`&File`のメニュー`Form2`次の順序で: <xref:System.Windows.Forms.ToolStripSeparator>、 `&Save`、 `Save and &Close`、もう 1 つと<xref:System.Windows.Forms.ToolStripSeparator>します。  
  
9. 設定、<xref:System.Windows.Forms.MergeAction>と<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>のプロパティ、`Form2`メニュー項目を次の表に示すようにします。  
  
    |Form2 のメニュー項目|MergeAction 値|MergeIndex 値|  
    |---------------------|-----------------------|----------------------|  
    |ファイル|MatchOnly|-1|  
    |区切り記号|挿入|2|  
    |保存|挿入|3|  
    |保存して閉じる|挿入|4|  
    |区切り記号|挿入|5|  
  
10. イベント ハンドラーを作成、<xref:System.Windows.Forms.Control.Click>のイベント、`&Open`<xref:System.Windows.Forms.ToolStripMenuItem>します。  
  
11. このイベント ハンドラー内に次のコード例のようなコードを挿入し、`Form2` の新規インスタンスを `Form1` の MDI 子フォームとして作成し、表示します。  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As System.Object, _  
    ByVal e As System.EventArgs) Handles openToolStripMenuItem.Click  
        Dim NewMDIChild As New Form2()  
        'Set the parent form of the child window.  
            NewMDIChild.MdiParent = Me  
        'Display the new form.  
            NewMDIChild.Show()  
    End Sub  
    ```  
  
    ```csharp  
    private void openToolStripMenuItem_Click(object sender, EventArgs e)  
    {  
        Form2 newMDIChild = new Form2();  
        // Set the parent form of the child window.  
            newMDIChild.MdiParent = this;  
        // Display the new form.  
            newMDIChild.Show();  
    }  
    ```  
  
12. 次のコード例のようなコードを配置、`&Open`<xref:System.Windows.Forms.ToolStripMenuItem>イベント ハンドラーを登録します。  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   `Form1` と `Form2` という名前の 2 つの <xref:System.Windows.Forms.Form> コントロール。  
  
-   `Form1` 上の `menuStrip1` という名前の <xref:System.Windows.Forms.MenuStrip> コントロールと、`Form2` 上の `menuStrip2` という名前の <xref:System.Windows.Forms.MenuStrip> コントロール。  
  
-   <xref:System?displayProperty=nameWithType> アセンブリおよび <xref:System.Windows.Forms?displayProperty=nameWithType> アセンブリへの参照。  
  
## <a name="see-also"></a>関連項目

- [方法: MDI 親フォームを作成する](../advanced/how-to-create-mdi-parent-forms.md)
- [方法: MDI 子フォームを作成する](../advanced/how-to-create-mdi-child-forms.md)
- [MenuStrip コントロールの概要 (Windows フォーム)](menustrip-control-overview-windows-forms.md)
