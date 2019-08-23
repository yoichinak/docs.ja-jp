---
title: '方法: キー フレームを使用して行列をアニメーション化する'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
ms.openlocfilehash: 6aa3e27cdfda7597c9b6acbf2980a2774f2b667b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963025"
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a>方法: キー フレームを使用して行列をアニメーション化する
この例では、 <xref:System.Windows.Media.MatrixTransform.Matrix%2A> <xref:System.Windows.Media.MatrixTransform>キーフレームを使用してのプロパティをアニメーション化する方法を示します。  
  
## <a name="example"></a>例  
 <xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames>クラスを使用しての<xref:System.Windows.Media.MatrixTransform.Matrix%2A> <xref:System.Windows.Media.MatrixTransform>プロパティをアニメーション化する例を次に示します。 この例では<xref:System.Windows.Media.MatrixTransform> 、オブジェクトを使用して、 <xref:System.Windows.Controls.Button>の外観と位置を変換します。  
  
 このアニメーションでは<xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame> 、クラスを使用して2つのキーフレームを作成し、次のことを行います。  
  
1. 最初の 0.2 <xref:System.Windows.Media.Matrix>秒間に最初のをアニメーション化します。 この例では<xref:System.Windows.Media.Matrix.M11%2A> 、 <xref:System.Windows.Media.Matrix.M12%2A>の<xref:System.Windows.Media.Matrix>プロパティとプロパティを変更します。 この変更により、ボタンが伸縮され、傾斜します。 また、この例で<xref:System.Windows.Media.Matrix.OffsetX%2A>は<xref:System.Windows.Media.Matrix.OffsetY%2A> 、ボタンが位置を変更するようにプロパティとプロパティを変更します。  
  
2. 2番目<xref:System.Windows.Media.Matrix>のを1.0 秒でアニメーション化します。 ボタンが傾斜または拡大されていなくても、ボタンは別の位置に移動します。  
  
3. アニメーションを無制限に繰り返します。  
  
> [!NOTE]
> <xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame>オブジェクトから派生したキーフレームは、値の間に急激なジャンプを作成します。つまり、アニメーションの動きが不自然になります。  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 サンプル全体については、「[キーフレーム アニメーションのサンプル](https://go.microsoft.com/fwlink/?LinkID=160012)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.MatrixTransform.Matrix%2A>
- <xref:System.Windows.Media.MatrixTransform>
- [キー フレーム アニメーションの概要](key-frame-animations-overview.md)
- [キー フレームに関する「方法」トピック](key-frame-animation-how-to-topics.md)
