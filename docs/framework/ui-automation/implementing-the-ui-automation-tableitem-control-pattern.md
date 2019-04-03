---
title: UI オートメーション TableItem コントロール パターンの実装
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Table Item
- UI Automation, Table Item control pattern
- TableItem control pattern
ms.assetid: ac178408-1485-436f-8d3e-eee3bf80cb24
ms.openlocfilehash: f5dda4792d09970d9f03a56be226781187cf2a03
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2019
ms.locfileid: "57674550"
---
# <a name="implementing-the-ui-automation-tableitem-control-pattern"></a>UI オートメーション TableItem コントロール パターンの実装
> [!NOTE]
>  このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 に関する最新情報については[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]を参照してください[Windows Automation API:UI オートメーション](https://go.microsoft.com/fwlink/?LinkID=156746)します。  
  
 このトピックでは、イベントおよびプロパティに関する情報など、 <xref:System.Windows.Automation.Provider.ITableItemProvider>の実装のためのガイドラインと規則について説明します。 その他のリファレンスへのリンクは、概要の最後に記載します。  
  
 <xref:System.Windows.Automation.Provider.ITableProvider> を実装するコンテナーの子コントロールをサポートするために、<xref:System.Windows.Automation.TableItemPattern> コントロール パターンが使用されています。 個々のセル機能へのアクセスは、必要な <xref:System.Windows.Automation.Provider.IGridItemProvider> の同時実装によって提供されます。 このコントロール パターンは <xref:System.Windows.Automation.Provider.IGridItemProvider> と同様です。異なる点は、<xref:System.Windows.Automation.Provider.ITableItemProvider> を実装するコントロールは、個々のセルとその行および列情報の間の関係をプログラムによって公開しなければならないことです。 このコントロール パターンを実装するコントロールの例については、「 [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)」をご覧ください。  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>実装のガイドラインと規則  
  
-   関連するグリッド項目の機能を参照してください。 [UI オートメーション GridItem コントロール パターンを実装する](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)します。  
  
<a name="Required_Members_for_ITableItemProvider"></a>   
## <a name="required-members-for-itableitemprovider"></a>ITableItemProvider の必須メンバー  
  
|必須メンバー|メンバーの型|メモ|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetColumnHeaderItems%2A>|メソッド|なし|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider.GetRowHeaderItems%2A>|メソッド|なし|  
  
 このコントロール パターンに関連付けられるプロパティやイベントはありません。  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>例外  
 このコントロール パターンに関連付けられた例外はありません。  
  
## <a name="see-also"></a>関連項目
- [UI Automation コントロール パターンの概要](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [UI オートメーション プロバイダーでのコントロール パターンのサポート](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [クライアントの UI オートメーション コントロール パターン](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [UI オートメーション Table コントロール パターンの実装](../../../docs/framework/ui-automation/implementing-the-ui-automation-table-control-pattern.md)
- [UI オートメーション GridItem コントロール パターンの実装](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)
- [UI Automation ツリーの概要](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [UI オートメーションにおけるキャッシュの使用](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
