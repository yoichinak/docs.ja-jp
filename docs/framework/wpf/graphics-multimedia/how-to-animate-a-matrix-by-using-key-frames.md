---
title: '方法: キー フレームを使用して行列をアニメーション化する'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], Matrix properties with key frames
- Matrix properties [WPF], animating with key frames
- key frames [WPF], animating Matrix properties with
ms.assetid: b851a4c7-ecb1-420e-9203-83e7afd037fd
ms.openlocfilehash: 8cc94117cc26f44288835fd85c6ded429124d3c6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107927"
---
# <a name="how-to-animate-a-matrix-by-using-key-frames"></a>方法: キー フレームを使用して行列をアニメーション化する
この例は、アニメーション化する方法を示しています。、<xref:System.Windows.Media.MatrixTransform.Matrix%2A>のプロパティを<xref:System.Windows.Media.MatrixTransform>キー フレームを使用しています。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames>をアニメーション化するクラス、<xref:System.Windows.Media.MatrixTransform.Matrix%2A>のプロパティを<xref:System.Windows.Media.MatrixTransform>します。 この例では、<xref:System.Windows.Media.MatrixTransform>の位置と外観を変換するオブジェクト、<xref:System.Windows.Controls.Button>します。  
  
 このアニメーションを使用して、<xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame>クラスの 2 つのキー フレームを作成して、それらを使用して、次は。  
  
1.  最初のアニメーション<xref:System.Windows.Media.Matrix>最初 0.2 秒間にします。 例の変更、<xref:System.Windows.Media.Matrix.M11%2A>と<xref:System.Windows.Media.Matrix.M12%2A>のプロパティ、<xref:System.Windows.Media.Matrix>します。 この変更により、拡大し、傾斜するボタンをクリックします。 また、<xref:System.Windows.Media.Matrix.OffsetX%2A>と<xref:System.Windows.Media.Matrix.OffsetY%2A>プロパティ、ボタンの位置を変更するようにします。  
  
2.  2 番目のアニメーション<xref:System.Windows.Media.Matrix>1.0 秒。 ボタンは、ボタンが不要になった傾斜や拡大中に別の位置に移動します。  
  
3.  アニメーションを無限に繰り返されます。  
  
> [!NOTE]
>  キー フレームから派生した、<xref:System.Windows.Media.Animation.DiscreteMatrixKeyFrame>オブジェクトの値の間に急なジャンプを作成する、つまり、アニメーションの動きはぎくしゃくします。  
  
 [!code-xaml[keyframes_snip#MatrixAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/MatrixAnimationUsingKeyFramesExample.xaml#matrixanimationusingkeyframeswholepage)]  
  
 サンプル全体については、「[キーフレーム アニメーションのサンプル](https://go.microsoft.com/fwlink/?LinkID=160012)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.MatrixTransform.Matrix%2A>
- <xref:System.Windows.Media.MatrixTransform>
- [キー フレーム アニメーションの概要](key-frame-animations-overview.md)
- [キー フレームに関する「方法」トピック](key-frame-animation-how-to-topics.md)
