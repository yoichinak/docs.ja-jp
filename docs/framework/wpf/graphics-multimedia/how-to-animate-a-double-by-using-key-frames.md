---
title: '方法: キー フレームを使用して Double 値をアニメーション化する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Doubles [WPF], animating with key frames
- animation [WPF], Doubles with key frames
- key frames [WPF], animating Doubles with
ms.assetid: 3a1a7dba-7694-4907-8a2f-3408baebfa82
ms.openlocfilehash: 73cbeab8aee566313bad8e8a18a5500374287de0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59305586"
---
# <a name="how-to-animate-a-double-by-using-key-frames"></a>方法: キー フレームを使用して Double 値をアニメーション化する
この例を受け取るプロパティの値をアニメーション化する方法を示しています、<xref:System.Double>キー フレームを使用しています。  
  
## <a name="example"></a>例  
 次の例では、画面を横切るように四角形を移動します。 この例では、<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>をアニメーション化するクラス、<xref:System.Windows.Media.TranslateTransform.X%2A>のプロパティを<xref:System.Windows.Media.TranslateTransform>に適用される、 <xref:System.Windows.Shapes.Rectangle>。 無期限に繰り返すこのアニメーションでは、次の方法で 3 つのキー フレームを使用します。  
  
1. 最初の 3 秒のインスタンスを使用して、<xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>クラス パスに沿った四角形の開始位置からの一定の速度で 500 の位置に移動します。 などの線形キーフレーム<xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>値の間の滑らかな線形トランジションを作成します。  
  
2. 4 番目の 2 つ目の末尾にはのインスタンスを使用して、<xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>クラスに次の位置に突然四角形を移動します。 などの不連続のキーフレーム<xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>値の間に急なジャンプを作成します。 この例では、開始位置にあった四角形が突然 500 の位置に出現します。  
  
3. 最後の 2 秒では、インスタンスを使用して、<xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>クラスに四角形を開始位置に移動します。 スプライン キー フレームのような<xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>の値に基づいて値の間に可変遷移を作成、<xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A>プロパティ。 この例では、四角形の動きは最初はゆっくりしていますが、時間セグメントの終点に向かった急激に速くなります。  
  
 [!code-csharp[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/AltDoubleAnimationUsingKeyFramesExample.cs#altdoubleanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/altdoubleanimationusingkeyframesexample.vb#altdoubleanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/AltDoubleAnimationUsingKeyFramesExample.xaml#altdoubleanimationusingkeyframeswholepage)]  
  
 サンプル全体については、「[キーフレーム アニメーションのサンプル](https://go.microsoft.com/fwlink/?LinkID=160012)」を参照してください。  
  
 この例のコードを使用して、他のアニメーション例と一貫性を保つのため、<xref:System.Windows.Media.Animation.Storyboard>を適用するオブジェクト、<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>します。 または、コード内で 1 つのアニメーションを適用する場合は簡単に使用、<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>メソッドを使用してではなく、<xref:System.Windows.Media.Animation.Storyboard>します。 例については、「[ストーリーボードを使用せずにプロパティをアニメーション化する](how-to-animate-a-property-without-using-a-storyboard.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>
- <xref:System.Windows.Shapes.Rectangle>
- <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>
- <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>
- [キー フレーム アニメーションの概要](key-frame-animations-overview.md)
- [キー フレームに関する「方法」トピック](key-frame-animation-how-to-topics.md)
