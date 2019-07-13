---
title: '方法: 深度がわからないデータに TreeView をバインドする'
ms.date: 03/30/2017
helpviewer_keywords:
- TreeView control [WPF], binding to data of indeterminate depth
ms.assetid: daddcd74-1b0f-4ffd-baeb-ec934c5e0f53
ms.openlocfilehash: 7da0a121cdb854c787c105c92cec70b7c4b3244e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61911080"
---
# <a name="how-to-bind-a-treeview-to-data-that-has-an-indeterminable-depth"></a>方法: 深度がわからないデータに TreeView をバインドする
バインドに必要な場合がある可能性があります、<xref:System.Windows.Controls.TreeView>深さがわからない場合は、データ ソースにします。  これは、データが再帰的な場所のフォルダーは、フォルダーを含めることができます、ファイル システム、または企業の組織の構造など、本質的に直属の部下として他の従業員の従業員がある場合に発生します。  
  
 データ ソースには、階層化されたオブジェクト モデルが必要です。 たとえば、`Employee`クラスには、従業員の直属の部下である従業員のオブジェクトのコレクションが含まれます。 データは、階層ではない方法で表される、データの階層的な表現をビルドする必要があります。  
  
 設定すると、<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A?displayProperty=nameWithType>プロパティ場合に、<xref:System.Windows.Controls.ItemsControl>が生成されます、 <xref:System.Windows.Controls.ItemsControl> 、各子項目では後で、子<xref:System.Windows.Controls.ItemsControl>同じ<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>親として。 設定する場合など、<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>データ バインドされたプロパティ<xref:System.Windows.Controls.TreeView>、それぞれ<xref:System.Windows.Controls.TreeViewItem>生成された使用されている、<xref:System.Windows.DataTemplate>に割り当てられた、<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>のプロパティ、<xref:System.Windows.Controls.TreeView>します。  
  
 <xref:System.Windows.HierarchicalDataTemplate>を指定することができます、<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>の<xref:System.Windows.Controls.TreeViewItem>、または any <xref:System.Windows.Controls.HeaderedItemsControl>、データ テンプレートにします。 設定すると、 <xref:System.Windows.HierarchicalDataTemplate.ItemsSource%2A?displayProperty=nameWithType> 、プロパティ値である場合に使用、<xref:System.Windows.HierarchicalDataTemplate>が適用されます。 使用して、 <xref:System.Windows.HierarchicalDataTemplate>、再帰的に設定する、<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>各<xref:System.Windows.Controls.TreeViewItem>で、<xref:System.Windows.Controls.TreeView>します。  
  
## <a name="example"></a>例  
 次の例では、バインドする方法、<xref:System.Windows.Controls.TreeView>階層データを使用して、<xref:System.Windows.HierarchicalDataTemplate>を指定する、<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>各<xref:System.Windows.Controls.TreeViewItem>します。  <xref:System.Windows.Controls.TreeView>社内の従業員を表す XML データをバインドします。  各`Employee`要素はその他を含めることができます`Employee`をユーザーに報告を示す要素。 データは再帰的であるため、<xref:System.Windows.HierarchicalDataTemplate>各レベルに適用できます。  
  
 [!code-xaml[TreeViewWithUnknownDepth#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewWithUnknownDepth/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a>関連項目

- [データ バインディングの概要](../data/data-binding-overview.md)
- [データ テンプレートの概要](../data/data-templating-overview.md)
