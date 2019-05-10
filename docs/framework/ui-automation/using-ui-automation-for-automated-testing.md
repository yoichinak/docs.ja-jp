---
title: UI オートメーションによる自動テスト
ms.date: 03/30/2017
helpviewer_keywords:
- automated testing
- testing, UI Automation
- UI Automation, automated testing
ms.assetid: 3a0435c0-a791-4ad7-ba92-a4c1d1231fde
ms.openlocfilehash: 0e5e2252225c824dfbc9d799b29a16ab6206eb3c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64630660"
---
# <a name="using-ui-automation-for-automated-testing"></a>UI オートメーションによる自動テスト
> [!NOTE]
>  このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 に関する最新情報については[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]を参照してください[Windows Automation API:UI オートメーション](https://go.microsoft.com/fwlink/?LinkID=156746)します。  
  
 ここでは、自動テストのシナリオで、プログラムによるアクセスのためのフレームワークとして [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] がどのように役立つかについて説明します。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] の統一されたオブジェクト モデルを使用すると、すべての [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] フレームワークにおいて、複雑で豊富な機能をアクセシビリティが高く自動化しやすい方法で公開できます。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] は、 [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)]の後継として開発されました。 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] は、コントロールとアプリケーションにアクセスできるように設計された既存のフレームワークです。 ユーザー補助と自動化の要件がよく似ているため、[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] はテストの自動化に使用されるようになりましたが、この役割を想定して設計されたものではありません。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]は、ユーザー補助のためのより洗練されたソリューションを提供するだけでなく、信頼性の高い自動テスト機能を提供するように設計されています。 たとえば、 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] では、UI に関する情報の公開と、AT 製品に必要な情報の収集の両方に、同じインターフェイスを使用します。これに対して [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] では、2 つのモデルを分けています。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] を自動テスト ツールとして利用するには、プロバイダーとクライアントの両方にこれを実装する必要があります。 UI オートメーション プロバイダーは、Microsoft Word、Excel やその他のサードパーティ アプリケーションなどのアプリケーション、または [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] オペレーティング システムに基づくコントロールです。 UI オートメーション クライアントは、自動テスト スクリプトや支援 (補助) 技術アプリケーションなどです。  
  
> [!NOTE]
>  この概要の目的は、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の、自動テストに関する新機能と強化された機能について説明することです。 この概要はユーザー補助機能に関する情報の提供を目的とするものではなく、必要な場合以外、ユーザー補助については説明しません。  
  
<a name="Using_UI_Automation_During_Development"></a>   
## <a name="ui-automation-in-a-provider"></a>プロバイダーにおける UI オートメーション  
 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] を自動化するためにアプリケーションやコントロールの開発者が注意する必要があるのは、その [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] オブジェクトでキーボードとマウスの標準操作を使用して実行できるエンド ユーザーのアクションです。  
  
 これらの主要なアクションを特定したら、対応する [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] コントロール パターン (つまり、 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 要素の機能と動作をミラー化するコントロール パターン) をコントロール上に実装します。 たとえば、コンボ ボックス コントロール (実行用のダイアログなど) でのユーザー操作には、通常、項目の一覧を非表示にしたり表示したりするためのコンボ ボックスの展開と折りたたみ、一覧からの項目の選択、またはキーボード入力による新しい値の追加が含まれます。  
  
> [!NOTE]
>  他のユーザー補助モデルでは、開発者が直接、個々のボタン、メニューなどのコントロールから情報を収集する必要があります。 しかも、各コントロール型には、細部の異なるバリエーションが多数存在します。 つまり、あるプッシュボタンに 10 個のバリエーションが存在すると、それらすべての動作と機能が同じであっても、それぞれを別個のコントロールとして扱う必要があります。 これらのコントロールが機能的に同等であることを知る方法はありません。 コントロール パターンは、こうした共通のコントロール動作を表すために開発されました。 詳細については、「 [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)」を参照してください。  
  
<a name="Implementing_UI_Automation"></a>   
### <a name="implementing-ui-automation"></a>UI オートメーションの実装  
 既に述べたように、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の統一されたモデルを使用しない場合、フレームワーク内のコントロールのプロパティや動作を公開するためには、フレームワーク固有の情報をテスト ツールや開発者が知る必要があります。 複数の UI フレームワーク Windows オペレーティング システム内には常に存在することができる、のでなど[!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)]、 [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]、Windows Presentation Foundation (WPF) を持つ複数のアプリケーションをテストする面倒な作業をすることと似たコントロール。 次の表では、例として、あるボタン コントロールに関連付けられた名前 (またはテキスト) を取得するために必要なフレームワーク固有のプロパティ名と、それと同等の単一 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] プロパティを示します。  
  
