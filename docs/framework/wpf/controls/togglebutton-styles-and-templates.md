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
ms.openlocfilehash: e055dcbd557f9b90eb2fe99ad15a05b6f229fd28
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805913"
---
# <a name="togglebutton-styles-and-templates"></a>ToggleButton のスタイルとテンプレート

このトピックでは、コントロールのスタイルとテンプレートについて<xref:System.Windows.Controls.Primitives.ToggleButton>説明します。 <xref:System.Windows.Controls.ControlTemplate>の既定値を変更して外観を制御します。 詳細については、「[コントロールのテンプレートを作成する」を](../../../desktop-wpf/themes/how-to-create-apply-template.md)参照してください。

## <a name="togglebutton-parts"></a>トグルボタンパーツ

<xref:System.Windows.Controls.Primitives.ToggleButton>コントロールには名前付きパーツがありません。

## <a name="togglebutton-states"></a>トグルボタンの状態

次の表に、コントロールの表示状態<xref:System.Windows.Controls.Primitives.ToggleButton>を示します。

|VisualState 名|VisualStateGroup 名|説明|
|-|-|-|
|Normal|CommonStates|既定の状態です。|
|MouseOver|CommonStates|マウス ポインターがコントロール上に配置されます。|
|押されている|CommonStates|コントロールが押されています。|
|無効|CommonStates|コントロールが無効になっています。|
|フォーカスされている|FocusStates|コントロールにフォーカスがあります。|
|フォーカスされていない|FocusStates|コントロールにフォーカスがありません。|
|オン|チェックステート|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> は `true` です。|
|オフ|チェックステート|<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> は `false` です。|
|不確定|チェックステート|<xref:System.Windows.Controls.Primitives.ToggleButton.IsThreeState%2A> が `true` で、<xref:System.Windows.Controls.Primitives.ToggleButton.IsChecked%2A> が `null` です。|
|有効|ValidationStates|コントロールはクラスを<xref:System.Windows.Controls.Validation>使用し、<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`です。|
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`、コントロールにフォーカスがあります。|
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティが`true`、コントロールにフォーカスがありません。|

> [!NOTE]
> Indeterminate 表示状態がコントロール テンプレートに存在しない場合、チェックされていない表示状態が既定の表示状態として使用されます。

## <a name="togglebutton-controltemplate-example"></a>トグルボタンコントロールテンプレートの例

コントロールの を定義する方法を<xref:System.Windows.Controls.ControlTemplate>次の<xref:System.Windows.Controls.Primitives.ToggleButton>例に示します。

[!code-xaml[ControlTemplateExamples#ToggleButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/combobox.xaml#togglebutton)]

前の例では、次のリソースの 1 つ以上を使用します。

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

完全なサンプルについては、[Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)を参照してください。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [コントロールのスタイルとテンプレート](control-styles-and-templates.md)
- [コントロールのカスタマイズ](control-customization.md)
- [スタイルとテンプレート](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [コントロールのテンプレートを作成する](../../../desktop-wpf/themes/how-to-create-apply-template.md)
