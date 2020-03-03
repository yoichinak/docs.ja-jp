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
ms.openlocfilehash: cde7c32b48dff3d6d054e700b2f95771ba3b3773
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930163"
---
# <a name="how-to-control-a-mediaelement-play-pause-stop-volume-and-speed"></a>方法: MediaElement (再生、一時停止、停止、ボリューム、速度) を制御する
次の例は、 <xref:System.Windows.Controls.MediaElement>を使用してメディアの再生を制御する方法を示しています。 この例では、メディア内での再生、一時停止、停止、スキップを可能にする簡単なメディアプレーヤーを作成します。また、音量と速度を調整することもできます。  
  
## <a name="example"></a>例  
 次のコードでは、UI を作成します。  
  
> [!NOTE]
> メディア<xref:System.Windows.Controls.MediaElement.LoadedBehavior%2A>を対話的<xref:System.Windows.Controls.MediaElement>に停止、一時停止、および再生できるようにするには、のプロパティをに`Manual`設定する必要があります。  
  
 [!code-xaml[MediaGallery_snip#MediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml#mediaelementexamplewholepage)]  
  
## <a name="example"></a>例  
 次のコードは、サンプル UI コントロールの機能を実装しています。 、 <xref:System.Windows.Controls.MediaElement.Play%2A>、 <xref:System.Windows.Controls.MediaElement.Pause%2A>および<xref:System.Windows.Controls.MediaElement.Stop%2A>の各メソッドは、それぞれ、メディアを再生、一時停止、および停止するために使用されます。 <xref:System.Windows.Controls.MediaElement.Position%2A> のプロパティを変更すると、メディア内<xref:System.Windows.Controls.MediaElement>をスキップできます。 最後に、プロパティ<xref:System.Windows.Controls.MediaElement.SpeedRatio%2A> とプロパティを使用して、メディアのボリュームと再生速度を調整します。<xref:System.Windows.Controls.MediaElement.Volume%2A>  
  
 [!code-csharp[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaGallery_snip/CSharp/MediaElementExample.xaml.cs#codebehindmediaelementexamplewholepage)]
 [!code-vb[MediaGallery_snip#CodeBehindMediaElementExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MediaGallery_snip/VB/MediaElementExample.xaml.vb#codebehindmediaelementexamplewholepage)]  
  
## <a name="see-also"></a>関連項目

- [ストーリーボードを使用して MediaElement を制御する](how-to-control-a-mediaelement-by-using-a-storyboard.md)
