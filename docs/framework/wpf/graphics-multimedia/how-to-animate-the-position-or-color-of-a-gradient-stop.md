---
title: '方法: グラデーション ストップの位置または色をアニメーション化する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- position [WPF], animating
- animation [WPF], position of GradientStop objects
- GradientStop objects [WPF], animating color of
- colors [WPF], animating
- animation [WPF], color of GradientStop objects
- GradientStop objects [WPF], animating position of
ms.assetid: 6f5b8b47-6c32-4b8e-98ee-fdf6515ec843
ms.openlocfilehash: 4762233cace895c9d492fb426f3f6be14498ad53
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593365"
---
# <a name="how-to-animate-the-position-or-color-of-a-gradient-stop"></a>方法: グラデーション ストップの位置または色をアニメーション化する
この例は、アニメーション化する方法を示しています、<xref:System.Windows.Media.GradientStop.Color%2A>と<xref:System.Windows.Media.GradientStop.Offset%2A>の<xref:System.Windows.Media.GradientStop>オブジェクト。  
  
## <a name="example"></a>例  
 次の例では、アニメーション内の 3 つのグラデーションの分岐点を<xref:System.Windows.Media.LinearGradientBrush>します。 例では、さまざまなグラデーションの分岐点をアニメーション化の 3 つのアニメーションを使用します。  
  
- 最初のアニメーションを<xref:System.Windows.Media.Animation.DoubleAnimation>、アニメーションの最初のグラデーションの<xref:System.Windows.Media.GradientStop.Offset%2A>0.0 ~ 1.0 0.0 に戻ります。 その結果、最初の色の四角形の右側にあるを左側にあるグラデーション シフトで、左側に戻ります。  
  
- 2 番目のアニメーションを<xref:System.Windows.Media.Animation.ColorAnimation>、2 番目のグラデーションのアニメーション化<xref:System.Windows.Media.GradientStop.Color%2A>から<xref:System.Windows.Media.Colors.Purple%2A>に<xref:System.Windows.Media.Colors.Yellow%2A>に再び<xref:System.Windows.Media.Colors.Purple%2A>します。 その結果、黄色および紫へ、グラデーションの中間色を表すは紫から変更します。  
  
- 3 番目のアニメーションでは、もう 1 つ<xref:System.Windows.Media.Animation.ColorAnimation>、3 番目のグラデーション ストップの不透明度をアニメーション化<xref:System.Windows.Media.GradientStop.Color%2A>-1 で戻ります。 その結果、3 番目の色、グラデーションはフェードアウトし、し、再び不透明になります。  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/GradientStopAnimationExample.cs#graphicsmmgradientanimationexampleswholepage)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/gradientstopanimationexample.vb#graphicsmmgradientanimationexampleswholepage)]
 [!code-xaml[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/GradientStopAnimationExample.xaml#graphicsmmgradientanimationexampleswholepage)]  
  
 この例では、 <xref:System.Windows.Media.LinearGradientBrush>、プロセスは、アニメーション化するため同じ<xref:System.Windows.Media.GradientStop>内でオブジェクトを<xref:System.Windows.Media.RadialGradientBrush>します。  
  
 その他の例では、次を参照してください。、[ブラシのサンプル](https://go.microsoft.com/fwlink/?LinkID=159973)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.GradientStop>
- [アニメーションの概要](animation-overview.md)
- [ストーリーボードの概要](storyboards-overview.md)
