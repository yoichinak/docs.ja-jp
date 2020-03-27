---
title: '方法 : キー フレームを使用してオブジェクトをアニメーション化する'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
ms.openlocfilehash: 0bc33b189fd856dbe8106c1db35bc18e27ea131e
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344702"
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a>方法 : キー フレームを使用してオブジェクトをアニメーション化する
この例では、キー フレームを使用してコントロールの<xref:System.Windows.Controls.Page.Background%2A>プロパティであるオブジェクトをアニメーション化する方法<xref:System.Windows.Controls.Page>を次の例に示します。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>このクラスを使用して、コントロールのプロパティ<xref:System.Windows.Controls.Page.Background%2A>の色の<xref:System.Windows.Controls.Page>変更をアニメーション化します。 アニメーション例は、一定の間隔で別の背景ブラシに変更されます。 このアニメーションでは、<xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>クラスを使用して 3 つの異なるキー フレームを作成します。 アニメーションでは、次のようにキー フレームを使用します。  
  
1. 最初の 1 秒目の終わりに、クラスのインスタンスを<xref:System.Windows.Media.LinearGradientBrush>アニメーション化します。 このセクションでは、背景色に線形グラデーションを適用し、色が黄色からオレンジ色から赤に変わります。  
  
2. 次の 1 秒の終わりに、クラスのインスタンスをアニメーション<xref:System.Windows.Media.RadialGradientBrush>化します。 このセクションでは、背景色に放射状グラデーションを適用し、色が白から青から黒に変わります。  
  
3. 3 秒目の終わりに、クラスのインスタンスをアニメーション化します<xref:System.Windows.Media.DrawingBrush>。 このセクションでは、背景にチェッカーボードパターンを適用します。  
  
4. アニメーションは再び開始され、無限に繰り返されます。  
  
> [!NOTE]
> <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>は、クラスで使用できる唯一のタイプのキー<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>フレームです。 キー フレーム<xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>のような値の急激な変化、つまりこの例の色の変化が突然発生します。  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 サンプル全体については、「[キーフレーム アニメーションのサンプル](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>
- <xref:System.Windows.Controls.Page.Background%2A>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>
- <xref:System.Windows.Media.LinearGradientBrush>
- <xref:System.Windows.Media.RadialGradientBrush>
- <xref:System.Windows.Media.DrawingBrush>
- [キー フレーム アニメーションの概要](key-frame-animations-overview.md)
- [キー フレームに関する「方法」トピック](key-frame-animation-how-to-topics.md)
