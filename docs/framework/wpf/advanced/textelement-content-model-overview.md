---
title: TextElement コンテンツ モデルの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- documents [WPF], flow documents
- TextElement content model [WPF]
- flow content elements [WPF], TextElement content model
ms.assetid: d0a7791c-b090-438c-812f-b9d009d83ee9
ms.openlocfilehash: ddb2613dc924424b5f4b9d90f06d44b45b7b5e77
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186905"
---
# <a name="textelement-content-model-overview"></a>TextElement コンテンツ モデルの概要
このコンテンツ モデルの概要では、 でサポート<xref:System.Windows.Documents.TextElement>されるコンテンツについて説明します。 クラス<xref:System.Windows.Documents.Paragraph>は の型です<xref:System.Windows.Documents.TextElement>。 コンテンツ モデルは、他のオブジェクトや要素に含めることのできるオブジェクトや要素を記述します。 この概要は、 から派生したオブジェクトに使用される<xref:System.Windows.Documents.TextElement>コンテンツ モデルをまとめたものです。 詳細については、「[フロードキュメントの概要](flow-document-overview.md)」を参照してください。  

<a name="text_element_classes"></a>
## <a name="content-model-diagram"></a>コンテンツ モデルの図  
 次の図は、派生<xref:System.Windows.Documents.TextElement>クラスのコンテンツ モデルと、他の`TextElement`非クラスがこのモデルにどのように適合するかをまとめます。  
  
 ![ダイアグラム: フロー コンテンツ コンテインメント スキーマ](./media/flow-content-schema.png "Flow_Content_Schema")  
  
 前の図からわかるように、要素に対して許可される子は、クラスが<xref:System.Windows.Documents.Block>クラスから派生しているかクラス<xref:System.Windows.Documents.Inline>であるかによって決まるわけではありません。 <xref:System.Windows.Documents.Span>たとえば、a <xref:System.Windows.Documents.Inline>(派生クラス) には子要素のみを<xref:System.Windows.Documents.Inline>含めることができますが<xref:System.Windows.Documents.Figure>、a (派生<xref:System.Windows.Documents.Inline>クラスも) 子要素のみを<xref:System.Windows.Documents.Block>持つことができます。 そのため、どの要素を別の要素に含めることができるかをすばやく判断するには、図が役立ちます。 例として、図を使用して<xref:System.Windows.Controls.RichTextBox>、 のフロー コンテンツの構築方法を決定してみましょう。  
  
