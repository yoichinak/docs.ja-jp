---
title: '方法: デザイナーで Windows フォーム TreeView コントロールを使ってノードを追加および削除する'
ms.date: 03/30/2017
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
ms.openlocfilehash: ef3a963b5621f0b972b02a007681f600fbdb1050
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/25/2019
ms.locfileid: "69040072"
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control-using-the-designer"></a>方法: デザイナーで Windows フォーム TreeView コントロールを使ってノードを追加および削除する

Windows フォーム<xref:System.Windows.Forms.TreeView>コントロールではノードが階層構造で表示されるため、ノードを追加するときは、その親ノードに注意する必要があります。

次の手順では、 <xref:System.Windows.Forms.TreeView>コントロールを含むフォームを含む**Windows アプリケーション**プロジェクトが必要です。 このようなプロジェクトの設定の詳細につい[ては、「方法:Windows フォームアプリケーションプロジェクト](/visualstudio/ide/step-1-create-a-windows-forms-application-project)を作成し[、次の操作を行います。Windows フォーム](how-to-add-controls-to-windows-forms.md)にコントロールを追加します。

### <a name="to-add-or-remove-nodes-in-the-designer"></a>デザイナーでノードを追加または削除するには

1. <xref:System.Windows.Forms.TreeView> コントロールを選択します。

2. **[プロパティ]** ウィンドウで、プロパティの横![に**ある省略記号 (省略**記号ボタン ([...])](./media/visual-studio-ellipsis-button.png)をクリックして、 <xref:System.Windows.Forms.TreeView.Nodes%2A>プロパティの横にある [プロパティウィンドウ] ボタンをクリックします。

     **TreeNode エディター**が表示されます。

3. ノードを追加するには、ルートノードが存在している必要があります。存在しない場合は、まず **[ルートの追加]** ボタンをクリックしてルートを追加する必要があります。 その後、ルートまたは他の任意のノードを選択し、 **[子の追加]** ボタンをクリックして、子ノードを追加できます。

4. ノードを削除するには、削除するノードを選択し、 **[削除]** ボタンをクリックします。

## <a name="see-also"></a>関連項目

- [TreeView コントロール](treeview-control-windows-forms.md)
- [TreeView コントロールの概要](treeview-control-overview-windows-forms.md)
- [方法: Windows フォーム TreeView コントロールのアイコンを設定する](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [方法: Windows フォーム TreeView コントロールのすべてのノードを反復処理します。](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [方法: クリックされた TreeView ノードを確認する](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [方法: TreeView コントロールまたは ListView コントロールにカスタム情報を追加する (Windows フォーム)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
