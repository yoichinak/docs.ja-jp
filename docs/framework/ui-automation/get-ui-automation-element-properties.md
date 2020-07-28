---
title: UI オートメーション要素のプロパティの取得
description: UI オートメーション要素の現在またはキャッシュされているプロパティを取得する方法については、「」および「例」を参照してください。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties, retrieving
- UI Automation, retrieving properties of elements
ms.assetid: 09576b1a-291f-435c-980e-dee32d899ae1
ms.openlocfilehash: 277822c9d89046bfbad50df16bce83da7dd45b3b
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164102"
---
# <a name="get-ui-automation-element-properties"></a>UI オートメーション要素のプロパティの取得
> [!NOTE]
> このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。  
  
 このトピックでは、要素のプロパティを取得する方法について説明 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] します。  
  
### <a name="get-a-current-property-value"></a>現在のプロパティ値を取得します。  
  
1. 取得するプロパティが含まれているを取得 <xref:System.Windows.Automation.AutomationElement> します。  
  
2. を呼び出す <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> か、 <xref:System.Windows.Automation.AutomationElement.Current%2A> プロパティ構造体を取得して、そのメンバーの1つから値を取得します。  
  
### <a name="get-a-cached-property-value"></a>キャッシュされたプロパティ値を取得する  
  
1. 取得するプロパティが含まれているを取得 <xref:System.Windows.Automation.AutomationElement> します。 プロパティは、で指定されている必要があり <xref:System.Windows.Automation.CacheRequest> ます。  
  
2. を呼び出す <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> か、 <xref:System.Windows.Automation.AutomationElement.Cached%2A> プロパティ構造体を取得して、そのメンバーの1つから値を取得します。  
  
## <a name="example"></a>例  
 次の例は、の現在のプロパティを取得するさまざまな方法を示して <xref:System.Windows.Automation.AutomationElement> います。  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a>関連項目

- [クライアントの UI オートメーション プロパティ](ui-automation-properties-for-clients.md)
- [UI オートメーションにおけるキャッシュの使用](use-caching-in-ui-automation.md)
- [UI オートメーション クライアントにおけるキャッシュ](caching-in-ui-automation-clients.md)
