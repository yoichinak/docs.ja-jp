---
title: フロー ドキュメントの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- 'documents [WPF], flow documents [WPF], , '
- ', '
- flow documents [WPF]
ms.assetid: ef236a50-d44f-43c8-ba7c-82b0c733c0b7
ms.openlocfilehash: 1dcba034dd934cb0e103cd131fcaa2088e2f93d3
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856151"
---
# <a name="flow-document-overview"></a>フロー ドキュメントの概要

フロー ドキュメントは、表示と読みやすさを最適化するように設計されたドキュメントです。 フロー ドキュメントは、1 つの定義済みのレイアウトに設定するのではなく、ウィンドウのサイズ、デバイスの解像度、省略可能なユーザー設定など、ランタイム変数に基づいてコンテンツを動的に調整したりリフローしたりします。 また、フロー ドキュメントは、改ページ位置の自動修正や列などの高度なドキュメント機能を提供します。 ここでは、フロー ドキュメントの概要およびフロー ドキュメントの作成方法について説明します。

<a name="what_is_a_flow_document"></a>

## <a name="what-is-a-flow-document"></a>フロー ドキュメントとは

フロー ドキュメントは、ウィンドウ サイズ、デバイスの解像度、およびその他の環境変数に応じて "コンテンツをリフロー" するために設計されています。 また、フロー ドキュメントには、検索、読みやすさを最適化するモードの表示、およびフォントのサイズと外観を変更する機能を含むさまざまな組み込み機能があります。 フロー ドキュメントは、主なドキュメントの使用シナリオが読みやすさである場合に最適です。 これに対し、固定ドキュメントは、静的なプレゼンテーションを行うように設計されています。 ソース コンテンツの再現性が重要である場合は、固定ドキュメントが便利です。 さまざまな種類のドキュメントの詳細については、「 [WPF のドキュメント](documents-in-wpf.md)」を参照してください。

さまざまなサイズの複数のウィンドウで表示されるサンプルのフロー ドキュメントを次の図に示します。 表示領域が変わると、コンテンツはスペースを最大限に利用できるようにリフローされます。

![フロー ドキュメントのコンテンツのリフロー](./media/edocs-flowdocument.png "eDocs_FlowDocument")

