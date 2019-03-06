---
title: '方法: ListBox にデータをバインドする'
ms.date: 03/30/2017
helpviewer_keywords:
- ListBox controls [WPF], binding data to
- data binding [WPF], ListBox control
- binding data [WPF], to ListBox control
ms.assetid: de93a907-709a-44a7-84bf-578b846a3d8b
ms.openlocfilehash: 2cbcb0fb859605c33e2d92559b4a47aa1725472c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372882"
---
# <a name="how-to-bind-a-listbox-to-data"></a>方法: ListBox にデータをバインドする
アプリケーション開発者が作成できる<xref:System.Windows.Controls.ListBox>それぞれのコンテンツを指定することがなくコントロール<xref:System.Windows.Controls.ListBoxItem>とは別にします。 データ バインディングを使用すると、個々 の項目にデータをバインドします。  
  
 次の例を作成する方法を示しています、<xref:System.Windows.Controls.ListBox>を設定する、<xref:System.Windows.Controls.ListBoxItem>というデータ ソースへのデータ バインディングによって要素*色*します。 ここで使用する必要はありません<xref:System.Windows.Controls.ListBoxItem>タグを各項目の内容を指定します。  
  
## <a name="example"></a>例  
 [!code-xaml[ListBoxEvent#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#7)]  
[!code-xaml[ListBoxEvent#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#3)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.Controls.ListBoxItem>
- [コントロール](../advanced/optimizing-performance-controls.md)
