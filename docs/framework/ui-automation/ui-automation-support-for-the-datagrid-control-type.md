---
title: UI オートメーションによる DataGrid コントロール型のサポート
ms.date: 03/30/2017
helpviewer_keywords:
- Data Grid control type
- control types, Data Grid
- UI Automation, Data Grid control type
ms.assetid: a3db4a3f-feb5-4e5f-9b42-aae7fa816e8a
ms.openlocfilehash: 8a991af5e8e48ce377acf1c1d8342d163d17c1e4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441084"
---
# <a name="ui-automation-support-for-the-datagrid-control-type"></a>UI オートメーションによる DataGrid コントロール型のサポート
> [!NOTE]
> このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI Automation (Windows のオートメーション API: UI オートメーション)](/windows/win32/winauto/entry-uiauto-win32)」を参照してください。  
  
 このトピックでは、DataGrid コントロール型の [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] サポートに関する情報を提供します。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]でのコントロール型とは、コントロールが `ControlType` プロパティを使用するために満たす必要がある一連の条件のことです。 これらの条件には、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリー構造、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] のプロパティ値、およびコントロール パターンに関する特定のガイドラインが含まれます。  
  
 DataGrid コントロール型により、列で表されるメタデータを含む項目をユーザーが簡単に扱うことができます。 データ グリッド コントロールでは、項目の行と、それらの項目に関する情報の列があります。 Microsoft Vista Explorer のリスト ビュー コントロールは、DataGrid コントロール型をサポートする例です。  
  
 以下の各セクションで、DataGrid コントロール型に必要な [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリー構造、プロパティ、コントロール パターン、およびイベントを定義します。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] の要件は、 [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]、 [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]、 [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]のいずれの場合も、すべてのデータ グリッド コントロールに適用されます。  
  
