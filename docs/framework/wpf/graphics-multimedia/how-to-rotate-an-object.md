---
title: '方法 : オブジェクトを回転させる'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rotating objects [WPF]
- rotating objects [WPF]
ms.assetid: ee3466cd-e66f-4e8f-8a5a-71d77bc1e390
ms.openlocfilehash: e17d3b7b9986b477df198480129edaf4c139c6bc
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112064"
---
# <a name="how-to-rotate-an-object"></a>方法 : オブジェクトを回転させる
次の例では、オブジェクトを回転させる方法を示します。 この例では、まず<xref:System.Windows.Media.RotateTransform>a を<xref:System.Windows.Media.RotateTransform.Angle%2A>作成し、次に度を指定します。  
  
 次の使用例は、オブジェクト<xref:System.Windows.Shapes.Polyline>を左上隅を中心に 45 度回転します。  
  
## <a name="example"></a>例  
 [!code-xaml[Transforms_snip#RotatePolylineAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineabouttopleft)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineabouttopleft)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineabouttopleft)]  
  
 の<xref:System.Windows.Media.RotateTransform.CenterX%2A><xref:System.Windows.Media.RotateTransform.CenterY%2A>プロパティと<xref:System.Windows.Media.RotateTransform>プロパティは、オブジェクトを回転するポイントを指定します。 この中心点は、変換する要素の座標空間で表します。 既定では、回転は (0,0) に適用されます。これは変換対象のオブジェクトの左上隅です。  
  
 次の例では、オブジェクト<xref:System.Windows.Shapes.Polyline>を点(25,50)を中心に時計回りに 45 度回転します。  
  
 [!code-xaml[Transforms_snip#RotatePolylineAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineaboutcenter)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineaboutcenter)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutCenter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineaboutcenter)]  
  
 次の図は、2 つのオブジェクトに<xref:System.Windows.Media.Transform>a を適用した結果を示しています。  
  
 ![中心点が異なる 45 度の回転](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
異なる中心点を軸に 45 度回転させた 2 つのオブジェクト  
  
 前<xref:System.Windows.Shapes.Polyline>の例のは<xref:System.Windows.UIElement>. プロパティ<xref:System.Windows.Media.Transform><xref:System.Windows.UIElement.RenderTransform%2A>に<xref:System.Windows.UIElement>を適用する場合、プロパティを<xref:System.Windows.UIElement.RenderTransformOrigin%2A>使用して、要素に適用するすべての<xref:System.Windows.Media.Transform>要素の原点を指定できます。 プロパティは<xref:System.Windows.UIElement.RenderTransformOrigin%2A>相対座標を使用するため、サイズがわからない場合でも、要素の中心に変換を適用できます。 詳細および例については、「[相対値を使用して変換の原点を指定する](how-to-specify-the-origin-of-a-transform-by-using-relative-values.md)」を参照してください。  
  
 完全なサンプルについては[、2D 変換のサンプルを](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Transform>
- [変換の概要](transforms-overview.md)
- [ハウツートピック](transformations-how-to-topics.md)
