---
title: '方法: (Windows フォーム) がクリックしてされた TreeView ノードを決定します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- TreeNode
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- tree nodes in TreeView control [Windows Forms], determining node clicked
- TreeView control [Windows Forms], determining node clicked
ms.assetid: 06a4a191-d918-42af-9f49-956c93eff261
ms.openlocfilehash: 71f13c7b160822c92475d4d03e923b40d4f0454d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59296733"
---
# <a name="how-to-determine-which-treeview-node-was-clicked-windows-forms"></a>方法: (Windows フォーム) がクリックしてされた TreeView ノードを決定します。
Windows フォームを使用するときに<xref:System.Windows.Forms.TreeView>コントロール、一般的なタスクが判断するノードがクリックしてされ、適切に応答します。  
  
### <a name="to-determine-which-treeview-node-was-clicked"></a>クリックしてされた TreeView ノードを確認するには  
  
1. 使用して、<xref:System.EventArgs>クリックされたノードのオブジェクトへの参照を取得するオブジェクト。  
  
2. チェックしているノードがクリックしてされたかを判断、<xref:System.Windows.Forms.TreeViewEventArgs>クラスは、イベントに関連するデータが含まれています。  
  
    ```vb  
    Private Sub TreeView1_AfterSelect(ByVal sender As System.Object, _  
    ByVal e As System.Windows.Forms.TreeViewEventArgs) Handles TreeView1.AfterSelect  
       ' Determine by checking the Node property of the TreeViewEventArgs.  
       MessageBox.Show(e.Node.Text)  
    End Sub  
    ```  
  
    ```csharp  
    protected void treeView1_AfterSelect (object sender,   
    System.Windows.Forms.TreeViewEventArgs e)  
    {  
       // Determine by checking the Text property.  
       MessageBox.Show(e.Node.Text);  
    }  
    ```  
  
    ```cpp  
    private:  
       void treeView1_AfterSelect(System::Object ^  sender,  
          System::Windows::Forms::TreeViewEventArgs ^  e)  
       {  
          // Determine by checking the Text property.  
          MessageBox::Show(e->Node->Text);  
       }  
    ```  
  
    > [!NOTE]
    >  代わりに、使用することができます、<xref:System.Windows.Forms.MouseEventArgs>の<xref:System.Windows.Forms.Control.MouseDown>または<xref:System.Windows.Forms.Control.MouseUp>を取得するイベント、<xref:System.Drawing.Point.X%2A>と<xref:System.Drawing.Point.Y%2A>座標の値、<xref:System.Drawing.Point>クリックが発生します。 次に、使用、<xref:System.Windows.Forms.TreeView>コントロールの<xref:System.Windows.Forms.TreeView.GetNodeAt%2A>クリックしてされたノードを調べます。  
  
## <a name="see-also"></a>関連項目

- [TreeView コントロール](treeview-control-windows-forms.md)
