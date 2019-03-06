---
title: ToggleButton のスタイルとテンプレート
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], ToggleButton
- ToggleButton [WPF], styles and templates
- ControlTemplate [WPF], ToggleButton
- styles [WPF], ToggleButton
- templates [WPF], ToggleButton
- parts [WPF], ToggleButton
ms.assetid: 54f23f30-4bcb-4f09-8ce4-376a13a255a1
ms.openlocfilehash: fd8d1986bf5c9b5f42a4c8146a89682f4a96b75e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57376183"
---
# <a name="togglebutton-syles-and-templates"></a>ToggleButton のスタイルとテンプレート
このトピックでは、スタイルとテンプレートについて説明します、<xref:System.Windows.Controls.Primitives.ToggleButton>コントロール。 既定値を変更する<xref:System.Windows.Controls.ControlTemplate>固有の外観を制御します。 詳細については、「[ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](customizing-the-appearance-of-an-existing-control.md)」を参照してください。  
  
## <a name="togglebutton-parts"></a>トグル ボタンのパーツ  
 <xref:System.Windows.Controls.Primitives.ToggleButton>コントロールには、名前付きパーツはありません。  
  
## <a name="togglebutton-states"></a>トグル ボタンの状態  
 次の表のビジュアルの状態、<xref:System.Windows.Controls.Primitives.ToggleButton>コントロール。  
  
|VisualState 名|VisualStateGroup 名|説明|  
|-|-|-|  
|標準|CommonStates|既定の状態です。|  
|MouseOver|CommonStates|マウス ポインターがコントロール上に配置されています。|  
|押されている|CommonStates|コントロールが押されています。|  
|無効|CommonStates|コントロールが無効になっています。|  
|フォーカスされている|FocusStates|コントロールにフォーカスがあります。|  
|フォーカスされていない|FocusStates|コントロールにフォーカスがありません。|  
|チェック済み|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> は `true` です。|  
|オフ|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> は `false` です。|  
|不確定です|CheckStates|<xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> が `true` で、<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> が `null` です。|  
|有効|ValidationStates|コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。|  
  
> [!NOTE]
>  コントロール テンプレートで不確定な表示状態が存在しない場合、チェックを行わない表示状態は、既定の状態として使用します。  
  
## <a name="togglebutton-controltemplate-example"></a>トグル ボタン ControlTemplate の例  
 次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.Primitives.ToggleButton>コントロール。  
  
 [!code-xaml[ControlTemplateExamples#ToggleButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#togglebutton)]  
  
 前の例では、次のリソースの 1 つ以上を使用します。  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 完全なサンプルについては、[Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)を参照してください。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [コントロールのスタイルとテンプレート](control-styles-and-templates.md)
- [コントロールのカスタマイズ](control-customization.md)
- [スタイルとテンプレート](styling-and-templating.md)
- [ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](customizing-the-appearance-of-an-existing-control.md)
