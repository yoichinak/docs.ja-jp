---
title: '方法: キー フレーム アニメーションのタイミングを制御する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], timing
- timing key-fram animation
ms.assetid: b059216f-7d4b-4ca8-a019-bc287ee7bf16
ms.openlocfilehash: 02171c4e2bf444d0bd31bc53fab9d451f081a93c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57353726"
---
# <a name="how-to-control-key-frame-animation-timing"></a>方法: キー フレーム アニメーションのタイミングを制御する
この例では、キー フレーム アニメーション内のキー フレームのタイミングを制御する方法を示します。 キー フレーム アニメーションがあるその他のアニメーションと同様に、<xref:System.Windows.Media.Animation.Timeline.Duration%2A>プロパティ。 アニメーションの継続時間を指定するだけでなくその時間の部分がそのキー フレームのそれぞれに割り当てられた時間を指定する必要があります。 指定した時間を割り当てる、<xref:System.Windows.Media.Animation.KeyTime>の各キー フレーム アニメーションにします。  
  
 <xref:System.Windows.Media.Animation.KeyTime> (は指定しませんキー フレームの再生時間の長さ) のキー フレームの終了時に、各キー フレームが指定します。 指定することができます、<xref:System.Windows.Media.Animation.KeyTime>として、<xref:System.TimeSpan>値、パーセンテージまたはとして、<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>または<xref:System.Windows.Media.Animation.KeyTime.Paced%2A>特殊な値。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>を画面上で四角形をアニメーション化します。 キー フレームのキー時刻が設定されて<xref:System.TimeSpan>値。  
  
 [!code-csharp[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimestimespanexample)]
 [!code-vb[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimestimespanexample)]
 [!code-xaml[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimestimespanexample)]  
  
 次の図の各キー フレームの値に達するとを示します。  
  
 ![キーの値が 3、4、および 10 秒の位置に到達](./media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm_keyframe_keytime1_timespan")  
  
 次の例では、パーセンテージの値でキー フレームのキー時刻を設定する点を除いて同じですが、あるアニメーションを示します。  
  
 [!code-csharp[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespercentageexample)]
 [!code-vb[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespercentageexample)]
 [!code-xaml[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespercentageexample)]  
  
 次の図の各キー フレームの値に達するとを示します。  
  
 ![キーの値が 3、4、および 10 秒の位置に到達](./media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm_keyframe_keytime2_percentage")  
  
 次の例では<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>キー時刻値。  
  
 [!code-csharp[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimesuniformexample)]
 [!code-vb[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimesuniformexample)]
 [!code-xaml[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimesuniformexample)]  
  
 次の図の各キー フレームの値に達するとを示します。  
  
 ![キーの値に達すると 3.3、6.6、および 9.9 秒](./media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm_keyframe_keytime3_uniform")  
  
 最後の例を使用して<xref:System.Windows.Media.Animation.KeyTime.Paced%2A>キー時刻値。  
  
 [!code-csharp[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespacedexample)]
 [!code-vb[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespacedexample)]
 [!code-xaml[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespacedexample)]  
  
 次の図の各キー フレームの値に達するとを示します。  
  
 ![キーの値が 0、5、および 10 秒の位置に到達](./media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm_keyframe_keytime4_paced")  
  
 わかりやすくするため、この例を使用してローカル、アニメーションのコードでは、いないストーリー ボードを 1 つのアニメーションを 1 つのプロパティに適用されているが、ストーリー ボードを代わりに使用する例を変更する可能性があります。 コード内のストーリー ボードを宣言する方法を示す例は、次を参照してください。[ストーリー ボードを使用してプロパティをアニメーション化する](how-to-animate-a-property-by-using-a-storyboard.md)します。  
  
 サンプル全体については、「[キーフレーム アニメーションのサンプル](https://go.microsoft.com/fwlink/?LinkID=160012)」を参照してください。 キー フレーム アニメーションの詳細については、次を参照してください。、[キー フレーム アニメーションの概要](key-frame-animations-overview.md)します。  
  
## <a name="see-also"></a>関連項目
- [キー フレーム アニメーションの概要](key-frame-animations-overview.md)
- [アニメーションの概要](animation-overview.md)
- [方法トピック](animation-and-timing-how-to-topics.md)
