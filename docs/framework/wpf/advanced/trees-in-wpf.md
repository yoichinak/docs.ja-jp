---
title: WPF のツリー
ms.date: 03/30/2017
helpviewer_keywords:
- logical tree [WPF]
- element tree [WPF]
- visual tree [WPF]
ms.assetid: e83f25e5-d66b-4fc7-92d2-50130c9a6649
ms.openlocfilehash: f9b507c874dfe0ab3feca19e7fcf79df5af93e10
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197686"
---
# <a name="trees-in-wpf"></a>WPF のツリー
多くのテクノロジ要素とコンポーネントは、開発者は直接レンダリングや、アプリケーションの動作に影響を与える、ツリー内のオブジェクト ノード、操作をツリー構造で編成されています。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] またプログラム要素間のリレーションシップを定義するのにいくつかのツリー構造のメタファを使用します。 WPF 開発者の大部分できますコードでアプリケーションを作成または XAML で概念的には、オブジェクト ツリーの比喩を考えながら、アプリケーションの部分的な定義が、特定の API を呼び出すかをいくつかの一般的なのではなく、その特定のマークアップを使用する方法XML DOM で使用するなどのオブジェクトのツリー操作 API WPF のツリーの比喩ビューを提供する 2 つのヘルパー クラスが公開<xref:System.Windows.LogicalTreeHelper>と<xref:System.Windows.Media.VisualTreeHelper>します。 用語のビジュアル ツリーと論理ツリーも使用されます、WPF ドキュメントのため、同じようなツリーは特定のキーの WPF 機能の動作を理解するのに役立ちます。 このトピックでは、ビジュアル ツリーと論理ツリーが表す内容を定義し、このようなツリーが、全体的なオブジェクトのツリーの概念に関連する方法について説明しますが導入されています<xref:System.Windows.LogicalTreeHelper>と<xref:System.Windows.Media.VisualTreeHelper>秒。  

<a name="element_tree"></a>   
## <a name="trees-in-wpf"></a>WPF のツリー  
 最も完全なツリー構造で[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]はオブジェクトのツリーです。 アプリケーション ページを定義する場合[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]し、ロード、 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、ツリー構造は、マークアップ内の要素の入れ子のリレーションシップに基づいて作成されます。 アプリケーションを定義するか、コードでは、アプリケーション、ツリー構造の一部が作成された場合は、特定のオブジェクトのコンテンツ モデルを実装するプロパティのプロパティ値を割り当てる方法に基づいています。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]は、完全なオブジェクトのツリーが概念化し、そのパブリック API に報告できます 2 つの方法があります: 論理ツリーとビジュアル ツリー。 論理ツリーとビジュアル ツリー間の違いは、必ずしも、必ずしも重要なが特定の問題が発生することができる場合によっては、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]サブシステムとマークアップまたはコードで選択したに影響します。  
  
 実行しない常に、論理ツリーまたはビジュアル ツリーを直接操作する場合でも、ツリーの操作方法の概念を理解するはテクノロジとして WPF を理解するために役立ちます。 何らかの木のたとえはのプロパティの継承やイベントのルーティングのしくみを理解するために重要でも、WPF の検討[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]します。  
  
> [!NOTE]
>  オブジェクト ツリーより実際の API の概念の詳細は、概念と考えることを別の方法をオブジェクト グラフとしてです。 実際には、ツリーの比喩が分割は、実行時のオブジェクト間のリレーションシップには。 ただし、特に UI の XAML 定義木のたとえは関連この一般的な概念を参照するときに、ほとんどの WPF のドキュメントがオブジェクト ツリーという用語を使用します。  
  
