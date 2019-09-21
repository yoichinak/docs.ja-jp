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
ms.openlocfilehash: 21df7228f8dca884c5f36be23ae1aced7b31cc9a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942214"
---
# <a name="textelement-content-model-overview"></a>TextElement コンテンツ モデルの概要
このコンテンツモデルの概要では、 <xref:System.Windows.Documents.TextElement>でサポートされるコンテンツについて説明します。 クラスは、の<xref:System.Windows.Documents.TextElement>型です。 <xref:System.Windows.Documents.Paragraph> コンテンツ モデルは、他のオブジェクトや要素に含めることのできるオブジェクトや要素を記述します。 この概要では、から<xref:System.Windows.Documents.TextElement>派生したオブジェクトに使用するコンテンツモデルの概要を示します。 詳細については、「[フロードキュメントの概要](flow-document-overview.md)」を参照してください。  

<a name="text_element_classes"></a>   
## <a name="content-model-diagram"></a>コンテンツ モデルの図  
 次の図は、から<xref:System.Windows.Documents.TextElement>派生したクラスのコンテンツモデルと、その他の`TextElement`非クラスがこのモデルにどのように適合するかをまとめたものです。  
  
 ![モデルフローコンテンツコンテインメントスキーマ](./media/flow-content-schema.png "Flow_Content_Schema")  
  
 上の図からわかるように、要素として使用できる子は、クラスがクラス<xref:System.Windows.Documents.Block> <xref:System.Windows.Documents.Inline>またはクラスから派生しているかどうかによって決まるとは限りません。 たとえば<xref:System.Windows.Documents.Span> 、 <xref:System.Windows.Documents.Figure> <xref:System.Windows.Documents.Inline> <xref:System.Windows.Documents.Block> (派生クラス) には子要素のみを含めることができますが、(または派生クラス)には子要素のみを含めることができます。<xref:System.Windows.Documents.Inline> <xref:System.Windows.Documents.Inline> そのため、どの要素を別の要素に含めることができるかをすばやく判断するには、図が役立ちます。 例として、図を使用して、 <xref:System.Windows.Controls.RichTextBox>のフローコンテンツを構築する方法を決定します。  
  
