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
ms.openlocfilehash: 10e177d1f6d6add4638ce14af900e75d7e363890
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59150736"
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
