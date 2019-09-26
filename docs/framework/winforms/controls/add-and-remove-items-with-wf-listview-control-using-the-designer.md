---
title: '方法: デザイナーで Windows フォーム ListView コントロールを使って項目を追加および削除する'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], populating
- ListView control [Windows Forms], adding list items
ms.assetid: 217611ee-fd11-4d39-9a54-a37c3e781be1
ms.openlocfilehash: 62665746ea9fcd1553717b02b1f1349dc6415ab2
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/25/2019
ms.locfileid: "69040084"
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control-using-the-designer"></a>方法: デザイナーで Windows フォーム ListView コントロールを使って項目を追加および削除する

項目を Windows フォーム<xref:System.Windows.Forms.ListView>コントロールに追加するプロセスは、主に項目を指定し、その項目にプロパティを割り当てることによって構成されます。 リスト項目の追加または削除は、いつでも行うことができます。

次の手順では、 <xref:System.Windows.Forms.ListView>コントロールを含むフォームを含む**Windows アプリケーション**プロジェクトが必要です。 このようなプロジェクトの設定の詳細につい[ては、「方法:Windows フォームアプリケーションプロジェクト](/visualstudio/ide/step-1-create-a-windows-forms-application-project)を作成し[、次の操作を行います。Windows フォーム](how-to-add-controls-to-windows-forms.md)にコントロールを追加します。

### <a name="to-add-or-remove-items-using-the-designer"></a>デザイナーを使用して項目を追加または削除するには

1. <xref:System.Windows.Forms.ListView> コントロールを選択します。

2. **[プロパティ]** ウィンドウで、プロパティの横![に**ある省略記号 (省略**記号ボタン ([...])](./media/visual-studio-ellipsis-button.png)をクリックして、 <xref:System.Windows.Forms.ListView.Items%2A>プロパティの横にある [プロパティウィンドウ] ボタンをクリックします。

     **ListViewItem Collection エディター**が表示されます。

3. 項目を追加するには、 **[追加]** ボタンをクリックします。 その後、プロパティ<xref:System.Windows.Forms.ListView.Text%2A>や<xref:System.Windows.Forms.ListViewItem.ImageIndex%2A>プロパティなど、新しい項目のプロパティを設定できます。

4. 項目を削除するには、項目を選択し、 **[削除]** ボタンをクリックします。

## <a name="see-also"></a>関連項目

- [ListView コントロールの概要](listview-control-overview-windows-forms.md)
- [方法: Windows フォーム ListView コントロールに列を追加する](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [方法: Windows フォーム ListView コントロールを使用して列にサブ項目を表示する](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [方法: Windows フォーム ListView コントロールのアイコンを表示する](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [方法: TreeView コントロールまたは ListView コントロールにカスタム情報を追加する (Windows フォーム)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [方法: Windows フォーム ListView コントロールの項目をグループ化する](how-to-group-items-in-a-windows-forms-listview-control.md)
