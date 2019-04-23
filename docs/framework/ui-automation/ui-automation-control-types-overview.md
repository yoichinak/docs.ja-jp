---
title: UI オートメーション コントロール型の概要
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control types
- control types, UI Automation
ms.assetid: 75159ef8-bd43-4d13-acb7-1f1fe9253160
ms.openlocfilehash: e9cbff2ec6496cabe827e075b737a8c6f16fee93
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59147720"
---
# <a name="ui-automation-control-types-overview"></a>UI オートメーション コントロール型の概要
> [!NOTE]
>  このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 に関する最新情報については[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]を参照してください[Windows Automation API:UI オートメーション](https://go.microsoft.com/fwlink/?LinkID=156746)します。  
  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] コントロール型は、コンボ ボックスやボタンなど、特定の要素が表すコントロールの種類を示すのに使用できる既知の識別子です。  
  
 既知の識別子を使用すると、支援テクノロジ デバイスで、 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] で使用できるコントロール型およびコントロールとの対話方法を簡単に確認できるようになります。  
  
<a name="UI_Automation_Control_Type_Requisites"></a>   
## <a name="ui-automation-control-type-requisites"></a>UI オートメーション コントロール型の要件  
 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] コントロール型は、プロバイダーが満たす必要のある一連の条件を提供します。 これらの条件が満たされると、コントロールは特定のコントロール型名を使用できます。 コントロール型にはそれぞれ、次のような条件があります。  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] コントロール パターン - サポートする必要があるコントロール パター、省略可能なコントロール パターン、およびコントロールでサポートする必要がないコントロール パターン。  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] プロパティ値 - サポートされるプロパティ値。  
  
