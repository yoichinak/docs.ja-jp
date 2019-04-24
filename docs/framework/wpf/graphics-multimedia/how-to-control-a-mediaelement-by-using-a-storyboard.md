---
title: '方法: ストーリーボードを使用して MediaElement を制御する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- multimedia [WPF], controlling playback of media with Storyboards
- controlling playback of media [WPF], with Storyboards
- Storyboards [WPF], controlling playback of media with
- media [WPF], controlling playback with Storyboards
- playback of media [WPF], controlling with Storyboards
ms.assetid: 6128ca77-b826-4e36-b968-6f237157c543
ms.openlocfilehash: ae785e11b1da0f2c408b24021ad46ab071419378
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59100315"
---
# <a name="how-to-control-a-mediaelement-by-using-a-storyboard"></a>方法: ストーリーボードを使用して MediaElement を制御する
この例を制御する方法を示しています、<xref:System.Windows.Controls.MediaElement>を使用して、<xref:System.Windows.Media.MediaTimeline>で、 <xref:System.Windows.Media.Animation.Storyboard>。  
  
## <a name="example"></a>例  
 使用すると、<xref:System.Windows.Media.MediaTimeline>で、<xref:System.Windows.Media.Animation.Storyboard>のタイミングを制御する、 <xref:System.Windows.Controls.MediaElement>、機能が他の機能と同じです。<xref:System.Windows.Media.Animation.Timeline>アニメーションなどのオブジェクト。 たとえば、<xref:System.Windows.Media.MediaTimeline>を使用して<xref:System.Windows.Media.Animation.Timeline>などのプロパティ、<xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>を開始するタイミングを指定するプロパティを<xref:System.Windows.Controls.MediaElement>(メディアの再生を開始)。 また、使用、<xref:System.Windows.Media.Animation.Timeline.Duration%2A>プロパティを指定するどのくらいの期間、<xref:System.Windows.Controls.MediaElement>がアクティブ (メディアの再生の継続時間)。 使用しての詳細については<xref:System.Windows.Media.Animation.Timeline>オブジェクトを<xref:System.Windows.Media.Animation.Storyboard>を参照してください[ストーリー ボードの概要](storyboards-overview.md)します。  
  
 この例を使用する簡単なメディア プレーヤーを作成する方法を示しています、<xref:System.Windows.Media.MediaTimeline>再生を制御します。 メディア プレーヤーには、再生、一時停止、再開、およびボタンを停止します。 また、<xref:System.Windows.Controls.Slider>進行状況バーとして機能するコントロール。  
  
 次の例では、作成、 [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] media player 用です。  
  
 [!code-xaml[MediaGallery_snip#MediaTimelineExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml#mediatimelineexamplewholepage)]  
  
 次の例では、進行状況バーの機能を作成します。  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaTimelineExample.xaml.cs#codebehindmediatimelineexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaTimelineExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaTimelineExample.xaml.vb#codebehindmediatimelineexamplewholepage)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.MediaElement>
- <xref:System.Windows.Media.MediaTimeline>
- <xref:System.Windows.Media.Animation.Storyboard>
- [MediaElement (再生、一時停止、停止、ボリューム、および速度) を制御する](how-to-control-a-mediaelement-play-pause-stop-volume-and-speed.md)
- [ストーリーボードの概要](storyboards-overview.md)
- [キー フレーム アニメーションの概要](key-frame-animations-overview.md)
- [アニメーションの概要](animation-overview.md)
- [方法トピック](audio-and-video-how-to-topics.md)
- [グラフィックスとマルチメディア](index.md)
