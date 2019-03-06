---
title: TreeView のスタイルとテンプレート
ms.date: 03/30/2017
helpviewer_keywords:
- ControlTemplate [WPF], TreeView
- templates [WPF], TreeView
- parts [WPF], TreeView
- states [WPF], TreeView
- styles [WPF], TreeView
- TreeView [WPF], styles and templates
ms.assetid: a49adb77-0202-4caa-b94a-8bb110d7fa9a
ms.openlocfilehash: 300fd8d6c6bc8a73257d71280bbb0b5565c275ec
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57375559"
---
# <a name="treeview-styles-and-templates"></a>TreeView のスタイルとテンプレート
このトピックでは、スタイルとテンプレートについて説明します、<xref:System.Windows.Controls.TreeView>コントロール。 既定値を変更する<xref:System.Windows.Controls.ControlTemplate>固有の外観を制御します。 詳細については、「[ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](customizing-the-appearance-of-an-existing-control.md)」を参照してください。  
  
## <a name="treeview-parts"></a>TreeView のパーツ  
 <xref:System.Windows.Controls.TreeView>コントロールには、名前付きパーツはありません。  
  
 作成するときに、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.TreeView>、テンプレートが含まれます、<xref:System.Windows.Controls.ItemsPresenter>内、 <xref:System.Windows.Controls.ScrollViewer>。 (、<xref:System.Windows.Controls.ItemsPresenter>内の各項目が表示されます、 <xref:System.Windows.Controls.TreeView>、<xref:System.Windows.Controls.ScrollViewer>コントロール内でスクロールできます)。  場合、<xref:System.Windows.Controls.ItemsPresenter>の直接の子ではない、<xref:System.Windows.Controls.ScrollViewer>を付ける必要があります、<xref:System.Windows.Controls.ItemsPresenter>名、`ItemsPresenter`します。  
  
## <a name="treeview-states"></a>TreeView の状態  
 次の表のビジュアルの状態、<xref:System.Windows.Controls.TreeView>コントロール。  
  
|VisualState 名|VisualStateGroup 名|説明|  
|-|-|-|  
|有効|ValidationStates|コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。|  
  
## <a name="treeviewitem-parts"></a>TreeViewItem のパーツ  
 次の表に、名前付きパーツ、<xref:System.Windows.Controls.TreeViewItem>コントロール。  
  
|パーツ|型|説明|  
|----------|----------|-----------------|  
|PART_Header|<xref:System.Windows.FrameworkElement>|そのヘッダーのコンテンツが含まれる視覚的要素、<xref:System.Windows.Controls.TreeView>コントロール。|  
  
## <a name="treeviewitem-states"></a>TreeViewItem の状態  
 次の表に、用ビジュアル状態<xref:System.Windows.Controls.TreeViewItem>コントロール。  
  
|VisualState 名|VisualStateGroup 名|説明|  
|----------------------|---------------------------|-----------------|  
|標準|CommonStates|既定の状態です。|  
|MouseOver|CommonStates|マウス ポインターを置いた、<xref:System.Windows.Controls.TreeViewItem>します。|  
|無効|CommonStates|<xref:System.Windows.Controls.TreeViewItem>は無効です。|  
|フォーカスされている|FocusStates|<xref:System.Windows.Controls.TreeViewItem>にフォーカスがあります。|  
|フォーカスされていない|FocusStates|<xref:System.Windows.Controls.TreeViewItem>にフォーカスがないです。|  
|[展開済み]|ExpansionStates|<xref:System.Windows.Controls.TreeViewItem>コントロールを展開します。|  
|Collapsed|ExpansionStates|<xref:System.Windows.Controls.TreeViewItem>コントロールが折りたたまれています。|  
|HasItems|HasItemsStates|<xref:System.Windows.Controls.TreeViewItem>項目が含まれています。|  
|項目|HasItemsStates|<xref:System.Windows.Controls.TreeViewItem>項目はありません。|  
|選択済み|SelectionStates|<xref:System.Windows.Controls.TreeViewItem>が選択されています。|  
|SelectedInactive|SelectionStates|<xref:System.Windows.Controls.TreeViewItem>は選択したがアクティブではありません。|  
|未選択|SelectionStates|<xref:System.Windows.Controls.TreeViewItem>が選択されていません。|  
|有効|ValidationStates|コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。|  
  
## <a name="treeview-controltemplate-example"></a>TreeView ControlTemplate の例  
 次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.TreeView>コントロールとその関連する型。  
  
 [!code-xaml[ControlTemplateExamples#TreeView](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/treeview.xaml#treeview)]  
  
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
