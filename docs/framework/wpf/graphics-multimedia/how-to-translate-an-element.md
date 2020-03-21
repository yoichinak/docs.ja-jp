---
title: '方法 : 要素を変換する'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], translations
ms.assetid: 461c8273-15df-42f6-8672-89ba22887cc0
ms.openlocfilehash: addff0e22fb3f27ea924887809c0635aeb3ad67d
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111973"
---
# <a name="how-to-translate-an-element"></a>方法 : 要素を変換する
この例では、 を使用して要素を移動 (移動<xref:System.Windows.Media.TranslateTransform>) する方法を示します。  
  
 この<xref:System.Windows.Media.TranslateTransform>クラスは、絶対位置決めをサポートしないパネル内の要素を移動する場合に特に便利です。 たとえば<xref:System.Windows.Media.TranslateTransform>、要素の<xref:System.Windows.UIElement.RenderTransform%2A>プロパティに a を適用すると、 または<xref:System.Windows.Controls.StackPanel><xref:System.Windows.Controls.DockPanel>内の要素を移動できます。  
  
 要素を<xref:System.Windows.Media.TranslateTransform.X%2A>x<xref:System.Windows.Media.TranslateTransform>軸に沿って移動するには、のプロパティを使用してピクセル単位で指定します。 y<xref:System.Windows.Media.TranslateTransform.Y%2A>軸に沿って要素を移動する量をピクセル単位で指定するには、プロパティを使用します。 最後に、要素<xref:System.Windows.Media.TranslateTransform>の<xref:System.Windows.UIElement.RenderTransform%2A>プロパティにを適用します。  
  
 次の例では、<xref:System.Windows.Media.TranslateTransform>要素をを使用して、要素を右に 50 ピクセル、下に 50 ピクセル移動します。  
  
## <a name="example"></a>例  
 [!code-xaml[transformsSample#53](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/TranslateTransformExample.xaml#53)]  
  
 完全なサンプルについては[、2D 変換のサンプルを](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)参照してください。  
  
## <a name="see-also"></a>関連項目

- [変換の概要](transforms-overview.md)
