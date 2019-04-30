---
title: TreeView コントロールの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- TreeView
helpviewer_keywords:
- TreeView control [Windows Forms], about TreeView control
ms.assetid: 0ece823a-9508-478a-bbdb-7d7c3bae51d5
ms.openlocfilehash: 046713745e7de18cefe5b4883af73034af2cfb31
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009228"
---
# <a name="treeview-control-overview-windows-forms"></a>TreeView コントロールの概要 (Windows フォーム)

Windows フォームの <xref:System.Windows.Forms.TreeView> コントロールでは、Windows オペレーティング システムの Windows エクスプローラーの左側のウィンドウにファイルやフォルダーが表示されるのと同じように、ノードの階層をユーザーに表示することができます。 ツリー ビュー内の各ノードと呼ばれるその他のノードを含む可能性があります*子ノード*します。 親ノード、または子ノードを含むノードを展開または折りたたんで表示できます。 また、ツリー ビューの <xref:System.Windows.Forms.TreeView.CheckBoxes%2A> プロパティを `true` に設定することで、ノードの横にチェック ボックスがあるツリー ビューを表示することもできます。 ノードの <xref:System.Windows.Forms.TreeNode.Checked%2A> プロパティを `true` または `false` に設定することにより、プログラムでノードをオンまたはオフにすることができます。

## <a name="key-properties"></a>キー プロパティ

<xref:System.Windows.Forms.TreeView> コントロールの主要プロパティは、<xref:System.Windows.Forms.TreeView.Nodes%2A> および <xref:System.Windows.Forms.TreeView.SelectedNode%2A> です。 <xref:System.Windows.Forms.TreeView.Nodes%2A> プロパティには、ツリー ビューの最上位のノードの一覧が含まれています。 <xref:System.Windows.Forms.TreeView.SelectedNode%2A> プロパティは、現在選択されているノードを設定します。 ノードの横にあるアイコンを表示することができます。 コントロールはツリー ビューの <xref:System.Windows.Forms.TreeView.ImageList%2A> プロパティで <xref:System.Windows.Forms.ImageList> という名前のイメージを使用します。 <xref:System.Windows.Forms.TreeView.ImageIndex%2A> プロパティは、ツリー ビューでノードの既定のイメージを設定します。 イメージを表示する方法の詳細については、次を参照してください。[方法。Windows フォーム TreeView コントロール アイコンを設定](how-to-set-icons-for-the-windows-forms-treeview-control.md)します。 使用できる標準のイメージの大規模なライブラリにアクセス権がある Visual Studio 2005 を使用している場合、<xref:System.Windows.Forms.TreeView>コントロール。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.TreeView>
- [TreeView コントロール](treeview-control-windows-forms.md)
- [方法: Windows フォーム TreeView コントロールのアイコンを設定します。](how-to-set-icons-for-the-windows-forms-treeview-control.md)
- [方法: 追加して、Windows フォーム TreeView コントロールでノードを削除](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [方法: Windows フォーム TreeView コントロールのすべてのノードを反復処理します。](how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)
- [方法: クリックしてされた TreeView ノードを決定します。](how-to-determine-which-treeview-node-was-clicked-windows-forms.md)
- [方法: TreeView コントロールまたは ListView コントロール (Windows フォーム) にカスタム情報を追加します。](add-custom-information-to-a-treeview-or-listview-control-wf.md)