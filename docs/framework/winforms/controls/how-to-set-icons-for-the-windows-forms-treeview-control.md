---
title: '方法: Windows フォーム TreeView コントロールのアイコンを設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], node icons
- ImageList component [Windows Forms], adding images
- icons [Windows Forms], setting for TreeView control
- tree nodes in TreeView control [Windows Forms], icons
ms.assetid: c14ddcc0-e5a6-4c21-a2d5-6799fd491781
ms.openlocfilehash: 451f9ab2b35ad1fbbe9401dacbc8aab44e302701
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69909806"
---
# <a name="how-to-set-icons-for-the-windows-forms-treeview-control"></a>方法: Windows フォーム TreeView コントロールのアイコンを設定する
Windows フォーム<xref:System.Windows.Forms.TreeView>コントロールでは、各ノードの横にアイコンを表示できます。 アイコンがノードテキストのすぐ左に配置されます。 これらのアイコンを表示するには、ツリービューを<xref:System.Windows.Forms.ImageList>コントロールに関連付ける必要があります。 イメージリストの詳細については、「 [ImageList コンポーネント](imagelist-component-windows-forms.md)」および[「方法:Windows フォーム ImageList コンポーネント](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)を使用してイメージを追加または削除します。  
  
> [!NOTE]
> Microsoft .NET Framework バージョン1.1 のバグにより、アプリケーションがを<xref:System.Windows.Forms.TreeView>呼び出す<xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>ときに、イメージがノードに表示されないようにすることができます。 このバグを回避するには<xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> 、を`Main`呼び出し<xref:System.Windows.Forms.Application.EnableVisualStyles%2A>た直後にメソッドでを呼び出します。 このバグは .NET Framework 2.0 で修正されています。  
  
### <a name="to-display-images-in-a-tree-view"></a>ツリービューでイメージを表示するには  
  
1. コントロールの<xref:System.Windows.Forms.TreeView.ImageList%2A>プロパティを、使用する既存<xref:System.Windows.Forms.ImageList>のコントロールに設定します。 <xref:System.Windows.Forms.TreeView>  
  
     これらのプロパティは、デザイナーでプロパティウィンドウまたはコードで設定できます。  
  
    ```vb  
    TreeView1.ImageList = ImageList1  
    ```  
  
    ```csharp  
    treeView1.ImageList = imageList1;  
    ```  
  
    ```cpp  
    treeView1->ImageList = imageList1;  
    ```  
  
2. ノードの<xref:System.Windows.Forms.TreeNode.ImageIndex%2A>プロパティと<xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A>プロパティを設定します。 プロパティ<xref:System.Windows.Forms.TreeNode.ImageIndex%2A>は、ノードの通常の状態と展開された状態に表示さ<xref:System.Windows.Forms.TreeNode.SelectedImageIndex%2A>れるイメージを決定し、プロパティはノードの選択された状態に表示されるイメージを決定します。  
  
     これらのプロパティは、コードで設定することも、TreeNode エディター内で設定することもできます。 TreeNode エディターを開くには、プロパティウィンドウのプロパティの![ <xref:System.Windows.Forms.TreeView.Nodes%2A>横にある省略記号ボタン ([...] プロパティウィンドウ](./media/visual-studio-ellipsis-button.png)) をクリックします。  
  
    ```vb  
    ' (Assumes that ImageList1 contains at least two images and  
    ' the TreeView control contains a selected image.)  
    TreeView1.SelectedNode.ImageIndex = 0  
    TreeView1.SelectedNode.SelectedImageIndex = 1  
    ```  
  
    ```csharp  
    // (Assumes that imageList1 contains at least two images and  
    // the TreeView control contains a selected image.)  
    treeView1.SelectedNode.ImageIndex = 0;  
    treeView1.SelectedNode.SelectedImageIndex = 1;  
    ```  
  
    ```cpp  
    // (Assumes that imageList1 contains at least two images and  
    // the TreeView control contains a selected image.)  
    treeView1->SelectedNode->ImageIndex = 0;  
    treeView1->SelectedNode->SelectedImageIndex = 1;  
    ```  
  
## <a name="see-also"></a>関連項目

- [TreeView コントロールの概要](treeview-control-overview-windows-forms.md)
- [方法: Windows フォーム TreeView コントロールを使用してノードを追加および削除する](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [方法: Windows フォーム TreeView コントロールのすべてのノードを反復処理します。](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [方法: クリックされた TreeView ノードを確認する](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [方法: TreeView コントロールまたは ListView コントロールにカスタム情報を追加する (Windows フォーム)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
