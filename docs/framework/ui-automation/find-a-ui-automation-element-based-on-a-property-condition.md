---
title: プロパティ条件に基づく UI オートメーション要素の検索
description: プロパティ条件に基づいて UI オートメーション要素を検索します。 特定のプロパティまたはプロパティに基づいて、UI オートメーションツリー内の要素を検索します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- elements, finding by property conditions
- UI Automation, finding elements by property conditions
ms.assetid: 3acaee5a-6ce8-4c3e-81c8-67e59eb74477
ms.openlocfilehash: 5e5fa4fde9049bd87b2722fa9b7d084d96ff6f42
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168438"
---
# <a name="find-a-ui-automation-element-based-on-a-property-condition"></a>プロパティ条件に基づく UI オートメーション要素の検索
> [!NOTE]
> このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。  
  
 このトピックに [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] は、特定のプロパティまたはプロパティに基づいてツリー内の要素を検索する方法を示すコード例が含まれています。  
  
## <a name="example"></a>例  
 次の例では、ツリー内の関心のある要素 (または要素) を識別する一連のプロパティ条件を指定してい <xref:System.Windows.Automation.AutomationElement> ます。 次に、一致するすべての要素の検索が、 <xref:System.Windows.Automation.AutomationElement.FindAll%2A> <xref:System.Windows.Automation.AndCondition> 一致する要素の数を制限する一連のブール演算を組み込むメソッドを使用して実行されます。  
  
> [!NOTE]
> から検索する場合 <xref:System.Windows.Automation.AutomationElement.RootElement%2A> は、直接の子のみを取得するようにしてください。 子孫の検索では、数百または数千の要素を反復処理することがあります。その結果、スタックオーバーフローが発生する可能性があります。 下位レベルの特定の要素を取得しようとする場合、アプリケーション ウィンドウから、または下位レベルのコンテナーから検索を開始する必要があります。  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## <a name="see-also"></a>関連項目

- [InvokePattern と ExpandCollapsePattern のメニュー項目のサンプル](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771636(v=vs.90))
- [UI オートメーション要素の取得](obtaining-ui-automation-elements.md)
- [AutomationID プロパティの使用](use-the-automationid-property.md)
