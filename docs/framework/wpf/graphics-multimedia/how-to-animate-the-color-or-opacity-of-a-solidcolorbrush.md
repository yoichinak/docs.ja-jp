---
title: '方法: SolidColorBrush の色または不透明度をアニメーション化する'
ms.date: 03/30/2017
helpviewer_keywords:
- SolidColorBrush [WPF], animating color of
- colors [WPF], animating
- opacity [WPF], animating
- animation [WPF], color of SolidColorBrush
- animation [WPF], opacity of SolidColorBrush
- SolidColorBrush [WPF], animating opacity of
ms.assetid: d9154354-843f-4713-bad1-35bb0ba6eaeb
ms.openlocfilehash: 541835a7827467aeceb1ed72e54b69e62dc4f916
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354441"
---
# <a name="how-to-animate-the-color-or-opacity-of-a-solidcolorbrush"></a>方法: SolidColorBrush の色または不透明度をアニメーション化する
この例は、アニメーション化する方法を示しています、<xref:System.Windows.Media.SolidColorBrush.Color%2A>と<xref:System.Windows.Media.Brush.Opacity%2A>の<xref:System.Windows.Media.SolidColorBrush>します。  
  
## <a name="example"></a>例  
 次の例では、アニメーション化する 3 つのアニメーションを使用して、<xref:System.Windows.Media.SolidColorBrush.Color%2A>と<xref:System.Windows.Media.Brush.Opacity%2A>の<xref:System.Windows.Media.SolidColorBrush>します。  
  
-   最初のアニメーションを<xref:System.Windows.Media.Animation.ColorAnimation>、ブラシの色を変更<xref:System.Windows.Media.Colors.Gray%2A>マウスが四角形に入ったとき。  
  
-   [次へ] のアニメーションでは、もう 1 つ<xref:System.Windows.Media.Animation.ColorAnimation>、ブラシの色を変更<xref:System.Windows.Media.Colors.Orange%2A>マウスから離したときに四角形。  
  
-   最後のアニメーションを<xref:System.Windows.Media.Animation.DoubleAnimation>マウスの左ボタンが押されたときに、ブラシの不透明度を 0.0 に変更します。  
  
 [!code-csharp[brushanimations_snip#SolidColorBrushAnimationExample](~/samples/snippets/csharp/VS_Snippets_Wpf/brushanimations_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushanimationexample)]  
  
 さまざまな種類のブラシをアニメーション化する方法を示していますより完全なサンプルを参照してください、[ブラシのサンプル](https://go.microsoft.com/fwlink/?LinkID=159973)します。 アニメーションの詳細については、、[アニメーションの概要](animation-overview.md)を参照してください。  
  
 この例のコードを使用して、他のアニメーション例と一貫性を保つのため、<xref:System.Windows.Media.Animation.Storyboard>アニメーションを適用するオブジェクト。 ただし、コード内で 1 つのアニメーションを適用する場合は使いやすく、<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>メソッドを使用してではなく、<xref:System.Windows.Media.Animation.Storyboard>します。 例については、「[ストーリーボードを使用せずにプロパティをアニメーション化する](how-to-animate-a-property-without-using-a-storyboard.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目
- [アニメーションの概要](animation-overview.md)
- [ストーリーボードの概要](storyboards-overview.md)
- [ブラシのサンプル](https://go.microsoft.com/fwlink/?LinkID=159973)
