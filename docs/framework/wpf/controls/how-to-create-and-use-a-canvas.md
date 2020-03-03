---
title: '方法: Canvas を作成および使用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Canvas
- Canvas control [WPF], creating
- Canvas control [WPF], using
ms.assetid: 420b9487-9a15-477c-9489-a22a4dec7779
ms.openlocfilehash: edef660b2da2f09e0a6edbc0a87f0d1f26eb03da
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964229"
---
# <a name="how-to-create-and-use-a-canvas"></a>方法: Canvas を作成および使用する
この例では、の<xref:System.Windows.Controls.Canvas>インスタンスを作成して使用する方法を示します。  
  
## <a name="example"></a>例  
 次の例では、 <xref:System.Windows.Controls.TextBlock>のメソッド<xref:System.Windows.Controls.Canvas.SetTop%2A>と<xref:System.Windows.Controls.Canvas.SetLeft%2A>メソッドを使用し<xref:System.Windows.Controls.Canvas>て、2つの要素を明示的に配置しています。 また、この例で<xref:System.Windows.Controls.Control.Background%2A>は、 `LightSteelBlue` <xref:System.Windows.Controls.Canvas>の色をに割り当てています。  
  
> [!NOTE]
> を使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]し<xref:System.Windows.Controls.Canvas.Top%2A>て要素<xref:System.Windows.Controls.TextBlock>を配置する場合は<xref:System.Windows.Controls.Canvas.Left%2A> 、プロパティとプロパティを使用します。  
  
 [!code-csharp[CanvasCode#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CanvasCode/CSharp/Canvas_Code.cs#1)]
 [!code-vb[CanvasCode#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasCode/VisualBasic/canvas_vb.vb#1)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.Canvas>
- <xref:System.Windows.Controls.TextBlock>
- <xref:System.Windows.Controls.Canvas.SetTop%2A>
- <xref:System.Windows.Controls.Canvas.SetLeft%2A>
- <xref:System.Windows.Controls.Canvas.Top%2A>
- <xref:System.Windows.Controls.Canvas.Left%2A>
- [パネルの概要](panels-overview.md)
- [方法トピック](canvas-how-to-topics.md)
