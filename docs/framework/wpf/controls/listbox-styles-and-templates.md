---
title: ListBox のスタイルとテンプレート
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], ListBox
- templates [WPF], ListBox
- states [WPF], ListBox
- ControlTemplate [WPF], ListBox
- parts [WPF], ListBox
- ListBox [WPF], styles and templates
ms.assetid: fc5764cb-c27b-495b-88d4-d969a8213ccb
ms.openlocfilehash: e3171322e0f24060422f54c74f4d2b4751433415
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357899"
---
# <a name="listbox-styles-and-templates"></a>ListBox のスタイルとテンプレート
このトピックでは、スタイルとテンプレートについて説明します、<xref:System.Windows.Controls.ListBox>コントロール。 既定値を変更する<xref:System.Windows.Controls.ControlTemplate>固有の外観を制御します。 詳細については、「[ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](customizing-the-appearance-of-an-existing-control.md)」を参照してください。  
  
## <a name="listbox-parts"></a>ListBox パーツ  
 <xref:System.Windows.Controls.ListBox>コントロールには、名前付きパーツはありません。  
  
 作成するときに、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.ListBox>、テンプレートが含まれます、<xref:System.Windows.Controls.ItemsPresenter>内、 <xref:System.Windows.Controls.ScrollViewer>。 (、<xref:System.Windows.Controls.ItemsPresenter>内の各項目が表示されます、 <xref:System.Windows.Controls.ListBox>、<xref:System.Windows.Controls.ScrollViewer>コントロール内でスクロールできます)。  場合、<xref:System.Windows.Controls.ItemsPresenter>の直接の子ではない、<xref:System.Windows.Controls.ScrollViewer>を付ける必要があります、<xref:System.Windows.Controls.ItemsPresenter>名、`ItemsPresenter`します。  
  
## <a name="listbox-states"></a>リスト ボックスの状態  
 次の表のビジュアルの状態、<xref:System.Windows.Controls.ListBox>コントロール。  
  
|VisualState 名|VisualStateGroup 名|説明|  
|-|-|-|  
|有効|ValidationStates|コントロールは有効です。|  
|InvalidFocused|ValidationStates|コントロールが無効で、フォーカスがあります。|  
|InvalidUnfocused|ValidationStates|コントロールが無効で、フォーカスがありません。|  
  
## <a name="listboxitem-parts"></a>ListBoxItem のパーツ  
 <xref:System.Windows.Controls.ListBoxItem>コントロールには、名前付きパーツはありません。  
  
## <a name="listboxitem-states"></a>ListBoxItem の状態  
 次の表のビジュアルの状態、<xref:System.Windows.Controls.ListBox>コントロール。  
  
|VisualState 名|VisualStateGroup 名|説明|  
|-|-|-|  
|標準|CommonStates|既定の状態です。|  
|MouseOver|CommonStates|マウス ポインターがコントロール上に配置されます。|  
|無効|CommonStates|この項目は無効です。|  
|フォーカスされている|FocusStates|この項目にフォーカスがあります。|  
|フォーカスされていない|FocusStates|この項目にフォーカスがありません。|  
|未選択|SelectionStates|この項目は選択されていません。|  
|選択済み|SelectionStates|この項目は、選択した currentlyplate です。|  
|SelectedUnfocused|SelectionStates|この項目は選択されていますが、フォーカスがありません。|  
|有効|ValidationStates|コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。|  
  
## <a name="listbox-controltemplate-example"></a>ListBox ControlTemplate の例  
 次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.ListBox>と<xref:System.Windows.Controls.ListBoxItem>コントロール。  
  
 [!code-xaml[ControlTemplateExamples#ListBox](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/listbox.xaml#listbox)]  
  
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
