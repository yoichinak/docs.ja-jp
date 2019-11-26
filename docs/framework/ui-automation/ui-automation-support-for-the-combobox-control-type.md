---
title: UI オートメーションによる ComboBox コントロール型のサポート
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Combo Box
- UI Automation, Combo Box control type
- ComboBox controls
ms.assetid: bb321126-4770-41da-983a-67b7b89d45dd
ms.openlocfilehash: eea5068fa5e5e9401a8197c1be9e14f8064b1aa4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441090"
---
# <a name="ui-automation-support-for-the-combobox-control-type"></a>UI オートメーションによる ComboBox コントロール型のサポート
> [!NOTE]
> このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI Automation (Windows のオートメーション API: UI オートメーション)](/windows/win32/winauto/entry-uiauto-win32)」を参照してください。  
  
 このトピックでは、ComboBox コントロール型の [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] サポートについて説明します。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]でのコントロール型とは、コントロールが <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> プロパティを使用するために満たす必要がある一連の条件のことです。 条件には、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリー構造、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] プロパティの値、コントロール パターン、および [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] イベントに関する特定のガイドラインが含まれます。  
  
 コンボ ボックスは、スタティック コントロールまたは編集コントロールが組み合わせられたリスト ボックスです。コンボ ボックスのリスト ボックスの部分には、現在選択されている項目が表示されます。 コントロールのリスト ボックスの部分は常に表示されるか、ユーザーがコントロールの横にあるドロップダウン矢印 (プッシュ ボタン) を選択したときにのみ表示されます。 選択フィールドが編集コントロールである場合、ユーザーは、リスト ボックスに含まれていない情報を入力できます。そうでない場合、ユーザーはリスト ボックスに含まれる項目を選択することしかできません。  
  
 以降のセクションで、ComboBox コントロール型に必要な [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリー構造、プロパティ、コントロール パターン、およびイベントを定義します。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 要件は、 [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]、 [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]、または [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]であるかに関わらず、すべてのコンボ ボックス コントロールに適用されます。  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>必須の UI オートメーション ツリー構造  
 次の表に、コンボ ボックス コントロールに関連する [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリーのコントロール ビューとコンテンツ ビューを示し、それぞれのビューに含めることができる内容について説明します。 For more information about the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree, see [UI Automation Tree Overview](ui-automation-tree-overview.md).  
  
|コントロール ビュー|コンテンツ ビュー|  
|------------------|------------------|  
|ComboBox<br /><br /> -   Edit (0 or 1)<br />-   List (1)<br />-   List Item (child of List; 0 to many)<br />-   Button (1)|ComboBox<br /><br /> -   List Item (0 to many)|  
  
 コンボ ボックスのコントロール ビュー内の編集コントロールは、[実行] ダイアログ ボックスの場合と同じく、コンボ ボックスが編集可能で任意の入力値を受け取る場合にのみ必要です。  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>必須の UI オートメーション プロパティ  
 次の表に、コンボ ボックス コントロールに特に関連する値または定義を持つ [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] プロパティを示します。 For more information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] properties, see [UI Automation Properties for Clients](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] プロパティ|[値]|ノート|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|「ノート」をご覧ください。|このプロパティの値は、アプリケーション内のすべてのコントロールで一意である必要があります。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|「ノート」をご覧ください。|コントロール全体を格納する最も外側の四角形。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|「ノート」をご覧ください。|四角形領域が存在する場合にサポートされます。 四角形領域内にクリック不可能な点が存在し、特別なヒット テストを実行する場合は、オーバーライドしてクリック可能な点を提供します。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|ComboBox|この値は、すべての [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] フレームワークで同じです。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|「ノート」をご覧ください。|コンボ ボックス コントロールのヘルプ テキストで、コンボ ボックスからオプションを選択するようにユーザーに求める理由を説明する必要があります。 テキストは、ツールヒントに表示する情報に似ています。 たとえば、「項目を選択してモニターのディスプレイ解像度を設定してください」などです。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|コンボ ボックス コントロールは、常に [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリーのコンテンツ ビューに組み込まれます。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|コンボ ボックス コントロールは、常に [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリーのコントロール ビューに組み込まれます。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|True|コンボ ボックス コントロールは、選択コンテナーの項目のセットを公開します。 コンボ ボックス コントロールは、キーボード フォーカスを受け取ることができますが、UI オートメーション クライアントがコンボ ボックスにフォーカスを設定すると、コンボ ボックス サブツリーの項目がフォーカスを受け取る場合があります。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|「ノート」をご覧ください。|コンボ ボックス コントロールには、通常、このプロパティが参照する静的なテキスト ラベルがあります。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|「コンボ ボックス」|ComboBox コントロール型に対応する、ローカライズされた文字列。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|「ノート」をご覧ください。|コンボ ボックス コントロールの名前は、通常、静的なテキスト コントロールから取得されます。|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>必須の UI オートメーション コントロール パターン  
 次の表に、すべてのコンボ ボックス コントロールでサポートされなければならない [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] コントロール パターンを示します。 コントロール パターンの詳細については、「 [UI Automation Control Patterns Overview](ui-automation-control-patterns-overview.md)」を参照してください。  
  
|コントロール パターン|Support|ノート|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|[はい]|コンボ ボックス コントロールがコンボ ボックスであるためには、必ず、ドロップダウン ボタンがなければなりません。|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|[はい]|コンボ ボックスで現在選択されている項目を表示します。 このサポートは、コンボ ボックスの下にあるリスト ボックスに委任されます。|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|状況に依存|コンボ ボックスが任意のテキスト値を受け取ることができる場合、Value パターンをサポートする必要があります。 このパターンでは、コンボ ボックスの文字列の内容をプログラムで設定することができます。 Value パターンがサポートされていない場合、ユーザーはコンボ ボックスのサブツリー内のリスト項目から項目を選択する必要があります。|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Never|スクロール パターンがコンボ ボックスで直接サポートされることはありません。 コンボ ボックスに含まれるリスト ボックスをスクロールできる場合は、このパターンがサポートされます。 リスト ボックスが画面に表示されている場合にのみサポートできます。|  
  
<a name="Required_Events"></a>   
## <a name="required-events"></a>必須イベント  
 次の表に、すべてのコンボ ボックス コントロールでサポートされなければならない [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] イベントを示します。 イベントについて詳しくは、「 [UI Automation Events Overview](ui-automation-events-overview.md)」をご覧ください。  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] イベント|Support|ノート|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|必要|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> プロパティ変更イベント。|必要|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> プロパティ変更イベント。|必要|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> プロパティ変更イベント。|必要|None|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|必要|None|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty> プロパティ変更イベント。|必要|None|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> プロパティ変更イベント。|状況に依存|コントロールが Value パターンをサポートする場合は、このイベントをサポートする必要があります。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Automation.ControlType.ComboBox>
- [UI オートメーション コントロール型の概要](ui-automation-control-types-overview.md)
- [UI オートメーションの概要](ui-automation-overview.md)
