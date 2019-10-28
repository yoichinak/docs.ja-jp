---
title: '方法 : LINQ クエリの結果にバインドする'
ms.date: 03/30/2017
helpviewer_keywords:
- running a LINQ query [WPF], bind to results
- binding to LINQ query results [WPF]
ms.assetid: ff2844d9-17ed-4ea6-aab1-5111af0bc684
ms.openlocfilehash: 70f4b439d231d69e5671216bc4e62d0789ce66c7
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920132"
---
# <a name="how-to-bind-to-the-results-of-a-linq-query"></a>方法 : LINQ クエリの結果にバインドする

この例では、LINQ クエリを実行し、その結果にバインドする方法を示します。

## <a name="example"></a>例

次の例では、2つのリストボックスを作成します。 最初のリストボックスには、3つのリスト項目が含まれています。

[!code-xaml[LinqExample#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml#ui)]

最初のリストボックスから項目を選択すると、次のイベントハンドラーが呼び出されます。 この例では、`Tasks` は `Task` オブジェクトのコレクションです。 `Task` クラスには、`Priority`という名前のプロパティがあります。 このイベントハンドラーは、選択した優先順位値を持つ `Task` オブジェクトのコレクションを返す LINQ クエリを実行し、それを <xref:System.Windows.FrameworkElement.DataContext%2A>として設定します。

[!code-csharp[LinqExample#Using](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#using)]
[!code-csharp[LinqExample#Tasks](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#tasks)]
[!code-csharp[LinqExample#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#handler)]

<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> 値が `{Binding}`に設定されているため、2番目のリストボックスはそのコレクションにバインドされます。 その結果、返されたコレクションが (`myTaskTemplate` <xref:System.Windows.DataTemplate>に基づいて) 表示されます。

## <a name="see-also"></a>関連項目

- [XAML でデータをバインディング可能にする](how-to-make-data-available-for-binding-in-xaml.md)
- [コレクションにバインドして選択に基づく情報を表示する](how-to-bind-to-a-collection-and-display-information-based-on-selection.md)
- [WPF Version 4.5 の新機能](../getting-started/whats-new.md)
- [データ バインディングの概要](data-binding-overview.md)
