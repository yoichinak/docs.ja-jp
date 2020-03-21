---
title: GroupBox のスタイルとテンプレート
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], GroupBox
- parts [WPF], GroupBox
- GroupBox [WPF], styles and templates
- states [WPF], GroupBox
- styles [WPF], GroupBox
- templates [WPF], GroupBox
ms.assetid: 33df7037-0a1b-476f-b9d0-41566a777699
ms.openlocfilehash: 474cda0abc6a18c015836c749c78f4d33aa5abd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187477"
---
# <a name="groupbox-styles-and-templates"></a>GroupBox のスタイルとテンプレート
<a name="introduction"></a>このトピックでは、コントロールのスタイルとテンプレートについて<xref:System.Windows.Controls.GroupBox>説明します。 <xref:System.Windows.Controls.ControlTemplate>の既定値を変更して外観を制御します。 詳細については、「[コントロールのテンプレートを作成する」を](../../../desktop-wpf/themes/how-to-create-apply-template.md)参照してください。  
  
<a name="groupbox_parts"></a>
## <a name="groupbox-parts"></a>グループボックスパーツ  
 <xref:System.Windows.Controls.GroupBox>コントロールには名前付きパーツがありません。  
  
<a name="groupbox_states"></a>
## <a name="groupbox-states"></a>グループボックスの状態  
 次の表に、コントロールの表示状態<xref:System.Windows.Controls.GroupBox>を示します。  
  
|VisualState 名|VisualStateGroup 名|説明|  
|-|-|-|  
|有効|ValidationStates|コントロールはクラスを<xref:System.Windows.Controls.Validation>使用し、<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`です。|  
|InvalidFocused|ValidationStates|添付<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>プロパティは、`true`コントロールにフォーカスがあります。|  
|InvalidUnfocused|ValidationStates|添付<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>プロパティは、`true`コントロールにフォーカスがありません。|  
  
<a name="groupbox_controltemplate_example"></a>
## <a name="groupbox-controltemplate-example"></a>グループ ボックス コントロール テンプレートの例  
 コントロールの を定義する方法を<xref:System.Windows.Controls.ControlTemplate>次の<xref:System.Windows.Controls.GroupBox>例に示します。  
  
 [!code-xaml[ControlTemplateExamples#GroupBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/groupbox.xaml#groupbox)]  
  
 では<xref:System.Windows.Controls.ControlTemplate>、次のリソースの 1 つ以上を使用します。  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 完全なサンプルについては、[Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [コントロールのスタイルとテンプレート](control-styles-and-templates.md)
- [コントロールのカスタマイズ](control-customization.md)
- [スタイルとテンプレート](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [コントロールのテンプレートを作成する](../../../desktop-wpf/themes/how-to-create-apply-template.md)
