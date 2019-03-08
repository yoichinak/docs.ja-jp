---
title: UI オートメーションによる Menu コントロール型のサポート
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Menu
- UI Automation, Menu control type
- Menu control type
ms.assetid: 016323cb-f800-4938-b77b-2eb25d646090
ms.openlocfilehash: 9d711aeb2f02bc5630fd5a773b80cccfb661dedb
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2019
ms.locfileid: "57676188"
---
# <a name="ui-automation-support-for-the-menu-control-type"></a>UI オートメーションによる Menu コントロール型のサポート
> [!NOTE]
>  このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 に関する最新情報については[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]を参照してください[Windows Automation API:UI オートメーション](https://go.microsoft.com/fwlink/?LinkID=156746)します。  
  
 このトピックでは、Menu コントロール型の [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] サポートについて説明します。 このコントロールの [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] ツリー構造を説明し、特定のコントロール シナリオでのプロパティとコントロール パターンを示します。  
  
 メニュー コントロールを使用すると、コマンドおよびイベント ハンドラーに関連付けられている要素を階層に編成できます。 一般的な [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] アプリケーションでは、メニュー バーに複数のメニュー ボタン ( **[ファイル]**、 **[編集]**、 **[ウィンドウ]** など) が含まれ、各メニュー ボタンがメニューを表示します。 メニューには、メニュー項目 ( **[新規]**、 **[開く]**、 **[閉じる]** など) のコレクションが含まれていて、メニュー項目を展開して追加のメニュー項目を表示したり、クリックして特定の操作を実行したりできます。  
  
 以降のセクションで、Menu コントロール型に必要な [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリー構造、プロパティ、コントロール パターン、およびイベントを定義します。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 要件は、 [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]、 [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]、または [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]のいずれの場合も、すべてのリスト コントロールに適用されます。  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>必須の UI オートメーション ツリー構造  
 次の表に、メニュー コントロールに関連する [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリーのコントロール ビューとコンテンツ ビューを示し、それぞれのビューに含めることができる内容について説明します。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ツリーの詳細については、[UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)をご覧ください。  
  
|コントロール ビュー|コンテンツ ビュー|  
|------------------|------------------|  
|メニュー<br /><br /> -MenuItem (1 以上)|該当なし (メニュー コントロールが、メニュー項目でないオブジェクトの親であるコンテキスト メニューに相当する場合を除く)<br /><br /> -MenuItem (1 以上)|  
  
 メニュー コントロールは、コントロール ビューと [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリーのコンテンツ ビューに常に表示されます。 Menu コントロール型は、その情報が参照しているコントロールの下に表示されます。 UI オートメーション クライアントは、メニュー コントロールによって伝えられる情報を常に取得できるよう、 `MenuOpenedEvent` をリッスンする必要があります。 コンテキスト メニュー コントロールは、特殊なケースです。 これらのコントロールは、デスクトップの子として表示されます。  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>必須の UI オートメーション プロパティ  
 次の表に、Menu コントロール型に特に関連する値または定義を持つ [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] プロパティを示します。 詳細については[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]プロパティを参照してください[クライアントの UI オートメーション プロパティ](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)します。  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] プロパティ|[値]|メモ|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|サポート非対象|メニュー コントロールでは、Name プロパティを設定する必要はありません。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|一般的なメニュー コントロールには、ラベルは不要です。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|メニュー|この値は、すべての UI フレームワークで同じです。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|False|メニュー コントロールは、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリーのコンテンツ ビューに組み込まれません。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|メニュー コントロールは、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリーのコントロール ビューに常に組み込まれます。|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>必須の UI オートメーション コントロール パターン  
 Menu コントロール型に必要なコントロール パターンはありません。  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>必須の UI オートメーション イベント  
 メニュー コントロールは、画面に表示された場合に `MenuOpenedEvent` を生成する必要があります。 `MenuOpenedEvent` にはコントロールのテキストが含まれます。 メニューが画面から非表示になった場合には、 `MenuClosedEvent` が生成されなければなりません。  
  
 次の表に、すべてのメニュー コントロールでサポートされなければならない [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] イベントを示します。 イベントについて詳しくは、「 [UI Automation Events Overview](../../../docs/framework/ui-automation/ui-automation-events-overview.md)」をご覧ください。  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] イベント|サポート/値|メモ|  
|---------------------------------------------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.MenuOpenedEvent>|必要|なし|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.MenuClosedEvent>|必須|なし|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> プロパティ変更イベント。|必須|なし|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> プロパティ変更イベント。|必須|なし|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> プロパティ変更イベント。|必須|なし|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|必須|なし|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|必須|なし|  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Automation.ControlType.Menu>
- [UI Automation コントロール パターンの概要](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [UI オートメーション コントロール型の概要](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)
- [UI オートメーションの概要](../../../docs/framework/ui-automation/ui-automation-overview.md)
