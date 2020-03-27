---
title: '方法 : キー フレームを使用して行列をアニメーション化する'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
ms.openlocfilehash: eb596cf728f8a7cc1964963b8509f42bdd7a392a
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344915"
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a>方法 : キー フレームを使用して行列をアニメーション化する
この例では、キー フレームを使用<xref:System.Windows.Media.MatrixTransform.Matrix%2A>して a<xref:System.Windows.Media.MatrixTransform>のプロパティをアニメーション化する方法を示します。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames>クラスを使用して、<xref:System.Windows.Media.MatrixTransform.Matrix%2A>のプロパティを<xref:System.Windows.Media.MatrixTransform>アニメーション化します。 この例では、<xref:System.Windows.Media.MatrixTransform>オブジェクトを使用して、 の外観と<xref:System.Windows.Controls.Button>位置を変換します。  
  
 このアニメーションでは、<xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame>クラスを使用して 2 つのキー フレームを作成し、次の処理を行います。  
  
1. 最初の 0.2 秒間に最初<xref:System.Windows.Media.Matrix>のアニメーションを実行します。 この例では、 <xref:System.Windows.Media.Matrix.M11%2A> <xref:System.Windows.Media.Matrix.M12%2A>の プロパティ<xref:System.Windows.Media.Matrix>と プロパティを変更します。 この変更により、ボタンが伸びて傾斜します。 また、ボタンの位置<xref:System.Windows.Media.Matrix.OffsetX%2A>が<xref:System.Windows.Media.Matrix.OffsetY%2A>変更されるように、 および プロパティも変更します。  
  
2. 2 番目<xref:System.Windows.Media.Matrix>のアニメーションを 1.0 秒でアニメーション化します。 ボタンが傾斜または伸びない間、ボタンが別の位置に移動します。  
  
3. アニメーションを無期限に繰り返します。  
  
> [!NOTE]
> オブジェクトから派生した<xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame>キーフレームは、値の間に突然ジャンプを作成します。  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 サンプル全体については、「[キーフレーム アニメーションのサンプル](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.MatrixTransform.Matrix%2A>
- <xref:System.Windows.Media.MatrixTransform>
- [キー フレーム アニメーションの概要](key-frame-animations-overview.md)
- [キー フレームに関する「方法」トピック](key-frame-animation-how-to-topics.md)
