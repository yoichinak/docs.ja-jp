---
title: UI オートメーションと Microsoft Active Accessibility
ms.date: 03/30/2017
helpviewer_keywords:
- Active Accessibility
- UI Automation, Active Accessibility compared to
- UI Automation, Microsoft Active Accessibility
- Active Accessibility, UI Automation compared to
ms.assetid: 87bee662-0a3e-4232-a421-20e7a5968321
ms.openlocfilehash: 9a84c344ffabdaaa9d0aed68b05b7a4449776789
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179978"
---
# <a name="ui-automation-and-microsoft-active-accessibility"></a>UI オートメーションと Microsoft Active Accessibility
> [!NOTE]
> このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。  
  
 Microsoft アクティブ アクセシビリティは、アプリケーションをアクセシビリティ対応にするための以前のソリューションでした。 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]は、Microsoft Windows の新しいアクセシビリティ モデルであり、支援技術製品と自動テスト ツールのニーズに対応することを目的としています。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]では、アクティブなアクセシビリティよりも多くの改善が行えます。  
  
 このトピックでは、これらの機能と[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]アクティブ アクセシビリティの主な機能について説明します。  
  
<a name="Programming_Languages_compare"></a>
## <a name="programming-languages"></a>プログラミング言語  
<アクティブ なユーザー補助は、デュアル インターフェイスをサポートするコンポーネント オブジェクト モデル (COM) に基づいているため、C/C++、Microsoft Visual Basic 6.0、およびスクリプト言語でプログラムできます。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)](標準コントロール用のクライアント側プロバイダー ライブラリを含む) はマネージ コードで記述され、UI オートメーション クライアント アプリケーションは C# または Visual Basic .NET を使用して最も簡単にプログラムできます。 インターフェイスを実装する UI オートメーション プロバイダーは、マネージド コードまたは C/C++ で記述できます。  
  
<a name="Support_in_Windows_Presentation_Foundation_"></a>
## <a name="support-in-windows-presentation-foundation"></a>Windows Presentation Foundation におけるサポート  
 Windows プレゼンテーションファンデーション (WPF) は、ユーザー インターフェイスを作成するための新しいモデルです。 WPF 要素には、アクティブ なアクセシビリティのネイティブ サポートは含まれていません。ただし、アクティブなユーザー[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]補助クライアントのブリッジング サポートを含む 、 サポートを行います。 特に用に記述[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]されたクライアントだけが、テキストの豊富なサポートなど、WPF のアクセシビリティ機能を最大限に活用できます。  
  
<a name="Servers_and_Clients_compare"></a>
## <a name="servers-and-clients"></a>サーバーとクライアント  
 Active Accessibility では、サーバーとクライアントは、主に サーバーの 実装を通`IAccessible`じて直接通信します。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]では、サーバー (プロバイダー) とクライアントの間にコア サービスが存在します。 このコア サービスは、プロバイダーによって実装されたインターフェイスを呼び出して、追加のサービス (要素の一意のランタイム識別子の生成など) を提供します。 クライアント アプリケーションはライブラリ関数を使用して [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] サービスを呼び出します。  
  
 UI オートメーション プロバイダーは、アクティブなユーザー補助クライアントに情報を提供でき、アクティブなユーザー補助サーバーは、UI オートメーション クライアント アプリケーションに情報を提供できます。 ただし、アクティブなアクセシビリティは、 ほど[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]多くの情報を公開しないため、この 2 つのモデルは完全には互換性がありません。  
  
<a name="UI_Elements_compare"></a>
## <a name="ui-elements"></a>UI 要素  
 アクティブアクセシビリティは[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]、`IAccessible`インターフェイスまたは子識別子として要素を表示します。 2 つの `IAccessible` ポインターを比較してそれらが同じ要素を参照しているかどうかを判断するのは困難です。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]では、すべての要素が <xref:System.Windows.Automation.AutomationElement> オブジェクトとして表現されます。 比較は等値演算子または <xref:System.Windows.Automation.AutomationElement.Equals%2A> メソッドを使用して行われますが、どちらの方法でも、要素の一意のランタイム識別子が比較されます。  
  
