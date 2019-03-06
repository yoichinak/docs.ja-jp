---
title: '方法: 要素またはブラシの不透明度をアニメーション化する'
ms.date: 03/30/2017
helpviewer_keywords:
- opacity [WPF], animating
- animation [WPF], Opacity property
ms.assetid: 572af23b-39dd-48d1-9db5-4bca56a4b3d3
ms.openlocfilehash: f07138a0b68fff050133d477074571c60cd8651e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57363372"
---
# <a name="how-to-animate-the-opacity-of-an-element-or-brush"></a>方法: 要素またはブラシの不透明度をアニメーション化する
フレームワーク要素がフェードインおよびフェードアウトするために、アニメーション化できますその<xref:System.Windows.UIElement.Opacity%2A>またはプロパティをアニメーション化することができます、<xref:System.Windows.Media.Brush.Opacity%2A>のプロパティ、 <xref:System.Windows.Media.Brush> (またはブラシ) 描画するために使用します。 により、要素の不透明度をアニメーション化して、その子フェードインおよびフェードアウトがのどの部分の要素のフェードインはより慎重に選択する要素の描画に使用されるブラシをアニメーション化することができます。 たとえば、ボタンの背景を描画に使用されるブラシの不透明度をアニメーション化できます。 これにより、ビュー、そのテキストを完全に不透明なままのフェードインとフェードアウトをボタンの背景が原因です。  
  
> [!NOTE]
>  アニメーション化、<xref:System.Windows.Media.Brush.Opacity%2A>の<xref:System.Windows.Media.Brush>パフォーマンスのメリットが得をアニメーション化、<xref:System.Windows.UIElement.Opacity%2A>要素のプロパティ。  
  
 次の例では、2 つのボタンをアニメーション化してフェードインおよびフェードアウトします。 最初の不透明度<xref:System.Windows.Controls.Button>がからアニメーション化`1.0`に`0.0`経由で、 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 5 秒間です。 2 番目のボタンがアニメーション化もが、描画に使用される、SolidColorBrush の不透明度その<xref:System.Windows.Controls.Control.Background%2A>ボタン全体の不透明度ではなくがアニメーション化されます。 例が実行される最初のボタン完全にフェードインおよびフェードアウト ビュー、中に、2 番目のボタンの背景のみがフェードインおよびフェードアウトします。 テキストと境界線は、完全に不透明なままです。  
  
## <a name="example"></a>例  
 [!code-xaml[timingbehaviors_snip#10](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/OpacityAnimationExample.xaml#10)]  
  
 コードは、この例から省略されています。 完全なサンプルでは、不透明度をアニメーション化する方法も示しています、<xref:System.Windows.Media.Color>内、<xref:System.Windows.Media.LinearGradientBrush>します。  完全なサンプルは、次を参照してください。、[要素のサンプルの不透明度をアニメーション化](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/OpacityAnimation)します。
