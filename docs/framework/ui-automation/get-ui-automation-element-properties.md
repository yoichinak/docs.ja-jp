---
title: UI オートメーション要素のプロパティの取得
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties, retrieving
- UI Automation, retrieving properties of elements
ms.assetid: 09576b1a-291f-435c-980e-dee32d899ae1
ms.openlocfilehash: e3b3b118c3db95f55c67c2b27149734efc8cbea8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968962"
---
# <a name="get-ui-automation-element-properties"></a>UI オートメーション要素のプロパティの取得
> [!NOTE]
> このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 の最新情報[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]については[、「Windows Automation API:UI オートメーション](https://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 このトピックでは、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]要素のプロパティを取得する方法について説明します。  
  
### <a name="get-a-current-property-value"></a>現在のプロパティ値を取得します。  
  
1. 取得する<xref:System.Windows.Automation.AutomationElement>プロパティが含まれているを取得します。  
  
2. を<xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>呼び出すか、 <xref:System.Windows.Automation.AutomationElement.Current%2A>プロパティ構造体を取得して、そのメンバーの1つから値を取得します。  
  
### <a name="get-a-cached-property-value"></a>キャッシュされたプロパティ値を取得する  
  
1. 取得する<xref:System.Windows.Automation.AutomationElement>プロパティが含まれているを取得します。 プロパティは、 <xref:System.Windows.Automation.CacheRequest>で指定されている必要があります。  
  
2. を<xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>呼び出すか、 <xref:System.Windows.Automation.AutomationElement.Cached%2A>プロパティ構造体を取得して、そのメンバーの1つから値を取得します。  
  
## <a name="example"></a>例  
 次の例は、 <xref:System.Windows.Automation.AutomationElement>の現在のプロパティを取得するさまざまな方法を示しています。  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a>関連項目

- [クライアントの UI オートメーション プロパティ](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)
- [UI オートメーションにおけるキャッシュの使用](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
- [UI オートメーション クライアントにおけるキャッシュ](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