<a name="Tree_Views_and_Navigation_compare"></a>
## <a name="tree-views-and-navigation"></a>ツリー ビューとナビゲーション  
 画面上の [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] 要素は、ツリー構造で表すことができます。デスクトップがルートで、その直接の子としてアプリケーション ウィンドウがあり、アプリケーション内の要素がその子孫となります。  
  
 アクティブアクセシビリティでは、エンドユーザーとは関係のない多くのオートメーション要素がツリーに表示されます。 クライアント アプリケーションは、すべての要素の中から意味のあるものを特定する必要があります。  
  
 UI オートメーション クライアント アプリケーションは、フィルタリングしたビューを使用して [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] を確認します。 このビューには、必要な要素 (ユーザーに情報を提供したり、対話を可能にしたりする要素) のみが表示されます。 コントロール要素だけが含まれるビューや、コンテンツ要素だけが含まれるビューがあらかじめ定義されています。さらに、アプリケーションでカスタム ビューを定義することもできます。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] は、ユーザーに対して [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] を簡単に表せるようにして、ユーザーとアプリケーションの対話を支援します。  
  
 [アクティブ なアクセシビリティ] の要素間のナビゲーションは、空間 (たとえば、画面の左側にある要素に移動する)、論理的 (たとえば、次のメニュー項目に移動する、ダイアログ ボックス内のタブ オーダーの次の項目) 、または階層 (たとえば、コンテナ内の最初の子を移動したり、子から親に移動したりします。 子要素が `IAccessible`を実装しているオブジェクトであるとは限らないため、階層的ナビゲーションは複雑です。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]では、すべての [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 要素は、同じ基本機能をサポートする <xref:System.Windows.Automation.AutomationElement> オブジェクトです (プロバイダの観点からは、これらのオブジェクトは、から<xref:System.Windows.Automation.Provider.IRawElementProviderSimple>継承されたインターフェイスを実装するオブジェクトです)。ナビゲーションは主に階層的で、親から子へ、兄弟間を次に進みます。 (兄弟間のナビゲーションには、タブ オーダーに従う場合があるため、論理要素があります)。<xref:System.Windows.Automation.TreeWalker>クラスを使用して、ツリーのフィルタービューを使用して、任意の開始点から移動できます。 <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> と <xref:System.Windows.Automation.AutomationElement.FindAll%2A>を使用して、特定の子または子孫に移動することもできます。たとえば、指定したコントロール パターンがサポートされるダイアログ ボックス内のすべての要素を非常に簡単に取得できます。  
  
 での[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ナビゲーションは、アクティブなアクセシビリティよりも一貫性があります。 ドロップダウンリストやポップアップウィンドウなどの一部の要素は、[アクティブなアクセシビリティ]ツリーに2回表示され、それらからのナビゲーションは予期しない結果になる可能性があります。 実際には、Rebar コントロールに対してアクティブなアクセシビリティを適切に実装することは不可能です。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] では親の再指定や位置の変更が可能なため、ウィンドウの所有関係による階層にかかわらず、要素をツリー内の任意の場所に配置できます。  
  
<a name="Roles_and_Control_Types"></a>
## <a name="roles-and-control-types"></a>役割とコントロール型  
 アクティブ アクセシビリティでは`accRole`、プロパティ`IAccessible::get_actRole`( ) を使用して、 ROLE_SYSTEM_SLIDER や[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]ROLE_SYSTEM_MENUITEM などの要素のロールの説明を取得します。 要素の役割は、要素の機能を表す主要な鍵になります。 コントロールとの対話は、 `IAccessible::accSelect` や `IAccessible::accDoDefaultAction`などの固定のメソッドを使用して実現されます。 クライアント アプリケーションと [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] の間の対話は、 `IAccessible`を通して実行できる範囲に限定されます。  
  
 これに対して、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] では、要素のコントロール型 ( <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> プロパティで記述) と、その要素に期待される機能とが大きく分離されています。 機能は、特殊なインターフェイスの実装を通じてプロバイダーによってサポートされる、コントロール パターンによって決定されます。 複数のコントロール パターンを組み合わせると、特定の [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 要素がサポートする機能をすべて記述することができます。 プロバイダーによっては、ある 1 つの特定のコントロール パターンをサポートしなければならないものがあります。たとえば、チェック ボックスのプロバイダーは Toggle コントロール パターンをサポートする必要があります。 また、コントロール パターンのセットを 1 つ以上サポートしなければならないものもあります。たとえば、ボタンは、Toggle と Invoke のいずれかをサポートする必要があります。 さらに、コントロール パターンをまったくサポートしないものもあります。たとえば、移動もサイズ変更もドッキングもできないペインには、コントロール パターンはありません。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] は、 <xref:System.Windows.Automation.ControlType.Custom> プロパティによって識別され、 <xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty> プロパティによって記述可能なカスタム コントロールをサポートします。  
  
 次の表は、コントロールの種類へのアクティブ[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]アクセシビリティ ロールのマッピングを示しています。  
  
