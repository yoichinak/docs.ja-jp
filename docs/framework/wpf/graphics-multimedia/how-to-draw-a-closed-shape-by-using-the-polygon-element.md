---
title: '方法: 多角形要素を使用して、閉じた図形を描画する'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], Polygon elements
- closed shapes [WPF], drawing with Polygon elements
- Polygon elements [WPF]
- drawing [WPF], closed shapes with Polygon elements
ms.assetid: 4b0ca008-29ce-48dd-8bc3-f3a20ffca6a6
ms.openlocfilehash: 533c341e2fae528ec896bf38bafa13974af1d127
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360040"
---
# <a name="how-to-draw-a-closed-shape-by-using-the-polygon-element"></a>方法: 多角形要素を使用して、閉じた図形を描画する
この例を使用して、閉じた形状を描画する方法を示しています、<xref:System.Windows.Shapes.Polygon>要素。 閉じた図形を描画するために作成、<xref:System.Windows.Shapes.Polygon>要素と使用してその<xref:System.Windows.Shapes.Polygon.Points%2A>図形の頂点を指定するプロパティ。 行が最初と最後の点を結ぶを自動的に描画されます。 最後に、指定、 <xref:System.Windows.Shapes.Shape.Fill%2A>、 <xref:System.Windows.Shapes.Shape.Stroke%2A>、またはその両方です。  
  
## <a name="example"></a>例  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ポイントの有効な構文がコンマで区切られた x 座標と y 座標のペアのスペースで区切られた一覧を示します。  
  
 [!code-xaml[drawingwithshapeelements#PolygonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polygonexample.xaml#polygonexample1)]  
  
 例を使用しますが、<xref:System.Windows.Controls.Canvas>多角形を格納することができます使用する多角形要素 (およびその他のすべての図形要素) と<xref:System.Windows.Controls.Panel>または<xref:System.Windows.Controls.Control>テキスト以外のコンテンツをサポートします。  
  
 この例より大きなサンプルの一部です。サンプル全体については、次を参照してください。 [Shape 要素のサンプル](https://go.microsoft.com/fwlink/?LinkID=160037)します。
