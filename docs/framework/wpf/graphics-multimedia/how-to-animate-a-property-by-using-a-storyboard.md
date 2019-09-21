---
title: '方法: ストーリーボードを使ってプロパティをアニメーション化する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], Storyboards
- Storyboards [WPF], animation
ms.assetid: f4a314e9-1da2-4367-85fc-1232487efa7a
ms.openlocfilehash: a7a2656d84d37d3e2726df009a07ccf29661df07
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963041"
---
# <a name="how-to-animate-a-property-by-using-a-storyboard"></a>方法: ストーリーボードを使ってプロパティをアニメーション化する
この例では、 <xref:System.Windows.Media.Animation.Storyboard>を使用してプロパティをアニメーション化する方法を示します。 を使用し<xref:System.Windows.Media.Animation.Storyboard>てプロパティをアニメーション化するには、アニメーション化するプロパティごとにアニメーションを作成し、 <xref:System.Windows.Media.Animation.Storyboard>アニメーションを格納するを作成することもできます。  
  
 プロパティの種類によって、使用するアニメーションの種類が決まります。 たとえば、値を受け取る<xref:System.Double>プロパティをアニメーション化するには、を<xref:System.Windows.Media.Animation.DoubleAnimation>使用します。 添付プロパティは、 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>アニメーションを適用するオブジェクトとプロパティを指定します。 <xref:System.Windows.Media.Animation.Storyboard.TargetProperty>  
  
 で[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ストーリーボードを開始するには<xref:System.Windows.Media.Animation.BeginStoryboard> 、アクションと<xref:System.Windows.EventTrigger>を使用します。 は<xref:System.Windows.EventTrigger> 、 <xref:System.Windows.EventTrigger.RoutedEvent%2A>プロパティ<xref:System.Windows.Media.Animation.BeginStoryboard>によって指定されたイベントが発生したときにアクションを開始します。 アクション<xref:System.Windows.Media.Animation.BeginStoryboard>は、を<xref:System.Windows.Media.Animation.Storyboard>開始します。  
  
 次の例で<xref:System.Windows.Media.Animation.Storyboard>は、オブジェクトを<xref:System.Windows.Controls.Button>使用して、2つのコントロールをアニメーション化します。 最初のボタンのサイズを変更するには<xref:System.Windows.FrameworkElement.Width%2A> 、そのボタンをアニメーション化します。 2番目のボタンの色<xref:System.Windows.Media.SolidColorBrush.Color%2A>を変更するには、のプロパティ<xref:System.Windows.Media.SolidColorBrush>を使用<xref:System.Windows.Controls.Control.Background%2A>して、アニメーション化されたボタンのを設定します。  
  
## <a name="example"></a>例  
 [!code-xaml[AnimatePropertyStoryboards#1](~/samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/StoryboardExample.xaml#1)]  
  
> [!NOTE]
> アニメーション<xref:System.Windows.FrameworkElement>は<xref:System.Windows.FrameworkElement.Name%2A>オブジェクト ( <xref:System.Windows.Controls.Control>や<xref:System.Windows.Controls.Panel>など) と<xref:System.Windows.Freezable>オブジェクト ( <xref:System.Windows.Media.Brush>や<xref:System.Windows.Media.Transform>など) の両方をターゲットにすることができますが、プロパティを持つのはフレームワーク要素だけです。 名前をフリーズ可能オブジェクトに割り当てて、アニメーションの対象にできるようにするには、前の例で示したように [x:Name ディレクティブ](../../xaml-services/x-name-directive.md)を使用します。  
  
 コードを使用する場合は、 <xref:System.Windows.NameScope> <xref:System.Windows.FrameworkElement>に対してを作成し、その<xref:System.Windows.FrameworkElement>オブジェクトの名前を登録してアニメーション化する必要があります。 コードでアニメーションを開始するには、 <xref:System.Windows.Media.Animation.BeginStoryboard> <xref:System.Windows.EventTrigger>でアクションを使用します。 必要に応じて、イベントハンドラーと<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>の<xref:System.Windows.Media.Animation.Storyboard>メソッドを使用できます。 <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> メソッドを使用する方法の例を次に示します。  
  
 [!code-csharp[AnimatePropertyStoryboards#11](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimatePropertyStoryboards/CSharp/StoryboardExample.cs#11)]
 [!code-vb[AnimatePropertyStoryboards#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AnimatePropertyStoryboards/VisualBasic/StoryboardExample.vb#11)]  
  
 アニメーションとストーリー ボードの詳細については、「[アニメーションの概要](animation-overview.md)」を参照してください。  
  
 コードを使用する場合、プロパティをアニメーション化する<xref:System.Windows.Media.Animation.Storyboard>ためにオブジェクトを使用するだけではありません。 使用例を含む詳細については、「[ストーリーボードを使用せずにプロパティをアニメーション化する](how-to-animate-a-property-without-using-a-storyboard.md)」と「[AnimationClock を使用してプロパティをアニメーション化する](how-to-animate-a-property-by-using-an-animationclock.md)」を参照してください。
