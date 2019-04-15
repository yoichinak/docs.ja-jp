---
title: '方法: ビュー内のデータをフィルター処理する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- views [WPF], filtering data
- filtering data in views [WPF]
- data binding [WPF], filtering data in views
ms.assetid: c76e8606-4cc4-45a8-9110-e2ec66dc6afd
ms.openlocfilehash: a31c07e6be26f67cc29813a14745ecf4a83ab98a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59147473"
---
# <a name="how-to-filter-data-in-a-view"></a>方法: ビュー内のデータをフィルター処理する
この例では、ビュー内のデータをフィルター処理する方法を示します。  
  
## <a name="example"></a>例  
 フィルターを作成するには、フィルター処理のロジックを提供するメソッドを定義します。 メソッドは、コールバックとして使用され、型のパラメーターを受け入れる`object`します。 次のメソッドは、すべてを返します、`Order`オブジェクトを`filled`プロパティを"No"に、オブジェクトの残りの部分でフィルター処理を設定します。  
  
 [!code-csharp[SortFilter#2](~/samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#2)]
 [!code-vb[SortFilter#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#2)]  
  
 次の例に示すように、フィルターを適用できます。 この例で`myCollectionView`は、<xref:System.Windows.Data.ListCollectionView>オブジェクト。  
  
 [!code-csharp[SortFilter#Filter](~/samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#filter)]
 [!code-vb[SortFilter#Filter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#filter)]  
  
 フィルター処理を元に戻すには、設定することができます、<xref:System.Windows.Data.CollectionView.Filter%2A>プロパティを`null`:  
  
 [!code-csharp[SortFilter#Unfilter](~/samples/snippets/csharp/VS_Snippets_Wpf/SortFilter/CSharp/Page1.xaml.cs#unfilter)]
 [!code-vb[SortFilter#Unfilter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SortFilter/VisualBasic/Page1.xaml.vb#unfilter)]  
  
 ビューを取得または作成する方法については、次を参照してください。[データ コレクションの既定のビューを取得](how-to-get-the-default-view-of-a-data-collection.md)します。 完全な例では、次を参照してください。[並べ替えとビューのサンプル内の項目をフィルター処理](https://go.microsoft.com/fwlink/?LinkID=160040)します。  
  
 ビュー オブジェクトの場合、<xref:System.Windows.Data.CollectionViewSource>オブジェクトのイベント ハンドラーを設定してフィルター処理のロジックを適用する、<xref:System.Windows.Data.CollectionViewSource.Filter>イベント。 次の例では、`listingDataView`のインスタンスである<xref:System.Windows.Data.CollectionViewSource>します。  
  
 [!code-csharp[DataBindingLab#10](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#10)]
 [!code-vb[DataBindingLab#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#10)]  
  
 この例の実装を次に示します`ShowOnlyBargainsFilter`フィルター イベント ハンドラー。 このイベント ハンドラーを使用して、<xref:System.Windows.Data.FilterEventArgs.Accepted%2A>プロパティをフィルターで除外`AuctionItem`を持つオブジェクトを`CurrentPrice`25 ドル以上。  
  
 [!code-csharp[DataBindingLab#5](~/samples/snippets/csharp/VS_Snippets_Wpf/DataBindingLab/CSharp/MainWindow.xaml.cs#5)]
 [!code-vb[DataBindingLab#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DataBindingLab/VisualBasic/MainWindow.xaml.vb#5)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Data.CollectionView.CanFilter%2A>
- <xref:System.Windows.Data.BindingListCollectionView.CustomFilter%2A>
- [データ バインディングの概要](data-binding-overview.md)
- [ビュー内のデータの並べ替え](how-to-sort-data-in-a-view.md)
- [方法のトピック](data-binding-how-to-topics.md)
