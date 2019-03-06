---
title: '方法: ListView の各項目の MouseDoubleClick イベントを処理する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
ms.openlocfilehash: a4a93ffdf7c9cf2737c41a7fd196d8cfff716ea1
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377201"
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a>方法: ListView の各項目の MouseDoubleClick イベントを処理する
内の項目のイベントを処理するために、 <xref:System.Windows.Controls.ListView>、それぞれにイベント ハンドラーを追加する必要がある<xref:System.Windows.Controls.ListViewItem>します。 ときに、<xref:System.Windows.Controls.ListView>がバインドされているデータ ソースに明示的に作成しない、 <xref:System.Windows.Controls.ListViewItem>、追加することで各項目のイベントを処理することができますが、<xref:System.Windows.EventSetter>のスタイルを<xref:System.Windows.Controls.ListViewItem>します。  
  
## <a name="example"></a>例  
 次の例は、データ バインドを作成します。<xref:System.Windows.Controls.ListView>を作成し、<xref:System.Windows.Style>各にイベント ハンドラーを追加する<xref:System.Windows.Controls.ListViewItem>します。  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 次の例のハンドル、<xref:System.Windows.Controls.Control.MouseDoubleClick>イベント。  
  
 [!code-csharp[ListViewHowTos#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
>  バインドする最も一般的な<xref:System.Windows.Controls.ListView>各にイベント ハンドラーを追加するスタイルを使用するデータ ソースに<xref:System.Windows.Controls.ListViewItem>、非データ バインドで<xref:System.Windows.Controls.ListView>明示的に作成するかどうかに関係なく、<xref:System.Windows.Controls.ListViewItem>します。  明示的および暗黙的が作成の詳細については<xref:System.Windows.Controls.ListViewItem>コントロールを参照してください<xref:System.Windows.Controls.ItemsControl>します。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Xml.XmlElement>
- [データ バインディングの概要](../data/data-binding-overview.md)
- [スタイルとテンプレート](styling-and-templating.md)
- [XMLDataProvider と XPath クエリを使用して XML データにバインドする](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [ListView の概要](listview-overview.md)