1. には、 <xref:System.Windows.Documents.FlowDocument>から派生したオブジェクトを<xref:System.Windows.Documents.Block>含むが含まれている必要があります。<xref:System.Windows.Controls.RichTextBox> 上の図に対応するセグメントを次に示します。  
  
     ![モデルRichTextBox コンテインメントルール](./media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")  
  
     この段階では、マークアップは次のようになります。  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
2. 図によれば、 <xref:System.Windows.Documents.Block> 、、 <xref:System.Windows.Documents.Table>、 <xref:System.Windows.Documents.Paragraph> <xref:System.Windows.Documents.Section> <xref:System.Windows.Documents.List>、および<xref:System.Windows.Documents.BlockUIContainer>を含むいくつかの要素を選択できます (前の図のブロック派生クラスを参照してください)。 たとえば、を<xref:System.Windows.Documents.Table>使用するとします。 上の図によれば、 <xref:System.Windows.Documents.Table>には<xref:System.Windows.Documents.TableRowGroup> 、 <xref:System.Windows.Documents.TableRow>から派生した<xref:System.Windows.Documents.TableCell> <xref:System.Windows.Documents.Block>オブジェクトを含む要素を含む要素が含まれています。 次に示すのは、前<xref:System.Windows.Documents.Table>の図から取得した対応するセグメントです。  
  
     ![モデル&#47;テーブル](./media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")の親子スキーマ  
  
     対応するマークアップは次のとおりです。  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
3. ここでも、の<xref:System.Windows.Documents.Block> <xref:System.Windows.Documents.TableCell>下に1つ以上の要素が必要です。 簡単にするために、セル内にいくつかのテキストを配置することにします。 これは、 <xref:System.Windows.Documents.Run>要素を持つ<xref:System.Windows.Documents.Paragraph>を使用して実行できます。 次に示す<xref:System.Windows.Documents.Paragraph>のは、が<xref:System.Windows.Documents.Inline>要素を受け取ることができ、( <xref:System.Windows.Documents.Inline> 1 つの要素<xref:System.Windows.Documents.Run> ) はプレーンテキストのみを受け取ることができることを示している、対応するセグメントです。  
  
     ![モデル&#47;段落](./media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")の親子スキーマ  
  
     ![モデル&#47;実行](./media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")の親子スキーマ  
  
 例全体をマークアップで次に示します。  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="Using_the_Content_Property"></a>   
## <a name="working-with-textelement-content-programmatically"></a>TextElement のコンテンツをプログラムで操作する  
 の内容はコレクション<xref:System.Windows.Documents.TextElement>によって構成されるので、プログラムによっ<xref:System.Windows.Documents.TextElement>てオブジェクトの内容を操作するには、これらのコレクションを使用します。 派生クラスで<xref:System.Windows.Documents.TextElement>は、次の3つの異なるコレクションが使用されます。  
  
- <xref:System.Windows.Documents.InlineCollection>:<xref:System.Windows.Documents.Inline> 要素のコレクションを表します。 <xref:System.Windows.Documents.InlineCollection> は、<xref:System.Windows.Documents.Paragraph>、<xref:System.Windows.Documents.Span>、<xref:System.Windows.Controls.TextBlock> の要素の使用できる子コンテンツを定義します。  
  
- <xref:System.Windows.Documents.BlockCollection>:<xref:System.Windows.Documents.Block> 要素のコレクションを表します。 <xref:System.Windows.Documents.BlockCollection> は <xref:System.Windows.Documents.FlowDocument>、<xref:System.Windows.Documents.Section>、<xref:System.Windows.Documents.ListItem>、<xref:System.Windows.Documents.TableCell>、<xref:System.Windows.Documents.Floater>、<xref:System.Windows.Documents.Figure> 要素で許容される子コンテンツを定義します。  
  
- <xref:System.Windows.Documents.ListItemCollection>:順序付けられたまたは順序<xref:System.Windows.Documents.List>付けられていない特定のコンテンツ項目を表すフローコンテンツ要素。  
  
 これらのコレクションの項目を操作 (追加または削除) するには、**インライン**、**ブロック**、および**ListItems**の各プロパティを使用します。 次の例では、**インライン**プロパティを使用してスパンのコンテンツを操作する方法を示します。  
  
> [!NOTE]
> Table では、コンテンツの操作にいくつかのコレクションが使用されますが、これらのコレクションについてはここでは取り上げません。 詳細については、「[テーブルの概要](table-overview.md)」を参照してください。  
  
 次の例では、 <xref:System.Windows.Documents.Span>新しいオブジェクトを作成し、 `Add`メソッドを使用して、 <xref:System.Windows.Documents.Span>2 つのテキストランをのコンテンツの子として追加します。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
 次の例では、 <xref:System.Windows.Documents.Run>新しい要素を作成し、 <xref:System.Windows.Documents.Span>の先頭に挿入します。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
 次の例では、 <xref:System.Windows.Documents.Inline>の<xref:System.Windows.Documents.Span>最後の要素を削除します。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 次の例では、<xref:System.Windows.Documents.Inline> <xref:System.Windows.Documents.Span>からすべての内容 (要素) を削除します。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
<a name="Types_that_Share_this_Content_Model"></a>   
## <a name="types-that-share-this-content-model"></a>このコンテンツ モデルを共有する種類  
 次の型は<xref:System.Windows.Documents.TextElement>クラスから継承し、この概要で説明されている内容を表示するために使用できます。  
  
 <xref:System.Windows.Documents.Bold>, <xref:System.Windows.Documents.Figure>, <xref:System.Windows.Documents.Floater>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Documents.InlineUIContainer>, <xref:System.Windows.Documents.Italic>, <xref:System.Windows.Documents.LineBreak>, <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Run>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Span>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.Underline>.  
  
 この一覧には、 [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]と共に配布される非抽象型のみが含まれていることに注意してください。 を継承<xref:System.Windows.Documents.TextElement>する他の型を使用することもできます。  
  
<a name="Types_that_Can_Contain_ContentControl_Objects"></a>   
## <a name="types-that-can-contain-textelement-objects"></a>TextElement オブジェクトを含むことのできる型  
 「 [WPF コンテンツモデル](../controls/wpf-content-model.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [Blocks プロパティを介して FlowDocument を操作する](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Blocks プロパティを介してフロー コンテンツ要素を操作する](how-to-manipulate-flow-content-elements-through-the-blocks-property.md)
- [Blocks プロパティを介して FlowDocument を操作する](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Columns プロパティによってテーブルの列を操作する](how-to-manipulate-table-columns-through-the-columns-property.md)
- [RowGroups プロパティを介してテーブルの行グループを操作する](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
