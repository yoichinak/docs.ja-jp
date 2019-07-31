---
title: ScrollBar のスタイルとテンプレート
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], ScrollBar
- ControlTemplate [WPF], ScrollBar
- states [WPF], ScrollBar
- ScrollBar [WPF], styles and templates
- templates [WPF], ScrollBar
- parts [WPF], ScrollBar
ms.assetid: 066ea45a-e27d-43b0-adfe-cce6934c22f5
ms.openlocfilehash: 016556fb825ddf60af7dc572d6fda7323b9bb09d
ms.sourcegitcommit: 3eeea78f52ca771087a6736c23f74600cc662658
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/31/2019
ms.locfileid: "68671983"
---
# <a name="scrollbar-styles-and-templates"></a>ScrollBar のスタイルとテンプレート
このトピックでは、 <xref:System.Windows.Controls.Primitives.ScrollBar>コントロールのスタイルとテンプレートについて説明します。 <xref:System.Windows.Controls.ControlTemplate>の既定値を変更して外観を制御します。 詳細については、「[ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](customizing-the-appearance-of-an-existing-control.md)」を参照してください。  
  
## <a name="scrollbar-parts"></a>ScrollBar の部分  
 次の表に、 <xref:System.Windows.Controls.Primitives.ScrollBar>コントロールの名前付きの部分を示します。  
  
|パーツ|種類|説明|  
|-|-|-|  
|PART_Track|<xref:System.Windows.Controls.Primitives.Track>|の位置を示す要素のコンテナー <xref:System.Windows.Controls.Primitives.ScrollBar>。|  
  
## <a name="scrollbar-states"></a>スクロールバーの状態  
 次の表に、 <xref:System.Windows.Controls.Primitives.ScrollBar>コントロールの表示状態を示します。  
  
|VisualState 名|VisualStateGroup 名|説明|  
|----------------------|---------------------------|-----------------|  
|標準|CommonStates|既定の状態です。|  
|MouseOver|CommonStates|マウス ポインターがコントロール上に配置されます。|  
|Disabled|CommonStates|コントロールが無効になっています。|  
|有効|ValidationStates|コントロールは<xref:System.Windows.Controls.Validation>クラス<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>を使用し、添付プロパティは`false`です。|  
|InvalidFocused|ValidationStates|添付プロパティは`true`であり、コントロールにフォーカスがあります。 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>|  
|InvalidUnfocused|ValidationStates|添付プロパティが`true`であり、コントロールにフォーカスがありません。 <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>|  
  
## <a name="scrollbar-controltemplate-example"></a>ScrollBar ControlTemplate の例  
 次の例は、 <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Primitives.ScrollBar>コントロールのを定義する方法を示しています。  
  
 [!code-xaml[ControlTemplateExamples#ScrollBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/scrollbar.xaml#scrollbar)]  
  
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
