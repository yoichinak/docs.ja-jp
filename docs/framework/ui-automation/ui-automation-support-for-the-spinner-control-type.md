---
title: UI オートメーションによる Spinner コントロール型のサポート
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Spinner control type
- Spinner control type
- control types, Spinner
ms.assetid: 3a29d185-65d8-42e3-bcc3-7f43e96f40c5
ms.openlocfilehash: 43e892f681669cd80c83b23dc4e16c81026f1d7e
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2019
ms.locfileid: "57676100"
---
# <a name="ui-automation-support-for-the-spinner-control-type"></a>UI オートメーションによる Spinner コントロール型のサポート
> [!NOTE]
>  このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 に関する最新情報については[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]を参照してください[Windows Automation API:UI オートメーション](https://go.microsoft.com/fwlink/?LinkID=156746)します。  
  
 このトピックでは、Spinner コントロール型の [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] サポートについて説明します。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]でのコントロール型とは、コントロールが <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> プロパティを使用するために満たす必要がある一連の条件のことです。 これらの条件には、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリー構造、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] のプロパティ値、およびコントロール パターンに関する特定のガイドラインが含まれます。  
  
 スピン ボタン コントロールは、ある範囲の項目や数字から選択するために使用します。  
  
 以降のセクションでは、Spinner コントロール型に必要な [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリー構造、プロパティ、コントロール パターン、およびイベントを定義します。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] の要件は、 [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]、 [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]、または [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]のいずれの場合でも、すべてのスピン ボタン コントロールに適用されます。  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>必須の UI オートメーション ツリー構造  
 次の表に、Range Value、Value、および Selection の各コントロール パターンをサポートするスピン ボタン コントロールに関連する [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリーのコントロール ビューとコンテンツ ビューを示し、各ビューに格納できるものについて説明します。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ツリーの詳細については、[UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)をご覧ください。  
  
 **Range Value コントロール パターンまたは Value コントロール パターン**  
  
|コントロール ビュー|コンテンツ ビュー|  
|------------------|------------------|  
|Spinner<br /><br /> -(0 または 1) を編集します。<br />ボタン (2)|Spinner|  
  
 **Selection コントロール パターン**  
  
|コントロール ビュー|コンテンツ ビュー|  
|------------------|------------------|  
|Spinner<br /><br /> -(0 または 1) を編集します。<br />ボタン (2)<br />リスト項目 (0 以上)|Spinner<br /><br /> -ListItem (0 以上)|  
  
 自動テスト ツールによってコントロール ビュー サブツリーの 2 つのボタンを識別できることを確実に割り当てる、`SmallIncrement`または`SmallDecrement``AutomationId`に応じて。 実装によっては、関連付けられたエディット コントロールが Spinner コントロールのピアである場合があります。  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>必須の UI オートメーション プロパティ  
 次の表に、スピン ボタン コントロールに特に関連する値または定義を持つ [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] プロパティを示します。 詳細については[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]プロパティを参照してください[クライアントの UI オートメーション プロパティ](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)します。  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] プロパティ|[値]|メモ|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|「ノート」をご覧ください。|このプロパティの値は、アプリケーションのすべてのコントロールで一意である必要があります。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|「ノート」をご覧ください。|コントロール全体を格納する最も外側の四角形。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|「ノート」をご覧ください。|スピン ボタン コントロールのクリック可能なポイントは、コントロールの編集部分にフォーカスを設定します。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|「ノート」をご覧ください。|コントロールがキーボード フォーカスを受け取ることができる場合は、このプロパティをサポートする必要があります。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|「ノート」をご覧ください。|スピン ボタン コントロールは、通常、静的テキスト ラベルからその名前を取得します。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|ノートを参照してください。|スピン ボタン コントロールには静的なテキスト ラベルがあります。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Spinner|この値は、すべての UI フレームワークで同じです。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"スピン ボタン"|Spinner コントロール型に対応する、ローカライズされた文字列。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|スピン ボタン コントロールは、常にコンテンツである必要があります。|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Spinner コントロールは、常にコントロールである必要があります。|  
  
<a name="Required_UI_Automation_Control_Patterns_and_Properties"></a>   
## <a name="required-ui-automation-control-patterns-and-properties"></a>必須の UI オートメーション コントロール パターンおよびプロパティ  
 次の表に、スピン ボタン コントロールでサポートする必要がある [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] コントロール パターンを示します。 コントロール パターンについて詳しくは、「 [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)」をご覧ください。  
  
|コントロール パターン/パターン プロパティ|サポート/値|メモ|  
|---------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|状況に依存|選択する項目のリストを持つスピン ボタン コントロールは、このパターンをサポートする必要があります。|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|False|スピン ボタン コントロールは、常に単一選択コンテナーです。|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|状況に依存|数値の範囲を対象にするスピン ボタン コントロールは、このパターンをサポートできます。|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|状況に依存|個別のオプション セットまたは数値のセットを対象にするスピン ボタン コントロールは、このパターンをサポートできます。|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>必須の UI オートメーション イベント  
 次の表に、すべてのスピン ボタン コントロールでサポートする必要がある [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] イベントを示します。 イベントについて詳しくは、「 [UI Automation Events Overview](../../../docs/framework/ui-automation/ui-automation-events-overview.md)」をご覧ください。  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] イベント|サポート|メモ|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|状況に依存|なし|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> プロパティ変更イベント。|必須|なし|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> プロパティ変更イベント。|必須|なし|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> プロパティ変更イベント。|必須|なし|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> プロパティ変更イベント。|状況に依存|なし|  
|<xref:System.Windows.Automation.RangeValuePatternIdentifiers.ValueProperty> プロパティ変更イベント。|状況に依存|なし|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|必須|なし|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|必須|なし|  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Automation.ControlType.Spinner>
- [UI オートメーション コントロール型の概要](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)
- [UI オートメーションの概要](../../../docs/framework/ui-automation/ui-automation-overview.md)
