---
title: '方法 : TileBrush のタイル サイズを設定する'
ms.date: 03/30/2017
helpviewer_keywords:
- TileBrush [WPF], size of tile properties
- Viewport property of TileBrush [WPF]
ms.assetid: 04f41090-1b46-4e36-832f-d27d28708b8c
ms.openlocfilehash: af7bab59a292549b29dad9b6a7417f22b1b84e48
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186836"
---
# <a name="how-to-set-the-tile-size-for-a-tilebrush"></a>方法 : TileBrush のタイル サイズを設定する

この例では、 のタイル サイズを設定<xref:System.Windows.Media.TileBrush>する方法を示します。 既定では、<xref:System.Windows.Media.TileBrush>は、ペイントする領域全体を完全に塗りつぶす単一のタイルを生成します。 この動作は、 プロパティと<xref:System.Windows.Media.TileBrush.Viewport%2A>プロパティ<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>を設定することでオーバーライドできます。

プロパティ<xref:System.Windows.Media.TileBrush.Viewport%2A>は、 のタイル サイズ<xref:System.Windows.Media.TileBrush>を指定します。 デフォルトでは、プロパティの<xref:System.Windows.Media.TileBrush.Viewport%2A>値は、ペイントされる領域のサイズに対する相対的な値です。 プロパティに<xref:System.Windows.Media.TileBrush.Viewport%2A>絶対タイル サイズを指定するには、プロパティを<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>に<xref:System.Windows.Media.BrushMappingMode.Absolute>設定します。

## <a name="example"></a>例

次の例では<xref:System.Windows.Media.ImageBrush>、の種類<xref:System.Windows.Media.TileBrush>を使用して、タイルを持つ四角形を描画します。 この例では、各タイルを出力領域 (四角形) の 50 % から 50% に設定します。 その結果、四角形は、イメージの 4 つの投影で塗りつぶされます。

次の図は、この例で生成される出力を示しています。

![イメージ ブラシでタイリングを示す 4 つのサクランボを持つ四角形。](./media/how-to-set-the-tile-size-for-a-tilebrush/rectangle-tile-image-brush.png)

[!code-csharp[UsingImageBrush_snip#RelativeTileSizeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#relativetilesizeexample)]

次<xref:System.Windows.Media.ImageBrush>の例では、 を作成<xref:System.Windows.Media.TileBrush.Viewport%2A>し`0,0,25,25`、その<xref:System.Windows.Media.TileBrush.ViewportUnits%2A><xref:System.Windows.Media.BrushMappingMode.Absolute>を に設定し、それを使用して別の四角形を描画します。 その結果、ブラシは、幅が 25 ピクセル、高さが 25 ピクセルのタイルを生成します。

次の図は、この例で生成される出力を示しています。

![ビューポート付きタイル ブラシを示す 48 個のサクランボを持つ四角形。](./media/how-to-set-the-tile-size-for-a-tilebrush/25-x-25-viewport-tilebrush.png)

[!code-csharp[UsingImageBrush_snip#AbsoluteTileSizeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#absolutetilesizeexample)]

上記の例は、大規模なサンプルの一部です。 完全なサンプルについては、「[イメージブラシのサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush)」を参照してください。

この例ではクラスを<xref:System.Windows.Media.ImageBrush>使用していますが、 <xref:System.Windows.Media.TileBrush.Viewport%2A> <xref:System.Windows.Media.TileBrush.ViewportUnits%2A>プロパティと プロパティは他<xref:System.Windows.Media.TileBrush>のオブジェクト (for<xref:System.Windows.Media.DrawingBrush>および<xref:System.Windows.Media.VisualBrush>for) とで同じように動作します。 その他<xref:System.Windows.Media.TileBrush>のオブジェクト<xref:System.Windows.Media.ImageBrush>の詳細については、「[イメージ、描画、およびビジュアルを使用したペイント](painting-with-images-drawings-and-visuals.md)」を参照してください。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.TileBrush>
- [イメージ、描画、およびビジュアルによる塗りつぶし](painting-with-images-drawings-and-visuals.md)
- [TileBrush を使用してさまざまなタイル パターンを作成する](how-to-create-different-tile-patterns-with-a-tilebrush.md)