|アクティブなアクセシビリティ ロール|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] のコントロール型|  
|----------------------------------------------------------------------|----------------------------------------------------------------------------------------|  
|ROLE_SYSTEM_PUSHBUTTON|ボタン|  
|ROLE_SYSTEM_CLIENT|Calendar|  
|ROLE_SYSTEM_CHECKBUTTON|チェック ボックス|  
|ROLE_SYSTEM_COMBOBOX|コンボ ボックス|  
|ROLE_SYSTEM_CLIENT|Custom|  
|ROLE_SYSTEM_LIST|データ グリッド|  
|ROLE_SYSTEM_LISTITEM|データ アイテム|  
|ROLE_SYSTEM_DOCUMENT|ドキュメント|  
|ROLE_SYSTEM_TEXT|[編集]|  
|ROLE_SYSTEM_GROUPING|グループ|  
|ROLE_SYSTEM_LIST|ヘッダー|  
|ROLE_SYSTEM_COLUMNHEADER|ヘッダー項目|  
|ROLE_SYSTEM_LINK|ハイパーリンク|  
|ROLE_SYSTEM_GRAPHIC|Image|  
|ROLE_SYSTEM_LIST|List|  
|ROLE_SYSTEM_LISTITEM|リスト項目|  
|ROLE_SYSTEM_MENUPOPUP|メニュー|  
|ROLE_SYSTEM_MENUBAR|メニュー バー|  
|ROLE_SYSTEM_MENUITEM|メニュー項目|  
|ROLE_SYSTEM_PANE|ペイン|  
|ROLE_SYSTEM_PROGRESSBAR|進行状況バー|  
|ROLE_SYSTEM_RADIOBUTTON|オプション ボタン|  
|ROLE_SYSTEM_SCROLLBAR|スクロール バー|  
|ROLE_SYSTEM_SEPARATOR|区切り記号|  
|ROLE_SYSTEM_SLIDER|スライダー|  
|ROLE_SYSTEM_SPINBUTTON|Spinner|  
|ROLE_SYSTEM_SPLITBUTTON|分割ボタン|  
|ROLE_SYSTEM_STATUSBAR|ステータス バー|  
|ROLE_SYSTEM_PAGETABLIST|タブ|  
|ROLE_SYSTEM_PAGETAB|タブ項目|  
|ROLE_SYSTEM_TABLE|テーブル|  
|ROLE_SYSTEM_STATICTEXT|Text|  
|ROLE_SYSTEM_INDICATOR|つまみ|  
|ROLE_SYSTEM_TITLEBAR|タイトル バー|  
|ROLE_SYSTEM_TOOLBAR|ツール バー|  
|ROLE_SYSTEM_TOOLTIP|ヒント|  
|ROLE_SYSTEM_OUTLINE|ツリー|  
|ROLE_SYSTEM_OUTLINEITEM|ツリー項目|  
|ROLE_SYSTEM_WINDOW|ウィンドウ|  
  
 さまざまなコントロール型の詳細については、「 [UI Automation Control Types](ui-automation-control-types.md)」を参照してください。  
  
<a name="States_and_Properties"></a>
## <a name="states-and-properties"></a>状態とプロパティ  
 Active Accessibility では、要素は共通のプロパティ セットをサポートし、一`accState`部のプロパティ ( など ) は要素の役割に応じて非常に異なる記述をする必要があります。 サーバーは、プロパティを返す `IAccessible` のメソッドをすべて (要素に無関係なものも含む) 実装する必要があります。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]では、さらに多くのプロパティを定義しますが、その一部はアクティブなアクセシビリティの状態に対応しています。 すべての要素に共通するものもあれば、コントロール型とコントロール パターンに固有のものもあります。 プロパティは一意の識別子によって識別され、ほとんどのプロパティは単一のメソッド ( <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> または <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>) を使用して取得できます。 多くのプロパティは、 <xref:System.Windows.Automation.AutomationElement.Current%2A> プロパティ アクセサーおよび <xref:System.Windows.Automation.AutomationElement.Cached%2A> プロパティ アクセサーからも容易に取得できます。  
  
 UI オートメーション プロバイダーは、無関係なプロパティを実装する必要はなく、サポートしていないプロパティに対しては単に `null` 値を返すことができます。 また、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] のコア サービスは、一部のプロパティを既定のウィンドウ プロバイダーから取得できます。これらのプロパティは、プロバイダーによって明示的に実装されたプロパティと 1 つにまとめられます。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] では、多くのプロパティをサポートすることに加えて、単一のプロセス間呼び出しで複数のプロパティを取得できるので、パフォーマンスが向上します。  
  
 次の表に、2 つのモデルのプロパティ間の対応を示します。  
  