<a name="logical_tree"></a>   
## <a name="the-logical-tree"></a>論理ツリー  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、それらの要素のバックアップを作成するオブジェクトのプロパティを設定して UI 要素にコンテンツを追加します。 項目を追加するなど、<xref:System.Windows.Controls.ListBox>コントロールを操作することによってその<xref:System.Windows.Controls.ItemsControl.Items%2A>プロパティ。 これによりにアイテムを配置する、<xref:System.Windows.Controls.ItemCollection>つまり、<xref:System.Windows.Controls.ItemsControl.Items%2A>プロパティの値。 同様に、追加するオブジェクトを<xref:System.Windows.Controls.DockPanel>、操作するその<xref:System.Windows.Controls.Panel.Children%2A>プロパティの値。 ここでは、オブジェクトを追加する、<xref:System.Windows.Controls.UIElementCollection>します。 コード例では、次を参照してください。[方法。要素を動的に追加](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms752374(v=vs.100))します。  
  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]でリスト項目を配置するとき、 <xref:System.Windows.Controls.ListBox> 、コントロール、または他の UI 要素で、 <xref:System.Windows.Controls.DockPanel>、使用することも、<xref:System.Windows.Controls.ItemsControl.Items%2A>と<xref:System.Windows.Controls.Panel.Children%2A>プロパティ、明示的または暗黙的に、次の例のようにします。  
  
 [!code-xaml[TreeOvwsSupport#AllCode](~/samples/snippets/csharp/VS_Snippets_Wpf/TreeOvwsSupport/CS/page1.xaml#allcode)]  
  
 かどうかとして XML ドキュメント オブジェクト モデルでは、この XAML を処理したコメント タグが含まれていたかどうか、out 暗黙的な (これは有効でした)、結果の XML DOM ツリーに要素が含まれますが、`<ListBox.Items>`とその他の暗黙的な項目です。 マークアップを読み取るオブジェクトを記述すると XAML がその方法を処理しませんは、生成されたオブジェクト グラフには文字どおりは含まれません`ListBox.Items`します。 ただしが、<xref:System.Windows.Controls.ListBox>という名前のプロパティ`Items`を格納している、 <xref:System.Windows.Controls.ItemCollection>、および<xref:System.Windows.Controls.ItemCollection>は初期化されますが、空にする、 <xref:System.Windows.Controls.ListBox> XAML が処理されます。 次に、各子オブジェクト要素のコンテンツとして存在する、<xref:System.Windows.Controls.ListBox>に追加されます、<xref:System.Windows.Controls.ItemCollection>パーサーを呼び出して`ItemCollection.Add`します。 この例のオブジェクト ツリーに XAML の処理はこれまでに一見例作成されたオブジェクト ツリーが論理ツリーでは基本的に。  
  
 ただし、論理ツリーは、XAML の暗黙的な構文項目を使用しても、実行時に UI が除外されているアプリケーションに対して存在する全体オブジェクト グラフではありません。この主な理由は、ビジュアルとテンプレートです。 たとえば、<xref:System.Windows.Controls.Button>します。 論理ツリー レポート、<xref:System.Windows.Controls.Button>オブジェクトともその文字列`Content`します。 実行時のオブジェクト ツリーで、このボタンにはたくさんあります。 具体的には、ボタンのみ画面に表示されるためはその方法は、特定の<xref:System.Windows.Controls.Button>コントロール テンプレートが適用されました。 ビジュアル、適用されたテンプレートから取得した (テンプレートで定義されたなど<xref:System.Windows.Controls.Border>visual ボタンの周囲の濃い灰色の) 実行時に、論理ツリーが表示されている場合でも、論理ツリーでは報告されません (からの入力イベントの処理など、表示される UI とし、論理ツリーを読み取る)。 テンプレートのビジュアルを検索するには、ビジュアル ツリーを調べるには代わりに必要です。  
  
 詳細について[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]構文は、作成されたオブジェクトのグラフと、XAML で暗黙の型の構文を参照してください[XAML 構文の詳細](xaml-syntax-in-detail.md)または[XAML の概要 (WPF)](xaml-overview-wpf.md)します。  
  
<a name="tree_property_inheritance_event_routing"></a>   
### <a name="the-purpose-of-the-logical-tree"></a>論理ツリーの目的は、  
 論理ツリーには、コンテンツ モデルは、使用可能な子オブジェクトを簡単に反復処理できるように、およびコンテンツ モデルの拡張が存在します。 また、論理ツリー フレームワークを提供、特定の論理ツリー内のすべてのオブジェクトが読み込まれるタイミングなどの通知。 基本的には、論理ツリーは、ビジュアルは含まれませんが、独自の実行時のアプリケーションの構成に対して多くのクエリ操作のための適切なフレームワーク レベルで実行時のオブジェクト グラフの概数です。  
  
 上の論理ツリーを検索して両方の静的および動的なリソースの参照を解決するさらに、<xref:System.Windows.FrameworkElement.Resources%2A>上、最初の要求オブジェクトと論理ツリーを続行し、各コレクション<xref:System.Windows.FrameworkElement>(または<xref:System.Windows.FrameworkContentElement>)別の`Resources`値を含む、 <xref:System.Windows.ResourceDictionary>、そのキーを格納している可能性があります。 論理ツリーは、論理ツリーとビジュアル ツリーの両方が存在する場合、リソースの検索の使用されます。 リソース ディクショナリ、およびルックアップの詳細については、次を参照してください。 [XAML リソース](xaml-resources.md)します。  
  
<a name="composition"></a>   
### <a name="composition-of-the-logical-tree"></a>論理ツリーのコンポジション  
 論理ツリーが、WPF フレームワーク レベル、つまり論理ツリー操作にとって最も重要な WPF 基本要素はいずれかで定義されている<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>します。 ただし、ことがわかります。 実際に使用場合、 <xref:System.Windows.LogicalTreeHelper> API、論理ツリーもノードが含まれますどちらでもない<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>します。 たとえば、論理ツリーを報告、<xref:System.Windows.Controls.TextBlock.Text%2A>の値を<xref:System.Windows.Controls.TextBlock>文字列であります。  
  
<a name="override_logical_tree"></a>   
### <a name="overriding-the-logical-tree"></a>論理ツリーをオーバーライドします。  
 高度なコントロールの作成者は、いくつかの操作をオーバーライドすることで、論理ツリーをオーバーライドできます[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]一般的なオブジェクトまたはコンテンツ モデルが追加または論理ツリー内のオブジェクトを削除する方法を定義します。 論理ツリーをオーバーライドする方法の例は、次を参照してください。[論理ツリーをオーバーライド](how-to-override-the-logical-tree.md)します。  
  
<a name="pvi"></a>   
### <a name="property-value-inheritance"></a>プロパティ値の継承  
 プロパティ値の継承は、ハイブリッド ツリーを通じて動作します。 実際のメタデータを含む、<xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A>プロパティの継承を有効にするプロパティは、WPF フレームワーク レベル<xref:System.Windows.FrameworkPropertyMetadata>クラス。 そのため、元の値を保持する親とその値を継承する子オブジェクトの両方もなりません<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>、必要がありますどちらもいくつかの論理ツリーの一部であるとします。 ただし、プロパティの継承をサポートする既存の WPF プロパティ、プロパティ値の継承は、論理ツリーに含まれていない間にあるオブジェクトを永続化することです。 これは主には、継承されたプロパティの値は、テンプレート化されたインスタンスのいずれかの設定を使用して、テンプレート要素を含むもののまたはページ レベルの構成のも高いレベルでは関連があり、論理ツリー内の上位。 プロパティ値の継承、このような境界を越えて一貫して動作するためには、継承プロパティは、添付プロパティとして登録する必要があり。、カスタム依存関係プロパティとプロパティを定義する場合、このパターンに従う必要があります。継承の動作です。 プロパティの継承に使用される正確なツリーは、実行時にもヘルパー クラスのユーティリティ メソッドがまったく予期することはできません。 詳細については、「[プロパティ値の継承](property-value-inheritance.md)」を参照してください。  
  
<a name="two_trees"></a>   
## <a name="the-visual-tree"></a>ビジュアル ツリー  
 だけでなく、論理ツリーの概念も、概念は、ビジュアル ツリー内の[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]します。 によって表されるビジュアル ツリーは、ビジュアル オブジェクトの構造について説明します、<xref:System.Windows.Media.Visual>基本クラス。 コントロールのテンプレートを記述するときにを定義するか、そのコントロールに適用するビジュアル ツリーを再定義ができます。 ビジュアル ツリーは、パフォーマンスおよび最適化のために、描画に対して低レベルの制御を望む開発者にとって重要なのもです。 従来の一部として、ビジュアル ツリーの 1 つの露出[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーション プログラミングは、ルーティング イベントのイベント ルートはほとんどの場合、論理ツリーではなく、ビジュアル ツリーに沿って伝達されます。 コントロールの作成者でない限り、ルーティング イベントの動作の細部をすぐにわかりますできない可能性があります。 ビジュアル ツリーを介したイベントのルーティングには、イベントを処理したり、イベント setter を作成するビジュアル レベルで構成を実装するコントロールができます。  
  
<a name="trees_content"></a>   
## <a name="trees-content-elements-and-content-hosts"></a>ツリー、コンテンツ要素、およびコンテンツのホスト  
 要素のコンテンツ (クラスから派生した<xref:System.Windows.ContentElement>)、ビジュアル ツリーの一部ではない; から継承しない<xref:System.Windows.Media.Visual>視覚的に表現はありません。 すべての UI に表示するには、<xref:System.Windows.ContentElement>両方にあるコンテンツのホストでホストする必要があります、<xref:System.Windows.Media.Visual>および論理ツリーの参加要素。 このようなオブジェクトは、通常、<xref:System.Windows.FrameworkElement>します。 コンテンツのホストは、コンテンツが、"browser"のようなものと、ホストを制御する画面領域内でそのコンテンツを表示する方法を選択を考えることができます。 コンテンツがホストされている場合、コンテンツは通常、ビジュアル ツリーに関連付けられている特定のツリー プロセスに参加要素を作成できます。 一般に、<xref:System.Windows.FrameworkElement>ホスト クラスには、ホストされているいずれかを追加する実装コードが含まれています。<xref:System.Windows.ContentElement>コンテンツの論理ツリーのサブノードをイベントのルーティングに場合でもホストされたコンテンツが true のビジュアル ツリーの一部です。 これは、必要なように、<xref:System.Windows.ContentElement>自体以外の任意の要素にルーティングするルーティング イベント ソースのことができます。  
  
<a name="tree_traversal"></a>   
## <a name="tree-traversal"></a>ツリーの走査  
 <xref:System.Windows.LogicalTreeHelper>クラスには、 <xref:System.Windows.LogicalTreeHelper.GetChildren%2A>、 <xref:System.Windows.LogicalTreeHelper.GetParent%2A>、および<xref:System.Windows.LogicalTreeHelper.FindLogicalNode%2A>論理ツリーの走査のためのメソッド。 ほとんどの場合必要はありません、既存のコントロールの論理ツリーを走査するため、これらのコントロールはなどコレクションへのアクセスをサポートする専用のコレクション プロパティとして、論理上の子要素を公開するほとんどの場合に`Add`インデクサー、などなど。 ツリーの走査は主にシナリオなど、目的のコントロール パターンから派生しないように選択コントロールの作成者によって使用される<xref:System.Windows.Controls.ItemsControl>または<xref:System.Windows.Controls.Panel>コレクションのプロパティが既に定義されていると、独自のコレクションを使用するユーザープロパティのサポート。  
  
 ビジュアル ツリーの走査のビジュアル ツリーがヘルパー クラスにもサポートしています<xref:System.Windows.Media.VisualTreeHelper>します。 コントロール固有のプロパティで、ビジュアル ツリーとして簡単に公開されないため、<xref:System.Windows.Media.VisualTreeHelper>クラスは、プログラミングのシナリオのために必要な場合に、ビジュアル ツリーを走査するをお勧めします。 詳しくは、「[WPF グラフィックス レンダリングの概要](../graphics-multimedia/wpf-graphics-rendering-overview.md)」をご覧ください。  
  
> [!NOTE]
>  適用されたテンプレートのビジュアル ツリーを調べる必要があります。 この手法を使用する場合は注意する必要があります。 コントロールのビジュアル ツリーを走査し、テンプレートを定義するが、場合でも、コントロールのコンシューマー常に、テンプレート設定を変更できます、<xref:System.Windows.Controls.Control.Template%2A>インスタンス、およびエンド ユーザーでもプロパティが変更することでテンプレートを適用したを与えることができます、システムのテーマ。  
  
<a name="routes"></a>   
## <a name="routes-for-routed-events-as-a-tree"></a>ルーティング イベントとして「ツリー」のルート  
 前述のように、特定のルーティング イベントのルートはビジュアルと論理ツリー表現を組み合わせるハイブリッドであるツリーの 1 つと事前に定義されたパスに沿って移動します。 イベントのルーティングが最大でいずれかに移動または、方向がかどうかに応じて、ツリー内をトンネリングやバブル ルーティング イベント。 イベント ルートの概念には、「説明」実際にルーティングするイベントを発生させるとは別にイベントのルーティングに使用できるヘルパー クラスを直接サポートはありません。 ルートを表すクラスがある<xref:System.Windows.EventRoute>、そのクラスのメソッドは、通常、内部使用のみが、します。  
  
<a name="resourcesandtrees"></a>   
## <a name="resource-dictionaries-and-trees"></a>リソース ディクショナリとツリー  
 すべてのリソース ディクショナリのルックアップ`Resources`定義ページに基本的に、論理はツリーを走査します。 論理ツリーに含まれていないオブジェクトがキーを持つリソースを参照できますが、論理ツリーにそのオブジェクトが接続されているポイントではリソース参照シーケンスが開始されます。 WPF では、論理ツリーのノードのみを持つことができます、`Resources`プロパティを含む、 <xref:System.Windows.ResourceDictionary>、したがってからキーを持つリソースを探して、ビジュアル ツリーの走査の利点はありません、<xref:System.Windows.ResourceDictionary>します。  
  
 ただし、リソースの検索も、直接の論理ツリーを超えて拡張できます。 アプリケーション マークアップでは、アプリケーション レベルのリソース ディクショナリ、静的プロパティまたはキーとして参照されているテーマのサポート、およびシステム値へとリソース検索が続きます。 テーマ自体は、動的リソース参照である場合、テーマの論理ツリーの外部システムの値を参照できます。 リソース ディクショナリとルックアップ ロジックの詳細については、次を参照してください。 [XAML リソース](xaml-resources.md)します。  
  
## <a name="see-also"></a>関連項目

- [入力の概要](input-overview.md)
- [WPF グラフィックス レンダリングの概要](../graphics-multimedia/wpf-graphics-rendering-overview.md)
- [ルーティング イベントの概要](routed-events-overview.md)
- [オブジェクト ツリーに存在しないオブジェクト要素の初期化](initialization-for-object-elements-not-in-an-object-tree.md)
- [WPF アーキテクチャ](wpf-architecture.md)
