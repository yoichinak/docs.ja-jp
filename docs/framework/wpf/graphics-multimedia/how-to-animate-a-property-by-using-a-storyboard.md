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
ms.openlocfilehash: f6064368b4f5e4fa8324b4039d734d4430cd9174
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761209"
---
# <a name="how-to-animate-a-property-by-using-a-storyboard"></a>方法: ストーリーボードを使ってプロパティをアニメーション化する
この例は、使用する方法を示します、<xref:System.Windows.Media.Animation.Storyboard>プロパティをアニメーション化します。 使用してプロパティをアニメーション化する、 <xref:System.Windows.Media.Animation.Storyboard>、アニメーション化しても作成する各プロパティのアニメーションを作成、<xref:System.Windows.Media.Animation.Storyboard>アニメーションを格納します。  
  
 プロパティの種類によって、使用するアニメーションの種類が決まります。 受け取るプロパティをアニメーション化の例については<xref:System.Double>、値を使用して、<xref:System.Windows.Media.Animation.DoubleAnimation>します。 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>と<xref:System.Windows.Media.Animation.Storyboard.TargetProperty>添付プロパティは、オブジェクトと、アニメーションを適用するプロパティを指定します。  
  
 ストーリー ボードを起動する[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]を使用して、<xref:System.Windows.Media.Animation.BeginStoryboard>アクションと<xref:System.Windows.EventTrigger>します。 <xref:System.Windows.EventTrigger>開始、<xref:System.Windows.Media.Animation.BeginStoryboard>されるイベントのアクションで指定されたその<xref:System.Windows.EventTrigger.RoutedEvent%2A>プロパティに発生します。 <xref:System.Windows.Media.Animation.BeginStoryboard>アクションの開始、<xref:System.Windows.Media.Animation.Storyboard>します。  
  
 次の例では<xref:System.Windows.Media.Animation.Storyboard>2 つをアニメーション化するオブジェクト<xref:System.Windows.Controls.Button>コントロール。 最初のボタンのサイズを変更するため、<xref:System.Windows.FrameworkElement.Width%2A>がアニメーション化されます。 2 番目のボタンの色を変更するため、<xref:System.Windows.Media.SolidColorBrush.Color%2A>のプロパティ、<xref:System.Windows.Media.SolidColorBrush>設定に使用される、<xref:System.Windows.Controls.Control.Background%2A>のアニメーション化するボタン。  
  
## <a name="example"></a>例  
 [!code-xaml[AnimatePropertyStoryboards#1](~/samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/StoryboardExample.xaml#1)]  
  
> [!NOTE]
>  アニメーション両方を対象にできますが、<xref:System.Windows.FrameworkElement>オブジェクトなど、<xref:System.Windows.Controls.Control>または<xref:System.Windows.Controls.Panel>と<xref:System.Windows.Freezable>などのオブジェクト、<xref:System.Windows.Media.Brush>または<xref:System.Windows.Media.Transform>、フレームワーク要素だけが、<xref:System.Windows.FrameworkElement.Name%2A>プロパティ。 名前をフリーズ可能オブジェクトに割り当てて、アニメーションの対象にできるようにするには、前の例で示したように [x:Name ディレクティブ](../../xaml-services/x-name-directive.md)を使用します。  
  
 作成する必要があるコードを使用する場合、<xref:System.Windows.NameScope>の<xref:System.Windows.FrameworkElement>をアニメーション化するオブジェクトの名前の登録と<xref:System.Windows.FrameworkElement>します。 コードでアニメーションを開始するには使用、<xref:System.Windows.Media.Animation.BeginStoryboard>とアクション、<xref:System.Windows.EventTrigger>します。 必要に応じて、イベント ハンドラーを使用することができます、<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>メソッドの<xref:System.Windows.Media.Animation.Storyboard>します。 <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> メソッドを使用する方法の例を次に示します。  
  
 [!code-csharp[AnimatePropertyStoryboards#11](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimatePropertyStoryboards/CSharp/StoryboardExample.cs#11)]
 [!code-vb[AnimatePropertyStoryboards#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AnimatePropertyStoryboards/VisualBasic/StoryboardExample.vb#11)]  
  
 アニメーションとストーリー ボードの詳細については、「[アニメーションの概要](animation-overview.md)」を参照してください。  
  
 コードを使用していない場合だけを使用する<xref:System.Windows.Media.Animation.Storyboard>プロパティをアニメーション化するオブジェクト。 使用例を含む詳細については、「[ストーリーボードを使用せずにプロパティをアニメーション化する](how-to-animate-a-property-without-using-a-storyboard.md)」と「[AnimationClock を使用してプロパティをアニメーション化する](how-to-animate-a-property-by-using-an-animationclock.md)」を参照してください。