|アクティブ アクセシビリティ プロパティ アクセサー|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] のプロパティ ID|解説|  
|-----------------------------------------------------------------------------------|---------------------------------------------------------------------------------------|-------------|  
|`get_accKeyboardShortcut`|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty> または <xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|両方とも存在する場合は`AccessKeyProperty` が優先されます。|  
|`get_accName`|<xref:System.Windows.Automation.AutomationElement.NameProperty>||  
|`get_accRole`|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|役割とコントロール型のマッピングについては、前の表を参照してください。|  
|`get_accValue`|<xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=nameWithType>|ValuePattern または RangeValuePattern をサポートするコントロール型でのみ有効です。 MSAA 動作との一貫性を保つために、RangeValue 値は 0 ～ 100 に正規化されます。 Value 項目は文字列を使用します。|  
|`get_accHelp`|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>||  
|`accLocation`|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>||  
|`get_accDescription`|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|`accDescription` に関する明確な仕様が MSAA 内に存在しなかったので、このプロパティに格納される情報はプロバイダーによって異なります。|  
|`get_accHelpTopic`|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]||  
  
 次の表は、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]アクティブなアクセシビリティ状態定数に対応するプロパティを示しています。  
  
|アクティブなアクセシビリティの状態|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] プロパティ|状態の変更をトリガーする|  
|-----------------------------------------------------------------------|------------------------------------------------------------------------------------|----------------------------|  
|STATE_SYSTEM_CHECKED|チェック ボックスの場合、 <xref:System.Windows.Automation.TogglePattern.ToggleStateProperty><br /><br /> オプション ボタンの場合、 <xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|Y|  
|STATE_SYSTEM_COLLAPSED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> = <xref:System.Windows.Automation.ExpandCollapseState.Collapsed>|Y|  
|STATE_SYSTEM_EXPANDED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> = <xref:System.Windows.Automation.ExpandCollapseState.Expanded> または <xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded>|Y|  
|STATE_SYSTEM_FOCUSABLE|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|N|  
|STATE_SYSTEM_FOCUSED|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|N|  
|STATE_SYSTEM_HASPOPUP|<xref:System.Windows.Automation.ExpandCollapsePattern> (メニュー項目の場合)|N|  
|STATE_SYSTEM_INVISIBLE|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty> = True かつ <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A> の場合に <xref:System.Windows.Automation.NoClickablePointException>|N|  
|STATE_SYSTEM_LINKED|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> =<br /><br /> <xref:System.Windows.Automation.ControlType.Hyperlink>|N|  
|STATE_SYSTEM_MIXED|<xref:System.Windows.Automation.TogglePattern.TogglePatternInformation.ToggleState%2A> = <xref:System.Windows.Automation.ToggleState.Indeterminate>|N|  
|STATE_SYSTEM_MOVEABLE|<xref:System.Windows.Automation.TransformPattern.CanMoveProperty>|N|  
|STATE_SYSTEM_MUTLISELECTABLE|<xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty>|N|  
|STATE_SYSTEM_OFFSCREEN|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty> = True|N|  
|STATE_SYSTEM_PROTECTED|<xref:System.Windows.Automation.AutomationElement.IsPasswordProperty>|N|  
|STATE_SYSTEM_READONLY|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty?displayProperty=nameWithType> および <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty?displayProperty=nameWithType>|N|  
|STATE_SYSTEM_SELECTABLE|<xref:System.Windows.Automation.SelectionItemPattern> がサポートされています|N|  
|STATE_SYSTEM_SELECTED|<xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|N|  
|STATE_SYSTEM_SIZEABLE|<xref:System.Windows.Automation.TransformPattern.TransformPatternInformation.CanResize%2A>|N|  
|STATE_SYSTEM_UNAVAILABLE|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|Y|  
  
 次の状態は、ほとんどのアクティブなアクセシビリティ コントロール サーバーによって実装されていないか、または[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]に同等の状態がないのいずれかです。  
  
