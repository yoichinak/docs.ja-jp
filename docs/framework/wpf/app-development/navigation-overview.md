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
ms.openlocfilehash: 874bc0b1b0ac38210569632dc3d21ed727ae26e4
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291649"
---
# <a name="navigation-overview"></a>ナビゲーションの概要

Windows Presentation Foundation (WPF) では、スタンドアロンアプリケーションと [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] の2種類のアプリケーションで使用できるブラウザースタイルのナビゲーションがサポートされています。 コンテンツをナビゲーション用にパッケージ化するために、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は <xref:System.Windows.Controls.Page> クラスを提供します。 @No__t-1 を使用するか、プログラムによって <xref:System.Windows.Navigation.NavigationService> を使用して、1つの @no__t ~ 0 から別のに、宣言によって移動できます。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は、ナビゲート元のページを記憶し、それらのページに戻るために、履歴を使用します。

<xref:System.Windows.Controls.Page>、<xref:System.Windows.Documents.Hyperlink>、<xref:System.Windows.Navigation.NavigationService>、およびジャーナルは、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] で提供されるナビゲーションサポートの中核となります。 この概要では、これらの機能について詳しく説明した後、@no__t 0 のファイル、HTML ファイル、およびオブジェクトへの移動を含む高度なナビゲーションサポートについて説明します。

> [!NOTE]
> このトピックでは、"browser" という用語は、現在 Microsoft Internet Explorer および Firefox を含む @no__t 0 アプリケーションをホストできるブラウザーのみを指します。 特定の [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 機能が特定のブラウザーでのみサポートされている場合は、ブラウザーのバージョンが参照されます。

## <a name="navigation-in-wpf-applications"></a>WPF アプリケーションでのナビゲーション

このトピックでは [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] の主要なナビゲーション機能の概要について説明します。 これらの機能は、スタンドアロンアプリケーションと [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] の両方で使用できます。ただし、このトピックでは、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] のコンテキスト内でこれらの機能を示します。

> [!NOTE]
> このトピックでは [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] をビルドして展開する方法については説明しません。 @No__t 0 の詳細については、「 [WPF XAML ブラウザーアプリケーションの概要](wpf-xaml-browser-applications-overview.md)」を参照してください。

このセクションでは、ナビゲーションの次の側面について説明し、例を示します。

