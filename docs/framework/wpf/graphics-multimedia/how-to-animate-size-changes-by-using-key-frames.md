---
title: '方法: キー フレームを使用してサイズの変更をアニメーション化する'
ms.date: 03/30/2017
helpviewer_keywords:
- key frames [WPF], animating size changes with
- animation [WPF], size changes with key frames
- size changes [WPF], animating with key frames
ms.assetid: 86bd2950-d4c9-4ec4-aa8d-7dc3ccadded4
ms.openlocfilehash: 0629b6600444bd172af451fd7e970bff894d8047
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789260"
---
# <a name="how-to-animate-size-changes-by-using-key-frames"></a>方法: キー フレームを使用してサイズの変更をアニメーション化する
この例では、キー フレームを使用してサイズの変更をアニメーション化する方法を示します。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>をアニメーション化するクラス、<xref:System.Windows.Media.ArcSegment.Size%2A>のプロパティ、<xref:System.Windows.Media.ArcSegment>します。 このアニメーションは、次の方法で 3 つのキー フレームを使用します。  
  
1. インスタンスを使用して、アニメーションの最初の 0.5 秒、<xref:System.Windows.Media.Animation.LinearSizeKeyFrame>クラスは、円弧のサイズを徐々 に増やします。などの線形キーフレーム<xref:System.Windows.Media.Animation.LinearSizeKeyFrame>値の間の滑らかな線形トランジションを作成します。  
  
2. インスタンスを使用している 0.5 秒は、次の最後に、<xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>クラスを突然、円弧のサイズを大ききます。などの不連続のキーフレーム<xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>されている値の間に急なジャンプを作成、サイズの変更が突然発生してはなく。  
  
3. インスタンスが使用する最後の 2 秒、<xref:System.Windows.Media.Animation.SplineSizeKeyFrame>円弧のサイズを大きくクラス。スプライン キー フレームのような<xref:System.Windows.Media.Animation.SplineSizeKeyFrame>の値に基づいて値の間に可変遷移を作成、<xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A>プロパティ。 この例では、円弧のサイズは最初はゆっくり大きくなりますが、時間セグメントの終点に向かって急激に大きくなります。  
  
 [!code-xaml[keyframes_snip#SizeAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/SizeAnimationUsingKeyFramesExample.xaml#sizeanimationusingkeyframeswholepage)]  
  
 サンプル全体については、「[キーフレーム アニメーションのサンプル](https://go.microsoft.com/fwlink/?LinkID=160012)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>
- <xref:System.Windows.Media.ArcSegment.Size%2A>
- <xref:System.Windows.Media.ArcSegment>
- <xref:System.Windows.Media.Animation.LinearSizeKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>
- <xref:System.Windows.Media.Animation.SplineSizeKeyFrame>
- [キー フレーム アニメーションの概要](key-frame-animations-overview.md)
- [キー フレームに関する「方法」トピック](key-frame-animation-how-to-topics.md)
