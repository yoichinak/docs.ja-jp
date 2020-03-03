---
title: '方法: ビジュアルをイメージ ファイルにエンコードする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image files [WPF], encoding from visuals
- encoding image formats [WPF]
- visuals [WPF], encoding to an image file
ms.assetid: 2036385b-ea47-4d54-8027-5797f52c8149
ms.openlocfilehash: 193b6a14e404d32bb49d6e0ef3cbd513166bcce2
ms.sourcegitcommit: 43761fcee10aeefcf851ea81cea3f3c691420856
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/16/2019
ms.locfileid: "69545295"
---
# <a name="how-to-encode-a-visual-to-an-image-file"></a>方法: ビジュアルをイメージ ファイルにエンコードする
この例では、 <xref:System.Windows.Media.Visual> <xref:System.Windows.Media.Imaging.RenderTargetBitmap>とを<xref:System.Windows.Media.Imaging.PngBitmapEncoder>使用して、オブジェクトをイメージファイルにエンコードする方法を示します。  
  
## <a name="example"></a>例  
 は、に<xref:System.Windows.Media.Imaging.BitmapImage> レンダリングされるを<xref:System.Windows.Media.FormattedText>使用して作成されます。<xref:System.Windows.Media.Imaging.RenderTargetBitmap> <xref:System.Windows.Media.DrawingVisual> レンダリングされたビットマップは、新しいポータブル<xref:System.Windows.Media.Imaging.BitmapFrame>ネットワークグラフィックス (PNG) <xref:System.Windows.Media.Imaging.PngBitmapEncoder>ファイルを作成するためにに追加されるを作成するために使用されます。  
  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample_Encode.cs#rtbencodeinline1)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample_Encode.vb#rtbencodeinline1)]  
  
 この<xref:System.Windows.Media.Imaging.PngBitmapEncoder>例では、が使用されてい<xref:System.Windows.Media.Imaging.BitmapEncoder>ましたが、派生したオブジェクトはいずれも、イメージファイルの作成に使用されている可能性があります。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Media.DrawingContext>
- [イメージングの概要](imaging-overview.md)
- [Drawing オブジェクトの概要](drawing-objects-overview.md)
- [DrawingVisual オブジェクトの使用](using-drawingvisual-objects.md)