|UI オートメーション コントロール型|UI フレームワーク|フレームワーク固有のプロパティ|UI Automation のプロパティ|  
|--------------------------------|------------------|---------------------------------|----------------------------|  
|ボタン|Windows Presentation Foundation|Content|NameProperty|  
|ボタン|Win32|[キャプション]|NameProperty|  
|イメージ|HTML|alt|NameProperty|  
  
 UI オートメーション プロバイダーは、そのコントロールのフレームワーク固有のプロパティから、同等の [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] プロパティへのマッピングを行います。  
  
 実装について[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]プロバイダー内にある[マネージ コードの UI オートメーション プロバイダー](../../../docs/framework/ui-automation/ui-automation-providers-for-managed-code.md)します。 コントロール パターンを実装する方法については、「 [UI Automation Control Patterns](../../../docs/framework/ui-automation/ui-automation-control-patterns.md) 」および「 [UI Automation Text Pattern](../../../docs/framework/ui-automation/ui-automation-text-pattern.md)」を参照してください。  
  
<a name="Testing_with_UI_Automation"></a>   
## <a name="ui-automation-in-a-client"></a>クライアントにおける UI オートメーション  
 多くの自動テスト ツールやシナリオの目的は、一貫性があって再現可能なユーザー インターフェイス操作です。 これには、特定のコントロールの単体テストから、コントロールのグループに対する一連の一般的なアクションを反復処理するテスト スクリプトの記録と再生までが含まれます。  
  
 自動アプリケーションでの問題は、動的な対象にテストを合わせることが難しい点です。 たとえば、Windows タスク マネージャーに含まれているような、現在実行中のアプリケーションを一覧表示するリスト ボックス コントロールがあります。 リスト ボックス内の項目はテスト アプリケーションの制御範囲外で動的に更新されるため、リスト ボックスの特定の項目を一貫性を保って繰り返し選択することは不可能です。 テスト アプリケーションの制御範囲外の [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] でフォーカスの単純な変更を繰り返そうとした場合も、同様の問題が起きることがあります。  
  
<a name="Programmatic_Access"></a>   
### <a name="programmatic-access"></a>プログラムによるアクセス  
 プログラムによるアクセスでは、従来のマウス入力やキーボード入力によって公開される対話やエクスペリエンスをコードによって模倣する機能が提供されます。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] は、5 つのコンポーネントにより、プログラムによるアクセスを有効にします。  
  
- [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリーは、 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]の構造全体にわたってナビゲーションを容易にします。 ツリーは、hWnd のツリーのコレクションから構築されます。 詳細については、「 [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)」を参照してください。  
  
- オートメーション要素は、 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]の個々のコンポーネントです。 通常、これらは hWnd よりも細かい単位です。 詳細については、「 [UI Automation Control Types Overview](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)」を参照してください。  
  
- オートメーション プロパティは、 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 要素に関する具体的な情報を提供します。 詳細については、「 [UI Automation Properties Overview](../../../docs/framework/ui-automation/ui-automation-properties-overview.md)」を参照してください。  
  
- コントロール パターンは、コントロールが持つ機能の特定の側面を定義します。プロパティ、メソッド、イベント、および構造体の情報で構成することができます。 詳細については、「 [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)」を参照してください。  
  
- オートメーション イベントは、イベント通知と情報を提供します。 詳細については、「 [UI Automation Events Overview](../../../docs/framework/ui-automation/ui-automation-events-overview.md)」を参照してください。  
  
<a name="Key_properties_critical_to_test_automation"></a>   
### <a name="key-properties-for-test-automation"></a>自動テストの主要なプロパティ  
 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] 内の任意のコントロールを一意に識別して検索する機能は、自動テスト アプリケーションがその [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]を処理する基盤です。 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] プロパティの中にはこれを支援するものがいくつかあり、クライアントとプロバイダーによって使用されます。  
  
#### <a name="automationid"></a>AutomationID  
 オートメーション要素をその兄弟から一意に識別します。 製品が複数言語で出荷される場合に通常ローカライズされる<xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> などのプロパティとは異なり、 <xref:System.Windows.Automation.AutomationElement.NameProperty> はローカライズされません。 「 [Use the AutomationID Property](../../../docs/framework/ui-automation/use-the-automationid-property.md)」を参照してください。  
  
> [!NOTE]
>  <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> では、オートメーション ツリー全体にわたって一意に識別できるとは限りません。 たとえば、アプリケーションには複数のトップレベルのメニュー項目を持つメニュー コントロールが含まれ、さらに、それらのメニュー項目に複数の子メニュー項目が含まれている場合があります。 これらの 2 次メニュー項目は、Item1、Item2、Item3 などの汎用スキームで識別され、トップレベルのメニュー項目間で子の識別子が重複することがあります。  
  
