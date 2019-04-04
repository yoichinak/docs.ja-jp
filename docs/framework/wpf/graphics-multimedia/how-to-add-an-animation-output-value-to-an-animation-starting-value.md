---
title: '方法: アニメーションの出力値をアニメーションの開始値に追加する'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF]
ms.assetid: b89a82be-b03d-481e-a8d3-cc513d09ca00
ms.openlocfilehash: f27a214d4fa6fd33d993e7ae458ebb736b60bed7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57351958"
---
# <a name="how-to-add-an-animation-output-value-to-an-animation-starting-value"></a>方法: アニメーションの出力値をアニメーションの開始値に追加する
この例では、アニメーションの開始値をアニメーションの出力値を追加する方法を示します。  
  
## <a name="example"></a>例  
 <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A>プロパティをアニメーション化されたプロパティの開始値 (基本値) に追加するアニメーションの出力値にするかどうかを指定します。 使用することができます、<xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A>最も基本的なアニメーションとほとんどのキー フレーム アニメーションのプロパティ。 詳細については、[アニメーションの概要](animation-overview.md)と[キー フレーム アニメーションの概要](key-frame-animations-overview.md)を参照してください。  
  
 次の例を使用する効果を示しています、<xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A?displayProperty=nameWithType>プロパティ<xref:System.Windows.Media.Animation.DoubleAnimation>を使用して、<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsAdditive%2A?displayProperty=nameWithType>プロパティ<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>。  
  
 [!code-xaml[timingbehaviors_snip#IsAdditiveWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsAdditiveExample.xaml#isadditivewholepage)]  
  
## <a name="see-also"></a>関連項目
- [反復サイクル中にアニメーション値を累積する](how-to-accumulate-animation-values-during-repeat-cycles.md)
- [アニメーションの概要](animation-overview.md)
- [キー フレーム アニメーションの概要](key-frame-animations-overview.md)
- [アニメーションとタイミングに関するトピック](animation-and-timing-how-to-topics.md)
