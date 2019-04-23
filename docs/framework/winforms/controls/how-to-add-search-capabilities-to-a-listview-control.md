---
title: '方法: ListView コントロールに検索機能を追加する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- lists [Windows Forms], enabling searching
- list views [Windows Forms], enabling searching
- ListView control [Windows Forms], adding search capabilities
- searching [Windows Forms], adding search capabilities to ListView control
ms.assetid: 557782d9-b705-4bab-b496-9938afddac82
ms.openlocfilehash: d5d4dae55fc9f0613ab6535b2fe57e262d0ef141
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59314023"
---
# <a name="how-to-add-search-capabilities-to-a-listview-control"></a>方法: ListView コントロールに検索機能を追加する
内の項目の大規模な一覧を使用する場合に多くの場合、<xref:System.Windows.Forms.ListView>をユーザーに検索機能を提供するコントロール。 <xref:System.Windows.Forms.ListView>コントロールは、2 つの方法でこの機能を提供しています。 テキストに一致すると、場所を検索します。  
  
 <xref:System.Windows.Forms.ListView.FindItemWithText%2A>メソッドでは、テキスト検索を実行できます。、<xref:System.Windows.Forms.ListView>リストまたは詳細ビューで、検索文字列と省略可能な開始と終了インデックスを指定します。 これに対し、<xref:System.Windows.Forms.ListView.FindNearestItem%2A>メソッド内の項目を見つけることができます、<xref:System.Windows.Forms.ListView>アイコンまたはタイル ビューで、一連の x 座標と y 座標と検索する方向を指定します。  
  
### <a name="to-find-an-item-using-text"></a>テキストを使用して項目を検索するには  
  
1. 作成、<xref:System.Windows.Forms.ListView>で、<xref:System.Windows.Forms.ListView.View%2A>プロパティに設定<xref:System.Windows.Forms.View.Details>または<xref:System.Windows.Forms.View.List>、および設定し、<xref:System.Windows.Forms.ListView>項目を含む。  
  
2. 呼び出す、<xref:System.Windows.Forms.ListView.FindItemWithText%2A>メソッドを検索したい項目のテキストを渡します。  
  
3. 次のコード例は、基本的なを作成する方法を示します<xref:System.Windows.Forms.ListView>項目では、設定、および、ユーザーからのテキスト入力リストの項目の検索を使用しています。  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#1)]  
  
### <a name="to-find-an-item-using-x--and-y-coordinates"></a>X 座標と y 座標を使用して項目を検索するには  
  
1. 作成、<xref:System.Windows.Forms.ListView>で、<xref:System.Windows.Forms.View>プロパティに設定<xref:System.Windows.Forms.View.SmallIcon>または<xref:System.Windows.Forms.View.LargeIcon>、および設定し、<xref:System.Windows.Forms.ListView>項目を含む。  
  
2. 呼び出す、<xref:System.Windows.Forms.ListView.FindNearestItem%2A>を渡して、必要な x 座標と y 座標と方向に検索するメソッド。  
  
3. 次のコード例は、基本的なアイコンを作成する方法を示します<xref:System.Windows.Forms.ListView>、アイテム、およびキャプチャを設定、<xref:System.Windows.Forms.Control.MouseDown>上向きの方向に最も近い項目を検索するイベントです。  
  
 [!code-cpp[System.Windows.Forms.ListViewFindItems#2](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/cpp/form1.cpp#2)]
 [!code-csharp[System.Windows.Forms.ListViewFindItems#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/CS/form1.cs#2)]
 [!code-vb[System.Windows.Forms.ListViewFindItems#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewFindItems/VB/form1.vb#2)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListView.FindItemWithText%2A>
- <xref:System.Windows.Forms.ListView.FindNearestItem%2A>
- [ListView コントロール](listview-control-windows-forms.md)
- [ListView コントロールの概要](listview-control-overview-windows-forms.md)
- [方法: Windows フォーム ListView コントロールで項目追加および削除](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
