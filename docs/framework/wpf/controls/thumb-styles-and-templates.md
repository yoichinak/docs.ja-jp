---
title: つまみのスタイルとテンプレート
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], Thumb
- styles [WPF], Thumb
- templates [WPF], Thumb
- Thumb [WPF], styles and templates
- ControlTemplate [WPF], Thumb
- parts [WPF], Thumb
ms.assetid: 86a49235-62d9-414e-923e-53126e3f930a
ms.openlocfilehash: c2114a02016db96d898a394b6892b6d3042d81ff
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458240"
---
# <a name="thumb-styles-and-templates"></a>つまみのスタイルとテンプレート

このトピックでは、<xref:System.Windows.Controls.Primitives.Thumb> コントロールのスタイルとテンプレートについて説明します。 <xref:System.Windows.Controls.ControlTemplate>の既定値を変更して外観を制御します。 詳細については、「[Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md)」を参照してください。

## <a name="thumb-parts"></a>Thumb パーツ

<xref:System.Windows.Controls.Primitives.Thumb> コントロールには、名前付きの部分がありません。

## <a name="thumb-states"></a>Thumb の状態

次の表は、<xref:System.Windows.Controls.Primitives.Thumb> コントロールの表示状態を示しています。

|VisualState 名|VisualStateGroup 名|説明|
|-|-|-|
|標準|CommonStates|既定の状態です。|
|MouseOver|CommonStates|マウス ポインターがコントロール上に配置されます。|
|押されている|CommonStates|コントロールが押されています。|
|Disabled|CommonStates|コントロールが無効になっています。|
|フォーカスされている|FocusStates|コントロールにフォーカスがあります。|
|フォーカスされていない|FocusStates|コントロールにフォーカスがありません。|
|有効|ValidationStates|コントロールは <xref:System.Windows.Controls.Validation> クラスを使用し、<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 添付プロパティは `false`ます。|
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 添付プロパティは、コントロールにフォーカスがある `true` です。|
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 添付プロパティは、コントロールにフォーカスがない `true` です。|

## <a name="thumb-controltemplate-example"></a>Thumb ControlTemplate の例

次の例は、<xref:System.Windows.Controls.Primitives.Thumb> コントロールの <xref:System.Windows.Controls.ControlTemplate> を定義する方法を示しています。

[!code-xaml[ControlTemplateExamples#Thumb](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#thumb)]

前の例では、次のリソースの 1 つ以上を使用します。

[!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]

完全なサンプルについては、[Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)を参照してください。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [コントロールのスタイルとテンプレート](control-styles-and-templates.md)
- [コントロールのカスタマイズ](control-customization.md)
- [スタイルとテンプレート](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](customizing-the-appearance-of-an-existing-control.md)
