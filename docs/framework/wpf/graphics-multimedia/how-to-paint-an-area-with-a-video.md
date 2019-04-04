---
title: '方法: ビデオを使用して領域を塗りつぶす'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- painting with a video [WPF]
- video [WPF], painting with
- brushes [WPF], painting with a video
ms.assetid: 04dd6600-4a6e-4b43-a93e-21cce7dfbcb8
ms.openlocfilehash: 0756a9e87840648b55ecad4b3f1ce6e0e5452eb7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57363294"
---
# <a name="how-to-paint-an-area-with-a-video"></a>方法: ビデオを使用して領域を塗りつぶす
この例では、メディアで領域を塗りつぶす方法を示します。 メディアで領域を塗りつぶす方法の 1 つが使用するには、<xref:System.Windows.Controls.MediaElement>と共に、<xref:System.Windows.Media.VisualBrush>します。 使用して、<xref:System.Windows.Controls.MediaElement>ロードし、メディアの再生設定に使用すること、<xref:System.Windows.Media.VisualBrush.Visual%2A>のプロパティ、<xref:System.Windows.Media.VisualBrush>します。 使用することができますし、<xref:System.Windows.Media.VisualBrush>読み込まれたメディアを使用して領域を描画します。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Controls.MediaElement>と<xref:System.Windows.Media.VisualBrush>を描画する、<xref:System.Windows.Controls.TextBlock.Foreground%2A>の<xref:System.Windows.Controls.TextBlock>ビデオ コントロール。 この例の設定、<xref:System.Windows.Controls.MediaElement.IsMuted%2A>のプロパティ、<xref:System.Windows.Controls.MediaElement>に`true`サウンドが生成されないようにします。  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundInline](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundinline)]  
  
## <a name="example"></a>例  
 <xref:System.Windows.Media.VisualBrush>から継承、<xref:System.Windows.Media.TileBrush>クラス、並べて表示モードをいくつか提供します。 設定して、<xref:System.Windows.Media.TileBrush.TileMode%2A>のプロパティを<xref:System.Windows.Media.VisualBrush>に<xref:System.Windows.Media.TileMode.Tile>設定し、その<xref:System.Windows.Media.TileBrush.Viewport%2A>プロパティは、描画領域より小さい値を並べて表示するパターンを作成することができます。  
  
 次の例は、点を除いて前の例と同じ、<xref:System.Windows.Media.VisualBrush>ビデオから、パターンが生成されます。  
  
 [!code-csharp[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/PaintWithVideoExample.cs#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-vb[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/paintwithvideoexample.vb#graphicsmmvideoastextbackgroundtiledinline)]
 [!code-xaml[Visualbrush_markup_snip#GraphicsMMVideoAsTextBackgroundTiledInline](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/PaintWithVideoExample.xaml#graphicsmmvideoastextbackgroundtiledinline)]  
  
 アプリケーションには、メディア ファイルなどのコンテンツ ファイルを追加する方法については、[WPF アプリケーションのリソース、コンテンツ、およびデータ ファイル](../app-development/wpf-application-resource-content-and-data-files.md)を参照してください。 メディア ファイルを追加すると、リソース ファイルではなく、コンテンツ ファイルとして追加する必要があります。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Media.VisualBrush>
- [イメージ、描画、およびビジュアルによる塗りつぶし](painting-with-images-drawings-and-visuals.md)
- [TileBrush の概要](tilebrush-overview.md)
- [マルチメディアの概要](multimedia-overview.md)
