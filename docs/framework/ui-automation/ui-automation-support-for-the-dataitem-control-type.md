---
title: UI オートメーションによる DataItem コントロール型のサポート
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Data Item control type
- Data Item control type
- control types, Data Item
ms.assetid: 181708fd-2595-4c43-9abd-75811627d64c
ms.openlocfilehash: ebc5f9a5b50766b9a49a9772469f8ae731f3aa4c
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679399"
---
# <a name="ui-automation-support-for-the-dataitem-control-type"></a>UI オートメーションによる DataItem コントロール型のサポート
> [!NOTE]
>  このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 に関する最新情報については[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]を参照してください[Windows Automation API:UI オートメーション](https://go.microsoft.com/fwlink/?LinkID=156746)します。  
  
 このトピックでは、DataItem コントロール型に対する [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] のサポートについて説明します。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] でのコントロール型とは、コントロールが <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> プロパティを使用するために満たす必要がある一連の条件のことです。 これらの条件には、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリー構造、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] のプロパティ値、およびコントロール パターンに関する特定のガイドラインが含まれます。  
  
 連絡先リストのエントリは、データ項目コントロールの一例です。 データ項目コントロールには、エンド ユーザーに必要な情報が格納されます。 これは、より豊富な情報が格納されるため、単純なリスト項目よりも複雑になります。  
  
 以下の各セクションで、DataItem コントロール型に必要な [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリー構造、プロパティ、コントロール パターン、およびイベントを定義します。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] の要件は、 [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]、 [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]、 [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]のいずれの場合も、すべてのデータ項目コントロールに適用されます。  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>必須の UI オートメーション ツリー構造  
 次の表に、データ項目コントロールに関連する [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリーのコントロール ビューとコンテンツ ビューを示し、それぞれのビューに含めることができる内容について説明します。 詳細については、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ツリーを参照してください[UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)します。  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリー - コントロール ビュー|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリー - コンテンツ ビュー|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|DataItem<br /><br /> -異なります (0 以上階層で構造化することができます)。|DataItem<br /><br /> -異なります (0 以上階層で構造化することができます)。|  
  
 データ グリッド内のデータ項目要素は、さまざまなオブジェクトをホストできます。たとえば、別のレイヤーのデータ項目や、テキスト、イメージ、エディット コントロールなどの特定のグリッド要素をホストできます。 データ項目要素に特定のオブジェクトの役割がある場合は、その要素を特定のコントロール型 (たとえば、グリッド内の選択可能なデータ項目の場合は ListItem コントロール型など) として公開する必要があります。  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>必須の UI オートメーション プロパティ  
 次の表に、データ項目コントロールに特に関連する値または定義を持つプロパティを示します。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]プロパティの詳細については[クライアントの UI オートメーション プロパティ](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)をご覧ください。  
  
|プロパティ|[値]|メモ|  
|--------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|「ノート」をご覧ください。|このプロパティの値は、アプリケーションのすべてのコントロールで一意である必要があります。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|「ノート」をご覧ください。|コントロール全体を格納する最も外側の四角形。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|「ノート」をご覧ください。|四角形領域が存在する場合にサポートされます。 四角形領域内にクリック不可能な点が存在し、特別なヒット テストを実行する場合は、オーバーライドしてクリック可能な点を提供します。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|DataItem|この値は、すべての UI フレームワークで同じです。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|データ項目コントロールは、常にコンテンツである必要があります。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|データ項目コントロールは、常にコントロールである必要があります。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|「ノート」をご覧ください。|コントロールがキーボード フォーカスを受け取ることができる場合は、このプロパティをサポートする必要があります。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty>|「ノート」をご覧ください。|コントロールに動的に更新される状態が含まれる場合、要素の状態が変化したときに支援技術が更新を受け取ることができるように、このプロパティをサポートする必要があります。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemTypeProperty>|「ノート」をご覧ください。|これは、項目が表す基になるオブジェクトをエンド ユーザーに伝達する文字列値です。 例として "メディア ファイル" や "連絡先" があります。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|データ項目コントロールに静的なテキスト ラベルはありません。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"data item"|DataItem コントロール型に対応するローカライズされた文字列。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|「ノート」をご覧ください。|データ項目コントロールには、主要なテキスト要素が常に含まれています。この要素は、その項目に対してユーザーが最も意味的な識別子として連想するものに関連しています。|  
  
<a name="_Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>必須の UI オートメーション コントロール パターン  
 次の表に、すべてのデータ項目コントロールでサポートされなければならない [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] コントロール パターンを示します。 コントロール パターンについて詳しくは、「 [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)」をご覧ください。  
  
