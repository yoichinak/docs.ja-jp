---
title: '方法: 線形グラデーションを使用して領域を塗りつぶす'
ms.date: 03/30/2017
helpviewer_keywords:
- linear gradients [WPF], painting with
- brushes [WPF], painting with linear gradients
- painting [WPF], with linear gradients
ms.assetid: 00e0cd04-48c0-4ec5-850e-d321beb37a34
ms.openlocfilehash: c48ff13811d784ecc7042b73b964a9e6f2d42a34
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921920"
---
# <a name="how-to-paint-an-area-with-a-linear-gradient"></a>方法: 線形グラデーションを使用して領域を塗りつぶす
この例は、使用する方法を示します、<xref:System.Windows.Media.LinearGradientBrush>線形グラデーションを使用して領域を描画するクラス。 次の例では、<xref:System.Windows.Shapes.Shape.Fill%2A>の<xref:System.Windows.Shapes.Rectangle>が黄色から緑に青に赤に遷移対角線方向の線形グラデーションで塗りつぶされます。  
  
## <a name="example"></a>例  
 [!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 次の図は、前の例で作成したグラデーションを示しています。  
  
 ![対角線方向の線形グラデーション](./media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")  
  
 水平方向の線形グラデーションを作成するには、変更、<xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A>と<xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>の<xref:System.Windows.Media.LinearGradientBrush>(0,0.5) に (1,0.5) とします。 次の例では、<xref:System.Windows.Shapes.Rectangle>が水平方向の線形グラデーションで塗りつぶされます。  
  
 [!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 次の図は、前の例で作成したグラデーションを示しています。  
  
 ![水平方向の線形グラデーション](./media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")  
  
 垂直方向の線形グラデーションを作成するには、変更、<xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A>と<xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>の<xref:System.Windows.Media.LinearGradientBrush>(0.5,0) に (0.5,1) とします。 次の例では、<xref:System.Windows.Shapes.Rectangle>が垂直方向の線形グラデーションで塗りつぶされます。  
  
 [!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](~/samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](~/samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 次の図は、前の例で作成したグラデーションを示しています。  
  
 ![垂直方向の線形グラデーション](./media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")  
  
> [!NOTE]
>  このトピックの例では、始点と終点を設定するための既定の座標系を使用します。 既定の座標系は、境界ボックスに対して相対的です。0、境界ボックスの 0% を示し、1 は境界ボックスの 100% を示します。 この座標系を設定して変更することができます、<xref:System.Windows.Media.GradientBrush.MappingMode%2A>プロパティ値を<xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType>します。 絶対座標系は、境界ボックスに相対しません。 値は、ローカル空間に直接変換されます。  
  
 その他の例では、次を参照してください。[ブラシのサンプル](https://go.microsoft.com/fwlink/?LinkID=159973)します。 グラデーションおよびその他の種類のブラシの詳細については、次を参照してください。[純色およびグラデーション概要](painting-with-solid-colors-and-gradients-overview.md)します。
