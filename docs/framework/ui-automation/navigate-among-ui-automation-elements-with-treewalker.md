---
title: TreeWalker を使用した UI オートメーション要素間の移動
description: TreeWalker クラスを使用して UI オートメーション要素間を移動する方法を示すコード例を参照してください。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes, TreeWalker
- TreeWalker class
- elements, navigating among
- UI Automation, navigating among elements
ms.assetid: afcd21dc-2ffa-48c9-9332-51269f44b7e9
ms.openlocfilehash: e1784862433083f15d600ea2ec39aee2323bbd12
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168015"
---
# <a name="navigate-among-ui-automation-elements-with-treewalker"></a>TreeWalker を使用した UI オートメーション要素間の移動
> [!NOTE]
> このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](/windows/win32/winauto/entry-uiauto-win32)」をご覧ください。  
  
 このトピックには、クラスを使用して要素間を移動する方法を示すコード例が含まれてい [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] <xref:System.Windows.Automation.TreeWalker> ます。  
  
## <a name="example"></a>例  
 次の例では、を使用し <xref:System.Windows.Automation.TreeWalker.GetParent%2A> [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] て、ルート要素 (desktop) が見つかるまでツリーをウォークします。 指定された要素の親ウィンドウである、そのすぐ下にある要素。  
  
 [!code-csharp[UIAFocusTracker_snip#102](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFocusTracker_snip/CSharp/FocusTracker.cs#102)]
 [!code-vb[UIAFocusTracker_snip#102](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFocusTracker_snip/VisualBasic/FocusTracker.vb#102)]  
  
## <a name="example"></a>例  
 次の例では、およびを使用して <xref:System.Windows.Automation.TreeWalker.GetFirstChild%2A> <xref:System.Windows.Automation.TreeWalker.GetNextSibling%2A> 、 <xref:System.Windows.Forms.TreeView> [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] コントロールビュー内にあり、有効になっている要素のサブツリー全体を表示するを作成します。  
  
 [!code-csharp[UIAClient_snip#174](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#174)]
 [!code-vb[UIAClient_snip#174](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#174)]  
  
## <a name="see-also"></a>関連項目

- [UI オートメーション要素の取得](obtaining-ui-automation-elements.md)
