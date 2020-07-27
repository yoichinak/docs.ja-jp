---
title: リスト項目の UI オートメーション要素の検索
description: 項目のインデックスがわかっている場合に、リスト項目の UI オートメーション要素を検索する方法を示す例を参照してください。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- list items, finding elements for
- elements, finding for list items
- UI Automation, finding elements for List items
ms.assetid: c326ad2b-2144-4f64-ae4c-d850c74f95c5
ms.openlocfilehash: ec6464bc0ec504fd34ed113c9bed1a54a7d4eaec
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168408"
---
# <a name="find-a-ui-automation-element-for-a-list-item"></a>リスト項目の UI オートメーション要素の検索
> [!NOTE]
> このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。  
  
 このトピックで <xref:System.Windows.Automation.AutomationElement> は、項目のインデックスがわかっている場合に、リスト内の項目のを取得する方法について説明します。  
  
## <a name="example"></a>例  
 次の例では、指定した項目をリストから取得する2つの方法を示します。1つはを使用し、もう1つ <xref:System.Windows.Automation.TreeWalker> はを使用し <xref:System.Windows.Automation.AutomationElement.FindAll%2A> ます。  
  
 最初の手法は Win32 コントロールではより高速になる傾向がありますが、2番目の方法は Windows Presentation Foundation (WPF) コントロールではより高速です。  
  
 [!code-csharp[UIAClient_snip#184](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#184)]
 [!code-vb[UIAClient_snip#184](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#184)]  
  
## <a name="see-also"></a>関連項目

- [UI オートメーション要素の取得](obtaining-ui-automation-elements.md)
