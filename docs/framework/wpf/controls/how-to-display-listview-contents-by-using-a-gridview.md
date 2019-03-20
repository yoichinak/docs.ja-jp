---
title: '方法: GridView を使用して ListView コンテンツを表示する'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView controls [WPF], displaying contents with GridView
- GridView [WPF], displaying ListView contents
ms.assetid: 5bc1e767-ab46-4f14-bd41-3d5d39e1d000
ms.openlocfilehash: 1066869c80bf5bd87d656bcb4994c188ee0e8efc
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2019
ms.locfileid: "58185611"
---
# <a name="how-to-display-listview-contents-by-using-a-gridview"></a>方法: GridView を使用して ListView コンテンツを表示する
この例は、定義する方法を示します、<xref:System.Windows.Controls.GridView>の表示モード、<xref:System.Windows.Controls.ListView>コントロール。  
  
## <a name="example"></a>例  
 表示モードを定義することができます、<xref:System.Windows.Controls.GridView>を指定して<xref:System.Windows.Controls.GridViewColumn>オブジェクト。 次の例は、定義する方法を示します<xref:System.Windows.Controls.GridViewColumn>に対して指定されているデータの内容にバインドするオブジェクト、<xref:System.Windows.Controls.ListView>コントロール。 これは、<xref:System.Windows.Controls.GridView>の例では、3 つを指定します<xref:System.Windows.Controls.GridViewColumn>にマップされているオブジェクト、 `FirstName`、 `LastName`、および`EmployeeNumber`のフィールド、`EmployeeInfoDataSource`として設定されている、<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>の<xref:System.Windows.Controls.ListView>コントロール。  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 次の図は、この例の表示方法を示します。  
  
 ![GridView 出力を含むの ListView を示すスクリーン ショット。](./media/gridview-overview/listview-gridview-output.jpg)  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [ListView の概要](listview-overview.md)
- [GridView の概要](gridview-overview.md)
- [方法トピック](listview-how-to-topics.md)
