---
title: '方法 : アニメーションをテキストに適用する'
ms.date: 03/30/2017
helpviewer_keywords:
- typography [WPF], animations
- animation [WPF], text
ms.assetid: eec3d26c-0a21-420f-8012-671621c47089
ms.openlocfilehash: ed2f3beb904f724ac93e2c4033aa6b2eb3fa1290
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174629"
---
# <a name="how-to-apply-animations-to-text"></a>方法 : アニメーションをテキストに適用する
アニメーションを利用すると、アプリケーションのテキストの表示方法や見た目を変えることができます。 次の例では、さまざまな種類のアニメーションを使用して、コントロール内のテキスト<xref:System.Windows.Controls.TextBlock>の表示に影響を与えます。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.Animation.DoubleAnimation>を使用してテキスト ブロックの幅をアニメーション化します。 幅の値が 10 秒間、テキスト ブロックの幅から 0 に変化します。その後、幅の値を戻します。 この種類のアニメーションでワイプ効果を作ります。  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample1)]  
  
 次の例では、<xref:System.Windows.Media.Animation.DoubleAnimation>を使用してテキスト ブロックの不透明度をアニメーション化します。 不透明度の値が 5 秒間、1.0 から 0 に変化し、その後、不透明度の値を戻します。  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample2)]  
  
 次の図は、<xref:System.Windows.Controls.TextBlock>コントロールがで定義された 5 秒間隔`1.00`で`0.00`不透明度を変更した場合の影響を<xref:System.Windows.Media.Animation.Timeline.Duration%2A>示しています。  
  
 ![不透明度を 1.00 から 0.00 に変更するテキスト。](./media/how-to-apply-animations-to-text/faded-text-opacity-change.png)  

 次の例では、<xref:System.Windows.Media.Animation.ColorAnimation>を使用して、テキスト ブロックの前景色をアニメーション化します。 前景色の値が 5 秒間、ある色から別の色に変化し、その後、色の値を戻します。  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample3)]  
  
 次の例では、<xref:System.Windows.Media.Animation.DoubleAnimation>を使用してテキスト ブロックを回転します。 テキスト ブロックは 20 秒間、完全な回転を行い、その後、回転を引き続き繰り返します。  
  
 [!code-xaml[TextAnimationSample#TextAnimationSample4](~/samples/snippets/csharp/VS_Snippets_Wpf/TextAnimationSample/CS/Window1.xaml#textanimationsample4)]  
  
## <a name="see-also"></a>関連項目

- [アニメーションの概要](../graphics-multimedia/animation-overview.md)
