---
title: '方法: 直線または線分の終点のキャップを変更する'
ms.date: 03/30/2017
helpviewer_keywords:
- Shape elements [WPF], ends
- Shape elements [WPF], caps
- graphics [WPF], Shape caps
ms.assetid: f4bf3416-b3d8-4568-b98e-3eda8f6dbf7a
ms.openlocfilehash: ba61b30b4ff575bb504f792f8990bbfc64a6c33e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371477"
---
# <a name="how-to-modify-the-cap-at-the-end-of-a-line-or-segment"></a>方法: 直線または線分の終点のキャップを変更する
この例では、先頭または末尾の開いている図形を変更する方法を示しています<xref:System.Windows.Shapes.Shape>要素。 オープンの先頭に上限を変更する<xref:System.Windows.Shapes.Shape>を使用して、その<xref:System.Windows.Shapes.Shape.StrokeStartLineCap%2A>プロパティ。 オープンの終点のキャップを変更する<xref:System.Windows.Shapes.Shape>を使用して、その<xref:System.Windows.Shapes.Shape.StrokeEndLineCap%2A>プロパティ。 使用可能なライン キャップを表示するを参照してください。、<xref:System.Windows.Media.PenLineCap>列挙体。  
  
> [!NOTE]
>  このプロパティは、開いている図形をなど、 <xref:System.Windows.Shapes.Line>、 <xref:System.Windows.Shapes.Polyline>、または開いている<xref:System.Windows.Shapes.Path>要素。  
  
 次の例では、4 つを描画<xref:System.Windows.Shapes.Polyline>要素の各端にさまざまな図形を使用しています。  
  
## <a name="example"></a>例  
 [!code-xaml[drawingwithshapeelements#ShapeLineCaps1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/linecapsandjoinsexample.xaml#shapelinecaps1)]  
  
 この例より大きなサンプルの一部です。サンプル全体については、[Shape 要素のサンプル](https://go.microsoft.com/fwlink/?LinkID=160037)を参照してください。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Media.PenLineCap>
