---
title: ナビゲーションの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- loose XAML files [WPF]
- windows [WPF]
- Start page [WPF]
- HTML files [WPF]
- structured navigation [WPF]
- fragment navigation [WPF]
- URIs (Uniform Resource Identifiers)
- custom objects [WPF]
- Uniform Resource Identifiers (URIs)
- pages [WPF]
- frames [WPF]
- navigation hosts [WPF]
- journals [WPF]
- lifetimes [WPF]
- retaining content state [WPF]
- content state [WPF]
- programmatic navigation [WPF]
- hyperlinks [WPF]
ms.assetid: 86ad2143-606a-4e34-bf7e-51a2594248b8
ms.openlocfilehash: 7636a7d9a100d0df95f7d5462672819624ba52a4
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2019
ms.locfileid: "57679971"
---
# <a name="navigation-overview"></a>ナビゲーションの概要
Windows Presentation Foundation (WPF) は、2 種類のアプリケーションで使用できるブラウザー スタイルのナビゲーションをサポートしています: スタンドアロン アプリケーションと[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]します。 ナビゲーションのためのパッケージ コンテンツに[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]提供、<xref:System.Windows.Controls.Page>クラス。 1 つから移動することができます<xref:System.Windows.Controls.Page>別に宣言を使用して、 <xref:System.Windows.Documents.Hyperlink>、またはを使用してプログラムで、<xref:System.Windows.Navigation.NavigationService>します。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は、ナビゲート元のページを記憶し、それらのページに戻るために、履歴を使用します。  
  
 <xref:System.Windows.Controls.Page>、 <xref:System.Windows.Documents.Hyperlink>、 <xref:System.Windows.Navigation.NavigationService>、履歴がで提供されるナビゲーション サポートの中核を形成し、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]します。 この概要では、これらの機能の詳細を説明へのナビゲーションを含む高度なナビゲーション サポートをカバーする前に[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ファイル、[!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)]ファイル、およびオブジェクト。  
  
