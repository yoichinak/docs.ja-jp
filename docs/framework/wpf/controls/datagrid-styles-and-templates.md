---
title: DataGrid のスタイルとテンプレート
ms.date: 03/30/2017
helpviewer_keywords:
- states [WPF], DataGrid
- ControlTemplate [WPF], DataGrid
- DataGrid [WPF], styles and templates
- templates [WPF], DataGrid
- styles [WPF], DataGrid
- parts [WPF], DataGrid
ms.assetid: 9cb31d63-f148-4d25-b079-816e73f988c7
ms.openlocfilehash: dacc1222958ab05971c9681d33a0c431b72d0531
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218460"
---
# <a name="datagrid-styles-and-templates"></a>DataGrid のスタイルとテンプレート
このトピックでは、スタイルとテンプレートについて説明します、<xref:System.Windows.Controls.DataGrid>コントロール。 既定値を変更する<xref:System.Windows.Controls.ControlTemplate>固有の外観を制御します。 詳細については、「[ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](customizing-the-appearance-of-an-existing-control.md)」を参照してください。  
  
## <a name="datagrid-parts"></a>DataGrid のパーツ  
 次の表に、名前付きパーツ、<xref:System.Windows.Controls.DataGrid>コントロール。  
  
|パーツ|型|説明|  
|-|-|-|  
|PART_ColumnHeadersPresenter|<xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter>|この行は、列ヘッダーが含まれています。|  
  
 作成するときに、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.DataGrid>、テンプレートが含まれます、<xref:System.Windows.Controls.ItemsPresenter>内、 <xref:System.Windows.Controls.ScrollViewer>。 (、<xref:System.Windows.Controls.ItemsPresenter>内の各項目が表示されます、 <xref:System.Windows.Controls.DataGrid>、<xref:System.Windows.Controls.ScrollViewer>コントロール内でスクロールできます)。  場合、<xref:System.Windows.Controls.ItemsPresenter>の直接の子ではない、<xref:System.Windows.Controls.ScrollViewer>を付ける必要があります、<xref:System.Windows.Controls.ItemsPresenter>名、`ItemsPresenter`します。  
  
 既定のテンプレート、<xref:System.Windows.Controls.DataGrid>が含まれています、<xref:System.Windows.Controls.ScrollViewer>コントロール。 によって定義されたパーツの詳細については、<xref:System.Windows.Controls.ScrollViewer>を参照してください[ScrollViewer のスタイルとテンプレート](scrollviewer-styles-and-templates.md)します。  
  
## <a name="datagrid-states"></a>DataGrid の状態  
 次の表のビジュアルの状態、<xref:System.Windows.Controls.DataGrid>コントロール。  
  
|VisualState 名|VisualStateGroup 名|説明|  
|-|-|-|  
|標準|CommonStates|既定の状態です。|  
|無効|CommonStates|コントロールが無効になっています。|  
|InvalidFocused|ValidationStates|コントロールが無効で、フォーカスがあります。|  
|InvalidUnfocused|ValidationStates|コントロールが無効で、フォーカスがありません。|  
|有効|ValidationStates|コントロールは有効です。|  
  
## <a name="datagridcell-parts"></a>DataGridCell パーツ  
 <xref:System.Windows.Controls.DataGridCell>要素には、名前付きパーツはありません。  
  
## <a name="datagridcell-states"></a>DataGridCell 状態  
 次の表のビジュアルの状態、<xref:System.Windows.Controls.DataGridCell>要素。  
  
