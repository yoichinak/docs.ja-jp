---
title: '方法: コレクションにバインドして選択に基づく情報を表示する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data collections [WPF], selecting data for views
- data binding [WPF], creating views of data collections
- data binding [WPF], selecting data for views
- data binding [WPF], binding to collections
ms.assetid: 952a7d76-dd29-49e5-86f5-32c4530e70eb
ms.openlocfilehash: 5ceda723ad982fc788e8d0b81e6cf92975790682
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57360395"
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a>方法: コレクションにバインドして選択に基づく情報を表示する
データ バインドがある場合、単純なマスター詳細シナリオで<xref:System.Windows.Controls.ItemsControl>など、<xref:System.Windows.Controls.ListBox>します。 ユーザー選択に基づいて、選択した項目の詳細についてを表示します。 この例では、このシナリオを実装する方法を示します。  
  
## <a name="example"></a>例  
 この例で`People`は、<xref:System.Collections.ObjectModel.ObservableCollection%601>の`Person`クラス。 これは、`Person`クラスには、3 つのプロパティが含まれています: `FirstName`、 `LastName`、および`HomeTown`、すべての種類の`string`します。  
  
 [!code-xaml[CollectionBinding#Source](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 <xref:System.Windows.Controls.ContentControl> 、次を使用して<xref:System.Windows.DataTemplate>を定義する方法の情報を`Person`が表示されます。  
  
 [!code-xaml[CollectionBinding#DetailTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 この例の生成のスクリーン ショットを次に示します。 <xref:System.Windows.Controls.ContentControl>選択されているユーザーの他のプロパティを示しています。  
  
 ![コレクションへのバインディング](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")  
  
 この例では、2 つの処理は次のとおりです。  
  
1.  <xref:System.Windows.Controls.ListBox>と<xref:System.Windows.Controls.ContentControl>を同じソースにバインドします。 <xref:System.Windows.Data.Binding.Path%2A>両方のコントロールは、コレクション オブジェクト全体にバインドするため、どちらのバインドのプロパティが指定されていません。  
  
2.  設定する必要があります、<xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A>プロパティを`true`これが機能します。 このプロパティ設定によって、選択した項目として常に設定されている、<xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>します。 また場合、<xref:System.Windows.Controls.ListBox>からデータを取得しますが、<xref:System.Windows.Data.CollectionViewSource>の選択と通貨を自動的に同期されます。  
  
 なお、`Person`オーバーライド、`ToString`メソッドは次の方法です。 既定で、<xref:System.Windows.Controls.ListBox>呼び出し`ToString`バインドのコレクション内の各オブジェクトの文字列表現を表示します。 その理由は各`Person`の最初の名前として表示されます、<xref:System.Windows.Controls.ListBox>します。  
  
 [!code-csharp[CollectionBinding#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a>関連項目
- [階層データでマスター詳細パターンを使用する](how-to-use-the-master-detail-pattern-with-hierarchical-data.md)
- [階層 XML データでマスター詳細パターンを使用する](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [データ バインディングの概要](data-binding-overview.md)
- [データ テンプレートの概要](data-templating-overview.md)
- [方法トピック](data-binding-how-to-topics.md)