> [!NOTE]
>  このトピックで、"browser"という用語がホストできるブラウザーだけを参照[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]など現在アプリケーションを[!INCLUDE[TLA#tla_ie](../../../../includes/tlasharptla-ie-md.md)]と Firefox。 特定[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]機能が特定のブラウザーでのみサポートされている、ブラウザーのバージョンと呼びます。  
   
     
## <a name="navigation-in-wpf-applications"></a>WPF アプリケーションでのナビゲーション  
 このトピックの主なナビゲーション機能の概要を示します[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]します。 これらの機能は両方のスタンドアロン アプリケーションで使用できると[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]のコンテキスト内でこのトピックで説明していますが、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]します。  
  
> [!NOTE]
>  このトピックでを構築してデプロイする方法について説明しない[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]します。 詳細については[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]を参照してください[WPF XAML ブラウザー アプリケーションの概要](wpf-xaml-browser-applications-overview.md)します。  
  
 このセクションでは、ナビゲーションの次の側面について説明し、例を示します。  
  
-   [ページの実装](#CreatingAXAMLPage)  
  
-   [スタート ページの構成](#Configuring_a_Start_Page)  
  
-   [ホスト ウィンドウのタイトル、幅、および高さの構成](#ConfiguringAXAMLPage)  
  
-   [ハイパーリンクのナビゲーション](#NavigatingBetweenXAMLPages)  
  
-   [フラグメント ナビゲーション](#FragmentNavigation)  
  
-   [ナビゲーション サービス](#NavigationService)  
  
-   [ナビゲーション サービスによるプログラム ナビゲーション](#Programmatic_Navigation_with_the_Navigation_Service)  
  
-   [ナビゲーションの有効期間](#Navigation_Lifetime)  
  
-   [履歴によるナビゲーションの記憶](#NavigationHistory)  
  
-   [ページの有効期間と履歴](#PageLifetime)  
  
-   [ナビゲーション履歴によるコンテンツの状態の保持](#RetainingContentStateWithNavigationHistory)  
  
-   [Cookie](#Cookies)  
  
-   [構造化ナビゲーション](#Structured_Navigation)  
  
<a name="CreatingAXAMLPage"></a>   
### <a name="implementing-a-page"></a>ページの実装  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]は、.NET Framework のオブジェクト、カスタム オブジェクト、列挙値、ユーザー コントロールでは、いくつかのコンテンツの種類に移動できます[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイル、および[!INCLUDE[TLA#tla_html](../../../../includes/tlasharptla-html-md.md)]ファイル。 パッケージ コンテンツを最も一般的で便利な方法を使用して、ただし、わかります<xref:System.Windows.Controls.Page>します。 さらに、<xref:System.Windows.Controls.Page>ナビゲーション固有の機能をそれらの外観を強化し、開発を簡略化を実装します。  
  
 使用して<xref:System.Windows.Controls.Page>のナビゲート可能なページを宣言によって実装できます[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]次のようなマークアップを使用して別のコンテンツ。  
  
 [!code-xaml[NavigationOverviewSnippets#Page1XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page1.xaml#page1xaml)]  
  
 A<xref:System.Windows.Controls.Page>で実装される[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]マークアップが`Page`、ルート要素とする必要があります、 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]名前空間宣言。 `Page`要素に移動し、表示するコンテンツが含まれています。 設定してコンテンツを追加する、`Page.Content`プロパティ要素の次のマークアップで示すようにします。  
  
 [!code-xaml[NavigationOverviewSnippets#Page2XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page2.xaml#page2xaml)]  
  
 `Page.Content` には、1 つの子要素のみを含めることができます。前の例では、コンテンツは単一の文字列「Hello, Page!」です。 実際は、通常使用するレイアウト コントロールの子要素として (を参照してください[レイアウト](../advanced/layout.md)) に格納し、コンテンツを構成します。  
  
 子要素を`Page`要素のコンテンツと見なされます、<xref:System.Windows.Controls.Page>と、その結果、明示的なを使用する必要はありません`Page.Content`宣言します。 次のマークアップは、前のサンプルの宣言と同等です。  
  
 [!code-xaml[NavigationOverviewSnippets#Page3XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page3.xaml#page3xaml)]  
  
 この場合、`Page.Content`の子要素を自動的に設定されますが、`Page`要素。 詳細については、「[WPF のコンテンツ モデル](../controls/wpf-content-model.md)」を参照してください。  
  
 マークアップのみ<xref:System.Windows.Controls.Page>はコンテンツを表示するのに便利です。 ただし、<xref:System.Windows.Controls.Page>ことも、このページと対話をユーザーに許可する表示コントロールとイベントを処理し、アプリケーション ロジックを呼び出すことによってユーザーの操作に応答できます。 対話型<xref:System.Windows.Controls.Page>の次の例に示すように、マークアップと分離コードの組み合わせを使用して実装されます。  
  
 [!code-xaml[XBAPAppDefSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml#homepagemarkup)]  
  
 [!code-csharp[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml.cs#homepagecodebehind)]
 [!code-vb[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/HomePage.xaml.vb#homepagecodebehind)]  
  
 マークアップ ファイルと分離コード ファイルを連携させるには、次の構成が必要です。  
  
-   マークアップでは、`Page`要素を含める必要があります、`x:Class`属性。 ときに、アプリケーションがビルドが存在する`x:Class`ファイルにより、マークアップで[!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)]を作成する、`partial`クラスから派生した<xref:System.Windows.Controls.Page>によって指定された名前を持つ、`x:Class`属性。 追加する必要があります、[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]名前空間宣言、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]スキーマ ( `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"` )。 生成された`partial`クラスが実装する`InitializeComponent`イベントが登録され、プロパティを設定すると呼ばれる、マークアップで実装されます。  
  
-   分離コード クラスがある必要があります、`partial`によって指定される同じ名前のクラス、`x:Class`のマークアップ、およびその属性がから派生する必要があります<xref:System.Windows.Controls.Page>します。 これにより、分離コード ファイルに関連付けられる、`partial`アプリケーションのビルド時にマークアップ ファイル用に生成されたクラス (を参照してください[WPF アプリケーションのビルド](building-a-wpf-application-wpf.md))。  
  
-   分離コードで、<xref:System.Windows.Controls.Page>クラスを呼び出すコンス トラクターを実装する必要があります、`InitializeComponent`メソッド。 `InitializeComponent` 実装ファイルの生成されたマークアップによって`partial`イベントを登録し、マークアップで定義されているプロパティを設定するクラス。  
  
> [!NOTE]
>  新しいを追加すると<xref:System.Windows.Controls.Page>を使用してプロジェクトに[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]、<xref:System.Windows.Controls.Page>マークアップと分離コードの両方を使用して実装としてマークアップと分離コード ファイル間の関連付けを作成するために必要な構成が含まれていますここで説明します。  
  
 作成したら、 <xref:System.Windows.Controls.Page>、そこに移動できます。 最初に指定する<xref:System.Windows.Controls.Page>に移動するアプリケーションを開始を構成する必要がある<xref:System.Windows.Controls.Page>します。  
  
<a name="Configuring_a_Start_Page"></a>   
### <a name="configuring-a-start-page"></a>スタート ページの構成  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] では、一定の量のアプリケーション インフラストラクチャをブラウザーでホストする必要があります。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]、<xref:System.Windows.Application>クラスは、必要なアプリケーション インフラストラクチャを確立するアプリケーション定義の一部 (を参照してください[アプリケーション管理の概要](application-management-overview.md))。  
  
 アプリケーション定義として構成されているマークアップ ファイルを使用してマークアップと分離コードの両方を使用して、通常、実装、 [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `ApplicationDefinition`項目。 用のアプリケーション定義を次に、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]します。  
  
 [!code-xaml[XBAPAppDefSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]  
  
 [!code-csharp[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml.cs#xbapapplicationdefinitioncodebehind)]
 [!code-vb[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/Application.xaml.vb#xbapapplicationdefinitioncodebehind)]  
  
 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 、アプリケーション定義を使用して、開始を指定できます<xref:System.Windows.Controls.Page>、これは、<xref:System.Windows.Controls.Page>を自動的に読み込まれるときに、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]が起動します。 これを行う、<xref:System.Windows.Application.StartupUri%2A>プロパティを[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]目的の<xref:System.Windows.Controls.Page>します。  
  
> [!NOTE]
>  ほとんどの場合、<xref:System.Windows.Controls.Page>がアプリケーションと共に配置またはにコンパイルします。 このような場合、[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]を識別する、<xref:System.Windows.Controls.Page>パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]、これは、[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]に準拠した、*パック*スキーム。 パック[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]については、説明でさらに[WPF におけるパック Uri](pack-uris-in-wpf.md)します。 以下で説明する http スキームを使用してコンテンツにナビゲートすることもできます。  
  
 設定できる<xref:System.Windows.Application.StartupUri%2A>次の例に示すように、マークアップで宣言します。  
  
 [!code-xaml[NavigationOverviewSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]  
  
 この例で、`StartupUri`属性が設定され、相対パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]HomePage.xaml を識別します。 ときに、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]が起動すると、HomePage.xaml が自動的に移動し、表示します。 次の図は、これを示します、 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] Web サーバーからを起動されました。  
  
 ![XBAP ページ](./media/navigation-overview/xbap-launched-from-a-web-server.png "Web サーバーから起動した XBAP が表示されます。")  
  
> [!NOTE]
>  開発と展開に関する詳細については[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]を参照してください[WPF XAML ブラウザー アプリケーションの概要](wpf-xaml-browser-applications-overview.md)と[WPF アプリケーションの配置](deploying-a-wpf-application-wpf.md)します。  
  
<a name="ConfiguringAXAMLPage"></a>   
### <a name="configuring-the-host-windows-title-width-and-height"></a>ホスト ウィンドウのタイトル、幅、および高さの構成  
 前の図からお気付きの 1 つは、ブラウザーとタブのパネルのタイトルが、[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]の[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]します。 このタイトルは、長いだけでなく、見た目が良いわけでも、有益な情報になっているわけでもありません。 このため、<xref:System.Windows.Controls.Page>を設定してタイトルを変更する方法を提供する、<xref:System.Windows.Controls.Page.WindowTitle%2A>プロパティ。 ブラウザー ウィンドウの高さと幅を構成を設定するさらに、<xref:System.Windows.Controls.Page.WindowWidth%2A>と<xref:System.Windows.Controls.Page.WindowHeight%2A>、それぞれします。  
  
 <xref:System.Windows.Controls.Page.WindowTitle%2A>、 <xref:System.Windows.Controls.Page.WindowWidth%2A>、および<xref:System.Windows.Controls.Page.WindowHeight%2A>設定できます宣言によってマークアップでは、次の例に示すようにします。  
  
 [!code-xaml[NavigationOverviewSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/HomePage.xaml#homepagemarkup)]  
  
 結果を次の例に示します。  
  
 ![ウィンドウのタイトル、高さ、幅](./media/navigation-overview/window-title-width-height.png "表示ウィンドウのタイトル、高さ、および幅を構成することができます。")  
  
<a name="NavigatingBetweenXAMLPages"></a>   
### <a name="hyperlink-navigation"></a>ハイパーリンクのナビゲーション  
 一般的な[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]はいくつかのページで構成されます。 別に 1 つのページから移動する最も簡単な方法が使用するには、<xref:System.Windows.Documents.Hyperlink>します。 宣言を追加することができます、<xref:System.Windows.Documents.Hyperlink>を<xref:System.Windows.Controls.Page>を使用して、`Hyperlink`要素で、次のマークアップに表示されます。  
  
 [!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]  
  
 A`Hyperlink`要素には、次が必要です。  
  
-   パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]の<xref:System.Windows.Controls.Page>に移動するで指定されたとおり、`NavigateUri`属性。  
  
-   テキストやイメージなど、ナビゲーションを開始するユーザーがクリックするコンテンツ (コンテンツを`Hyperlink`要素が含まれてを参照してください<xref:System.Windows.Documents.Hyperlink>)。  
  
 次に示します、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]で、<xref:System.Windows.Controls.Page>を持つ、<xref:System.Windows.Documents.Hyperlink>します。  
  
 ![ハイパーリンクを含むページ](./media/navigation-overview/xbap-with-a-page-with-a-hyperlink.png "XBAP ハイパーリンクが設定されたページが表示されます。")  
  
 次のものを予想どおりをクリックすると、<xref:System.Windows.Documents.Hyperlink>により、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]に移動する、<xref:System.Windows.Controls.Page>によって識別される、`NavigateUri`属性。 さらに、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]前のエントリを追加します。<xref:System.Windows.Controls.Page>で最近表示したページの一覧に[!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]します。 これを次の図に示します。  
  
 ![戻るボタンと進むボタン](./media/navigation-overview/back-and-forward-navigation.png "戻る ボタンと進むボタンに移動します。")  
  
 1 つからナビゲーションをサポートすることに加えて<xref:System.Windows.Controls.Page>、<xref:System.Windows.Documents.Hyperlink>フラグメントのナビゲーションもサポートしています。  
  
<a name="FragmentNavigation"></a>   
### <a name="fragment-navigation"></a>フラグメント ナビゲーション  
 *フラグメント ナビゲーション*いずれかでコンテンツ フラグメントへの移動は現在、<xref:System.Windows.Controls.Page>別または<xref:System.Windows.Controls.Page>します。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]、コンテンツ フラグメントは、名前付きの要素によって格納されているコンテンツ。 名前付き要素を持つ要素は、その`Name`属性に設定します。 次のマークアップを示しています、名前付き`TextBlock`コンテンツ フラグメントを含む要素。  
  
 [!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup1)]  
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup2)]  
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup3)]  
  
 <xref:System.Windows.Documents.Hyperlink>コンテンツ フラグメントに移動する、`NavigateUri`属性は、次を含める必要があります。  
  
-   [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]の<xref:System.Windows.Controls.Page>コンテンツ フラグメントに移動するとします。  
  
-   「#」文字。  
  
-   要素の名前、<xref:System.Windows.Controls.Page>コンテンツ フラグメントを格納しています。  
  
 フラグメント[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]形式は、次のとおりです。  
  
 *PageURI* `#` *ElementName*  
  
 次の例を示しています、`Hyperlink`コンテンツ フラグメントにナビゲートする構成されています。  
  
 [!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml1)]  
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml2)]  
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml3)]  
  
> [!NOTE]
>  既定のフラグメント ナビゲーション実装について説明[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]します。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 部分的に処理が必要ですが、独自のフラグメント ナビゲーション スキームを実装することもできます、<xref:System.Windows.Navigation.NavigationService.FragmentNavigation?displayProperty=nameWithType>イベント。  
  
> [!IMPORTANT]
>  疎でのフラグメントにナビゲートできる[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ページ (マークアップのみ[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を使用するファイル`Page`ルート要素として) を使用して、ページを参照できる場合にのみ[!INCLUDE[TLA2#tla_http](../../../../includes/tla2sharptla-http-md.md)]します。  
>   
>  ただし、loose[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ページは、独自のフラグメントにナビゲートできます。  
  
<a name="NavigationService"></a>   
### <a name="navigation-service"></a>ナビゲーション サービス  
 中に<xref:System.Windows.Documents.Hyperlink>により、ユーザーを特定のナビゲーションを開始する<xref:System.Windows.Controls.Page>、検索およびダウンロード ページの作業を行った、<xref:System.Windows.Navigation.NavigationService>クラス。 基本的に、<xref:System.Windows.Navigation.NavigationService>など、クライアント コードの代わりのナビゲーション要求を処理する機能を提供、<xref:System.Windows.Documents.Hyperlink>します。 さらに、<xref:System.Windows.Navigation.NavigationService>追跡したり、ナビゲーション要求の影響を与えての上位レベルのサポートを実装します。  
  
 ときに、<xref:System.Windows.Documents.Hyperlink>がクリックされた[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]呼び出し<xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType>検索とダウンロード、 <xref:System.Windows.Controls.Page> 、指定されたパック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]します。 ダウンロードした<xref:System.Windows.Controls.Page>がルート オブジェクトは、ダウンロードしたインスタンス オブジェクトのツリーに変換されます<xref:System.Windows.Controls.Page>します。 ルートへの参照を<xref:System.Windows.Controls.Page>にオブジェクトが格納されている、<xref:System.Windows.Navigation.NavigationService.Content%2A?displayProperty=nameWithType>プロパティ。 パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]でに移動したコンテンツが格納されているため、<xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType>プロパティ中、 <xref:System.Windows.Navigation.NavigationService.CurrentSource%2A?displayProperty=nameWithType> 、パックを格納[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]最後のページに移動した先の。  
  
> [!NOTE]
>  可能性があります、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]アプリケーションに 1 つ以上の現在アクティブな<xref:System.Windows.Navigation.NavigationService>します。 詳細については、[ナビゲーション ホスト](#Navigation_Hosts)このトピックで後述を参照してください。  
  
<a name="Programmatic_Navigation_with_the_Navigation_Service"></a>   
### <a name="programmatic-navigation-with-the-navigation-service"></a>ナビゲーション サービスによるプログラム ナビゲーション  
 について知っておく必要はありません<xref:System.Windows.Navigation.NavigationService>ナビゲーションを使用してマークアップで宣言によって実装されている場合<xref:System.Windows.Documents.Hyperlink>ため、<xref:System.Windows.Documents.Hyperlink>を使用して、<xref:System.Windows.Navigation.NavigationService>あなたの代わりにします。 つまり、間の直接または間接の親を<xref:System.Windows.Documents.Hyperlink>ナビゲーション ホストは、(を参照してください[ナビゲーション ホスト](#Navigation_Hosts))、<xref:System.Windows.Documents.Hyperlink>を見つけて、ナビゲーション ホストのナビゲーション サービスを使用して処理できる、ナビゲーション要求。  
  
 ただし場合もありますを使用する必要がある<xref:System.Windows.Navigation.NavigationService>を直接、次を含みます。  
  
-   インスタンスを作成する必要がある場合、<xref:System.Windows.Controls.Page>既定以外のコンス トラクターを使用します。  
  
-   プロパティを設定する必要がある場合、<xref:System.Windows.Controls.Page>そこに移動する前にします。  
  
-   ときに、<xref:System.Windows.Controls.Page>こと必要がありますにナビゲートすることができますのみが実行時に決定します。  
  
 このような状況では、プログラムで呼び出すことによってナビゲーションを開始するコードを記述する必要があります、<xref:System.Windows.Navigation.NavigationService.Navigate%2A>のメソッド、<xref:System.Windows.Navigation.NavigationService>オブジェクト。 参照を取得する必要があります<xref:System.Windows.Navigation.NavigationService>します。  
  
#### <a name="getting-a-reference-to-the-navigationservice"></a>NavigationService への参照の取得  
 覆われる上の理由から、[ナビゲーション ホスト](#Navigation_Hosts) セクションで、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]アプリケーションでは 1 つ以上<xref:System.Windows.Navigation.NavigationService>します。 これは、コードを見つけることが必要があることを意味する<xref:System.Windows.Navigation.NavigationService>、これは通常、<xref:System.Windows.Navigation.NavigationService>現在にナビゲートした<xref:System.Windows.Controls.Page>。 参照を取得することができます、<xref:System.Windows.Navigation.NavigationService>呼び出すことによって、 `static` <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A?displayProperty=nameWithType>メソッド。 取得する、<xref:System.Windows.Navigation.NavigationService>特定にナビゲートした<xref:System.Windows.Controls.Page>への参照を渡す、<xref:System.Windows.Controls.Page>の引数として、<xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A>メソッド。 次のコードを取得する方法を示しています、 <xref:System.Windows.Navigation.NavigationService> 、現在の<xref:System.Windows.Controls.Page>します。  
  
 [!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind1)]  
[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPage.xaml.vb#getnscodebehind2)]  
  
 検索するショートカットとして、<xref:System.Windows.Navigation.NavigationService>の<xref:System.Windows.Controls.Page>、<xref:System.Windows.Controls.Page>実装、<xref:System.Windows.Controls.Page.NavigationService%2A>プロパティ。 これを次の例に示します。  
  
 [!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind1)]  
[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPageShortCut.xaml.vb#getnsshortcutcodebehind2)]  
  
> [!NOTE]
>  A<xref:System.Windows.Controls.Page>のみへの参照を取得できます、<xref:System.Windows.Navigation.NavigationService>とき<xref:System.Windows.Controls.Page>発生させる、<xref:System.Windows.FrameworkElement.Loaded>イベント。  
  
#### <a name="programmatic-navigation-to-a-page-object"></a>ページ オブジェクトへのプログラム ナビゲーション  
 次の例は、使用する方法を示します、<xref:System.Windows.Navigation.NavigationService>にプログラムで移動する、<xref:System.Windows.Controls.Page>します。 プログラム ナビゲーションが必要な<xref:System.Windows.Controls.Page>は移動先のみインスタンス化できる、既定以外の 1 つのコンス トラクターを使用します。 <xref:System.Windows.Controls.Page>既定以外のコンス トラクターでの次のマークアップとコードに示します。  
  
 [!code-xaml[NavigationOverviewSnippets#PageWithNonDefaultConstructorXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml#pagewithnondefaultconstructorxaml)]  
  
 [!code-csharp[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml.cs#pagewithnondefaultconstructorcodebehind)]
 [!code-vb[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithNonDefaultConstructor.xaml.vb#pagewithnondefaultconstructorcodebehind)]  
  
 <xref:System.Windows.Controls.Page>にナビゲートする、<xref:System.Windows.Controls.Page>既定以外のコンス トラクターでの次のマークアップとコードに示します。  
  
 [!code-xaml[NavigationOverviewSnippets#NSNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml#nsnavigationpagexaml)]  
  
 [!code-csharp[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml.cs#nsnavigationpagecodebehind)]
 [!code-vb[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSNavigationPage.xaml.vb#nsnavigationpagecodebehind)]  
  
 ときに、<xref:System.Windows.Documents.Hyperlink>この<xref:System.Windows.Controls.Page>がクリックされると、ナビゲーションがインスタンス化によって開始される、<xref:System.Windows.Controls.Page>既定以外のコンス トラクターを使用して、呼び出しに移動する、<xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType>メソッド。 <xref:System.Windows.Navigation.NavigationService.Navigate%2A> オブジェクトへの参照を受け取りますが、<xref:System.Windows.Navigation.NavigationService>パックではなくに移動します[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]します。  
  
#### <a name="programmatic-navigation-with-a-pack-uri"></a>パック URI によるプログラム ナビゲーション  
 パックを構築する必要がある場合[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]プログラムで (できますのみを決定する場合、パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]実行時に、たとえばで)、使用することができます、<xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType>メソッド。 これを次の例に示します。  
  
 [!code-xaml[NavigationOverviewSnippets#NSUriNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml#nsurinavigationpagexaml)]  
  
 [!code-csharp[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml.cs#nsurinavigationpagecodebehind)]
 [!code-vb[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSUriNavigationPage.xaml.vb#nsurinavigationpagecodebehind)]  
  
#### <a name="refreshing-the-current-page"></a>現在のページの更新  
 A<xref:System.Windows.Controls.Page>同じパックがある場合はダウンロードされません[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]パックとして[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]に格納されている、<xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType>プロパティ。 強制的に[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]、現在のページを再度ダウンロードするには、呼び出すことができます、<xref:System.Windows.Navigation.NavigationService.Refresh%2A?displayProperty=nameWithType>メソッドを次の例に示すようにします。  
  
 [!code-xaml[NavigationOverviewSnippets#NSRefreshNavigationPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml#nsrefreshnavigationpagexaml1)]  
  
 [!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind1)]
 [!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind1)]  
[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind2)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind2)]  
  
<a name="Navigation_Lifetime"></a>   
### <a name="navigation-lifetime"></a>ナビゲーションの有効期間  
 これまでに説明したように、ナビゲーションを開始するには多くの方法があります。 ナビゲーションが開始されると、ナビゲーションの進行中は、追跡し、によって実装される次のイベントを使用して、ナビゲーションに影響を与える場合<xref:System.Windows.Navigation.NavigationService>:  
  
-   <xref:System.Windows.Navigation.NavigationService.Navigating>。 新しいナビゲーションが要求されたときに発生します。 ナビゲーションのキャンセルに使用できます。  
  
-   <xref:System.Windows.Navigation.NavigationService.NavigationProgress>。 ナビゲーション進行状況の情報提供を目的として、ダウンロード中に定期的に発生します。  
  
-   <xref:System.Windows.Navigation.NavigationService.Navigated>。 ページの位置が特定され、ダウンロードされたときに発生します。  
  
-   <xref:System.Windows.Navigation.NavigationService.NavigationStopped>。 ナビゲーションが停止しているときに発生します (呼び出して<xref:System.Windows.Navigation.NavigationService.StopLoading%2A>)、現在のナビゲーションの進行中に新しいナビゲーションが要求された場合またはします。  
  
-   <xref:System.Windows.Navigation.NavigationService.NavigationFailed>。 要求されたコンテンツにナビゲートするときにエラーが発生したときに発生します。  
  
-   <xref:System.Windows.Navigation.NavigationService.LoadCompleted>。 ナビゲート先のコンテンツが読み込まれ、解析されて、レンダリングが開始されたときに発生します。  
  
-   <xref:System.Windows.Navigation.NavigationService.FragmentNavigation>。 コンテンツ フラグメントへのナビゲーションが開始されたときに、次のタイミングで発生します。  
  
    -   目的のフラグメントが現在のコンテンツの場合は、すぐに発生します。  
  
    -   目的のフラグメントが別のコンテンツにある場合は、ソース コンテンツが読み込まれた後で発生します。  
  
 ナビゲーション イベントは、次の図に示されている順序で発生します。  
  
 ![ページ ナビゲーションのフロー チャート](./media/navigation-overview/order-of-navigation-events.png "ページ ナビゲーション イベントのフロー チャート")  
  
 一般に、<xref:System.Windows.Controls.Page>これらのイベントについて心配はありません。 アプリケーションはそれらに関係し、そのため、これらのイベントはによってこと可能性が高く、<xref:System.Windows.Application>クラス。  
  
-   <xref:System.Windows.Application.Navigating?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.NavigationProgress?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.Navigated?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.NavigationFailed?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.NavigationStopped?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.LoadCompleted?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Application.FragmentNavigation?displayProperty=nameWithType>  
  
 たびに<xref:System.Windows.Navigation.NavigationService>イベントを発生させる、<xref:System.Windows.Application>クラスは、対応するイベントを発生させます。 <xref:System.Windows.Controls.Frame> <xref:System.Windows.Navigation.NavigationWindow>それぞれのスコープ内のナビゲーションを検出するために同じイベントを提供します。  
  
 場合によってで、<xref:System.Windows.Controls.Page>これらのイベントに興味をもたれるかもしれません。 たとえば、<xref:System.Windows.Controls.Page>が処理、<xref:System.Windows.Navigation.NavigationService.Navigating?displayProperty=nameWithType>ナビゲーションをキャンセルするかどうかを決定するイベントです。 これを次の例に示します。  
  
 [!code-xaml[NavigationOverviewSnippets#CancelNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml#cancelnavigationpagexaml)]  
  
 [!code-csharp[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml.cs#cancelnavigationpagecodebehind)]
 [!code-vb[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/CancelNavigationPage.xaml.vb#cancelnavigationpagecodebehind)]  
  
 ナビゲーション イベントにハンドラーを登録するかどうか、 <xref:System.Windows.Controls.Page>、イベント ハンドラーの登録解除もする必要があるように前の例では、します。 方法に関して、副作用がある可能性がありますしない場合は、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]ナビゲーションを記憶<xref:System.Windows.Controls.Page>ナビゲーション履歴を使用します。  
  
<a name="NavigationHistory"></a>   
### <a name="remembering-navigation-with-the-journal"></a>履歴によるナビゲーションの記憶  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は、戻るスタックと進むスタックの 2 つのスタックを使用して、ナビゲート元のページを記憶します。 現在から移動すると<xref:System.Windows.Controls.Page>を新しい<xref:System.Windows.Controls.Page>を既存の前方または<xref:System.Windows.Controls.Page>、現在<xref:System.Windows.Controls.Page>に追加されます、*戻るスタック*します。 現在から移動すると<xref:System.Windows.Controls.Page>、以前に<xref:System.Windows.Controls.Page>、現在<xref:System.Windows.Controls.Page>に追加されます、*進むスタック*します。 戻るスタック、進むスタック、およびそれらを管理する機能を、まとめて履歴と呼びます。 戻るスタックと進むスタック内の各項目のインスタンスである、<xref:System.Windows.Navigation.JournalEntry>クラスし、呼びます、*仕訳*します。  
  
#### <a name="navigating-the-journal-from-internet-explorer"></a>Internet Explorer からの履歴のナビゲート  
 概念的には、履歴は、同じ方法、**戻る**と**フォワード**ボタン[!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]の操作を行います。 これを次の図に示します。  
  
 ![戻るボタンと進むボタン](./media/navigation-overview/back-and-forward-navigation.png "戻る ボタンと進むボタンに移動します。")  
  
 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]によってホストされる[!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]ナビゲーション履歴に統合[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]の[!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]します。 内のページを移動することができます、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]を使用して、**戻る**、**フォワード**と**最近表示したページ**ボタン[!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]します。 ジャーナルは統合されません[!INCLUDE[TLA2#tla_ie6](../../../../includes/tla2sharptla-ie6-md.md)]は同じ方法で[!INCLUDE[TLA2#tla_ie7](../../../../includes/tla2sharptla-ie7-md.md)]または Internet Explorer 8。 代わりに、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]レンダリング、代替ナビゲーション[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]します。  
  
> [!IMPORTANT]
>  [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]との間でナビゲートするときに戻す、 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]、アライブされなかったページの履歴項目のみが履歴に保持されます。 ページを履歴に保持する方法の詳細については、[ページの有効期間と履歴](#PageLifetime)このトピックで後述を参照してください。  
  
 既定で各テキスト<xref:System.Windows.Controls.Page>に表示される、**最近表示したページ**の一覧[!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]は、[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]の<xref:System.Windows.Controls.Page>します。 多くの場合、これは、ユーザーにとって特に意味がありません。 幸い、次のオプションのいずれかを使用して、テキストを変更できます。  
  
1.  関連付けられている`JournalEntry.Name`属性の値。  
  
2.  `Page.Title`属性の値。  
  
3.  `Page.WindowTitle`属性の値と[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]、現在の<xref:System.Windows.Controls.Page>します。  
  
4.  現在の [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] の <xref:System.Windows.Controls.Page>。 (既定)  
  
 これらのオプションの順序は、テキスト検索の優先順位と一致します。 たとえば場合、`JournalEntry.Name`が設定された場合、その他の値は無視されます。  
  
 次の例では、`Page.Title`履歴エントリに表示されるテキストを変更する属性。  
  
 [!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup1)]  
[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup2)]  
  
 [!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind1)]
 [!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind1)]  
[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind2)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind2)]  
  
#### <a name="navigating-the-journal-using-wpf"></a>WPF を使用する履歴のナビゲート  
 ユーザーは、ジャーナルを使用して移動できますが、**戻る**、**フォワード**、および**最近表示したページ**で[!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]、両方を使用して、ジャーナルを移動することもできます。によって提供される宣言およびプログラム メカニズム[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]します。 これを行う理由の 1 つはカスタム ナビゲーションを提供する[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]ページにします。  
  
 によって公開されるナビゲーション コマンドを使用して宣言によって履歴ナビゲーション サポートを追加できます<xref:System.Windows.Input.NavigationCommands>します。 次の例では、使用する方法、`BrowseBack`ナビゲーション コマンド。  
  
 [!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml1)]  
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml2)]  
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml3)]  
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML4](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml4)]  
  
 プログラムでの次のメンバーのいずれかを使用して、ジャーナルを移動することができます、<xref:System.Windows.Navigation.NavigationService>クラス。  
  
-   <xref:System.Windows.Navigation.NavigationService.GoBack%2A>  
  
-   <xref:System.Windows.Navigation.NavigationService.GoForward%2A>  
  
-   <xref:System.Windows.Navigation.NavigationService.CanGoBack%2A>  
  
-   <xref:System.Windows.Navigation.NavigationService.CanGoForward%2A>  
  
 履歴で説明したように、プログラムで操作することも[ナビゲーション履歴によるコンテンツ状態の保持](#RetainingContentStateWithNavigationHistory)このトピックで後述します。  
  
<a name="PageLifetime"></a>   
### <a name="page-lifetime-and-the-journal"></a>ページの有効期間と履歴  
 検討してください、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]リッチ コンテンツを含むいくつかのページで、グラフィックス、アニメーション、およびメディアを含むです。 このようなページのメモリ使用量は、特にビデオやオーディオ メディアが使用されている場合、非常に大きくなることがあります。 仕訳帳「記憶」ページに移動されていること、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]がすばやく、大規模で顕著な量のメモリを消費します。  
  
 このため、履歴の既定の動作は、格納する<xref:System.Windows.Controls.Page>への参照ではなく、各履歴エントリ内のメタデータを<xref:System.Windows.Controls.Page>オブジェクト。 履歴エントリに移動したとき、<xref:System.Windows.Controls.Page>メタデータは、指定の新しいインスタンスを作成するために使用<xref:System.Windows.Controls.Page>します。 その結果、各<xref:System.Windows.Controls.Page>ナビゲートする有効期間は、次の図で示されています。  
  
 ![ページの有効期間](./media/navigation-overview/navigated-page-lifetime.png "ページを移動するときに有効期間が表示されます。")  
  
 既定の履歴の動作を使用してメモリの消費量に保存してできます、ページごとのレンダリングのパフォーマンスが低下する可能性があります。<xref:System.Windows.Controls.Page>時間のかかる、大量のコンテンツがある場合に特にをすることができます。 保持する必要がある場合、<xref:System.Windows.Controls.Page>インスタンス、journal では、これを行うための 2 つの手法に描画できます。 最初に、プログラムでに移動すること、<xref:System.Windows.Controls.Page>オブジェクトを呼び出すことによって、<xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType>メソッド。  
  
 第 2 に、ことを指定できる[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]のインスタンスを保持、<xref:System.Windows.Controls.Page>を設定して、journal で、<xref:System.Windows.Controls.Page.KeepAlive%2A>プロパティを`true`(既定値は`false`)。 次の例に示すように設定できる<xref:System.Windows.Controls.Page.KeepAlive%2A>マークアップで宣言します。  
  
 [!code-xaml[NavigationOverviewSnippets#KeepAlivePageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/KeepAlivePage.xaml#keepalivepagexaml)]  
  
 有効期間、<xref:System.Windows.Controls.Page>は微妙に異なるされていないからでは有効のまま保持します。 初めて、<xref:System.Windows.Controls.Page>されるアライブが移動先と同じようにインスタンス化される、<xref:System.Windows.Controls.Page>がキープ ア ライブされません。 ただし、ためのインスタンス、<xref:System.Windows.Controls.Page>は保持されます、journal では、そのインスタンスを作成しませんもう一度の仕訳帳に残っている限りです。 そのため場合、<xref:System.Windows.Controls.Page>たびに呼び出される必要がある初期化ロジックを持つ、<xref:System.Windows.Controls.Page>ナビゲートする必要がありますから移動コンス トラクターにハンドラーを<xref:System.Windows.FrameworkElement.Loaded>イベント。 次の図に示すように、<xref:System.Windows.FrameworkElement.Loaded>と<xref:System.Windows.FrameworkElement.Unloaded>イベントは発生するたびに、<xref:System.Windows.Controls.Page>がナビゲート先およびからは、それぞれします。  
  
 ![Loaded および Unloaded イベントが発生した場合](./media/navigation-overview/loaded-and-unloaded-events.png "ページとの間の移動が Loaded および unloaded イベントが発生します。")  
  
 ときに、<xref:System.Windows.Controls.Page>がキープ アライブされず、実行しないで、次のいずれか。  
  
-   ページへの参照、またはその一部への参照を格納する。  
  
-   ページによって実装されていないイベントのイベント ハンドラーを登録する。  
  
 これらのいずれかの方法を強制する参照を作成、<xref:System.Windows.Controls.Page>履歴から削除された後でも、メモリに保持されます。  
  
 一般に、既定値を優先すべき<xref:System.Windows.Controls.Page>は、<xref:System.Windows.Controls.Page>アライブします。 ただし、これには、次のセクションで説明されている状態も関係します。  
  
<a name="RetainingContentStateWithNavigationHistory"></a>   
### <a name="retaining-content-state-with-navigation-history"></a>ナビゲーション履歴によるコンテンツの状態の保持  
 場合、<xref:System.Windows.Controls.Page>がキープ アライブされず、との間でナビゲートする場合に戻すと、データへの動作、ユーザーからデータを収集するコントロールを持っている、<xref:System.Windows.Controls.Page>でしょうか。 ユーザー エクスペリエンスの観点から見ると、ユーザーは以前に入力したデータが表示されることを期待します。 残念ながら、ための新しいインスタンス、<xref:System.Windows.Controls.Page>各ナビゲーションで収集されたデータが再インスタンス化されて、データが失われたコントロールが作成されます。  
  
 さいわい、ジャーナルは間でデータを記憶しておくのサポートを提供<xref:System.Windows.Controls.Page>コントロール データを含むナビゲーション。 具体的には、各履歴<xref:System.Windows.Controls.Page>関連付けられている一時的なコンテナーとして機能します<xref:System.Windows.Controls.Page>状態。 次の手順は、このサポートの使用方法を説明と、<xref:System.Windows.Controls.Page>ナビゲートします。  
  
1.  現在のエントリ<xref:System.Windows.Controls.Page>履歴に追加されます。  
  
2.  状態、<xref:System.Windows.Controls.Page>戻るスタックに追加される、そのページの履歴エントリに格納されます。  
  
3.  新しい<xref:System.Windows.Controls.Page>にナビゲートするとします。  
  
 ときにページ<xref:System.Windows.Controls.Page>が journal を使用して移動する、次の手順が実行します。  
  
1.  <xref:System.Windows.Controls.Page> (戻るスタック上の最上位の履歴エントリ) をインスタンス化します。  
  
2.  <xref:System.Windows.Controls.Page>の履歴エントリに格納された状態で更新されますが、<xref:System.Windows.Controls.Page>します。  
  
3.  <xref:System.Windows.Controls.Page>に移動します。  
  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 次のコントロールを使用すると自動的にこのサポートを使用して、 <xref:System.Windows.Controls.Page>:  
  
-   <xref:System.Windows.Controls.CheckBox>  
  
-   <xref:System.Windows.Controls.ComboBox>  
  
-   <xref:System.Windows.Controls.Expander>  
  
-   <xref:System.Windows.Controls.Frame>  
  
-   <xref:System.Windows.Controls.ListBox>  
  
-   <xref:System.Windows.Controls.ListBoxItem>  
  
-   <xref:System.Windows.Controls.MenuItem>  
  
-   <xref:System.Windows.Controls.ProgressBar>  
  
-   <xref:System.Windows.Controls.RadioButton>  
  
-   <xref:System.Windows.Controls.Slider>  
  
-   <xref:System.Windows.Controls.TabControl>  
  
-   <xref:System.Windows.Controls.TabItem>  
  
-   <xref:System.Windows.Controls.TextBox>  
  
 場合、<xref:System.Windows.Controls.Page>制御これらは、これらに入力されたデータをまたいで記憶されます<xref:System.Windows.Controls.Page>ナビゲーションに示すように、**好きな色**<xref:System.Windows.Controls.ListBox>次の図。  
  
 ![状態を記憶するコントロールを含むページ](./media/navigation-overview/data-remembered-across-page-navigations.png "入力されたデータは、ページ ナビゲーション間をまたいで記憶されます。")  
  
 ときに、<xref:System.Windows.Controls.Page>上記の一覧にないコントロールを持っているか、カスタム オブジェクトの状態が保存されると、履歴に間で状態を記憶するコードを記述する必要があります。<xref:System.Windows.Controls.Page>ナビゲーション。  
  
 少量の間で状態情報を覚えておかなければならないかどうか<xref:System.Windows.Controls.Page>ナビゲーション、依存関係プロパティを使用することができます (を参照してください<xref:System.Windows.DependencyProperty>) で構成されている、<xref:System.Windows.FrameworkPropertyMetadata.Journal%2A?displayProperty=nameWithType>メタデータ フラグ。  
  
 場合、状態を<xref:System.Windows.Controls.Page>ナビゲーション間をまたいで記憶する必要があるデータの複数の部分で構成される場合があります、少ないコードでは、1 つのクラスの状態をカプセル化して実装する処理を要する、<xref:System.Windows.Navigation.IProvideCustomContentState>インターフェイス。  
  
 かどうかは、1 つのさまざまな状態をナビゲートする必要があります<xref:System.Windows.Controls.Page>からはナビゲートせず、<xref:System.Windows.Controls.Page>使える自体、<xref:System.Windows.Navigation.IProvideCustomContentState>と<xref:System.Windows.Navigation.NavigationService.AddBackEntry%2A?displayProperty=nameWithType>します。  
  
<a name="Cookies"></a>   
### <a name="cookies"></a>クッキー  
 もう 1 つ方法[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]アプリケーションは、データを格納できますが、作成されると、cookie に次のように更新、および削除を使用して、<xref:System.Windows.Application.SetCookie%2A>と<xref:System.Windows.Application.GetCookie%2A>メソッド。 作成できる cookie[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]クッキーと同じことを他の種類の Web アプリケーションの使用は、cookie は、中、またはアプリケーション セッション全体で、クライアント コンピューター上のアプリケーションによって格納されているデータの任意の部分。 クッキー データは、通常、次の形式の名前と値のペアです。  
  
 *Name* `=` *Value*  
  
 データが渡された場合<xref:System.Windows.Application.SetCookie%2A>、と共に、<xref:System.Uri>の cookie を設定する場所、cookie は、メモリ内に作成し、のみ入手可能になったアプリケーションの現在のセッションの実行中です。 この種類の cookie と呼びます、*セッション cookie*します。  
  
 複数のアプリケーション セッションにまたがってクッキーを格納するには、次の形式を使用して、有効期限をクッキーに追加する必要があります。  
  
 *NAME* `=` *VALUE* `; expires=DAY, DD-MMM-YYYY HH:MM:SS GMT`  
  
 現在の有効期限の cookie が格納されている[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]cookie の有効期限が切れるまでのインストールのインターネット一時ファイル フォルダー。 このような cookie と呼ばれる、*永続的なクッキー*アプリケーション セッションをまたいでいるためです。  
  
 セッションと永続的な cookie の両方を呼び出すことで取得した、<xref:System.Windows.Application.GetCookie%2A>渡して、メソッド、<xref:System.Uri>で cookie を設定した場所の場所の<xref:System.Windows.Application.SetCookie%2A>メソッド。  
  
 クッキーがサポートされている方法の一部を次に[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]:  
  
-   [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] スタンドアロン アプリケーションと[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]両方を作成して cookie を管理します。  
  
-   によって作成された cookie を[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]ブラウザーからアクセスできます。  
  
-   同じドメインの [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] は、クッキーを作成して共有できます。  
  
-   [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]同じドメインからのページは作成し、cookie を共有します。  
  
-   クッキーがディスパッチと[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]や loose[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ページが Web 要求を行います。  
  
-   最上位レベルの両方[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]と[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]でホストされている IFRAME がクッキーにアクセスできます。  
  
-   クッキーのサポート[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]のサポートされているすべてのブラウザーで同じです。  
  
-   [!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]、クッキーに関する P3P ポリシーはで受け入れられます[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]、ファースト パーティおよびサード パーティ製に関して特に[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]します。  
  
<a name="Structured_Navigation"></a>   
### <a name="structured-navigation"></a>構造化ナビゲーション  
 1 つからデータを渡す必要がある場合<xref:System.Windows.Controls.Page>別にすることができます、データに引数として渡すの既定以外のコンス トラクター、<xref:System.Windows.Controls.Page>します。 この手法を使用する場合しなければならないことに注意してください、<xref:System.Windows.Controls.Page>に移動する場合、次回、生きて、 <xref:System.Windows.Controls.Page>、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]再インスタンス化、<xref:System.Windows.Controls.Page>既定のコンス トラクターを使用しています。  
  
 または、<xref:System.Windows.Controls.Page>渡す必要があるデータと設定されているプロパティを実装することができます。 処理がただし、注意が必要になります、ときに、<xref:System.Windows.Controls.Page>必要がありますを渡すためにデータを戻す、<xref:System.Windows.Controls.Page>にナビゲートしました。 問題があるナビゲーションはネイティブでサポート メカニズムを保証する、<xref:System.Windows.Controls.Page>からは、ナビゲート後に返されます。 基本的に、ナビゲーションは、"呼び出す/戻る" というセマンティクスをサポートしていません。 この問題を解決する[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]提供、<xref:System.Windows.Navigation.PageFunction%601>いることを確認するために使用できるクラス、<xref:System.Windows.Controls.Page>が予測可能な構造化された方法で返されます。 詳細については、[構造化ナビゲーションの概要](structured-navigation-overview.md)を参照してください。  
  
<a name="The_NavigationWindow_Class"></a>   
## <a name="the-navigationwindow-class"></a>NavigationWindow クラス  
 ここまでで、ナビゲート可能なコンテンツを含むアプリケーションをビルドするために使用する可能性が最も高いナビゲーション サービスの全容を説明しました。 これらのサービスは、のコンテキストで説明した[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]に限定されてはいませんが、[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]します。 最新のオペレーティング システムと Windows アプリケーションにブラウザー スタイルのナビゲーションをスタンドアロン アプリケーションに組み込む現代のユーザーのブラウザーの経験を活用します。 一般的な例は、次のとおりです。  
  
-   **Word の類義語辞典**:選択された語を移動します。  
  
-   **ファイル エクスプ ローラー**:ファイルとフォルダーを移動します。  
  
-   **ウィザード**:複雑なタスクの間で移動できる複数のページを分割します。 たとえば、Windows コンポーネント ウィザードを追加して、Windows の機能の削除を処理するなどです。  
  
 ブラウザー スタイルのナビゲーションをスタンドアロン アプリケーションに組み込むを使用することができます、<xref:System.Windows.Navigation.NavigationWindow>クラス。 <xref:System.Windows.Navigation.NavigationWindow> 派生した<xref:System.Windows.Window>が拡張され、同じナビゲーション サポートと[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]を提供します。 使用することができます<xref:System.Windows.Navigation.NavigationWindow>スタンドアロン アプリケーションのメイン ウィンドウ、またはダイアログ ボックスなどの 2 次ウィンドウとして。  
  
 実装する、<xref:System.Windows.Navigation.NavigationWindow>の最上位レベルのほとんどのクラスと同様に、 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] (<xref:System.Windows.Window>、<xref:System.Windows.Controls.Page>など)、マークアップと分離コードの組み合わせを使用します。 これを次の例に示します。  
  
 [!code-xaml[IntroToNavNavigationWindowSnippets#NavigationWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml#navigationwindowmarkup)]  
  
 [!code-csharp[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml.cs#navigationwindowcodebehind)]
 [!code-vb[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/MainWindow.xaml.vb#navigationwindowcodebehind)]  
  
 このコードを作成、<xref:System.Windows.Navigation.NavigationWindow>に自動的にナビゲートする、 <xref:System.Windows.Controls.Page> (HomePage.xaml) ときに、<xref:System.Windows.Navigation.NavigationWindow>が開きます。 場合、<xref:System.Windows.Navigation.NavigationWindow>アプリケーションのメイン ウィンドウは、使用することができます、`StartupUri`属性を起動します。 これを次のマークアップに示します。  
  
 [!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchNavWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/App.xaml#applaunchnavwindow)]  
  
 次に示します、<xref:System.Windows.Navigation.NavigationWindow>スタンドアロン アプリケーションのメイン ウィンドウとして。  
  
 ![メイン ウィンドウ](./media/navigation-overview/navigation-window-as-main-window.png "のメイン ウィンドウとナビゲーション ウィンドウ")  
  
 図からを確認できます、<xref:System.Windows.Navigation.NavigationWindow>では設定されなかった場合でも、タイトルが付いて、<xref:System.Windows.Navigation.NavigationWindow>前の例のコードを実装します。 タイトルを設定を使用して、代わりに、<xref:System.Windows.Controls.Page.WindowTitle%2A>プロパティで、次のコードに示します。  
  
 [!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup1)]  
[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup2)]  
  
 設定、<xref:System.Windows.Controls.Page.WindowWidth%2A>と<xref:System.Windows.Controls.Page.WindowHeight%2A>プロパティにも影響、<xref:System.Windows.Navigation.NavigationWindow>します。  
  
 通常、実装する独自<xref:System.Windows.Navigation.NavigationWindow>動作や外観をカスタマイズする必要がある場合。 どちらも行わない場合は、ショートカットを使用できます。 パックを指定する場合[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]の<xref:System.Windows.Controls.Page>として、<xref:System.Windows.Application.StartupUri%2A>をスタンドアロン アプリケーションで<xref:System.Windows.Application>が自動的に作成、<xref:System.Windows.Navigation.NavigationWindow>ホストに、 <xref:System.Windows.Controls.Page>。 次のマークアップは、この方法を示しています。  
  
 [!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchPage](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/AnotherApp.xaml#applaunchpage)]  
  
 セカンダリ アプリケーション ウィンドウにする ダイアログ ボックスなどをするかどうか、<xref:System.Windows.Navigation.NavigationWindow>を開きます次の例では、コードを使用することができます。  
  
 [!code-csharp[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/DialogOwnerWindow.xaml.cs#createnwdialogbox)]
 [!code-vb[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/DialogOwnerWindow.xaml.vb#createnwdialogbox)]  
  
 次の図に、結果を示します。  
  
 ![ダイアログ ボックス](./media/navigation-overview/navigation-window-as-dialog-box.png " ダイアログ ボックスのナビゲーション ウィンドウ")  
  
 ご覧のとおり、<xref:System.Windows.Navigation.NavigationWindow>が表示されます[!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]-スタイル**戻る**と**フォワード**履歴をナビゲートできるようにボタン。 これらのボタンは、次の図に示されているように、同じユーザー エクスペリエンスを提供します。  
  
 ![Navigationwindow の前後](./media/navigation-overview/back-and-forward-buttons-in-navigation-window.png "前後のナビゲーション ウィンドウのボタン")  
  
 非表示にする場合は、ページは、独自の履歴ナビゲーション サポートと UI を提供する、**戻る**と**フォワード**で表示されるボタン<xref:System.Windows.Navigation.NavigationWindow>の値を設定して、 <xref:System.Windows.Navigation.NavigationWindow.ShowsNavigationUI%2A> プロパティ`false`.  
  
 カスタマイズのサポートを使用する代わりに、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]を置き換える、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]の<xref:System.Windows.Navigation.NavigationWindow>自体。  
  
<a name="Frame_in_Standalone_Applications"></a>   
## <a name="the-frame-class"></a>Frame クラス  
 両方のブラウザーと<xref:System.Windows.Navigation.NavigationWindow>ナビゲート可能なコンテンツをホストを windows には。 場合によっては、アプリケーションには、ウィンドウ全体でホストする必要のないコンテンツがあることもあります。 このようなコンテンツは、代わりに、他のコンテンツ内でホストされます。 その他のコンテンツにナビゲート可能なコンテンツを挿入するにを使用して、<xref:System.Windows.Controls.Frame>クラス。 <xref:System.Windows.Controls.Frame> 同じサポートを提供します<xref:System.Windows.Navigation.NavigationWindow>と[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]します。  
  
 次の例は、追加する方法を示します、<xref:System.Windows.Controls.Frame>を<xref:System.Windows.Controls.Page>を使用して宣言によって、`Frame`要素。  
  
 [!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml1)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml2)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml3)]  
  
 このマークアップは、`Source`の属性、`Frame`パックを持つ要素[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]の<xref:System.Windows.Controls.Page>を<xref:System.Windows.Controls.Frame>最初にナビゲートする必要があります。 次に示します、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]で、<xref:System.Windows.Controls.Page>を持つ、<xref:System.Windows.Controls.Frame>いくつかのページ間を移動します。  
  
 ![複数のページ間を移動したフレーム](./media/navigation-overview/frame-navigation-between-multiple-pages.png "複数のページ間のフレームのナビゲーションが表示されます。")  
  
 のみでは、使用する必要はありません<xref:System.Windows.Controls.Frame>コンテンツの内部に、<xref:System.Windows.Controls.Page>します。 共通するホストも、<xref:System.Windows.Controls.Frame>コンテンツの内部に、<xref:System.Windows.Window>します。  
  
 既定では、<xref:System.Windows.Controls.Frame>のみ別の履歴がない場合は、独自の履歴を使用します。 場合、<xref:System.Windows.Controls.Frame>内でホストされているコンテンツの一部である、<xref:System.Windows.Navigation.NavigationWindow>または[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]、<xref:System.Windows.Controls.Frame>が属している、ジャーナルを使用して、<xref:System.Windows.Navigation.NavigationWindow>または[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]。 場合によっては、ただし、<xref:System.Windows.Controls.Frame>独自の履歴を担当する必要があります。 これを行う理由の 1 つがによってホストされているページ内で履歴ナビゲーションを許可するには、<xref:System.Windows.Controls.Frame>します。 これを次の図に示します。  
  
 ![フレームとページのダイアグラム](./media/navigation-overview/journal-navigation-within-pages-hosted-by-a-frame.png "フレームでホストされているページ内で履歴ナビゲーションが表示されます。")  
  
 この場合、構成することができます、<xref:System.Windows.Controls.Frame>設定して、独自の履歴を使用する、<xref:System.Windows.Controls.Frame.JournalOwnership%2A>のプロパティ、<xref:System.Windows.Controls.Frame>に<xref:System.Windows.Navigation.JournalOwnership.OwnsJournal>します。 これを次のマークアップに示します。  
  
 [!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml1)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml2)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml3)]  
  
 次の図は内での移動の効果を示しています、<xref:System.Windows.Controls.Frame>独自の履歴を使用します。  
  
 ![独自の履歴を使用するフレーム](./media/navigation-overview/frame-uses-its-own-journal.png "これは、独自の履歴を使用するフレーム内での移動の効果を示しています。")  
  
 通知の履歴エントリはナビゲーションによって示されている[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]で、<xref:System.Windows.Controls.Frame>ではなく[!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]します。  
  
> [!NOTE]
>  場合、<xref:System.Windows.Controls.Frame>でホストされているコンテンツの一部である、 <xref:System.Windows.Window>、<xref:System.Windows.Controls.Frame>独自の履歴を使用し、その結果、独自のナビゲーションを表示します。[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]します。  
  
 ユーザー エクスペリエンスが必要な場合、<xref:System.Windows.Controls.Frame>ナビゲーションを表示することがなく、独自の履歴を提供する[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]、ナビゲーションを非表示にすることができます[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]を設定して、<xref:System.Windows.Controls.Frame.NavigationUIVisibility%2A>に<xref:System.Windows.Visibility.Hidden>します。 これを次のマークアップに示します。  
  
 [!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml1)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml2)]  
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml3)]  
  
<a name="Navigation_Hosts"></a>   
## <a name="navigation-hosts"></a>ナビゲーション ホスト  
 <xref:System.Windows.Controls.Frame> <xref:System.Windows.Navigation.NavigationWindow>ナビゲーション ホストと呼ばれるクラスします。 A*ナビゲーション ホスト*に移動して、コンテンツを表示できるクラスです。 これを実現する各ナビゲーション ホストは、独自<xref:System.Windows.Navigation.NavigationService>ジャーナルとします。 ナビゲーション ホストの基本的な構造を次の図に示します。  
  
 ![ナビゲーターのダイアグラム](./media/navigation-overview/navigation-host-construction.png "ナビゲーション ホストの基本的な構造")  
  
 これにより、基本的に、<xref:System.Windows.Navigation.NavigationWindow>と<xref:System.Windows.Controls.Frame>同等ナビゲーションをサポートする、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]ブラウザーでホストされている場合に提供します。  
  
 使用しただけでなく<xref:System.Windows.Navigation.NavigationService>と、journal では、ナビゲーション ホストは、同じメンバーを実装する<xref:System.Windows.Navigation.NavigationService>を実装します。 これを次の図に示します。  
  
 ![フレームおよび NavigationWindow 内のジャーナル](./media/navigation-overview/navigation-window-and-frame.png "ナビゲーション ウィンドウとフレーム")  
  
 これにより、これらのメンバーに対して直接、ナビゲーション サポートをプログラミングできます。 カスタム ナビゲーションを提供する必要がある場合は、これを検討できます[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]の<xref:System.Windows.Controls.Frame>でホストされる、<xref:System.Windows.Window>します。 さらに、両方の種類の実装を含む、追加のナビゲーション関連のメンバー `BackStack` (<xref:System.Windows.Navigation.NavigationWindow.BackStack%2A?displayProperty=nameWithType>、 <xref:System.Windows.Controls.Frame.BackStack%2A?displayProperty=nameWithType>) と`ForwardStack`(<xref:System.Windows.Navigation.NavigationWindow.ForwardStack%2A?displayProperty=nameWithType>、 <xref:System.Windows.Controls.Frame.ForwardStack%2A?displayProperty=nameWithType>)、バックアップの履歴エントリを列挙できますスタックが作成され、それぞれ、スタックを転送します。  
  
 前に述べたように、アプリケーション内に複数の履歴が存在することがあります。 次の図は、この例を示しています。  
  
 ![1 つのアプリケーション内の複数の履歴](./media/navigation-overview/multiple-journals-in-one-application.png "これは、アプリケーションでは、複数の journal の例です。")  
  
<a name="Navigating_to_Content_Other_than_Pages"></a>   
## <a name="navigating-to-content-other-than-xaml-pages"></a>XAML ページ以外のコンテンツへのナビゲート  
 このトピックでは、全体で<xref:System.Windows.Controls.Page>と pack[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]のさまざまなナビゲーション機能のデモンストレーションに使用されている[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]します。 ただし、<xref:System.Windows.Controls.Page>つまり移動できるコンテンツと pack の唯一の型でないアプリケーションにコンパイル[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]コンテンツを識別する唯一の方法はありません。  
  
 緩やかに移動できますもここに示す、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイル、[!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]ファイル、およびオブジェクト。  
  
<a name="Navigating_to_Loose_XAML_Files"></a>   
### <a name="navigating-to-loose-xaml-files"></a>Loose XAML ファイルへのナビゲート  
 Loose[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイルは、次の特性を持つファイル。  
  
-   のみを含む[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)](つまり、コードなし)。  
  
-   適切な名前空間宣言がある。  
  
-   .xaml ファイル名拡張子を持つ。  
  
 たとえば、loose として格納されている次の内容[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]Person.xaml ファイルします。  
  
 [!code-xaml[NavigationOverviewSnippets#LooseXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Person.xaml#loosexaml)]  
  
 ファイルをダブルクリックすると、ブラウザーが開き、コンテンツにナビゲートして、コンテンツを表示します。 これを次の図に示します。  
  
 ![Person.XAML ファイルのコンテンツの表示](./media/navigation-overview/contents-of-person-xaml-file.png "Person.XAML ファイルの内容を示しています。")  
  
 Loose を表示する[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、次からのファイル。  
  
-   ローカル コンピューター、イントラネット、またはインターネット上の Web サイト。  
  
-   A[!INCLUDE[TLA#tla_unc](../../../../includes/tlasharptla-unc-md.md)]ファイル共有。  
  
-   ローカル ディスク。  
  
 Loose[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイルは、ブラウザーのお気に入りに追加できるか、ブラウザーのホーム ページにあります。  
  
> [!NOTE]
>  公開と疎起動の詳細については[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、ページを参照してください[WPF アプリケーションの配置](deploying-a-wpf-application-wpf.md)します。  
  
 Loose に関して制限事項の 1 つ[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]が部分信頼で実行しても安全なコンテンツをホストすることのみできます。 たとえば、 `Window` loose のルート要素にすることはできません[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイル。 詳細については、[WPF 部分信頼セキュリティ](../wpf-partial-trust-security.md)を参照してください。  
  
<a name="Navigating_to_HTML_Files_Using_Frame"></a>   
### <a name="navigating-to-html-files-by-using-frame"></a>フレームを使用した HTML ファイルへのナビゲート  
 移動できますもご想像のとおり、[!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]します。 単に提供する必要があります、 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] http スキームを使用します。 たとえば、次[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を示しています、<xref:System.Windows.Controls.Frame>にナビゲートする、[!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]ページ。  
  
 [!code-xaml[NavigationOverviewSnippets#FrameHtmlNavMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHTMLNavPage.xaml#framehtmlnavmarkup)]  
  
 移動する[!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]特殊なアクセス許可が必要です。 たとえばから移動することはできません、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]インターネット ゾーン部分信頼セキュリティ サンド ボックスで実行されています。 詳細については、[WPF 部分信頼セキュリティ](../wpf-partial-trust-security.md)を参照してください。  
  
<a name="Navigating_to_HTML_Files_Using_WebBrowser"></a>   
### <a name="navigating-to-html-files-by-using-the-webbrowser-control"></a>WebBrowser コントロールを使用した HTML ファイルへのナビゲート  
 <xref:System.Windows.Controls.WebBrowser>サポートを制御[!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]ドキュメントのホスティング、ナビゲーション、およびスクリプト/マネージ コードの相互運用性。 詳細についてはに関する、<xref:System.Windows.Controls.WebBrowser>コントロールを参照してください<xref:System.Windows.Controls.WebBrowser>します。  
  
 ような<xref:System.Windows.Controls.Frame>に移動する、[!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]を使用して<xref:System.Windows.Controls.WebBrowser>特殊なアクセス許可が必要です。 たとえば、部分的に信頼されたアプリケーションから移動できますにのみ[!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]起点のサイトにあります。 詳細については、[WPF 部分信頼セキュリティ](../wpf-partial-trust-security.md)を参照してください。  
  
<a name="Navigating_to_Objects"></a>   
### <a name="navigating-to-custom-objects"></a>カスタム オブジェクトへのナビゲート  
 カスタム オブジェクトとして格納されているデータがある場合は、そのデータを表示する方法の 1 つは、作成、<xref:System.Windows.Controls.Page>それらのオブジェクトにバインドされているコンテンツを含む (を参照してください[データ バインディングの概要](../data/data-binding-overview.md))。 オブジェクトを表示するためだけにページ全体を作成するオーバーヘッドが必要ない場合には、代わりに、オブジェクトに直接ナビゲートすることもできます。  
  
 検討してください、`Person`次のコードで実装されているクラス。  
  
 [!code-csharp[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/Person.cs#personclasscode)]
 [!code-vb[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/Person.vb#personclasscode)]  
  
 それに移動するを呼び出す、<xref:System.Windows.Navigation.NavigationWindow.Navigate%2A?displayProperty=nameWithType>メソッドは、次のコードに示すようにします。  
  
 [!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject1)]  
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject2)]  
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject3)]  
  
 [!code-csharp[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml.cs#pagethatnavstoobjectcodebehind)]
 [!code-vb[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/HomePage.xaml.vb#pagethatnavstoobjectcodebehind)]  
  
 次の図に、結果を示します。  
  
 ![クラスに移動するページ](./media/navigation-overview/page-navigates-to-an-object.png "オブジェクトに移動するページの例になります。")  
  
 この図には、役立つものが何も表示されていません。 表示される値の戻り値は、実際には、`ToString`のメソッド、 **Person**オブジェクト。 既定では、これは、唯一の値[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]オブジェクトの表示に使用できます。 オーバーライドして、`ToString`に意味のある情報を返すことが、それでもメソッドは文字列値のみができます。 1 つの手法が使用することができますのプレゼンテーション機能を活用した[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]データ テンプレートを使用することです。 データ テンプレートを実装することができますを[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]特定の種類のオブジェクトと関連付けることができます。 次のコードはデータ テンプレートを`Person`オブジェクト。  
  
 [!code-xaml[NavigateToObjectSnippets#DataTemplateMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/App.xaml#datatemplatemarkup)]  
  
 ここでは、データ テンプレートに関連付けられている、`Person`型を使用して、`x:Type`のマークアップ拡張機能、`DataType`属性。 データ テンプレートにバインドし、`TextBlock`要素 (を参照してください<xref:System.Windows.Controls.TextBlock>) のプロパティに、`Person`クラス。 次の図は、の更新された外観を示しています。、`Person`オブジェクト。  
  
 ![データ テンプレートを持つクラスへの移動](./media/navigation-overview/navigating-to-a-class.png "データ テンプレートを持つクラスに移動します。")  
  
 この方法の利点は、データ テンプレートを再利用して、アプリケーションの任意の場所で オブジェクトを一貫して表示できることによって得られる一貫性です。  
  
 データ テンプレートの詳細については、[データ テンプレートの概要](../data/data-templating-overview.md)を参照してください。  
  
<a name="Security"></a>   
## <a name="security"></a>セキュリティ  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ナビゲーション サポートによって[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]に、インターネットとの間で移動するのには、サード パーティ コンテンツをホストするアプリケーション。 有害な動作からのアプリケーションとユーザーの両方を保護する[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]のさまざまな記載されているセキュリティ機能を提供します。[セキュリティ](../security-wpf.md)と[WPF 部分信頼セキュリティ](../wpf-partial-trust-security.md)します。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Application.SetCookie%2A>
- <xref:System.Windows.Application.GetCookie%2A>
- [アプリケーション管理の概要](application-management-overview.md)
- [WPF におけるパッケージの URI](pack-uris-in-wpf.md)
- [構造化ナビゲーションの概要](structured-navigation-overview.md)
- [ナビゲーション トポロジの概要](navigation-topologies-overview.md)
- [方法トピック](navigation-how-to-topics.md)
- [WPF アプリケーションの配置](deploying-a-wpf-application-wpf.md)
