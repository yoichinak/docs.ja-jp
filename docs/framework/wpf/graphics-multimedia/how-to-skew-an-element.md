---
title: '方法: 要素を傾斜させる'
ms.date: 03/30/2017
helpviewer_keywords:
- skewing elements [WPF]
- graphics [WPF], skewing elements
- classes [WPF], SkewTransform
ms.assetid: 56b65f2f-dc6e-4238-923f-ca44ec53c52f
ms.openlocfilehash: 47f671f493e7b379c36f9bf4b50ec9d185d10b8a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59144964"
---
# <a name="how-to-skew-an-element"></a>方法: 要素を傾斜させる
この例は、使用する方法を示します、<xref:System.Windows.Media.SkewTransform>要素を傾斜します。 傾斜 (スキューと呼ばれることもあります) は、一様でない方法で座標空間を拡大する変換です。 一般的な用途の 1 つ、<xref:System.Windows.Media.SkewTransform>をシミュレートするため、[!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)]で深さ[!INCLUDE[TLA#tla_2d](../../../../includes/tlasharptla-2d-md.md)]オブジェクト。  
  
 使用して、<xref:System.Windows.Media.SkewTransform.CenterX%2A>と<xref:System.Windows.Media.SkewTransform.CenterY%2A>のポイントの中心を指定するプロパティ、<xref:System.Windows.Media.SkewTransform>します。  
  
 使用して、<xref:System.Windows.Media.SkewTransform.AngleX%2A>と<xref:System.Windows.Media.SkewTransform.AngleY%2A>x 軸と y 軸の傾斜角度を指定して、これらの軸に沿って現在の座標系を傾斜させるプロパティ。  
  
 傾斜変換の効果を予測するを検討してください。 <xref:System.Windows.Media.SkewTransform.AngleX%2A> x 軸の値、元の座標系を傾斜します。 そのため、 <xref:System.Windows.Media.SkewTransform.AngleX%2A> 30 の y 軸が原点を通って 30 度回転し、値では、x-が原点から 30 度傾斜します。 同様に、 <xref:System.Windows.Media.SkewTransform.AngleY%2A> 30 の図形の y 値を原点から 30 度傾斜します。 これは、座標系の x または y での 30 度の平行移動 (移動) と同じ効果はないことに注意してください。  
  
 次の例は、水平方向に 45 度の傾斜を適用する<xref:System.Windows.Shapes.Rectangle>(0, 0) の中心点からです。  
  
## <a name="example"></a>例  
 [!code-xaml[transformsSample#41](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#41)]  
  
 次の例は、水平方向に 45 度の傾斜を適用する<xref:System.Windows.Shapes.Rectangle>中心点 (25, 25) から。  
  
 [!code-xaml[transformsSample#42](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#42)]  
  
 次の例は、垂直方向に 45 度の傾斜を適用する<xref:System.Windows.Shapes.Rectangle>中心点 (25, 25) から。  
  
 [!code-xaml[transformsSample#43](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/SkewTransformExample.xaml#43)]  
  
 次の図は、この例で使用されている各種の傾斜を示しています。  
  
 ![SkewTransform の例](./media/img-wcpsdk-graphicsmm-skewtransformexample.gif "img_wcpsdk_graphicsmm_skewtransformexample")  
説明した 3 つの SkewTransform の例  
  
 完全なサンプルについては、「[2-D 変換のサンプル](https://go.microsoft.com/fwlink/?LinkID=158252)」をご覧ください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.SkewTransform>
- [変換の概要](transforms-overview.md)
- [方法トピック](transformations-how-to-topics.md)
