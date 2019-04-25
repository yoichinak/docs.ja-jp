---
title: '方法: ビジュアルのオフセットを取得する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting offset values from visual objects [WPF]
- offset values [WPF], retrieving from visual objects [WPF]
- visual objects [WPF], retrieving offset values from
- retrieving offset values from visual objects [WPF]
ms.assetid: 889a1dd6-1b11-445a-b351-fbb04c53ee34
ms.openlocfilehash: 4787b771c7e59a8b033b9267079c068a5845a1e6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59093411"
---
# <a name="how-to-get-the-offset-of-a-visual"></a>方法: ビジュアルのオフセットを取得する
これらの例では、その親または先祖、または子孫に対して相対的なビジュアル オブジェクトのオフセット値を取得する方法を示します。  
  
## <a name="example"></a>例  
 次のマークアップ例は、<xref:System.Windows.Controls.TextBlock>で定義されている<xref:System.Windows.FrameworkElement.Margin%2A>4 の値。  
  
 [!code-xaml[VisualSnippets#VisualSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml#visualsnippet1)]  
  
 次のコード例を使用する方法を示しています、<xref:System.Windows.Media.VisualTreeHelper.GetOffset%2A>のオフセットを取得するメソッドを<xref:System.Windows.Controls.TextBlock>します。 オフセット値が含まれている、返された内<xref:System.Windows.Vector>値。  
  
 [!code-csharp[VisualSnippets#VisualSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet2)]
 [!code-vb[VisualSnippets#VisualSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet2)]  
  
 オフセットがアカウントには、<xref:System.Windows.FrameworkElement.Margin%2A>値。 この場合、<xref:System.Windows.Vector.X%2A>は 4、および<xref:System.Windows.Vector.Y%2A>は 4 です。  
  
 返されるオフセット値は、の親に対する相対的な<xref:System.Windows.Media.Visual>します。 親に相対でないオフセット値を取得する場合、<xref:System.Windows.Media.Visual>を使用して、<xref:System.Windows.Media.Visual.TransformToAncestor%2A>メソッド。  
  
## <a name="getting-the-offset-relative-to-an-ancestor"></a>先祖からの相対オフセットの取得  
 次のマークアップ例は、<xref:System.Windows.Controls.TextBlock>内で 2 つの入れ子になっている<xref:System.Windows.Controls.StackPanel>オブジェクト。  
  
 [!code-xaml[VisualSnippets#VisualSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window2.xaml#visualsnippet7)]  
  
 次の図は、マークアップの結果を示します。  
  
 ![オブジェクトのオフセット値](./media/visualoffset-01.png "VisualOffset_01")  
TextBlock は、2 つの StackPanels 内で入れ子になった  
  
 次のコード例を使用する方法を示しています、<xref:System.Windows.Media.Visual.TransformToAncestor%2A>のオフセットを取得するメソッドを<xref:System.Windows.Controls.TextBlock>含むの基準とした<xref:System.Windows.Window>します。 オフセット値が含まれている、返された内<xref:System.Windows.Media.GeneralTransform>値。  
  
 [!code-csharp[VisualSnippets#VisualSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet5)]
 [!code-vb[VisualSnippets#VisualSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet5)]  
  
 オフセットがアカウントには、<xref:System.Windows.FrameworkElement.Margin%2A>コンテナー内のすべてのオブジェクトの値<xref:System.Windows.Window>します。 この場合、 <xref:System.Windows.Vector.X%2A> 28 (16 + 8 + 4)、および<xref:System.Windows.Vector.Y%2A>は 28 です。  
  
 返されるオフセット値の先祖、<xref:System.Windows.Media.Visual>します。 子孫に対する相対的なオフセットの値を取得する場合、<xref:System.Windows.Media.Visual>を使用して、<xref:System.Windows.Media.Visual.TransformToDescendant%2A>メソッド。  
  
## <a name="getting-the-offset-relative-to-a-descendant"></a>子に相対的なオフセットの取得  
 次のマークアップ例は、<xref:System.Windows.Controls.TextBlock>内に含まれる、<xref:System.Windows.Controls.StackPanel>オブジェクト。  
  
 [!code-xaml[VisualSnippets#VisualSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml#visualsnippet4)]  
  
 次のコード例を使用する方法を示しています、<xref:System.Windows.Media.Visual.TransformToDescendant%2A>のオフセットを取得するメソッドを<xref:System.Windows.Controls.StackPanel>その子の基準とした<xref:System.Windows.Controls.TextBlock>します。 オフセット値が含まれている、返された内<xref:System.Windows.Media.GeneralTransform>値。  
  
 [!code-csharp[VisualSnippets#VisualSnippet9](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualSnippets/CSharp/Window1.xaml.cs#visualsnippet9)]
 [!code-vb[VisualSnippets#VisualSnippet9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualSnippets/visualbasic/window1.xaml.vb#visualsnippet9)]  
  
 オフセットがアカウントには、<xref:System.Windows.FrameworkElement.Margin%2A>すべてのオブジェクトの値。 この場合、 <xref:System.Windows.Vector.X%2A> -4、および<xref:System.Windows.Vector.Y%2A>-4 です。 オフセットの値は、親オブジェクトがその子オブジェクトを基準としてオフセット悪影響を及ぼすために、負の値です。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Visual>
- <xref:System.Windows.Media.VisualTreeHelper>
- [WPF グラフィックス レンダリングの概要](wpf-graphics-rendering-overview.md)
