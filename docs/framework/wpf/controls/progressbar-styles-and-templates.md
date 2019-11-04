---
title: ProgressBar のスタイルとテンプレート
ms.date: 03/30/2017
helpviewer_keywords:
- parts [WPF], ProgressBar
- ProgressBar [WPF], styles and templates
- styles [WPF], ProgressBar
- ControlTemplate [WPF], ProgressBar
- templates [WPF], ProgressBar
- states [WPF], ProgressBar
ms.assetid: 935aa600-16e6-4947-a905-37a189a583dd
ms.openlocfilehash: 3a1bea39ba9b6d2cff9937a3fee1d1de41daf16b
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459871"
---
# <a name="progressbar-styles-and-templates"></a>ProgressBar のスタイルとテンプレート
このトピックでは、<xref:System.Windows.Controls.ProgressBar> コントロールのスタイルとテンプレートについて説明します。 <xref:System.Windows.Controls.ControlTemplate>の既定値を変更して外観を制御します。 詳細については、「[Customizing the Appearance of an Existing Control by Creating a ControlTemplate](customizing-the-appearance-of-an-existing-control.md)」を参照してください。  
  
## <a name="progressbar-parts"></a>ProgressBar のパーツ  
 次の表に、<xref:System.Windows.Controls.ProgressBar> コントロールの名前付きの部分を示します。  
  
|パーツ|[種類]|説明|  
|-|-|-|  
|PART_Indicator|<xref:System.Windows.FrameworkElement>|進行状況を示すオブジェクト。|  
|PART_Track|<xref:System.Windows.FrameworkElement>|進行状況インジケーターのパスを定義するオブジェクト。|  
|PART_GlowRect|<xref:System.Windows.FrameworkElement>|プログレスバーを embellishes するオブジェクト。|  
  
## <a name="progressbar-states"></a>ProgressBar の状態  
 次の表は、<xref:System.Windows.Controls.ProgressBar> コントロールの表示状態を示しています。  
  
|VisualState 名|VisualStateGroup 名|説明|  
|----------------------|---------------------------|-----------------|  
|一定|CommonStates|<xref:System.Windows.Controls.ProgressBar> は、<xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> プロパティに基づいて進行状況をレポートします。|  
|確定|CommonStates|<xref:System.Windows.Controls.ProgressBar> は、繰り返しパターンを使用して一般的な進行状況を報告します。|  
|有効|ValidationStates|コントロールは <xref:System.Windows.Controls.Validation> クラスを使用し、<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 添付プロパティは `false`ます。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 添付プロパティは、コントロールにフォーカスがある `true` です。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType> 添付プロパティは、コントロールにフォーカスがない `true` です。|  
  
## <a name="progressbar-controltemplate-example"></a>ProgressBar ControlTemplate の例  
 次の例は、<xref:System.Windows.Controls.ProgressBar> コントロールの <xref:System.Windows.Controls.ControlTemplate> を定義する方法を示しています。  
  
 [!code-xaml[ControlTemplateExamples#ProgressBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/progressbar.xaml#progressbar)]  
  
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
