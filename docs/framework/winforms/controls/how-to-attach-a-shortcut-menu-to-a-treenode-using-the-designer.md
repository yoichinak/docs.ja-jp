---
title: '方法: デザイナーを使用して TreeNode にショートカット メニューを割り当てる'
ms.date: 03/30/2017
helpviewer_keywords:
- shortcut menus [Windows Forms], attaching to TreeNodes
- TreeNode [Windows Forms], attaching a shortcut menu using Designer
ms.assetid: 8e45e184-1313-4f8f-90ff-2cd5789b2268
ms.openlocfilehash: eb3240d35309e03aa8ce949b9c5000f8581d2c2f
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040456"
---
# <a name="how-to-attach-a-shortcut-menu-to-a-treenode-using-the-designer"></a>方法: デザイナーを使用して TreeNode にショートカット メニューを割り当てる
Windows フォーム<xref:System.Windows.Forms.TreeView>コントロールは、windows オペレーティングシステムの windows エクスプローラー機能の左ペインに表示されるファイルやフォルダーと同様に、ノードの階層を表示します。 <xref:System.Windows.Forms.Control.ContextMenuStrip%2A>プロパティを設定することにより、ユーザーが<xref:System.Windows.Forms.TreeView>コントロールを右クリックしたときに、状況に応じた操作をユーザーに提供できます。 コンポーネントを<xref:System.Windows.Forms.ContextMenuStrip>個々<xref:System.Windows.Forms.TreeNode>のアイテムに関連付けることにより、カスタマイズされたレベルの<xref:System.Windows.Forms.TreeView>ショートカットメニュー機能をコントロールに追加できます。

## <a name="to-associate-a-shortcut-menu-with-a-treenode-at-design-time"></a>デザイン時にショートカットメニューを TreeNode に関連付けるには

1. フォームに<xref:System.Windows.Forms.TreeView>コントロールを追加し、必要に応じてにノードを追加します。 <xref:System.Windows.Forms.TreeView> 詳細については、「[方法 :Windows フォーム TreeView コントロール](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)を使用してノードを追加および削除します。

2. フォームに<xref:System.Windows.Forms.ContextMenuStrip>コンポーネントを追加し、実行時に使用できるようにするノードレベルの操作を表すメニュー項目をショートカットメニューに追加します。 詳細については、「[方法 :ContextMenuStrip](how-to-add-menu-items-to-a-contextmenustrip.md)にメニュー項目を追加します。

3. <xref:System.Windows.Forms.TreeView>コントロールの **[TreeNodeEditor]** ダイアログボックスを再び開き、編集するノードを選択し、 <xref:System.Windows.Forms.ContextMenuStrip>プロパティを追加したショートカットメニューに設定します。

4. このプロパティを設定すると、ノードを右クリックしたときにショートカットメニューが表示されます。

     また、これらのメニュー項目の<xref:System.Windows.Forms.ToolStripItem.Click>イベントを処理するコードを記述することもできます。

## <a name="see-also"></a>関連項目

- [TreeView コントロール](treeview-control-windows-forms.md)
- [TreeView コントロールの概要](treeview-control-overview-windows-forms.md)
- [ContextMenuStrip コントロール](contextmenustrip-control.md)
