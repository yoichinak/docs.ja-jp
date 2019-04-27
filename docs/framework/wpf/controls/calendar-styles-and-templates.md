---
title: カレンダーのスタイルとテンプレート
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], Calendar
- templates [WPF], Calendar
- states [WPF], Calendar
- parts [WPF], Calendar
- Calendar [WPF], styles and templates
- ControlTemplate [WPF], Calendar
ms.assetid: f4fcf046-7a8f-41b8-b5a8-534b64e0345c
ms.openlocfilehash: 18bef548b11f1a680c1361027b86f6952bedaad0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61912445"
---
# <a name="calendar-styles-and-templates"></a>カレンダーのスタイルとテンプレート
このトピックでは、スタイルとテンプレートについて説明します、<xref:System.Windows.Controls.Calendar>コントロール。 既定値を変更する<xref:System.Windows.Controls.ControlTemplate>固有の外観を制御します。 詳細については、「[ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](customizing-the-appearance-of-an-existing-control.md)」を参照してください。  
  
## <a name="calendar-parts"></a>予定表のパーツ  
 次の表に、名前付きパーツ、<xref:System.Windows.Controls.Calendar>コントロール。  
  
|パーツ|型|説明|  
|-|-|-|  
|PART_CalendarItem|<xref:System.Windows.Controls.Primitives.CalendarItem>|現在表示されている月または年、<xref:System.Windows.Controls.Calendar>します。|  
|PART_Root|<xref:System.Windows.Controls.Panel>|格納しているパネル、<xref:System.Windows.Controls.Primitives.CalendarItem>します。|  
  
## <a name="calendar-states"></a>予定表の状態  
 次の表のビジュアルの状態、<xref:System.Windows.Controls.Calendar>コントロール。  
  
|VisualState 名|VisualStateGroup 名|説明|  
|----------------------|---------------------------|-----------------|  
|有効|ValidationStates|コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。|  
  
## <a name="calendaritem-parts"></a>CalendarItem のパーツ  
 次の表に、名前付きパーツ、<xref:System.Windows.Controls.Primitives.CalendarItem>コントロール。  
  
|パーツ|型|説明|  
|-|-|-|  
|PART_Root|<xref:System.Windows.FrameworkElement>|コントロールのルートです。|  
|PART_PreviousButton|<xref:System.Windows.Controls.Button>|このボタンがクリックされたときに、予定表の前のページが表示されます。|  
|PART_NextButton|<xref:System.Windows.Controls.Button>|このボタンがクリックされたときに、予定表の次のページが表示されます。|  
|PART_HeaderButton|<xref:System.Windows.Controls.Button>|このボタンは、モードを 1 か月、年モード、および 10 年間モードを切り替えることができます。|  
|PART_MonthView|<xref:System.Windows.Controls.Grid>|1 か月のモードでコンテンツをホストします。|  
|PART_YearView|<xref:System.Windows.Controls.Grid>|1 年または 10 年間のモードでコンテンツをホストします。|  
|PART_DisabledVisual|<xref:System.Windows.FrameworkElement>|無効の状態のオーバーレイします。|  
|DayTitleTemplate|<xref:System.Windows.DataTemplate>|<xref:System.Windows.DataTemplate>視覚的な構造を記述します。|  
  
## <a name="calendaritem-states"></a>CalendarItem の状態  
 次の表のビジュアルの状態、<xref:System.Windows.Controls.Primitives.CalendarItem>コントロール。  
  
|VisualState 名|VisualStateGroup 名|説明|  
|-|-|-|  
|通常の状態|CommonStates|既定の状態です。|  
|無効の状態|CommonStates|予定表の状態と、<xref:System.Windows.UIElement.IsEnabled%2A>プロパティは`false`します。|  
|有効|ValidationStates|コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。|  
|有効|ValidationStates|コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。|  
  
## <a name="calendardaybutton-parts"></a>CalendarDayButton のパーツ  
 <xref:System.Windows.Controls.Primitives.CalendarDayButton>コントロールには、名前付きパーツはありません。  
  
## <a name="calendardaybutton-states"></a>CalendarDayButton の状態  
 次の表のビジュアルの状態、<xref:System.Windows.Controls.Primitives.CalendarDayButton>コントロール。  
  
|VisualState 名|VisualStateGroup 名|説明|  
|-|-|-|  
|標準|CommonStates|既定の状態です。|  
|無効|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarDayButton>は無効です。|  
|MouseOver|CommonStates|マウス ポインターを置いた、<xref:System.Windows.Controls.Primitives.CalendarDayButton>します。|  
|押されている|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarDayButton>が押されました。|  
|選択済み|SelectionStates|ボタンが選択されます。|  
|未選択|SelectionStates|ボタンが選択されていません。|  
|CalendarButtonFocused|CalendarButtonFocusStates|ボタンには、フォーカスがあります。|  
|CalendarButtonUnfocused|CalendarButtonFocusStates|ボタンにフォーカスがありません。|  
|フォーカスされている|FocusStates|ボタンには、フォーカスがあります。|  
|フォーカスされていない|FocusStates|ボタンにフォーカスがありません。|  
|アクティブ|ActiveStates|ボタンはアクティブです。|  
|非アクティブ|ActiveStates|ボタンがアクティブではできません。|  
|RegularDay|DayStates|ボタンは表しません<xref:System.DateTime.Today%2A?displayProperty=nameWithType>します。|  
|今日|DayStates|ボタンを表す<xref:System.DateTime.Today%2A?displayProperty=nameWithType>します。|  
|NormalDay|BlackoutDayStates|ボタンは、選択可能な日を表します。|  
|BlackoutDay|BlackoutDayStates|ボタンは、選択できない日を表します。|  
|有効|ValidationStates|コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。|  
  
## <a name="calendarbutton-parts"></a>CalendarButton パーツ  
 <xref:System.Windows.Controls.Primitives.CalendarButton>コントロールには、名前付きパーツはありません。  
  
## <a name="calendarbutton-states"></a>CalendarButton 状態  
 次の表のビジュアルの状態、<xref:System.Windows.Controls.Primitives.CalendarButton>コントロール。  
  
|VisualState 名|VisualStateGroup 名|説明|  
|-|-|-|  
|標準|CommonStates|既定の状態です。|  
|無効|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarButton>は無効です。|  
|MouseOver|CommonStates|マウス ポインターを置いた、<xref:System.Windows.Controls.Primitives.CalendarButton>します。|  
|押されている|CommonStates|<xref:System.Windows.Controls.Primitives.CalendarButton>が押されました。|  
|選択済み|SelectionStates|ボタンが選択されます。|  
|未選択|SelectionStates|ボタンが選択されていません。|  
|CalendarButtonFocused|CalendarButtonFocusStates|ボタンには、フォーカスがあります。|  
|CalendarButtonUnfocused|CalendarButtonFocusStates|ボタンにフォーカスがありません。|  
|フォーカスされている|FocusStates|ボタンには、フォーカスがあります。|  
|フォーカスされていない|FocusStates|ボタンにフォーカスがありません。|  
|アクティブ|ActiveStates|ボタンはアクティブです。|  
|非アクティブ|ActiveStates|ボタンがアクティブではできません。|  
|有効|ValidationStates|コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。|  
  
## <a name="calendar-controltemplate-example"></a>カレンダーの ControlTemplate の例  
 次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.Calendar>コントロールと関連する型。  
  
 [!code-xaml[ControlTemplateExamples#Calendar](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/calendar.xaml#calendar)]  
  
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
