---
title: '方法: ImageDrawing を使用してイメージを描画する'
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], images
- graphics [WPF], drawing images
- images [WPF], drawing
ms.assetid: df28ab41-25fb-4ab3-b51d-7f695b24f55e
ms.openlocfilehash: 9a9a7ee32104e44997e6eaada09edaac2b1d610e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57355601"
---
# <a name="how-to-draw-an-image-using-imagedrawing"></a>方法: ImageDrawing を使用してイメージを描画する
この例は、使用する方法を示します、<xref:System.Windows.Media.ImageDrawing>イメージを描画します。 <xref:System.Windows.Media.ImageDrawing>を表示できるように、<xref:System.Windows.Media.ImageSource>で、 <xref:System.Windows.Media.DrawingBrush>、 <xref:System.Windows.Media.DrawingImage>、または<xref:System.Windows.Media.Visual>します。 作成したイメージを描画するために、<xref:System.Windows.Media.ImageDrawing>設定とその<xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType>と<xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType>プロパティ。 <xref:System.Windows.Media.ImageDrawing.ImageSource%2A?displayProperty=nameWithType>プロパティを描画するイメージを指定して、<xref:System.Windows.Media.ImageDrawing.Rect%2A?displayProperty=nameWithType>プロパティは、各イメージのサイズと位置を指定します。  
  
## <a name="example"></a>例  
 次の例では、4 つを使用して複合描画<xref:System.Windows.Media.ImageDrawing>オブジェクト。 この例では、次の図が生成されます。  
  
 ![複数の DrawingImage オブジェクト](./media/graphicsmm-imagedrawingexample.jpg "graphicsmm_ImageDrawingExample")  
4 つの ImageDrawing オブジェクト  
  
 [!code-csharp[DrawingMiscSnippets_snip#ImageDrawingExample](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/ImageDrawingExample.cs#imagedrawingexample)]
 [!code-xaml[DrawingMiscSnippets_snip#ImageDrawingExample](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/ImageDrawingExample.xaml#imagedrawingexample)]  
  
 使用せずにイメージを表示する簡単な方法を示す例については<xref:System.Windows.Media.ImageDrawing>を参照してください[イメージ要素を使用して](../controls/how-to-use-the-image-element.md)します。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Freezable.Freeze%2A>
- <xref:System.Windows.Controls.Image>
- [Drawing オブジェクトの概要](drawing-objects-overview.md)
- [Freezable オブジェクトの概要](../advanced/freezable-objects-overview.md)
- [PresentationOptions:Freeze 属性](../advanced/presentationoptions-freeze-attribute.md)
