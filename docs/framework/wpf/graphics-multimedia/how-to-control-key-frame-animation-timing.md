---
title: '方法 : キー フレーム アニメーションのタイミングを制御する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], timing
- timing key-frame animation
ms.assetid: b059216f-7d4b-4ca8-a019-bc287ee7bf16
ms.openlocfilehash: 8cfd2be0bbc526ed92a5fb1b558a5a41dc9c3113
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344736"
---
# <a name="how-to-control-key-frame-animation-timing"></a>方法 : キー フレーム アニメーションのタイミングを制御する

この例では、キー フレーム アニメーション内のキー フレームのタイミングを制御する方法を示します。 他のアニメーションと同様に、キー フレーム アニメーション<xref:System.Windows.Media.Animation.Timeline.Duration%2A>にもプロパティがあります。 アニメーションの継続時間を指定するだけでなく、その期間の各キーフレームに割り当てる部分を指定する必要があります。 時間を割り当てるには、アニメーション<xref:System.Windows.Media.Animation.KeyTime>の各キー フレームに 対して を指定します。

各<xref:System.Windows.Media.Animation.KeyTime>キー フレームのキー フレームは、いつキー フレームが終了するかを指定します (キー フレームが再生される時間の長さは指定しません)。 値<xref:System.Windows.Media.Animation.KeyTime>、<xref:System.TimeSpan>パーセント、または<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A><xref:System.Windows.Media.Animation.KeyTime.Paced%2A>特殊値として指定できます。

## <a name="example"></a>例

次の例では、<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>を使用して、画面上の四角形をアニメーション化します。 キー フレームのキータイムは値で<xref:System.TimeSpan>設定されます。

[!code-csharp[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimestimespanexample)]
[!code-vb[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimestimespanexample)]
[!code-xaml[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimestimespanexample)]

次の図は、各キー フレームの値に達したときを示しています。

![キー値は 3 秒、4 秒、および 10 秒です](./media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm_keyframe_keytime1_timespan")

次の例では、キー フレームのキータイムがパーセンテージ値で設定される点を除いて、同一のアニメーションを示します。

[!code-csharp[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespercentageexample)]
[!code-vb[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespercentageexample)]
[!code-xaml[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespercentageexample)]

次の図は、各キー フレームの値に達したときを示しています。

![キー値は 3 秒、4 秒、および 10 秒です](./media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm_keyframe_keytime2_percentage")

次の例では<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>、キー時間値を使用します。

[!code-csharp[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimesuniformexample)]
[!code-vb[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimesuniformexample)]
[!code-xaml[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimesuniformexample)]

次の図は、各キー フレームの値に達したときを示しています。

![キー値は 3.3 秒、6.6 秒、および 9.9 秒です](./media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm_keyframe_keytime3_uniform")

最後の例では<xref:System.Windows.Media.Animation.KeyTime.Paced%2A>、キー時間値を使用します。

[!code-csharp[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespacedexample)]
[!code-vb[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespacedexample)]
[!code-xaml[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespacedexample)]

次の図は、各キー フレームの値に達したときを示しています。

![キー値は 0 秒、5 秒、および 10 秒です](./media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm_keyframe_keytime4_paced")

わかりやすくするために、この例のコード バージョンでは、1 つのプロパティに適用されるアニメーションは 1 つだけであるため、ストーリーボードではなくローカル アニメーションが使用されますが、代わりにストーリーボードを使用するように変更できます。 コードでストーリーボードを宣言する方法の例については、「[ストーリーボードを使用してプロパティをアニメーション化](how-to-animate-a-property-by-using-a-storyboard.md)する 」を参照してください。

サンプル全体については、「[キーフレーム アニメーションのサンプル](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)」を参照してください。 キー フレーム アニメーションの詳細については、「 キー フレーム[アニメーションの概要](key-frame-animations-overview.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [キー フレーム アニメーションの概要](key-frame-animations-overview.md)
- [アニメーションの概要](animation-overview.md)
- [方法のトピック](animation-and-timing-how-to-topics.md)
