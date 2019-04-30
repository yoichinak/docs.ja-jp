---
title: '方法: MenuStrip を MDI 親ウィンドウ (Windows フォーム) に追加します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip control [Windows Forms], merging
- MenuStrip control [Windows Forms], appending
- MDI [Windows Forms], merging menu items
ms.assetid: ab70c936-b452-4653-b417-17be57bb795b
ms.openlocfilehash: a335531b090983de4e2b3daccc9f956930cbad6e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011030"
---
# <a name="how-to-append-a-menustrip-to-an-mdi-parent-window-windows-forms"></a>方法: MenuStrip を MDI 親ウィンドウ (Windows フォーム) に追加します。
アプリケーションの中には、マルチ ドキュメント インターフェイス (MDI) 子ウィンドウの種類が MDI 親ウィンドウと異なるものがあります。 たとえば、MDI 親がスプレッドシートで、MDI 子がグラフの場合があります。 そのような場合は、異なる種類の MDI 子ウィンドウがアクティブになったときに、MDI 子メニューの内容で MDI 親メニューの内容を更新する必要があります。  
  
 次の手順では、<xref:System.Windows.Forms.Form.IsMdiContainer%2A>、<xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>、<xref:System.Windows.Forms.MergeAction>、および <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> の各プロパティを使用して MDI 子メニューを MDI 親メニューに追加します MDI 子ウィンドウを閉じると、追加したメニューが MDI 親から削除されます。  
  
 参照してください[マルチ ドキュメント インターフェイス (MDI) アプリケーション](../advanced/multiple-document-interface-mdi-applications.md)します。  
  
### <a name="to-append-a-menu-item-to-an-mdi-parent"></a>メニュー項目を MDI 親に追加するには  
  
1. フォームを作成し、その <xref:System.Windows.Forms.Form.IsMdiContainer%2A> プロパティを `true` に設定します。  
  
2. <xref:System.Windows.Forms.MenuStrip> を `Form1` に追加し、<xref:System.Windows.Forms.MenuStrip> の <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> プロパティを `true` に設定します。  
  
3. `Form1` の <xref:System.Windows.Forms.MenuStrip> の <xref:System.Windows.Forms.ToolStripItem.Visible%2A> プロパティを `false` に設定します。  
  
4. トップレベル メニュー項目を `Form1` の <xref:System.Windows.Forms.MenuStrip> に追加し、その <xref:System.Windows.Forms.Control.Text%2A> プロパティを「`&File`」に設定しますす。  
  
5. サブメニュー項目を `&File` メニュー項目に追加し、その <xref:System.Windows.Forms.Form.Text%2A> プロパティを「`&Open`」に設定します。  
  
6. プロジェクトにフォームを追加し、フォームに <xref:System.Windows.Forms.MenuStrip> を追加し、`Form2` の <xref:System.Windows.Forms.MenuStrip> の <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> のプロパティを `true` に設定します。  
  
7. トップレベル メニュー項目を `Form2` の <xref:System.Windows.Forms.MenuStrip> に追加し、その <xref:System.Windows.Forms.Form.Text%2A> プロパティを「`&Special`」に設定しますす。  
  
8. 2 つのサブメニュー項目を `&Special` メニュー項目に追加し、それらの <xref:System.Windows.Forms.Form.Text%2A> プロパティをそれぞれ「`Command&1`」と「`Command&2`」に設定します。  
  
9. `&Special`、`Command&1`、および `Command&2` メニュー項目の <xref:System.Windows.Forms.MergeAction> プロパティを <xref:System.Windows.Forms.MergeAction.Append> に設定します。  
  
10. <xref:System.Windows.Forms.ToolStripMenuItem> の `&New` の <xref:System.Windows.Forms.Control.Click> イベントにイベント ハンドラーを作成します。  
  
11. このイベント ハンドラー内に次のコード例のようなコードを挿入し、`Form2` の新規インスタンスを `Form1` の MDI 子フォームとして作成し、表示します。  
  
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
  
12. `&Open`<xref:System.Windows.Forms.ToolStripMenuItem> に次のコード例のようなコードを配置し、イベント ハンドラーを登録します。  
  
    ```vb  
    Private Sub openToolStripMenuItem_Click(sender As Object, e As _  
    EventArgs) Handles openToolStripMenuItem.Click  
    ```  
  
    ```csharp  
    this.openToolStripMenuItem.Click += new System.EventHandler(this.openToolStripMenuItem_Click);  
    ```  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
- `Form1` と `Form2` という名前の 2 つの <xref:System.Windows.Forms.Form> コントロール。  
  
- `Form1` 上の `menuStrip1` という名前の <xref:System.Windows.Forms.MenuStrip> コントロールと、`Form2` 上の `menuStrip2` という名前の <xref:System.Windows.Forms.MenuStrip> コントロール。  
  
- <xref:System?displayProperty=nameWithType> アセンブリおよび <xref:System.Windows.Forms?displayProperty=nameWithType> アセンブリへの参照。
