---
title: '方法: TreeView のパフォーマンスを改善する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TreeView control [WPF], improving the performance
ms.assetid: b792c740-cf2b-4da8-8ba8-3d2e5a821874
ms.openlocfilehash: de1b46da2a7c6c3db0c0c19cdbb654fcf2fbbd6c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59153440"
---
# <a name="how-to-improve-the-performance-of-a-treeview"></a>方法: TreeView のパフォーマンスを改善する
場合、<xref:System.Windows.Controls.TreeView>多くの項目を含むの読み込みにかかる時間は、ユーザー インターフェイスで大きな遅延を引き起こす可能性があります。 設定して、読み込み時間を向上させることができます、`VirtualizingStackPanel.IsVirtualizing`添付プロパティを`true`します。  UI は、ユーザーがスクロールときに応答に時間がかかる場合があります、<xref:System.Windows.Controls.TreeView>をマウス ホイールを使用するかスクロール バーのつまみをドラッグします。 パフォーマンスを向上させることができます、<xref:System.Windows.Controls.TreeView>を設定してユーザーがスクロールすると、`VirtualizingStackPanel.VirtualizationMode`添付プロパティを<xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>します。  
  
## <a name="example"></a>例  
  
## <a name="description"></a>説明  
次の例では、作成、<xref:System.Windows.Controls.TreeView>設定、`VirtualizingStackPanel.IsVirtualizing`添付プロパティを true に、`VirtualizingStackPanel.VirtualizationMode`添付プロパティを<xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>そのパフォーマンスを最適化します。  
  
## <a name="code"></a>コード  
 [!code-xaml[RecycleItemContainerShippets#VirtualizingTreeView](~/samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizingtreeview)]  
  
 次の例では、前の例を使用してデータを示します。  
  
 [!code-csharp[RecycleItemContainerShippets#TreeViewData](~/samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#treeviewdata)]
 [!code-vb[RecycleItemContainerShippets#TreeViewData](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#treeviewdata)]  
  
## <a name="see-also"></a>関連項目

- [コントロール](../advanced/optimizing-performance-controls.md)
