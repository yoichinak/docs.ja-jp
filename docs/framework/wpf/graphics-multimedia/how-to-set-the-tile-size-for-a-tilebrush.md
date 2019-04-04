---
title: '方法: TileBrush のタイル サイズを設定する'
ms.date: 03/30/2017
helpviewer_keywords:
- TileBrush [WPF], size of tile properties
- Viewport property of TileBrush [WPF]
ms.assetid: 04f41090-1b46-4e36-832f-d27d28708b8c
ms.openlocfilehash: 80b5dfc668464df829db593668bea8a9a4ec09e4
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839697"
---
# <a name="how-to-set-the-tile-size-for-a-tilebrush"></a>方法: TileBrush のタイル サイズを設定する

この例のタイル サイズを設定する方法を示しています、<xref:System.Windows.Media.TileBrush>します。 既定で、<xref:System.Windows.Media.TileBrush>描画している領域を完全に塗りつぶす 1 つのタイルを生成します。 この動作をオーバーライドするには、設定、<xref:System.Windows.Media.TileBrush.Viewport%2A>と<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>プロパティ。

<xref:System.Windows.Media.TileBrush.Viewport%2A>プロパティのタイル サイズを指定します、<xref:System.Windows.Media.TileBrush>します。 既定の値で、<xref:System.Windows.Media.TileBrush.Viewport%2A>プロパティは、塗りつぶされる領域のサイズを基準とします。 させる、<xref:System.Windows.Media.TileBrush.Viewport%2A>プロパティを絶対タイル サイズを指定する設定、<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>プロパティを<xref:System.Windows.Media.BrushMappingMode.Absolute>します。

## <a name="example"></a>例

次の例では、 <xref:System.Windows.Media.ImageBrush>、一種の<xref:System.Windows.Media.TileBrush>タイルを含む四角形を描画します。 例では、各タイルを出力領域 (四角形) の 50% 50% に設定します。 その結果、四角形は、イメージの 4 つの投影で塗りつぶされます。

次の図は、例では、生成する出力を示しています。

![イメージ ブラシを並べて表示を示す 4 つのスピードで四角形。](./media/how-to-set-the-tile-size-for-a-tilebrush/rectangle-tile-image-brush.png)

[!code-csharp[UsingImageBrush_snip#RelativeTileSizeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#relativetilesizeexample)]

次の例では、作成、 <xref:System.Windows.Media.ImageBrush>、設定、<xref:System.Windows.Media.TileBrush.Viewport%2A>に`0,0,25,25`とその<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>に<xref:System.Windows.Media.BrushMappingMode.Absolute>、され別の四角形を描画するために使用します。 その結果、ブラシは、幅が 25 ピクセル、高さが 25 ピクセルのタイルを生成します。

次の図は、例では、生成する出力を示しています。

![448 個結婚記念日おめでとうビューポート TileBrush を並べて表示を示す四角形。](./media/how-to-set-the-tile-size-for-a-tilebrush/25-x-25-viewport-tilebrush.png)

[!code-csharp[UsingImageBrush_snip#AbsoluteTileSizeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#absolutetilesizeexample)]

上記の例は、大規模なサンプルの一部です。 サンプル全体については、[ImageBrush のサンプル](https://go.microsoft.com/fwlink/?LinkID=160005)を参照してください。

この例では、<xref:System.Windows.Media.ImageBrush>クラス、<xref:System.Windows.Media.TileBrush.Viewport%2A>と<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>プロパティの他の動作は同じ<xref:System.Windows.Media.TileBrush>オブジェクト、つまりの<xref:System.Windows.Media.DrawingBrush>と<xref:System.Windows.Media.VisualBrush>します。 詳細については<xref:System.Windows.Media.ImageBrush>およびその他、 <xref:System.Windows.Media.TileBrush> 、オブジェクトを参照してください[イメージ、描画、およびビジュアル](painting-with-images-drawings-and-visuals.md)します。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.TileBrush>
- [イメージ、描画、およびビジュアルによる塗りつぶし](painting-with-images-drawings-and-visuals.md)
- [TileBrush を使用してさまざまなタイル パターンを作成する](how-to-create-different-tile-patterns-with-a-tilebrush.md)
