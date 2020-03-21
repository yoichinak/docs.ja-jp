---
title: '方法 : 純色で領域を塗りつぶす'
ms.date: 03/30/2017
helpviewer_keywords:
- solid colors [WPF], painting with
- brushes [WPF], painting with solid colors
- painting [WPF], with solid colors
ms.assetid: 5d27d8a7-4bd7-4063-bdf3-2c5c0f19f9d3
ms.openlocfilehash: be28a0af04c4e43cdf745a5429468aee99e34c40
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2020
ms.locfileid: "78849523"
---
# <a name="how-to-paint-an-area-with-a-solid-color"></a>方法 : 純色で領域を塗りつぶす
単色<xref:System.Windows.Media.Brushes.Red%2A>で領域をペイントするには、定義済みのシステム ブラシ (or<xref:System.Windows.Media.Brushes.Blue%2A>など) を使用するか、新しい<xref:System.Windows.Media.SolidColorBrush>ブラシを作成してアルファ<xref:System.Windows.Media.SolidColorBrush.Color%2A>、赤、緑、青の値を使用して説明します。 XAML では、16 進数表記を使用して、純色で領域を塗りつぶすこともできます。  
  
 次の例では、これらの各手法を使用して青色<xref:System.Windows.Shapes.Rectangle>を塗りつぶします。  
  
## <a name="example"></a>例  
 **定義済みのブラシの使用**  
  
 次の例では、定義済みのブラシ<xref:System.Windows.Media.Brushes.Blue%2A>を使用して、四角形を青色で塗りつぶします。  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_PredefinedBrush1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_predefinedbrush1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_PredefinedBrush1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_predefinedbrush1)]  
  
 **16 進数表記の使用**  
  
 次の例では、8 桁の 16 進数表記を使用して、四角形を青で塗りつぶします。  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_HexNotation8Digit1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_hexnotation8digit1)]  
  
 **ARGB 値の使用**  
  
 次の例では、a を<xref:System.Windows.Media.SolidColorBrush>作成<xref:System.Windows.Media.SolidColorBrush.Color%2A>し、青の ARGB 値を使用して、その a を説明します。  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_RgbNotation1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_rgbnotation1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_RgbNotation1](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_rgbnotation1)]  
  
 色を記述する他の方法については、構造<xref:System.Windows.Media.Color>を参照してください。  
  
 **関連トピック**  
  
 詳細<xref:System.Windows.Media.SolidColorBrush>と追加の例については、「[単色とグラデーションによるペイントの概要」を](painting-with-solid-colors-and-gradients-overview.md)参照してください。  
  
 このコード例は、クラスに用意されている大きな例<xref:System.Windows.Media.SolidColorBrush>の一部です。 完全なサンプルについては、[ブラシのサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.Brushes>