-   [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリー構造 - コントロールに必要な [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリー構造。  
  
 コントロールが特定のコントロール型の条件を満たす場合、 <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> プロパティの値がそのコントロール型を示します。  
  
<a name="Current_UI_Automation_Control_Types"></a>   
## <a name="current-ui-automation-control-types"></a>現在の UI オートメーション コントロール型  
 現在の [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] コントロール型の一覧を次に示します。  
  
-   [UI オートメーションによる Button コントロール型のサポート](../../../docs/framework/ui-automation/ui-automation-support-for-the-button-control-type.md)  
  
-   [UI オートメーションによる Calendar コントロール型のサポート](../../../docs/framework/ui-automation/ui-automation-support-for-the-calendar-control-type.md)  
  
-   [UI オートメーションによる CheckBox コントロール型のサポート](../../../docs/framework/ui-automation/ui-automation-support-for-the-checkbox-control-type.md)  
  
-   [UI オートメーションによる ComboBox コントロール型のサポート](../../../docs/framework/ui-automation/ui-automation-support-for-the-combobox-control-type.md)  
  
-   [UI オートメーションによる DataGrid コントロール型のサポート](../../../docs/framework/ui-automation/ui-automation-support-for-the-datagrid-control-type.md)  
  
-   [UI オートメーションによる DataItem コントロール型のサポート](../../../docs/framework/ui-automation/ui-automation-support-for-the-dataitem-control-type.md)  
  
-   [UI オートメーションによる Document コントロール型のサポート](../../../docs/framework/ui-automation/ui-automation-support-for-the-document-control-type.md)  
  
-   [UI オートメーションによる Edit コントロール型のサポート](../../../docs/framework/ui-automation/ui-automation-support-for-the-edit-control-type.md)  
  
-   [UI オートメーションによる Group コントロール型のサポート](../../../docs/framework/ui-automation/ui-automation-support-for-the-group-control-type.md)  
  
-   [UI オートメーションによる Header コントロール型のサポート](../../../docs/framework/ui-automation/ui-automation-support-for-the-header-control-type.md)  
  
-   [UI オートメーションによる HeaderItem コントロール型のサポート](../../../docs/framework/ui-automation/ui-automation-support-for-the-headeritem-control-type.md)  
  
-   [UI オートメーションによる Hyperlink コントロール型のサポート](../../../docs/framework/ui-automation/ui-automation-support-for-the-hyperlink-control-type.md)  
  
-   [UI オートメーションによる Image コントロール型のサポート](../../../docs/framework/ui-automation/ui-automation-support-for-the-image-control-type.md)  
  
-   [UI オートメーションによる List コントロール型のサポート](../../../docs/framework/ui-automation/ui-automation-support-for-the-list-control-type.md)  
  
-   [UI オートメーションによる ListItem コントロール型のサポート](../../../docs/framework/ui-automation/ui-automation-support-for-the-listitem-control-type.md)  
  
-   [UI オートメーションによる Menu コントロール型のサポート](../../../docs/framework/ui-automation/ui-automation-support-for-the-menu-control-type.md)  
  
-   [UI オートメーションによる MenuBar コントロール型のサポート](../../../docs/framework/ui-automation/ui-automation-support-for-the-menubar-control-type.md)  
  
-   [UI オートメーションによる MenuItem コントロール型のサポート](../../../docs/framework/ui-automation/ui-automation-support-for-the-menuitem-control-type.md)  
  
-   [UI オートメーションによる Pane コントロール型のサポート](../../../docs/framework/ui-automation/ui-automation-support-for-the-pane-control-type.md)  
  
-   [UI オートメーションによる ProgressBar コントロール型のサポート](../../../docs/framework/ui-automation/ui-automation-support-for-the-progressbar-control-type.md)  
  
-   [UI オートメーションによる RadioButton コントロール型のサポート](../../../docs/framework/ui-automation/ui-automation-support-for-the-radiobutton-control-type.md)  
  
-   [UI オートメーションによる ScrollBar コントロール型のサポート](../../../docs/framework/ui-automation/ui-automation-support-for-the-scrollbar-control-type.md)  
  
-   [UI オートメーションによる Separator コントロール型のサポート](../../../docs/framework/ui-automation/ui-automation-support-for-the-separator-control-type.md)  
  
-   [UI オートメーションによる Slider コントロール型のサポート](../../../docs/framework/ui-automation/ui-automation-support-for-the-slider-control-type.md)  
  
-   [UI オートメーションによる Spinner コントロール型のサポート](../../../docs/framework/ui-automation/ui-automation-support-for-the-spinner-control-type.md)  
  
-   [UI オートメーションによる SplitButton コントロール型のサポート](../../../docs/framework/ui-automation/ui-automation-support-for-the-splitbutton-control-type.md)  
  
-   [UI オートメーションによる StatusBar コントロール型のサポート](../../../docs/framework/ui-automation/ui-automation-support-for-the-statusbar-control-type.md)  
  
-   [UI オートメーションによる Tab コントロール型のサポート](../../../docs/framework/ui-automation/ui-automation-support-for-the-tab-control-type.md)  
  
-   [UI オートメーションでの TabItem コントロール型のサポート](../../../docs/framework/ui-automation/ui-automation-support-for-the-tabitem-control-type.md)  
  
-   [UI オートメーションによる Table コントロール型のサポート](../../../docs/framework/ui-automation/ui-automation-support-for-the-table-control-type.md)  
  
-   [UI オートメーションによる Text コントロール型のサポート](../../../docs/framework/ui-automation/ui-automation-support-for-the-text-control-type.md)  
  
-   [UI オートメーションによる Thumb コントロール型のサポート](../../../docs/framework/ui-automation/ui-automation-support-for-the-thumb-control-type.md)  
  
-   [UI オートメーションによる TitleBar コントロール型のサポート](../../../docs/framework/ui-automation/ui-automation-support-for-the-titlebar-control-type.md)  
  
-   [UI オートメーションによる ToolBar コントロール型のサポート](../../../docs/framework/ui-automation/ui-automation-support-for-the-toolbar-control-type.md)  
  
-   [UI オートメーションによる ToolTip コントロール型のサポート](../../../docs/framework/ui-automation/ui-automation-support-for-the-tooltip-control-type.md)  
  
-   [UI オートメーションによる Tree コントロール型のサポート](../../../docs/framework/ui-automation/ui-automation-support-for-the-tree-control-type.md)  
  
-   [UI オートメーションによる TreeItem コントロール型のサポート](../../../docs/framework/ui-automation/ui-automation-support-for-the-treeitem-control-type.md)  
  
-   [UI オートメーションによる Window コントロール型のサポート](../../../docs/framework/ui-automation/ui-automation-support-for-the-window-control-type.md)  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Automation.ControlType>
