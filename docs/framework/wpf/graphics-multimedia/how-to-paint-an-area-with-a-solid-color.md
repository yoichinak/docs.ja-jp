---
title: '方法: 純色で領域を塗りつぶす'
ms.date: 03/30/2017
helpviewer_keywords:
- solid colors [WPF], painting with
- brushes [WPF], painting with solid colors
- painting [WPF], with solid colors
ms.assetid: 5d27d8a7-4bd7-4063-bdf3-2c5c0f19f9d3
ms.openlocfilehash: c85ba72c858d155f29875bb944824db1c44ffaab
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59086846"
---
# <a name="how-to-paint-an-area-with-a-solid-color"></a>方法: 純色で領域を塗りつぶす
純色で領域を塗りつぶすに、使用できる、定義済みのシステム ブラシなど<xref:System.Windows.Media.Brushes.Red%2A>または<xref:System.Windows.Media.Brushes.Blue%2A>、新規に作成することができますか<xref:System.Windows.Media.SolidColorBrush>について説明してその<xref:System.Windows.Media.SolidColorBrush.Color%2A>アルファ、赤、緑、および青の値を使用して。 XAML では、16 進数表記を使用して、純色で領域を塗りつぶすこともできます。  
  
 次の例では、これらの手法を使用を描画する、<xref:System.Windows.Shapes.Rectangle>青。  
  
## <a name="example"></a>例  
 **定義済みのブラシを使用します。**  
  
 次の例では、定義済みのブラシを使用して<xref:System.Windows.Media.Brushes.Blue%2A>青い四角形を描画します。  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_PredefinedBrush1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_predefinedbrush1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_PredefinedBrush1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_predefinedbrush1)]  
  
 **16 進数表記を使用します。**  
  
 次の例では、8 桁の 16 進数表記を使用して、四角形を青で塗りつぶします。  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_HexNotation8Digit1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_hexnotation8digit1)]  
  
 **ARGB 値を使用してください。**  
  
 次の例では、作成、<xref:System.Windows.Media.SolidColorBrush>について説明しますと、 <xref:System.Windows.Media.SolidColorBrush.Color%2A> ARGB を使用して、色の青の値します。  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_RgbNotation1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_rgbnotation1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_RgbNotation1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_rgbnotation1)]  
  
 他の色を記述する方法についてを参照してください。、<xref:System.Windows.Media.Color>構造体。  
  
 **関連トピック**  
  
 詳細については<xref:System.Windows.Media.SolidColorBrush>し、その他の例を参照してください、[純色およびグラデーション概要](painting-with-solid-colors-and-gradients-overview.md)の概要。  
  
 このコード例が示されている例の一部、<xref:System.Windows.Media.SolidColorBrush>クラス。 完全なサンプルについては、「[ブラシのサンプル](https://go.microsoft.com/fwlink/?LinkID=159973)」をご覧ください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Brushes>
