---
title: '方法: 要素のスピンを設定する'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], spinning elements
- spinning elements [WPF]
ms.assetid: 1f011976-8b07-4c31-9faf-019e0ddaa24c
ms.openlocfilehash: aca9bd577f2882e31e8d49abe5eeb5ade86f95f7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947253"
---
# <a name="how-to-make-an-element-spin-in-place"></a>方法: 要素のスピンを設定する
この例は、スピンを使用して要素を作成する方法を示しています、<xref:System.Windows.Media.RotateTransform>と<xref:System.Windows.Media.Animation.DoubleAnimation>します。  
  
 次の例では、適用、<xref:System.Windows.Media.RotateTransform>を<xref:System.Windows.UIElement.RenderTransform%2A>要素のプロパティ。 この例では、<xref:System.Windows.Media.Animation.DoubleAnimation>をアニメーション化する、<xref:System.Windows.Media.RotateTransform.Angle%2A>の<xref:System.Windows.Media.RotateTransform>します。 例を設定するために、スピンが要素、<xref:System.Windows.UIElement.RenderTransformOrigin%2A>ポイント (0.5, 0.5) に要素のプロパティ。  
  
## <a name="example"></a>例  
 [!code-xaml[transformanimations_snip#11](~/samples/snippets/xaml/VS_Snippets_Wpf/transformanimations_snip/XAML/RotateAboutCenterExample.xaml#11)]  
  
 例については変換が含まれているサンプル全体については、次を参照してください。 [2-d 変換のサンプル](https://go.microsoft.com/fwlink/?LinkID=158252)します。  
  
## <a name="see-also"></a>関連項目

- [アニメーションの概要](animation-overview.md)
- [変換の概要](transforms-overview.md)
