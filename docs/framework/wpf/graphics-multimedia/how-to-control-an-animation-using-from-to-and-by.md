---
title: '方法: "From"、"To"、および "By" を使用してアニメーションを制御する'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], From/to/by
- basic animation [WPF]
- animation [WPF], basic animation
- From/to/by animation
ms.assetid: 59afba57-6fc1-44c8-987e-8a5f4142adad
ms.openlocfilehash: 56522ee5bd4391e43c261558b2fa622234c9ea3b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59073273"
---
# <a name="how-to-control-an-animation-using-from-to-and-by"></a>方法: "From"、"To"、および "By" を使用してアニメーションを制御する
"から/に/By"または「基本アニメーション」が 2 つのターゲット値の間の遷移を作成します (を参照してください[アニメーションの概要](animation-overview.md)さまざまな種類のアニメーションの概要について)。 基本的なアニメーションのターゲット値を設定する次のように使用します。 その<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>、 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>、および<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>プロパティ。  次の表にまとめたものですが、どのように<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>、 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>、および<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>プロパティを同時に使用することや、個別に、アニメーションのターゲットを決定する値します。  
  
|指定するプロパティ|結果として生じる動作|  
|--------------------------|------------------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>|によって指定された値からアニメーション、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>プロパティをアニメーション化されているプロパティの基本値または前のアニメーションの前のアニメーションの構成方法に応じて、値を出力します。|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> および <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|によって指定された値からアニメーション、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>プロパティによって指定された値を<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>プロパティ。|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> および <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|によって指定された値からアニメーション、<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>プロパティの合計によって指定された値を<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>と<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>プロパティ。|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|アニメーションがアニメーション化されたプロパティの基本値から、または前のアニメーションの出力値を指定する値を<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>プロパティ。|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|出力値で指定された値の合計に値をアニメーション化されているプロパティの基準値からアニメーション、または前のアニメーション、<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>プロパティ。|  
  
> [!NOTE]
>  両方を設定しないでください、<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>プロパティおよび<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>同じアニメーションのプロパティ。  
  
 他の補間方式を使用したり、3 つ以上のターゲット値の間でアニメーション化したりするには、キー フレーム アニメーションを使用します。 参照してください[キー フレーム アニメーションの概要](key-frame-animations-overview.md)詳細についてはします。  
  
 1 つのプロパティに複数のアニメーションを適用する方法の詳細については、次を参照してください。[キー フレーム アニメーションの概要](key-frame-animations-overview.md)します。  
  
 次の例は、さまざまな設定の効果を示しています。 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>、 <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>、および<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>アニメーションのプロパティ。  
  
## <a name="example"></a>例  
 [!code-xaml[BasicAnimations_snippet#AnimationTargetValuesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snippet/CS/AnimationTargetValuesExample.xaml#animationtargetvalueswholepage)]  
  
## <a name="see-also"></a>関連項目

- [アニメーションの概要](animation-overview.md)
- [キー フレーム アニメーションの概要](key-frame-animations-overview.md)
- [アニメーションのターゲット値 (From、To、および By) のサンプル](https://go.microsoft.com/fwlink/?LinkID=159988)
