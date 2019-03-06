---
title: '方法: サムネイルとしてイメージを読み込む'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- loading images as thumbnails [WPF]
- images [WPF], loading as thumbnails
- thumbnails [WPF], loading images as
ms.assetid: 02e055a0-54df-499a-b8b6-ab6ff7535cff
ms.openlocfilehash: 0b5435e9b06f37dae7dc762e9035b1eca8156ca6
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57353389"
---
# <a name="how-to-load-an-image-as-a-thumbnail"></a>方法: サムネイルとしてイメージを読み込む
次の例を読み込む方法を示して、<xref:System.Windows.Controls.Image>アプリケーション メモリを節約するサムネイルとして。  
  
## <a name="example"></a>例  
 次の例のセット、<xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A>のプロパティを<xref:System.Windows.Media.Imaging.BitmapImage>で[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]イメージの読み込みに必要なメモリを削減します。  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## <a name="example"></a>例  
 次の例のセット、<xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A>のプロパティを<xref:System.Windows.Media.Imaging.BitmapImage>コードに、イメージの読み込みに必要なメモリ量を減らします。  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## <a name="see-also"></a>関連項目
- [イメージングの概要](imaging-overview.md)
