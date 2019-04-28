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
ms.openlocfilehash: f8e5a7475765bffb76e7b07e81db25b4a62ae038
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61703928"
---
# <a name="flow-document-overview"></a>フロー ドキュメントの概要
フロー ドキュメントは、表示と読みやすさを最適化するように設計されたドキュメントです。 フロー ドキュメントは、1 つの定義済みのレイアウトに設定するのではなく、ウィンドウのサイズ、デバイスの解像度、省略可能なユーザー設定など、ランタイム変数に基づいてコンテンツを動的に調整したりリフローしたりします。 また、フロー ドキュメントは、改ページ位置の自動修正や列などの高度なドキュメント機能を提供します。 ここでは、フロー ドキュメントの概要およびフロー ドキュメントの作成方法について説明します。  

<a name="what_is_a_flow_document"></a>   
## <a name="what-is-a-flow-document"></a>フロー ドキュメントとは  
 フロー ドキュメントは、ウィンドウ サイズ、デバイスの解像度、およびその他の環境変数に応じて "コンテンツをリフロー" するために設計されています。 また、フロー ドキュメントには、検索、読みやすさを最適化するモードの表示、およびフォントのサイズと外観を変更する機能を含むさまざまな組み込み機能があります。 フロー ドキュメントは、主なドキュメントの使用シナリオが読みやすさである場合に最適です。 これに対し、固定ドキュメントは、静的なプレゼンテーションを行うように設計されています。 ソース コンテンツの再現性が重要である場合は、固定ドキュメントが便利です。 参照してください[WPF のドキュメント](documents-in-wpf.md)ドキュメントのさまざまな種類の詳細についてはします。  
  
 さまざまなサイズの複数のウィンドウで表示されるサンプルのフロー ドキュメントを次の図に示します。 表示領域が変わると、コンテンツはスペースを最大限に利用できるようにリフローされます。  
  
 ![フロー ドキュメントのコンテンツのリフロー](./media/edocs-flowdocument.png "eDocs_FlowDocument")  
  
 上のイメージに示すように、フロー コンテンツには、段落、リスト、イメージなどの多くのコンポーネントを含めることができます。 これらのコンポーネントは、マークアップでの要素と手続き型コードでのオブジェクトに対応します。 後でこれらのクラスの詳細の移動、[フロー関連のクラス](#flow_related_classes)この概要のセクション。 ここでは、次の太字のテキストと、一覧の段落で構成されるフロー ドキュメントを作成する単純なコード例に示します。
  
 [!code-xaml[FlowOvwSnippets_snip#SimpleFlowExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SimpleFlowExample.xaml#simpleflowexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#SimpleFlowCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/SimpleFlowExample.cs#simpleflowcodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#SimpleFlowCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/SimpleFlowExample.vb#simpleflowcodeonlyexamplewholepage)]  
  
 次の図は、このコード スニペットの結果を示したものです。  
  
 ![スクリーン ショット:表示される FlowDocument の例](./media/flow-ovw-first-example.png "Flow_Ovw_First_Example")  
  
 この例で、<xref:System.Windows.Controls.FlowDocumentReader>フロー コンテンツをホストするコントロールを使用します。 参照してください[フロー ドキュメントの種類](#flow_document_types)コントロールをホストしているフロー コンテンツの詳細についてはします。 <xref:System.Windows.Documents.Paragraph>、 <xref:System.Windows.Documents.List>、 <xref:System.Windows.Documents.ListItem>、および<xref:System.Windows.Documents.Bold>要素を制御するため、コンテンツの書式設定マークアップ内の順序に基づいています。 たとえば、<xref:System.Windows.Documents.Bold>要素が、段落のテキストの部分のみにまたがって。 その結果、テキストのその部分のみが太字以外。 HTML を使用したことがある場合、これは慣れ親しまれているでしょう。  
  
 上の図で強調表示されている、としては、フロー ドキュメントに組み込まれているいくつかの機能があります。
  
- 検索:ドキュメント全体のフルテキスト検索を実行できます。  
  
- 表示モード:ユーザーは、単一ページ (ページに-、-時に) 表示モード、2 つのページ-で-、-時間 (読書形式) 表示モード、連続したスクロール (ボトムレス) 表示モードなど、適切な表示モードを選択できます。  これらの表示モードの詳細については、次を参照してください。<xref:System.Windows.Controls.FlowDocumentReaderViewingMode>します。  
  
- ページ ナビゲーション コントロール:ドキュメントの表示モードでは、ページを使用する場合にページ ナビゲーション コントロールには、次のページ (下矢印) または前のページ (上向きの矢印) だけでなく、現在のページ番号とページの合計数のインジケーターにジャンプするためのボタンが含まれます。 ページ間の移動は、キーボードの方向キーを使用して行うこともできます。  
  
- ズーム:ズーム コントロールはそれぞれプラスまたはマイナス ボタン、ズーム レベルを増減するユーザーを有効にします。 ズーム コントロールには、ズーム レベルの調整用スライダーも含まれます。 詳細については、「 <xref:System.Windows.Controls.FlowDocumentReader.Zoom%2A> 」を参照してください。  
  
 これらの機能は、フロー コンテンツをホストするために使用されるコントロールに基づいて変更できます。 次のセクションでは、さまざまなコントロールについて説明します。  
  
<a name="flow_document_types"></a>   
## <a name="flow-document-types"></a>フロー ドキュメントの種類  
 フロー ドキュメント コンテンツの表示、およびそれがどのように表示されるかは、どのようなオブジェクトがフロー コンテンツをホストするために使用されるかに依存します。 フロー コンテンツの表示をサポートする 4 つのコントロールがある: <xref:System.Windows.Controls.FlowDocumentReader>、 <xref:System.Windows.Controls.FlowDocumentPageViewer>、 <xref:System.Windows.Controls.RichTextBox>、および<xref:System.Windows.Controls.FlowDocumentScrollViewer>します。 これらのコントロールについて、以下に簡単に説明します。  
  
 **注:** <xref:System.Windows.Documents.FlowDocument>が直接フロー コンテンツをホストする、必要なすべてのこれらのコントロールの表示を使用ため、<xref:System.Windows.Documents.FlowDocument>フロー コンテンツのホスティングを有効にします。
  
### <a name="flowdocumentreader"></a>FlowDocumentReader  
 <xref:System.Windows.Controls.FlowDocumentReader> 単一ページ (ページに-、-時に) 表示モード、2 つのページ-で-、-時間 (読書形式) 表示モード、連続したスクロール (ボトムレス) 表示モードなど、各種の表示モードの間で動的に選択するユーザーを有効にする機能が含まれています。 これらの表示モードの詳細については、次を参照してください。<xref:System.Windows.Controls.FlowDocumentReaderViewingMode>します。 さまざまな表示モードを動的に切り替える機能が必要ない場合<xref:System.Windows.Controls.FlowDocumentPageViewer>と<xref:System.Windows.Controls.FlowDocumentScrollViewer>コンテンツ ビューアーは、特定の表示モードで修正される軽量のフローを提供します。  
  
### <a name="flowdocumentpageviewer-and-flowdocumentscrollviewer"></a>FlowDocumentPageViewer と FlowDocumentScrollViewer  
 <xref:System.Windows.Controls.FlowDocumentPageViewer> コンテンツを時間でのページで表示モードを表示するには、while<xref:System.Windows.Controls.FlowDocumentScrollViewer>コンテンツを連続したスクロール モードで表示します。 両方<xref:System.Windows.Controls.FlowDocumentPageViewer>と<xref:System.Windows.Controls.FlowDocumentScrollViewer>は特定の表示モードに固定されます。 比較する<xref:System.Windows.Controls.FlowDocumentReader>、さまざまな表示モードを動的に選択するユーザーを有効にする機能が含まれています (によって提供される、<xref:System.Windows.Controls.FlowDocumentReaderViewingMode>列挙型) より多くのリソースよりも処理を要するができますが<xref:System.Windows.Controls.FlowDocumentPageViewer>または<xref:System.Windows.Controls.FlowDocumentScrollViewer>します。  
  
 既定では、垂直スクロール バーは常に表示され、水平スクロール バーは必要に応じて表示されます。 既定の UI<xref:System.Windows.Controls.FlowDocumentScrollViewer>ツールバーには含まれません。 ただし、、<xref:System.Windows.Controls.FlowDocumentScrollViewer.IsToolBarVisible%2A>組み込みツールバーを有効にするプロパティを使用できます。  
  
### <a name="richtextbox"></a>RichTextBox  
 使用する、<xref:System.Windows.Controls.RichTextBox>フロー コンテンツを編集するユーザーを許可する場合。 たとえばをユーザーが操作できるようにするエディターを作成する場合などのテーブル、斜体や太字の書式設定など、使用する、<xref:System.Windows.Controls.RichTextBox>します。 参照してください[RichTextBox の概要](../controls/richtextbox-overview.md)詳細についてはします。  
  
 **注:** 内のコンテンツのフローを<xref:System.Windows.Controls.RichTextBox>他のコントロールに含まれるフロー コンテンツとまったく同じように動作しません。 たとえば、列ではありません、<xref:System.Windows.Controls.RichTextBox>のため自動サイズ変更なし動作とします。 また、検索、表示モード、ページ ナビゲーション、ズームなどのフロー コンテンツの通常の組み込みの機能は内で使用できるはできません、<xref:System.Windows.Controls.RichTextBox>します。  
  
<a name="creating_flow_content"></a>   
## <a name="creating-flow-content"></a>フロー コンテンツの作成  
 フロー コンテンツは複雑で、テキスト、イメージ、テーブルを含むさまざまな要素で構成されるとでもできる<xref:System.Windows.UIElement>コントロールなどのクラスを派生します。 複雑なフロー コンテンツを作成する方法を理解するには、次の点が重要です。  
  
- **フローに関連するクラス**:フロー コンテンツで使用される各クラスには、特定の目的があります。 また、フロー クラス間の階層型の関係により、それらがどのように使用されるかが理解しやすくなっています。 などから派生したクラス、<xref:System.Windows.Documents.Block>クラスから派生したときに、その他のオブジェクトを格納するためのクラス<xref:System.Windows.Documents.Inline>表示されているオブジェクトを含めることができます。  
  
- **コンテンツ スキーマ**:フロー ドキュメントには、相当な数の入れ子になった要素が必要なことができます。 コンテンツ スキーマは、使用可能な要素間の親/子リレーションシップを指定します。  
  
 以下のセクションでは、これらの各領域について詳しく説明します。  
  
<a name="flow_related_classes"></a>   
## <a name="flow-related-classes"></a>フロー関連のクラス  
 次の図は、フロー コンテンツで最も一般的に使用されるオブジェクトを示します。  
  
 ![図に示します。フロー コンテンツ要素クラス階層](./media/flow-class-hierarchy.png "Flow_Class_Hierarchy")  
  
 フロー コンテンツのために、次の 2 つの重要なカテゴリがあります。  
  
1. **Block の派生クラス**:「Block コンテンツ要素」または単に「ブロック要素」とも呼ばれます。 継承する要素<xref:System.Windows.Documents.Block>共通の親要素をグループ化またはグループに共通の属性を適用するために使用できます。  
  
2. **Inline の派生クラス**:「Inline コンテンツ要素」または単に「インライン要素」とも呼ばれます。 継承する要素<xref:System.Windows.Documents.Inline>Block 要素または別の Inline 要素に含まれるいずれか。 Inline 要素は、多くの場合、画面にレンダリングされるコンテンツの直接のコンテナーとして使用されます。 たとえば、 <xref:System.Windows.Documents.Paragraph> (Block 要素) を含めることができます、 <xref:System.Windows.Documents.Run> (Inline 要素) が、<xref:System.Windows.Documents.Run>実際に画面に表示されるテキストが含まれています。  
  
 これらの 2 つのカテゴリの各クラスについて、以下に簡単に説明します。  
  
### <a name="block-derived-classes"></a>Block の派生クラス  
 **Paragraph**  
  
 <xref:System.Windows.Documents.Paragraph> 段落にグループの内容を通常に使用されます。 Paragraph の最も単純かつ一般的な用途は、テキストの段落の作成です。  
  
 [!code-xaml[FlowOvwSnippets_snip#ParagraphExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/ParagraphExample.xaml#paragraphexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#ParagraphCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/ParagraphExample.cs#paragraphcodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#ParagraphCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/ParagraphExample.vb#paragraphcodeonlyexamplewholepage)]  
  
 ただし、後述するように他の inline の派生要素をこともできます。 
  
 **セクション**  
  
 <xref:System.Windows.Documents.Section> その他を含める場合にのみ使用されます<xref:System.Windows.Documents.Block>-派生要素。 格納している要素に対して、既定の書式設定を適用することはありません。 ただし、任意のプロパティの値セットを<xref:System.Windows.Documents.Section>その子要素に適用されます。 セクションでは、プログラムで子コレクションを反復処理することもできます。 <xref:System.Windows.Documents.Section> 同様の方法で使用されて、 \<DIV > HTML タグ。  
  
 いずれかで次の例で 3 つの段落が定義されている<xref:System.Windows.Documents.Section>します。 セクションには、 <xref:System.Windows.Documents.TextElement.Background%2A> Red、段落の背景色ではそのためのプロパティの値が赤でも。  
  
 [!code-xaml[FlowOvwSnippets_snip#SectionExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SectionExample.xaml#sectionexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#SectionCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/SectionExample.cs#sectioncodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#SectionCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/SectionExample.vb#sectioncodeonlyexamplewholepage)]  
  
 **BlockUIContainer**  
  
 <xref:System.Windows.Documents.BlockUIContainer> により、<xref:System.Windows.UIElement>要素 (つまり、 <xref:System.Windows.Controls.Button>) を block の派生フロー コンテンツに埋め込むことです。 <xref:System.Windows.Documents.InlineUIContainer> 埋め込む (下記参照) が使用される<xref:System.Windows.UIElement>inline の派生フロー コンテンツ要素。 <xref:System.Windows.Documents.BlockUIContainer> <xref:System.Windows.Documents.InlineUIContainer>を使用するには、その他の方法がないために、重要な<xref:System.Windows.UIElement>フロー内でこれら 2 つの要素のいずれかに含まれている場合を除き、コンテンツにします。  
  
 次の例は、使用する方法を示します、<xref:System.Windows.Documents.BlockUIContainer>ホスト要素<xref:System.Windows.UIElement>フロー コンテンツ内のオブジェクト。  
  
 [!code-xaml[SpanSnippets#_BlockUIXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml#_blockuixaml)]  
  
 次の図は、この例の表示方法を示しています。  
  
 ![UIElement を示すスクリーン ショットは、フロー コンテンツに埋め込まれます。](./media/flow-document-overview/embedded-blockuicontainer.png)  
  
 **List**  
  
 <xref:System.Windows.Documents.List> 箇条書きまたは数値のリストの作成に使用されます。 設定、<xref:System.Windows.Documents.List.MarkerStyle%2A>プロパティを<xref:System.Windows.TextMarkerStyle>リストのスタイルを決定する列挙値。 簡単なリストを作成する方法を次の例に示します。  
  
 [!code-xaml[FlowOvwSnippets_snip#ListExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/ListExample.xaml#listexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#ListCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/ListExample.cs#listcodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#ListCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/ListExample.vb#listcodeonlyexamplewholepage)]  
  
 **注:** <xref:System.Windows.Documents.List>を使用するフロー要素のみ、<xref:System.Windows.Documents.ListItemCollection>子要素を管理します。  
  
 **テーブル**  
  
 <xref:System.Windows.Documents.Table> テーブルの作成に使用されます。 <xref:System.Windows.Documents.Table> ような<xref:System.Windows.Controls.Grid>要素が、その他の機能があり、そのため、大きいリソースのオーバーヘッドが必要です。 <xref:System.Windows.Controls.Grid>は、<xref:System.Windows.UIElement>に含まれている場合を除きには、フロー コンテンツで使用することはできません、<xref:System.Windows.Documents.BlockUIContainer>または<xref:System.Windows.Documents.InlineUIContainer>します。 詳細については<xref:System.Windows.Documents.Table>を参照してください[テーブルの概要](table-overview.md)します。  
  
### <a name="inline-derived-classes"></a>Inline の派生クラス  
 **実行**  
  
 <xref:System.Windows.Documents.Run> 書式なしテキストの格納に使用します。 ご想像<xref:System.Windows.Documents.Run>フロー コンテンツを広範囲に使用するオブジェクト。 ただし、マークアップでは、<xref:System.Windows.Documents.Run>要素に明示的に使用する必要はありません。 <xref:System.Windows.Documents.Run> 作成またはコードを使用してフロー ドキュメントを操作するときに使用される必要があります。 以下は、最初のマークアップでなど<xref:System.Windows.Documents.Paragraph>を指定します、<xref:System.Windows.Documents.Run>要素、2 つ目の中に明示的にはありません。 両方の段落は、同じ出力を生成します。  
  
 [!code-xaml[FlowOvwSnippets_snip#RunExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/RunSnippetsExample.xaml#runexample1)]  
  
 **注:** 以降では、 [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]、<xref:System.Windows.Documents.Run.Text%2A>のプロパティ、<xref:System.Windows.Documents.Run>オブジェクトが依存関係プロパティ。 バインドすることができます、<xref:System.Windows.Documents.Run.Text%2A>プロパティをデータ ソースなど、<xref:System.Windows.Controls.TextBlock>します。 <xref:System.Windows.Documents.Run.Text%2A>プロパティは、一方向のバインドを完全にサポートします。 <xref:System.Windows.Documents.Run.Text%2A>以外のプロパティが双方向のバインドにもサポートしています<xref:System.Windows.Controls.RichTextBox>します。 例については、「<xref:System.Windows.Documents.Run.Text%2A?displayProperty=nameWithType>」を参照してください。  
  
 **Span**  
  
 <xref:System.Windows.Documents.Span> その他のインライン コンテンツ要素をグループ化します。 内のコンテンツに固有のレンダリングが適用されず、<xref:System.Windows.Documents.Span>要素。 ただし、要素から継承した<xref:System.Windows.Documents.Span>など<xref:System.Windows.Documents.Hyperlink>、 <xref:System.Windows.Documents.Bold>、<xref:System.Windows.Documents.Italic>と<xref:System.Windows.Documents.Underline>テキストに書式を適用しないでください。  
  
 例を次に示します、 <xref:System.Windows.Documents.Span> 、テキストを含むインライン コンテンツを格納するために使用される、<xref:System.Windows.Documents.Bold>要素、および<xref:System.Windows.Controls.Button>します。  
  
 [!code-xaml[FlowOvwSnippets_snip#SpanExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SpanExample.xaml#spanexamplewholepage)]  
  
 次のスクリーンショットは、この例がどのように表示されるかを示しています。  
  
 ![スクリーン ショット:表示される Span の例](./media/flow-spanexample.gif "Flow_SpanExample")  
  
 **InlineUIContainer**  
  
 <xref:System.Windows.Documents.InlineUIContainer> により、<xref:System.Windows.UIElement>要素 (つまり、コントロールのような<xref:System.Windows.Controls.Button>) に埋め込まれる、<xref:System.Windows.Documents.Inline>コンテンツ要素。 この要素は同等のインライン<xref:System.Windows.Documents.BlockUIContainer>上記で説明しました。 使用する例を次に示します<xref:System.Windows.Documents.InlineUIContainer>を挿入する、<xref:System.Windows.Controls.Button>インラインで、<xref:System.Windows.Documents.Paragraph>します。  
  
 [!code-xaml[FlowOvwSnippets_snip#InlineUIContainerExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/InlineUIContainerExample.xaml#inlineuicontainerexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#InlineUIContainerCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/InlineUIContainerExample.cs#inlineuicontainercodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#InlineUIContainerCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/InlineUIContainerExample.vb#inlineuicontainercodeonlyexamplewholepage)]  
  
 **注:** <xref:System.Windows.Documents.InlineUIContainer>マークアップで明示的に使用する必要はありません。 省略した場合、<xref:System.Windows.Documents.InlineUIContainer>コードのコンパイル時にも作成されます。  
  
 **Figure および Floater**  
  
 <xref:System.Windows.Documents.Figure> <xref:System.Windows.Documents.Floater>主要コンテンツ フローから独立してカスタマイズできる配置プロパティを持つフロー ドキュメントにコンテンツを埋め込むために使用されます。 <xref:System.Windows.Documents.Figure> または<xref:System.Windows.Documents.Floater>強調表示するか、イメージやその他のコンテンツのメイン フロー コンテンツをサポートしているホストへのコンテンツの部分を強調する要素が使用される多くの場合、または疎を挿入する提供情報などのコンテンツに関連します。  
  
 次の例を組み込む方法を示します、<xref:System.Windows.Documents.Figure>テキストの段落にします。  
  
 [!code-xaml[FlowOvwSnippets_snip#FigureExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/FigureExample.xaml#figureexamplewholepage)]  
  
 [!code-csharp[FlowOvwSnippets_procedural_snip#FigureCodeOnlyExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/CSharp/FigureExample.cs#figurecodeonlyexamplewholepage)]
 [!code-vb[FlowOvwSnippets_procedural_snip#FigureCodeOnlyExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowOvwSnippets_procedural_snip/VisualBasic/FigureExample.vb#figurecodeonlyexamplewholepage)]  
  
 この例がどのように表示されるかを次の図に示します。  
  
 ![スクリーン ショット:図の例](./media/flow-ovw-figure-example.png "Flow_Ovw_Figure_Example")  
  
 <xref:System.Windows.Documents.Figure> <xref:System.Windows.Documents.Floater>いくつかの方法が異なるし、さまざまなシナリオのために使用します。  
  
 **Figure:**  
  
- 配置することができます。ページ、コンテンツ、列、または段落に対して相対的にドッキングする、水平および垂直方向のアンカーを設定することができます。 使用することもその<xref:System.Windows.Documents.Figure.HorizontalOffset%2A>と<xref:System.Windows.Documents.Figure.VerticalOffset%2A>プロパティを任意のオフセットを指定します。  
  
- 1 つ以上の列に有効です。設定できる<xref:System.Windows.Documents.Figure>ページ、コンテンツ、または列の高さまたは幅の倍数に幅と高さ。 ページおよびコンテンツの場合は、1 より大きい倍数は指定できない点に注意してください。 幅を設定するなど、 <xref:System.Windows.Documents.Figure> 「0.5 ページ」または「0.25 コンテンツ」または「2 列」にします。 高さと幅は、絶対ピクセル値で指定することもできます。  
  
- 改ページ調整されません。場合内のコンテンツを<xref:System.Windows.Documents.Figure>内に収まらない、<xref:System.Windows.Documents.Figure>はあらゆるコンテンツに合わせて表示して、残りの内容は失われます  
  
 **Floater:**  
  
- 配置できません。必要なスペースを確保できる場所に描画されます。 オフセットやアンカーを設定することはできません、<xref:System.Windows.Documents.Floater>します。  
  
- 1 つ以上の列にサイズを変更できません。既定では、<xref:System.Windows.Documents.Floater>サイズは 1 列。 <xref:System.Windows.Documents.Floater.Width%2A> 1 つの列のサイズはこの値が 1 つの列の幅は無視され、浮遊要素より大きい場合は、絶対ピクセル値を設定できるプロパティです。 正しいピクセル幅を設定して 1 つ未満の列にサイズことができますがサイズ変更はない列の相対のため"はできないの有効な式<xref:System.Windows.Documents.Floater>幅。 <xref:System.Windows.Documents.Floater> 高さのプロパティを持たないし、なる要素の高さを設定することはできませんの高さは、内容によって異なります。  
  
- <xref:System.Windows.Documents.Floater> ページに割り当てます。指定した幅には、そのコンテンツの列の高さを 1 つ以上の場合、浮遊要素では、次回のコラムでは、次のページなどをページに割り当てます。  
  
 <xref:System.Windows.Documents.Figure> サイズを制御するスタンドアロンのコンテンツを配置する適切な場所と配置、およびコンテンツは、指定されたサイズに収まるかどうかを確信します。 <xref:System.Windows.Documents.Floater> 同様に、メイン ページ コンテンツ フローしますが、そこから分離されているより多くの自由なコンテンツを配置することをお勧めします。  
  
 **LineBreak**  
  
 <xref:System.Windows.Documents.LineBreak> フロー コンテンツで改行をによりします。 次の例は、<xref:System.Windows.Documents.LineBreak> の使い方を示しています。  
  
 [!code-xaml[FlowOvwSnippets_snip#LineBreakExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/LineBreakExample.xaml#linebreakexamplewholepage)]  
  
 次のスクリーンショットは、この例がどのように表示されるかを示しています。  
  
 ![スクリーン ショット:LineBreak の例](./media/flow-ovw-linebreakexample.png "Flow_Ovw_LineBreakExample")  
  
### <a name="flow-collection-elements"></a>フロー コレクションの要素  
 上記の例の多くで、<xref:System.Windows.Documents.BlockCollection>と<xref:System.Windows.Documents.InlineCollection>フロー コンテンツをプログラムで構築するために使用します。 たとえば、要素を追加するため、<xref:System.Windows.Documents.Paragraph>構文を使用することができます。  
  
 `…`  
  
 `myParagraph.Inlines.Add(new Run("Some text"));`  
  
 `…`  
  
 これを追加、<xref:System.Windows.Documents.Run>を<xref:System.Windows.Documents.InlineCollection>の<xref:System.Windows.Documents.Paragraph>します。  これは、暗黙の型と同じ<xref:System.Windows.Documents.Run>内で検出された、<xref:System.Windows.Documents.Paragraph>マークアップで。  
  
 `…`  
  
 `<Paragraph>`  
  
 `Some Text`  
  
 `</Paragraph>`  
  
 `…`  
  
 使用する例として、 <xref:System.Windows.Documents.BlockCollection>、次の例では、作成、新しい<xref:System.Windows.Documents.Section>しを使用して、**追加**メソッドを追加する新しい<xref:System.Windows.Documents.Paragraph>を<xref:System.Windows.Documents.Section>内容。  
  
 [!code-csharp[FlowDocumentSnippets#_SectionBlocksAdd](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml.cs#_sectionblocksadd)]
 [!code-vb[FlowDocumentSnippets#_SectionBlocksAdd](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FlowDocumentSnippets/visualbasic/window1.xaml.vb#_sectionblocksadd)]  
  
 フロー コレクションに項目を追加できるだけでなく、項目を削除することもできます。  次の例では、削除、最終<xref:System.Windows.Documents.Inline>内の要素、<xref:System.Windows.Documents.Span>します。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesremovelast)]
 [!code-vb[SpanSnippets#_SpanInlinesRemoveLast](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesremovelast)]  
  
 次の例では、すべての内容をクリア (<xref:System.Windows.Documents.Inline>要素) から、<xref:System.Windows.Documents.Span>します。  
  
 [!code-csharp[SpanSnippets#_SpanInlinesClear](~/samples/snippets/csharp/VS_Snippets_Wpf/SpanSnippets/CSharp/Window1.xaml.cs#_spaninlinesclear)]
 [!code-vb[SpanSnippets#_SpanInlinesClear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SpanSnippets/visualbasic/window1.xaml.vb#_spaninlinesclear)]  
  
 フロー コンテンツをプログラムで操作する場合、これらのコレクションを広く活用する可能性があります。  
  
 フロー要素を使用しているかどうか、 <xref:System.Windows.Documents.InlineCollection> (インライン) または<xref:System.Windows.Documents.BlockCollection>(ブロック) の子を格納する要素は子要素の種類によって異なります (<xref:System.Windows.Documents.Block>または<xref:System.Windows.Documents.Inline>)、親に含まれることができます。 フロー コンテンツ要素のコンテインメイト規則については、次のセクションのコンテンツ スキーマにまとめます。  
  
 **注:** フロー コンテンツと共に使用されるコレクションの 3 番目の型がある、 <xref:System.Windows.Documents.ListItemCollection>、このコレクションでのみ使用しますが、 <xref:System.Windows.Documents.List>。 さらで使用されるいくつかのコレクションがある<xref:System.Windows.Documents.Table>します。 参照してください[テーブルの概要](table-overview.md)詳細についてはします。  
  
<a name="content_schema"></a>   
## <a name="content-schema"></a>コンテンツ スキーマ  
 多数のさまざまなフロー コンテンツ要素が指定されると、要素が格納できる子要素の種類を追跡できなくなる可能性があります。 フロー要素のコンテインメイト規則をまとめたものを次の図に示します。 矢印は、使用可能な親/子リレーションシップを表します。  
  
 ![図に示します。フロー コンテンツ コンテインメント スキーマ](./media/flow-content-schema.png "Flow_Content_Schema")  
  
 上の図からわかるように、要素で許容される子は必ずしも決定されませんがかどうかによって、<xref:System.Windows.Documents.Block>要素または<xref:System.Windows.Documents.Inline>要素。 など、 <xref:System.Windows.Documents.Span> (、<xref:System.Windows.Documents.Inline>要素) のみ持つことができます<xref:System.Windows.Documents.Inline>中に子要素を<xref:System.Windows.Documents.Figure>(も、<xref:System.Windows.Documents.Inline>要素) しか<xref:System.Windows.Documents.Block>子要素。 そのため、どの要素を別の要素に含めることができるかをすばやく判断するには、図が役立ちます。 たとえばのフロー コンテンツを構築する方法を決定するみましょう、図を使用する<xref:System.Windows.Controls.RichTextBox>します。  
  
 **1.** A<xref:System.Windows.Controls.RichTextBox>含める必要があります、<xref:System.Windows.Documents.FlowDocument>をさらに含める必要があります、 <xref:System.Windows.Documents.Block>-派生オブジェクト。 上の図でこれに対応する部分を次に示します。  
  
 ![図に示します。RichTextBox コンテインメント規則](./media/flow-ovw-schemawalkthrough1.png "Flow_Ovw_SchemaWalkThrough1")  
  
 この段階では、マークアップは次のようになります。  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough1](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough1)]  
  
 **2.** に従って、ダイアグラムは、いくつか<xref:System.Windows.Documents.Block>要素を含むを<xref:System.Windows.Documents.Paragraph>、 <xref:System.Windows.Documents.Section>、 <xref:System.Windows.Documents.Table>、 <xref:System.Windows.Documents.List>、および<xref:System.Windows.Documents.BlockUIContainer>(上記の Block の派生クラスを参照してください)。 ここですると、<xref:System.Windows.Documents.Table>します。 上記の図によると、<xref:System.Windows.Documents.Table>が含まれています、<xref:System.Windows.Documents.TableRowGroup>を含む<xref:System.Windows.Documents.TableRow>を含む要素を<xref:System.Windows.Documents.TableCell>を含む要素を<xref:System.Windows.Documents.Block>-派生オブジェクト。 対応する部分を次に示します<xref:System.Windows.Documents.Table>上の図から取得されます。  
  
 ![図に示します。親&#47;子テーブルのスキーマ](./media/flow-ovw-schemawalkthrough2.png "Flow_Ovw_SchemaWalkThrough2")  
  
 以下は、これに対応するマークアップです。  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaWalkThrough2](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/MiscSnippets.xaml#schemawalkthrough2)]  
  
 **3.** ここでも、1 つまたは複数<xref:System.Windows.Documents.Block>要素は、下にある必要がある、<xref:System.Windows.Documents.TableCell>します。 簡単にするために、セル内にいくつかのテキストを配置することにします。 これにを使用して、<xref:System.Windows.Documents.Paragraph>で、<xref:System.Windows.Documents.Run>要素。 示すダイアグラムから対応するセグメントを次に示します、<xref:System.Windows.Documents.Paragraph>かかることがあります、<xref:System.Windows.Documents.Inline>要素とする、 <xref:System.Windows.Documents.Run> (、<xref:System.Windows.Documents.Inline>要素) プレーン テキストのみを取ることができます。  
  
 ![図に示します。親&#47;段落の子スキーマ](./media/flow-ovw-schemawalkthrough3.png "Flow_Ovw_SchemaWalkThrough3")  
  
 ![図に示します。親&#47;実行子スキーマ](./media/flow-ovw-schemawalkthrough4.png "Flow_Ovw_SchemaWalkThrough4")  
  
 以下は、マークアップでの例の全体です。  
  
 [!code-xaml[FlowOvwSnippets_snip#SchemaExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowOvwSnippets_snip/CS/SchemaExample.xaml#schemaexamplewholepage)]  
  
<a name="customizing_text"></a>   
## <a name="customizing-text"></a>テキストのカスタマイズ  
 通常、テキストは、フロー ドキュメントで最も一般的なコンテンツの種類です。 上で導入されたオブジェクトは、テキストをレンダリングする方法のほとんどの側面を制御するために使用できますが、このセクションで説明されるテキストのカスタマイズ用にその他のメソッドがいくつか存在します。  
  
### <a name="text-decorations"></a>文字装飾  
 文字装飾によって、下線、上線、ベースライン、および取り消し線の効果をテキストに適用できます (下図参照)。 これらの装飾を追加するには、<xref:System.Windows.Documents.Inline.TextDecorations%2A>数などのオブジェクトによって公開されるプロパティ<xref:System.Windows.Documents.Inline>、 <xref:System.Windows.Documents.Paragraph>、 <xref:System.Windows.Controls.TextBlock>、および<xref:System.Windows.Controls.TextBox>します。  
  
 <xref:System.Windows.Documents.Paragraph.TextDecorations%2A> の <xref:System.Windows.Documents.Paragraph> プロパティを設定する方法を次の例に示します。  
  
 [!code-xaml[InlineSnippets#_Paragraph_TextDecXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/InlineSnippets/CSharp/Window1.xaml#_paragraph_textdecxaml)]  
  
 [!code-csharp[InlineSnippets#_Paragraph_TextDec](~/samples/snippets/csharp/VS_Snippets_Wpf/InlineSnippets/CSharp/Window1.xaml.cs#_paragraph_textdec)]
 [!code-vb[InlineSnippets#_Paragraph_TextDec](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InlineSnippets/visualbasic/window1.xaml.vb#_paragraph_textdec)]  
  
 この例の表示結果を次の図に示します。  
  
 ![スクリーン ショット:既定の取り消し線効果テキスト](./media/inline-textdec-strike.png "Inline_TextDec_Strike")  
  
 次の図方法、**上線**、**ベースライン**、および**に下線を引く**、それぞれします。  
  
 ![スクリーン ショット:TextDecorator の上に線](./media/inline-textdec-over.png "Inline_TextDec_Over")  
  
 ![スクリーン ショット:既定のテキストのベースライン効果](./media/inline-textdec-base.png "Inline_TextDec_Base")  
  
 ![スクリーン ショット:既定の下線効果でテキスト](./media/inline-textdec-under.png "Inline_TextDec_Under")  
  
### <a name="typography"></a>タイポグラフィ  
 <xref:System.Windows.Documents.TextElement.Typography%2A>プロパティがほとんどフローに関連するコンテンツを含めることによって公開される<xref:System.Windows.Documents.TextElement>、 <xref:System.Windows.Documents.FlowDocument>、 <xref:System.Windows.Controls.TextBlock>、および<xref:System.Windows.Controls.TextBox>します。 このプロパティは、テキストの文字体裁の特性またはバリエーション (つまり、小さい大文字か大きい大文字か、上付き文字と下付き文字の作成など) を制御するために使用されます。  
  
 次の例は、設定する方法を示します、<xref:System.Windows.Documents.TextElement.Typography%2A>属性を使用して<xref:System.Windows.Documents.Paragraph>要素例として。  
  
 [!code-xaml[TextElementSnippets#_TextElement_TypogXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml#_textelement_typogxaml)]  
  
 この例の表示結果を次の図に示します。  
  
 ![スクリーン ショット:変更されたタイポグラフィを含むテキスト](./media/textelement-typog.png "TextElement_Typog")  
  
 これに対し、既定の文字体裁プロパティを設定した同様の例がどのように表示されるかを次の図に示します。  
  
 ![スクリーン ショット:変更されたタイポグラフィを含むテキスト](./media/textelement-typog-default.png "TextElement_Typog_Default")  
  
 次の例は、設定する方法を示します、<xref:System.Windows.Controls.TextBox.Typography%2A>プロパティ プログラムを使用します。  
  
 [!code-csharp[TextElementSnippets#_TextElement_Typog](~/samples/snippets/csharp/VS_Snippets_Wpf/TextElementSnippets/CSharp/Window1.xaml.cs#_textelement_typog)]
 [!code-vb[TextElementSnippets#_TextElement_Typog](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextElementSnippets/visualbasic/window1.xaml.vb#_textelement_typog)]  
  
 参照してください[WPF のタイポグラフィ](typography-in-wpf.md)文字体裁の詳細についてはします。  
  
## <a name="see-also"></a>関連項目

- [Text](optimizing-performance-text.md)
- [WPF のタイポグラフィ](typography-in-wpf.md)
- [方法トピック](flow-content-elements-how-to-topics.md)
- [TextElement コンテンツ モデルの概要](textelement-content-model-overview.md)
- [RichTextBox の概要](../controls/richtextbox-overview.md)
- [WPF のドキュメント](documents-in-wpf.md)
- [テーブルの概要](table-overview.md)
- [注釈の概要](annotations-overview.md)
