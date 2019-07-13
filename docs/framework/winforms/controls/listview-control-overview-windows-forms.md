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
ms.openlocfilehash: a60c415427a1be994f8081725f20e867dca66aa1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012803"
---
# <a name="listview-control-overview-windows-forms"></a>ListView コントロールの概要 (Windows フォーム)
Windows フォーム <xref:System.Windows.Forms.ListView> コントロールにはアイコン表示で項目の一覧が表示されます。 リスト ビューを使用すると、Windows エクスプローラーの右側のペインのようなユーザー インターフェイスを作成することができます。 コントロールでは、次の 4 つの表示モードがあります。LargeIcon、SmallIcon、リスト、および詳細。  
  
## <a name="what-you-can-do-with-the-listview-control"></a>ListView コントロールで行うことができます。  
  
> [!NOTE]
>  追加の表示モード、タイルには、Windows XP と Windows Server 2003 オペレーティング システムのできるだけです。 詳細については、「[方法 :Windows で有効にする並べて表示ビュー フォーム ListView コントロール](how-to-enable-tile-view-in-a-windows-forms-listview-control.md)します。  
  
 LargeIcon モードは、項目のテキストの横にある大きいアイコンを表示します。項目は、コントロールが十分な大きさの場合に、複数の列に表示されます。 SmallIcon モードでは、小さいアイコンが表示される点を除いて同じです。 リスト モードでは、小さいアイコンが表示されますは、常に 1 つの列。 詳細モードでは、複数の列の項目が表示されます。 詳細については、「[方法: 列を Windows フォーム ListView コントロールを追加する](how-to-add-columns-to-the-windows-forms-listview-control.md)します。 表示モードはによって決定されます、<xref:System.Windows.Forms.ListView.View%2A>プロパティ。 イメージ リストのイメージ ビュー モードをすべて表示できます。 詳細については、「[方法: Windows フォーム ListView コントロール アイコンを表示](how-to-display-icons-for-the-windows-forms-listview-control.md)します。  
  
 次の表の一覧、<xref:System.Windows.Forms.ListView>メンバーと、ビューで有効です。  
  
|ListView のメンバー|表示|  
|---------------------|----------|  
|<xref:System.Windows.Forms.ListView.Alignment%2A> プロパティ|<xref:System.Windows.Forms.View.SmallIcon> または <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.AutoArrange%2A> プロパティ|<xref:System.Windows.Forms.View.SmallIcon> または <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.AutoResizeColumn%2A> メソッド|<xref:System.Windows.Forms.View.Details>|  
|<xref:System.Windows.Forms.ListView.Columns%2A> プロパティ|<xref:System.Windows.Forms.View.Details> または <xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.DrawSubItem> イベント|<xref:System.Windows.Forms.View.Details>|  
|<xref:System.Windows.Forms.ListView.FindItemWithText%2A> メソッド|<xref:System.Windows.Forms.View.Details>、 <xref:System.Windows.Forms.View.List>、または <xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.FindNearestItem%2A> メソッド|<xref:System.Windows.Forms.View.SmallIcon> または <xref:System.Windows.Forms.View.LargeIcon>|  
|<xref:System.Windows.Forms.ListView.GetItemAt%2A> メソッド|<xref:System.Windows.Forms.View.Details> または <xref:System.Windows.Forms.View.Tile>|  
|<xref:System.Windows.Forms.ListView.Groups%2A> プロパティ|除くすべてのビュー <xref:System.Windows.Forms.View.List>|  
|<xref:System.Windows.Forms.ListView.HeaderStyle%2A> プロパティ|<xref:System.Windows.Forms.View.Details>。|  
|<xref:System.Windows.Forms.ListView.InsertionMark%2A> プロパティ|<xref:System.Windows.Forms.View.LargeIcon>、 <xref:System.Windows.Forms.View.SmallIcon>、または <xref:System.Windows.Forms.View.Tile>|  
  
 キー プロパティ、<xref:System.Windows.Forms.ListView>コントロールが<xref:System.Windows.Forms.ListView.Items%2A>、コントロールによって表示される項目が含まれています。 <xref:System.Windows.Forms.ListView.SelectedItems%2A>プロパティには、コントロールで現在選択されている項目のコレクションが含まれています。 ユーザーがドラッグし、その場合は、別のコントロールには、一度に複数の項目を削除する例については、複数の項目を選択、<xref:System.Windows.Forms.ListView.MultiSelect%2A>プロパティに設定されて`true`します。 <xref:System.Windows.Forms.ListView>場合、コントロールは、項目の横にあるチェック ボックスを表示できます、<xref:System.Windows.Forms.ListView.CheckBoxes%2A>プロパティに設定されて`true`します。  
  
 <xref:System.Windows.Forms.ListView.Activation%2A>プロパティは、アクションの種類、ユーザーは、リスト内の項目をアクティブにするため必要がありますを決定します。 オプションは<xref:System.Windows.Forms.ItemActivation.Standard>、 <xref:System.Windows.Forms.ItemActivation.OneClick>、と<xref:System.Windows.Forms.ItemActivation.TwoClick>。 <xref:System.Windows.Forms.ItemActivation.OneClick> アクティブ化では、1 回のクリック、項目をアクティブ化する必要があります。 <xref:System.Windows.Forms.ItemActivation.TwoClick> アクティブ化が、ユーザーをダブルクリックすると、アイテムをアクティブ化が必要です。1 回のクリックでは、項目のテキストの色を変更します。 <xref:System.Windows.Forms.ItemActivation.Standard> アクティブ化をダブルクリックすると、項目をアクティブ化ユーザーが必要ですが、項目の外観は変わりません。  
  
 <xref:System.Windows.Forms.ListView>コントロールもサポートしています、スタイルとその他の機能の使用可能なグループ化、並べて表示ビュー、および挿入マークを含む、Windows XP のプラットフォームで。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ListView>
- [ListView コントロール](listview-control-windows-forms.md)
- [方法: Windows フォーム ListView コントロールで項目追加および削除](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [方法: Windows フォーム ListView コントロールに列を追加します。](how-to-add-columns-to-the-windows-forms-listview-control.md)
- [方法: Windows フォーム ListView コントロールのアイコンを表示します。](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [方法: Windows フォーム ListView コントロールでの列にサブ項目を表示](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [方法: Windows フォーム ListView コントロールで項目を選択します。](how-to-select-an-item-in-the-windows-forms-listview-control.md)
- [方法: Windows フォーム ListView コントロールに項目をグループ化](how-to-group-items-in-a-windows-forms-listview-control.md)
- [方法: Windows フォーム ListView コントロールに挿入マークを表示します。](how-to-display-an-insertion-mark-in-a-windows-forms-listview-control.md)
- [方法: ListView コントロールに検索機能を追加します。](how-to-add-search-capabilities-to-a-listview-control.md)
- [方法: TreeView コントロールまたは ListView コントロール (Windows フォーム) にカスタム情報を追加します。](add-custom-information-to-a-treeview-or-listview-control-wf.md)
- [方法: Windows フォームでマルチペイン ユーザー インターフェイスを作成します。](how-to-create-a-multipane-user-interface-with-windows-forms.md)