|VisualState 名|VisualStateGroup 名|説明|  
|-|-|-|  
|標準|CommonStates|既定の状態です。|  
|MouseOver|CommonStates|マウス ポインターがセルに配置されます。|  
|フォーカスされている|FocusStates|セルにフォーカスがあります。|  
|フォーカスされていない|FocusStates|セルにフォーカスがないです。|  
|現在|CurrentStates|セルは、現在のセルです。|  
|Regular|CurrentStates|セルは、現在のセルではありません。|  
|表示|InteractionStates|セルが表示モードです。|  
|編集|InteractionStates|セルが編集モードにします。|  
|選択済み|SelectionStates|セルが選択されます。|  
|未選択|SelectionStates|セルが選択されていません。|  
|InvalidFocused|ValidationStates|セルは、有効でないし、フォーカスがあります。|  
|InvalidUnfocused|ValidationStates|セルは、有効でないしにフォーカスがないです。|  
|有効|ValidationStates|セルが無効です。|  
  
## <a name="datagridrow-parts"></a>DataGridRow パーツ  
 <xref:System.Windows.Controls.DataGridRow>要素には、名前付きパーツはありません。  
  
## <a name="datagridrow-states"></a>DataGridRow 状態  
 次の表のビジュアルの状態、<xref:System.Windows.Controls.DataGridRow>要素。  
  
|VisualState 名|VisualStateGroup 名|説明|  
|-|-|-|  
|標準|CommonStates|既定の状態です。|  
|MouseOver|CommonStates|マウスのポインターは、行に配置されます。|  
|MouseOver_Editing|CommonStates|行の上にマウス ポインターが配置され、行が編集モードにします。|  
|MouseOver_Selected|CommonStates|行の上にマウス ポインターが配置され、行を選択します。|  
|MouseOver_Unfocused_Editing|CommonStates|行の上にマウス ポインターが配置される、行が編集モード、およびにフォーカスがないです。|  
|MouseOver_Unfocused_Selected|CommonStates|行の上にマウス ポインターが配置される、行が選択されているし、フォーカスがないです。|  
|Normal_AlternatingRow|CommonStates|行が、交互の行です。|  
|Normal_Editing|CommonStates|行が編集モードにします。|  
|Normal_Selected|CommonStates|行を選択します。|  
|Unfocused_Editing|CommonStates|行が編集モードでと、フォーカスがないです。|  
|Unfocused_Selected|CommonStates|行が選択され、フォーカスがないです。|  
|InvalidFocused|ValidationStates|コントロールが無効で、フォーカスがあります。|  
|InvalidUnfocused|ValidationStates|コントロールが無効で、フォーカスがありません。|  
|有効|ValidationStates|コントロールは有効です。|  
  
## <a name="datagridrowheader-parts"></a>DataGridRowHeader パーツ  
 次の表に、名前付きパーツ、<xref:System.Windows.Controls.Primitives.DataGridRowHeader>要素。  
  
|パーツ|型|説明|  
|-|-|-|  
|PART_TopHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|上部の行ヘッダーのサイズを変更するために使用する要素。|  
|PART_BottomHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|下部にある行ヘッダーのサイズを変更するために使用する要素。|  
  
## <a name="datagridrowheader-states"></a>DataGridRowHeader 状態  
 次の表のビジュアルの状態、<xref:System.Windows.Controls.Primitives.DataGridRowHeader>要素。  
  
