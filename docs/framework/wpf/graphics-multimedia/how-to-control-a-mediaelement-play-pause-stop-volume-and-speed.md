---
title: '方法: MediaElement (再生、一時停止、停止、ボリューム、速度) を制御する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- playback of media [WPF], controlling
- controlling playback of media [WPF]
- multimedia [WPF], controlling playback of media
- media [WPF], controlling playback of
ms.assetid: 6885a730-e054-4c16-8c1e-ffe17b1f7c32
ms.openlocfilehash: bb7319fc7ccec0220cbd79a32d5d015f9f2422d0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182859"
---
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a>方法: MediaElement (再生、一時停止、停止、ボリューム、速度) を制御する
次の例を使用してメディアの再生を制御する方法を示しています、<xref:System.Windows.Controls.MediaElement>します。 例では、再生、一時停止、停止、およびメディアに前後へスキップだけでなくボリュームと速度比を調整することができます簡単なメディア プレーヤーを作成します。  
  
## <a name="example"></a>例  
 次のコードは、UI を作成します。  
  
> [!NOTE]
>  <xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>プロパティの<xref:System.Windows.Controls.MediaElement>に設定する必要があります`Manual`対話的に停止できるようにするには、するには、一時停止、およびメディアを再生します。  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a>例  
 次のコードでは、サンプル UI コントロールの機能を実装します。 <xref:System.Windows.Controls.MediaElement.Play%2A>、 <xref:System.Windows.Controls.MediaElement.Pause%2A>、および<xref:System.Windows.Controls.MediaElement.Stop%2A>メソッドを使用して、それぞれの再生、一時停止およびメディアを停止します。 変更、<xref:System.Windows.Controls.MediaElement.Position%2A>のプロパティ、<xref:System.Windows.Controls.MediaElement>メディア スキップすることができます。 最後に、<xref:System.Windows.Controls.MediaElement.Volume%2A>と<xref:System.Windows.Controls.MediaElement.SpeedRatio%2A>プロパティを使用して、メディアのボリュームや再生速度を調整します。  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a>関連項目

- [ストーリーボードを使用して MediaElement を制御する](how-to-control-a-mediaelement-by-using-a-storyboard.md)
