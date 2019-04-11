---
title: '方法: DataTemplate によって生成された要素を検索する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- finding DataTemplate elements [WPF]
- DataTemplate [WPF]
ms.assetid: bfcd564e-5e9e-451e-8641-a9b5c3cfac90
ms.openlocfilehash: de5a4937feabdb4486d9dcf9d5e5bfddd2356690
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089187"
---
# <a name="how-to-find-datatemplate-generated-elements"></a>方法: DataTemplate によって生成された要素を検索する
この例によって生成される要素を検索する方法を示しています、<xref:System.Windows.DataTemplate>します。  
  
## <a name="example"></a>例  
 この例では、<xref:System.Windows.Controls.ListBox>一部にバインドされている[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]データ。  
  
 [!code-xaml[FindGeneratedItems#LB](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#lb)]  
  
 <xref:System.Windows.Controls.ListBox> 、次を使用して<xref:System.Windows.DataTemplate>:  
  
 [!code-xaml[FindGeneratedItems#DT](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#dt)]  
  
 取得する場合、<xref:System.Windows.Controls.TextBlock>によって生成された要素、<xref:System.Windows.DataTemplate>特定の<xref:System.Windows.Controls.ListBoxItem>、取得する必要がある、 <xref:System.Windows.Controls.ListBoxItem>、検索、<xref:System.Windows.Controls.ContentPresenter>内で<xref:System.Windows.Controls.ListBoxItem>を呼び出して<xref:System.Windows.FrameworkTemplate.FindName%2A>上、 <xref:System.Windows.DataTemplate>設定されている<xref:System.Windows.Controls.ContentPresenter>します。 次の例では、これらの手順を実行する方法を示します。 デモのために、この例で、テキストを示すメッセージ ボックスのコンテンツ、 <xref:System.Windows.DataTemplate>-テキスト ブロックを生成します。  
  
 [!code-csharp[FindGeneratedItems#DTFindElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#dtfindelement)]
 [!code-vb[FindGeneratedItems#DTFindElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#dtfindelement)]  
  
 実装を次に示します`FindVisualChild`、使用、<xref:System.Windows.Media.VisualTreeHelper>メソッド。  
  
 [!code-csharp[FindGeneratedItems#FVC](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#fvc)]
 [!code-vb[FindGeneratedItems#FVC](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#fvc)]  
  
## <a name="see-also"></a>関連項目

- [方法: ControlTemplate によって生成された要素を検索する](../controls/how-to-find-controltemplate-generated-elements.md)
- [データ バインディングの概要](data-binding-overview.md)
- [方法のトピック](data-binding-how-to-topics.md)
- [スタイルとテンプレート](../controls/styling-and-templating.md)
- [WPF XAML 名前スコープ](../advanced/wpf-xaml-namescopes.md)
- [WPF のツリー](../advanced/trees-in-wpf.md)
