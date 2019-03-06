---
title: '方法: TileBrush のタイル サイズを設定する'
ms.date: 03/30/2017
helpviewer_keywords:
- TileBrush [WPF], size of tilepropertys
- Viewport property of TileBrush [WPF]
ms.assetid: 04f41090-1b46-4e36-832f-d27d28708b8c
ms.openlocfilehash: 2b603345e00ae3067c4be860b6aad1cf7b9883c5
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354454"
---
# <a name="how-to-set-the-tile-size-for-a-tilebrush"></a>方法: TileBrush のタイル サイズを設定する
この例のタイル サイズを設定する方法を示しています、<xref:System.Windows.Media.TileBrush>します。 既定で、<xref:System.Windows.Media.TileBrush>描画している領域を完全に塗りつぶす 1 つのタイルを生成します。 この動作をオーバーライドするには、設定、<xref:System.Windows.Media.TileBrush.Viewport%2A>と<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>プロパティ。  
  
 <xref:System.Windows.Media.TileBrush.Viewport%2A>プロパティのタイル サイズを指定します、<xref:System.Windows.Media.TileBrush>します。 既定の値で、<xref:System.Windows.Media.TileBrush.Viewport%2A>プロパティは、塗りつぶされる領域のサイズを基準とします。 させる、<xref:System.Windows.Media.TileBrush.Viewport%2A>プロパティを絶対タイル サイズを指定する設定、<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>プロパティを<xref:System.Windows.Media.BrushMappingMode.Absolute>します。  
  
## <a name="example"></a>例  
 次の例では、 <xref:System.Windows.Media.ImageBrush>、一種の<xref:System.Windows.Media.TileBrush>タイルを含む四角形を描画します。 例では、各タイルを出力領域 (四角形) の 50% x 50% に設定します。 その結果、四角形は、イメージの 4 つの投影で塗りつぶされます。  
  
 次の図は、この例で生成される出力を示しています。
  
 ![イメージ ブラシを並べて表示する例](./media/0.png "0")  
  
 [!code-csharp[UsingImageBrush_snip#RelativeTileSizeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#relativetilesizeexample)]  
  
 次の例では、作成、 <xref:System.Windows.Media.ImageBrush>、設定、<xref:System.Windows.Media.TileBrush.Viewport%2A>に`0,0,25,25`とその<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>に<xref:System.Windows.Media.BrushMappingMode.Absolute>、され別の四角形を描画するために使用します。 その結果、ブラシは、幅が 25 ピクセル、高さが 25 ピクセルのタイルを生成します。  
  
 次の図は、この例で生成される出力を示しています。  
  
 ![0,0,0.25,0.25 の Viewport を使用したタイル表示の TileBrush](./media/25x25viewport.png "25x25viewport")  
  
 [!code-csharp[UsingImageBrush_snip#AbsoluteTileSizeExample](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#absolutetilesizeexample)]  
  
 上記の例は、大規模なサンプルの一部です。 サンプル全体については、次を参照してください。 [ImageBrush のサンプル](https://go.microsoft.com/fwlink/?LinkID=160005)します。  
  
 この例では、<xref:System.Windows.Media.ImageBrush>クラス、<xref:System.Windows.Media.TileBrush.Viewport%2A>と<xref:System.Windows.Media.TileBrush.ViewportUnits%2A>プロパティの他の動作は同じ<xref:System.Windows.Media.TileBrush>オブジェクト、つまりの<xref:System.Windows.Media.DrawingBrush>と<xref:System.Windows.Media.VisualBrush>します。 詳細については<xref:System.Windows.Media.ImageBrush>およびその他、 <xref:System.Windows.Media.TileBrush> 、オブジェクトを参照してください[イメージ、描画、およびビジュアル](painting-with-images-drawings-and-visuals.md)します。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Media.TileBrush>
- [イメージ、描画、およびビジュアルによる塗りつぶし](painting-with-images-drawings-and-visuals.md)
- [TileBrush を使用してさまざまなタイル パターンを作成する](how-to-create-different-tile-patterns-with-a-tilebrush.md)
