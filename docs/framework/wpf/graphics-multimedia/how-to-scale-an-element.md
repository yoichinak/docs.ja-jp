---
title: '方法: 要素を拡大縮小する'
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], elements
- graphics [WPF], scaling elements
ms.assetid: 18158d94-bbe7-4f6a-814e-84d27fa748bf
ms.openlocfilehash: 607b3a11085f746503c1b82552f1740b49d9ef5d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942073"
---
# <a name="how-to-scale-an-element"></a>方法: 要素を拡大縮小する
この例は、使用する方法を示します、<xref:System.Windows.Media.ScaleTransform>に要素をスケーリングします。  
  
 使用して、<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>と<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>プロパティを指定する係数を使用して、要素のサイズを変更します。 たとえば、 <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> 1.5 の値が元の幅の 150 パーセントに要素を拡大します。 A<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>値 0.5 は 50% 要素の高さを縮小します。  
  
 使用して、<xref:System.Windows.Media.ScaleTransform.CenterX%2A>と<xref:System.Windows.Media.ScaleTransform.CenterY%2A>プロパティをスケール操作の中心点を指定します。 既定で、<xref:System.Windows.Media.ScaleTransform>四角形の左上隅に対応するポイント (0, 0) で中央揃えで配置します。 これは、要素の移動およびも適用するため、サイズが大きくなるように見えるのでの効果を<xref:System.Windows.Media.Transform>オブジェクトが存在する座標空間を変更します。  
  
 次の例では、 <xref:System.Windows.Media.ScaleTransform> 50 での 50 のサイズを 2 倍に<xref:System.Windows.Shapes.Rectangle>します。 <xref:System.Windows.Media.ScaleTransform>両方の 0 (既定値) の値を持つ<xref:System.Windows.Media.ScaleTransform.CenterX%2A>と<xref:System.Windows.Media.ScaleTransform.CenterY%2A>します。  
  
## <a name="example"></a>例  
 [!code-xaml[transformsSample#21](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#21)]  
  
 通常、設定<xref:System.Windows.Media.ScaleTransform.CenterX%2A>と<xref:System.Windows.Media.ScaleTransform.CenterY%2A>スケール オブジェクトの中心を: (<xref:System.Windows.FrameworkElement.Width%2A>/2、  <xref:System.Windows.FrameworkElement.Height%2A> /2)。  
  
 次の例では別<xref:System.Windows.Shapes.Rectangle>; のサイズが倍増するただし、この<xref:System.Windows.Media.ScaleTransform>両方の 25 の値を持つ<xref:System.Windows.Media.ScaleTransform.CenterX%2A>と<xref:System.Windows.Media.ScaleTransform.CenterY%2A>、四角形の中心に対応します。  
  
 [!code-xaml[transformsSample#22](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#22)]  
  
 次の図は、2 つの違いを示しています。<xref:System.Windows.Media.ScaleTransform>操作。 点線は、拡大/縮小する前の四角形のサイズと位置を示しています。  
  
 ![中心点が異なる 2 倍のスケール](./media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")  
2 つの ScaleTransform 操作では、ScaleX と ScaleY の値は同じですが、中心点が異なっています。  
  
 完全なサンプルについては、「[2-D 変換のサンプル](https://go.microsoft.com/fwlink/?LinkID=158252)」をご覧ください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.ScaleTransform>
- [変換の概要](transforms-overview.md)
- [方法トピック](transformations-how-to-topics.md)
