---
title: '方法: テンプレートを使用して、GridView を使用する ListView のスタイルを設定する'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], styling
ms.assetid: 94bf964b-96c8-4bdf-a0c3-f5271b7cb565
ms.openlocfilehash: baef8bdee73d8493ba406f5eef1e3e3676680704
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57355767"
---
# <a name="how-to-use-templates-to-style-a-listview-that-uses-gridview"></a>方法: テンプレートを使用して、GridView を使用する ListView のスタイルを設定する
この例は、使用する方法を示します、<xref:System.Windows.DataTemplate>と<xref:System.Windows.Style>の外観を指定するオブジェクト、<xref:System.Windows.Controls.ListView>を使用するコントロールを<xref:System.Windows.Controls.GridView>表示モード。  
  
## <a name="example"></a>例  
 次の例に示す<xref:System.Windows.Style>と<xref:System.Windows.DataTemplate>の列ヘッダーの外観をカスタマイズするオブジェクト、<xref:System.Windows.Controls.GridViewColumn>します。  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheaderstyle)]  
  
 [!code-xaml[ListViewTemplate#GridViewHeaderTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewheadertemplate)]  
  
 次の例は、これらを使用する方法を示しています。<xref:System.Windows.Style>と<xref:System.Windows.DataTemplate>を設定するオブジェクト、<xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A>と<xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A>のプロパティを<xref:System.Windows.Controls.GridViewColumn>します。 <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>プロパティは、列のセルの内容を定義します。  
  
 [!code-xaml[ListViewTemplate#GridViewColumnTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcolumntemplate)]  
  
 <xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A>と<xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A>は 2 つの列ヘッダーの外観をカスタマイズするのに使用できるいくつかのプロパティののみ、<xref:System.Windows.Controls.GridView>コントロール。 詳細については、[GridView の列ヘッダーのスタイルとテンプレートの概要](gridview-column-header-styles-and-templates-overview.md)を参照してください。  
  
 次の例は、定義する方法を示します、<xref:System.Windows.DataTemplate>内のセルの外観をカスタマイズする、<xref:System.Windows.Controls.GridViewColumn>します。  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 次の例は、これを使用する方法を示します<xref:System.Windows.DataTemplate>のコンテンツを定義する、<xref:System.Windows.Controls.GridViewColumn>セル。 代わりにこのテンプレートを使用、<xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>前に表示されるプロパティ<xref:System.Windows.Controls.GridViewColumn>例。  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [GridView の概要](gridview-overview.md)
- [方法トピック](listview-how-to-topics.md)
- [ListView の概要](listview-overview.md)
