---
title: '方法: VideoDrawing を使用してメディアを再生する'
ms.date: 03/30/2017
helpviewer_keywords:
- playback of media [WPF]
- classes [WPF], MediaPlayer
ms.assetid: 165d47ed-22ce-4ded-aa6a-aa9b7467de87
ms.openlocfilehash: 2e2007525be770186a17cf9d2d42a7c52ba93fba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956951"
---
# <a name="how-to-play-media-using-a-videodrawing"></a>方法: VideoDrawing を使用してメディアを再生する
オーディオファイルまたはビデオファイルを再生するには<xref:System.Windows.Media.VideoDrawing> 、 <xref:System.Windows.Media.MediaPlayer>とを使用します。 メディアを読み込んで再生するには、2 つの方法があります。 1つ目の方法は<xref:System.Windows.Media.MediaPlayer> 、 <xref:System.Windows.Media.VideoDrawing>とを単独で使用することです。2番目の<xref:System.Windows.Media.MediaTimeline>方法は、 <xref:System.Windows.Media.MediaPlayer>と<xref:System.Windows.Media.VideoDrawing>で使用する独自のを作成することです。  
  
> [!NOTE]
> アプリケーションでメディアを配布するときは、イメージのようにプロジェクト リソースとしてメディア ファイルを使うことはできません。 プロジェクト ファイルで、メディアの種類を `Content` に設定し、`CopyToOutputDirectory` を `PreserveNewest` または `Always` に設定する必要があります。  
  
## <a name="example"></a>例  
 次の例では<xref:System.Windows.Media.VideoDrawing> 、と<xref:System.Windows.Media.MediaPlayer>を使用して、ビデオファイルを1回再生します。  
  
 [!code-csharp[DrawingMiscSnippets_snip#VideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#videodrawingexampleinline)]  
  
 メディアに対する追加のタイミング制御を取得するに<xref:System.Windows.Media.MediaTimeline>は、 <xref:System.Windows.Media.MediaPlayer> <xref:System.Windows.Media.VideoDrawing>オブジェクトとオブジェクトを使用してを使用します。 を<xref:System.Windows.Media.MediaTimeline>使用すると、ビデオを繰り返し表示するかどうかを指定できます。  
  
## <a name="example"></a>例  
 次の例では<xref:System.Windows.Media.MediaTimeline> 、 <xref:System.Windows.Media.VideoDrawing>オブジェクト<xref:System.Windows.Media.MediaPlayer>とオブジェクトを使用して、ビデオを繰り返し再生します。  
  
 [!code-csharp[DrawingMiscSnippets_snip#RepeatingVideoDrawingExampleInline](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/VideoDrawingExample.cs#repeatingvideodrawingexampleinline)]  
  
 を<xref:System.Windows.Media.MediaTimeline>使用する場合は、の<xref:System.Windows.Media.Animation.Clock.Controller%2A>プロパティ<xref:System.Windows.Media.MediaClock>から返された<xref:System.Windows.Media.Animation.ClockController>対話型のを使用して、の<xref:System.Windows.Media.MediaPlayer>対話型メソッドではなくメディアの再生を制御することに注意してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.VideoDrawing>
- [Drawing オブジェクトの概要](drawing-objects-overview.md)
