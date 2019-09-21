---
title: リスト項目の UI オートメーション要素の検索
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- list items, finding elements for
- elements, finding for list items
- UI Automation, finding elements for List items
ms.assetid: c326ad2b-2144-4f64-ae4c-d850c74f95c5
ms.openlocfilehash: 2b9fb1ffe4b20074de66afe6d418a7cf5d39be0c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043714"
---
# <a name="find-a-ui-automation-element-for-a-list-item"></a>リスト項目の UI オートメーション要素の検索
> [!NOTE]
> このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 の最新情報[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]については[、「Windows Automation API:UI オートメーション](https://go.microsoft.com/fwlink/?LinkID=156746)。  
  
 このトピックでは、項目の<xref:System.Windows.Automation.AutomationElement>インデックスがわかっている場合に、リスト内の項目のを取得する方法について説明します。  
  
## <a name="example"></a>例  
 次の例では、指定した項目をリストから取得する2つ<xref:System.Windows.Automation.TreeWalker>の方法を示し<xref:System.Windows.Automation.AutomationElement.FindAll%2A>ます。1つはを使用し、もう1つはを使用します。  
  
 最初の手法はコントロールに対して[!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)]より高速になる傾向がありますが、2番目の方法は Windows Presentation Foundation (WPF) コントロールの方が高速です。  
  
 [!code-csharp[UIAClient_snip#184](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#184)]
 [!code-vb[UIAClient_snip#184](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#184)]  
  
## <a name="see-also"></a>関連項目

- [UI オートメーション要素の取得](obtaining-ui-automation-elements.md)