1. A<xref:System.Windows.Controls.RichTextBox>には<xref:System.Windows.Documents.FlowDocument>、派生オブジェクトを含める必要<xref:System.Windows.Documents.Block>があるが、 上の図に対応するセグメントを次に示します。  
  
     ![ダイアグラム: RichTextBox コンテインメント規則](./media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")  
  
     この段階では、マークアップは次のようになります。  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
2. 図によると、 <xref:System.Windows.Documents.Block> 、 、<xref:System.Windows.Documents.Paragraph><xref:System.Windows.Documents.Section>および<xref:System.Windows.Documents.Table><xref:System.Windows.Documents.List>を含む複数の要素を選択できます<xref:System.Windows.Documents.BlockUIContainer>(前の図のブロック派生クラスを参照)。 私たちが欲しいとしましょう<xref:System.Windows.Documents.Table>. 前の図によると、<xref:System.Windows.Documents.Table>に含まれる<xref:System.Windows.Documents.TableRowGroup><xref:System.Windows.Documents.TableRow>要素が含まれています。 <xref:System.Windows.Documents.TableCell> <xref:System.Windows.Documents.Block> 次は、前の図から<xref:System.Windows.Documents.Table>取得した対応するセグメントです。  
  
     ![図: テーブルの親&#47;子スキーマ](./media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")  
  
     対応するマークアップは次のとおりです。  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
3. 繰り返しになります<xref:System.Windows.Documents.Block>が、 の下に<xref:System.Windows.Documents.TableCell>1 つ以上の要素が必要です。 簡単にするために、セル内にいくつかのテキストを配置することにします。 これを行うには、<xref:System.Windows.Documents.Paragraph><xref:System.Windows.Documents.Run>要素を持つ を使用します。 次に示す図の対応する<xref:System.Windows.Documents.Paragraph>セグメントは、<xref:System.Windows.Documents.Inline>要素を取得でき<xref:System.Windows.Documents.Run>、(<xref:System.Windows.Documents.Inline>要素) はプレーン テキストしか取ることができないことを示しています。  
  
     ![図: 段落の親&#47;子スキーマ](./media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")  
  
     ![図: 実行用&#47;親子スキーマ](./media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")  
  
 例全体をマークアップで次に示します。  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="Using_the_Content_Property"></a>
## <a name="working-with-textelement-content-programmatically"></a>TextElement のコンテンツをプログラムで操作する  
 の内容<xref:System.Windows.Documents.TextElement>はコレクションによって構成されるため、オブジェクトの<xref:System.Windows.Documents.TextElement>内容をプログラムで操作するには、これらのコレクションを操作します。 派生クラスで使用される<xref:System.Windows.Documents.TextElement>3 つの異なるコレクションがあります。  
  
- <xref:System.Windows.Documents.InlineCollection>: 要素のコレクション<xref:System.Windows.Documents.Inline>を表します。 <xref:System.Windows.Documents.InlineCollection> は、<xref:System.Windows.Documents.Paragraph>、<xref:System.Windows.Documents.Span>、<xref:System.Windows.Controls.TextBlock> の要素の使用できる子コンテンツを定義します。  
  
- <xref:System.Windows.Documents.BlockCollection>: 要素のコレクション<xref:System.Windows.Documents.Block>を表します。 <xref:System.Windows.Documents.BlockCollection> は <xref:System.Windows.Documents.FlowDocument>、<xref:System.Windows.Documents.Section>、<xref:System.Windows.Documents.ListItem>、<xref:System.Windows.Documents.TableCell>、<xref:System.Windows.Documents.Floater>、<xref:System.Windows.Documents.Figure> 要素で許容される子コンテンツを定義します。  
  
- <xref:System.Windows.Documents.ListItemCollection>: 順序付きまたは順序<xref:System.Windows.Documents.List>なしの特定のコンテンツ項目を表すフロー コンテンツ要素。  
  
 これらのコレクションの操作 (項目の追加または削除) は、**インライン**、**ブロック**、および**ListItems**のそれぞれのプロパティを使用して行うことができます。 次の例は **、Inlines**プロパティを使用して Span の内容を操作する方法を示しています。  
  
> [!NOTE]
> Table では、コンテンツの操作にいくつかのコレクションが使用されますが、これらのコレクションについてはここでは取り上げません。 詳細については、「[テーブルの概要](table-overview.md)」を参照してください。  
  
 次の例では、新<xref:System.Windows.Documents.Span>しいオブジェクトを作成し、`Add`メソッドを使用して 2 つのテキスト実行を<xref:System.Windows.Documents.Span>コンテンツの子として追加します。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
 次の例では、新<xref:System.Windows.Documents.Run>しい要素を作成し、その要素を<xref:System.Windows.Documents.Span>.  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
 次の例では、 の<xref:System.Windows.Documents.Inline>最後の要素<xref:System.Windows.Documents.Span>を削除します。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 次の例では、すべてのコンテンツ (<xref:System.Windows.Documents.Inline>要素) を<xref:System.Windows.Documents.Span>から消去します。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
<a name="Types_that_Share_this_Content_Model"></a>
## <a name="types-that-share-this-content-model"></a>このコンテンツ モデルを共有する種類  
 次の型は<xref:System.Windows.Documents.TextElement>クラスから継承され、この概要で説明されている内容を表示するために使用できます。  
  
 <xref:System.Windows.Documents.Bold>, <xref:System.Windows.Documents.Figure>, <xref:System.Windows.Documents.Floater>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Documents.InlineUIContainer>, <xref:System.Windows.Documents.Italic>, <xref:System.Windows.Documents.LineBreak>, <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Run>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Span>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.Underline>.  
  
 このリストには、Windows SDK で配布される非抽象型のみが含まれていることに注意してください。 から<xref:System.Windows.Documents.TextElement>継承する他の型を使用できます。  
  
<a name="Types_that_Can_Contain_ContentControl_Objects"></a>
## <a name="types-that-can-contain-textelement-objects"></a>TextElement オブジェクトを含むことのできる型  
 [WPF コンテンツ モデル](../controls/wpf-content-model.md)を参照してください。  
  
## <a name="see-also"></a>関連項目

- [Blocks プロパティを介して FlowDocument を操作する](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Blocks プロパティを介してフロー コンテンツ要素を操作する](how-to-manipulate-flow-content-elements-through-the-blocks-property.md)
- [Blocks プロパティを介して FlowDocument を操作する](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Columns プロパティによってテーブルの列を操作する](how-to-manipulate-table-columns-through-the-columns-property.md)
- [RowGroups プロパティを介してテーブルの行グループを操作する](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
