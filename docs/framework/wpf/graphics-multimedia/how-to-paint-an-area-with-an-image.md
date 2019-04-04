---
title: '方法: イメージで領域を塗りつぶす'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [WPF], painting with
- painting [WPF], with images
- brushes [WPF], painting with images
ms.assetid: 3432c533-1fc7-492d-94ee-0b13d60125ae
ms.openlocfilehash: c1db803aacad85ce90fec519b5eabdd8df7bb584
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369124"
---
# <a name="how-to-paint-an-area-with-an-image"></a>方法: イメージで領域を塗りつぶす
この例は、使用する方法を示します、<xref:System.Windows.Media.ImageBrush>イメージで領域を塗りつぶすクラス。 <xref:System.Windows.Media.ImageBrush>で指定された 1 つのイメージを表示します。 その<xref:System.Windows.Media.ImageBrush.ImageSource%2A>プロパティ。  
  
## <a name="example"></a>例  
 次の例の描画、 <xref:System.Windows.Controls.Control.Background%2A> 、ボタンを使用して、<xref:System.Windows.Media.ImageBrush>します。  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/PaintingWithImagesExample.cs#imagebrushexamplewholepage)]  
  
 既定で、<xref:System.Windows.Media.ImageBrush>イメージ、描画している領域を完全に埋めるを引き伸ばします。 前の例のようにイメージを引き伸ばしてボタンを塗りつぶすと、イメージにゆがみが生じることがあります。 設定してこの動作を制御することができます、<xref:System.Windows.Media.TileBrush.Stretch%2A>プロパティの<xref:System.Windows.Media.TileBrush>に<xref:System.Windows.Media.Stretch.Uniform>または<xref:System.Windows.Media.Stretch.UniformToFill>、それが原因で、イメージの縦横比を維持するブラシ。  
  
 設定した場合、<xref:System.Windows.Media.TileBrush.Viewport%2A>と<xref:System.Windows.Media.TileBrush.TileMode%2A>のプロパティ、 <xref:System.Windows.Media.ImageBrush>、繰り返しパターンを作成することができます。 次の例は、イメージから作成したパターンを使用してボタンを塗りつぶします。  
  
 [!code-csharp[UsingImageBrush_snip#TiledImageBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TiledImageBrushExample.cs#tiledimagebrushexamplewholepage)]
 [!code-vb[UsingImageBrush_snip#TiledImageBrushExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UsingImageBrush_snip/VisualBasic/TiledImageBrushExample.vb#tiledimagebrushexamplewholepage)]  
  
 詳細については、<xref:System.Windows.Media.ImageBrush>クラスを参照してください[イメージ、描画、およびビジュアル](painting-with-images-drawings-and-visuals.md)します。  
  
 このコード例はに対して提供されている例の一部、<xref:System.Windows.Media.ImageBrush>クラス。 サンプル全体については、[ImageBrush のサンプル](https://go.microsoft.com/fwlink/?LinkID=160005)を参照してください。  
  
## <a name="see-also"></a>関連項目
- [イメージ、描画、およびビジュアルによる塗りつぶし](painting-with-images-drawings-and-visuals.md)
