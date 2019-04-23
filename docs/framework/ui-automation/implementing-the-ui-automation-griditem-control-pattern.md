---
title: UI オートメーション GridItem コントロール パターンの実装
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
ms.openlocfilehash: 932eb0af6afbe958695d5c084d2cb0c0bc188830
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59176619"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a>UI オートメーション GridItem コントロール パターンの実装
> [!NOTE]
>  このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 に関する最新情報については[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]を参照してください[Windows Automation API:UI オートメーション](https://go.microsoft.com/fwlink/?LinkID=156746)します。  
  
 ここでは、プロパティに関する情報など、 <xref:System.Windows.Automation.Provider.IGridItemProvider>を実装するガイドラインと規則について説明します。 その他のリファレンスへのリンクは、概要の最後に記載します。  
  
 <xref:System.Windows.Automation.GridItemPattern> コントロール パターンは、<xref:System.Windows.Automation.Provider.IGridProvider> を実装するコンテナーの個々の子コントロールをサポートするために使用されます。 このコントロール パターンを実装するコントロールの例については、「 [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)」をご覧ください。  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>実装のガイドラインと規則  
 <xref:System.Windows.Automation.Provider.IGridProvider> を実装する場合は、次のガイドラインと規則に留意してください。  
  
-   グリッドの座標は 0 から始まり、左上のセルの座標が (0, 0) です。  
  
-   結合されたセルが報告する <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> および <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> プロパティは、UI オートメーション プロバイダーによって定義された、基になるアンカー セルに基づきます。 通常、これは、最上位の左端の行または列です。  
  
-   <xref:System.Windows.Automation.Provider.IGridItemProvider> は、セルの結合や分割などのアクティブなグリッド操作を提供しません。  
  
-   <xref:System.Windows.Automation.Provider.IGridItemProvider> を実装するコントロールは、一般にキーボードを使用して横断できます (つまり、UI オートメーション クライアントが隣接するコントロールに移動できます)。  
  
<a name="Required_Members_for_IGridItemProvider"></a>   
## <a name="required-members-for-igriditemprovider"></a>IGridItemProvider の必須メンバー  
 <xref:System.Windows.Automation.Provider.IGridItemProvider>の実装には、次のプロパティとメソッドが必要です。  
  
|必須メンバー|メンバーの型|メモ|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|プロパティ|なし|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|プロパティ|なし|  
  
 このコントロール パターンに関連するメソッドまたはイベントはありません。  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>例外  
 このコントロール パターンに関連付けられた例外はありません。  
  
## <a name="see-also"></a>関連項目

- [UI Automation コントロール パターンの概要](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [UI オートメーション プロバイダーでのコントロール パターンのサポート](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [クライアントの UI オートメーション コントロール パターン](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [UI オートメーション Grid コントロール パターンの実装](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md)
- [UI Automation ツリーの概要](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [UI オートメーションにおけるキャッシュの使用](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
