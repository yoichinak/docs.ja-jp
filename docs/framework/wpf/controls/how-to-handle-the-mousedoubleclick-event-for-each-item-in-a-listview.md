---
title: '方法: ListView の各項目の MouseDoubleClick イベントを処理する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
ms.openlocfilehash: 7e51c810a2e1e4bf4157aa1311255c5547021b60
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962063"
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a>方法: ListView の各項目の MouseDoubleClick イベントを処理する
内<xref:System.Windows.Controls.ListView>の項目のイベントを処理するには、それぞれ<xref:System.Windows.Controls.ListViewItem>にイベントハンドラーを追加する必要があります。 がデータソースにバインドされている場合、明示的に<xref:System.Windows.Controls.ListViewItem>を作成する必要はありませんが、の<xref:System.Windows.Controls.ListViewItem>スタイル<xref:System.Windows.EventSetter>にを追加することによって、各項目のイベントを処理できます。 <xref:System.Windows.Controls.ListView>  
  
## <a name="example"></a>例  
 次の例では、データバインド<xref:System.Windows.Controls.ListView>を作成し<xref:System.Windows.Style> 、を作成して、それぞれ<xref:System.Windows.Controls.ListViewItem>にイベントハンドラーを追加します。  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 次の例では<xref:System.Windows.Controls.Control.MouseDoubleClick> 、イベントを処理します。  
  
 [!code-csharp[ListViewHowTos#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
> を<xref:System.Windows.Controls.ListView>データソースにバインドするのが最も一般的ですが、を明示的に作成<xref:System.Windows.Controls.ListViewItem>するかどうかに関係なく<xref:System.Windows.Controls.ListViewItem> 、スタイルを使用して非<xref:System.Windows.Controls.ListView>データバインド内の各にイベントハンドラーを追加できます。  明示的および暗黙的に作成され<xref:System.Windows.Controls.ListViewItem>たコントロールの<xref:System.Windows.Controls.ItemsControl>詳細については、「」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Xml.XmlElement>
- [データ バインディングの概要](../data/data-binding-overview.md)
- [スタイルとテンプレート](styling-and-templating.md)
- [XMLDataProvider と XPath クエリを使用して XML データにバインドする](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [ListView の概要](listview-overview.md)
