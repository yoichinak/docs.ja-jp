---
title: ListView コントロールの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- ListView
helpviewer_keywords:
- lists
- ListView control [Windows Forms], about ListView control
- list views
ms.assetid: c9ef56c1-3bb1-4101-9f4e-e95e720f2756
ms.openlocfilehash: 7b7eac942a7e857ad731c0f77389e84aee287c08
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952162"
---
# <a name="listview-control-overview-windows-forms"></a>ListView コントロールの概要 (Windows フォーム)
Windows フォーム <xref:System.Windows.Forms.ListView> コントロールにはアイコン表示で項目の一覧が表示されます。 リスト ビューを使用すると、Windows エクスプローラーの右側のペインのようなユーザー インターフェイスを作成することができます。 このコントロールには、次の4つの表示モードがあります。LargeIcon、SmallIcon、List、および Details。  
  
## <a name="what-you-can-do-with-the-listview-control"></a>ListView コントロールでできること  
  
> [!NOTE]
> 追加の表示モードであるタイルは、Windows XP と Windows Server 2003 オペレーティングシステムでのみ使用できます。 詳細については、「[方法 :Windows フォーム ListView コントロール](how-to-enable-tile-view-in-a-windows-forms-listview-control.md)でタイルビューを有効にします。  
  
 LargeIcon モードでは、項目のテキストの横に大きいアイコンが表示されます。コントロールのサイズが十分な場合、項目は複数の列に表示されます。 SmallIcon モードは、小さいアイコンを表示する点を除いて同じです。 リストモードでは小さいアイコンが表示されますが、常に1つの列に表示されます。 詳細モードでは、複数の列に項目が表示されます。 詳細については、「[方法: Windows フォーム ListView コントロール](how-to-add-columns-to-the-windows-forms-listview-control.md)に列を追加します。 ビューモードは、 <xref:System.Windows.Forms.ListView.View%2A>プロパティによって決定されます。 すべての表示モードでは、イメージリストのイメージを表示できます。 詳細については、「[方法: Windows フォーム ListView コントロール](how-to-display-icons-for-the-windows-forms-listview-control.md)のアイコンを表示します。  
  
 次の表に、で有効<xref:System.Windows.Forms.ListView>なメンバーとビューの一部を示します。  
  
|ListView メンバー|表示|  
|---------------------|----------|  
|<xref:System.Windows.Forms.ListView.Alignment%2A> プロパティ|<xref:System.Windows.Forms.View.SmallIcon> または <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.AutoArrange%2A> プロパティ|<xref:System.Windows.Forms.View.SmallIcon> または <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.AutoResizeColumn%2A> メソッド|<xref:System.Windows.Forms.View.Details>|  
|<xref:System.Windows.Forms.ListView.Columns%2A> プロパティ|<xref:System.Windows.Forms.View.Details> または <xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.DrawSubItem> イベント|<xref:System.Windows.Forms.View.Details>|  
|<xref:System.Windows.Forms.ListView.FindItemWithText%2A> メソッド|<xref:System.Windows.Forms.View.Details>、 <xref:System.Windows.Forms.View.List>、または <xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.FindNearestItem%2A> メソッド|<xref:System.Windows.Forms.View.SmallIcon> または <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.GetItemAt%2A> メソッド|<xref:System.Windows.Forms.View.Details> または <xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.Groups%2A> プロパティ|を除くすべてのビュー<xref:System.Windows.Forms.View.List>|  
|<xref:System.Windows.Forms.ListView.HeaderStyle%2A> プロパティ|<xref:System.Windows.Forms.View.Details>。|  
|<xref:System.Windows.Forms.ListView.InsertionMark%2A> プロパティ|<xref:System.Windows.Forms.View.LargeIcon>、 <xref:System.Windows.Forms.View.SmallIcon>、または <xref:System.Windows.Forms.View.Tile>|  
  
 <xref:System.Windows.Forms.ListView>コントロールのキープロパティは<xref:System.Windows.Forms.ListView.Items%2A>で、コントロールによって表示される項目が含まれています。 プロパティ<xref:System.Windows.Forms.ListView.SelectedItems%2A>は、コントロールで現在選択されている項目のコレクションを格納します。 ユーザーは複数の項目を選択できます。たとえば、 <xref:System.Windows.Forms.ListView.MultiSelect%2A>プロパティがに`true`設定されている場合は、別のコントロールに一度に複数の項目をドラッグアンドドロップすることができます。 コントロール<xref:System.Windows.Forms.ListView>は、 <xref:System.Windows.Forms.ListView.CheckBoxes%2A>プロパティがに`true`設定されている場合、項目の横にチェックボックスを表示できます。  
  
 プロパティ<xref:System.Windows.Forms.ListView.Activation%2A>は、リスト内の項目をアクティブにするためにユーザーが実行する必要のあるアクションの<xref:System.Windows.Forms.ItemActivation.Standard>種類を決定<xref:System.Windows.Forms.ItemActivation.TwoClick>します。オプションは、 <xref:System.Windows.Forms.ItemActivation.OneClick>、、およびです。 <xref:System.Windows.Forms.ItemActivation.OneClick>アクティブ化を行うには、1回のクリックで項目をアクティブ化する必要があります。 <xref:System.Windows.Forms.ItemActivation.TwoClick>ライセンス認証を行うには、ユーザーがダブルクリックして項目をアクティブにする必要があります。1回のクリックで、項目のテキストの色を変更します。 <xref:System.Windows.Forms.ItemActivation.Standard>アクティブ化を行うには、ユーザーがダブルクリックして項目をアクティブにする必要がありますが、項目は外観を変更しません。  
  
 <xref:System.Windows.Forms.ListView>コントロールでは、Windows XP プラットフォームで使用できる視覚スタイルやその他の機能 (グループ化、タイルビュー、挿入マークなど) もサポートされています。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ListView>
- [ListView コントロール](listview-control-windows-forms.md)
- [方法: Windows フォーム ListView コントロールを使用して項目を追加および削除する](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [方法: Windows フォーム ListView コントロールに列を追加する](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [方法: Windows フォーム ListView コントロールのアイコンを表示する](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [方法: Windows フォーム ListView コントロールを使用して列にサブ項目を表示する](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [方法: Windows フォーム ListView コントロール内の項目を選択します](how-to-select-an-item-in-the-windows-forms-listview-control.md)
- [方法: Windows フォーム ListView コントロールの項目をグループ化する](how-to-group-items-in-a-windows-forms-listview-control.md)
- [方法: Windows フォーム ListView コントロールに挿入マークを表示する](how-to-display-an-insertion-mark-in-a-windows-forms-listview-control.md)
- [方法: ListView コントロールに検索機能を追加する](how-to-add-search-capabilities-to-a-listview-control.md)
- [方法: TreeView コントロールまたは ListView コントロールにカスタム情報を追加する (Windows フォーム)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [方法: Windows フォームを使用してマルチペインユーザーインターフェイスを作成する](how-to-create-a-multipane-user-interface-with-windows-forms.md)
