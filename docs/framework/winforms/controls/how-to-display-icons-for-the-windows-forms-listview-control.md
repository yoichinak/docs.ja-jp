---
title: '方法: Windows フォーム ListView コントロールのアイコンを表示する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView control [Windows Forms], displaying icons
- icons [Windows Forms], displaying for ListView controls
- lists [Windows Forms], displaying icons
- ImageList component [Windows Forms], with ListView control
- list views [Windows Forms], displaying icons
ms.assetid: 9d577542-8595-429b-99e5-078770ec9d35
ms.openlocfilehash: 8e4ae744eecbe894767114179dd63651828b191b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59318612"
---
# <a name="how-to-display-icons-for-the-windows-forms-listview-control"></a>方法: Windows フォーム ListView コントロールのアイコンを表示する
Windows フォーム<xref:System.Windows.Forms.ListView>コントロールは、次の 3 つのイメージ リストのアイコンを表示できます。 リスト、詳細、および SmallIcon ビューが指定されているイメージの一覧からイメージを表示、<xref:System.Windows.Forms.ListView.SmallImageList%2A>プロパティ。 LargeIcon ビューが指定されているイメージの一覧の画像を表示、<xref:System.Windows.Forms.ListView.LargeImageList%2A>プロパティ。 リスト ビューは、追加で設定アイコンのセットを表示できます、<xref:System.Windows.Forms.ListView.StateImageList%2A>大きいアイコンまたは小さいアイコンの横にあるプロパティ。 イメージ リストの詳細については、次を参照してください。 [ImageList コンポーネント](imagelist-component-windows-forms.md)と[方法。追加または削除のイメージで、Windows フォームの ImageList コンポーネント](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md)します。  
  
### <a name="to-display-images-in-a-list-view"></a>リスト ビューでイメージを表示するには  
  
1. 適切なプロパティを設定 —<xref:System.Windows.Forms.ListView.SmallImageList%2A>、 <xref:System.Windows.Forms.ListView.LargeImageList%2A>、または<xref:System.Windows.Forms.ListView.StateImageList%2A>— 既存<xref:System.Windows.Forms.ImageList>コンポーネントを使用します。  
  
     デザイナーの [プロパティ] ウィンドウまたはコードでは、これらのプロパティを設定できます。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#41)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#41)]  
  
2. 設定、<xref:System.Windows.Forms.ListViewItem.ImageIndex%2A>または<xref:System.Windows.Forms.ListViewItem.StateImageIndex%2A>アイコンが関連付けられている各リスト項目のプロパティ。  
  
     コードでは、または、これらのプロパティを設定できる、 **ListViewItem コレクション エディター**します。 開くには、 **ListViewItem コレクション エディター**、省略記号ボタンをクリックします (![VisualStudioEllipsesButton スクリーン ショット](../media/vbellipsesbutton.png "vbEllipsesButton"))、の横にある<xref:System.Windows.Forms.ListView.Items%2A>プロパティを**プロパティ**ウィンドウ。  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#42)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#42)]  
  
## <a name="see-also"></a>関連項目

- [ListView コントロールの概要](listview-control-overview-windows-forms.md)
- [方法: Windows フォーム ListView コントロールで項目を追加および削除する](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [方法: Windows フォーム ListView コントロールに列を追加する](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [方法: TreeView コントロールまたは ListView コントロール (Windows フォーム) にカスタム情報を追加する](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [ImageList コンポーネント](imagelist-component-windows-forms.md)