|VisualState 名|VisualStateGroup 名|説明|  
|-|-|-|  
|標準|CommonStates|既定の状態です。|  
|MouseOver|CommonStates|マウスのポインターは、行に配置されます。|  
|MouseOver_CurrentRow|CommonStates|行の上にマウス ポインターが配置され、その行が現在の行。|  
|MouseOver_CurrentRow_Selected|CommonStates|マウス ポインターが、行の下に、行が現在で選択されています。|  
|MouseOver_EditingRow|CommonStates|行の上にマウス ポインターが配置され、行が編集モードにします。|  
|MouseOver_Selected|CommonStates|行の上にマウス ポインターが配置され、行を選択します。|  
|MouseOver_Unfocused_CurrentRow_Selected|CommonStates|マウス ポインターが配置されている、行、行が最新で、選択した場合とにフォーカスがないです。|  
|MouseOver_Unfocused_EditingRow|CommonStates|行の上にマウス ポインターが配置される、行が編集モード、およびにフォーカスがないです。|  
|MouseOver_Unfocused_Selected|CommonStates|行の上にマウス ポインターが配置される、行が選択されているし、フォーカスがないです。|  
|Normal_CurrentRow|CommonStates|行は、現在の行です。|  
|Normal_CurrentRow_Selected|CommonStates|行は、現在の行は、され、選択されます。|  
|Normal_EditingRow|CommonStates|行が編集モードにします。|  
|Normal_Selected|CommonStates|行を選択します。|  
|Unfocused_CurrentRow_Selected|CommonStates|行は、現在の行が選択されている、およびにフォーカスがないです。|  
|Unfocused_EditingRow|CommonStates|行が編集モードでと、フォーカスがないです。|  
|Unfocused_Selected|CommonStates|行が選択され、フォーカスがないです。|  
|InvalidFocused|ValidationStates|コントロールが無効で、フォーカスがあります。|  
|InvalidUnfocused|ValidationStates|コントロールが無効で、フォーカスがありません。|  
|有効|ValidationStates|コントロールは有効です。|  
  
## <a name="datagridcolumnheaderspresenter-parts"></a>DataGridColumnHeadersPresenter パーツ  
 次の表に、名前付きパーツ、<xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter>要素。  
  
|パーツ|型|説明|  
|-|-|-|  
|PART_FillerColumnHeader|<xref:System.Windows.Controls.Primitives.DataGridColumnHeader>|列ヘッダーのプレース ホルダー。|  
  
## <a name="datagridcolumnheaderspresenter-states"></a>DataGridColumnHeadersPresenter 状態  
 次の表のビジュアルの状態、<xref:System.Windows.Controls.Primitives.DataGridColumnHeadersPresenter>要素。  
  
|VisualState 名|VisualStateGroup 名|説明|  
|-|-|-|  
|InvalidFocused|ValidationStates|セルは、有効でないし、フォーカスがあります。|  
|InvalidUnfocused|ValidationStates|セルは、有効でないしにフォーカスがないです。|  
|有効|ValidationStates|セルが無効です。|  
  
## <a name="datagridcolumnheader-parts"></a>DataGridColumnHeader パーツ  
 次の表に、名前付きパーツ、<xref:System.Windows.Controls.Primitives.DataGridColumnHeader>要素。  
  
|パーツ|型|説明|  
|-|-|-|  
|PART_LeftHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|左側の列ヘッダーのサイズを変更するために使用する要素。|  
|PART_RightHeaderGripper|<xref:System.Windows.Controls.Primitives.Thumb>|右側の列ヘッダーのサイズを変更するために使用する要素。|  
  
## <a name="datagridcolumnheader-states"></a>DataGridColumnHeader 状態  
 次の表のビジュアルの状態、<xref:System.Windows.Controls.Primitives.DataGridColumnHeader>要素。  
  
|VisualState 名|VisualStateGroup 名|説明|  
|-|-|-|  
|標準|CommonStates|既定の状態です。|  
|MouseOver|CommonStates|マウス ポインターがコントロール上に配置されています。|  
|押されている|CommonStates|コントロールが押されています。|  
|SortAscending|SortStates|列は昇順で並べ替えられます。|  
|SortDescending|SortStates|列が降順で並べ替えられます。|  
|並べ替えられていません。|SortStates|列が並べ替えられていません。|  
|InvalidFocused|ValidationStates|コントロールが無効で、フォーカスがあります。|  
|InvalidUnfocused|ValidationStates|コントロールが無効で、フォーカスがありません。|  
|有効|ValidationStates|コントロールは有効です。|  
  
## <a name="datagrid-controltemplate-example"></a>DataGrid の ControlTemplate の例  
 次の例は、定義する方法を示します、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.DataGrid>コントロールとその関連する型。  
  
 [!code-xaml[ControlTemplateExamples#DataGrid](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/datagrid.xaml#datagrid)]  
  
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