|アクティブなアクセシビリティの状態|解説|  
|-----------------------------------------------------------------------|-------------|  
|STATE_SYSTEM_BUSY|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_DEFAULT|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_ANIMATED|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_EXTSELECTABLE|アクティブなアクセシビリティサーバーによって広く実装されていません|  
|STATE_SYSTEM_MARQUEED|アクティブなアクセシビリティサーバーによって広く実装されていません|  
|STATE_SYSTEM_SELFVOICING|アクティブなアクセシビリティサーバーによって広く実装されていません|  
|STATE_SYSTEM_TRAVERSED|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_ALERT_HIGH|アクティブなアクセシビリティサーバーによって広く実装されていません|  
|STATE_SYSTEM_ALERT_MEDIUM|アクティブなアクセシビリティサーバーによって広く実装されていません|  
|STATE_SYSTEM_ALERT_LOW|アクティブなアクセシビリティサーバーによって広く実装されていません|  
|STATE_SYSTEM_FLOATING|アクティブなアクセシビリティサーバーによって広く実装されていません|  
|STATE_SYSTEM_HOTTRACKED|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_PRESSED|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
  
 プロパティ識別子の完全な[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]一覧については、「 [UI オートメーション プロパティの概要](ui-automation-properties-overview.md)」を参照してください。  
  
<a name="uiautomation_events_compare"></a>
## <a name="events"></a>events  
 のイベント メカニズム[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]は、アクティブ なユーザー補助の場合とは異なり、Windows イベント ルーティング (ウィンドウ ハンドルと密接に結び付けられている) に依存せず、クライアント アプリケーションがフックを設定する必要はありません。 イベントのサブスクリプションは、特定のイベントに対してだけでなく、ツリーの特定の部分を対象とするように細かく調整できます。 プロバイダーも、リッスンされているイベントを追跡して、イベントの生成を細かく調整できます。  
  
 イベントを生成した要素をクライアントで取得することも簡単です。このような要素は、イベント コールバックに直接渡されるからです。 クライアントがイベントをサブスクライブしているときにキャッシュ要求がアクティブであった場合は、自動的に要素のプロパティがプリフェッチされます。  
  
 次の表は、アクティブなアクセシビリティ WinEvents[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]とイベントの対応を示しています。  
  
