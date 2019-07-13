---
title: '方法: ストーリーボードを使用せずにプロパティをアニメーション化する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- non-Storyboard animation
- local animation [WPF]
- animation [WPF], non-Storyboard (local)
ms.assetid: d411db70-4df7-487d-82bc-95a7c1b2e7f8
ms.openlocfilehash: 93609cdeb4d879cbec0f90096e4fa2c131a2ec5e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761287"
---
# <a name="how-to-animate-a-property-without-using-a-storyboard"></a>方法: ストーリーボードを使用せずにプロパティをアニメーション化する
この例を使用せず、プロパティにアニメーションを適用する 1 つの方法を示しています、<xref:System.Windows.Media.Animation.Storyboard>します。  
  
> [!NOTE]
>  この機能は、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] では使用できません。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] でプロパティをアニメーション化する方法については、「[ストーリーボードを使ってプロパティをアニメーション化する](how-to-animate-a-property-by-using-a-storyboard.md)」を参照してください。  
  
 ローカル アニメーションをプロパティに適用するには、使用、<xref:System.Windows.UIElement.BeginAnimation%2A>メソッド。 このメソッドは、2 つのパラメーター: <xref:System.Windows.DependencyProperty> 、アニメーション化するプロパティとそのプロパティに適用するアニメーションを指定します。  
  
## <a name="example"></a>例  
 次の例の幅と背景色をアニメーション化する方法を示しています、<xref:System.Windows.Controls.Button>します。  
  
 [!code-cpp[animateproperty#11](~/samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](~/samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
 さまざまなアニメーションのクラス、<xref:System.Windows.Media.Animation>名前空間が異なる種類のプロパティをアニメーション化するために存在します。 プロパティのアニメーション化の詳細については、「[アニメーションの概要](animation-overview.md)」を参照してください。 依存関係プロパティ (これらの例に示されているプロパティの種類) とその機能の詳細については、「[依存関係プロパティの概要](../advanced/dependency-properties-overview.md)」を参照してください。  
  
 使用せずにアニメーション化するには、他の方法はあります<xref:System.Windows.Media.Animation.Storyboard>オブジェクト。 詳細については、次を参照してください。[プロパティ アニメーションの手法の概要](property-animation-techniques-overview.md)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Animation.AnimationTimeline>
- <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Animation.Storyboard>
- [プロパティ アニメーションの手法の概要](property-animation-techniques-overview.md)
- [アニメーションの概要](animation-overview.md)
