---
title: '方法 : キー フレームを使用して Double 値をアニメーション化する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Doubles [WPF], animating with key frames
- animation [WPF], Doubles with key frames
- key frames [WPF], animating Doubles with
ms.assetid: 3a1a7dba-7694-4907-8a2f-3408baebfa82
ms.openlocfilehash: 9eab794cc8411230226cddc97beaa13c1bdd9405
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344929"
---
# <a name="how-to-animate-a-double-by-using-key-frames"></a>方法 : キー フレームを使用して Double 値をアニメーション化する
この例では、キー フレームを使用<xref:System.Double>して を取得するプロパティの値をアニメーション化する方法を示します。  
  
## <a name="example"></a>例  
 次の例では、画面を横切るように四角形を移動します。 この例では、<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>このクラスを使用して、<xref:System.Windows.Media.TranslateTransform.X%2A>に適用<xref:System.Windows.Media.TranslateTransform>される プロパティ<xref:System.Windows.Shapes.Rectangle>をアニメーション化します。 無期限に繰り返すこのアニメーションでは、次の方法で 3 つのキー フレームを使用します。  
  
1. 最初の 3 秒間に、クラスのインスタンス<xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>を使用して、開始位置から 500 の位置に、パスに沿って四角形を安定した速度で移動します。 線形キー フレーム<xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>のような値間のスムーズな直線遷移を作成します。  
  
2. 4 秒目の終わりには、クラスのインスタンスを<xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>使用して、突然四角形を次の位置に移動します。 値の間に<xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>突然ジャンプを作成するような離散的なキー フレーム。 この例では、開始位置にあった四角形が突然 500 の位置に出現します。  
  
3. 最後の 2 秒で、クラスのインスタンス<xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>を使用して、四角形を開始位置に戻します。 スプライン キー<xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>フレームのような値の間に、プロパティの値に従<xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A>った可変的な遷移を作成します。 この例では、四角形の動きは最初はゆっくりしていますが、時間セグメントの終点に向かった急激に速くなります。  
  
 [!code-csharp[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/AltDoubleAnimationUsingKeyFramesExample.cs#altdoubleanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/altdoubleanimationusingkeyframesexample.vb#altdoubleanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/AltDoubleAnimationUsingKeyFramesExample.xaml#altdoubleanimationusingkeyframeswholepage)]  
  
 サンプル全体については、「[キーフレーム アニメーションのサンプル](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)」を参照してください。  
  
 他のアニメーションの例との一貫性を保つために、この例<xref:System.Windows.Media.Animation.Storyboard>のコード バージョン<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>ではオブジェクトを使用して を適用します。 または、コード内で単一のアニメーションを適用する場合は、<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A><xref:System.Windows.Media.Animation.Storyboard>メソッドを使用する代わりに、より簡単に使用できます。 例については、「[ストーリーボードを使用せずにプロパティをアニメーション化する](how-to-animate-a-property-without-using-a-storyboard.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>
- <xref:System.Windows.Shapes.Rectangle>
- <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>
- <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>
- [キー フレーム アニメーションの概要](key-frame-animations-overview.md)
- [キー フレームに関する「方法」トピック](key-frame-animation-how-to-topics.md)
