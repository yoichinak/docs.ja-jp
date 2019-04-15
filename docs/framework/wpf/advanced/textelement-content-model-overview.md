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
ms.openlocfilehash: 990642d288481fff8eeef900a86070d54790f151
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59336188"
---
# <a name="textelement-content-model-overview"></a>TextElement コンテンツ モデルの概要
このコンテンツ モデルの概要についてのサポートされているコンテンツを説明します、<xref:System.Windows.Documents.TextElement>します。 <xref:System.Windows.Documents.Paragraph>クラスは、型の<xref:System.Windows.Documents.TextElement>します。 コンテンツ モデルは、他のオブジェクトや要素に含めることのできるオブジェクトや要素を記述します。 派生したオブジェクトに使用するコンテンツ モデルのこの概要を示します<xref:System.Windows.Documents.TextElement>します。 詳細については、次を参照してください。[フロー ドキュメントの概要](flow-document-overview.md)します。  

<a name="text_element_classes"></a>   
## <a name="content-model-diagram"></a>コンテンツ モデルの図  
 次の図から派生したクラスのコンテンツ モデルをまとめたものです<xref:System.Windows.Documents.TextElement>とどのように他の非`TextElement`クラスのこのモデルに適合します。  
  
 ![図に示します。フロー コンテンツ コンテインメント スキーマ](./media/flow-content-schema.png "Flow_Content_Schema")  
  
 前の図からわかるように、要素で許容される子は必ずしも決定されませんからクラスを派生するかどうかによって、<xref:System.Windows.Documents.Block>クラスまたは<xref:System.Windows.Documents.Inline>クラス。 など、 <xref:System.Windows.Documents.Span> (、 <xref:System.Windows.Documents.Inline>-クラスの派生) のみ持つことができます<xref:System.Windows.Documents.Inline>、子要素が、 <xref:System.Windows.Documents.Figure> (も、 <xref:System.Windows.Documents.Inline>-派生クラス) のみ持つことができます<xref:System.Windows.Documents.Block>子要素。 そのため、どの要素を別の要素に含めることができるかをすばやく判断するには、図が役立ちます。 たとえばのフロー コンテンツを構築する方法を決定するみましょう、図を使用する<xref:System.Windows.Controls.RichTextBox>します。  
  