- [ページの実装](#CreatingAXAMLPage)

- [スタート ページの構成](#Configuring_a_Start_Page)

- [ホスト ウィンドウのタイトル、幅、および高さの構成](#ConfiguringAXAMLPage)

- [ハイパーリンクのナビゲーション](#NavigatingBetweenXAMLPages)

- [フラグメント ナビゲーション](#FragmentNavigation)

- [ナビゲーション サービス](#NavigationService)

- [ナビゲーション サービスによるプログラム ナビゲーション](#Programmatic_Navigation_with_the_Navigation_Service)

- [ナビゲーションの有効期間](#Navigation_Lifetime)

- [履歴によるナビゲーションの記憶](#NavigationHistory)

- [ページの有効期間と履歴](#PageLifetime)

- [ナビゲーション履歴によるコンテンツの状態の保持](#RetainingContentStateWithNavigationHistory)

- [Cookie](#Cookies)

- [構造化ナビゲーション](#Structured_Navigation)

<a name="CreatingAXAMLPage"></a>

### <a name="implementing-a-page"></a>ページの実装

@No__t 0 の場合、.NET Framework オブジェクト、カスタムオブジェクト、列挙値、ユーザーコントロール、@no__t 1 ファイル、HTML ファイルなど、いくつかのコンテンツの種類に移動できます。 ただし、コンテンツをパッケージ化する最も一般的で便利な方法は、<xref:System.Windows.Controls.Page> を使用することです。 さらに、<xref:System.Windows.Controls.Page> は、外観を向上させ、開発を簡素化するために、ナビゲーション固有の機能を実装します。

@No__t-0 を使用すると、次のようなマークアップを使用して、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] コンテンツのナビゲート可能なページを宣言によって実装できます。

[!code-xaml[NavigationOverviewSnippets#Page1XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page1.xaml#page1xaml)]

@No__t-1 マークアップに実装されている @no__t 0 は、ルート要素として `Page` を持ち、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] @ no__t-4 名前空間宣言を必要とします。 @No__t-0 要素には、移動して表示するコンテンツが含まれています。 コンテンツを追加するには、次のマークアップに示すように、`Page.Content` プロパティ要素を設定します。

[!code-xaml[NavigationOverviewSnippets#Page2XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page2.xaml#page2xaml)]

`Page.Content` には、1 つの子要素のみを含めることができます。前の例では、コンテンツは単一の文字列「Hello, Page!」です。 実際には、通常はレイアウトコントロールを子要素として使用し (「[レイアウト](../advanced/layout.md)」を参照)、コンテンツを格納して構成します。

@No__t-0 要素の子要素は、<xref:System.Windows.Controls.Page> のコンテンツと見なされます。したがって、明示的な `Page.Content` 宣言を使用する必要はありません。 次のマークアップは、前のサンプルの宣言と同等です。

[!code-xaml[NavigationOverviewSnippets#Page3XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page3.xaml#page3xaml)]

この場合、`Page.Content` は、`Page` 要素の子要素で自動的に設定されます。 詳細については、「[WPF のコンテンツ モデル](../controls/wpf-content-model.md)」を参照してください。

マークアップのみの <xref:System.Windows.Controls.Page> は、コンテンツを表示する場合に便利です。 ただし、<xref:System.Windows.Controls.Page> は、ユーザーがページと対話できるようにするコントロールを表示することもできます。また、イベントを処理し、アプリケーションロジックを呼び出すことによって、ユーザーの操作に応答できます。 次の例に示すように、マークアップと分離コードの組み合わせを使用して、対話型の @no__t 0 が実装されます。

[!code-xaml[XBAPAppDefSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml#homepagemarkup)]

[!code-csharp[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml.cs#homepagecodebehind)]
[!code-vb[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/HomePage.xaml.vb#homepagecodebehind)]

マークアップ ファイルと分離コード ファイルを連携させるには、次の構成が必要です。

- マークアップでは、@no__t 0 要素に `x:Class` 属性が含まれている必要があります。 アプリケーションのビルド時にマークアップファイルに `x:Class` が存在すると、Microsoft build engine (MSBuild) によって、<xref:System.Windows.Controls.Page> から派生し、`x:Class` 属性によって指定された名前を持つ @no__t 1 クラスが作成されます。 そのためには、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] スキーマ (`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`) に [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] 名前空間宣言を追加する必要があります。 生成された `partial` クラスは `InitializeComponent` を実装します。これは、イベントを登録し、マークアップで実装されるプロパティを設定するために呼び出されます。

- 分離コードでは、クラスは、マークアップで `x:Class` 属性によって指定された名前と同じ名前の @no__t 0 クラスである必要があり、<xref:System.Windows.Controls.Page> から派生する必要があります。 これにより、分離コードファイルは、アプリケーションのビルド時にマークアップファイル用に生成される @no__t 0 クラスに関連付けることができます (「 [WPF アプリケーションのビルド](building-a-wpf-application-wpf.md)」を参照してください)。

- 分離コードでは、@no__t 0 クラスは、`InitializeComponent` メソッドを呼び出すコンストラクターを実装する必要があります。 `InitializeComponent` は、マークアップファイルによって生成される `partial` クラスによって実装され、イベントを登録したり、マークアップで定義されているプロパティを設定したりします。

> [!NOTE]
> @No__t-1 を使用して新しい <xref:System.Windows.Controls.Page> をプロジェクトに追加すると、マークアップと分離コードの両方を使用して <xref:System.Windows.Controls.Page> が実装されます。また、ここで説明するように、マークアップファイルと分離コードファイルの関連付けを作成するために必要な構成が含まれます。

@No__t 0 になったら、その場所に移動できます。 アプリケーションがナビゲートする最初の @no__t 0 を指定するには、start <xref:System.Windows.Controls.Page> を構成する必要があります。

<a name="Configuring_a_Start_Page"></a>

### <a name="configuring-a-start-page"></a>スタート ページの構成

[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] では、一定の量のアプリケーション インフラストラクチャをブラウザーでホストする必要があります。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] では、<xref:System.Windows.Application> クラスは、必要なアプリケーションインフラストラクチャを確立するアプリケーション定義の一部です (「[アプリケーション管理の概要](application-management-overview.md)」を参照してください)。

通常、アプリケーション定義はマークアップと分離コードの両方を使用して実装され、マークアップファイルは MSBuild @ no__t-0 項目として構成されます。 @No__t-0 のアプリケーション定義を次に示します。

[!code-xaml[XBAPAppDefSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]

[!code-csharp[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml.cs#xbapapplicationdefinitioncodebehind)]
[!code-vb[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/Application.xaml.vb#xbapapplicationdefinitioncodebehind)]

@No__t-0 は、アプリケーション定義を使用して start <xref:System.Windows.Controls.Page> を指定できます。これは、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] の起動時に自動的に読み込まれる <xref:System.Windows.Controls.Page> です。 これを行うには、必要な <xref:System.Windows.Controls.Page> の [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] を指定して <xref:System.Windows.Application.StartupUri%2A> プロパティを設定します。

> [!NOTE]
> ほとんどの場合、@no__t 0 は、アプリケーションにコンパイルされるか、アプリケーションと共に配置されます。 このような場合、<xref:System.Windows.Controls.Page> を識別する @no__t 0 はパック [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] です。これは、*パック*スキームに準拠した @no__t 3 です。 Pack [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] については、「 [WPF のパック uri](pack-uris-in-wpf.md)」で詳しく説明します。 以下で説明する http スキームを使用してコンテンツにナビゲートすることもできます。

次の例に示すように、マークアップで <xref:System.Windows.Application.StartupUri%2A> を宣言によって設定できます。

[!code-xaml[NavigationOverviewSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]

この例では、`StartupUri` 属性に、ホームページを識別する相対パック [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] が設定されています。 @No__t 0 が起動すると、ホームページに自動的に移動して表示されます。 これは、次の図に示すように、Web サーバーから起動された @no__t 0 を示しています。

![Xbap ページ](./media/navigation-overview/xbap-launched-from-a-web-server.png "これは、Web サーバーから起動された xbap を示しています。")

> [!NOTE]
> @No__t-0 の開発と配置の詳細については、「 [WPF XAML ブラウザーアプリケーションの概要](wpf-xaml-browser-applications-overview.md)」および「 [Wpf アプリケーションの配置](deploying-a-wpf-application-wpf.md)」を参照してください。

<a name="ConfiguringAXAMLPage"></a>

### <a name="configuring-the-host-windows-title-width-and-height"></a>ホスト ウィンドウのタイトル、幅、および高さの構成

前の図では、ブラウザーとタブパネルの両方のタイトルが [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] の [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] であることがわかりました。 このタイトルは、長いだけでなく、見た目が良いわけでも、有益な情報になっているわけでもありません。 このため、<xref:System.Windows.Controls.Page> は、<xref:System.Windows.Controls.Page.WindowTitle%2A> プロパティを設定してタイトルを変更する方法を提供します。 さらに、<xref:System.Windows.Controls.Page.WindowWidth%2A> と <xref:System.Windows.Controls.Page.WindowHeight%2A> をそれぞれ設定して、ブラウザーウィンドウの幅と高さを構成できます。

<xref:System.Windows.Controls.Page.WindowTitle%2A>、<xref:System.Windows.Controls.Page.WindowWidth%2A>、および <xref:System.Windows.Controls.Page.WindowHeight%2A> は、次の例に示すように、マークアップで宣言によって設定できます。

[!code-xaml[NavigationOverviewSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/HomePage.xaml#homepagemarkup)]

結果を次の例に示します。

![[ウィンドウのタイトル]、[高さ]]、[幅] には、(./media/navigation-overview/window-title-width-height.png "構成できるウィンドウのタイトル、高さ、および幅が表示されます。")

<a name="NavigatingBetweenXAMLPages"></a>

### <a name="hyperlink-navigation"></a>ハイパーリンクのナビゲーション

一般的な @no__t 0 は複数のページで構成します。 あるページから別のページに移動する最も簡単な方法は、<xref:System.Windows.Documents.Hyperlink> を使用することです。 次のマークアップに示すように、`Hyperlink` 要素を使用して、<xref:System.Windows.Documents.Hyperlink> を宣言によって <xref:System.Windows.Controls.Page> に追加できます。

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

@No__t 0 要素には、次のものが必要です。

- @No__t-2 属性の指定に従って移動する <xref:System.Windows.Controls.Page> のパック [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。

- ユーザーがクリックしてナビゲーションを開始できるコンテンツ (@no__t 0 要素に含めることができるコンテンツについては、「<xref:System.Windows.Documents.Hyperlink>」を参照してください)。

次の図は、@no__t が2である <xref:System.Windows.Controls.Page> の @no__t 0 を示しています。

![ハイパーリンク付きページ](./media/navigation-overview/xbap-with-a-page-with-a-hyperlink.png "ハイパーリンクを含むページを含む XBAP を表示します。")

ご想像のとおり、<xref:System.Windows.Documents.Hyperlink> をクリックすると、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] が `NavigateUri` 属性で識別される <xref:System.Windows.Controls.Page> に移動します。 さらに、[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] は、Internet Explorer の [最近使ったページ] の一覧に前の <xref:System.Windows.Controls.Page> のエントリを追加します。 これを次の図に示します。

![[戻る] ボタン]と [進む] ボタン(./media/navigation-overview/back-and-forward-navigation.png "を使用すると、[戻る] および [進む] ボタンを操作できます。")

また、1つの @no__t から別のへのナビゲーションもサポートしています。また、<xref:System.Windows.Documents.Hyperlink> でもフラグメントナビゲーションがサポートされています。

<a name="FragmentNavigation"></a>

### <a name="fragment-navigation"></a>フラグメント ナビゲーション

*フラグメントナビゲーション*は、現在の <xref:System.Windows.Controls.Page> または別の <xref:System.Windows.Controls.Page> のコンテンツフラグメントへのナビゲーションです。 @No__t-0 では、コンテンツフラグメントは名前付き要素に含まれるコンテンツです。 名前付き要素は、@no__t 0 の属性セットを持つ要素です。 次のマークアップは、コンテンツフラグメントを含む名前付き `TextBlock` 要素を示しています。

[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup1)]
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup2)]
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup3)]

@No__t-0 がコンテンツフラグメントに移動するには、`NavigateUri` 属性に次のものが含まれている必要があります。

- コンテンツフラグメントが移動する <xref:System.Windows.Controls.Page> の [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。

- 「#」文字。

- コンテンツフラグメントを含む @no__t 0 の要素の名前。

フラグメント [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] の形式は次のとおりです。

*PageURI* `#` *ElementName*

コンテンツフラグメントに移動するように構成されている @no__t 0 の例を次に示します。

[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml1)]
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml2)]
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml3)]

> [!NOTE]
> このセクションでは、@no__t 0 での既定のフラグメントナビゲーション実装について説明します。 また、@no__t 0 を使用すると、独自のフラグメントナビゲーションスキームを実装することもできます。この場合、パートでは、<xref:System.Windows.Navigation.NavigationService.FragmentNavigation?displayProperty=nameWithType> イベントを処理する必要があります。

> [!IMPORTANT]
> ページを HTTP 経由で参照できる場合に限り、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ページ (マークアップのみ [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイル `Page`) のフラグメントをルート要素として使用できます。
>
> ただし、@no__t 0 ページがある場合は、それ自体のフラグメントに移動できます。

<a name="NavigationService"></a>

### <a name="navigation-service"></a>ナビゲーション サービス

@No__t-0 を使用すると、ユーザーは特定の <xref:System.Windows.Controls.Page> へのナビゲーションを開始できますが、ページの検索とダウンロードの作業は <xref:System.Windows.Navigation.NavigationService> クラスによって実行されます。 基本的に、<xref:System.Windows.Navigation.NavigationService> は、<xref:System.Windows.Documents.Hyperlink> などのクライアントコードに代わってナビゲーション要求を処理する機能を提供します。 さらに、<xref:System.Windows.Navigation.NavigationService> は、ナビゲーション要求の追跡と影響に対する上位レベルのサポートを実装します。

@No__t 0 がクリックされると、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> を呼び出して、指定したパック @no__t にある <xref:System.Windows.Controls.Page> を検索してダウンロードします。 ダウンロードした <xref:System.Windows.Controls.Page> は、ルートオブジェクトがダウンロードされた <xref:System.Windows.Controls.Page> のインスタンスであるオブジェクトのツリーに変換されます。 ルート <xref:System.Windows.Controls.Page> オブジェクトへの参照は、<xref:System.Windows.Navigation.NavigationService.Content%2A?displayProperty=nameWithType> プロパティに格納されます。 移動先のコンテンツのパック [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] は、<xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> プロパティに格納されます。一方、<xref:System.Windows.Navigation.NavigationService.CurrentSource%2A?displayProperty=nameWithType> は、移動先の最後のページのパック @no__t を格納します。

> [!NOTE]
> @No__t 0 のアプリケーションは、現在アクティブな @no__t を1つ以上持つことができます。 詳細については、このトピックで後述する「[ナビゲーションホスト](#Navigation_Hosts)」を参照してください。

<a name="Programmatic_Navigation_with_the_Navigation_Service"></a>

### <a name="programmatic-navigation-with-the-navigation-service"></a>ナビゲーション サービスによるプログラム ナビゲーション

@No__t-1 を使用してマークアップで宣言的にナビゲーションが実装されている場合、@no__t について認識する必要はありません。 <xref:System.Windows.Documents.Hyperlink> では、ユーザーに代わって <xref:System.Windows.Navigation.NavigationService> が使用されるためです。 つまり、@no__t 0 の直接または間接の親がナビゲーションホスト (「[ナビゲーション](#Navigation_Hosts)ホスト」を参照) である限り、@no__t はナビゲーションホストのナビゲーションサービスを検索して使用し、ナビゲーション要求を処理することができます。

ただし、次のように <xref:System.Windows.Navigation.NavigationService> を直接使用する必要がある場合もあります。

- パラメーター化されていないコンストラクターを使用して @no__t 0 をインスタンス化する必要がある場合。

- @No__t に移動する前に、そのプロパティを設定する必要がある場合。

- 移動する必要がある @no__t 0 は実行時にのみ決定できます。

このような状況では、<xref:System.Windows.Navigation.NavigationService> オブジェクトの @no__t 0 メソッドを呼び出すことによって、プログラムでナビゲーションを開始するコードを記述する必要があります。 @No__t への参照を取得する必要があります-0。

#### <a name="getting-a-reference-to-the-navigationservice"></a>NavigationService への参照の取得

「[ナビゲーションホスト](#Navigation_Hosts)」セクションで説明されている理由により、@no__t 1 のアプリケーションは複数の @no__t を持つことができます。 つまり、コードには @no__t 0 を検索する方法が必要です。これは通常、現在の @no__t に移動した <xref:System.Windows.Navigation.NavigationService> です。 @No__t 0 への参照を取得するには、`static` @ no__t-2 メソッドを呼び出します。 特定の @no__t に移動した @no__t 0 を取得するには、<xref:System.Windows.Controls.Page> への参照を <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A> メソッドの引数として渡します。 次のコードは、現在の <xref:System.Windows.Controls.Page> の @no__t を取得する方法を示しています。

[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind1)]
[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPage.xaml.vb#getnscodebehind2)]

@No__t-1 の <xref:System.Windows.Navigation.NavigationService> を見つけるためのショートカットとして、<xref:System.Windows.Controls.Page> は <xref:System.Windows.Controls.Page.NavigationService%2A> プロパティを実装します。 これを次の例に示します。

[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind1)]
[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPageShortCut.xaml.vb#getnsshortcutcodebehind2)]

> [!NOTE]
> @No__t-0 は、<xref:System.Windows.Controls.Page> が <xref:System.Windows.FrameworkElement.Loaded> イベントを発生させる場合にのみ、@no__t への参照を取得できます。

#### <a name="programmatic-navigation-to-a-page-object"></a>ページ オブジェクトへのプログラム ナビゲーション

次の例では、<xref:System.Windows.Navigation.NavigationService> を使用して、プログラムで <xref:System.Windows.Controls.Page> に移動する方法を示します。 移動先の @no__t 0 は、パラメーター化されていない単一のコンストラクターを使用してのみインスタンス化できるため、プログラムによるナビゲーションが必要です。 パラメーターなしのコンストラクターを持つ <xref:System.Windows.Controls.Page> は、次のマークアップとコードに示されています。

[!code-xaml[NavigationOverviewSnippets#PageWithNonDefaultConstructorXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml#pagewithnondefaultconstructorxaml)]

[!code-csharp[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml.cs#pagewithnondefaultconstructorcodebehind)]
[!code-vb[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithNonDefaultConstructor.xaml.vb#pagewithnondefaultconstructorcodebehind)]

パラメーターなしのコンストラクターを使用して <xref:System.Windows.Controls.Page> に移動する @no__t 0 は、次のマークアップとコードに示されています。

[!code-xaml[NavigationOverviewSnippets#NSNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml#nsnavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml.cs#nsnavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSNavigationPage.xaml.vb#nsnavigationpagecodebehind)]

この @no__t の <xref:System.Windows.Documents.Hyperlink> をクリックすると、<xref:System.Windows.Controls.Page> をインスタンス化して、パラメーター化されていないコンストラクターを使用し、<xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> メソッドを呼び出すことによって、ナビゲーションが開始されます。 <xref:System.Windows.Navigation.NavigationService.Navigate%2A> は、パック [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] ではなく、<xref:System.Windows.Navigation.NavigationService> が移動するオブジェクトへの参照を受け入れます。

#### <a name="programmatic-navigation-with-a-pack-uri"></a>パック URI によるプログラム ナビゲーション

プログラムを使用して @no__t パックを作成する必要がある場合 (たとえば、実行時にパック [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] を特定できる場合) は、<xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> メソッドを使用できます。 これを次の例に示します。

[!code-xaml[NavigationOverviewSnippets#NSUriNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml#nsurinavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml.cs#nsurinavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSUriNavigationPage.xaml.vb#nsurinavigationpagecodebehind)]

#### <a name="refreshing-the-current-page"></a>現在のページの更新

@No__t-0 は、<xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> プロパティに格納されているパック [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] と同じパック @no__t ある場合は、ダウンロードされません。 @No__t-0 に強制的に現在のページをダウンロードするには、次の例に示すように、<xref:System.Windows.Navigation.NavigationService.Refresh%2A?displayProperty=nameWithType> メソッドを呼び出すことができます。

[!code-xaml[NavigationOverviewSnippets#NSRefreshNavigationPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml#nsrefreshnavigationpagexaml1)]

[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind1)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind1)]
[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind2)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind2)]

<a name="Navigation_Lifetime"></a>

### <a name="navigation-lifetime"></a>ナビゲーションの有効期間

これまでに説明したように、ナビゲーションを開始するには多くの方法があります。 ナビゲーションが開始されていて、ナビゲーションの進行中に、<xref:System.Windows.Navigation.NavigationService> によって実装される次のイベントを使用してナビゲーションを追跡し、影響を与えることができます。

- <xref:System.Windows.Navigation.NavigationService.Navigating>。 新しいナビゲーションが要求されたときに発生します。 ナビゲーションのキャンセルに使用できます。

- <xref:System.Windows.Navigation.NavigationService.NavigationProgress>。 ナビゲーション進行状況の情報提供を目的として、ダウンロード中に定期的に発生します。

- <xref:System.Windows.Navigation.NavigationService.Navigated>。 ページの位置が特定され、ダウンロードされたときに発生します。

- <xref:System.Windows.Navigation.NavigationService.NavigationStopped>。 @No__t 0 を呼び出すことによって) ナビゲーションが停止したとき、または現在のナビゲーションの進行中に新しいナビゲーションが要求されたときに発生します。

- <xref:System.Windows.Navigation.NavigationService.NavigationFailed>。 要求されたコンテンツにナビゲートするときにエラーが発生したときに発生します。

- <xref:System.Windows.Navigation.NavigationService.LoadCompleted>。 ナビゲート先のコンテンツが読み込まれ、解析されて、レンダリングが開始されたときに発生します。

- <xref:System.Windows.Navigation.NavigationService.FragmentNavigation>。 コンテンツ フラグメントへのナビゲーションが開始されたときに、次のタイミングで発生します。

  - 目的のフラグメントが現在のコンテンツの場合は、すぐに発生します。

  - 目的のフラグメントが別のコンテンツにある場合は、ソース コンテンツが読み込まれた後で発生します。

ナビゲーション イベントは、次の図に示されている順序で発生します。

![ページナビゲーションフローチャート](./media/navigation-overview/order-of-navigation-events.png "ページナビゲーションイベントフローチャート")

一般に、このようなイベントについては、@no__t 0 は考慮されません。 多くの場合、アプリケーションで問題が発生する可能性があります。そのため、これらのイベントも <xref:System.Windows.Application> クラスによって発生します。

- <xref:System.Windows.Application.Navigating?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationProgress?displayProperty=nameWithType>

- <xref:System.Windows.Application.Navigated?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationFailed?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationStopped?displayProperty=nameWithType>

- <xref:System.Windows.Application.LoadCompleted?displayProperty=nameWithType>

- <xref:System.Windows.Application.FragmentNavigation?displayProperty=nameWithType>

@No__t-0 によってイベントが発生するたびに、<xref:System.Windows.Application> クラスによって対応するイベントが発生します。 <xref:System.Windows.Controls.Frame> および <xref:System.Windows.Navigation.NavigationWindow> は、それぞれのスコープ内のナビゲーションを検出するために同じイベントを提供します。

場合によっては、これらのイベントには @no__t 0 が必要になることがあります。 たとえば、<xref:System.Windows.Controls.Page> は、<xref:System.Windows.Navigation.NavigationService.Navigating?displayProperty=nameWithType> のイベントを処理して、ナビゲーションをキャンセルするかどうかを決定します。 これを次の例に示します。

[!code-xaml[NavigationOverviewSnippets#CancelNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml#cancelnavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml.cs#cancelnavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/CancelNavigationPage.xaml.vb#cancelnavigationpagecodebehind)]

前の例のように、<xref:System.Windows.Controls.Page> からのナビゲーションイベントを使用してハンドラーを登録する場合は、イベントハンドラーの登録を解除する必要もあります。 そうでない場合は、@no__t 0 のナビゲーションによって、履歴を使用して @no__t 1 のナビゲーションが記憶される方法に関して副作用が生じる可能性があります。

<a name="NavigationHistory"></a>

### <a name="remembering-navigation-with-the-journal"></a>履歴によるナビゲーションの記憶

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は、戻るスタックと進むスタックの 2 つのスタックを使用して、ナビゲート元のページを記憶します。 現在の <xref:System.Windows.Controls.Page> から新しい <xref:System.Windows.Controls.Page> に移動するか、既存の <xref:System.Windows.Controls.Page> に進むと、現在の <xref:System.Windows.Controls.Page> が*バックスタック*に追加されます。 現在の <xref:System.Windows.Controls.Page> から前の <xref:System.Windows.Controls.Page> に戻ると、現在の <xref:System.Windows.Controls.Page> が*前方スタック*に追加されます。 戻るスタック、進むスタック、およびそれらを管理する機能を、まとめて履歴と呼びます。 バックスタックと転送スタックの各項目は @no__t 0 クラスのインスタンスであり、*履歴エントリ*と呼ばれます。

#### <a name="navigating-the-journal-from-internet-explorer"></a>Internet Explorer からの履歴のナビゲート

概念的には、journal は Internet Explorer の **[戻る]** ボタンと **[進む]** ボタンと同じ方法で動作します。 これを次の図に示します。

![[戻る] ボタン]と [進む] ボタン(./media/navigation-overview/back-and-forward-navigation.png "を使用すると、[戻る] および [進む] ボタンを操作できます。")

Internet Explorer でホストされている @no__t 0 の場合、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は、journal を Internet Explorer の @no__t のナビゲーションに統合します。 これにより、ユーザーは Internet Explorer の **[戻る]** 、 **[進む]** 、 **[最近使ったページ]** の各ボタンを使用して、@no__t 0 のページに移動できます。

> [!IMPORTANT]
> Internet Explorer では、ユーザーが [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] に移動したときに、そのユーザーが保持されていないページの履歴項目だけが履歴に保持されます。 ページを維持したままにする方法については、このトピックで後述する「[ページの有効期間と履歴](#PageLifetime)」を参照してください。

既定では、Internet Explorer の **[最近使ったページ]** の一覧に表示される各 <xref:System.Windows.Controls.Page> のテキストは、<xref:System.Windows.Controls.Page> の [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] です。 多くの場合、これは、ユーザーにとって特に意味がありません。 幸い、次のオプションのいずれかを使用して、テキストを変更できます。

1. アタッチされている `JournalEntry.Name` 属性値。

2. @No__t-0 属性値。

3. @No__t-0 属性値と、現在の <xref:System.Windows.Controls.Page> の [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]。

4. 現在の [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] の <xref:System.Windows.Controls.Page>。 (既定)

これらのオプションの順序は、テキスト検索の優先順位と一致します。 たとえば、`JournalEntry.Name` を設定した場合、他の値は無視されます。

次の例では、`Page.Title` 属性を使用して、journal エントリに対して表示されるテキストを変更します。

[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup1)]
[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup2)]

[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind1)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind1)]
[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind2)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind2)]

#### <a name="navigating-the-journal-using-wpf"></a>WPF を使用する履歴のナビゲート

ユーザーは、Internet Explorer の **[戻る]** 、 **[進む]** 、および 最近 の各**ページ**を使用して履歴を移動できますが、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] によって提供される宣言型とプログラム用の両方のメカニズムを使用して、履歴内を移動することもできます。 これを行う理由の1つは、ページにカスタムナビゲーション Ui を提供することです。

@No__t-0 によって公開されているナビゲーションコマンドを使用して、の journal ナビゲーションサポートを宣言によって追加できます。 次の例は、`BrowseBack` ナビゲーションコマンドの使用方法を示しています。

[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml1)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml2)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml3)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML4](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml4)]

@No__t-0 クラスの次のいずれかのメンバーを使用して、プログラムを使用して履歴をナビゲートできます。

- <xref:System.Windows.Navigation.NavigationService.GoBack%2A>

- <xref:System.Windows.Navigation.NavigationService.GoForward%2A>

- <xref:System.Windows.Navigation.NavigationService.CanGoBack%2A>

- <xref:System.Windows.Navigation.NavigationService.CanGoForward%2A>

このトピックの「[ナビゲーション履歴によるコンテンツの状態の保持](#RetainingContentStateWithNavigationHistory)」で説明されているように、履歴はプログラムによって操作することもできます。

<a name="PageLifetime"></a>

### <a name="page-lifetime-and-the-journal"></a>ページの有効期間と履歴

グラフィックス、アニメーション、メディアなどのリッチコンテンツを含む複数のページを含む @no__t 0 を考えてみます。 このようなページのメモリ使用量は、特にビデオやオーディオ メディアが使用されている場合、非常に大きくなることがあります。 移動先のページを "記憶" している場合、このような [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] は、大量のメモリをすばやく消費する可能性があります。

このため、ジャーナルの既定の動作では、<xref:System.Windows.Controls.Page> オブジェクトへの参照ではなく、各履歴エントリに @no__t 0 のメタデータが格納されます。 履歴項目に移動すると、その @no__t 0 のメタデータを使用して、指定された <xref:System.Windows.Controls.Page> の新しいインスタンスが作成されます。 その結果、移動される各 @no__t 0 には、次の図に示す有効期間があります。

![ページの有効期間](./media/navigation-overview/navigated-page-lifetime.png "ページが移動されたときの有効期間を示します。")

既定のジャーナル動作を使用すると、メモリ使用量を節約できますが、ページごとのレンダリングのパフォーマンスが低下する可能性があります。@no__t 0 を再インスタンス化すると、特に大量のコンテンツがある場合は、時間がかかることがあります。 @No__t 0 のインスタンスをジャーナルに保持する必要がある場合は、2つの方法で作成できます。 まず、<xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> メソッドを呼び出すことによって、プログラムを使用して @no__t 0 のオブジェクトに移動できます。

次に、<xref:System.Windows.Controls.Page.KeepAlive%2A> プロパティを `true` (既定値は `false`) に設定することによって、ジャーナル内の <xref:System.Windows.Controls.Page> のインスタンスを @no__t 0 に保持するように指定できます。 次の例に示すように、マークアップで <xref:System.Windows.Controls.Page.KeepAlive%2A> を宣言によって設定できます。

[!code-xaml[NavigationOverviewSnippets#KeepAlivePageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/KeepAlivePage.xaml#keepalivepagexaml)]

保持されている @no__t 0 の有効期間は、それ以外の場合とはわずかに異なります。 保持されている @no__t 0 が初めて移動されると、@no__t のようにインスタンス化されます。 ただし、<xref:System.Windows.Controls.Page> のインスタンスはジャーナルに保持されるため、ジャーナルに残っている限り、再インスタンス化されることはありません。 その結果、<xref:System.Windows.Controls.Page> がナビゲートされるたびに呼び出される必要がある初期化ロジックが @no__t 0 にある場合は、それをコンストラクターから <xref:System.Windows.FrameworkElement.Loaded> イベントのハンドラーに移動する必要があります。 次の図に示すように、<xref:System.Windows.FrameworkElement.Loaded> と <xref:System.Windows.FrameworkElement.Unloaded> のイベントは、それぞれ <xref:System.Windows.Controls.Page> がナビゲートされるたびに発生します。

![読み込まれたイベントとアンロードされたイベントが]読み込まれたときに、(./media/navigation-overview/loaded-and-unloaded-events.png "ページの移動元とアンロード後のイベントが発生")したとき。

@No__t 0 が保持されていない場合は、次のいずれの操作も実行しないでください。

- ページへの参照、またはその一部への参照を格納する。

- ページによって実装されていないイベントのイベント ハンドラーを登録する。

これらのいずれかを実行すると、履歴から削除された後でも、@no__t 0 がメモリに保持されることを強制する参照が作成されます。

一般に、<xref:System.Windows.Controls.Page> を使用しないようにする場合は、既定の @no__t 0 の動作を使用することをお勧めします。 ただし、これには、次のセクションで説明されている状態も関係します。

<a name="RetainingContentStateWithNavigationHistory"></a>

### <a name="retaining-content-state-with-navigation-history"></a>ナビゲーション履歴によるコンテンツの状態の保持

@No__t 0 が維持されていない状態で、ユーザーからのデータを収集するコントロールがある場合、ユーザーが <xref:System.Windows.Controls.Page> との間で移動した場合、データはどうなりますか。 ユーザー エクスペリエンスの観点から見ると、ユーザーは以前に入力したデータが表示されることを期待します。 残念ながら、各ナビゲーションで <xref:System.Windows.Controls.Page> の新しいインスタンスが作成されるため、データを収集したコントロールは再インスタンス化され、データは失われます。

幸いにも、この履歴では、制御データを含む @no__t 0 のナビゲーション全体でデータを記憶することがサポートされています。 具体的には、各 <xref:System.Windows.Controls.Page> の履歴エントリは、関連付けられた <xref:System.Windows.Controls.Page> 状態の一時コンテナーとして機能します。 次の手順では、@no__t 0 に移動したときに、このサポートがどのように使用されるかを説明します。

1. 現在の <xref:System.Windows.Controls.Page> のエントリがジャーナルに追加されます。

2. @No__t-0 の状態は、そのページの履歴エントリと共に格納され、バックスタックに追加されます。

3. 新しい <xref:System.Windows.Controls.Page> に移動します。

@No__t のページに移動すると、ジャーナルを使用して、次の手順が実行されます。

1. @No__t-0 (バックスタックの一番上のジャーナルエントリ) がインスタンス化されます。

2. @No__t-0 は、<xref:System.Windows.Controls.Page> の履歴エントリと共に保存された状態で更新されます。

3. @No__t-0 はに戻ります。

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] @no__t で次のコントロールが使用されている場合に、このサポートを自動的に使用します。

- <xref:System.Windows.Controls.CheckBox>

- <xref:System.Windows.Controls.ComboBox>

- <xref:System.Windows.Controls.Expander>

- <xref:System.Windows.Controls.Frame>

- <xref:System.Windows.Controls.ListBox>

- <xref:System.Windows.Controls.ListBoxItem>

- <xref:System.Windows.Controls.MenuItem>

- <xref:System.Windows.Controls.ProgressBar>

- <xref:System.Windows.Controls.RadioButton>

- <xref:System.Windows.Controls.Slider>

- <xref:System.Windows.Controls.TabControl>

- <xref:System.Windows.Controls.TabItem>

- <xref:System.Windows.Controls.TextBox>

@No__t 0 がこれらのコントロールを使用している場合は、次の図に示すように、お気に入りの @no__t**色**によって示されているように、これらのコントロールに入力されたデータは @no__t 1 回のナビゲーションで記憶されます。

入力した状態データを![記憶するコントロールを含むページ](./media/navigation-overview/data-remembered-across-page-navigations.png "は、ページナビゲーション間で記憶されます。")

@No__t 0 が前のリストのコントロール以外のコントロールを持っている場合、または状態がカスタムオブジェクトに格納されている場合は、履歴が @no__t のナビゲーション全体で状態を記憶するようにコードを記述する必要があります。

@No__t 0 のナビゲーション全体で小さな状態を記憶する必要がある場合は、<xref:System.Windows.FrameworkPropertyMetadata.Journal%2A?displayProperty=nameWithType> メタデータフラグで構成されている依存関係プロパティ (@no__t を参照) を使用できます。

ナビゲーション間で @no__t 0 が記憶する必要のある状態が複数のデータで構成されている場合は、1つのクラスに状態をカプセル化して、<xref:System.Windows.Navigation.IProvideCustomContentState> インターフェイスを実装すると、コードの負担が少なくなることがあります。

1つの @no__t のさまざまな状態を移動する必要がある場合は、<xref:System.Windows.Controls.Page> から移動せずに、<xref:System.Windows.Navigation.IProvideCustomContentState> と @no__t を使用できます。

<a name="Cookies"></a>

### <a name="cookies"></a>クッキー

@No__t 0 のアプリケーションがデータを格納できるもう1つの方法は、<xref:System.Windows.Application.SetCookie%2A> および <xref:System.Windows.Application.GetCookie%2A> メソッドを使用して作成、更新、削除される cookie を使用することです。 @No__t-0 で作成できる cookie は、他の種類の Web アプリケーションが使用する cookie と同じです。cookie は、アプリケーションセッション中またはアプリケーションセッション間でクライアントコンピューター上のアプリケーションによって保存される任意のデータです。 クッキー データは、通常、次の形式の名前と値のペアです。

*Name* `=` *Value*

データが <xref:System.Windows.Application.SetCookie%2A> に、cookie を設定する必要がある場所の <xref:System.Uri> に渡されると、cookie はメモリ内に作成され、現在のアプリケーションセッションの間のみ使用できます。 この種類の cookie は、*セッション cookie*と呼ばれます。

複数のアプリケーション セッションにまたがってクッキーを格納するには、次の形式を使用して、有効期限をクッキーに追加する必要があります。

*NAME* `=` *VALUE* `; expires=DAY, DD-MMM-YYYY HH:MM:SS GMT`

有効期限が切れたクッキーは、cookie の有効期限が切れるまで、現在の Windows インストールのインターネット一時ファイルフォルダーに格納されます。 このような cookie は、アプリケーションセッション間で保持されるため、*永続的なクッキー*と呼ばれます。

セッションと永続的な cookie の両方を取得するには、<xref:System.Windows.Application.GetCookie%2A> メソッドを呼び出し、cookie が <xref:System.Windows.Application.SetCookie%2A> メソッドに設定されている場所の <xref:System.Uri> を渡します。

次に、@no__t 0 でクッキーがサポートされるいくつかの方法を示します。

- @no__t 0 のスタンドアロンアプリケーションと [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] では、cookie の作成と管理の両方を行うことができます。

- @No__t 0 によって作成された cookie には、ブラウザーからアクセスできます。

- 同じドメインの [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] は、クッキーを作成して共有できます。

- 同じドメインの @no__t 0 と HTML ページでは、cookie を作成して共有できます。

- Cookie がディスパッチされるのは、[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] および緩い [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ページが Web 要求を行うときです。

- IFRAME でホストされているトップレベルの [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] と @no__t は、どちらも cookie にアクセスできます。

- @No__t 0 での Cookie のサポートは、サポートされているすべてのブラウザーで同じです。

- Internet Explorer では、cookie に関連する P3P ポリシーは、特にファーストパーティおよびサードパーティの [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] に関して @no__t 0 によって受け入れられます。

<a name="Structured_Navigation"></a>

### <a name="structured-navigation"></a>構造化ナビゲーション

@No__t 0 から別のデータにデータを渡す必要がある場合は、<xref:System.Windows.Controls.Page> のパラメーターなしのコンストラクターに引数としてデータを渡すことができます。 この手法を使用する場合は、@no__t 0 のままにしておく必要があることに注意してください。それ以外の場合は、次に <xref:System.Windows.Controls.Page> に移動したときに、パラメーターなしのコンストラクターを使用して <xref:System.Windows.Controls.Page> を再インスタンス化 @no__t ます。

または、@no__t 0 に渡す必要があるデータで設定されたプロパティを実装できます。 ただし、<xref:System.Windows.Controls.Page> がデータを移動する <xref:System.Windows.Controls.Page> にデータを渡す必要がある場合は、注意が必要です。 問題は、ナビゲーションから移動した後に <xref:System.Windows.Controls.Page> が返されることを保証するメカニズムが、ナビゲーションでネイティブにサポートされていないことです。 基本的に、ナビゲーションは、"呼び出す/戻る" というセマンティクスをサポートしていません。 この問題を解決するために、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] には、予測可能で構造化された方法で <xref:System.Windows.Controls.Page> が返されることを保証するために使用できる @no__t 1 のクラスが用意されています。 詳細については、「[構造化ナビゲーションの概要](structured-navigation-overview.md)」を参照してください。

<a name="The_NavigationWindow_Class"></a>

## <a name="the-navigationwindow-class"></a>NavigationWindow クラス

ここまでで、ナビゲート可能なコンテンツを含むアプリケーションをビルドするために使用する可能性が最も高いナビゲーション サービスの全容を説明しました。 これらのサービスは [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] のコンテキストで説明されていましたが、[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] に限定されていません。 最新のオペレーティングシステムと Windows アプリケーションでは、最新のユーザーのブラウザーエクスペリエンスを利用して、ブラウザー形式のナビゲーションをスタンドアロンアプリケーションに組み込むことができます。 一般的な例は、次のとおりです。

- **単語の類義語辞典**:単語の選択項目を移動します。

- **エクスプローラー**:ファイルとフォルダーに移動します。

- **ウィザード**:複雑なタスクを複数のページに分割し、移動することができます。 例として、windows の機能の追加と削除を処理する Windows コンポーネントウィザードがあります。

スタンドアロンアプリケーションにブラウザースタイルのナビゲーションを組み込むには、<xref:System.Windows.Navigation.NavigationWindow> クラスを使用できます。 <xref:System.Windows.Navigation.NavigationWindow> は <xref:System.Windows.Window> から派生し、[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] が提供するナビゲーションの同じサポートで拡張します。 @No__t-0 は、スタンドアロンアプリケーションのメインウィンドウとして使用することも、ダイアログボックスなどのセカンダリウィンドウとして使用することもできます。

@No__t-1 (<xref:System.Windows.Window>、<xref:System.Windows.Controls.Page> など) の最上位レベルのクラスと同様に @no__t 0 を実装するには、マークアップと分離コードの組み合わせを使用します。 これを次の例に示します。

[!code-xaml[IntroToNavNavigationWindowSnippets#NavigationWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml#navigationwindowmarkup)]

[!code-csharp[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml.cs#navigationwindowcodebehind)]
[!code-vb[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/MainWindow.xaml.vb#navigationwindowcodebehind)]

このコードは、<xref:System.Windows.Navigation.NavigationWindow> を開いたときに <xref:System.Windows.Controls.Page> (ホームページ) に自動的に移動する @no__t 0 を作成します。 @No__t-0 がメインアプリケーションウィンドウである場合は、`StartupUri` 属性を使用して起動できます。 これを次のマークアップに示します。

[!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchNavWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/App.xaml#applaunchnavwindow)]

次の図は、スタンドアロンアプリケーションのメインウィンドウとして @no__t 0 を示しています。

メイン(./media/navigation-overview/navigation-window-as-main-window.png "ウィンドウとして")の![メインウィンドウ]のナビゲーションウィンドウ

この図からは、前の例の <xref:System.Windows.Navigation.NavigationWindow> 実装コードで設定されていない場合でも、<xref:System.Windows.Navigation.NavigationWindow> にタイトルがあることがわかります。 代わりに、次のコードに示すように、<xref:System.Windows.Controls.Page.WindowTitle%2A> プロパティを使用してタイトルを設定します。

[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup1)]
[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup2)]

@No__t-0 および <xref:System.Windows.Controls.Page.WindowHeight%2A> プロパティを設定すると、<xref:System.Windows.Navigation.NavigationWindow> にも影響します。

通常、動作または外観をカスタマイズする必要がある場合は、独自の @no__t 0 を実装します。 どちらも行わない場合は、ショートカットを使用できます。 スタンドアロンアプリケーションで <xref:System.Windows.Application.StartupUri%2A> として <xref:System.Windows.Controls.Page> のパックを @no__t 0 に指定すると @no__t、<xref:System.Windows.Controls.Page> をホストするための @no__t が自動的に作成されます。 次のマークアップは、この方法を示しています。

[!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchPage](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/AnotherApp.xaml#applaunchpage)]

ダイアログボックスなどのセカンダリアプリケーションウィンドウを @no__t 0 にする必要がある場合は、次の例のコードを使用してそれを開くことができます。

[!code-csharp[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/DialogOwnerWindow.xaml.cs#createnwdialogbox)]
[!code-vb[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/DialogOwnerWindow.xaml.vb#createnwdialogbox)]

次の図に、結果を示します。

![]ダイアログボックスのダイアログボックスの(./media/navigation-overview/navigation-window-as-dialog-box.png "ナビゲーションウィンドウ")

ご覧のように、<xref:System.Windows.Navigation.NavigationWindow> は、ユーザーが journal を操作できるようにする Internet Explorer スタイルの **[戻る]** ボタンと **[進む]** ボタンを表示します。 これらのボタンは、次の図に示されているように、同じユーザー エクスペリエンスを提供します。

![](./media/navigation-overview/back-and-forward-buttons-in-navigation-window.png "ナビゲーションウィンドウの NavigationWindow back および forward ボタン")の [戻る] ボタンと [進む] ボタン

ページに独自のジャーナルナビゲーションサポートと UI が用意されている場合は、@no__t 3 プロパティの値を `false` に設定することによって、@no__t 2 によって表示される **[戻る]** ボタンと **[進む]** ボタンを非表示にすることができます。

または、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] のカスタマイズサポートを使用して、<xref:System.Windows.Navigation.NavigationWindow> の @no__t を置き換えることもできます。

<a name="Frame_in_Standalone_Applications"></a>

## <a name="the-frame-class"></a>Frame クラス

ブラウザーと @no__t 0 は、ナビゲーション可能なコンテンツをホストする windows です。 場合によっては、アプリケーションには、ウィンドウ全体でホストする必要のないコンテンツがあることもあります。 このようなコンテンツは、代わりに、他のコンテンツ内でホストされます。 @No__t-0 クラスを使用して、他のコンテンツに誘導可能なコンテンツを挿入できます。 <xref:System.Windows.Controls.Frame> は、<xref:System.Windows.Navigation.NavigationWindow> と [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] と同じサポートを提供します。

次の例では、`Frame` 要素を使用して、宣言によって <xref:System.Windows.Controls.Page> に @no__t 0 を追加する方法を示します。

[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml3)]

このマークアップは、`Frame` 要素の `Source` 属性に、@no__t の最初の移動先の @no__t 3 のパック @no__t を設定します。 次の図は、複数のページ間を移動する @no__t 2 を持つ <xref:System.Windows.Controls.Page> を持つ @no__t 0 を示しています。

![複数のページ間を移動するフレーム](./media/navigation-overview/frame-navigation-between-multiple-pages.png "。これは、複数のページ間のフレームナビゲーションを示します。")

@No__t-1 のコンテンツ内で <xref:System.Windows.Controls.Frame> を使用するだけではありません。 また、<xref:System.Windows.Window> のコンテンツ内で @no__t 0 をホストすることもよくあります。

既定では、<xref:System.Windows.Controls.Frame> は、別の履歴が存在しない場合にのみ独自の履歴を使用します。 @No__t 0 が <xref:System.Windows.Navigation.NavigationWindow> または [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] のいずれかの内部でホストされているコンテンツの一部である場合、<xref:System.Windows.Controls.Frame> は @no__t 4 または [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] に属するジャーナルを使用します。 ただし、場合によっては、@no__t 0 が独自のジャーナルを担当する必要があります。 その理由の1つは、<xref:System.Windows.Controls.Frame> によってホストされるページ内での journal ナビゲーションを許可することです。 これを次の図に示します。

![フレームとページダイアグラム](./media/navigation-overview/journal-navigation-within-pages-hosted-by-a-frame.png "これは、フレームによってホストされるページ内の journal ナビゲーションを示します。")

この場合は、<xref:System.Windows.Controls.Frame> の <xref:System.Windows.Controls.Frame.JournalOwnership%2A> プロパティを <xref:System.Windows.Navigation.JournalOwnership.OwnsJournal> に設定することによって、独自のジャーナルを使用するように <xref:System.Windows.Controls.Frame> を構成できます。 これを次のマークアップに示します。

[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml3)]

次の図は、独自の履歴を使用する @no__t 0 内で移動した場合の影響を示しています。

![独自の履歴を使用するフレームは]、(./media/navigation-overview/frame-uses-its-own-journal.png "独自の履歴を使用するフレーム内での移動の効果を示します。")

履歴エントリは、Internet Explorer ではなく <xref:System.Windows.Controls.Frame> のナビゲーション [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] に表示されることに注意してください。

> [!NOTE]
> @No__t 0 が <xref:System.Windows.Window> でホストされているコンテンツの一部である場合、@no__t 2 は独自のジャーナルを使用し、その結果、独自のナビゲーション [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] が表示されます。

ユーザーエクスペリエンスで、ナビゲーション [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を表示せずに独自の履歴を提供するために @no__t 0 が必要な場合は、<xref:System.Windows.Controls.Frame.NavigationUIVisibility%2A> を <xref:System.Windows.Visibility.Hidden> に設定することによって、ナビゲーション @no__t を非表示にすることができます。 これを次のマークアップに示します。

[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml3)]

<a name="Navigation_Hosts"></a>

## <a name="navigation-hosts"></a>ナビゲーション ホスト

<xref:System.Windows.Controls.Frame> および <xref:System.Windows.Navigation.NavigationWindow> は、ナビゲーションホストと呼ばれるクラスです。 *ナビゲーションホスト*は、コンテンツに移動して表示できるクラスです。 これを実現するために、各ナビゲーションホストは独自の @no__t 0 およびジャーナルを使用します。 ナビゲーション ホストの基本的な構造を次の図に示します。

![ナビゲーター図](./media/navigation-overview/navigation-host-construction.png "ナビゲーションホストの基本的な構築")

基本的に、これにより、<xref:System.Windows.Navigation.NavigationWindow> と <xref:System.Windows.Controls.Frame> は、ブラウザーでホストされるときに @no__t 2 が提供するのと同じナビゲーションサポートを提供できます。

@No__t-0 およびジャーナルを使用するだけでなく、ナビゲーションホストは、<xref:System.Windows.Navigation.NavigationService> が実装するのと同じメンバーを実装します。 これを次の図に示します。

![フレーム内および NavigationWindow](./media/navigation-overview/navigation-window-and-frame.png "ナビゲーションウィンドウおよびフレーム")内の履歴

これにより、これらのメンバーに対して直接、ナビゲーション サポートをプログラミングできます。 @No__t-2 でホストされている <xref:System.Windows.Controls.Frame> に対して、カスタムナビゲーション @no__t を指定する必要がある場合は、この点を考慮してください。 さらに、どちらの種類も、`BackStack` (<xref:System.Windows.Navigation.NavigationWindow.BackStack%2A?displayProperty=nameWithType>、<xref:System.Windows.Controls.Frame.BackStack%2A?displayProperty=nameWithType>) と `ForwardStack` (<xref:System.Windows.Navigation.NavigationWindow.ForwardStack%2A?displayProperty=nameWithType>、<xref:System.Windows.Controls.Frame.ForwardStack%2A?displayProperty=nameWithType>) を含む追加のナビゲーション関連メンバーを実装しています。これにより、バックスタックと転送スタックの履歴エントリをそれぞれ列挙できます。

前に述べたように、アプリケーション内に複数の履歴が存在することがあります。 次の図は、この例を示しています。

![1 つのアプリケーション内の複数](./media/navigation-overview/multiple-journals-in-one-application.png "のジャーナルこれは、アプリケーション内の複数のジャーナルの一例です。")

<a name="Navigating_to_Content_Other_than_Pages"></a>

## <a name="navigating-to-content-other-than-xaml-pages"></a>XAML ページ以外のコンテンツへのナビゲート

このトピックでは、<xref:System.Windows.Controls.Page> と pack [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] を使用して、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] のさまざまなナビゲーション機能を示します。 ただし、アプリケーションにコンパイルされた @no__t 0 は、移動できる唯一の種類のコンテンツではなく、パック [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] がコンテンツを識別する唯一の方法ではありません。

このセクションで示すように、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] のファイル、HTML ファイル、およびオブジェクトに移動することもできます。

<a name="Navigating_to_Loose_XAML_Files"></a>

### <a name="navigating-to-loose-xaml-files"></a>Loose XAML ファイルへのナビゲート

@No__t 0 ではないファイルは、次の特性を持つファイルです。

- @No__t-0 (つまり、コードなし) のみを含みます。

- 適切な名前空間宣言がある。

- .xaml ファイル名拡張子を持つ。

たとえば、@no__t 0 のファイル (Person) として保存されている次のコンテンツを考えてみます。

[!code-xaml[NavigationOverviewSnippets#LooseXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Person.xaml#loosexaml)]

ファイルをダブルクリックすると、ブラウザーが開き、コンテンツにナビゲートして、コンテンツを表示します。 これを次の図に示します。

![ユーザー .xaml ファイル]の内容を表示すると、(./media/navigation-overview/contents-of-person-xaml-file.png "ユーザーの .xaml ファイルの内容が")表示されます。

次のように、疎 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイルを表示できます。

- ローカル コンピューター、イントラネット、またはインターネット上の Web サイト。

- UNC (汎用名前付け規則) ファイル共有。

- ローカル ディスク。

ブラウザーのお気に入りには、@no__t 0 以上のファイルを追加できます。また、ブラウザーのホームページに追加することもできます。

> [!NOTE]
> 疎 @no__t ページのパブリッシュと起動の詳細については、「 [WPF アプリケーションの配置](deploying-a-wpf-application-wpf.md)」を参照してください。

厳密でない @no__t 0 に対する制限事項の1つは、部分信頼で実行しても安全なコンテンツのみをホストできることです。 たとえば、`Window` は、ルース [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイルのルート要素にすることはできません。 詳細については、「 [WPF 部分信頼セキュリティ](../wpf-partial-trust-security.md)」を参照してください。

<a name="Navigating_to_HTML_Files_Using_Frame"></a>

### <a name="navigating-to-html-files-by-using-frame"></a>フレームを使用した HTML ファイルへのナビゲート

ご想像のとおり、HTML に移動することもできます。 単に、http スキームを使用する @no__t 0 を指定する必要があります。 たとえば、次の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] は、HTML ページに移動する <xref:System.Windows.Controls.Frame> を示しています。

[!code-xaml[NavigationOverviewSnippets#FrameHtmlNavMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHTMLNavPage.xaml#framehtmlnavmarkup)]

HTML に移動するには、特殊なアクセス許可が必要です。 たとえば、インターネットゾーン部分信頼セキュリティサンドボックスで実行されている @no__t 0 から移動することはできません。 詳細については、「 [WPF 部分信頼セキュリティ](../wpf-partial-trust-security.md)」を参照してください。

<a name="Navigating_to_HTML_Files_Using_WebBrowser"></a>

### <a name="navigating-to-html-files-by-using-the-webbrowser-control"></a>WebBrowser コントロールを使用した HTML ファイルへのナビゲート

@No__t 0 コントロールは、HTML ドキュメントのホスト、ナビゲーション、スクリプト/マネージコードの相互運用性をサポートします。 @No__t 0 コントロールの詳細については、「<xref:System.Windows.Controls.WebBrowser>」を参照してください。

@No__t-0 のように、<xref:System.Windows.Controls.WebBrowser> を使用して HTML に移動するには、特別なアクセス許可が必要です。 たとえば、部分信頼アプリケーションでは、元のサイトにある HTML にのみ移動できます。 詳細については、「 [WPF 部分信頼セキュリティ](../wpf-partial-trust-security.md)」を参照してください。

<a name="Navigating_to_Objects"></a>

### <a name="navigating-to-custom-objects"></a>カスタム オブジェクトへのナビゲート

カスタムオブジェクトとして格納されているデータがある場合、そのデータを表示する方法の1つとして、それらのオブジェクトにバインドされたコンテンツを含む @no__t 0 を作成します (「[データバインディングの概要](../data/data-binding-overview.md)」を参照してください)。 オブジェクトを表示するためだけにページ全体を作成するオーバーヘッドが必要ない場合には、代わりに、オブジェクトに直接ナビゲートすることもできます。

次のコードに実装されている @no__t 0 クラスを考えてみます。

[!code-csharp[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/Person.cs#personclasscode)]
[!code-vb[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/Person.vb#personclasscode)]

このファイルに移動するには、次のコードに示すように、<xref:System.Windows.Navigation.NavigationWindow.Navigate%2A?displayProperty=nameWithType> メソッドを呼び出します。

[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject1)]
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject2)]
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject3)]

[!code-csharp[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml.cs#pagethatnavstoobjectcodebehind)]
[!code-vb[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/HomePage.xaml.vb#pagethatnavstoobjectcodebehind)]

次の図に、結果を示します。

![クラスに移動するページ]は、(./media/navigation-overview/page-navigates-to-an-object.png "オブジェクトに移動するページの例です。")

この図には、役立つものが何も表示されていません。 実際、表示される値は、 **Person**オブジェクトの `ToString` メソッドの戻り値です。既定では、これは [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] がオブジェクトを表すために使用できる唯一の値です。 @No__t-0 メソッドをオーバーライドして、より意味のある情報を返すこともできますが、それでも文字列値になります。 @No__t のプレゼンテーション機能を利用する1つの手法は、データテンプレートを使用することです。 @No__t-0 が特定の種類のオブジェクトに関連付けることができるデータテンプレートを実装できます。 次のコードは、`Person` オブジェクトのデータテンプレートを示しています。

[!code-xaml[NavigateToObjectSnippets#DataTemplateMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/App.xaml#datatemplatemarkup)]

ここでは、データテンプレートは、`DataType` 属性の `x:Type` マークアップ拡張機能を使用して @no__t 0 型に関連付けられています。 次に、データテンプレートは @no__t 0 の要素 (@no__t を参照) を `Person` クラスのプロパティにバインドします。 次の図は、`Person` オブジェクトの更新された外観を示しています。

データテンプレートを![持つクラスへの移動](./media/navigation-overview/navigating-to-a-class.png "。データテンプレートを持つクラスに移動します。")

この方法の利点は、データ テンプレートを再利用して、アプリケーションの任意の場所で オブジェクトを一貫して表示できることによって得られる一貫性です。

データテンプレートの詳細については、「データテンプレートの[概要](../data/data-templating-overview.md)」を参照してください。

<a name="Security"></a>

## <a name="security"></a>セキュリティ

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ナビゲーションサポートを使用すると、インターネット経由で [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] を移動でき、アプリケーションでサードパーティのコンテンツをホストできるようになります。 アプリケーションとユーザーの両方を有害な動作から保護するために、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] には、[セキュリティ](../security-wpf.md)と[WPF 部分信頼セキュリティ](../wpf-partial-trust-security.md)について説明されているさまざまなセキュリティ機能が用意されています。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Application.SetCookie%2A>
- <xref:System.Windows.Application.GetCookie%2A>
- [アプリケーション管理の概要](application-management-overview.md)
- [WPF におけるパッケージの URI](pack-uris-in-wpf.md)
- [構造化ナビゲーションの概要](structured-navigation-overview.md)
- [ナビゲーション トポロジの概要](navigation-topologies-overview.md)
- [方法トピック](navigation-how-to-topics.md)
- [WPF アプリケーションの配置](deploying-a-wpf-application-wpf.md)
