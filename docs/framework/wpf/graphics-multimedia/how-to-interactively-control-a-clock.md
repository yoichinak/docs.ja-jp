---
title: '方法: クロックを対話的に制御する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controlling clocks interactively [WPF]
- clocks [WPF], controlling interactively
ms.assetid: d0b520e0-2f18-4cef-977f-2909e709548a
ms.openlocfilehash: 05989b6a03e03fb5723a70c9c36d5e32f9117049
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59186590"
---
# <a name="how-to-interactively-control-a-clock"></a>方法: クロックを対話的に制御する
A<xref:System.Windows.Media.Animation.Clock>オブジェクトの<xref:System.Windows.Media.Animation.ClockController>プロパティでは、対話形式で開始、一時停止、再開、シーク、塗りつぶし期間、クロックを進みおよびクロックを停止することができます。 タイミング ツリーのルート クロックのみを対話的に制御できます。  
  
> [!NOTE]
>  クロックを直接操作する必要がないアニメーションを対話的に制御するには、その他の方法はあります。 ストーリー ボードを使用することもできます。 ストーリー ボードは、マークアップとコードの両方でサポートされます。 例については、次を参照してください。[ストーリー ボードを使用してプロパティをアニメーション化する](how-to-animate-a-property-by-using-a-storyboard.md)または[アニメーションの概要](animation-overview.md)します。  
  
 次の例では、いくつかのボタンは、アニメーション クロックを対話的に制御に使用されます。  
  
## <a name="example"></a>例  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerExample.cs#graphicsmmclockcontrollerexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerexample.vb#graphicsmmclockcontrollerexample)]  
  
## <a name="see-also"></a>関連項目

- [ストーリーボードを使ってプロパティをアニメーション化する](how-to-animate-a-property-by-using-a-storyboard.md)
- [アニメーションの概要](animation-overview.md)
