---
title: UI オートメーション Toggle コントロール パターンの実装
ms.date: 03/30/2017
helpviewer_keywords:
- Toggle control pattern
- control patterns, Toggle
- UI Automation, Toggle control pattern
ms.assetid: 3cfe875f-b0c0-413d-9703-5f14e6a1a30e
ms.openlocfilehash: cd14a20920b11cb198cfc91fd9be6ef83ca05c17
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59182157"
---
# <a name="implementing-the-ui-automation-toggle-control-pattern"></a>UI オートメーション Toggle コントロール パターンの実装
> [!NOTE]
>  このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 に関する最新情報については[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]を参照してください[Windows Automation API:UI オートメーション](https://go.microsoft.com/fwlink/?LinkID=156746)します。  
  
 このトピックでは、メソッドおよびプロパティに関する情報など、 <xref:System.Windows.Automation.Provider.IToggleProvider>の実装のためのガイドラインと規則について説明します。 その他のリファレンスへのリンクは、トピックの最後に記載します。  
  
 <xref:System.Windows.Automation.TogglePattern> コントロール パターンは、一連の状態を順番に繰り返し、状態を一度設定したらそれを保持できるコントロールをサポートするために使用します。 このコントロール パターンを実装するコントロールの例については、「 [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)」をご覧ください。  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>実装のガイドラインと規則  
 Toggle コントロール パターンを実装する場合は、次のガイドラインと規則にご留意ください。  
  
-   ボタン、ツール バー ボタン、ハイパーリンクなど、アクティブになったときに状態を保持しないコントロールは、代わりに <xref:System.Windows.Automation.Provider.IInvokeProvider> を実装する必要があります。  
  
-   コントロールは、 <xref:System.Windows.Automation.ToggleState> 、 <xref:System.Windows.Automation.ToggleState.On>、 <xref:System.Windows.Automation.ToggleState.Off> (サポートされている場合) の順にその <xref:System.Windows.Automation.ToggleState.Indeterminate>を繰り返す必要があります。  
  
-   <xref:System.Windows.Automation.TogglePattern> 3 つの状態のチェック ボックスの直接の設定をその適切な繰り返しをせずにまつわる問題のため SetState(newState) メソッドを提供しない<xref:System.Windows.Automation.ToggleState>シーケンス。  
  
-   RadioButton コントロールは <xref:System.Windows.Automation.Provider.IToggleProvider>を実装しません。これは、その正しい状態を順番に繰り返す機能がないためです。  
  
<a name="Required_Members_for_IToggleProvider"></a>   
## <a name="required-members-for-itoggleprovider"></a>IToggleProvider の必須メンバー  
 <xref:System.Windows.Automation.Provider.IToggleProvider>の実装には、次のプロパティとメソッドが必要です。  
  
|必須メンバー|メンバーの型|メモ|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.TogglePattern.Toggle%2A>|メソッド|なし|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>|プロパティ|なし|  
  
 このコントロール パターンには、関連するイベントがありません。  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>例外  
 このコントロール パターンに関連付けられた例外はありません。  
  
## <a name="see-also"></a>関連項目

- [UI オートメーション コントロール パターンの概要](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [UI オートメーション プロバイダーでのコントロール パターンのサポート](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [クライアントの UI オートメーション コントロール パターン](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [UI オートメーションを使用した、チェック ボックスのトグル状態の取得](../../../docs/framework/ui-automation/get-the-toggle-state-of-a-check-box-using-ui-automation.md)
- [UI オートメーション ツリーの概要](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [UI オートメーションにおけるキャッシュの使用](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
