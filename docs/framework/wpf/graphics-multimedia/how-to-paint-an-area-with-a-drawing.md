---
title: '方法: 描画を使用して領域を塗りつぶす'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with drawings
- painting [WPF], with drawings
- drawings [WPF], painting with
ms.assetid: c10dc4b1-09b1-41e8-ad14-456b5fb377df
ms.openlocfilehash: 6b204ae631912181333e2559ebadcdc37e7693b7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371562"
---
# <a name="how-to-paint-an-area-with-a-drawing"></a>方法: 描画を使用して領域を塗りつぶす
この例では、描画を使用して領域を塗りつぶす方法を示します。 使用する描画を使用して領域を描画する、<xref:System.Windows.Media.DrawingBrush>と 1 つ以上<xref:System.Windows.Media.Drawing>オブジェクト。   次の例では、<xref:System.Windows.Media.DrawingBrush>の 2 つの楕円の描画を使用してオブジェクトを描画します。  
  
## <a name="example"></a>例  
 [!code-xaml[drawingbrush_snip#DrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_snip/CS/DrawingBrushExample.xaml#drawingbrushexamplewholepage)]  
  
 [!code-csharp[drawingbrush_procedural_snip#DrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_procedural_snip/CSharp/DrawingBrushExample.cs#drawingbrushexamplewholepage)]
 [!code-vb[drawingbrush_procedural_snip#DrawingBrushExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/drawingbrush_procedural_snip/VisualBasic/DrawingBrushExample.vb#drawingbrushexamplewholepage)]  
  
 この例の出力を次の図に示します。  
  
 ![DrawingBrush からの出力](./media/graphicsmm-drawingbrush-simple.png "graphicsmm_drawingbrush_simple")  
  
 (で説明した理由から、図形の中心が白い[複合図形の塗りつぶしを制御](how-to-control-the-fill-of-a-composite-shape.md))。  
  
 設定して、<xref:System.Windows.Media.DrawingBrush>オブジェクトの<xref:System.Windows.Media.TileBrush.Viewport%2A>と<xref:System.Windows.Media.TileBrush.TileMode%2A>プロパティ、繰り返しパターンを作成することができます。 2 つの楕円の描画から作成されるパターンで、オブジェクトを塗りつぶす例を次に示します。  
  
 [!code-xaml[drawingbrush_snip#TiledDrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_snip/CS/TiledDrawingBrushExample.xaml#tileddrawingbrushexamplewholepage)]  
  
 [!code-csharp[drawingbrush_procedural_snip#TiledDrawingBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/drawingbrush_procedural_snip/CSharp/TiledDrawingBrushExample.cs#tileddrawingbrushexamplewholepage)]
 [!code-vb[drawingbrush_procedural_snip#TiledDrawingBrushExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/drawingbrush_procedural_snip/VisualBasic/TiledDrawingBrushExample.vb#tileddrawingbrushexamplewholepage)]  
  
 次の図は、並べて表示された<xref:System.Windows.Media.DrawingBrush>出力します。  
  
 ![並べて表示された DrawingBrush の出力](./media/graphicsmm-drawingbrush-tiled.png "graphicsmm_drawingbrush_tiled")  
  
 描画ブラシの詳細については、次を参照してください。[イメージ、描画、およびビジュアル](painting-with-images-drawings-and-visuals.md)します。 詳細については<xref:System.Windows.Media.Drawing>、オブジェクトを参照してください、 [Drawing オブジェクトの概要](drawing-objects-overview.md)します。