1. A<xref:System.Windows.Controls.RichTextBox>含める必要があります、<xref:System.Windows.Documents.FlowDocument>をさらに含める必要があります、 <xref:System.Windows.Documents.Block>-派生オブジェクト。 上の図に対応するセグメントを次に示します。  
  
     ![図に示します。RichTextBox コンテインメント規則](./media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")  
  
     この段階では、マークアップは次のようになります。  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
2. に従って、ダイアグラムは、いくつか<xref:System.Windows.Documents.Block>要素を含むを<xref:System.Windows.Documents.Paragraph>、 <xref:System.Windows.Documents.Section>、 <xref:System.Windows.Documents.Table>、 <xref:System.Windows.Documents.List>、および<xref:System.Windows.Documents.BlockUIContainer>(前の図の Block の派生クラスを参照してください)。 ここですると、<xref:System.Windows.Documents.Table>します。 上記の図によると、<xref:System.Windows.Documents.Table>が含まれています、<xref:System.Windows.Documents.TableRowGroup>を含む<xref:System.Windows.Documents.TableRow>を含む要素を<xref:System.Windows.Documents.TableCell>要素を含む、 <xref:System.Windows.Documents.Block>-派生オブジェクト。 次に、対応するセグメントの<xref:System.Windows.Documents.Table>上の図から取得されます。  
  
     ![図に示します。親&#47;子テーブルのスキーマ](./media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")  
  
     対応するマークアップは次のとおりです。  
  
     [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
3. ここでも、1 つまたは複数<xref:System.Windows.Documents.Block>要素は、下にある必要がある、<xref:System.Windows.Documents.TableCell>します。 簡単にするために、セル内にいくつかのテキストを配置することにします。 これにを使用して、<xref:System.Windows.Documents.Paragraph>で、<xref:System.Windows.Documents.Run>要素。 示すダイアグラムから対応するセグメントを次に、<xref:System.Windows.Documents.Paragraph>かかることがあります、<xref:System.Windows.Documents.Inline>要素とする、 <xref:System.Windows.Documents.Run> (、<xref:System.Windows.Documents.Inline>要素) プレーン テキストのみを取ることができます。  
  
     ![図に示します。親&#47;段落の子スキーマ](./media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")  
  
     ![図に示します。親&#47;実行子スキーマ](./media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")  
  
 例全体をマークアップで次に示します。  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="Using_the_Content_Property"></a>   
## <a name="working-with-textelement-content-programmatically"></a>TextElement のコンテンツをプログラムで操作する  
 内容を<xref:System.Windows.Documents.TextElement>コレクションの内容をプログラムで操作するため、作成されて<xref:System.Windows.Documents.TextElement>オブジェクトは、これらのコレクションの操作によって行われます。 使用される 3 つの異なるコレクションがある<xref:System.Windows.Documents.TextElement>-クラスを派生します。  
  
-   <xref:System.Windows.Documents.InlineCollection>:<xref:System.Windows.Documents.Inline> 要素のコレクションを表します。 <xref:System.Windows.Documents.InlineCollection> 許容される子のコンテンツを定義、 <xref:System.Windows.Documents.Paragraph>、 <xref:System.Windows.Documents.Span>、および<xref:System.Windows.Controls.TextBlock>要素。  
  
-   <xref:System.Windows.Documents.BlockCollection>:<xref:System.Windows.Documents.Block> 要素のコレクションを表します。 <xref:System.Windows.Documents.BlockCollection> 許容される子のコンテンツを定義、 <xref:System.Windows.Documents.FlowDocument>、 <xref:System.Windows.Documents.Section>、 <xref:System.Windows.Documents.ListItem>、 <xref:System.Windows.Documents.TableCell>、 <xref:System.Windows.Documents.Floater>、および<xref:System.Windows.Documents.Figure>要素。  
  
-   <xref:System.Windows.Documents.ListItemCollection>:順序付きで特定のコンテンツ項目を表すフロー コンテンツ要素を順序付けられていないまたは<xref:System.Windows.Documents.List>します。  
  
 操作することができます (追加または項目を削除) のそれぞれのプロパティを使用してこれらのコレクションから**Inlines**、**ブロック**、および**ListItems**します。 次の例は、Span を使用しての内容を操作する方法を示します、 **Inlines**プロパティ。  
  
> [!NOTE]
>  Table では、コンテンツの操作にいくつかのコレクションが使用されますが、これらのコレクションについてはここでは取り上げません。 詳細については、次を参照してください。[テーブルの概要](table-overview.md)します。  
  
 次の例では、作成、新しい<xref:System.Windows.Documents.Span>オブジェクト、および、使用、`Add`のコンテンツの子として 2 つのテキストを追加するメソッドが実行される、<xref:System.Windows.Documents.Span>します。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesadd)]
 [!code-vb[SpanSnippets#_SpanInlinesAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesadd)]  
  
 次の例では、作成、新しい<xref:System.Windows.Documents.Run>要素の開始位置に挿入し、<xref:System.Windows.Documents.Span>します。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesinsert)]
 [!code-vb[SpanSnippets#_SpanInlinesInsert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesinsert)]  
  
 次の例では、削除、最終<xref:System.Windows.Documents.Inline>内の要素、<xref:System.Windows.Documents.Span>します。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 次の例では、すべての内容をクリア (<xref:System.Windows.Documents.Inline>要素) から、<xref:System.Windows.Documents.Span>します。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
<a name="Types_that_Share_this_Content_Model"></a>   
## <a name="types-that-share-this-content-model"></a>このコンテンツ モデルを共有する種類  
 次の型から継承、<xref:System.Windows.Documents.TextElement>クラスし、この概要で説明した内容を表示するために使用可能性があります。  
  
 <xref:System.Windows.Documents.Bold>, <xref:System.Windows.Documents.Figure>, <xref:System.Windows.Documents.Floater>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Documents.InlineUIContainer>, <xref:System.Windows.Documents.Italic>, <xref:System.Windows.Documents.LineBreak>, <xref:System.Windows.Documents.List>, <xref:System.Windows.Documents.ListItem>, <xref:System.Windows.Documents.Paragraph>, <xref:System.Windows.Documents.Run>, <xref:System.Windows.Documents.Section>, <xref:System.Windows.Documents.Span>, <xref:System.Windows.Documents.Table>, <xref:System.Windows.Documents.Underline>.  
  
 この一覧にと共に配布非抽象型のみが含まれることに注意してください、[!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]します。 継承する他の種類を使用することがあります<xref:System.Windows.Documents.TextElement>します。  
  
<a name="Types_that_Can_Contain_ContentControl_Objects"></a>   
## <a name="types-that-can-contain-textelement-objects"></a>TextElement オブジェクトを含むことのできる型  
 参照してください[WPF コンテンツ モデル](../controls/wpf-content-model.md)します。  
  
## <a name="see-also"></a>関連項目

- [Blocks プロパティを介して FlowDocument を操作する](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Blocks プロパティを介してフロー コンテンツ要素を操作する](how-to-manipulate-flow-content-elements-through-the-blocks-property.md)
- [Blocks プロパティを介して FlowDocument を操作する](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [Columns プロパティによってテーブルの列を操作する](how-to-manipulate-table-columns-through-the-columns-property.md)
- [RowGroups プロパティを介してテーブルの行グループを操作する](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
