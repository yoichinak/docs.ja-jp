---
title: '方法: "From"、"To"、および "By" を使用してアニメーションを制御する'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], From/to/by
- basic animation [WPF]
- animation [WPF], basic animation
- From/to/by animation
ms.assetid: 59afba57-6fc1-44c8-987e-8a5f4142adad
ms.openlocfilehash: 812217a2905671567271687b974a435dd85cea47
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930082"
---
# <a name="how-to-control-an-animation-using-from-to-and-by"></a>方法: "From"、"To"、および "By" を使用してアニメーションを制御する
"From/To/By" または "基本アニメーション" は、2つのターゲット値の間の遷移を作成します (さまざまな種類のアニメーションの概要については、「[アニメーションの概要](animation-overview.md)」を参照してください)。 基本的なアニメーションのターゲット値を設定するには、 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>、 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>、および<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>の各プロパティを使用します。  次の表は<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>、、 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>、および<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>の各プロパティを組み合わせて使用して、アニメーションのターゲット値を決定する方法をまとめたものです。  
  
|指定するプロパティ|結果として生じる動作|  
|--------------------------|------------------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>|アニメーションは、前のアニメーションがどのよう<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>に構成されているかに応じて、アニメーション化するプロパティの基本値、または前のアニメーションの出力値に、プロパティによって指定された値から進みます。|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> および <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|アニメーションは、 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>プロパティによって指定された値から、 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>プロパティによって指定された値に進みます。|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> および <xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|アニメーションは、 <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>プロパティによって指定された値から、プロパティ<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>と<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>プロパティの合計によって指定された値に進みます。|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>|アニメーションは、アニメーション化されたプロパティの基本値または前のアニメーションの出力値から、 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>プロパティで指定された値に進行します。|  
|<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>|アニメーションは、アニメーション化されているプロパティの基本値または前のアニメーションの出力値から、その値と<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>プロパティで指定された値の合計まで進行します。|  
  
> [!NOTE]
> 同じアニメーションで、 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>プロパティ<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>とプロパティの両方を設定しないでください。  
  
 他の補間方式を使用したり、3 つ以上のターゲット値の間でアニメーション化したりするには、キー フレーム アニメーションを使用します。 詳細については[、「キーフレームアニメーションの概要](key-frame-animations-overview.md)」を参照してください。  
  
 1つのプロパティに複数のアニメーションを適用する方法の詳細については、「[キーフレームアニメーションの概要](key-frame-animations-overview.md)」を参照してください。  
  
 次の例は、アニメーションのプロパティ、 <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>プロパティ<xref:System.Windows.Media.Animation.DoubleAnimation.By%2A>、および<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>プロパティを設定した場合のさまざまな効果を示しています。  
  
## <a name="example"></a>例  
 [!code-xaml[BasicAnimations_snippet#AnimationTargetValuesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snippet/CS/AnimationTargetValuesExample.xaml#animationtargetvalueswholepage)]  
  
## <a name="see-also"></a>関連項目

- [アニメーションの概要](animation-overview.md)
- [キー フレーム アニメーションの概要](key-frame-animations-overview.md)
- [アニメーションのターゲット値 (From、To、および By) のサンプル](https://go.microsoft.com/fwlink/?LinkID=159988)
