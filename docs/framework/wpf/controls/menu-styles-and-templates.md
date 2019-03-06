---
title: メニューのスタイルとテンプレート
ms.date: 03/30/2017
helpviewer_keywords:
- styles [WPF], Menu
- ControlTemplate [WPF], Menu
- Menu [WPF], styles and templates
- states [WPF], Menu
- templates [WPF], Menu
- parts [WPF], Menu
ms.assetid: b89da183-9b87-42c6-ac53-731a42c7b09e
ms.openlocfilehash: d5b170bff841369e48d082f018577ee8f6f09f39
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57355624"
---
# <a name="menu-styles-and-templates"></a>メニューのスタイルとテンプレート
このトピックでは、スタイルとテンプレートについて説明します、<xref:System.Windows.Controls.Menu>コントロール。 既定値を変更する<xref:System.Windows.Controls.ControlTemplate>固有の外観を制御します。 詳細については、「[ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](customizing-the-appearance-of-an-existing-control.md)」を参照してください。  
  
## <a name="menu-parts"></a>メニューの部品  
 <xref:System.Windows.Controls.Menu>コントロールには、名前付きパーツはありません。  
  
 作成するときに、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.Menu>、テンプレートが含まれます、<xref:System.Windows.Controls.ItemsPresenter>内、 <xref:System.Windows.Controls.ScrollViewer>。 (、<xref:System.Windows.Controls.ItemsPresenter>内の各項目が表示されます、 <xref:System.Windows.Controls.Menu>、<xref:System.Windows.Controls.ScrollViewer>コントロール内でスクロールできます)。  場合、<xref:System.Windows.Controls.ItemsPresenter>の直接の子ではない、<xref:System.Windows.Controls.ScrollViewer>を付ける必要があります、<xref:System.Windows.Controls.ItemsPresenter>名、`ItemsPresenter`します。  
  
## <a name="menu-states"></a>メニューの状態  
 次の表のビジュアルの状態、<xref:System.Windows.Controls.Menu>コントロール。  
  
|VisualState 名|VisualStateGroup 名|説明|  
|-|-|-|  
|有効|ValidationStates|コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。|  
  
## <a name="menuitem-parts"></a>MenuItem のパーツ  
 次の表に、名前付きパーツ、<xref:System.Windows.Controls.Menu>コントロール。  
  
|パーツ|型|説明|  
|-|-|-|  
|PART_Popup|<xref:System.Windows.Controls.Primitives.Popup>|サブメニューの領域。|  
  
 作成するときに、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.MenuItem>、テンプレートが含まれます、<xref:System.Windows.Controls.ItemsPresenter>内、 <xref:System.Windows.Controls.ScrollViewer>。 (、<xref:System.Windows.Controls.ItemsPresenter>内の各項目が表示されます、 <xref:System.Windows.Controls.MenuItem>、<xref:System.Windows.Controls.ScrollViewer>コントロール内でスクロールできます)。  場合、<xref:System.Windows.Controls.ItemsPresenter>の直接の子ではない、<xref:System.Windows.Controls.ScrollViewer>を付ける必要があります、<xref:System.Windows.Controls.ItemsPresenter>名、`ItemsPresenter`します。  
  
## <a name="menuitem-states"></a>MenuItem の状態  
 次の表のビジュアルの状態、<xref:System.Windows.Controls.MenuItem>コントロール。  
  
|VisualState 名|VisualStateGroup 名|説明|  
|-|-|-|  
|有効|ValidationStates|コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。|  
  
## <a name="menu-and-menuitem-controltemplate-example"></a>メニューおよび MenuItem ControlTemplate の例  
 次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.Menu>コントロール。  
  
 [!code-xaml[ControlTemplateExamples#Menu](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menu)]  
  
 次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.MenuItem>コントロール。  
  
 [!code-xaml[ControlTemplateExamples#MenuItem](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuitem)]  
  
 次の例では、定義、 `MenuScrollViewer`、前の例で使用されます。  
  
 [!code-xaml[ControlTemplateExamples#MenuScrollViewer](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/menu.xaml#menuscrollviewer)]  
  
 <xref:System.Windows.Controls.ControlTemplate>例は、次のリソースの 1 つ以上を使用します。  
  
 [!code-xaml[ControlTemplateExamples#Resources](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 完全なサンプルについては、[Styling with ControlTemplates Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Styles%20&%20Templates/IntroToStylingAndTemplating)を参照してください。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.FrameworkElement.Style%2A>
- <xref:System.Windows.Controls.ControlTemplate>
- [コントロールのスタイルとテンプレート](control-styles-and-templates.md)
- [コントロールのカスタマイズ](control-customization.md)
- [スタイルとテンプレート](styling-and-templating.md)
- [ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](customizing-the-appearance-of-an-existing-control.md)
