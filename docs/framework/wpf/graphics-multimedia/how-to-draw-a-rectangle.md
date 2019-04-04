---
title: '方法: 四角形を描画する'
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], rectangles
- graphics [WPF], rectangles
- rectangles [WPF], drawing
ms.assetid: beeb57ef-fab5-4446-a38a-1588f97b4c2f
ms.openlocfilehash: 2734d5e808e8bc1f78c281e3fd6ab3c6ff12c58f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57363749"
---
# <a name="how-to-draw-a-rectangle"></a>方法: 四角形を描画する
この例を使用して四角形を描画する方法を示しています、<xref:System.Windows.Shapes.Rectangle>要素。  
  
 四角形を描画するために作成、<xref:System.Windows.Shapes.Rectangle>要素を指定し、<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>します。 四角形の内部を描画するには、次のように設定します。 その<xref:System.Windows.Shapes.Shape.Fill%2A>します。 四角形にアウトラインを与えるを使用してその<xref:System.Windows.Shapes.Shape.Stroke%2A>と<xref:System.Windows.Shapes.Shape.StrokeThickness%2A>プロパティ。  
  
 角の丸い四角形を提供する、省略可能な指定<xref:System.Windows.Shapes.Rectangle.RadiusX%2A>と<xref:System.Windows.Shapes.Rectangle.RadiusY%2A>プロパティ。 <xref:System.Windows.Shapes.Rectangle.RadiusX%2A>と<xref:System.Windows.Shapes.Rectangle.RadiusY%2A>プロパティは、四角形の角を丸めるに使用される楕円の x 軸と y 軸半径を設定します。  
  
 次の例では、2 つ<xref:System.Windows.Shapes.Rectangle>で要素が描画される、<xref:System.Windows.Controls.Canvas>します。 最初の四角形が、<xref:System.Windows.Media.Brushes.Blue%2A>内部。 2 番目の四角形が、 <xref:System.Windows.Media.Brushes.Blue%2A> 、内部、<xref:System.Windows.Media.Brushes.Black%2A>アウトラインとの角が丸いします。  
  
## <a name="example"></a>例  
 [!code-xaml[drawingwithshapeelements#Rectangle1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/rectangleexample.xaml#rectangle1)]  
  
 この例を使用しますが、<xref:System.Windows.Controls.Canvas>四角形を格納することができます使用する四角形要素 (およびその他のすべての図形要素) のいずれか<xref:System.Windows.Controls.Panel>または<xref:System.Windows.Controls.Control>テキスト以外のコンテンツをサポートします。 実際には、四角形の部分の背景を提供するために特に便利ですが<xref:System.Windows.Controls.Grid>パネル。 例については、、[テーブルの概要](../advanced/table-overview.md)を参照してください。  
  
 この例より大きなサンプルの一部です。サンプル全体については、[Shape 要素のサンプル](https://go.microsoft.com/fwlink/?LinkID=160037)を参照してください。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Shapes.Rectangle>
- [Shape 要素のサンプル](https://go.microsoft.com/fwlink/?LinkID=160037)
- [WPF での図形と基本描画の概要](shapes-and-basic-drawing-in-wpf-overview.md)
- [テーブルの概要](../advanced/table-overview.md)