#### <a name="controltype"></a>ControlType  
 オートメーション要素によって表されるコントロール型を識別します。 コントロール型がわかると、そこから多くの情報を推測できます。 「 [UI Automation Control Types Overview](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)」を参照してください。  
  
#### <a name="nameproperty"></a>NameProperty  
 これは、コントロールを識別または説明するテキスト文字列です。 <xref:System.Windows.Automation.AutomationElement.NameProperty> はローカライズされる可能性があるため、注意して使用する必要があります。 「 [UI Automation Properties Overview](../../../docs/framework/ui-automation/ui-automation-properties-overview.md)」を参照してください。  
  
<a name="Steps_Required_To_Automate_the_UI_in_a_Test_Application"></a>   
### <a name="implementing-ui-automation-in-a-test-application"></a>テスト アプリケーションへの UI オートメーションの実装  
  
|||  
|-|-|  
|UI オートメーション参照を追加します。|UI オートメーション クライアントに必要な [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] の dll を次に示します。<br /><br /> -UIAutomationClient.dll へのアクセスを提供する、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]クライアント側 Api。<br />-UIAutomationClientSideProvider.dll を自動化する機能を提供する[!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)]コントロール。 「 [UI Automation Support for Standard Controls](../../../docs/framework/ui-automation/ui-automation-support-for-standard-controls.md)」を参照してください。<br />-UIAutomationTypes.dll で定義されている特定の型へのアクセスを提供する[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]します。|  
|<xref:System.Windows.Automation> 名前空間を追加します。|この名前空間には、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] のテキスト処理以外の機能を使用するために UI オートメーション クライアントが必要とするすべてのものが含まれています。|  
|<xref:System.Windows.Automation.Text> 名前空間を追加します。|この名前空間には、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] のテキスト処理機能を使用するために UI オートメーション クライアントが必要とするすべてのものが含まれています。|  
|目的のコントロールを検索します。|自動テスト スクリプトは、目的のコントロールを表す UI オートメーション要素をオートメーション ツリー内で検索します。<br /><br /> コードで UI オートメーション要素を取得する方法は複数あります。<br /><br /> -クエリ、[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]を使用して、<xref:System.Windows.Automation.Condition>ステートメント。 この場合は、通常、言語に依存しない <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> を使用します。 **注:**<xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>明細化できる Inspect.exe などのツールを使用して取得できます、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]コントロールのプロパティ。 <br /><br /> -を使用して、<xref:System.Windows.Automation.TreeWalker>クラス全体を走査する[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ツリーまたはそのサブセットです。<br />フォーカスを追跡します。<br />-コントロールの hWnd を使用します。<br />-マウス カーソルの場所など、画面位置を使用します。<br /><br /> 「 [Obtaining UI Automation Elements](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)」を参照してください。|  
|コントロール パターンを取得します。|コントロール パターンは、機能的によく似た複数のコントロールにおける共通の動作を公開します。<br /><br /> 自動テスト スクリプトは、テストする必要があるコントロールを特定すると、それらの UI オートメーション要素から目的のコントロール パターンを取得します。 たとえば、一般的なボタン機能には <xref:System.Windows.Automation.InvokePattern> コントロール パターンを、ウィンドウ機能には <xref:System.Windows.Automation.WindowPattern> コントロール パターンを使用します。<br /><br /> 「 [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)」を参照してください。|  
|UI を自動化します。|自動テスト スクリプトで、 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] フレームワークの任意の [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] を、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] コントロール パターンによって公開された情報や機能を使用して制御できるようになりました。|  
  
<a name="Supporting_tools"></a>   
## <a name="related-tools-and-technologies"></a>関連ツールと関連技術  
 複数の関連ツールや関連技術で、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]を使用した自動テストがサポートされています。  
  
- Inspect.exe は、[!INCLUDE[TLA#tla_gui](../../../includes/tlasharptla-gui-md.md)]収集するために使用できるアプリケーション[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]プロバイダーとクライアントの開発とデバッグの両方の情報。 含まれている Inspect.exe、[!INCLUDE[TLA#tla_winfxsdk](../../../includes/tlasharptla-winfxsdk-md.md)]します。  
  
- MSAABridge は、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] クライアントに対して [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] 情報を公開します。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] と [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] の間に継続性を持たせる主な目的は、既存の [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] クライアントが [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]を実装済みの任意のフレームワークと対話できるようにすることです。  
  
<a name="Security"></a>   
## <a name="security"></a>セキュリティ  
 セキュリティについては、「 [UI Automation Security Overview](../../../docs/framework/ui-automation/ui-automation-security-overview.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [UI オートメーションの基礎](../../../docs/framework/ui-automation/index.md)
