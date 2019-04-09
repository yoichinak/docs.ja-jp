---
title: '方法: ToolStripMenuItem を MDI ドロップダウン メニュー (Windows フォーム) から削除します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- menu items [Windows Forms], removing from MDI drop-down menus
- MenuStrip control [Windows Forms], merging
- MenuStrip control [Windows Forms], removing
- MDI [Windows Forms], merging menu items
ms.assetid: bdafe60d-82ee-45bc-97fe-eeefca6e54c1
ms.openlocfilehash: 6e0d453903b817e9acd743e835f4d466e3565271
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132835"
---
# <a name="how-to-remove-a-toolstripmenuitem-from-an-mdi-drop-down-menu-windows-forms"></a>方法: ToolStripMenuItem を MDI ドロップダウン メニュー (Windows フォーム) から削除します。
アプリケーションの中には、マルチ ドキュメント インターフェイス (MDI) 子ウィンドウの種類が MDI 親ウィンドウと異なるものがあります。 たとえば、MDI 親がスプレッドシートで、MDI 子がグラフの場合があります。 そのような場合は、異なる種類の MDI 子ウィンドウがアクティブになったときに、MDI 子メニューの内容で MDI 親メニューの内容を更新する必要があります。  
  
 次の手順を使用して、 <xref:System.Windows.Forms.Form.IsMdiContainer%2A>、 <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>、 <xref:System.Windows.Forms.MergeAction>、および<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>MDI 親メニューのドロップダウン部分からメニュー項目を削除するプロパティ。 MDI 子ウィンドウを閉じる、MDI 親メニューを削除したメニュー項目を復元します。  
  
### <a name="to-remove-a-menustrip-from-an-mdi-drop-down-menu"></a>MenuStrip を MDI ドロップダウン メニューから削除するには  
  
1.  フォームを作成し、その <xref:System.Windows.Forms.Form.IsMdiContainer%2A> プロパティを `true` に設定します。  
  
2.  <xref:System.Windows.Forms.MenuStrip> を `Form1` に追加し、<xref:System.Windows.Forms.MenuStrip> の <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> プロパティを `true` に設定します。  
  
3.  トップレベルのメニュー項目を追加、`Form1`<xref:System.Windows.Forms.MenuStrip>設定とその<xref:System.Windows.Forms.Control.Text%2A>プロパティを`&File`します。  
  
4.  3 つのサブメニュー項目を追加、`&File`メニュー項目とその<xref:System.Windows.Forms.ToolStripItem.Text%2A>プロパティを`&Open`、`&Import from`と`E&xit`。  
  
5.  2 つのサブメニュー項目を追加、`&Import from`サブメニュー項目とその<xref:System.Windows.Forms.ToolStripItem.Text%2A>プロパティを`&Word`と`&Excel`します。  
  
6.  プロジェクトにフォームを追加して、<xref:System.Windows.Forms.MenuStrip>を設定し、フォーム、<xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>のプロパティ、`Form2`<xref:System.Windows.Forms.MenuStrip>に`true`します。  
  
7.  トップレベルのメニュー項目を追加、`Form2`<xref:System.Windows.Forms.MenuStrip>設定とその<xref:System.Windows.Forms.ToolStripItem.Text%2A>プロパティを`&File`します。  
  
8.  追加、`&Import from`サブメニュー項目を`&File`のメニュー `Form2`、追加、`&Word`サブメニュー項目を`&File`メニュー。  
  
9. 設定、<xref:System.Windows.Forms.MergeAction>と<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>のプロパティ、`Form2`メニュー項目を次の表に示すようにします。  
  
    |Form2 のメニュー項目|MergeAction 値|MergeIndex 値|  
    |---------------------|-----------------------|----------------------|  
    |ファイル|MatchOnly|-1|  
    |インポートします。|MatchOnly|-1|  
    |Word|削除|-1|  
  
10. `Form1`、イベント ハンドラーを作成、<xref:System.Windows.Forms.Control.Click>のイベント、`&Open`<xref:System.Windows.Forms.ToolStripMenuItem>します。  
  
11. イベント ハンドラー内の新しいインスタンスを作成し、次のコード例のようなコードを挿入`Form2`の MDI 子フォームとして`Form1`:  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles openToolStripMenuItem.Click  
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
    this.openToolStripMenuItem.Click += new _  
    System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   `Form1` と `Form2` という名前の 2 つの <xref:System.Windows.Forms.Form> コントロール。  
  
-   `Form1` 上の `menuStrip1` という名前の <xref:System.Windows.Forms.MenuStrip> コントロールと、`Form2` 上の `menuStrip2` という名前の <xref:System.Windows.Forms.MenuStrip> コントロール。  
  
-   
  <xref:System?displayProperty=nameWithType> アセンブリおよび <xref:System.Windows.Forms?displayProperty=nameWithType> アセンブリへの参照。  
  
## <a name="see-also"></a>関連項目

- [方法: MDI 親フォームを作成する](../advanced/how-to-create-mdi-parent-forms.md)
- [方法: MDI 子フォームを作成する](../advanced/how-to-create-mdi-child-forms.md)
- [MenuStrip コントロールの概要](menustrip-control-overview-windows-forms.md)
