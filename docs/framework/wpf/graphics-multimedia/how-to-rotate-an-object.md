---
title: '方法: オブジェクトを回転させる'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rotating objects [WPF]
- rotating objects [WPF]
ms.assetid: ee3466cd-e66f-4e8f-8a5a-71d77bc1e390
ms.openlocfilehash: d1c4700a5dc8f6ed99043552999d8f014116da8f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61804167"
---
# <a name="how-to-rotate-an-object"></a>方法: オブジェクトを回転させる
次の例では、オブジェクトを回転させる方法を示します。 例では、最初に作成、<xref:System.Windows.Media.RotateTransform>を指定してその<xref:System.Windows.Media.RotateTransform.Angle%2A>(度単位)。  
  
 次の例では、回転、 <xref:System.Windows.Shapes.Polyline> 45 度の左上隅のオブジェクトします。  
  
## <a name="example"></a>例  
 [!code-xaml[Transforms_snip#RotatePolylineAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineabouttopleft)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineabouttopleft)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutTopLeft](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineabouttopleft)]  
  
 <xref:System.Windows.Media.RotateTransform.CenterX%2A>と<xref:System.Windows.Media.RotateTransform.CenterY%2A>のプロパティ、<xref:System.Windows.Media.RotateTransform>ポイント オブジェクトが回転を指定します。 この中心点は、変換する要素の座標空間で表します。 既定では、回転は (0,0) に適用されます。これは変換対象のオブジェクトの左上隅です。  
  
 次の例では、回転、 <xref:System.Windows.Shapes.Polyline> (25, 50) にした、時計回りに 45 度のオブジェクトします。  
  
 [!code-xaml[Transforms_snip#RotatePolylineAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/RotateTransformExample.xaml#rotatepolylineaboutcenter)]  
  
 [!code-csharp[Transforms_Procedural_snip#RotatePolylineAboutCenter](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/RotateTransformExample.cs#rotatepolylineaboutcenter)]
 [!code-vb[Transforms_Procedural_snip#RotatePolylineAboutCenter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/RotateTransformExample.vb#rotatepolylineaboutcenter)]  
  
 次の図は、適用した結果、<xref:System.Windows.Media.Transform>に 2 つのオブジェクト。  
  
 ![中心点が異なる 45 度の回転](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
異なる中心点を軸に 45 度回転させた 2 つのオブジェクト  
  
 <xref:System.Windows.Shapes.Polyline>前の例では、<xref:System.Windows.UIElement>します。 適用すると、<xref:System.Windows.Media.Transform>を<xref:System.Windows.UIElement.RenderTransform%2A>のプロパティを<xref:System.Windows.UIElement>、使用することができます、<xref:System.Windows.UIElement.RenderTransformOrigin%2A>の原点を指定するプロパティすべて<xref:System.Windows.Media.Transform>要素に適用します。 <xref:System.Windows.UIElement.RenderTransformOrigin%2A>プロパティは、相対座標を使用して、そのサイズがわからない場合でも、要素の中央に変換を適用することができます。 詳細については、および例についてを参照してください。[を相対値での変換の原点を指定する](how-to-specify-the-origin-of-a-transform-by-using-relative-values.md)します。  
  
 完全なサンプルについては、「[2-D 変換のサンプル](https://go.microsoft.com/fwlink/?LinkID=158252)」をご覧ください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Transform>
- [変換の概要](transforms-overview.md)
- [方法トピック](transformations-how-to-topics.md)
