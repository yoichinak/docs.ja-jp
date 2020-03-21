---
title: '方法 : 背景として使用するイメージの縦横比を保持する'
ms.date: 03/30/2017
helpviewer_keywords:
- aspect ratios of background images [WPF], preserving
- brushes [WPF], preserving aspect ratios of background images
- background images [WPF], preserving aspect ratios
ms.assetid: 28c39478-13d7-4011-80a3-8b9cc3e54478
ms.openlocfilehash: b467fcd353994faef19b5a997e03d6582789eac1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186030"
---
# <a name="how-to-preserve-the-aspect-ratio-of-an-image-used-as-a-background"></a>方法 : 背景として使用するイメージの縦横比を保持する
この例では、イメージのア<xref:System.Windows.Media.TileBrush.Stretch%2A>スペクト比<xref:System.Windows.Media.ImageBrush>を保持するために、 のプロパティを使用する方法を示します。  
  
 既定では、を使用<xref:System.Windows.Media.ImageBrush>して領域をペイントすると、その内容が出力領域全体に広がって表示されます。 出力領域とイメージの縦横比が異なる場合は、この引き伸ばしによってイメージがゆがめられます。  
  
 イメージの<xref:System.Windows.Media.ImageBrush>縦横比を保持するには、プロパティを<xref:System.Windows.Media.TileBrush.Stretch%2A><xref:System.Windows.Media.Stretch.Uniform>or に<xref:System.Windows.Media.Stretch.UniformToFill>設定します。  
  
## <a name="example"></a>例  
 2 つのオブジェクトを<xref:System.Windows.Media.ImageBrush>使用して 2 つの四角形を描画する例を次に示します。 これらの四角形は 300 × 150 ピクセルで、どちらも 300 × 300 ピクセルのイメージを保持しています。 最初<xref:System.Windows.Media.TileBrush.Stretch%2A>のブラシのプロパティは に<xref:System.Windows.Media.Stretch.Uniform>設定され、2<xref:System.Windows.Media.TileBrush.Stretch%2A>番目のブラシのプロパティは<xref:System.Windows.Media.Stretch.UniformToFill>に設定されます。  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushStretchModesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/StretchModes.cs#imagebrushstretchmodesexamplewholepage)]  
  
 次の図は、設定が<xref:System.Windows.Media.TileBrush.Stretch%2A><xref:System.Windows.Media.Stretch.Uniform>[ ] の最初のブラシの出力を示しています。  
  
 ![Uniform 拡大を使用した ImageBrush](./media/graphicsmm-imagebrushuniformstretch.jpg "graphicsmm_ImageBrushUniformStretch")  
  
 次の図は、2 番目のブラシの出力を<xref:System.Windows.Media.TileBrush.Stretch%2A>示しています。 <xref:System.Windows.Media.Stretch.UniformToFill>  
  
 ![UniformToFill 拡大を使用した ImageBrush](./media/graphicsmm-imagebrushuniformtofillstretch.jpg "graphicsmm_ImageBrushUniformToFillStretch")  
  
 プロパティは、<xref:System.Windows.Media.TileBrush.Stretch%2A>他<xref:System.Windows.Media.TileBrush>のオブジェクト 、つまり、および<xref:System.Windows.Media.DrawingBrush><xref:System.Windows.Media.VisualBrush>に対して同じように動作します。 その他<xref:System.Windows.Media.TileBrush>のオブジェクト<xref:System.Windows.Media.ImageBrush>の詳細については、「[イメージ、描画、およびビジュアルを使用したペイント](painting-with-images-drawings-and-visuals.md)」を参照してください。  
  
 また、<xref:System.Windows.Media.TileBrush.Stretch%2A>このプロパティは、<xref:System.Windows.Media.TileBrush>コンテンツが出力領域に収まるように伸びる方法を指定するように見えますが、実際<xref:System.Windows.Media.TileBrush>にはコンテンツが基本タイルを埋めるように伸びる方法を指定します。 詳細については、<xref:System.Windows.Media.TileBrush> を参照してください。  
  
 このコード例は、クラスに用意されている大きな例の<xref:System.Windows.Media.ImageBrush>一部です。 完全なサンプルについては、「[イメージブラシのサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.TileBrush>
- [イメージ、描画、およびビジュアルによる塗りつぶし](painting-with-images-drawings-and-visuals.md)
