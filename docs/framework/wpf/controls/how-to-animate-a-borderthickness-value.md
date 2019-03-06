---
title: '方法: BorderThickness 値をアニメーション化する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- border thickness [WPF], animating changes to
- animation [WPF], changes to border thickness
ms.assetid: fd021978-f74b-4e7b-a7f7-3987dcad9e0f
ms.openlocfilehash: 4f38895f58e1a41a8a66b31a116e94f5b02492f7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57368939"
---
# <a name="how-to-animate-a-borderthickness-value"></a>方法: BorderThickness 値をアニメーション化する
この例を使用して境界線の太さに変更をアニメーション化する方法を示しています、<xref:System.Windows.Media.Animation.ThicknessAnimation>クラス。  
  
## <a name="example"></a>例  
 次の例を使用して境界線の太さをアニメーション化<xref:System.Windows.Media.Animation.ThicknessAnimation>します。 この例では、<xref:System.Windows.Controls.Border.BorderThickness%2A>プロパティの<xref:System.Windows.Controls.Border>します。  
  
 [!code-csharp[BasicAnimations_snip#ThicknessAnimationWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/ThicknessAnimationExample.cs#thicknessanimationwholepage)]
 [!code-vb[BasicAnimations_snip#ThicknessAnimationWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/ThicknessAnimationExample.vb#thicknessanimationwholepage)]  
  
 サンプル全体については、次を参照してください。[アニメーション サンプル ギャラリー](https://go.microsoft.com/fwlink/?LinkID=159969)します。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Media.Animation.ThicknessAnimation>
- <xref:System.Windows.Controls.Border.BorderThickness%2A>
- <xref:System.Windows.Controls.Border>
- [アニメーションの概要](../graphics-multimedia/animation-overview.md)
- [アニメーションとタイミングに関するトピック](../graphics-multimedia/animation-and-timing-how-to-topics.md)
- [キー フレームを使用して境界線の太さをアニメーション化する](../graphics-multimedia/how-to-animate-the-thickness-of-a-border-by-using-key-frames.md)
