---
title: "UI オートメーション RangeValue コントロール パターンの実装"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, Range Value
- Range Value control pattern
- UI Automation, Range Value control pattern
ms.assetid: 225feaa4-918e-418b-938e-7389338d0a69
caps.latest.revision: "19"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: a53f5f802d451d7575188d4687b6d88f96ec64fb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-the-ui-automation-rangevalue-control-pattern"></a>UI オートメーション RangeValue コントロール パターンの実装
> [!NOTE]
>  このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージ <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI Automation (Windows のオートメーション API: UI オートメーション)](http://go.microsoft.com/fwlink/?LinkID=156746)」を参照してください。  
  
 このトピックでは、イベントおよびプロパティに関する情報など、 <xref:System.Windows.Automation.Provider.IRangeValueProvider>の実装のためのガイドラインと規則について説明します。 その他のリファレンスへのリンクは、トピックの最後に記載します。  
  
 <xref:System.Windows.Automation.RangeValuePattern> コントロール パターンは、一定の範囲内の値に設定できるコントロールをサポートするために使用します。 このコントロール パターンを実装するコントロールの例については、「 [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)」をご覧ください。  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>実装のガイドラインと規則  
 Range Value コントロール パターンを実装する場合は、次のガイドラインと規則に留意してください。  
  
-   コントロールでは、ロケールまたはユーザー設定に基づいてサポートされているプロパティを再調整できます。 たとえば、温度計コントロールを、華氏または摂氏で温度を表示するように設定できます。  
  
-   進行状況バーやスライダーなどのあいまいな範囲の値を持つコントロールでは、それらの値を正規化する必要があります。  
  
 ![進行状況バーです。] (../../../docs/framework/ui-automation/media/uia-rangevaluepattern-progress-bar.PNG "UIA_RangeValuePattern_Progress_Bar")  
値が整数型で、最小値と最大値のプロパティ値がそれぞれ 0 と 100 に正規化された進行状況バーの例  
  
<a name="Required_Members_for_the_IRangeValueProvider"></a>   
## <a name="required-members-for-irangevalueprovider"></a>IRangeValueProvider の必須メンバー  
  
|必須メンバー|メンバーの型|ノート|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty>|プロパティ|なし|  
|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty>|プロパティ|なし|  
|<xref:System.Windows.Automation.RangeValuePattern.LargeChangeProperty>|プロパティ|なし|  
|<xref:System.Windows.Automation.RangeValuePattern.SmallChangeProperty>|プロパティ|なし|  
|<xref:System.Windows.Automation.RangeValuePattern.MaximumProperty>|プロパティ|なし|  
|<xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>|プロパティ|なし|  
|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A>|メソッド|なし|  
  
 このコントロール パターンには、関連するイベントがありません。  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>例外  
 プロバイダーは、次の例外をスローする必要があります。  
  
|例外の種類|状態|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.RangeValuePattern.SetValue%2A> は、 <xref:System.Windows.Automation.RangeValuePattern.MaximumProperty> より大きい値または <xref:System.Windows.Automation.RangeValuePattern.MinimumProperty>より小さい値で呼び出されます。|  
  
## <a name="see-also"></a>参照  
 [UI Automation コントロール パターンの概要](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [UI オートメーション プロバイダーでのコントロール パターンのサポート](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [クライアントの UI オートメーション コントロール パターン](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [UI Automation ツリーの概要](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [UI オートメーションにおけるキャッシュの使用](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
