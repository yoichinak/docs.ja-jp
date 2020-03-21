---
title: '方法 : 要素を傾斜させる'
ms.date: 03/30/2017
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
ms.openlocfilehash: 10b00044c1c518641281e2e72cdb5a68474b5170
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112025"
---
# <a name="how-to-skew-an-element"></a>方法 : 要素を傾斜させる
この例では、 を<xref:System.Windows.Media.SkewTransform>使用して要素を傾斜させる方法を示します。 傾斜 (スキューと呼ばれることもあります) は、一様でない方法で座標空間を拡大する変換です。 一般的な a<xref:System.Windows.Media.SkewTransform>の用途の 1 つは、2D オブジェクトの 3D 深度をシミュレートする場合です。  
  
 プロパティと<xref:System.Windows.Media.SkewTransform.CenterX%2A><xref:System.Windows.Media.SkewTransform.CenterY%2A>プロパティを使用して、 の中心<xref:System.Windows.Media.SkewTransform>点を指定します。  
  
 プロパティ<xref:System.Windows.Media.SkewTransform.AngleX%2A>と<xref:System.Windows.Media.SkewTransform.AngleY%2A>プロパティを使用して、X 軸と Y 軸のスキュー角度を指定し、これらの軸に沿って現在の座標系を傾斜させます。  
  
 傾斜変換の効果を予測するには、元の座標系<xref:System.Windows.Media.SkewTransform.AngleX%2A>に対して x 軸の値を傾斜させるとします。 したがって、30<xref:System.Windows.Media.SkewTransform.AngleX%2A>の場合、y 軸は原点を 30 度回転し、その原点から 30 度ずつ x- の値を歪めます。 同様に、30 の値は<xref:System.Windows.Media.SkewTransform.AngleY%2A>、原点から 30 度ずつ図形の y- 値を歪めます。 これは、座標系の x または y での 30 度の平行移動 (移動) と同じ効果はないことに注意してください。  
  
 次の使用例は、45 度の水平傾斜を<xref:System.Windows.Shapes.Rectangle>中心点 (0,0) から a に適用します。  
  
## <a name="example"></a>例  
 [!code-xaml[transformsSample#41](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 次の例では、45 度の水平傾斜を<xref:System.Windows.Shapes.Rectangle>中心点 (25,25) から a に適用します。  
  
 [!code-xaml[transformsSample#42](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 次の使用例は、45 度の垂直傾斜を<xref:System.Windows.Shapes.Rectangle>中心点 (25,25) から a に適用します。  
  
 [!code-xaml[transformsSample#43](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 次の図は、この例で使用されている各種の傾斜を示しています。  
  
 ![SkewTransform の例](./media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")  
説明した 3 つの SkewTransform の例  
  
 完全なサンプルについては[、2D 変換のサンプルを](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.SkewTransform>
- [変換の概要](transforms-overview.md)
- [ハウツートピック](transformations-how-to-topics.md)
