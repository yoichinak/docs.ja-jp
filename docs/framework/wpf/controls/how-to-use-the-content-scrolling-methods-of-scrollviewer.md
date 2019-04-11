---
title: '方法: ScrollViewer のコンテンツ スクロール メソッドを使用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- IScrollInfo interface [WPF]
- scrolling methods [WPF]
- ScrollViewer control [WPF], scrolling methods
ms.assetid: 4708cc65-6510-45f8-82e6-30b0d3e30045
ms.openlocfilehash: e81c63de16d09de8435d5ec49a013bf8dc5927cd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142156"
---
# <a name="how-to-use-the-content-scrolling-methods-of-scrollviewer"></a>方法: ScrollViewer のコンテンツ スクロール メソッドを使用する
この例は、<xref:System.Windows.Controls.ScrollViewer>のスクロール メソッドを使用する方法を示しています。 これらのメソッドにより、<xref:System.Windows.Controls.ScrollViewer>内のコンテンツを、行毎あるいはページ毎に、段階的にスクロールできます。  
  
## <a name="example"></a>例  
 次の例では、`sv1`という名前の<xref:System.Windows.Controls.ScrollViewer>を作成し、<xref:System.Windows.Controls.TextBlock>要素をホストさせています。 <xref:System.Windows.Controls.TextBlock>は親である<xref:System.Windows.Controls.ScrollViewer>よりも大きいので、スクロールを有効にするためにスクロール バーが表示されます。 <xref:System.Windows.Controls.Button> さまざまなスクロール メソッドを表す要素が個別の左側にドッキングされている<xref:System.Windows.Controls.StackPanel>します。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]内の各<xref:System.Windows.Controls.Button>は、<xref:System.Windows.Controls.ScrollViewer>内のスクロールの挙動をコントロールする，関連したカスタムメソッドを呼び出します。  
  
 [!code-xaml[ScrollViewerMethods#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml#1)]  
  
 次の例では、<xref:System.Windows.Controls.ScrollViewer.LineUp%2A>と<xref:System.Windows.Controls.ScrollViewer.LineDown%2A>メソッドを使用します。  
  
 [!code-csharp[ScrollViewerMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ScrollViewerMethods#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewerMethods/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.StackPanel>
