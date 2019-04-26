---
title: '方法: UIElement を透明または半透明にする'
ms.date: 03/30/2017
helpviewer_keywords:
- UIElements [WPF], transparency
- opacity [WPF], of UIElements
- transparency of UIElements [WPF]
- UIElements [WPF], opacity
ms.assetid: a49fc8d6-7b32-4f28-9122-39b632a19b4b
ms.openlocfilehash: 1de9a7e11fee241ecb71242e9808e77b7e5e63b0
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370528"
---
# <a name="how-to-make-a-uielement-transparent-or-semi-transparent"></a>方法: UIElement を透明または半透明にする
この例では、作成、<xref:System.Windows.UIElement>透明または半透明にします。 設定する要素を透明または半透明にするその<xref:System.Windows.UIElement.Opacity%2A>プロパティ。 値`0.0`の値の中に、完全に透明な要素は、`1.0`要素を完全に不透明になります。 値`0.5`、不透明で、要素を 50% になります。 要素の<xref:System.Windows.UIElement.Opacity%2A>に設定されている`1.0`既定。  
  
## <a name="example"></a>例  
 次の例のセット、<xref:System.Windows.UIElement.Opacity%2A>するボタンの`0.25`、作成し、その内容 (この例では、ボタンのテキスト) では 25% 不透明です。  
  
 [!code-xaml[brushsamples_snip#2](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#2)]  
  
 [!code-csharp[brushsamples_procedural_snip#2](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#2)]  
  
 要素の内容がある独自場合<xref:System.Windows.UIElement.Opacity%2A>設定、それらの値を含んでいる要素に対して乗算<xref:System.Windows.UIElement.Opacity%2A>します。  
  
 次の例では、ボタンの<xref:System.Windows.UIElement.Opacity%2A>に`0.25`、および<xref:System.Windows.UIElement.Opacity%2A>の<xref:System.Windows.Controls.Image>をボタンに含まれるコントロール`0.5`します。 その結果、イメージには、12.5% 不透明が表示されます。0.25 * 0.5 = 0.125.  
  
 [!code-xaml[brushsamples_snip#3](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#3)]  
  
 [!code-csharp[brushsamples_procedural_snip#3](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#3)]  
  
 要素の不透明度を制御するもう 1 つの方法は、の不透明度を設定するのには、<xref:System.Windows.Media.Brush>要素を描画します。 このアプローチは選択的に、要素の各部分の不透明度を変更することができ、要素を使用してパフォーマンスのメリットが得<xref:System.Windows.UIElement.Opacity%2A>プロパティ。 次の例のセット、<xref:System.Windows.Media.Brush.Opacity%2A>の<xref:System.Windows.Media.SolidColorBrush>ボタンの描画に使用される<xref:System.Windows.Controls.Control.Background%2A>に設定されている`0.25`します。 その結果、ブラシの背景が 25% 不透明でが不透明度 100% のままの内容 (ボタンのテキスト)。  
  
 [!code-xaml[brushsamples_snip#4](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/OpacityExample.xaml#4)]  
  
 [!code-csharp[brushsamples_procedural_snip#4](~/samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/OpacityExample.cs#4)]  
  
 ブラシ内の個々の色の不透明度を制御することもできます。色とブラシの詳細については、「[純色およびグラデーションによる塗りつぶしの概要](../graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)」を参照してください。 要素の不透明度をアニメーション化する方法を示す例は、「[要素またはブラシの不透明度をアニメーション化する](../graphics-multimedia/how-to-animate-the-opacity-of-an-element-or-brush.md)」を参照してください。
