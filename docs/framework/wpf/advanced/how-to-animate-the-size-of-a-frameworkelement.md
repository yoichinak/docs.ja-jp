---
title: '方法: FrameworkElement のサイズをアニメーション化する'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], FrameworkElement size
- FrameworkElement [WPF], animating size of
ms.assetid: d4cd5a13-c20d-4a6f-a2ba-14f2c9ce4cef
ms.openlocfilehash: d1995deec5ab2c9bf405911af43b4d242d599119
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776910"
---
# <a name="how-to-animate-the-size-of-a-frameworkelement"></a>方法: FrameworkElement のサイズをアニメーション化する
サイズをアニメーション化する、 <xref:System.Windows.FrameworkElement>、アニメーション化することができますか、その<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>プロパティまたは使用してアニメーション化された<xref:System.Windows.Media.ScaleTransform>します。  
  
 次の例では、これら 2 つのアプローチを使用して 2 つのボタンのサイズをアニメーション化します。 アニメーション化して 1 つのボタンのサイズが変更されたその<xref:System.Windows.FrameworkElement.Width%2A>プロパティと別のアニメーション化してサイズを変更、<xref:System.Windows.Media.ScaleTransform>に適用されるその<xref:System.Windows.UIElement.RenderTransform%2A>プロパティ。 各ボタンには、いくつかのテキストが含まれています。 最初に、両方のボタンで同じテキストが表示されますが、2 番目のボタンのテキストにゆがみが生じるように、ボタン サイズを変更する。  
  
## <a name="example"></a>例  
 [!code-xaml[transformanimations_snip#1](~/samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/AnimatingSizeExample.xaml#1)]  
  
 要素を変換する場合は、要素全体とその内容が変換されます。 場合の最初のボタンのように、要素のサイズを直接変更するとき、そのサイズと位置がそれぞれの親要素のサイズに依存しない限り、要素の内容はサイズ変更されません。  
  
 要素のサイズをアニメーション化するアニメーションの変換を適用することでその<xref:System.Windows.UIElement.RenderTransform%2A>プロパティがアニメーション化されるより優れたパフォーマンスを提供しますその<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>を直接ため、<xref:System.Windows.UIElement.RenderTransform%2A>プロパティでレイアウト パスがトリガーされません。  
  
 プロパティをアニメーション化の詳細については、次を参照してください。、[アニメーションの概要](../graphics-multimedia/animation-overview.md)します。 変換の詳細については、次を参照してください。、[変換の概要](../graphics-multimedia/transforms-overview.md)します。
