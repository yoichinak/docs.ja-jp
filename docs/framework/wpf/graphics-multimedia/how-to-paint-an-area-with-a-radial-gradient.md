---
title: '方法: 放射状グラデーションを使用して領域を塗りつぶす'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- brushes [WPF], painting with radial gradients
- radial gradients [WPF], painting with
- painting [WPF], with radial gradients
ms.assetid: b5d0fc8a-8986-4796-b003-a75b41a48928
ms.openlocfilehash: 5762ef1a1526ba6f004917c8a947e35ce731c86d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916099"
---
# <a name="how-to-paint-an-area-with-a-radial-gradient"></a>方法: 放射状グラデーションを使用して領域を塗りつぶす
この例では、 <xref:System.Windows.Media.RadialGradientBrush>クラスを使用して、放射状グラデーションで領域を塗りつぶす方法を示します。  
  
## <a name="example"></a>例  
 次の例では<xref:System.Windows.Media.RadialGradientBrush> 、を使用して、黄色から赤、青、黄緑に切り替わる放射状グラデーションで四角形を塗りつぶします。  
  
 [!code-csharp[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/RadialGradientBrushSnippet.cs#simpleradialgradientexamplewholepage)]
 [!code-vb[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/radialgradientbrushsnippet.vb#simpleradialgradientexamplewholepage)]
 [!code-xaml[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/RadialGradientBrushSnippet.xaml#simpleradialgradientexamplewholepage)]  
  
 次の図は、前の例のグラデーションを示しています。 グラデーションの分岐点が強調表示されています。  
  
 ![放射状グラデーションでのグラデーション境界](./media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")  
  
> [!NOTE]
> このトピックの例では、コントロールポイントを設定するための既定の座標系を使用します。 既定の座標系は、境界ボックスに対して相対的です。0 は境界ボックスの 0% を示し、1 は境界ボックスの 100% を示します。 この座標系を変更するには、 <xref:System.Windows.Media.GradientBrush.MappingMode%2A>プロパティを値<xref:System.Windows.Media.BrushMappingMode.Absolute>に設定します。 絶対座標系は、境界ボックスに相対しません。 値は、ローカル空間に直接変換されます。  
  
 <xref:System.Windows.Media.RadialGradientBrush> のさらに別の例については、「[ブラシのサンプル](https://go.microsoft.com/fwlink/?LinkID=159973)」を参照してください。 グラデーションおよびその他の種類のブラシの詳細については、「[純色およびグラデーションによる塗りつぶしの概要](painting-with-solid-colors-and-gradients-overview.md)」を参照してください。
