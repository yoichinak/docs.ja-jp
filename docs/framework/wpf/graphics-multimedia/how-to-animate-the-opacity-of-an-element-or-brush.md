---
title: '方法: 要素またはブラシの不透明度をアニメーション化する'
ms.date: 03/30/2017
helpviewer_keywords:
- opacity [WPF], animating
- animation [WPF], Opacity property
ms.assetid: 572af23b-39dd-48d1-9db5-4bca56a4b3d3
ms.openlocfilehash: 2f18861eb18f81b631245d1d933b7acb1b3e0e42
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950515"
---
# <a name="how-to-animate-the-opacity-of-an-element-or-brush"></a>方法: 要素またはブラシの不透明度をアニメーション化する
フレームワーク要素のフェードインとビューアウトを行うには、その<xref:System.Windows.UIElement.Opacity%2A>プロパティをアニメーション化するか、描画に使用する<xref:System.Windows.Media.Brush> (またはブラシ) の<xref:System.Windows.Media.Brush.Opacity%2A>プロパティをアニメーション化します。 要素の不透明度をアニメーション化すると、それとその子はフェードインおよびビューアウトされますが、要素の描画に使用するブラシをアニメーション化することで、要素のどの部分をフェードさせるかをより細かく選択できます。 たとえば、ボタンの背景を描画するために使用されるブラシの不透明度をアニメーション化することができます。 これにより、ボタンの背景が表示されなくなり、テキストが完全に不透明になります。  
  
> [!NOTE]
> のをアニメーション化<xref:System.Windows.Media.Brush>すると、要素のプロパティ<xref:System.Windows.UIElement.Opacity%2A>をアニメーション化するよりもパフォーマンスが向上します。 <xref:System.Windows.Media.Brush.Opacity%2A>  
  
 次の例では、2つのボタンがアニメーション化されて表示されるようになっています。 最初<xref:System.Windows.Controls.Button>のの不透明度は、 <xref:System.Windows.Media.Animation.Timeline.Duration%2A>から`1.0` 5 `0.0`秒間にアニメーション化されます。 2番目のボタンもアニメーション化されますが、の描画<xref:System.Windows.Controls.Control.Background%2A>に使用される system.windows.media.solidcolorbrush> の不透明度は、ボタン全体の不透明度ではなく、アニメーション化されます。 この例を実行すると、最初のボタンは完全にフェードインされ、ビューから除外されます。一方、2番目のボタンの背景だけがフェードインして表示されなくなります。 そのテキストと境界線は、完全に不透明なままです。  
  
## <a name="example"></a>例  
 [!code-xaml[timingbehaviors_snip#10](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/OpacityAnimationExample.xaml#10)]  
  
 この例では、コードは省略されています。 完全なサンプルでは、 <xref:System.Windows.Media.Color> <xref:System.Windows.Media.LinearGradientBrush>内のの不透明度をアニメーション化する方法も示しています。  完全なサンプルについては、「[要素の不透明度のアニメーション](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/OpacityAnimation)化」のサンプルを参照してください。
