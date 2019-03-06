---
title: '方法: ストーリーボードを使用してアニメーション化した後にプロパティを設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], changing property values after
ms.assetid: 79466556-4dbf-40bd-9c1e-a77613b07077
ms.openlocfilehash: 1f66c79f18fd02327c0c1f4f20787e566437f20f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57359431"
---
# <a name="how-to-set-a-property-after-animating-it-with-a-storyboard"></a>方法: ストーリーボードを使用してアニメーション化した後にプロパティを設定する
場合によっては、表示にアニメーション化した後、プロパティの値を変更できないことがあります。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.Animation.Storyboard>の色をアニメーション化するために使用、<xref:System.Windows.Media.SolidColorBrush>します。 ストーリー ボードは、ボタンがクリックされたときにトリガーされます。 <xref:System.Windows.Media.Animation.Timeline.Completed>プログラムが通知されるように、イベントが処理されるときに、<xref:System.Windows.Media.Animation.ColorAnimation>が完了するとします。  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton1Declaration](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton1declaration)]  
  
## <a name="example"></a>例  
 後に、<xref:System.Windows.Media.Animation.ColorAnimation>が完了したら、プログラム、ブラシの色を青に変更しよう。  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton1Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton1handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton1Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton1handler)]  
  
 何もする前のコードが表示されない: によって提供される、ブラシは黄色、これは、値、<xref:System.Windows.Media.Animation.ColorAnimation>ブラシをアニメーション化します。 基になるプロパティの値 (基本値) は実際に青に変更します。 ただし、有効な場合、または、現在の値は黄色ため、<xref:System.Windows.Media.Animation.ColorAnimation>は基本の値をまだオーバーライドします。 基本の値をもう一度有効な値をする場合は、プロパティへの影響からアニメーションを停止する必要があります。 ストーリー ボード アニメーションでそれを行う 3 つの方法はあります。  
  
-   アニメーションの<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>プロパティを <xref:System.Windows.Media.Animation.FillBehavior.Stop>  
  
-   ストーリー ボード全体を削除します。  
  
-   個々 のプロパティからアニメーションを削除します。  
  
## <a name="set-the-animations-fillbehavior-property-to-stop"></a>Stop に設定されて、アニメーションの FillBehavior プロパティ  
 設定して<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>に<xref:System.Windows.Media.Animation.FillBehavior.Stop>、アクティブな期間の末尾に達した後、ターゲット プロパティに影響することを停止するアニメーションに指示します。  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton2Declaration](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton2declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton2Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton2handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton2Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton2handler)]  
  
## <a name="remove-the-entire-storyboard"></a>ストーリー ボード全体を削除します。  
 使用して、<xref:System.Windows.Media.Animation.RemoveStoryboard>トリガーまたは<xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType>メソッド、そのターゲット プロパティの影響を与えることを停止するストーリー ボード アニメーションがわかります。 この方法と設定の違い、<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>プロパティは、ストーリー ボードを削除することができますにいつでも、while、<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>プロパティは、アニメーションがアクティブな期間の末尾に達したときにのみ効果が。  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton3Declaration](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton3declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton3Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton3handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton3Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton3handler)]  
  
## <a name="remove-an-animation-from-an-individual-property"></a>個々 のプロパティからアニメーションを削除します。  
 プロパティに影響を与えるからアニメーションを停止する別の手法は、使用する、<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29>アニメーション化されているオブジェクトのメソッド。 最初のパラメーターとしてアニメーション化されているプロパティを指定し、 `null` 2 つ目として。  
  
 [!code-xaml[timingbehaviors_snip#GraphicsMMButton4Declaration](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml#graphicsmmbutton4declaration)]  
  
 [!code-csharp[timingbehaviors_snip#GraphicsMMButton4Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AnimateThenSetPropertyExample.xaml.cs#graphicsmmbutton4handler)]
 [!code-vb[timingbehaviors_snip#GraphicsMMButton4Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/animatethensetpropertyexample.xaml.vb#graphicsmmbutton4handler)]  
  
 この手法は、非ストーリー ボード アニメーションに対しても機能します。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>
- <xref:System.Windows.Media.Animation.Storyboard.Remove%2A?displayProperty=nameWithType>
- <xref:System.Windows.Media.Animation.RemoveStoryboard>
- [アニメーションの概要](animation-overview.md)
- [プロパティ アニメーションの手法の概要](property-animation-techniques-overview.md)