上のイメージに示すように、フロー コンテンツには、段落、リスト、イメージなどの多くのコンポーネントを含めることができます。 これらのコンポーネントは、マークアップでの要素と手続き型コードでのオブジェクトに対応します。 これらのクラスについては、この概要の「[フロー関連クラス](#flow_related_classes)」で後ほど詳しく説明します。 ここでは、太字のテキストとリストを含む段落で構成されるフロードキュメントを作成する簡単なコード例を示します。

[!code-xaml[FlowOvwSnippets_snip#SimpleFlowExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SimpleFlowExample.xaml#simpleflowexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#SimpleFlowCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/SimpleFlowExample.cs#simpleflowcodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#SimpleFlowCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/SimpleFlowExample.vb#simpleflowcodeonlyexamplewholepage)]

次の図は、このコード スニペットの結果を示したものです。

![スクリーンレンダリングされ]た FlowDocument の例(./media/flow-ovw-first-example.png "Flow_Ovw_First_Example")

この例<xref:System.Windows.Controls.FlowDocumentReader>では、コントロールを使用して、フローコンテンツをホストします。 フローコンテンツホスティングコントロールの詳細については、「[フロードキュメントの種類](#flow_document_types)」を参照してください。 <xref:System.Windows.Documents.Paragraph>、、 <xref:System.Windows.Documents.List> 、および<xref:System.Windows.Documents.Bold>の各要素は、マークアップ内の順序に基づいて、コンテンツの書式設定を制御するために使用されます。 <xref:System.Windows.Documents.ListItem> たとえば、要素は<xref:System.Windows.Documents.Bold>段落内のテキストの一部のみにまたがり、その結果、テキストの一部だけが太字になります。 HTML を使用したことがある場合、これは慣れ親しまれているでしょう。

上の図で強調表示されているように、フロードキュメントにはいくつかの機能が組み込まれています。

- 検索:ユーザーがドキュメント全体のフルテキスト検索を実行できるようにします。

- 表示モード:ユーザーは、1ページ (一度に1ページ) の表示モード、2ページずつ (書籍の読み取り形式) 表示モード、および連続スクロール (制限カラム) 表示モードを選択して、優先表示モードを選択できます。  これらの表示モードの詳細について<xref:System.Windows.Controls.FlowDocumentReaderViewingMode>は、「」を参照してください。

- ページナビゲーションコントロール:ドキュメントの表示モードでページを使用している場合、ページナビゲーションコントロールには、次のページ (下矢印) または前のページ (上矢印) に移動するボタン、および現在のページ番号と総ページ数のインジケーターが含まれます。 ページ間の移動は、キーボードの方向キーを使用して行うこともできます。

- ズーム:ズームコントロールを使用すると、ユーザーは、プラスボタンまたはマイナスボタンをそれぞれクリックすることにより、ズームレベルを増減させることができます。 ズーム コントロールには、ズーム レベルの調整用スライダーも含まれます。 詳細については、「 <xref:System.Windows.Controls.FlowDocumentReader.Zoom%2A> 」を参照してください。

これらの機能は、フロー コンテンツをホストするために使用されるコントロールに基づいて変更できます。 次のセクションでは、さまざまなコントロールについて説明します。

<a name="flow_document_types"></a>

## <a name="flow-document-types"></a>フロー ドキュメントの種類

フロー ドキュメント コンテンツの表示、およびそれがどのように表示されるかは、どのようなオブジェクトがフロー コンテンツをホストするために使用されるかに依存します。 フローコンテンツ<xref:System.Windows.Controls.FlowDocumentReader>の表示をサポートするコントロールには<xref:System.Windows.Controls.RichTextBox>、 <xref:System.Windows.Controls.FlowDocumentPageViewer>、、、および<xref:System.Windows.Controls.FlowDocumentScrollViewer>の4つがあります。 これらのコントロールについて、以下に簡単に説明します。

> [!NOTE]
> <xref:System.Windows.Documents.FlowDocument>は、フローコンテンツを直接ホストするために必要です。このため、 <xref:System.Windows.Documents.FlowDocument>これらのすべての表示コントロールはを使用してフローコンテンツホスティングを有効にします。

### <a name="flowdocumentreader"></a>FlowDocumentReader

<xref:System.Windows.Controls.FlowDocumentReader>には、ユーザーがさまざまな表示モードを動的に選択できるようにする機能が用意されています。これには、シングルページ (一度に1ページ) 表示モード、2ページずつ (書籍読み取り形式) 表示モード、および連続スクロール (制限カラム) 表示モードが含まれます。 これらの表示モードの詳細について<xref:System.Windows.Controls.FlowDocumentReaderViewingMode>は、「」を参照してください。 さまざまな表示<xref:System.Windows.Controls.FlowDocumentPageViewer>モードを動的に切り替える機能が不要な場合は、特定<xref:System.Windows.Controls.FlowDocumentScrollViewer>の表示モードで固定されている軽量のフローコンテンツビューアーを提供します。

### <a name="flowdocumentpageviewer-and-flowdocumentscrollviewer"></a>FlowDocumentPageViewer と FlowDocumentScrollViewer

<xref:System.Windows.Controls.FlowDocumentPageViewer>コンテンツを同時に表示モードで表示します。一方<xref:System.Windows.Controls.FlowDocumentScrollViewer> 、連続スクロールモードでコンテンツを表示します。 と<xref:System.Windows.Controls.FlowDocumentPageViewer>は<xref:System.Windows.Controls.FlowDocumentScrollViewer>どちらも、特定の表示モードに固定されています。 と比較します。これには<xref:System.Windows.Controls.FlowDocumentReaderViewingMode> <xref:System.Windows.Controls.FlowDocumentPageViewer> <xref:System.Windows.Controls.FlowDocumentScrollViewer> <xref:System.Windows.Controls.FlowDocumentReader>、ユーザーがさまざまな表示モード (列挙体によって提供される) を動的に選択できるようにする機能が含まれています。これにより、またはより多くのリソースが消費されます。

既定では、垂直スクロール バーは常に表示され、水平スクロール バーは必要に応じて表示されます。 の<xref:System.Windows.Controls.FlowDocumentScrollViewer>既定の UI には、ツールバー <xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A>は含まれませんが、プロパティを使用して組み込みのツールバーを有効にすることができます。

### <a name="richtextbox"></a>RichTextBox

ユーザーがフロー <xref:System.Windows.Controls.RichTextBox>コンテンツを編集できるようにする場合は、を使用します。 たとえば、ユーザーがテーブル、斜体、太字の書式などを操作できるようにするエディターを作成する場合は、を<xref:System.Windows.Controls.RichTextBox>使用します。 詳細については、 [RichTextBox の概要](../controls/richtextbox-overview.md)を参照してください。

> [!NOTE]
> 内のフローコンテンツ<xref:System.Windows.Controls.RichTextBox>は、他のコントロールに含まれるフローコンテンツとまったく同じようには動作しません。 たとえば、に<xref:System.Windows.Controls.RichTextBox>は列がないため、自動サイズ変更の動作はありません。 また、通常、検索、表示モード、ページナビゲーション、ズームなどのフローコンテンツの組み込み機能は、内<xref:System.Windows.Controls.RichTextBox>では使用できません。

<a name="creating_flow_content"></a>

## <a name="creating-flow-content"></a>フロー コンテンツの作成

フローコンテンツは、テキスト、イメージ、テーブル、また<xref:System.Windows.UIElement>はコントロールなどの派生クラスを含むさまざまな要素で構成される複雑な場合があります。 複雑なフロー コンテンツを作成する方法を理解するには、次の点が重要です。

- **フロー関連のクラス**:フローコンテンツで使用される各クラスには、特定の目的があります。 また、フロー クラス間の階層型の関係により、それらがどのように使用されるかが理解しやすくなっています。 たとえば、 <xref:System.Windows.Documents.Block>クラスから派生したクラスは、他のオブジェクトを格納するために<xref:System.Windows.Documents.Inline>使用されますが、から派生したクラスには、表示されるオブジェクトが含まれます。

- **コンテンツスキーマ**:フロードキュメントには、多数の入れ子になった要素が必要になる場合があります。 コンテンツ スキーマは、使用可能な要素間の親/子リレーションシップを指定します。

以下のセクションでは、これらの各領域について詳しく説明します。

<a name="flow_related_classes"></a>

## <a name="flow-related-classes"></a>フロー関連のクラス

次の図は、フロー コンテンツで最も一般的に使用されるオブジェクトを示します。

![モデルフローコンテンツ要素クラス階層](./media/flow-class-hierarchy.png "Flow_Class_Hierarchy")

フロー コンテンツのために、次の 2 つの重要なカテゴリがあります。

1. **ブロック派生クラス**:"ブロックコンテンツ要素" または "ブロック要素" とも呼ばれます。 を継承<xref:System.Windows.Documents.Block>する要素を使用して、共通の親の下にある要素をグループ化したり、共通の属性をグループに適用したりできます。

2. **インライン派生クラス**:"インラインコンテンツ要素" または "インライン要素" とも呼ばれます。 を<xref:System.Windows.Documents.Inline>継承する要素は、ブロック要素または別のインライン要素内に含まれます。 Inline 要素は、多くの場合、画面にレンダリングされるコンテンツの直接のコンテナーとして使用されます。 たとえば<xref:System.Windows.Documents.Paragraph> 、(ブロック要素) には<xref:System.Windows.Documents.Run> (インライン要素) を含めることができ<xref:System.Windows.Documents.Run>ますが、実際には画面に表示されるテキストが含まれています。

これらの 2 つのカテゴリの各クラスについて、以下に簡単に説明します。

### <a name="block-derived-classes"></a>Block の派生クラス

**Paragraph**

<xref:System.Windows.Documents.Paragraph>は、通常、コンテンツを段落にグループ化するために使用されます。 Paragraph の最も単純かつ一般的な用途は、テキストの段落の作成です。

[!code-xaml[FlowOvwSnippets_snip#ParagraphExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/ParagraphExample.xaml#paragraphexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#ParagraphCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/ParagraphExample.cs#paragraphcodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#ParagraphCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/ParagraphExample.vb#paragraphcodeonlyexamplewholepage)]

ただし、次に示すように、インラインで派生した他の要素を含めることもできます。

**セクション**

<xref:System.Windows.Documents.Section>は、他の<xref:System.Windows.Documents.Block>派生要素を格納するためにのみ使用されます。 格納している要素に対して、既定の書式設定を適用することはありません。 ただし、に設定されている<xref:System.Windows.Documents.Section>プロパティ値は、その子要素に適用されます。 セクションでは、プログラムで子コレクションを反復処理することもできます。 <xref:System.Windows.Documents.Section>は、HTML の\<DIV > タグと同様の方法で使用されます。

次の例では、3つの段落が<xref:System.Windows.Documents.Section>1 つに定義されています。 セクション<xref:System.Windows.Documents.TextElement.Background%2A>のプロパティ値は red であるため、段落の背景色も赤色になります。

[!code-xaml[FlowOvwSnippets_snip#SectionExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SectionExample.xaml#sectionexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#SectionCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/SectionExample.cs#sectioncodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#SectionCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/SectionExample.vb#sectioncodeonlyexamplewholepage)]

**BlockUIContainer**

<xref:System.Windows.Documents.BlockUIContainer>要素<xref:System.Windows.UIElement> (つまり a <xref:System.Windows.Controls.Button>) をブロック派生フローコンテンツに埋め込むことができるようにします。 <xref:System.Windows.Documents.InlineUIContainer>(下記参照) は、インライン派生<xref:System.Windows.UIElement>フローコンテンツに要素を埋め込むために使用されます。 <xref:System.Windows.Documents.BlockUIContainer>これら<xref:System.Windows.Documents.InlineUIContainer>の2つの要素のいずれかに含まれ<xref:System.Windows.UIElement>ている場合を除き、フローコンテンツでを使用する他の方法がないため、とが重要です。

次の例は、要素を使用<xref:System.Windows.Documents.BlockUIContainer>してフロー <xref:System.Windows.UIElement>コンテンツ内のオブジェクトをホストする方法を示しています。

[!code-xaml[SpanSnippets#_BlockUIXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml#_blockuixaml)]

次の図は、この例がどのようにレンダリングされるかを示しています。

![フローコンテンツに埋め込まれている UIElement を示すスクリーンショット。](./media/flow-document-overview/embedded-blockuicontainer.png)

**List**

<xref:System.Windows.Documents.List>は、箇条書きまたは数値のリストを作成するために使用されます。 プロパティを<xref:System.Windows.TextMarkerStyle>列挙値に設定して、リストのスタイルを決定します。 <xref:System.Windows.Documents.List.MarkerStyle%2A> 簡単なリストを作成する方法を次の例に示します。

[!code-xaml[FlowOvwSnippets_snip#ListExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/ListExample.xaml#listexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#ListCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/ListExample.cs#listcodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#ListCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/ListExample.vb#listcodeonlyexamplewholepage)]

> [!NOTE]
> <xref:System.Windows.Documents.List>は、 <xref:System.Windows.Documents.ListItemCollection>を使用して子要素を管理する唯一のフロー要素です。

**テーブル**

<xref:System.Windows.Documents.Table>テーブルを作成するには、を使用します。 <xref:System.Windows.Documents.Table>は<xref:System.Windows.Controls.Grid>要素に似ていますが、より多くの機能を備えているため、リソースのオーバーヘッドが大きくなります。 はであるため<xref:System.Windows.Controls.Grid> <xref:System.Windows.Documents.BlockUIContainer> 、または<xref:System.Windows.Documents.InlineUIContainer>に含まれている場合を除き、フローコンテンツで使用することはできません。 <xref:System.Windows.UIElement> の<xref:System.Windows.Documents.Table>詳細については、「[テーブルの概要](table-overview.md)」を参照してください。

### <a name="inline-derived-classes"></a>Inline の派生クラス

**実行**

<xref:System.Windows.Documents.Run>書式設定されていないテキストを格納するために使用します。 オブジェクトがフロー <xref:System.Windows.Documents.Run>コンテンツで広範囲に使用されることが予想される場合があります。 ただし、マークアップ<xref:System.Windows.Documents.Run>では、要素を明示的に使用する必要はありません。 <xref:System.Windows.Documents.Run>は、コードを使用してフロードキュメントを作成または操作するときに使用する必要があります。 たとえば、次のマークアップでは、最初<xref:System.Windows.Documents.Paragraph>のは<xref:System.Windows.Documents.Run>要素を明示的に指定しますが、2番目は要素を明示的に指定しません。 両方の段落は、同じ出力を生成します。

[!code-xaml[FlowOvwSnippets_snip#RunExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/RunSnippetsExample.xaml#runexample1)]

> [!NOTE]
> .NET Framework 4 <xref:System.Windows.Documents.Run.Text%2A>以降では、 <xref:System.Windows.Documents.Run>オブジェクトのプロパティは依存関係プロパティです。 などのデータソース<xref:System.Windows.Documents.Run.Text%2A> <xref:System.Windows.Controls.TextBlock>にプロパティをバインドできます。 プロパティ<xref:System.Windows.Documents.Run.Text%2A>は、一方向のバインドを完全にサポートします。 プロパティ<xref:System.Windows.Documents.Run.Text%2A>は、を除き、双方向の<xref:System.Windows.Controls.RichTextBox>バインディングもサポートします。 例については、「<xref:System.Windows.Documents.Run.Text%2A?displayProperty=nameWithType>」を参照してください。

**Span**

<xref:System.Windows.Documents.Span>他のインラインコンテンツ要素をまとめてグループ化します。 要素内のコンテンツには、 <xref:System.Windows.Documents.Span>固有のレンダリングは適用されません。 <xref:System.Windows.Documents.Span>ただし、、 、および<xref:System.Windows.Documents.Italic>を含む<xref:System.Windows.Documents.Hyperlink>要素は 、書式設定をテキストに適用します。<xref:System.Windows.Documents.Bold> <xref:System.Windows.Documents.Underline>

テキスト<xref:System.Windows.Documents.Span> <xref:System.Windows.Controls.Button>、要素、およびを含むインラインコンテンツを格納するために使用されるの例を次に示します。 <xref:System.Windows.Documents.Bold>

[!code-xaml[FlowOvwSnippets_snip#SpanExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SpanExample.xaml#spanexamplewholepage)]

次のスクリーンショットは、この例がどのように表示されるかを示しています。

![スクリーンレンダリングされ]た Span の例(./media/flow-spanexample.gif "Flow_SpanExample")

**InlineUIContainer**

<xref:System.Windows.Documents.InlineUIContainer>要素<xref:System.Windows.UIElement> (など<xref:System.Windows.Controls.Button>のコントロール) <xref:System.Windows.Documents.Inline>をコンテンツ要素に埋め込むことができるようにします。 この要素は、上で説明<xref:System.Windows.Documents.BlockUIContainer>したのと同じようにインライン化されています。 次に、を使用<xref:System.Windows.Documents.InlineUIContainer>して<xref:System.Windows.Controls.Button>インライン<xref:System.Windows.Documents.Paragraph>をに挿入する例を示します。

[!code-xaml[FlowOvwSnippets_snip#InlineUIContainerExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/InlineUIContainerExample.xaml#inlineuicontainerexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#InlineUIContainerCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/InlineUIContainerExample.cs#inlineuicontainercodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#InlineUIContainerCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/InlineUIContainerExample.vb#inlineuicontainercodeonlyexamplewholepage)]

> [!NOTE]
> <xref:System.Windows.Documents.InlineUIContainer>マークアップで明示的に使用する必要はありません。 省略した場合、 <xref:System.Windows.Documents.InlineUIContainer>コードがコンパイルされるときにが作成されます。

**Figure および Floater**

<xref:System.Windows.Documents.Figure>と<xref:System.Windows.Documents.Floater>は、プライマリコンテンツフローとは別にカスタマイズできる配置プロパティを持つフロードキュメントにコンテンツを埋め込むために使用されます。 <xref:System.Windows.Documents.Figure>多くの場合、要素は、コンテンツの一部を強調表示または強調したり、メインコンテンツフロー内のサポートイメージやその他のコンテンツをホストしたり、公開通知などの疎関連コンテンツを挿入したりするために使用されます。<xref:System.Windows.Documents.Floater>

次の例は、を<xref:System.Windows.Documents.Figure>テキストの段落に埋め込む方法を示しています。

[!code-xaml[FlowOvwSnippets_snip#FigureExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/FigureExample.xaml#figureexamplewholepage)]

[!code-csharp[FlowOvwSnippets_procedural_snip#FigureCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/FigureExample.cs#figurecodeonlyexamplewholepage)]
[!code-vb[FlowOvwSnippets_procedural_snip#FigureCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/FigureExample.vb#figurecodeonlyexamplewholepage)]

この例がどのように表示されるかを次の図に示します。

![スクリーン図の]例(./media/flow-ovw-figure-example.png "Flow_Ovw_Figure_Example")

<xref:System.Windows.Documents.Figure>と<xref:System.Windows.Documents.Floater>はいくつかの点で異なり、さまざまなシナリオで使用されます。

**Figure:**

- 次の位置に配置できます。水平および垂直のアンカーを設定して、ページ、コンテンツ、列、または段落に対して相対的にドッキングできます。 また、プロパティ<xref:System.Windows.Documents.Figure.HorizontalOffset%2A>とプロパティを<xref:System.Windows.Documents.Figure.VerticalOffset%2A>使用して、任意のオフセットを指定することもできます。

- は、複数の列に対して大きくなります。高さと幅<xref:System.Windows.Documents.Figure>は、ページ、コンテンツ、または列の高さまたは幅の倍数に設定できます。 ページおよびコンテンツの場合は、1 より大きい倍数は指定できない点に注意してください。 たとえば、の<xref:System.Windows.Documents.Figure>幅を "0.5 ページ" または "0.25 コンテンツ" または "2 列" に設定できます。 高さと幅は、絶対ピクセル値で指定することもできます。

- ページのページングを行いません。内のコンテンツが<xref:System.Windows.Documents.Figure> <xref:System.Windows.Documents.Figure>内に収まっていない場合、どのようなコンテンツが表示され、残りのコンテンツは失われます。

**Floater:**

- 配置できません。必要なスペースを確保できる場所に描画されます。 オフセットまたはアンカーを<xref:System.Windows.Documents.Floater>設定することはできません。

- 複数の列にサイズを設定することはできません。既定では<xref:System.Windows.Documents.Floater> 、1つの列にサイズが設定されます。 これには<xref:System.Windows.Documents.Floater.Width%2A> 、絶対ピクセル値に設定できるプロパティがありますが、この値が1列の幅を超える場合は無視され、system.windows.documents.floater> は1つの列にサイズが設定されます。 正しいピクセル幅を設定することにより、1列未満にサイズを変更できますが、サイズ変更は列相対ではないため、"0.5 列" <xref:System.Windows.Documents.Floater>は幅の有効な式ではありません。 <xref:System.Windows.Documents.Floater>高さのプロパティはなく、高さを設定することはできません。高さはコンテンツによって異なります

- <xref:System.Windows.Documents.Floater>ページ指定された幅にあるコンテンツが1列の高さを超えている場合、system.windows.documents.floater> は次の列、次のページなどに分割してページします。

 <xref:System.Windows.Documents.Figure>は、サイズと位置を制御する必要があり、コンテンツが指定されたサイズに適合することを確信する、スタンドアロンコンテンツを配置するのに適した場所です。 <xref:System.Windows.Documents.Floater>は、メインページのコンテンツと同じようにフローする、よりフリーフローのコンテンツを配置するのに適していますが、それとは分離されています。

**LineBreak**

<xref:System.Windows.Documents.LineBreak>フローコンテンツで改行を発生させます。 次の例は、<xref:System.Windows.Documents.LineBreak> の使い方を示しています。

[!code-xaml[FlowOvwSnippets_snip#LineBreakExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/LineBreakExample.xaml#linebreakexamplewholepage)]

次のスクリーンショットは、この例がどのように表示されるかを示しています。

![スクリーンLineBreak の]例(./media/flow-ovw-linebreakexample.png "Flow_Ovw_LineBreakExample")

### <a name="flow-collection-elements"></a>フロー コレクションの要素

上記<xref:System.Windows.Documents.BlockCollection>の多くの例では、と<xref:System.Windows.Documents.InlineCollection>を使用して、プログラムによってフローコンテンツを構築しています。 たとえば、に<xref:System.Windows.Documents.Paragraph>要素を追加するには、次の構文を使用します。

```csharp
myParagraph.Inlines.Add(new Run("Some text"));
```

これ<xref:System.Windows.Documents.Run> により<xref:System.Windows.Documents.Paragraph>、がのに追加されます。<xref:System.Windows.Documents.InlineCollection>  これは、マークアップ内の<xref:System.Windows.Documents.Run>内で見つかっ<xref:System.Windows.Documents.Paragraph>た暗黙的なと同じです。

```xml
<Paragraph>
Some Text
</Paragraph>
```

を使用<xref:System.Windows.Documents.BlockCollection>する例として、次の例では<xref:System.Windows.Documents.Section> 、新しいを作成し、 **add** <xref:System.Windows.Documents.Section>メソッドを使用<xref:System.Windows.Documents.Paragraph>して新しいをコンテンツに追加しています。

[!code-csharp[FlowDocumentSnippets#_SectionBlocksAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksadd)]
[!code-vb[FlowDocumentSnippets#_SectionBlocksAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksadd)]

フロー コレクションに項目を追加できるだけでなく、項目を削除することもできます。  次の例では、 <xref:System.Windows.Documents.Inline>の<xref:System.Windows.Documents.Span>最後の要素を削除します。

[!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
[!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]

次の例では、<xref:System.Windows.Documents.Inline> <xref:System.Windows.Documents.Span>からすべての内容 (要素) を削除します。

[!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
[!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]

フロー コンテンツをプログラムで操作する場合、これらのコレクションを広く活用する可能性があります。

フロー要素が子要素を<xref:System.Windows.Documents.InlineCollection>格納するために<xref:System.Windows.Documents.BlockCollection> (インライン) または (ブロック) を使用するかどうかは、<xref:System.Windows.Documents.Block>親<xref:System.Windows.Documents.Inline>に含めることができる子要素の型 (または) によって異なります。 フロー コンテンツ要素のコンテインメイト規則については、次のセクションのコンテンツ スキーマにまとめます。

> [!NOTE]
> フローコンテンツ ( <xref:System.Windows.Documents.ListItemCollection>) で使用されるコレクションには3つの種類があり<xref:System.Windows.Documents.List>ますが、このコレクションはでのみ使用されます。 また、で<xref:System.Windows.Documents.Table>使用される複数のコレクションがあります。 詳細については、「[テーブルの概要](table-overview.md)」を参照してください。

<a name="content_schema"></a>

## <a name="content-schema"></a>コンテンツ スキーマ

多数のさまざまなフロー コンテンツ要素が指定されると、要素が格納できる子要素の種類を追跡できなくなる可能性があります。 フロー要素のコンテインメイト規則をまとめたものを次の図に示します。 矢印は、使用可能な親/子リレーションシップを表します。

![モデルフローコンテンツコンテインメントスキーマ](./media/flow-content-schema.png "Flow_Content_Schema")

上の図からわかるように、要素に使用できる子は、必ずしも<xref:System.Windows.Documents.Block>要素<xref:System.Windows.Documents.Inline>であるか要素であるかによって決定されるとは限りません。 たとえば<xref:System.Windows.Documents.Span> <xref:System.Windows.Documents.Inline> <xref:System.Windows.Documents.Figure> <xref:System.Windows.Documents.Block> <xref:System.Windows.Documents.Inline> 、(要素) は子要素のみを持つことができ、(または要素) は子要素のみを持つことができます。 <xref:System.Windows.Documents.Inline> そのため、どの要素を別の要素に含めることができるかをすばやく判断するには、図が役立ちます。 例として、図を使用して、 <xref:System.Windows.Controls.RichTextBox>のフローコンテンツを構築する方法を決定します。

**1.** には、 <xref:System.Windows.Documents.FlowDocument>から派生したオブジェクトを<xref:System.Windows.Documents.Block>含むが含まれている必要があります。<xref:System.Windows.Controls.RichTextBox> 上の図でこれに対応する部分を次に示します。

![モデルRichTextBox コンテインメントルール](./media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")

この段階では、マークアップは次のようになります。

[!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]

**2.** 図によれば、 <xref:System.Windows.Documents.Block> 、、 <xref:System.Windows.Documents.Table>、 <xref:System.Windows.Documents.Paragraph> <xref:System.Windows.Documents.Section> <xref:System.Windows.Documents.List>、および<xref:System.Windows.Documents.BlockUIContainer>を含むいくつかの要素を選択できます (上記のブロック派生クラスを参照してください)。 たとえば、を<xref:System.Windows.Documents.Table>使用するとします。 上<xref:System.Windows.Documents.Table>の図によれば、には、 <xref:System.Windows.Documents.TableRow>から派生した<xref:System.Windows.Documents.TableCell> <xref:System.Windows.Documents.Block>オブジェクトを含む要素を含む要素が<xref:System.Windows.Documents.TableRowGroup>含まれています。 次に示すのは、 <xref:System.Windows.Documents.Table>上の図から取得した対応するセグメントです。

![モデル&#47;テーブル](./media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")の親子スキーマ

以下は、これに対応するマークアップです。

[!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]

**3.** ここでも、の<xref:System.Windows.Documents.Block> <xref:System.Windows.Documents.TableCell>下に1つ以上の要素が必要です。 簡単にするために、セル内にいくつかのテキストを配置することにします。 これは、 <xref:System.Windows.Documents.Run>要素を持つ<xref:System.Windows.Documents.Paragraph>を使用して実行できます。 次に示すのは<xref:System.Windows.Documents.Paragraph> 、が<xref:System.Windows.Documents.Inline>要素を受け取ることができ、( <xref:System.Windows.Documents.Inline> 1 つの<xref:System.Windows.Documents.Run>要素) はプレーンテキストのみを受け取ることができることを示している、対応するセグメントです。

![モデル&#47;段落](./media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")の親子スキーマ

![モデル&#47;実行](./media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")の親子スキーマ

以下は、マークアップでの例の全体です。

[!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]

<a name="customizing_text"></a>

## <a name="customizing-text"></a>テキストのカスタマイズ

通常、テキストは、フロー ドキュメントで最も一般的なコンテンツの種類です。 上で導入されたオブジェクトは、テキストをレンダリングする方法のほとんどの側面を制御するために使用できますが、このセクションで説明されるテキストのカスタマイズ用にその他のメソッドがいくつか存在します。

### <a name="text-decorations"></a>文字装飾

文字装飾によって、下線、上線、ベースライン、および取り消し線の効果をテキストに適用できます (下図参照)。 これらの<xref:System.Windows.Documents.Inline.TextDecorations%2A>装飾は<xref:System.Windows.Documents.Inline>、、 <xref:System.Windows.Documents.Paragraph> <xref:System.Windows.Controls.TextBlock>、 、<xref:System.Windows.Controls.TextBox>などの多数のオブジェクトによって公開されるプロパティを使用して追加されます。

<xref:System.Windows.Documents.Paragraph.TextDecorations%2A> の <xref:System.Windows.Documents.Paragraph> プロパティを設定する方法を次の例に示します。

[!code-xaml[InlineSnippets#_Paragraph_TextDecXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InlineSnippets/CSharp/Window1.xaml#_paragraph_textdecxaml)]

[!code-csharp[InlineSnippets#_Paragraph_TextDec](~/samples/snippets/csharp/VS_Snippets_Wpf/InlineSnippets/CSharp/Window1.xaml.cs#_paragraph_textdec)]
[!code-vb[InlineSnippets#_Paragraph_TextDec](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InlineSnippets/visualbasic/window1.xaml.vb#_paragraph_textdec)]

この例の表示結果を次の図に示します。

![スクリーン既定の取り消し線効果]があるテキスト(./media/inline-textdec-strike.png "Inline_TextDec_Strike")

次の図は、上線、**ベースライン**、および**下線**の装飾がそれぞれどのようにレンダリング**されるか**を示しています。

![スクリーン上線の]textdecorator(./media/inline-textdec-over.png "Inline_TextDec_Over")

![スクリーンテキスト](./media/inline-textdec-base.png "Inline_TextDec_Base")に対する既定のベースライン効果

![スクリーン既定の下線効果が]適用されるテキスト(./media/inline-textdec-under.png "Inline_TextDec_Under")

### <a name="typography"></a>タイポグラフィ

<xref:System.Windows.Documents.TextElement>プロパティは<xref:System.Windows.Documents.FlowDocument>、 、、<xref:System.Windows.Controls.TextBox>、などのほとんどのフローに関連するコンテンツによって公開されます。 <xref:System.Windows.Controls.TextBlock> <xref:System.Windows.Documents.TextElement.Typography%2A> このプロパティは、テキストの文字体裁の特性またはバリエーション (つまり、小さい大文字か大きい大文字か、上付き文字と下付き文字の作成など) を制御するために使用されます。

次の例では、を例<xref:System.Windows.Documents.TextElement.Typography%2A>の要素と<xref:System.Windows.Documents.Paragraph>して使用して、属性を設定する方法を示します。

[!code-xaml[TextElementSnippets#_TextElement_TypogXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml#_textelement_typogxaml)]

この例の表示結果を次の図に示します。

![スクリーンタイポグラフィ]を変更したテキスト(./media/textelement-typog.png "TextElement_Typog")

これに対し、既定の文字体裁プロパティを設定した同様の例がどのように表示されるかを次の図に示します。

![スクリーンタイポグラフィ]を変更したテキスト(./media/textelement-typog-default.png "TextElement_Typog_Default")

次の例では、プログラムを<xref:System.Windows.Controls.TextBox.Typography%2A>使用してプロパティを設定する方法を示します。

[!code-csharp[TextElementSnippets#_TextElement_Typog](~/samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml.cs#_textelement_typog)]
[!code-vb[TextElementSnippets#_TextElement_Typog](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextElementSnippets/visualbasic/window1.xaml.vb#_textelement_typog)]

タイポグラフィの詳細については、「 [WPF のタイポグラフィ](typography-in-wpf.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [Text](optimizing-performance-text.md)
- [WPF のタイポグラフィ](typography-in-wpf.md)
- [方法トピック](flow-content-elements-how-to-topics.md)
- [TextElement コンテンツ モデルの概要](textelement-content-model-overview.md)
- [RichTextBox の概要](../controls/richtextbox-overview.md)
- [WPF のドキュメント](documents-in-wpf.md)
- [テーブルの概要](table-overview.md)
- [注釈の概要](annotations-overview.md)
