---
title: RepeatButton のスタイルとテンプレート
ms.date: 03/30/2017
helpviewer_keywords:
- RepeatButton [WPF], styles and templates
- styles [WPF], RepeatButton
- templates [WPF], RepeatButton
- parts [WPF], RepeatButton
- ControlTemplate [WPF], RepeatButton
- states [WPF], RepeatButton
ms.assetid: fd340743-f44f-4990-9077-085301469670
ms.openlocfilehash: 86f212326bc707e4b07b8cab8d9a95d4f6ef8920
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57509591"
---
# <a name="repeatbutton-styles-and-templates"></a>RepeatButton のスタイルとテンプレート

このトピックでは、スタイルとテンプレートについて説明します、<xref:System.Windows.Controls.Primitives.RepeatButton>コントロール。 既定値を変更する<xref:System.Windows.Controls.ControlTemplate>固有の外観を制御します。 詳細については、「[ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](customizing-the-appearance-of-an-existing-control.md)」を参照してください。

## <a name="repeatbutton-parts"></a>RepeatButton のパーツ

<xref:System.Windows.Controls.Primitives.RepeatButton>コントロールには、名前付きパーツはありません。

## <a name="repeatbutton-states"></a>RepeatButton の状態

次の表のビジュアルの状態、<xref:System.Windows.Controls.Primitives.RepeatButton>コントロール。

|VisualState 名|VisualStateGroup 名|説明|
|-|-|-|
|標準|CommonStates|既定の状態です。|
|MouseOver|CommonStates|マウス ポインターがコントロール上に配置されています。|
|押されている|CommonStates|コントロールが押されています。|
|無効|CommonStates|コントロールが無効になっています。|
|フォーカスされている|FocusStates|コントロールにフォーカスがあります。|
|フォーカスされていない|FocusStates|コントロールにフォーカスがありません。|
|有効|ValidationStates|コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。|
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。|
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。|

## <a name="repeatbutton-controltemplate-example"></a>RepeatButton ControlTemplate の例

次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.Primitives.RepeatButton>コントロール。

[!code-xaml[ControlTemplateExamples#RepeatButton](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#repeatbutton)]

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
