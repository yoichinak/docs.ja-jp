---
title: UI オートメーション フラグメント プロバイダーでのナビゲーションの有効化
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UI Automation, enabling navigation in provider
- navigation, enabling in UI Automation provider
ms.assetid: 3cb6092a-58c9-4ca0-84a5-0e54d5d00a0d
ms.openlocfilehash: e97494e01a81ad75820cd3cffa51b5a508152355
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59175995"
---
# <a name="enable-navigation-in-a-ui-automation-fragment-provider"></a>UI オートメーション フラグメント プロバイダーでのナビゲーションの有効化
> [!NOTE]
>  このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージド <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 に関する最新情報については[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]を参照してください[Windows Automation API:UI オートメーション](https://go.microsoft.com/fwlink/?LinkID=156746)します。  
  
 このトピックのコード例では、フラグメント内の要素に対して UI オートメーション プロバイダーでのナビゲーションを有効にする方法を示します。  
  
## <a name="example"></a>例  
 次のコード例では、リスト内のリスト項目に対して <xref:System.Windows.Automation.Provider.IRawElementProviderFragment.Navigate%2A> を実装しています。 親要素はリスト ボックス要素で、兄弟要素はそのリスト コレクション内の他の項目です。 このメソッドは正しくない方向の場合に `null` (Visual Basic では`Nothing` ) を返します。このケースでは、 <xref:System.Windows.Automation.Provider.NavigateDirection.FirstChild> と <xref:System.Windows.Automation.Provider.NavigateDirection.LastChild>がこれに相当します (要素に子がないため)。  
  
 [!code-csharp[UIAFragmentProvider_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListItemFragment.cs#103)]
 [!code-vb[UIAFragmentProvider_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListItemFragment.vb#103)]  
  
## <a name="see-also"></a>関連項目

- [UI オートメーション プロバイダーの概要](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)
- [サーバー側 UI オートメーション プロバイダーの実装](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