|コントロール パターン|サポート|メモ|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|状況に依存|データ項目を展開したり折りたたんだりして、情報の表示/非表示を切り替える場合、Expand Collapse パターンをサポートする必要があります。|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider>|状況に依存|データ項目の集合が、空間的に項目間を移動できるコンテナー内にある場合、データ項目は Grid Item パターンをサポートします。|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|状況に依存|画面に収まる項目数を超える項目がデータ コンテナーにある場合、すべてのデータ項目は Scroll Item パターンを使用して、スクロールして表示する機能をサポートします。|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|[はい]|すべてのデータ項目は、項目が選択されたタイミングを示す Selection Item パターンをサポートする必要があります。|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider>|状況に依存|データ項目が Data Grid コントロール型の中に含まれている場合、このパターンをサポートします。|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|状況に依存|データ項目に循環する状態が含まれる場合。|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|状況に依存|データ項目の主要なテキストが編集可能な場合は、Value パターンをサポートする必要があります。|  
  
<a name="Working_with_Data_Items_in_Large_Lists"></a>   
## <a name="working-with-data-items-in-large-lists"></a>大きなリストでのデータ項目の操作  
 大きなリストでは、多くの場合、パフォーマンスを向上させるため、 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] フレームワーク内でデータが仮想化されます。 そのため、UI オートメーション クライアントは、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] クエリ機能を使用して、他の項目コンテナーと同じように完全なツリーからコンテンツを取得することができません。 クライアントは、データ項目の完全に揃った情報にアクセスする前に、項目をスクロールして表示する (またはコントロールを展開して重要なすべてのオプションを表示する) 必要があります。  
  
 データ項目の `SetFocus` 要素で [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] を呼び出すときに、 [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)] の場合は正常に値を返し、データ項目サブツリー内でフォーカスを編集に設定します。  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>必須の UI オートメーション イベント  
 次の表に、すべてのデータ項目コントロールでサポートされなければならない [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] イベントを示します。 イベントについて詳しくは、「 [UI Automation Events Overview](../../../docs/framework/ui-automation/ui-automation-events-overview.md)」をご覧ください。  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] イベント|サポート|メモ|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|必要|なし|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> プロパティ変更イベント。|必須|なし|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> プロパティ変更イベント。|必須|なし|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> プロパティ変更イベント。|必須|なし|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> プロパティ変更イベント。|必須|なし|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|必須|なし|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|状況に依存|なし|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty> プロパティ変更イベント。|状況に依存|なし|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|必須|なし|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|必須|なし|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|必須|なし|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty> プロパティ変更イベント。|状況に依存|なし|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> プロパティ変更イベント。|状況に依存|なし|  
  
<a name="Data_Item_Control_Type_Example"></a>   
## <a name="dataitem-control-type-example"></a>DataItem コントロール型の例  
 次の図は、列の豊富な情報をサポートするリスト ビュー コントロール内の DataItem コントロール型を示しています。  
  
 ![2 つのデータ項目を含むリスト ビュー コントロールのグラフィック](../../../docs/framework/ui-automation/media/uiauto-data-grid-detailed.GIF "uiauto_data_grid_detailed")  
  
 以下には、データ項目コントロールに関連する [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリーのコントロール ビューとコンテンツ ビューが表示されています。 オートメーションの各要素のコントロール パターンが、かっこ内に示されています。 グループ "Contoso" は、データ グリッド ホスト コントロールのグリッドの一部でもあります。  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリー - コントロール ビュー|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリー - コンテンツ ビュー|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|-グループ"Contoso"(テーブル、グリッド)<br />-DataItem"Accounts Receivable.doc"(TableItem、GridItem、SelectionItem を呼び出す)<br />-"Accounts Receivable.doc"のイメージします。<br />-"Name"(TableItem、GridItem、値"Accounts Receivable.doc") を編集します。<br />編集「更新日」(TableItem、GridItem、値"2006 年 8 月 25 日午後 3時 29分")<br />-   Edit "Size" (GridItem, TableItem, Value "11.0 KB)<br />-   DataItem "Accounts Payable.doc" (TableItem, GridItem, SelectionItem, Invoke)<br />-   ...|-グループ"Contoso"(テーブル、グリッド)<br />-DataItem"Accounts Receivable.doc"(TableItem、GridItem、SelectionItem を呼び出す)<br />-"Accounts Receivable.doc"のイメージします。<br />-"Name"(TableItem、GridItem、値"Accounts Receivable.doc") を編集します。<br />編集「更新日」(TableItem、GridItem、値"2006 年 8 月 25 日午後 3時 29分")<br />-   Edit "Size" (GridItem, TableItem, Value "11.0 KB)<br />-   DataItem "Accounts Payable.doc" (TableItem, GridItem, SelectionItem, Invoke)<br />-   …|  
  
 グリッドが選択可能な項目のリストを表している場合、DataItem コントロール型の代わりに、ListItem コントロール型で対応する UI 要素を公開できます。 前の例では、グループ ("Contoso") の下の DataItem 要素 ("Accounts Receivable.doc" および "Accounts Payable.doc") を ListItem コントロール型として公開することで、その型が既に SelectionItem コントロール パターンをサポートしているため、それらの要素を向上させることができます。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Automation.ControlType.DataItem>
- [UI オートメーション コントロール型の概要](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)
- [UI オートメーションの概要](../../../docs/framework/ui-automation/ui-automation-overview.md)
