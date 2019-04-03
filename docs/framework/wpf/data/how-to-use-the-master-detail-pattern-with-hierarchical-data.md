---
title: '方法: 階層データでマスター詳細パターンを使用する'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], Master-Detail data paradigm
- Master-Detail data paradigm
ms.assetid: 11429b9e-058d-4084-bfb6-2cf209c8ddf7
ms.openlocfilehash: e18bc7d60b47b083a0b102938634473d85b39882
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/26/2019
ms.locfileid: "58463320"
---
# <a name="how-to-use-the-master-detail-pattern-with-hierarchical-data"></a>方法: 階層データでマスター詳細パターンを使用する
この例では、マスター/詳細シナリオを実装する方法を示します。  
  
## <a name="example"></a>例  
 この例で`LeagueList`のコレクションである`Leagues`します。 各`League`が、`Name`と一連の`Divisions`、および各`Division`名は、一連の`Teams`します。 各`Team`チームの名前します。  
  
 [!code-xaml[MasterDetail#HowTo1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto1)]  
[!code-xaml[MasterDetail#HowTo2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MasterDetail/VisualBasic/Page1.xaml#howto2)]  
  
 次に示すのは、この例のスクリーンショットです。 `Divisions` <xref:System.Windows.Controls.ListBox>の選択項目が自動的に追跡、 `Leagues` <xref:System.Windows.Controls.ListBox>し、対応するデータを表示します。 `Teams` <xref:System.Windows.Controls.ListBox>他の 2 つの選択項目を追跡<xref:System.Windows.Controls.ListBox>コントロール。  
  
 ![マスターを示すスクリーン ショット&#45;詳細のシナリオ例。](./media/how-to-use-the-master-detail-pattern-with-hierarchical-data/databinding-master-detail-scenario.png)  
  
 この例では、2 つの処理は次のとおりです。  
  
1.  3 つ<xref:System.Windows.Controls.ListBox>コントロールは、同じソースにバインドします。 設定する、<xref:System.Windows.Data.Binding.Path%2A>するデータのレベルを指定するバインドのプロパティ、<xref:System.Windows.Controls.ListBox>を表示します。  
  
2.  設定する必要があります、<xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A>プロパティを`true`で、<xref:System.Windows.Controls.ListBox>コントロールを追跡して選択します。 このプロパティ設定によって、選択した項目として常に設定されている、<xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>します。 また場合、<xref:System.Windows.Controls.ListBox>からデータを取得しますが、<xref:System.Windows.Data.CollectionViewSource>の選択と通貨を自動的に同期されます。  
  
 使用する場合に、この手法は若干異なります[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]データ。 例については、次を参照してください。[階層 XML データでマスター詳細パターンを使用して](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)します。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.HierarchicalDataTemplate>
- [コレクションにバインドして選択に基づく情報を表示する](how-to-bind-to-a-collection-and-display-information-based-on-selection.md)
- [データ バインディングの概要](data-binding-overview.md)
- [データ テンプレートの概要](data-templating-overview.md)
- [方法トピック](data-binding-how-to-topics.md)
