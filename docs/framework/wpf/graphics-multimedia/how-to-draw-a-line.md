---
title: '方法: 線を描画する'
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], lines
- graphics [WPF], lines
- lines [WPF], drawing
ms.assetid: 0513ee01-6b27-4bb3-85f3-3a3e6710d80e
ms.openlocfilehash: a194fad5471cafcb567aa00522a597a4186ef4af
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57374188"
---
# <a name="how-to-draw-a-line"></a>方法: 線を描画する
この例を使用して線を描画する方法を示します、<xref:System.Windows.Shapes.Line>要素。  
  
 線を描画するために作成、<xref:System.Windows.Shapes.Line>要素。 使用して、その<xref:System.Windows.Shapes.Line.X1%2A>と<xref:System.Windows.Shapes.Line.Y1%2A>; の開始ポイントを設定して使用するプロパティの<xref:System.Windows.Shapes.Line.X2%2A>と<xref:System.Windows.Shapes.Line.Y2%2A>エンドポイントを設定するプロパティ。 最後に、設定、<xref:System.Windows.Shapes.Shape.Stroke%2A>と<xref:System.Windows.Shapes.Shape.StrokeThickness%2A>線なしの行が表示されないためです。  
  
 設定、<xref:System.Windows.Shapes.Shape.Fill%2A>行要素も何も起こりません、行は内部があるないためです。  
  
 次の例は、内で 3 つの行を描画、<xref:System.Windows.Controls.Canvas>要素。  
  
## <a name="example"></a>例  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 この例より大きなサンプルの一部です。サンプル全体については、[Shape 要素のサンプル](https://go.microsoft.com/fwlink/?LinkID=160037)を参照してください。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Shapes.Line>
- [Shape 要素のサンプル](https://go.microsoft.com/fwlink/?LinkID=160037)
