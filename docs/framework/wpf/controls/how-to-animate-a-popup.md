---
title: '方法: ポップアップをアニメーション化する'
ms.date: 03/30/2017
helpviewer_keywords:
- Popup control [WPF], animating
- animation [WPF], Popup controls
ms.assetid: acaa2a0a-6137-4efd-9cd1-75ece222e390
ms.openlocfilehash: ed5edf298e59d6a9adddc03fc21de1900c7ee8e9
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372842"
---
# <a name="how-to-animate-a-popup"></a>方法: ポップアップをアニメーション化する
この例は、アニメーション化する 2 つの方法を示しています、<xref:System.Windows.Controls.Primitives.Popup>コントロール。  
  
## <a name="example"></a>例  
 次の例のセット、<xref:System.Windows.Controls.Primitives.PopupAnimation>プロパティの値を<xref:System.Windows.Controls.Primitives.PopupAnimation.Slide>、原因となる、 <xref:System.Windows.Controls.Primitives.Popup> 「スライドで表示されるときにします。  
  
 回転するには、 <xref:System.Windows.Controls.Primitives.Popup>、この例に割り当てます、<xref:System.Windows.Media.RotateTransform>を<xref:System.Windows.UIElement.RenderTransform%2A>プロパティを<xref:System.Windows.Controls.Canvas>の子要素は、<xref:System.Windows.Controls.Primitives.Popup>します。  
  
 正常に動作する変換の例を設定する必要があります、<xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A>プロパティを`true`します。 さらに、<xref:System.Windows.FrameworkElement.Margin%2A>上、<xref:System.Windows.Controls.Canvas>コンテンツが十分な領域を指定する必要があります、<xref:System.Windows.Controls.Primitives.Popup>回転します。  
  
 [!code-xaml[AnimatedPopup#RotateTransform2](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform2)]  
  
 次の例は方法、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベントが発生時に、<xref:System.Windows.Controls.Button>がクリックされた、トリガー、<xref:System.Windows.Media.Animation.Storyboard>アニメーションを開始します。  
  
 [!code-xaml[AnimatedPopup#RotateTransform1](~/samples/snippets/csharp/VS_Snippets_Wpf/AnimatedPopup/CS/Window1.xaml#rotatetransform1)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.UIElement.RenderTransform%2A>
- <xref:System.Windows.Controls.Primitives.BulletDecorator>
- <xref:System.Windows.Media.RotateTransform>
- <xref:System.Windows.Media.Animation.Storyboard>
- <xref:System.Windows.Controls.Primitives.Popup>
- [方法トピック](popup-how-to-topics.md)
- [ポップアップの概要](popup-overview.md)
