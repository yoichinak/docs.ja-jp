---
title: クライアントの UI オートメーション コントロール パターン
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, control patterns for clients
- control patterns, UI Automation clients
ms.assetid: 571561d8-5f49-43a9-a054-87735194e013
ms.openlocfilehash: f545cbbacac6670f11f28166191112c9fba4f70f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953233"
---
# <a name="ui-automation-control-patterns-for-clients"></a>クライアントの UI オートメーション コントロール パターン
> [!NOTE]
> このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 の最新情報[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]については[、「Windows Automation API:UI オートメーション](https://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 この概要では、UI オートメーション クライアントのコントロール パターンについて説明します。 また、UI オートメーション クライアントがコントロール パターンを使用して、 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)]の情報にアクセスするしくみについても説明します。  
  
 コントロール パターンは、コントロール型や外観に関係なく、コントロールの機能を分類したり公開したりするための手段です。 UI オートメーション クライアントは、 <xref:System.Windows.Automation.AutomationElement> を調べてどのコントロール パターンがサポートされているかを特定し、そのコントロールの動作を確実に実行することができます。  
  
 コントロール パターンの完全なリストについては、「 [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)」をご覧ください。  
  
<a name="uiautomation_getting_control_patterns"></a>   
## <a name="getting-control-patterns"></a>コントロール パターンの取得  
 クライアントは、 <xref:System.Windows.Automation.AutomationElement> または <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A?displayProperty=nameWithType> を呼び出して、 <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A?displayProperty=nameWithType>からコントロール パターンを取得します。  
  
 クライアントは、 <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> メソッドまたは個別の `IsPatternAvailable` プロパティ ( <xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>など) を使用して、パターンまたはパターンのグループが <xref:System.Windows.Automation.AutomationElement>でサポートされているかどうかを特定できます。 ただし、サポートされているプロパティを確認してコントロール パターンを取得するよりも、コントロール パターンを取得して `null` 参照に対するテストを試行する方が、プロセス間呼び出しが少なくなるため効率的です。  
  
 <xref:System.Windows.Automation.TextPattern> から <xref:System.Windows.Automation.AutomationElement>コントロール パターンを取得する方法を次の例に示します。  
  
 [!code-csharp[UIATextPattern_snip#1037](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#1037)]  
  
<a name="uiautomation_properties_on_control_patterns"></a>   
## <a name="retrieving-properties-on-control-patterns"></a>コントロール パターンのプロパティの取得  
 クライアントは、 <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A?displayProperty=nameWithType> または <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A?displayProperty=nameWithType> を呼び出し、返されたオブジェクトを適切な型にキャストすることで、コントロール パターンのプロパティ値を取得できます。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]プロパティの詳細については、「[クライアントの UI オートメーションのプロパティ](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)」を参照してください。  
  
 `GetPropertyValue`メソッドだけでなく、共通言語ランタイム (CLR) アクセサーを使用してプロパティ値を取得し、パターン[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]のプロパティにアクセスすることもできます。  
  
<a name="uiautomation_with_variable_patterns"></a>   
## <a name="controls-with-variable-patterns"></a>変数パターンを持つコントロール  
 一部のコントロール型は、状態やコントロールの使用方法に応じた複数のパターンをサポートしています。 変数パターンを持つコントロールの例としては、リスト ビュー (サムネイル、タイル、アイコン、リスト、詳細)、 [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] グラフ (円、線、横棒、式を使用するセル値)、 [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)]のドキュメント領域 (標準、Web レイアウト、アウトライン、印刷レイアウト、印刷プレビュー)、 [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] スキンなどがあります。  
  
 カスタム コントロール型を実装するコントロールは、機能を表すために必要なコントロール パターンの任意のセットを持つことができます。  
  
## <a name="see-also"></a>関連項目

- [UI オートメーション コントロール パターン](../../../docs/framework/ui-automation/ui-automation-control-patterns.md)
- [UI オートメーション テキスト パターン](../../../docs/framework/ui-automation/ui-automation-text-pattern.md)
- [UI オートメーションを使用したコントロールの呼び出し](../../../docs/framework/ui-automation/invoke-a-control-using-ui-automation.md)
- [UI オートメーションを使用した、チェック ボックスのトグル状態の取得](../../../docs/framework/ui-automation/get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [UI オートメーション クライアントのコントロール パターン マッピング](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)
- [TextPattern の挿入テキストのサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText)
- [TextPattern の検索と選択のサンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/FindText)
- [InvokePattern、ExpandCollapsePattern、および TogglePattern サンプル](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InvokePattern)
