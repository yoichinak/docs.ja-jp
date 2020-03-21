---
title: '方法 : 要素をスケーリングする'
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], elements
- graphics [WPF], scaling elements
ms.assetid: 18158d94-bbe7-4f6a-814e-84d27fa748bf
ms.openlocfilehash: 34d954f68747be9eedc0ef71634e0c18b411d260
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112051"
---
# <a name="how-to-scale-an-element"></a>方法 : 要素をスケーリングする
この例では、 を<xref:System.Windows.Media.ScaleTransform>使用して要素をスケーリングする方法を示します。  
  
 プロパティ<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>と<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>プロパティを使用して、指定した係数で要素のサイズを変更します。 たとえば、値が<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>1.5 の場合、要素は元の幅の 150% に伸ばされます。 値<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>を 0.5 に設定すると、要素の高さが 50% 縮小されます。  
  
 プロパティ<xref:System.Windows.Media.ScaleTransform.CenterX%2A>と<xref:System.Windows.Media.ScaleTransform.CenterY%2A>プロパティを使用して、スケール操作の中心となる点を指定します。 既定では、a<xref:System.Windows.Media.ScaleTransform>は、四角形の左上隅に対応する点 (0,0) を中心に配置されます。 これは、要素を移動し、<xref:System.Windows.Media.Transform>より大きく見えるようにする効果があります。  
  
 次の例では、<xref:System.Windows.Media.ScaleTransform>を使用して 50 倍の 50<xref:System.Windows.Shapes.Rectangle>倍のサイズを使用します。 と<xref:System.Windows.Media.ScaleTransform>の両方<xref:System.Windows.Media.ScaleTransform.CenterX%2A>に 0 (既定値) の<xref:System.Windows.Media.ScaleTransform.CenterY%2A>値があります。  
  
## <a name="example"></a>例  
 [!code-xaml[transformsSample#21](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#21)]  
  
 通常、スケールされる<xref:System.Windows.Media.ScaleTransform.CenterX%2A>オブジェクト<xref:System.Windows.Media.ScaleTransform.CenterY%2A>の中心に設定し、<xref:System.Windows.FrameworkElement.Height%2A>次の値を設定します<xref:System.Windows.FrameworkElement.Width%2A>。  
  
 次の例では、<xref:System.Windows.Shapes.Rectangle>サイズが 2 倍になった別の例を示します。ただし、この<xref:System.Windows.Media.ScaleTransform>値は、両方の値と<xref:System.Windows.Media.ScaleTransform.CenterX%2A><xref:System.Windows.Media.ScaleTransform.CenterY%2A>の値が、四角形の中心に対応します。  
  
 [!code-xaml[transformsSample#22](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#22)]  
  
 次の図は、2 つの<xref:System.Windows.Media.ScaleTransform>操作の違いを示しています。 点線は、拡大/縮小する前の四角形のサイズと位置を示しています。  
  
 ![中心点が異なる 2 倍の拡大](./media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")  
2 つの ScaleTransform 操作では、ScaleX と ScaleY の値は同じですが、中心点が異なっています。  
  
 完全なサンプルについては[、2D 変換のサンプルを](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.ScaleTransform>
- [変換の概要](transforms-overview.md)
- [ハウツートピック](transformations-how-to-topics.md)
