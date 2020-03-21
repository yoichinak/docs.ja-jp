---
title: '方法 : 要素のスピンを設定する'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
ms.openlocfilehash: a1b515822391de08ec8ed8ff0ff1f0086874dc02
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112077"
---
# <a name="how-to-make-an-element-spin-in-place"></a>方法 : 要素のスピンを設定する
この例では、<xref:System.Windows.Media.RotateTransform>および を使用して要素をスピンさせる<xref:System.Windows.Media.Animation.DoubleAnimation>方法を示します。  
  
 要素のプロパティに<xref:System.Windows.Media.RotateTransform>を適用<xref:System.Windows.UIElement.RenderTransform%2A>する例を次に示します。 この例では、<xref:System.Windows.Media.Animation.DoubleAnimation>の アニメーション<xref:System.Windows.Media.RotateTransform.Angle%2A>を行うために<xref:System.Windows.Media.RotateTransform>を使用します。 要素を所定の位置で回転させるために、要素の<xref:System.Windows.UIElement.RenderTransformOrigin%2A>プロパティをポイント(0.5,0.5)に設定します。  
  
## <a name="example"></a>例  
 [!code-xaml[transformanimations_snip#11](~/samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 その他の変換例を含む完全なサンプルについては[、「2D 変換のサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [アニメーションの概要](animation-overview.md)
- [変換の概要](transforms-overview.md)
