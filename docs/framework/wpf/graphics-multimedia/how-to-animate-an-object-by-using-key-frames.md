---
title: '方法: キー フレームを使用してオブジェクトをアニメーション化する'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
ms.openlocfilehash: ffbe1845b634c8f94eb6a10dfa44fcf9903e0cd5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933906"
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a>方法: キー フレームを使用してオブジェクトをアニメーション化する
この例では、キーフレームを使用して、オブジェクト (この<xref:System.Windows.Controls.Page.Background%2A>例では<xref:System.Windows.Controls.Page>コントロールのプロパティ) をアニメーション化する方法を示します。  
  
## <a name="example"></a>例  
 次の例では<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> 、クラスを使用して、 <xref:System.Windows.Controls.Page.Background%2A> <xref:System.Windows.Controls.Page>コントロールのプロパティの色の変更をアニメーション化しています。 この例のアニメーションは、一定の間隔で別の背景ブラシに変わります。 このアニメーションでは<xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> 、クラスを使用して、3つの異なるキーフレームを作成します。 アニメーションは、次の方法でキーフレームを使用します。  
  
1. 最初の秒の最後に、 <xref:System.Windows.Media.LinearGradientBrush>クラスのインスタンスをアニメーション化します。 この例のこのセクションでは、色が黄色からオレンジ色に変化するように、背景色に線状グラデーションを適用します。  
  
2. 次の秒の最後に、 <xref:System.Windows.Media.RadialGradientBrush>クラスのインスタンスをアニメーション化します。 この例のこのセクションでは、色が白から青に変化するように背景色に放射状グラデーションを適用します。  
  
3. 3番目の秒の最後に、 <xref:System.Windows.Media.DrawingBrush>クラスのインスタンスをアニメーション化します。 この例のこのセクションでは、背景にチェッカーボードパターンを適用します。  
  
4. アニメーションは再び開始され、無限に繰り返されます。  
  
> [!NOTE]
> <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>は、 <xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>クラスで使用できるキーフレームの唯一の種類です。 値が急激<xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>に変化するようなキーフレーム (この例の色の変化) は突然発生します。  
  
 [!code-xaml[keyframes_snip#ObjectAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ObjectAnimationUsingKeyFramesExample.xaml#objectanimationusingkeyframeswholepage)]  
  
 サンプル全体については、「[キーフレーム アニメーションのサンプル](https://go.microsoft.com/fwlink/?LinkID=160012)」を参照してください。  
  
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
