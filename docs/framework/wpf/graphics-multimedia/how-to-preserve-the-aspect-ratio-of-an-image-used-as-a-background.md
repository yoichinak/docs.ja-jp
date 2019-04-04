---
title: '方法: 背景として使用するイメージの縦横比を保持する'
ms.date: 03/30/2017
helpviewer_keywords:
- aspect ratios of background images [WPF], preserving
- brushes [WPF], preserving aspect ratios of background images
- background images [WPF], preserving aspect ratios
ms.assetid: 28c39478-13d7-4011-80a3-8b9cc3e54478
ms.openlocfilehash: df5632aa3d3c7dbc2442cabe1f4db7a850a1bd54
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57353947"
---
# <a name="how-to-preserve-the-aspect-ratio-of-an-image-used-as-a-background"></a>方法: 背景として使用するイメージの縦横比を保持する
この例は、使用する方法を示します、<xref:System.Windows.Media.TileBrush.Stretch%2A>のプロパティ、<xref:System.Windows.Media.ImageBrush>イメージの縦横比を維持するためにします。  
  
 既定で使用すると、<xref:System.Windows.Media.ImageBrush>出力領域を完全に埋めるように領域を塗りつぶすにそのコンテンツが拡大します。 出力領域とイメージの縦横比が異なる場合は、この引き伸ばしによってイメージがゆがめられます。  
  
 させる、<xref:System.Windows.Media.ImageBrush>そのイメージの縦横比を保持、設定、<xref:System.Windows.Media.TileBrush.Stretch%2A>プロパティを<xref:System.Windows.Media.Stretch.Uniform>または<xref:System.Windows.Media.Stretch.UniformToFill>します。  
  
## <a name="example"></a>例  
 次の例を使用して 2 つ<xref:System.Windows.Media.ImageBrush>2 つの四角形を描画するオブジェクト。 これらの四角形は 300 × 150 ピクセルで、どちらも 300 × 300 ピクセルのイメージを保持しています。 <xref:System.Windows.Media.TileBrush.Stretch%2A>最初のブラシのプロパティに設定されて<xref:System.Windows.Media.Stretch.Uniform>、および<xref:System.Windows.Media.TileBrush.Stretch%2A>2 番目のブラシのプロパティに設定されて<xref:System.Windows.Media.Stretch.UniformToFill>します。  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushStretchModesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/StretchModes.cs#imagebrushstretchmodesexamplewholepage)]  
  
 次の図は、最初のブラシの出力を<xref:System.Windows.Media.TileBrush.Stretch%2A>設定<xref:System.Windows.Media.Stretch.Uniform>します。  
  
 ![ImageBrush with Uniform stretching](./media/graphicsmm-imagebrushuniformstretch.jpg "graphicsmm_ImageBrushUniformStretch")  
  
 次の図は、2 番目のブラシの出力を示しています、<xref:System.Windows.Media.TileBrush.Stretch%2A>設定<xref:System.Windows.Media.Stretch.UniformToFill>します。  
  
 ![ImageBrush with UniformToFill stretching](./media/graphicsmm-imagebrushuniformtofillstretch.jpg "graphicsmm_ImageBrushUniformToFillStretch")  
  
 なお、<xref:System.Windows.Media.TileBrush.Stretch%2A>プロパティは、他の動作と同じ<xref:System.Windows.Media.TileBrush>オブジェクト、つまりの<xref:System.Windows.Media.DrawingBrush>と<xref:System.Windows.Media.VisualBrush>します。 詳細については<xref:System.Windows.Media.ImageBrush>およびその他、 <xref:System.Windows.Media.TileBrush> 、オブジェクトを参照してください[イメージ、描画、およびビジュアル](painting-with-images-drawings-and-visuals.md)します。  
  
 なおが、<xref:System.Windows.Media.TileBrush.Stretch%2A>を指定するプロパティが表示される方法、<xref:System.Windows.Media.TileBrush>コンテンツは、その出力領域に合わせて拡大、実際に指定する方法、<xref:System.Windows.Media.TileBrush>端まで拡大する基本タイルのコンテンツします。 詳細については、「 <xref:System.Windows.Media.TileBrush> 」を参照してください。  
  
 このコード例はに対して提供されている例の一部、<xref:System.Windows.Media.ImageBrush>クラス。 サンプル全体については、[ImageBrush のサンプル](https://go.microsoft.com/fwlink/?LinkID=160005)を参照してください。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Media.TileBrush>
- [イメージ、描画、およびビジュアルによる塗りつぶし](painting-with-images-drawings-and-visuals.md)
