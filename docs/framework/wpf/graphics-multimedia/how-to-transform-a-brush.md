---
title: '方法 : ブラシを変換する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], rotating contents
- brushes [WPF], Transform property
- rotating contents of brushes [WPF]
ms.assetid: ebada2f9-f01f-4863-9ea2-c2e4e51610f1
ms.openlocfilehash: b4484e2fc1ae3e969b02b1d8f3ae4ab2a035558e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187337"
---
# <a name="how-to-transform-a-brush"></a>方法 : ブラシを変換する
この例では、2<xref:System.Windows.Media.Brush>つの変換プロパティ<xref:System.Windows.Media.Brush.RelativeTransform%2A>と を使用してオブジェクト<xref:System.Windows.Media.Brush.Transform%2A>を変換する方法を示します。  
  
 次の例では、<xref:System.Windows.Media.RotateTransform>を使用して、<xref:System.Windows.Media.ImageBrush>の内容を 45 度回転します。  
  
 次の図は、<xref:System.Windows.Media.ImageBrush>を<xref:System.Windows.Media.RotateTransform>使用せずに<xref:System.Windows.Media.RotateTransform><xref:System.Windows.Media.Brush.RelativeTransform%2A>プロパティに適用し、 プロパティに<xref:System.Windows.Media.RotateTransform>適用します<xref:System.Windows.Media.Brush.Transform%2A>。  
  
 ![ブラシ RelativeTransform と変換の設定](./media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk_graphicsmm_transformandrelativetransform")  
  
## <a name="example"></a>例  
 最初の例では、<xref:System.Windows.Media.RotateTransform>の<xref:System.Windows.Media.Brush.RelativeTransform%2A>プロパティに<xref:System.Windows.Media.ImageBrush>a を適用します。 <xref:System.Windows.Media.RotateTransform>オブジェクト<xref:System.Windows.Media.RotateTransform.CenterX%2A>の<xref:System.Windows.Media.RotateTransform.CenterY%2A>プロパティと プロパティは、どちらも 0.5 に設定され、このコンテンツの中心点の相対座標です。 その結果、コンテンツは<xref:System.Windows.Media.ImageBrush>中心を中心に回転します。  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 2 番目の例では<xref:System.Windows.Media.RotateTransform>、<xref:System.Windows.Media.ImageBrush>に a も適用します。ただし、この例では<xref:System.Windows.Media.Brush.Transform%2A>、プロパティの代わりに<xref:System.Windows.Media.Brush.RelativeTransform%2A>プロパティを使用します。  
  
 ブラシを中心に回転させるには、オブジェクトの<xref:System.Windows.Media.RotateTransform.CenterX%2A>プロパティと<xref:System.Windows.Media.RotateTransform.CenterY%2A>プロパティを<xref:System.Windows.Media.RotateTransform>絶対座標に設定します。 このブラシは、175 x 90 ピクセルの四角形を描画するため、四角形の中心点は (87.5, 45) になります。  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xaml[BrushesIntroduction_snip#ImageBrushTransformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 プロパティ<xref:System.Windows.Media.Brush.RelativeTransform%2A>と<xref:System.Windows.Media.Brush.Transform%2A>プロパティの動作の詳細については、「[ブラシ変換の概要](brush-transformation-overview.md)」を参照してください。  
  
 完全なサンプルについては、「[ブラシのサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)」を参照してください。 ブラシの詳細については、「[純色およびグラデーションによる塗りつぶしの概要](painting-with-solid-colors-and-gradients-overview.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [ブラシの変換の概要](brush-transformation-overview.md)
- [純色およびグラデーションによる塗りつぶしの概要](painting-with-solid-colors-and-gradients-overview.md)
- [変換の概要](transforms-overview.md)
