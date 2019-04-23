---
title: '方法: イメージ要素を使用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Image
- Image control [WPF]
- rendering images [WPF]
ms.assetid: 5b92e74b-1b56-4756-ac64-d5e9e08d9854
ms.openlocfilehash: 967159894e25721bdf380f851712e91d76088f87
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59205304"
---
# <a name="how-to-use-the-image-element"></a>方法: イメージ要素を使用する
この例を使用して、アプリケーションでイメージを含める方法を示しています、<xref:System.Windows.Controls.Image>要素。  
  
## <a name="example"></a>例  
 次の例では、幅 200 ピクセルのイメージをレンダリングする方法を示します。 この[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]例では、イメージの定義に属性の構文とプロパティ タグ構文の両方を使用します。 属性構文とプロパティ構文の詳細については、「[依存関係プロパティの概要](../advanced/dependency-properties-overview.md)」を参照してください。 A<xref:System.Windows.Media.Imaging.BitmapImage>イメージのソース データを定義するために使用して、プロパティ タグ構文例では、明示的に定義されています。 さらに、<xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A>の<xref:System.Windows.Media.Imaging.BitmapImage>と同じ幅に設定されている、<xref:System.Windows.FrameworkElement.Width%2A>の<xref:System.Windows.Controls.Image>します。 これは、イメージのレンダリングに使用するメモリ量が最小になるように実行されます。  
  
> [!NOTE]
>  一般に、表示されるイメージのサイズを指定する場合のみを指定、<xref:System.Windows.FrameworkElement.Width%2A>または<xref:System.Windows.FrameworkElement.Height%2A>両方ではないです。 いずれかのみを指定する場合、イメージの縦横比が保持されます。 それ以外の場合、イメージの拡大表示やゆがみ表示が予期せず発生する可能性があります。 イメージを制御するための動作を拡大を使用して、<xref:System.Windows.Controls.Image.Stretch%2A>と<xref:System.Windows.Controls.Image.StretchDirection%2A>プロパティ。  
  
> [!NOTE]
>  いずれかでイメージのサイズを指定すると<xref:System.Windows.FrameworkElement.Width%2A>または<xref:System.Windows.FrameworkElement.Height%2A>、いずれかを設定する必要がありますも<xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A>または<xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelHeight%2A>それぞれ同じサイズにします。  
  
 <xref:System.Windows.Controls.Image.Stretch%2A>プロパティがイメージ要素の塗りつぶしにイメージのソースを拡大する方法を決定します。 詳細については、<xref:System.Windows.Media.Stretch> 列挙型のページをご覧ください。  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## <a name="example"></a>例  
 次の例は、コードを使用して幅 200 ピクセルのイメージをレンダリングする方法を示しています。  
  
> [!NOTE]
>  設定<xref:System.Windows.Media.Imaging.BitmapImage>プロパティ内で実行する必要があります、<xref:System.Windows.Media.Imaging.BitmapImage.BeginInit%2A>と<xref:System.Windows.Media.Imaging.BitmapImage.EndInit%2A>ブロックします。  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## <a name="see-also"></a>関連項目

- [イメージングの概要](../graphics-multimedia/imaging-overview.md)
