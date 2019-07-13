---
title: '方法: ListBox にデータをバインドする'
ms.date: 03/30/2017
helpviewer_keywords:
- ListBox controls [WPF], binding data to
- data binding [WPF], ListBox control
- binding data [WPF], to ListBox control
ms.assetid: de93a907-709a-44a7-84bf-578b846a3d8b
ms.openlocfilehash: 4dea53a524247d18628b3e7e7b2c06906dced53d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61911158"
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
