---
title: '方法: UIElement を左右または上下に反転させる'
ms.date: 03/30/2017
helpviewer_keywords:
- flipping UIElements [WPF]
- UIElements [WPF], flipping
ms.assetid: 02c6730f-65c0-40d5-a553-4cb663721882
ms.openlocfilehash: 6b3da322493d17e4f8e36a35b9a0e40fdc9dc685
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215522"
---
# <a name="how-to-flip-a-uielement-horizontally-or-vertically"></a>方法: UIElement を左右または上下に反転させる
この例は、使用する方法を示します、<xref:System.Windows.Media.ScaleTransform>反転する、<xref:System.Windows.UIElement>水平方向または垂直方向にします。 この例で、<xref:System.Windows.Controls.Button>コントロール (一種の<xref:System.Windows.UIElement>) を適用することで反転、<xref:System.Windows.Media.ScaleTransform>にその<xref:System.Windows.UIElement.RenderTransform%2A>プロパティ。  
  
## <a name="example"></a>例  
 次の図は、反転する ボタンを示します。  
  
 ![変換のないボタン](./media/graphicsmm-buttonflipbeforeflip.gif "graphicsmm_buttonflipbeforeflip")  
反転する UIElement  
  
 ボタンを作成するコードを次に示します。  
  
 [!code-xaml[Transforms_snip#GraphicsMMButtonWithoutFlip](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmbuttonwithoutflip)]  
  
## <a name="example"></a>例  
 ボタンを水平方向に反転するには作成、<xref:System.Windows.Media.ScaleTransform>設定とその<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>プロパティを-1 にします。 適用、<xref:System.Windows.Media.ScaleTransform>をボタンの<xref:System.Windows.UIElement.RenderTransform%2A>プロパティ。  
  
 [!code-xaml[Transforms_snip#GraphicsMMFlipButtonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmflipbuttonexample1)]  
  
 ![水平方向に反転されるボタン&#40;0, 0&#41;](./media/graphicsmm-buttonfliphorizontalflip-displaced.gif "graphicsmm_buttonfliphorizontalflip_displaced")  
ScaleTransform を適用した後、ボタン  
  
## <a name="example"></a>例  
 前の図からわかるように、ボタンの反転がも変わりました。 ボタンは左下隅から反転したためです。 適用する場所で、ボタンを反転する、<xref:System.Windows.Media.ScaleTransform>端のない、中央にします。 適用する簡単な方法、<xref:System.Windows.Media.ScaleTransform>ボタン センターで、ボタンの設定には<xref:System.Windows.UIElement.RenderTransformOrigin%2A>プロパティを 0.5 0.5 です。  
  
 [!code-xaml[Transforms_snip#GraphicsMMFlipButtonExample2](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmflipbuttonexample2)]  
  
 ![中心の周り水平方向に反転されるボタン](./media/graphicsmm-buttonfliphorizontalflip-inplace.gif "graphicsmm_buttonfliphorizontalflip_inplace")  
Rendertransformorigin が 0.5 ボタン 0.5  
  
## <a name="example"></a>例  
 ボタンを垂直方向に反転するには設定、<xref:System.Windows.Media.ScaleTransform>オブジェクトの<xref:System.Windows.Media.ScaleTransform.ScaleY%2A>プロパティの代わりにその<xref:System.Windows.Media.ScaleTransform.ScaleX%2A>プロパティ。  
  
 [!code-xaml[Transforms_snip#GraphicsMMVerticalFlipButtonExample2](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/FlipExample.xaml#graphicsmmverticalflipbuttonexample2)]  
  
 ![中心の周り垂直方向に反転されるボタン](./media/graphicsmm-buttonflipverticalflip-inplace.gif "graphicsmm_buttonflipverticalflip_inplace")  
垂直方向に反転したボタン  
  
## <a name="see-also"></a>関連項目

- [変換の概要](../graphics-multimedia/transforms-overview.md)
