---
title: '方法: Inlines プロパティを介してフロー コンテンツ要素を操作する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flow content elements [WPF], manipulating through Inlines property
- documents [WPF], manipulating flow Content elements through Inlines property
- Inlines property [WPF], manipulating flow Content elements
- properties [WPF], Inlines [WPF], manipulating flow Content elements
ms.assetid: 510780d2-3da1-4360-8763-7054bda22ea3
ms.openlocfilehash: 2631d088d677c5edb1ae73a3cb40d15bf4beb71f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57361812"
---
# <a name="how-to-manipulate-flow-content-elements-through-the-inlines-property"></a>方法: Inlines プロパティを介してフロー コンテンツ要素を操作する
これらの例では、インライン フロー コンテンツ要素に対して実行できる一般的な操作の一部を示します (および、このような要素のコンテナーなど<xref:System.Windows.Controls.TextBlock>) を通じて、 **Inlines**プロパティ。 このプロパティを使用して項目を追加および削除を<xref:System.Windows.Documents.InlineCollection>します。 フロー コンテンツ要素にその機能、 **Inlines**プロパティが含まれます。  
  
-   <xref:System.Windows.Documents.Bold>  
  
-   <xref:System.Windows.Documents.Hyperlink>  
  
-   <xref:System.Windows.Documents.Italic>  
  
-   <xref:System.Windows.Documents.Paragraph>  
  
-   <xref:System.Windows.Documents.Span>  
  
-   <xref:System.Windows.Documents.Underline>  
  
 使用する例<xref:System.Windows.Documents.Span>フロー コンテンツ要素は、これらの手法はすべての要素やホスト コントロールに適用する<xref:System.Windows.Documents.InlineCollection>コレクション。  
  
## <a name="example"></a>例  
 次の例では、作成、新しい<xref:System.Windows.Documents.Span>オブジェクト、および、使用、**追加**のコンテンツの子として 2 つのテキストを追加するメソッドが実行される、<xref:System.Windows.Documents.Span>します。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
## <a name="example"></a>例  
 次の例では、作成、新しい<xref:System.Windows.Documents.Run>要素の開始位置に挿入し、<xref:System.Windows.Documents.Span>します。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
## <a name="example"></a>例  
 次の例では、最上位レベルの数を取得します。<xref:System.Windows.Documents.Inline>に含まれる要素、<xref:System.Windows.Documents.Span>します。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesCount](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinescount)]
 [!code-vb[SpanSnippets#_SpanInlinesCount](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinescount)]  
  
## <a name="example"></a>例  
 次の例では、削除、最終<xref:System.Windows.Documents.Inline>内の要素、<xref:System.Windows.Documents.Span>します。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
## <a name="example"></a>例  
 次の例では、すべての内容をクリア (<xref:System.Windows.Documents.Inline>要素) から、<xref:System.Windows.Documents.Span>します。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Documents.BlockCollection>
- <xref:System.Windows.Documents.InlineCollection>
- <xref:System.Windows.Documents.ListItemCollection>
- [フロー ドキュメントの概要](flow-document-overview.md)
- [Blocks プロパティを介して FlowDocument を操作する](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Columns プロパティによってテーブルの列を操作する](how-to-manipulate-table-columns-through-the-columns-property.md)
- [RowGroups プロパティを介してテーブルの行グループを操作する](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
