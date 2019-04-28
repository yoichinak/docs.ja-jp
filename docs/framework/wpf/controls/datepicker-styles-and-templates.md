---
title: DatePicker のスタイルとテンプレート
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], DatePicker
- DatePicker [WPF], styles and templates
- templates [WPF], DatePicker
- parts [WPF], DatePicker
- styles [WPF], DatePicker
- states [WPF], DatePicker
ms.assetid: c430a657-692f-44bd-a549-2341f92d6115
ms.openlocfilehash: 5c8e199dd7123e1490c8a836a62ffea158797eb8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61912250"
---
# <a name="datepicker-styles-and-templates"></a>DatePicker のスタイルとテンプレート
このトピックでは、スタイルとテンプレートについて説明します、<xref:System.Windows.Controls.DatePicker>コントロール。 既定値を変更する<xref:System.Windows.Controls.ControlTemplate>固有の外観を制御します。 詳細については、「[ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](customizing-the-appearance-of-an-existing-control.md)」を参照してください。  
  
## <a name="datepicker-parts"></a>DatePicker のパーツ  
 次の表に、名前付きパーツ、<xref:System.Windows.Controls.DatePicker>コントロール。  
  
|パーツ|型|説明|  
|-|-|-|  
|PART_Root|<xref:System.Windows.Controls.Grid>|コントロールのルートです。|  
|PART_Button|<xref:System.Windows.Controls.Button>|ボタンを開いたり閉じたりすること、<xref:System.Windows.Controls.Calendar>します。|  
|PART_TextBox|<xref:System.Windows.Controls.Primitives.DatePickerTextBox>|テキスト ボックスは、日付を入力することができます。|  
|PART_Popup|<xref:System.Windows.Controls.Primitives.Popup>|ポップアップを<xref:System.Windows.Controls.DatePicker>コントロール。|  
  
## <a name="datepicker-states"></a>DatePicker の状態  
 次の表のビジュアルの状態、<xref:System.Windows.Controls.DatePicker>コントロール。  
  
|VisualState 名|VisualStateGroup 名|説明|  
|-|-|-|  
|標準|CommonStates|既定の状態です。|  
|無効|CommonStates|<xref:System.Windows.Controls.DatePicker>は無効です。|  
|有効|ValidationStates|コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。|  
  
## <a name="datepickertextbox-parts"></a>DatePickerTextBox パーツ  
 次の表に、名前付きパーツ、<xref:System.Windows.Controls.Primitives.DatePickerTextBox>コントロール。  
  
|パーツ|型|説明|  
|-|-|-|  
|PART_Watermark|<xref:System.Windows.Controls.ContentControl>|最初のテキストを含む要素、<xref:System.Windows.Controls.DatePicker>します。|  
|PART_ContentElement|<xref:System.Windows.FrameworkElement>|ビジュアル要素を含めることができます、<xref:System.Windows.FrameworkElement>します。 テキスト、<xref:System.Windows.Controls.TextBox>がこの要素に表示されます。|  
  
## <a name="datepickertextbox-states"></a>DatePickerTextBox 状態  
 次の表のビジュアルの状態、<xref:System.Windows.Controls.Primitives.DatePickerTextBox>コントロール。  
  
|VisualState 名|VisualStateGroup 名|説明|  
|-|-|-|  
|標準|CommonStates|既定の状態です。|  
|無効|CommonStates|<xref:System.Windows.Controls.Primitives.DatePickerTextBox>は無効です。|  
|MouseOver|CommonStates|マウス ポインターを置いた、<xref:System.Windows.Controls.Primitives.DatePickerTextBox>します。|  
|ReadOnly|CommonStates|内のテキストを変更することはできません、ユーザー、<xref:System.Windows.Controls.Primitives.DatePickerTextBox>します。|  
|フォーカスされている|FocusStates|コントロールにフォーカスがあります。|  
|フォーカスされていない|FocusStates|コントロールにフォーカスがありません。|  
|透かし|WatermarkStates|コントロールには、その最初のテキストが表示されます。  <xref:System.Windows.Controls.Primitives.DatePickerTextBox>ユーザーがいないテキストを入力または日付を選択した場合は、状態です。|  
|Unwatermarked|WatermarkStates|ユーザーがテキストを入力、<xref:System.Windows.Controls.Primitives.DatePickerTextBox>で日付を選択したか、<xref:System.Windows.Controls.DatePicker>します。|  
|有効|ValidationStates|コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。|  
  
## <a name="datepicker-controltemplate-example"></a>DatePicker の ControlTemplate の例  
 次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.DatePicker>コントロール。  
  
 [!code-xaml[ControlTemplateExamples#DatePicker](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/datepicker.xaml#datepicker)]  
  
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
