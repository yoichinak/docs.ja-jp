---
title: '方法: 要素の Width プロパティを設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- width properties [WPF]
- Panel control [WPF], width properties of elements
ms.assetid: 6ee04a9d-63f0-4f5b-a406-0a8cd4c35729
ms.openlocfilehash: a5ed67ba20176398a863a1e9826b1eab71b182f2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052041"
---
# <a name="how-to-set-the-width-properties-of-an-element"></a>方法: 要素の Width プロパティを設定する
## <a name="example"></a>例  
 この例は、レンダリングの 4 つの幅に関連するプロパティの間での動作の違いを視覚的にでは[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]します。  
  
 <xref:System.Windows.FrameworkElement>クラスは、要素の幅の特性を説明する 4 つのプロパティを公開します。 これら 4 つのプロパティが競合すること、および優先する値は次のように決定されます、:<xref:System.Windows.FrameworkElement.MinWidth%2A>値よりも優先、<xref:System.Windows.FrameworkElement.MaxWidth%2A>値で、さらによりも優先、<xref:System.Windows.FrameworkElement.Width%2A>値。 4 番目のプロパティ、<xref:System.Windows.FrameworkElement.ActualWidth%2A>は読み取り専用、および、レイアウト プロセスとの相互作用によって決定される実際の幅を報告します。  
  
 次[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]例の描画、<xref:System.Windows.Shapes.Rectangle>要素 (`rect1`) の子として<xref:System.Windows.Controls.Canvas>します。 幅のプロパティを変更することができます、<xref:System.Windows.Shapes.Rectangle>一連を使用して<xref:System.Windows.Controls.ListBox>要素のプロパティ値を表す<xref:System.Windows.FrameworkElement.MinWidth%2A>、 <xref:System.Windows.FrameworkElement.MaxWidth%2A>、および<xref:System.Windows.FrameworkElement.Width%2A>します。 この方法で、各プロパティの優先順位が視覚的に表示されます。  
  
 [!code-xaml[WidthMinWidthMaxWidth#1](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#1)]  
[!code-xaml[WidthMinWidthMaxWidth#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#2)]  
  
 次の分離コード例は、イベントを処理する、<xref:System.Windows.Controls.Primitives.Selector.SelectionChanged>イベントを発生させます。 各カスタム メソッドはから入力を受け取り、 <xref:System.Windows.Controls.ListBox>、として値を解析し、 <xref:System.Double>、し、指定した幅に関連するプロパティに値が適用されます。 幅の値も文字列に変換し、さまざまなに書き込まれる<xref:System.Windows.Controls.TextBlock>要素 (それらの要素の定義は選択した XAML では表示されません)。  
  
 [!code-csharp[WidthMinWidthMaxWidth#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml.cs#3)]
 [!code-vb[WidthMinWidthMaxWidth#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WidthMinWidthMaxWidth/VisualBasic/Window1.xaml.vb#3)]  
  
 サンプル全体については、次を参照してください。[幅のプロパティの比較サンプル](https://go.microsoft.com/fwlink/?LinkID=160050)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.FrameworkElement.ActualWidth%2A>
- <xref:System.Windows.FrameworkElement.MaxWidth%2A>
- <xref:System.Windows.FrameworkElement.MinWidth%2A>
- <xref:System.Windows.FrameworkElement.Width%2A>
- [パネルの概要](panels-overview.md)
- [要素の Height プロパティを設定する](how-to-set-the-height-properties-of-an-element.md)
- [幅のプロパティの比較のサンプル](https://go.microsoft.com/fwlink/?LinkID=160050)