|WinEvent|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] のイベント識別子|  
|--------------|--------------------------------------------------------------------------------------------|  
|EVENT_OBJECT_ACCELERATORCHANGE|<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty> プロパティの変更|  
|EVENT_OBJECT_CONTENTSCROLLED|関連付けられたスクロール バーにおける または  プロパティの変更|  
|EVENT_OBJECT_CREATE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_DEFACTIONCHANGE|該当するショートカットはありません|  
|EVENT_OBJECT_DESCRIPTIONCHANGE|まったく同等の項目はありません (おそらく <xref:System.Windows.Automation.AutomationElement.HelpTextProperty> または <xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty> プロパティの変更)|  
|EVENT_OBJECT_DESTROY|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_FOCUS|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent>|  
|EVENT_OBJECT_HELPCHANGE|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty> の変更|  
|EVENT_OBJECT_HIDE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_LOCATIONCHANGE|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> プロパティの変更|  
|EVENT_OBJECT_NAMECHANGE|<xref:System.Windows.Automation.AutomationElement.NameProperty> プロパティの変更|  
|EVENT_OBJECT_PARENTCHANGE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_REORDER|アクティブなアクセシビリティで一貫して使用されていません。 直接対応するイベントが [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]では定義されていません。|  
|EVENT_OBJECT_SELECTION|<xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>|  
|EVENT_OBJECT_SELECTIONADD|<xref:System.Windows.Automation.SelectionItemPattern.ElementAddedToSelectionEvent>|  
|EVENT_OBJECT_SELECTIONREMOVE|<xref:System.Windows.Automation.SelectionItemPattern.ElementRemovedFromSelectionEvent>|  
|EVENT_OBJECT_SELECTIONWITHIN|該当するショートカットはありません|  
|EVENT_OBJECT_SHOW|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_STATECHANGE|さまざまなプロパティ変更イベント|  
|EVENT_OBJECT_VALUECHANGE|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=nameWithType> および <xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=nameWithType> の変更|  
|EVENT_SYSTEM_ALERT|該当するショートカットはありません|  
|EVENT_SYSTEM_CAPTUREEND|該当するショートカットはありません|  
|EVENT_SYSTEM_CAPTURESTART|該当するショートカットはありません|  
|EVENT_SYSTEM_CONTEXTHELPEND|該当するショートカットはありません|  
|EVENT_SYSTEM_CONTEXTHELPSTART|該当するショートカットはありません|  
|EVENT_SYSTEM_DIALOGEND|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|  
|EVENT_SYSTEM_DIALOGSTART|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|  
|EVENT_SYSTEM_DRAGDROPEND|該当するショートカットはありません|  
|EVENT_SYSTEM_DRAGDROPSTART|該当するショートカットはありません|  
|EVENT_SYSTEM_FOREGROUND|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent>|  
|EVENT_SYSTEM_MENUEND|<xref:System.Windows.Automation.AutomationElement.MenuClosedEvent>|  
|EVENT_SYSTEM_MENUPOPUPEND|<xref:System.Windows.Automation.AutomationElement.MenuClosedEvent>|  
|EVENT_SYSTEM_MENUPOPUPSTART|<xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent>|  
|EVENT_SYSTEM_MENUSTART|<xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent>|  
|EVENT_SYSTEM_MINIMIZEEND|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty> プロパティの変更|  
|EVENT_SYSTEM_MINIMIZESTART|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty> プロパティの変更|  
|EVENT_SYSTEM_MOVESIZEEND|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> プロパティの変更|  
|EVENT_SYSTEM_MOVESIZESTART|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> プロパティの変更|  
|EVENT_SYSTEM_SCROLLINGEND|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> または <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> プロパティの変更|  
|EVENT_SYSTEM_SCROLLINGSTART|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> または <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> プロパティの変更|  
|EVENT_SYSTEM_SOUND|該当するショートカットはありません|  
|EVENT_SYSTEM_SWITCHEND|同等の項目はありませんが、新しいアプリケーションがフォーカスを受け取ったことは <xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent> イベントによって通知されます。|  
|EVENT_SYSTEM_SWITCHSTART|該当するショートカットはありません|  
|該当するショートカットはありません|<xref:System.Windows.Automation.MultipleViewPattern.CurrentViewProperty> プロパティの変更|  
|該当するショートカットはありません|<xref:System.Windows.Automation.ScrollPattern.HorizontallyScrollableProperty> プロパティの変更|  
|該当するショートカットはありません|<xref:System.Windows.Automation.ScrollPattern.VerticallyScrollableProperty> プロパティの変更|  
|該当するショートカットはありません|<xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> プロパティの変更|  
|該当するショートカットはありません|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> プロパティの変更|  
|該当するショートカットはありません|<xref:System.Windows.Automation.ScrollPattern.HorizontalViewSizeProperty> プロパティの変更|  
|該当するショートカットはありません|<xref:System.Windows.Automation.ScrollPattern.VerticalViewSizeProperty> プロパティの変更|  
|該当するショートカットはありません|<xref:System.Windows.Automation.TogglePattern.ToggleStateProperty> プロパティの変更|  
|該当するショートカットはありません|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty> プロパティの変更|  
|該当するショートカットはありません|<xref:System.Windows.Automation.AutomationElement.AsyncContentLoadedEvent> イベント|  
|該当するショートカットはありません|<xref:System.Windows.Automation.AutomationElement.ToolTipOpenedEvent>|  
  
<a name="Security_compare"></a>
## <a name="security"></a>Security  
 `IAccessible` をカスタマイズするシナリオでは、基本 `IAccessible` をラップしてからこれに対する呼び出しを行うという要件が生じることがあります。 このことは、セキュリティに影響を及ぼします。部分信頼コンポーネントにコード パスを中継させてはならないからです。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] モデルでは、プロバイダーが他のプロバイダー コードを呼び出す必要がありません。 必要な集約はすべて [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] コア サービスが行います。  
  
## <a name="see-also"></a>関連項目

- [UI オートメーションの基本](index.md)
