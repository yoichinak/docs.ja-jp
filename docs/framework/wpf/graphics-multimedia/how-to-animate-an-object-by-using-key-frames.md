---
title: '方法: キー フレームを使用してオブジェクトをアニメーション化する'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], objects with key frames
- key frames [WPF], animating objects with
ms.assetid: b1f15ba9-cac7-4cea-8699-5c6b55c05c5e
ms.openlocfilehash: 0b2b517410c6cbc4f3deca13e5948c8de583fd3d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177802"
---
# <a name="how-to-animate-an-object-by-using-key-frames"></a>方法: キー フレームを使用してオブジェクトをアニメーション化する
この例があり、この例では、オブジェクトをアニメーション化する方法を示しています、<xref:System.Windows.Controls.Page.Background%2A>のプロパティを<xref:System.Windows.Controls.Page>キー フレームを使用して、コントロール。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>の色をアニメーション化するクラスを変更、<xref:System.Windows.Controls.Page.Background%2A>のプロパティを<xref:System.Windows.Controls.Page>コントロール。 例アニメーション一定の間隔で異なる背景ブラシに変更されます。 このアニメーションを使用して、 <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> 3 つの異なるキー フレームを作成するクラス。 アニメーションは、次のようにキー フレームを使用します。  
  
1.  最初の 2 つ目の末尾には、インスタンスをアニメーション化、<xref:System.Windows.Media.LinearGradientBrush>クラス。 例では、このセクションでは、色が赤にオレンジ色に黄色から移行できるように、背景色に線形グラデーションが適用されます。  
  
2.  次の 2 つ目の末尾には、インスタンスをアニメーション化、<xref:System.Windows.Media.RadialGradientBrush>クラス。 例では、このセクションでは、色が白から黒に青に移行できるように、背景色に放射状のグラデーションが適用されます。  
  
3.  3 番目の 2 つ目の末尾には、インスタンスをアニメーション化、<xref:System.Windows.Media.DrawingBrush>クラス。 例では、このセクションでは、背景をチェッカー ボード パターンが適用されます。  
  
4.  アニメーションが再び開始され、無限に繰り返されます。  
  
> [!NOTE]
>  <xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame> 唯一の種類のキー フレームで使用できるは、<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>クラス。 キー フレームのような<xref:System.Windows.Media.Animation.DiscreteObjectKeyFrame>値、つまり急激な変化を作成、この例では色の変更が突然発生します。  
  
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
