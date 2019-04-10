---
title: '方法: Windows フォーム TreeView コントロールのすべてのノードを反復処理する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], iterating through nodes
- tree nodes in TreeView control [Windows Forms], iterating through
ms.assetid: 427f8928-ebcf-4beb-887f-695b905d5134
ms.openlocfilehash: 4b287cecddd63ec6535feb70118c3466c8960531
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59314231"
---
# <a name="how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control"></a>方法: Windows フォーム TreeView コントロールのすべてのノードを反復処理する
Windows フォーム内の各ノードをチェックすると役立つ場合があります<xref:System.Windows.Forms.TreeView>ノード値にいくつかの計算を実行するために制御します。 この操作は、ツリーの各コレクションの各ノードを反復処理する再帰プロシージャ (C# および C++ の場合は再帰メソッド) を使用して実行できます。  
  
 各<xref:System.Windows.Forms.TreeNode>ツリー ビュー内のオブジェクトがツリー ビュー内を移動する際のプロパティ: <xref:System.Windows.Forms.TreeNode.FirstNode%2A>、 <xref:System.Windows.Forms.TreeNode.LastNode%2A>、 <xref:System.Windows.Forms.TreeNode.NextNode%2A>、 <xref:System.Windows.Forms.TreeNode.PrevNode%2A>、および<xref:System.Windows.Forms.TreeNode.Parent%2A>します。 値、<xref:System.Windows.Forms.TreeNode.Parent%2A>プロパティの現在のノードの親ノードです。 現在のノードの子ノードは、いずれかを使用する必要がある場合に表示されます、<xref:System.Windows.Forms.TreeNode.Nodes%2A>プロパティ。 <xref:System.Windows.Forms.TreeView>コントロール自体には、<xref:System.Windows.Forms.TreeView.TopNode%2A>プロパティで、全体のツリー ビューのルート ノードです。  
  
### <a name="to-iterate-through-all-nodes-of-the-treeview-control"></a>TreeView コントロールのすべてのノードを反復処理するには  
  
1. 各ノードをテストする再帰プロシージャ (C# および C++ における再帰メソッド) を作成します。  
  
2. プロシージャを呼び出します。  
  
     次の例は、それぞれを印刷する方法を示しています。<xref:System.Windows.Forms.TreeNode>オブジェクトの<xref:System.Windows.Forms.TreeNode.Text%2A>プロパティ。  
  
    ```vb  
    Private Sub PrintRecursive(ByVal n As TreeNode)  
       System.Diagnostics.Debug.WriteLine(n.Text)  
       MessageBox.Show(n.Text)  
       Dim aNode As TreeNode  
       For Each aNode In n.Nodes  
          PrintRecursive(aNode)  
       Next  
    End Sub  
  
    ' Call the procedure using the top nodes of the treeview.  
    Private Sub CallRecursive(ByVal aTreeView As TreeView)  
       Dim n As TreeNode  
       For Each n In aTreeView.Nodes  
          PrintRecursive(n)  
       Next  
    End Sub  
    ```  
  
    ```csharp  
    private void PrintRecursive(TreeNode treeNode)  
    {  
       // Print the node.  
       System.Diagnostics.Debug.WriteLine(treeNode.Text);  
       MessageBox.Show(treeNode.Text);  
       // Print each node recursively.  
       foreach (TreeNode tn in treeNode.Nodes)  
       {  
          PrintRecursive(tn);  
       }  
    }  
  
    // Call the procedure using the TreeView.  
    private void CallRecursive(TreeView treeView)  
    {  
       // Print each node recursively.  
       TreeNodeCollection nodes = treeView.Nodes;  
       foreach (TreeNode n in nodes)  
       {  
          PrintRecursive(n);  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void PrintRecursive( TreeNode^ treeNode )  
       {  
          // Print the node.  
          System::Diagnostics::Debug::WriteLine( treeNode->Text );  
          MessageBox::Show( treeNode->Text );  
  
          // Print each node recursively.  
          System::Collections::IEnumerator^ myNodes = (safe_cast<System::Collections::IEnumerable^>(treeNode->Nodes))->GetEnumerator();  
          try  
          {  
             while ( myNodes->MoveNext() )  
             {  
                TreeNode^ tn = safe_cast<TreeNode^>(myNodes->Current);  
                PrintRecursive( tn );  
             }  
          }  
          finally  
          {  
             IDisposable^ disposable = dynamic_cast<System::IDisposable^>(myNodes);  
             if ( disposable != nullptr )  
                      disposable->Dispose();  
          }  
       }  
  
       // Call the procedure using the TreeView.  
       void CallRecursive( TreeView^ treeView )  
       {  
          // Print each node recursively.  
          TreeNodeCollection^ nodes = treeView->Nodes;  
          System::Collections::IEnumerator^ myNodes = (safe_cast<System::Collections::IEnumerable^>(nodes))->GetEnumerator();  
          try  
          {  
             while ( myNodes->MoveNext() )  
             {  
                TreeNode^ n = safe_cast<TreeNode^>(myNodes->Current);  
                PrintRecursive( n );  
             }  
          }  
          finally  
          {  
             IDisposable^ disposable = dynamic_cast<System::IDisposable^>(myNodes);  
             if ( disposable != nullptr )  
                      disposable->Dispose();  
          }  
       }  
    ```  
  
## <a name="see-also"></a>関連項目

- [TreeView コントロール](treeview-control-windows-forms.md)
- [再帰プロシージャ](~/docs/visual-basic/programming-guide/language-features/procedures/recursive-procedures.md)
