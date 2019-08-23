---
title: '方法: クリックされた TreeView ノードを確認する (Windows フォーム)'
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
ms.openlocfilehash: ab93158daf987e2f19516b8fb3abf80bfe79a12c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967341"
---
# <a name="how-to-determine-which-treeview-node-was-clicked-windows-forms"></a>方法: クリックされた TreeView ノードを確認する (Windows フォーム)
Windows フォーム<xref:System.Windows.Forms.TreeView>コントロールを使用する場合の一般的なタスクは、どのノードがクリックされたかを判断し、適切に対応することです。  
  
### <a name="to-determine-which-treeview-node-was-clicked"></a>クリックされた TreeView ノードを確認するには  
  
1. <xref:System.EventArgs>オブジェクトを使用して、クリックされたノードオブジェクトへの参照を返します。  
  
2. イベントに関連するデータを含む<xref:System.Windows.Forms.TreeViewEventArgs>クラスを確認して、どのノードがクリックされたかを確認します。  
  
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
    > 別の方法として、イベント<xref:System.Windows.Forms.MouseEventArgs> <xref:System.Drawing.Point.Y%2A> <xref:System.Drawing.Point.X%2A> <xref:System.Windows.Forms.Control.MouseDown>または<xref:System.Windows.Forms.Control.MouseUp>イベントのを使用して、クリックが発生<xref:System.Drawing.Point>したの座標値を取得することもできます。 次に、コントロール<xref:System.Windows.Forms.TreeView>の<xref:System.Windows.Forms.TreeView.GetNodeAt%2A>メソッドを使用して、どのノードがクリックされたかを確認します。  
  
## <a name="see-also"></a>関連項目

- [TreeView コントロール](treeview-control-windows-forms.md)
