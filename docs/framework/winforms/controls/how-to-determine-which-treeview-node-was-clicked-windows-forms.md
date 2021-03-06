---
title: "方法 : クリックされた TreeView ノード (Windows フォーム) を判別する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
f1_keywords: TreeNode
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- tree nodes in TreeView control [Windows Forms], determining node clicked
- TreeView control [Windows Forms], determining node clicked
ms.assetid: 06a4a191-d918-42af-9f49-956c93eff261
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2671d2790b3c5e476513cd5932d4684838aeceb6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-determine-which-treeview-node-was-clicked-windows-forms"></a>方法 : クリックされた TreeView ノード (Windows フォーム) を判別する
Windows フォームを使用するときに<xref:System.Windows.Forms.TreeView>一般的なタスクは制御を決定するノードがクリックされたして適切に応答します。  
  
### <a name="to-determine-which-treeview-node-was-clicked"></a>クリックしてされた TreeView ノードを決定するには  
  
1.  使用して、<xref:System.EventArgs>クリックされたノードのオブジェクトへの参照を取得するオブジェクト。  
  
2.  チェックしてのどのノードがクリックされたのか、<xref:System.Windows.Forms.TreeViewEventArgs>クラスは、イベントに関連するデータが含まれています。  
  
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
    >  代わりに、使用することができます、<xref:System.Windows.Forms.MouseEventArgs>の<xref:System.Windows.Forms.Control.MouseDown>または<xref:System.Windows.Forms.Control.MouseUp>取得するイベント、<xref:System.Drawing.Point.X%2A>と<xref:System.Drawing.Point.Y%2A>座標の値、<xref:System.Drawing.Point>クリックが発生します。 次に、使用、<xref:System.Windows.Forms.TreeView>コントロールの<xref:System.Windows.Forms.TreeView.GetNodeAt%2A>クリックしてされたノードを調べます。  
  
## <a name="see-also"></a>参照  
 [TreeView コントロール](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)
