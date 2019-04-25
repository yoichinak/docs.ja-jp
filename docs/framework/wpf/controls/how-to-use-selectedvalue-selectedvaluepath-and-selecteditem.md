---
title: '方法: SelectedValue、SelectedValuePath、および SelectedItem を使用する'
ms.date: 03/30/2017
helpviewer_keywords:
- TreeView control [WPF], SelectedValue properties
- Control class [WPF], SelectedItem properties
- Control class [WPF], TreeView properties
- Control class [WPF], SelectedValue properties
- TreeView control [WPF], SelectedItem properties
- SelectedValue [WPF], SelectedValuePath properties
- TreeView control [WPF], SelectedValuePath properties
- Control class [WPF], SelectedValuePath properties
- SelectedValue [WPF], SelectedItem properties
ms.assetid: 2fc92ad4-f02c-4f89-bbe9-d4978a7af0db
ms.openlocfilehash: d9f7a8f04f53b7d38a49dfef2c947dfa1c2d263d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59169706"
---
# <a name="how-to-use-selectedvalue-selectedvaluepath-and-selecteditem"></a>方法: SelectedValue、SelectedValuePath、および SelectedItem を使用する
この例は、使用する方法を示します、<xref:System.Windows.Controls.TreeView.SelectedValue%2A>と<xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>プロパティの値を指定する、<xref:System.Windows.Controls.TreeView.SelectedItem%2A>の<xref:System.Windows.Controls.TreeView>します。  
  
## <a name="example"></a>例  
 <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>プロパティを指定する方法を提供する、<xref:System.Windows.Controls.TreeView.SelectedValue%2A>の<xref:System.Windows.Controls.TreeView.SelectedItem%2A>で、<xref:System.Windows.Controls.TreeView>します。 <xref:System.Windows.Controls.TreeView.SelectedItem%2A>内のオブジェクトを表す、<xref:System.Windows.Controls.ItemsControl.Items%2A>コレクションと<xref:System.Windows.Controls.TreeView>選択された項目の 1 つのプロパティの値を表示します。 <xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>プロパティの値を決定するために使用されるプロパティへのパスを指定します、<xref:System.Windows.Controls.TreeView.SelectedValue%2A>プロパティ。 このトピックの例では、この概念を示します。  
  
 次の例は、<xref:System.Windows.Data.XmlDataProvider>従業員情報を格納します。  
  
 [!code-xaml[TreeViewSelectedValue#XMLDataProvider](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#xmldataprovider)]  
  
 次の例では、定義、<xref:System.Windows.HierarchicalDataTemplate>を表示する、`EmployeeName`と`EmployeeWorkDay`の`Employee`します。 なお、<xref:System.Windows.HierarchicalDataTemplate>で指定されていない、`EmployeeNumber`テンプレートの一部として。  
  
 [!code-xaml[TreeViewSelectedValue#HierarchicalDataTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#hierarchicaldatatemplate)]  
  
 次の例は、<xref:System.Windows.Controls.TreeView>を使用して、以前に定義された<xref:System.Windows.HierarchicalDataTemplate>設定して、<xref:System.Windows.Controls.TreeView.SelectedValue%2A>プロパティを`EmployeeNumber`します。 選択すると、`EmployeeName`で、 <xref:System.Windows.Controls.TreeView>、<xref:System.Windows.Controls.TreeView.SelectedItem%2A>プロパティが返す、`EmployeeInfo`に、選択した対応するデータ項目`EmployeeName`します。 ただし、ため、<xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>この<xref:System.Windows.Controls.TreeView>に設定されている`EmployeeNumber`、<xref:System.Windows.Controls.TreeView.SelectedValue%2A>に設定されている、`EmployeeNumber`します。  
  
 [!code-xaml[TreeViewSelectedValue#SelectedValuePath](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSelectedValue/CS/Window1.xaml#selectedvaluepath)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.TreeView>
- <xref:System.Windows.Controls.TreeViewItem>
- [TreeView の概要](treeview-overview.md)
- [方法トピック](treeview-how-to-topics.md)
