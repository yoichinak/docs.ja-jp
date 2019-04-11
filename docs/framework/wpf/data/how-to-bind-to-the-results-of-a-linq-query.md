---
title: '方法: LINQ クエリの結果にバインドする'
ms.date: 03/30/2017
helpviewer_keywords:
- running a LINQ query [WPF], bind to results
- binding to LINQ query results [WPF]
ms.assetid: ff2844d9-17ed-4ea6-aab1-5111af0bc684
ms.openlocfilehash: 5464ee9c59a7c99a83774a7535b9b3c422c1d2e1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59185901"
---
# <a name="how-to-bind-to-the-results-of-a-linq-query"></a>方法: LINQ クエリの結果にバインドする
この例では、LINQ クエリを実行し、結果にバインドする方法を示します。  
  
## <a name="example"></a>例  
 次の例では、2 つのリスト ボックスを作成します。 最初のリスト ボックスには、次の 3 つのリスト項目が含まれています。  
  
 [!code-xaml[LinqExample#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml#ui)]  
  
 次のイベント ハンドラーを呼び出す最初のリスト ボックスから項目を選択します。 この例で`Tasks`のコレクションである`Task`オブジェクト。 `Task`クラスという名前のプロパティには`Priority`します。 このイベント ハンドラーのコレクションを返す LINQ クエリを実行する`Task`オブジェクトを選択した優先順位の値を持ちとして設定し、 <xref:System.Windows.FrameworkElement.DataContext%2A>:  
  
 [!code-csharp[LinqExample#Using](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#using)]  
[!code-csharp[LinqExample#Tasks](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#tasks)]  
[!code-csharp[LinqExample#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#handler)]  
  
 2 番目のリスト ボックスがそのコレクションにバインドするため、その<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>値に設定されて`{Binding}`します。 その結果、返されるコレクションが表示されます (に基づいて、 `myTaskTemplate`<xref:System.Windows.DataTemplate>)。  
  
## <a name="see-also"></a>関連項目

- [XAML でデータをバインディング可能にする](how-to-make-data-available-for-binding-in-xaml.md)
- [コレクションにバインドして選択に基づく情報を表示する](how-to-bind-to-a-collection-and-display-information-based-on-selection.md)
- [WPF Version 4.5 の新機能](../getting-started/whats-new.md)
- [データ バインディングの概要](data-binding-overview.md)
- [方法のトピック](data-binding-how-to-topics.md)