## <a name="required-ui-automation-tree-structure"></a>必須の UI オートメーション ツリー構造  
 次の表では、データ グリッド コントロールに関連する [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリーのコントロール ビューとコンテンツ ビューを示し、それぞれのビューに含まれる可能性のある内容について説明します。 For more information about the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree, see [UI Automation Tree Overview](ui-automation-tree-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリー - コントロール ビュー|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリー - コンテンツ ビュー|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|DataGrid<br /><br /> <ul><li>Header (0、1、または 2)<br /><br /> <ul><li>HeaderItem (列または行の数)</li></ul></li><li>DataItem (0 以上。階層で構造化できます)</li></ul>|DataGrid<br /><br /> -   DataItem (0 or more; can be structured in hierarchy)|  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>必須の UI オートメーション プロパティ  
 次の表に、データ グリッド コントロールに特に関連する値または定義を持つプロパティを示します。 For more information on [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] properties, see [UI Automation Properties for Clients](ui-automation-properties-for-clients.md).  
  
|property|[値]|ノート|  
|--------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|「ノート」をご覧ください。|このプロパティの値は、アプリケーション内のすべてのコントロールで一意である必要があります。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|「ノート」をご覧ください。|コントロール全体を格納する最も外側の四角形。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|「ノート」をご覧ください。|四角形領域が存在する場合にサポートされます。 四角形領域内にクリック不可能な点が存在し、特別なヒット テストを実行する場合は、オーバーライドしてクリック可能な点を提供します。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|DataGrid|この値は、すべての UI フレームワークで同じです。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|このプロパティの値は、常に True にする必要があります。 つまり、データ グリッド コントロールが常に [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリーのコンテンツ ビューに存在している必要があります。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|このプロパティの値は、常に True にする必要があります。 つまり、データ グリッド コントロールが常に [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリーのコンテンツ ビューに存在している必要があります。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|「ノート」をご覧ください。|コントロールがキーボード フォーカスを受け取ることができる場合は、このプロパティをサポートする必要があります。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|「ノート」をご覧ください。|静的なテキスト ラベルがある場合、このプロパティは対象のコントロールへの参照を公開する必要があります。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"データ グリッド"|DataGrid コントロール型に対応するローカライズされた文字列。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|「ノート」をご覧ください。|データ グリッド コントロールは、通常、静的テキスト ラベルから `Name` プロパティの列を取得します。 静的なテキスト ラベルがない場合は、アプリケーション開発者が `Name` のプロパティ値を割り当てる必要があります。 `Name` プロパティの値が、編集コントロールのテキストの内容になることは決してありません。|  
  
## <a name="required-ui-automation-control-patterns"></a>必須の UI オートメーション コントロール パターン  
 次の表に、すべてのデータ グリッド コントロールでサポートされなければならないコントロール パターンを示します。 コントロール パターンについて詳しくは、「 [UI Automation Control Patterns Overview](ui-automation-control-patterns-overview.md)」をご覧ください。  
  
|コントロール パターン|Support|ノート|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|[はい]|データ グリッド コントロール自体は、メタデータを格納する項目がグリッドに配置されるため、常に、グリッド コントロール パターンをサポートします。|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|状況に依存|データ グリッドをスクロールする機能はコンテンツ、およびスクロール バーが存在するかどうかによって異なります。|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|状況に依存|データ グリッドを選択する機能は、コンテンツに依存します。|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|[はい]|データ グリッド コントロールはサブツリー内に常にヘッダーがあるため、Table コントロール パターンがサポートされる必要があります。|  
  
 データ グリッド コンテナー内のデータ項目は、少なくとも次をサポートします。  
  
- 選択項目コントロール パターン (データ グリッドが選択可能な場合)  
  
- スクロール項目コントロール パターン (データ グリッドがスクロール可能な場合)  
  
- グリッド項目コントロール パターン  
  
- テーブル項目コントロール パターン  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>必須の UI オートメーション イベント  
 次の表に、すべてのデータ グリッド コントロールでサポートされなければならない [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] イベントを示します。 イベントについて詳しくは、「 [UI Automation Events Overview](ui-automation-events-overview.md)」をご覧ください。  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] イベント|Support|ノート|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|必要|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> プロパティ変更イベント。|必要|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> プロパティ変更イベント。|必要|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> プロパティ変更イベント。|必要|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|状況に依存|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|必要|None|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty> プロパティ変更イベント。|状況に依存|None|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> プロパティ変更イベント。|状況に依存|コントロールで Scroll パターンをサポートする場合は、このイベントをサポートする必要があります。|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> プロパティ変更イベント。|状況に依存|コントロールで Scroll パターンをサポートする場合は、このイベントをサポートする必要があります。|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> プロパティ変更イベント。|状況に依存|コントロールで Scroll パターンをサポートする場合は、このイベントをサポートする必要があります。|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> プロパティ変更イベント。|状況に依存|コントロールで Scroll パターンをサポートする場合は、このイベントをサポートする必要があります。|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> プロパティ変更イベント。|状況に依存|コントロールで Scroll パターンをサポートする場合は、このイベントをサポートする必要があります。|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> プロパティ変更イベント。|状況に依存|コントロールで Scroll パターンをサポートする場合は、このイベントをサポートする必要があります。|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|必要|None|  
  
## <a name="date-grid-control-type-example"></a>データ グリッド コントロール型の例  
 次の図に、DataGrid コントロール型を実装するリスト ビュー コントロールを示します。  
  
 ![Graphic of a List View control with two data items](./media/uiauto-data-grid-detailed.GIF "uiauto_data_grid_detailed")  
  
 以下には、リスト ビュー コントロールに関連する [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリーのコントロール ビューとコンテンツ ビューが表示されています。 オートメーションの各要素のコントロール パターンが、かっこ内に示されています。  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリー - コントロール ビュー|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリー - コンテンツ ビュー|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|<ul><li>DataGrid (Table、Grid、Selection)</li><li>Header<br /><br /> <ul><li>HeaderItem "Name" (Invoke)</li><li>HeaderItem "Date Modified" (Invoke)</li><li>HeaderItem "Size" (Invoke)</li></ul></li><li>Group "Contoso" (TableItem, GridItem, SelectionItem, Table*, Grid\*)<br /><br /> <ul><li>DataItem "Accounts Receivable.doc" (SelectionItem, Invoke, TableItem\*, GridItem\*)</li><li>DataItem "Accounts Payable.doc" (SelectionItem, Invoke, TableItem\*, GridItem\*)</li></ul></li></ul>|<ul><li>DataGrid (Table、Grid、Selection)</li><li>Group "Contoso" (TableItem, GridItem, SelectionItem, Table*, Grid\*)<br /><br /> <ul><li>DataItem "Accounts Receivable.doc" (SelectionItem, Invoke, TableItem\*, GridItem\*)</li><li>DataItem "Accounts Payable.doc" (SelectionItem, Invoke, TableItem\*, GridItem\*)</li></ul></li></ul>|  
  
 \* The previous example shows a DataGrid that contains multiple levels of controls. グループ ("Contoso") のコントロールには、2 つのDataItem コントロール ("Accounts Receivable.doc" および "Accounts Payable.doc") が含まれています。 DataGrid と GridItem ペアは、他のレベルのペアから独立しています。 グループの下にある DataItem コントロールは、ListItem コントロール型として公開することもでき、単純なデータ要素としてではなく、選択可能オブジェクトとして、より明確に提示することができます。 この例では、グループ化されたデータ項目のサブ要素は含まれません。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Automation.ControlType.DataGrid>
- [UI オートメーション コントロール型の概要](ui-automation-control-types-overview.md)
- [UI オートメーションの概要](ui-automation-overview.md)
