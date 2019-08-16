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
ms.openlocfilehash: 145c4e33bd601fa61750df56b949bda5d43cc372
ms.sourcegitcommit: 10736f243dd2296212e677e207102c463e5f143e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2019
ms.locfileid: "68818000"
---
# <a name="navigation-overview"></a>ナビゲーションの概要

Windows Presentation Foundation (WPF) では、スタンドアロンアプリケーションと[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]の2種類のアプリケーションで使用できるブラウザースタイルのナビゲーションがサポートされています。 コンテンツをナビゲーション用にパッケージ[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]化する<xref:System.Windows.Controls.Page>ために、はクラスを提供します。 を使用するか、 <xref:System.Windows.Controls.Page>またはを使用して<xref:System.Windows.Navigation.NavigationService>プログラム<xref:System.Windows.Documents.Hyperlink>によって、相互に相互に移動できます。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は、ナビゲート元のページを記憶し、それらのページに戻るために、履歴を使用します。

<xref:System.Windows.Controls.Page>、 <xref:System.Windows.Documents.Hyperlink>、 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]、およびジャーナルは、によって提供されるナビゲーションサポートの中核となります。 <xref:System.Windows.Navigation.NavigationService> この概要では、圧縮[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]されていないファイル、HTML ファイル、およびオブジェクトへの移動を含む高度なナビゲーションサポートについて説明する前に、これらの機能について詳しく説明します。

> [!NOTE]
> このトピックでは、"browser" という用語は、現在 Microsoft Internet [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Explorer と Firefox を含むアプリケーションをホストできるブラウザーのみを指します。 特定の[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]機能が特定のブラウザーでのみサポートされている場合は、ブラウザーのバージョンが参照されます。

## <a name="navigation-in-wpf-applications"></a>WPF アプリケーションでのナビゲーション

このトピックでは、の[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]主要なナビゲーション機能の概要について説明します。 これらの機能は、スタンドアロンアプリケーションと[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]の両方で使用できます。ただし、このトピック[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]では、のコンテキスト内でこれらの機能を示しています。

> [!NOTE]
> このトピックでは、のビルドと配置[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]の方法については説明しません。 の[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]詳細については、「 [WPF XAML ブラウザーアプリケーションの概要](wpf-xaml-browser-applications-overview.md)」を参照してください。

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

で[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]は、.NET Framework オブジェクト、カスタムオブジェクト、列挙値、ユーザーコントロール、 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイル、HTML ファイルなど、いくつかのコンテンツの種類に移動できます。 ただし、を使用<xref:System.Windows.Controls.Page>すると、コンテンツをパッケージ化するための最も一般的で便利な方法を見つけることができます。 さらに<xref:System.Windows.Controls.Page> 、はナビゲーション固有の機能を実装して、外観を強化し、開発を簡略化します。

を<xref:System.Windows.Controls.Page>使用すると、次のようなマーク[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]アップを使用して、コンテンツのナビゲート可能なページを宣言によって実装できます。

[!code-xaml[NavigationOverviewSnippets#Page1XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page1.xaml#page1xaml)]

マーク<xref:System.Windows.Controls.Page> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]アップ[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] で実装[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]されるは、ルート要素として、名前空間の宣言を必要とします。`Page` `Page`要素には、移動して表示するコンテンツが含まれています。 コンテンツを追加するには`Page.Content` 、次のマークアップに示すように、property 要素を設定します。

[!code-xaml[NavigationOverviewSnippets#Page2XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page2.xaml#page2xaml)]

`Page.Content` には、1 つの子要素のみを含めることができます。前の例では、コンテンツは単一の文字列「Hello, Page!」です。 実際には、通常はレイアウトコントロールを子要素として使用し (「[レイアウト](../advanced/layout.md)」を参照)、コンテンツを格納して構成します。

`Page`要素の子要素は、 <xref:System.Windows.Controls.Page>のコンテンツと見なされます。したがって、明示的`Page.Content`な宣言を使用する必要はありません。 次のマークアップは、前のサンプルの宣言と同等です。

[!code-xaml[NavigationOverviewSnippets#Page3XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Page3.xaml#page3xaml)]

この場合、は`Page.Content` 、 `Page`要素の子要素を使用して自動的に設定されます。 詳細については、「[WPF のコンテンツ モデル](../controls/wpf-content-model.md)」を参照してください。

マークアップのみ<xref:System.Windows.Controls.Page>が、コンテンツを表示する場合に便利です。 ただし、は<xref:System.Windows.Controls.Page> 、ユーザーがページと対話できるようにするコントロールを表示することもできます。また、イベントを処理し、アプリケーションロジックを呼び出すことによって、ユーザーの操作に応答できます。 対話型<xref:System.Windows.Controls.Page>は、次の例に示すように、マークアップと分離コードの組み合わせを使用して実装されます。

[!code-xaml[XBAPAppDefSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml#homepagemarkup)]

[!code-csharp[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/HomePage.xaml.cs#homepagecodebehind)]
[!code-vb[XBAPAppDefSnippets#HomePageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/HomePage.xaml.vb#homepagecodebehind)]

マークアップ ファイルと分離コード ファイルを連携させるには、次の構成が必要です。

- マークアップでは`Page` 、要素に属性`x:Class`を含める必要があります。 アプリケーションがビルドされると、マークアップ`x:Class`ファイルにが存在する[!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)]ことにより`partial` 、は、から<xref:System.Windows.Controls.Page>派生したクラスを作成し、 `x:Class`属性で指定された名前を持ちます。 その[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] ためには、`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`スキーマ( ) の名前空間宣言を追加する必要があります。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 生成さ`partial`れた`InitializeComponent`クラスはを実装します。これは、イベントを登録し、マークアップで実装されるプロパティを設定するために呼び出されます。

- 分離コードでは、クラスは、マークアップ`partial`で`x:Class`属性によって指定された名前と同じ名前を持つクラスである必要<xref:System.Windows.Controls.Page>があり、から派生する必要があります。 これにより、分離コードファイルは、アプリケーションのビルド`partial`時にマークアップファイル用に生成されたクラスに関連付けることができます (「 [WPF アプリケーションのビルド](building-a-wpf-application-wpf.md)」を参照してください)。

- 分離コードでは、クラス<xref:System.Windows.Controls.Page>は、 `InitializeComponent`メソッドを呼び出すコンストラクターを実装する必要があります。 `InitializeComponent`マークアップファイルの生成さ`partial`れたクラスによって実装され、イベントを登録し、マークアップで定義されているプロパティを設定します。

> [!NOTE]
> を使用<xref:System.Windows.Controls.Page> [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]してプロジェクトに新しいを追加すると<xref:System.Windows.Controls.Page> 、はマークアップと分離コードの両方を使用して実装されます。これには、マークアップファイルと分離コードファイルの関連付けを作成するために必要な構成が含まれます。ここで説明します。

を作成<xref:System.Windows.Controls.Page>したら、それに移動できます。 アプリケーションが移動する<xref:System.Windows.Controls.Page>最初のを指定するには、開始<xref:System.Windows.Controls.Page>を構成する必要があります。

<a name="Configuring_a_Start_Page"></a>

### <a name="configuring-a-start-page"></a>スタート ページの構成

[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] では、一定の量のアプリケーション インフラストラクチャをブラウザーでホストする必要があります。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] では、<xref:System.Windows.Application> クラスは、必要なアプリケーションインフラストラクチャを確立するアプリケーション定義の一部です (「[アプリケーション管理の概要](application-management-overview.md)」を参照してください)。

通常、アプリケーション定義はマークアップと分離コードの両方を使用して実装され、マーク[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]アップファイルは`ApplicationDefinition`項目として構成されます。 のアプリケーション定義を次に示し[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]ます。

[!code-xaml[XBAPAppDefSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]

[!code-csharp[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/XBAPAppDefSnippets/CSharp/App.xaml.cs#xbapapplicationdefinitioncodebehind)]
[!code-vb[XBAPAppDefSnippets#XBAPApplicationDefinitionCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XBAPAppDefSnippets/VisualBasic/Application.xaml.vb#xbapapplicationdefinitioncodebehind)]

は、アプリケーション定義を使用して開始<xref:System.Windows.Controls.Page>を指定<xref:System.Windows.Controls.Page> [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] できます。これは、の起動時に自動的に[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]読み込まれるです。 これを行うには、 <xref:System.Windows.Application.StartupUri%2A>必要[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] <xref:System.Windows.Controls.Page>なのを使用してプロパティを設定します。

> [!NOTE]
> ほとんどの場合<xref:System.Windows.Controls.Page> 、は、アプリケーションにコンパイルされるか、アプリケーションと共に配置されます。 このような場合、 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]を<xref:System.Windows.Controls.Page>識別するは[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]です。これは、*パック*スキームに準拠しているです。 パック[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]については、「 [WPF のパック uri](pack-uris-in-wpf.md)」で詳しく説明します。 以下で説明する http スキームを使用してコンテンツにナビゲートすることもできます。

次の例<xref:System.Windows.Application.StartupUri%2A>に示すように、マークアップで宣言によって設定できます。

[!code-xaml[NavigationOverviewSnippets#XBAPApplicationDefinitionMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/App.xaml#xbapapplicationdefinitionmarkup)]

この例では、 `StartupUri`属性は、ホームページを識別[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]する相対パックで設定されています。 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]が起動されると、ホームページが自動的に移動されて表示されます。 これは、次の図に示す[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]ように、Web サーバーから起動されたを示しています。

![XBAP ページ](./media/navigation-overview/xbap-launched-from-a-web-server.png "これは、Web サーバーから起動された XBAP を示しています。")

> [!NOTE]
> の[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]開発と配置の詳細については、「 [wpf XAML ブラウザーアプリケーションの概要](wpf-xaml-browser-applications-overview.md)」および「 [wpf アプリケーションの配置](deploying-a-wpf-application-wpf.md)」を参照してください。

<a name="ConfiguringAXAMLPage"></a>

### <a name="configuring-the-host-windows-title-width-and-height"></a>ホスト ウィンドウのタイトル、幅、および高さの構成

前の図では、ブラウザーとタブパネルの両方のタイトルが[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]用になっていることがわかります。 このタイトルは、長いだけでなく、見た目が良いわけでも、有益な情報になっているわけでもありません。 このため、に<xref:System.Windows.Controls.Page>は、 <xref:System.Windows.Controls.Page.WindowTitle%2A>プロパティを設定してタイトルを変更する方法が用意されています。 さらに、ブラウザーウィンドウの幅と高さは、それぞれと<xref:System.Windows.Controls.Page.WindowWidth%2A> <xref:System.Windows.Controls.Page.WindowHeight%2A>を設定することによって構成できます。

<xref:System.Windows.Controls.Page.WindowTitle%2A>、 <xref:System.Windows.Controls.Page.WindowWidth%2A>、および<xref:System.Windows.Controls.Page.WindowHeight%2A>は、次の例に示すように、マークアップで宣言によって設定できます。

[!code-xaml[NavigationOverviewSnippets#HomePageMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/HomePage.xaml#homepagemarkup)]

結果を次の例に示します。

![ウィンドウのタイトル、高さ、幅](./media/navigation-overview/window-title-width-height.png "これにより、構成できるウィンドウのタイトル、高さ、および幅が表示されます。")

<a name="NavigatingBetweenXAMLPages"></a>

### <a name="hyperlink-navigation"></a>ハイパーリンクのナビゲーション

一般的[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]なは複数のページで構成します。 あるページから別のページに移動する最も簡単な方法は<xref:System.Windows.Documents.Hyperlink>、を使用することです。 次のマークアップに<xref:System.Windows.Documents.Hyperlink>示すよう<xref:System.Windows.Controls.Page>に、 `Hyperlink`要素を使用してを宣言によってに追加することができます。

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

要素`Hyperlink`には、次のものが必要です。

- 属性で<xref:System.Windows.Controls.Page> [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 指定された移動先ののパック`NavigateUri` 。

- ユーザーがクリックしてナビゲーションを開始できるコンテンツ ( `Hyperlink`要素に含めることができるコンテンツについては、「」を参照してください<xref:System.Windows.Documents.Hyperlink>)。

次の図は、 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]を持つ<xref:System.Windows.Controls.Page>を持つ<xref:System.Windows.Documents.Hyperlink>を示しています。

![ハイパーリンクがあるページ](./media/navigation-overview/xbap-with-a-page-with-a-hyperlink.png "これは、ページとハイパーリンクを持つ XBAP を示しています。")

ご想像のとおり、をクリック<xref:System.Windows.Documents.Hyperlink>すると[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] 、は`NavigateUri`属性で<xref:System.Windows.Controls.Page>識別されるに移動します。 さらに、 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]は、Internet Explorer の [ <xref:System.Windows.Controls.Page>最近使ったページ] の一覧に前のエントリを追加します。 これを次の図に示します。

![[戻る] ボタンと [進む] ボタン](./media/navigation-overview/back-and-forward-navigation.png "[戻る] ボタンと [進む] ボタンを使用して移動します。")

また、間のナビゲーション<xref:System.Windows.Controls.Page>をサポートすると、 <xref:System.Windows.Documents.Hyperlink>フラグメントナビゲーションもサポートされます。

<a name="FragmentNavigation"></a>

### <a name="fragment-navigation"></a>フラグメント ナビゲーション

*フラグメントナビゲーション*は、現在<xref:System.Windows.Controls.Page>のまたは別<xref:System.Windows.Controls.Page>のコンテンツフラグメントへのナビゲーションです。 で[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]は、コンテンツフラグメントは名前付き要素に含まれるコンテンツです。 名前付き要素は、 `Name`属性が設定されている要素です。 次のマークアップは、 `TextBlock`コンテンツフラグメントを含む名前付き要素を示しています。

[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup1)]
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup2)]
[!code-xaml[NavigationOverviewSnippets#PageWithContentFragmentsMARKUP3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithFragments.xaml#pagewithcontentfragmentsmarkup3)]

がコンテンツフラグメントに移動`NavigateUri` するには、属性に次のものが含まれている必要があります。<xref:System.Windows.Documents.Hyperlink>

- 移動先のコンテンツフラグメントを持つの。<xref:System.Windows.Controls.Page> [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]

- 「#」文字。

- コンテンツフラグメントを格納して<xref:System.Windows.Controls.Page>いる上の要素の名前。

フラグメント[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]の形式は次のとおりです。

*PageURI* `#` *ElementName*

コンテンツフラグメントに移動するように`Hyperlink`構成されているの例を次に示します。

[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml1)]
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml2)]
[!code-xaml[NavigationOverviewSnippets#PageThatNavigatesXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageThatNavigatesToFragment.xaml#pagethatnavigatesxaml3)]

> [!NOTE]
> ここでは、での[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]既定のフラグメントナビゲーション実装について説明します。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]では、イベントの<xref:System.Windows.Navigation.NavigationService.FragmentNavigation?displayProperty=nameWithType>処理を必要とする独自のフラグメントナビゲーションスキームを実装することもできます。

> [!IMPORTANT]
> ページを HTTP で参照できる場合[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]に限り、ルースページ[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] (ルート`Page`要素としてを持つマークアップのみのファイル) のフラグメントに移動できます。
>
> ただし、ルース[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ページは独自のフラグメントに移動できます。

<a name="NavigationService"></a>

### <a name="navigation-service"></a>ナビゲーション サービス

では、ユーザーは特定<xref:System.Windows.Controls.Page>のへのナビゲーションを開始<xref:System.Windows.Navigation.NavigationService> できますが、ページを検索してダウンロードする作業はクラスによって実行されます。<xref:System.Windows.Documents.Hyperlink> 基本的に<xref:System.Windows.Navigation.NavigationService> 、は、などのクライアントコード<xref:System.Windows.Documents.Hyperlink>に代わってナビゲーション要求を処理する機能を提供します。 また、 <xref:System.Windows.Navigation.NavigationService>は、ナビゲーション要求を追跡し、それに影響を与える上位レベルのサポートを実装します。

<xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType> <xref:System.Windows.Controls.Page> [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]がクリックされると[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 、はを呼び出して、指定されたパックでを検索してダウンロードします。 <xref:System.Windows.Documents.Hyperlink> ダウンロード<xref:System.Windows.Controls.Page>したは、ルートオブジェクトがダウンロード<xref:System.Windows.Controls.Page>されたのインスタンスであるオブジェクトのツリーに変換されます。 ルート<xref:System.Windows.Controls.Page>オブジェクトへの参照は、 <xref:System.Windows.Navigation.NavigationService.Content%2A?displayProperty=nameWithType>プロパティに格納されます。 移動先[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]のコンテンツのパックは<xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType>プロパティに格納され、は<xref:System.Windows.Navigation.NavigationService.CurrentSource%2A?displayProperty=nameWithType>移動先の最後のページ[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]のパックを格納します。

> [!NOTE]
> [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]アプリケーションに現在アクティブな<xref:System.Windows.Navigation.NavigationService>アプリケーションが複数存在する可能性があります。 詳細については、このトピックで後述する「[ナビゲーションホスト](#Navigation_Hosts)」を参照してください。

<a name="Programmatic_Navigation_with_the_Navigation_Service"></a>

### <a name="programmatic-navigation-with-the-navigation-service"></a>ナビゲーション サービスによるプログラム ナビゲーション

では、を使用し<xref:System.Windows.Navigation.NavigationService>て<xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.Documents.Hyperlink>マークアップで、ナビゲーションが宣言によって実装<xref:System.Windows.Navigation.NavigationService>されているかどうかを知る必要はありません。はを使用してを使用します。 つまり、の直接または間接の<xref:System.Windows.Documents.Hyperlink>親がナビゲーションホスト (「[ナビゲーション](#Navigation_Hosts)ホスト」を参照) である限り、 <xref:System.Windows.Documents.Hyperlink>はナビゲーションホストのナビゲーションサービスを検索して使用し、ナビゲーション要求を処理することができます。

ただし、次のようにを直接使用<xref:System.Windows.Navigation.NavigationService>する必要がある場合もあります。

- パラメーター化されてい<xref:System.Windows.Controls.Page>ないコンストラクターを使用してをインスタンス化する必要がある場合。

- に移動する前に、の<xref:System.Windows.Controls.Page>プロパティを設定する必要がある場合。

- <xref:System.Windows.Controls.Page>移動する必要があるが実行時にのみ決定される場合。

このような状況では、 <xref:System.Windows.Navigation.NavigationService.Navigate%2A> <xref:System.Windows.Navigation.NavigationService>オブジェクトのメソッドを呼び出すことによって、プログラムによってナビゲーションを開始するコードを記述する必要があります。 これにはへの<xref:System.Windows.Navigation.NavigationService>参照を取得する必要があります。

#### <a name="getting-a-reference-to-the-navigationservice"></a>NavigationService への参照の取得

[[ナビゲーションホスト](#Navigation_Hosts)] セクションで説明されている理由[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]から、アプリケーションには複数<xref:System.Windows.Navigation.NavigationService>のを含めることができます。 つまり、コードでを検索<xref:System.Windows.Navigation.NavigationService>する方法が必要になります。これは<xref:System.Windows.Navigation.NavigationService>通常、現在<xref:System.Windows.Controls.Page>のに移動するです。 メソッドを<xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A?displayProperty=nameWithType> 呼び出す<xref:System.Windows.Navigation.NavigationService>ことにより、への参照を取得できます。 `static` 特定<xref:System.Windows.Navigation.NavigationService> <xref:System.Windows.Controls.Page> <xref:System.Windows.Navigation.NavigationService.GetNavigationService%2A>のに移動したを取得するには、メソッドの引数としてへの参照を渡します。 <xref:System.Windows.Controls.Page> 次のコードは、現在<xref:System.Windows.Navigation.NavigationService> <xref:System.Windows.Controls.Page>ののを取得する方法を示しています。

[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind1)]
[!code-csharp[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPage.xaml.cs#getnscodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPage.xaml.vb#getnscodebehind2)]

<xref:System.Windows.Navigation.NavigationService> <xref:System.Windows.Controls.Page>のを検索するためのショートカットとして<xref:System.Windows.Controls.Page.NavigationService%2A> 、はプロパティを実装します。<xref:System.Windows.Controls.Page> これを次の例に示します。

[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind1)]
[!code-csharp[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/GetNSPageShortCut.xaml.cs#getnsshortcutcodebehind2)]
[!code-vb[NavigationOverviewSnippets#GetNSShortcutCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/GetNSPageShortCut.xaml.vb#getnsshortcutcodebehind2)]

> [!NOTE]
> は<xref:System.Windows.Controls.Page> <xref:System.Windows.Navigation.NavigationService> 、イベントを発生<xref:System.Windows.FrameworkElement.Loaded>させるとき<xref:System.Windows.Controls.Page>に、への参照のみを取得できます。

#### <a name="programmatic-navigation-to-a-page-object"></a>ページ オブジェクトへのプログラム ナビゲーション

次の例は、を使用し<xref:System.Windows.Navigation.NavigationService>てプログラムで<xref:System.Windows.Controls.Page>に移動する方法を示しています。 ナビゲート先のは<xref:System.Windows.Controls.Page> 、単一のパラメーターなしのコンストラクターを使用してのみインスタンス化できるため、プログラムによるナビゲーションが必要です。 パラメーター <xref:System.Windows.Controls.Page>なしのコンストラクターを持つは、次のマークアップとコードに示されています。

[!code-xaml[NavigationOverviewSnippets#PageWithNonDefaultConstructorXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml#pagewithnondefaultconstructorxaml)]

[!code-csharp[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithNonDefaultConstructor.xaml.cs#pagewithnondefaultconstructorcodebehind)]
[!code-vb[NavigationOverviewSnippets#PageWithNonDefaultConstructorCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithNonDefaultConstructor.xaml.vb#pagewithnondefaultconstructorcodebehind)]

パラメーターなしのコンストラクターを<xref:System.Windows.Controls.Page>使用してに移動するは、次のマークアップとコードに示されます。<xref:System.Windows.Controls.Page>

[!code-xaml[NavigationOverviewSnippets#NSNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml#nsnavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSNavigationPage.xaml.cs#nsnavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#NSNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSNavigationPage.xaml.vb#nsnavigationpagecodebehind)]

こののをクリックすると、をインスタンス化して、 <xref:System.Windows.Controls.Page>パラメーター化されていないコンストラクターを使用して<xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType>メソッドを呼び出すことによって、ナビゲーションが開始されます。 <xref:System.Windows.Controls.Page> <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.Navigation.NavigationService.Navigate%2A>がパック<xref:System.Windows.Navigation.NavigationService> [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]ではなく、移動先のオブジェクトへの参照を受け入れます。

#### <a name="programmatic-navigation-with-a-pack-uri"></a>パック URI によるプログラム ナビゲーション

プログラムによってパック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]を構築する必要がある場合 (実行時にパック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]を特定できる場合など) は、 <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType>メソッドを使用できます。 これを次の例に示します。

[!code-xaml[NavigationOverviewSnippets#NSUriNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml#nsurinavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSUriNavigationPage.xaml.cs#nsurinavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#NSUriNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSUriNavigationPage.xaml.vb#nsurinavigationpagecodebehind)]

#### <a name="refreshing-the-current-page"></a>現在のページの更新

プロパティに<xref:System.Windows.Controls.Page> [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]格納されているパックと同じパックがある場合、はダウンロードされません。 <xref:System.Windows.Navigation.NavigationService.Source%2A?displayProperty=nameWithType> 強制的[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]に現在のページをダウンロードするには、次の<xref:System.Windows.Navigation.NavigationService.Refresh%2A?displayProperty=nameWithType>例に示すように、メソッドを呼び出すことができます。

[!code-xaml[NavigationOverviewSnippets#NSRefreshNavigationPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml#nsrefreshnavigationpagexaml1)]

[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind1)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind1)]
[!code-csharp[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NSRefreshNavigationPage.xaml.cs#nsrefreshnavigationpagecodebehind2)]
[!code-vb[NavigationOverviewSnippets#NSRefreshNavigationPageCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/NSRefreshNavigationPage.xaml.vb#nsrefreshnavigationpagecodebehind2)]

<a name="Navigation_Lifetime"></a>

### <a name="navigation-lifetime"></a>ナビゲーションの有効期間

これまでに説明したように、ナビゲーションを開始するには多くの方法があります。 ナビゲーションが開始されている間、ナビゲーションの進行中に、によって<xref:System.Windows.Navigation.NavigationService>実装された次のイベントを使用して、ナビゲーションを追跡し、影響を与えることができます。

- <xref:System.Windows.Navigation.NavigationService.Navigating>。 新しいナビゲーションが要求されたときに発生します。 ナビゲーションのキャンセルに使用できます。

- <xref:System.Windows.Navigation.NavigationService.NavigationProgress>。 ナビゲーション進行状況の情報提供を目的として、ダウンロード中に定期的に発生します。

- <xref:System.Windows.Navigation.NavigationService.Navigated>。 ページの位置が特定され、ダウンロードされたときに発生します。

- <xref:System.Windows.Navigation.NavigationService.NavigationStopped>。 ナビゲーションが停止したとき (を呼び<xref:System.Windows.Navigation.NavigationService.StopLoading%2A>出すことによって)、または現在のナビゲーションの進行中に新しいナビゲーションが要求されたときに発生します。

- <xref:System.Windows.Navigation.NavigationService.NavigationFailed>。 要求されたコンテンツにナビゲートするときにエラーが発生したときに発生します。

- <xref:System.Windows.Navigation.NavigationService.LoadCompleted>。 ナビゲート先のコンテンツが読み込まれ、解析されて、レンダリングが開始されたときに発生します。

- <xref:System.Windows.Navigation.NavigationService.FragmentNavigation>。 コンテンツ フラグメントへのナビゲーションが開始されたときに、次のタイミングで発生します。

  - 目的のフラグメントが現在のコンテンツの場合は、すぐに発生します。

  - 目的のフラグメントが別のコンテンツにある場合は、ソース コンテンツが読み込まれた後で発生します。

ナビゲーション イベントは、次の図に示されている順序で発生します。

![ページナビゲーションのフローチャート](./media/navigation-overview/order-of-navigation-events.png "ページナビゲーションイベントのフローチャート")

一般に、は<xref:System.Windows.Controls.Page>これらのイベントについては考慮しません。 多くの場合、アプリケーションで問題が発生する可能性があります。そのため、これらのイベントは<xref:System.Windows.Application>クラスによっても発生します。

- <xref:System.Windows.Application.Navigating?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationProgress?displayProperty=nameWithType>

- <xref:System.Windows.Application.Navigated?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationFailed?displayProperty=nameWithType>

- <xref:System.Windows.Application.NavigationStopped?displayProperty=nameWithType>

- <xref:System.Windows.Application.LoadCompleted?displayProperty=nameWithType>

- <xref:System.Windows.Application.FragmentNavigation?displayProperty=nameWithType>

がイベントを<xref:System.Windows.Application> 発生させるたびに、クラスは対応するイベントを発生<xref:System.Windows.Navigation.NavigationService>させます。 <xref:System.Windows.Controls.Frame>と<xref:System.Windows.Navigation.NavigationWindow>は、それぞれのスコープ内のナビゲーションを検出するために同じイベントを提供します。

場合によっては<xref:System.Windows.Controls.Page> 、これらのイベントに関心があることもあります。 たとえば、は<xref:System.Windows.Controls.Page> 、ナビゲーションをキャンセル<xref:System.Windows.Navigation.NavigationService.Navigating?displayProperty=nameWithType>するかどうかを判断するために、イベントを処理する場合があります。 これを次の例に示します。

[!code-xaml[NavigationOverviewSnippets#CancelNavigationPageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml#cancelnavigationpagexaml)]

[!code-csharp[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/CancelNavigationPage.xaml.cs#cancelnavigationpagecodebehind)]
[!code-vb[NavigationOverviewSnippets#CancelNavigationPageCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/CancelNavigationPage.xaml.vb#cancelnavigationpagecodebehind)]

上の例のように、から<xref:System.Windows.Controls.Page>ナビゲーションイベントを使用してハンドラーを登録する場合は、イベントハンドラーの登録を解除する必要もあります。 そうでない場合は、ナビゲーションが履歴を使用して[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]ナビゲーションを<xref:System.Windows.Controls.Page>記憶する方法に関して副作用が生じる可能性があります。

<a name="NavigationHistory"></a>

### <a name="remembering-navigation-with-the-journal"></a>履歴によるナビゲーションの記憶

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は、戻るスタックと進むスタックの 2 つのスタックを使用して、ナビゲート元のページを記憶します。 現在<xref:System.Windows.Controls.Page>のから新規<xref:System.Windows.Controls.Page>または既存<xref:System.Windows.Controls.Page>のに移動すると、現在<xref:System.Windows.Controls.Page>のが*バックスタック*に追加されます。 現在<xref:System.Windows.Controls.Page>のから前<xref:System.Windows.Controls.Page>のに移動すると、現在<xref:System.Windows.Controls.Page>のが*前方スタック*に追加されます。 戻るスタック、進むスタック、およびそれらを管理する機能を、まとめて履歴と呼びます。 バックスタックと転送スタックの各項目は<xref:System.Windows.Navigation.JournalEntry>クラスのインスタンスであり、*ジャーナルエントリ*と呼ばれます。

#### <a name="navigating-the-journal-from-internet-explorer"></a>Internet Explorer からの履歴のナビゲート

概念的には、journal は Internet Explorer の **[戻る]** ボタンと **[進む]** ボタンと同じ方法で動作します。 これを次の図に示します。

![[戻る] ボタンと [進む] ボタン](./media/navigation-overview/back-and-forward-navigation.png "[戻る] ボタンと [進む] ボタンを使用して移動します。")

Internet [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] explorer でホストされている[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]の場合、は、journal [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]を internet explorer のナビゲーションに統合します。 これにより、ユーザーは Internet Explorer [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]の **[戻る]** 、 **[進む]** 、 **[最近使ったページ]** の各ボタンを使用して、内のページを移動できます。

> [!IMPORTANT]
> Internet Explorer では、ユーザーがに移動してからに[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]戻ると、保持されていないページの履歴項目だけが履歴に保持されます。 ページを維持したままにする方法については、このトピックで後述する「[ページの有効期間と履歴](#PageLifetime)」を参照してください。

既定では、 <xref:System.Windows.Controls.Page> [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] Internet Explorer の **[最近使ったページ]** の一覧に表示されるのテキスト<xref:System.Windows.Controls.Page>は、のです。 多くの場合、これは、ユーザーにとって特に意味がありません。 幸い、次のオプションのいずれかを使用して、テキストを変更できます。

1. 添付`JournalEntry.Name`属性値。

2. `Page.Title`属性値。

3. [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]現在`Page.WindowTitle` のの<xref:System.Windows.Controls.Page>属性値と。

4. 現在の [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] の <xref:System.Windows.Controls.Page>。 (既定)

これらのオプションの順序は、テキスト検索の優先順位と一致します。 たとえば、が設定`JournalEntry.Name`されている場合、他の値は無視されます。

次の例では`Page.Title` 、属性を使用して、journal エントリに対して表示されるテキストを変更します。

[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup1)]
[!code-xaml[NavigationOverviewSnippets#PageTitleMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml#pagetitlemarkup2)]

[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind1)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind1)]
[!code-csharp[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithTitle.xaml.cs#pagetitlecodebehind2)]
[!code-vb[NavigationOverviewSnippets#PageTitleCODEBEHIND2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigationOverviewSnippets/VisualBasic/PageWithTitle.xaml.vb#pagetitlecodebehind2)]

#### <a name="navigating-the-journal-using-wpf"></a>WPF を使用する履歴のナビゲート

ユーザーは、Internet Explorer の **[戻る]** 、 **[進む]** 、および 最近 の各**ページ**を使用して履歴内を移動できますが、で[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]提供される宣言型とプログラム機構の両方を使用して履歴を移動することもできます。 これを行う理由の1つは、ページ[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]にカスタムナビゲーションを提供することです。

によって<xref:System.Windows.Input.NavigationCommands>公開されているナビゲーションコマンドを使用して、の journal ナビゲーションサポートを宣言によって追加できます。 次の例は、ナビゲーションコマンドの`BrowseBack`使用方法を示しています。

[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml1)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml2)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml3)]
[!code-xaml[NavigationOverviewSnippets#NavigationCommandsPageXAML4](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/NavigationCommandsPage.xaml#navigationcommandspagexaml4)]

<xref:System.Windows.Navigation.NavigationService>クラスの次のいずれかのメンバーを使用して、プログラムを使用して履歴をナビゲートできます。

- <xref:System.Windows.Navigation.NavigationService.GoBack%2A>

- <xref:System.Windows.Navigation.NavigationService.GoForward%2A>

- <xref:System.Windows.Navigation.NavigationService.CanGoBack%2A>

- <xref:System.Windows.Navigation.NavigationService.CanGoForward%2A>

このトピックの「[ナビゲーション履歴によるコンテンツの状態の保持](#RetainingContentStateWithNavigationHistory)」で説明されているように、履歴はプログラムによって操作することもできます。

<a name="PageLifetime"></a>

### <a name="page-lifetime-and-the-journal"></a>ページの有効期間と履歴

グラフィックス、アニメーション、メディアなどのリッチコンテンツを含む複数のページを含むを考えてみましょう。[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] このようなページのメモリ使用量は、特にビデオやオーディオ メディアが使用されている場合、非常に大きくなることがあります。 移動先のページがジャーナルによって "記憶" されるため、 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]このような場合、大量のメモリをすばやく消費する可能性があります。

このため、履歴の既定の動作では、 <xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Page>オブジェクトへの参照ではなく、各履歴エントリにメタデータが格納されます。 履歴項目に移動すると、その<xref:System.Windows.Controls.Page>メタデータを使用して、指定した<xref:System.Windows.Controls.Page>の新しいインスタンスが作成されます。 その結果、移動する<xref:System.Windows.Controls.Page>各には、次の図に示す有効期間があります。

![ページの有効期間](./media/navigation-overview/navigated-page-lifetime.png "これは、ページが移動されたときの有効期間を示します。")

既定のジャーナル動作を使用すると、メモリ使用量を節約できますが、ページごとのレンダリングのパフォーマンスが低下する可能性があります。特に大量<xref:System.Windows.Controls.Page>のコンテンツがある場合は、の再インスタンス化に時間がかかることがあります。 インスタンスを<xref:System.Windows.Controls.Page>ジャーナルに保持する必要がある場合は、2つの方法で作成できます。 まず、 <xref:System.Windows.Controls.Page> <xref:System.Windows.Navigation.NavigationService.Navigate%2A?displayProperty=nameWithType>メソッドを呼び出して、オブジェクトにプログラムで移動することができます。

次[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]に、 <xref:System.Windows.Controls.Page.KeepAlive%2A>プロパティをに<xref:System.Windows.Controls.Page> `true`設定することによって、のインスタンスをジャーナルに保持するように指定`false`できます (既定値はです)。 次の例に示すように、マークアップ<xref:System.Windows.Controls.Page.KeepAlive%2A>で宣言によって設定できます。

[!code-xaml[NavigationOverviewSnippets#KeepAlivePageXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/KeepAlivePage.xaml#keepalivepagexaml)]

保持され<xref:System.Windows.Controls.Page>ているの有効期間は、そうでないものとはわずかに異なります。 保持されて<xref:System.Windows.Controls.Page>いるが初めて移動したときは、が保持され<xref:System.Windows.Controls.Page>ていないのようにインスタンス化されます。 ただし、の<xref:System.Windows.Controls.Page>インスタンスはジャーナルに保持されるため、ジャーナルに残っている限り、再インスタンス化されることはありません。 その結果、に<xref:System.Windows.Controls.Page>移動するたびに呼び出さ<xref:System.Windows.Controls.Page>れる必要がある初期化ロジックがにある場合、コンストラクターから<xref:System.Windows.FrameworkElement.Loaded>イベントのハンドラーにそれを移動する必要があります。 次の図<xref:System.Windows.FrameworkElement.Loaded>に示すように、と<xref:System.Windows.FrameworkElement.Unloaded>の各<xref:System.Windows.Controls.Page>イベントは、それぞれがに移動するたびに発生します。

![読み込みイベントとアンロードイベントが発生したとき](./media/navigation-overview/loaded-and-unloaded-events.png "読み込まれたイベントとアンロードされたイベントは、ページに移動したり、ページを移動したりすると発生します。")

<xref:System.Windows.Controls.Page>が保持されていない場合は、次のいずれの操作も実行しないでください。

- ページへの参照、またはその一部への参照を格納する。

- ページによって実装されていないイベントのイベント ハンドラーを登録する。

これらのいずれかを実行すると、履歴<xref:System.Windows.Controls.Page>から削除された後でも、を強制的にメモリに保持する参照が作成されます。

一般に、 <xref:System.Windows.Controls.Page> alive を保持しない<xref:System.Windows.Controls.Page>既定の動作を使用することをお勧めします。 ただし、これには、次のセクションで説明されている状態も関係します。

<a name="RetainingContentStateWithNavigationHistory"></a>

### <a name="retaining-content-state-with-navigation-history"></a>ナビゲーション履歴によるコンテンツの状態の保持

が維持されず、ユーザーからデータを収集するコントロールがある場合、ユーザーがに移動してから<xref:System.Windows.Controls.Page>に戻ると、データはどうなりますか。 <xref:System.Windows.Controls.Page> ユーザー エクスペリエンスの観点から見ると、ユーザーは以前に入力したデータが表示されることを期待します。 残念ながら、各ナビゲーションを使用し<xref:System.Windows.Controls.Page>ての新しいインスタンスが作成されるため、データを収集したコントロールは再インスタンス化され、データは失われます。

幸いにも、履歴では、制御データ<xref:System.Windows.Controls.Page>など、ナビゲーション全体でデータを記憶することがサポートされています。 具体的には、各<xref:System.Windows.Controls.Page>のジャーナルエントリは、関連付けられている<xref:System.Windows.Controls.Page>状態の一時コンテナーとして機能します。 次の手順では、をナビゲートするとき<xref:System.Windows.Controls.Page>に、このサポートがどのように使用されるかを説明します。

1. 現在<xref:System.Windows.Controls.Page>ののエントリが履歴に追加されます。

2. の<xref:System.Windows.Controls.Page>状態は、そのページの履歴エントリと共に格納され、バックスタックに追加されます。

3. 新しい<xref:System.Windows.Controls.Page>に移動します。

ページ<xref:System.Windows.Controls.Page>がに戻ると、ジャーナルを使用して次の手順が実行されます。

1. <xref:System.Windows.Controls.Page> (バックスタックの一番上のジャーナルエントリ) がインスタンス化されます。

2. は、の履歴エントリ<xref:System.Windows.Controls.Page>と共に保存された状態で更新されます。<xref:System.Windows.Controls.Page>

3. <xref:System.Windows.Controls.Page>はに戻ります。

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]で次のコントロールが使用されている場合、 <xref:System.Windows.Controls.Page>は自動的にこのサポートを使用します。

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

がこれら<xref:System.Windows.Controls.Page>のコントロールを使用する場合は、次の <xref:System.Windows.Controls.ListBox>図<xref:System.Windows.Controls.Page>に示すように、ユーザーに入力されたデータがナビゲーション間で記憶されます。

![状態を記憶するコントロールを含むページ](./media/navigation-overview/data-remembered-across-page-navigations.png "入力したデータはページナビゲーション間で記憶されます。")

に上記のリスト以外のコントロール<xref:System.Windows.Controls.Page> がある場合、または状態がカスタムオブジェクトに格納されている場合は、履歴がナビゲーション全体で状態を記憶するようにコードを記述する必要があります。<xref:System.Windows.Controls.Page>

ナビゲーション全体で<xref:System.Windows.Controls.Page>小規模な状態を記憶する必要がある場合は、 <xref:System.Windows.FrameworkPropertyMetadata.Journal%2A?displayProperty=nameWithType>メタデータフラグで<xref:System.Windows.DependencyProperty>構成されている依存関係プロパティ (「」を参照) を使用できます。

ナビゲーション間で覚えて<xref:System.Windows.Controls.Page>おく必要がある状態が複数のデータで構成されている場合は、1つのクラスで状態をカプセル化し、 <xref:System.Windows.Navigation.IProvideCustomContentState>インターフェイスを実装すると、コードの負担が少なくなることがあります。

<xref:System.Windows.Controls.Page>単独ではなく<xref:System.Windows.Controls.Page> 、のさまざまな状態をナビゲートする必要がある場合は、と<xref:System.Windows.Navigation.NavigationService.AddBackEntry%2A?displayProperty=nameWithType>を<xref:System.Windows.Navigation.IProvideCustomContentState>使用できます。

<a name="Cookies"></a>

### <a name="cookies"></a>クッキー

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]アプリケーションがデータを格納できるもう1つの方法は、メソッド<xref:System.Windows.Application.SetCookie%2A>と<xref:System.Windows.Application.GetCookie%2A>メソッドを使用して作成、更新、および削除される cookie を使用することです。 で[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]作成できる cookie は、他の種類の Web アプリケーションで使用される cookie と同じです。 cookie とは、アプリケーションセッション中またはアプリケーションセッション間でクライアントコンピューター上のアプリケーションによって格納される任意のデータのことです。 クッキー データは、通常、次の形式の名前と値のペアです。

*Name* `=` *Value*

データがに<xref:System.Windows.Application.SetCookie%2A>渡されるときに、クッキーが<xref:System.Uri>設定される場所のと共に、cookie はメモリ内に作成され、現在のアプリケーションセッションの間のみ使用できます。 この種類の cookie は、*セッション cookie*と呼ばれます。

複数のアプリケーション セッションにまたがってクッキーを格納するには、次の形式を使用して、有効期限をクッキーに追加する必要があります。

*NAME* `=` *VALUE* `; expires=DAY, DD-MMM-YYYY HH:MM:SS GMT`

有効期限が切れたクッキーは、cookie の有効[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]期限が切れるまで、現在のインストールのインターネット一時ファイルフォルダーに格納されます。 このような cookie は、アプリケーションセッション間で保持されるため、*永続的なクッキー*と呼ばれます。

<xref:System.Windows.Application.GetCookie%2A>メソッドを呼び出して、セッションと永続的な cookie の両方を取得<xref:System.Uri>し、 <xref:System.Windows.Application.SetCookie%2A>メソッドを使用して cookie が設定されている場所のを渡します。

で[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]クッキーがサポートされるいくつかの方法を次に示します。

- [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]スタンドアロンアプリケーション[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]とは、両方ともクッキーを作成および管理できます。

- によって[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]作成された cookie には、ブラウザーからアクセスできます。

- 同じドメインの [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] は、クッキーを作成して共有できます。

- [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]また、同じドメインの HTML ページでは、cookie を作成して共有できます。

- およびルース[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ページが Web 要求を行うときに、cookie がディスパッチされます。

- Iframe でホストさ[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]れ[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]ているトップレベルのとは、どちらもクッキーにアクセスできます。

- で[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]の Cookie のサポートは、サポートされているすべてのブラウザーで同じです。

- Internet Explorer では、cookie に関連する P3P ポリシーは、 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]特にファーストパーティおよびサードパーティ[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]に関して、によって受け入れられます。

<a name="Structured_Navigation"></a>

### <a name="structured-navigation"></a>構造化ナビゲーション

データを1つ<xref:System.Windows.Controls.Page>のから別のに渡す必要がある場合は、のパラメーターなしのコンストラクターに、その<xref:System.Windows.Controls.Page>データを引数として渡すことができます。 この手法を使用する<xref:System.Windows.Controls.Page>場合は、alive を保持する必要があることに注意してください。そうでない場合は、次<xref:System.Windows.Controls.Page>にに[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]移動するときに、パラメーターなしのコンストラクターを使用してを再インスタンス<xref:System.Windows.Controls.Page>化します。

また、 <xref:System.Windows.Controls.Page>に渡す必要があるデータで設定されたプロパティを実装することもできます。 ただし、が移動し<xref:System.Windows.Controls.Page> <xref:System.Windows.Controls.Page>たにデータを渡す必要がある場合は、注意が必要になります。 問題は、ナビゲーションから移動後にが返されることを<xref:System.Windows.Controls.Page>保証するためのメカニズムが、ナビゲーションでネイティブにサポートされていないことです。 基本的に、ナビゲーションは、"呼び出す/戻る" というセマンティクスをサポートしていません。 この問題を解決する[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]ために<xref:System.Windows.Navigation.PageFunction%601> 、には、予測可能で構造化<xref:System.Windows.Controls.Page>された方法でにが返されるようにするために使用できるクラスが用意されています。 詳細については、「[構造化ナビゲーションの概要](structured-navigation-overview.md)」を参照してください。

<a name="The_NavigationWindow_Class"></a>

## <a name="the-navigationwindow-class"></a>NavigationWindow クラス

ここまでで、ナビゲート可能なコンテンツを含むアプリケーションをビルドするために使用する可能性が最も高いナビゲーション サービスの全容を説明しました。 これらのサービスについては、 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]のコンテキストで説明しました[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]。ただし、これらのサービスはに限定されていません。 最新のオペレーティングシステムと Windows アプリケーションでは、最新のユーザーのブラウザーエクスペリエンスを利用して、ブラウザー形式のナビゲーションをスタンドアロンアプリケーションに組み込むことができます。 一般的な例は、次のとおりです。

- **単語の類義語辞典**:単語の選択項目を移動します。

- **エクスプローラー**:ファイルとフォルダーに移動します。

- **ウィザード**:複雑なタスクを複数のページに分割し、移動することができます。 例として、windows の機能の追加と削除を処理する Windows コンポーネントウィザードがあります。

スタンドアロンアプリケーションにブラウザースタイルのナビゲーションを組み込むには、 <xref:System.Windows.Navigation.NavigationWindow>クラスを使用できます。 <xref:System.Windows.Navigation.NavigationWindow>は、 <xref:System.Windows.Window>から派生し、を提供する[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]ナビゲーションの同じサポートを使用して拡張します。 は、スタンド<xref:System.Windows.Navigation.NavigationWindow>アロンアプリケーションのメインウィンドウとして、またはダイアログボックスなどのセカンダリウィンドウとして使用できます。

<xref:System.Windows.Navigation.NavigationWindow> [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ( 、<xref:System.Windows.Controls.Page>など) の最上位レベルのクラスと同様に、を実装するには、マークアップと分離コードの組み合わせを使用します。<xref:System.Windows.Window> これを次の例に示します。

[!code-xaml[IntroToNavNavigationWindowSnippets#NavigationWindowMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml#navigationwindowmarkup)]

[!code-csharp[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/MainWindow.xaml.cs#navigationwindowcodebehind)]
[!code-vb[IntroToNavNavigationWindowSnippets#NavigationWindowCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/MainWindow.xaml.vb#navigationwindowcodebehind)]

このコードは、 <xref:System.Windows.Navigation.NavigationWindow> <xref:System.Windows.Navigation.NavigationWindow>を開いたときに<xref:System.Windows.Controls.Page> 、(ホームページの .xaml) に自動的に移動するを作成します。 がメインアプリケーションウィンドウである場合は、 `StartupUri`属性を使用して起動できます。 <xref:System.Windows.Navigation.NavigationWindow> これを次のマークアップに示します。

[!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchNavWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/App.xaml#applaunchnavwindow)]

次の図は、 <xref:System.Windows.Navigation.NavigationWindow>スタンドアロンアプリケーションのメインウィンドウとしてを示しています。

![メインウィンドウ](./media/navigation-overview/navigation-window-as-main-window.png "メインウィンドウとしてのナビゲーションウィンドウ")

この図からは、前の例の<xref:System.Windows.Navigation.NavigationWindow> <xref:System.Windows.Navigation.NavigationWindow>実装コードでが設定されていない場合でも、にタイトルがあることがわかります。 代わりに、次のコードに示すよう<xref:System.Windows.Controls.Page.WindowTitle%2A>に、プロパティを使用してタイトルを設定します。

[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP1](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup1)]
[!code-xaml[IntroToNavNavigationWindowSnippets#HomePageMARKUP2](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/HomePage.xaml#homepagemarkup2)]

プロパティとプロパティ<xref:System.Windows.Controls.Page.WindowHeight%2A>を設定すると<xref:System.Windows.Navigation.NavigationWindow>、にも影響します。 <xref:System.Windows.Controls.Page.WindowWidth%2A>

通常、動作または外観<xref:System.Windows.Navigation.NavigationWindow>をカスタマイズする必要がある場合は、独自のを実装します。 どちらも行わない場合は、ショートカットを使用できます。 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] <xref:System.Windows.Application.StartupUri%2A> <xref:System.Windows.Navigation.NavigationWindow> <xref:System.Windows.Controls.Page>のパックをスタンドアロンアプリケーション<xref:System.Windows.Application>のとして指定した場合は、によってがホストされるが自動的に作成<xref:System.Windows.Controls.Page>されます。 次のマークアップは、この方法を示しています。

[!code-xaml[IntroToNavNavigationWindowSnippets#AppLaunchPage](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/AnotherApp.xaml#applaunchpage)]

ダイアログボックス<xref:System.Windows.Navigation.NavigationWindow>などのセカンダリアプリケーションウィンドウをにする場合は、次の例のコードを使用してそれを開くことができます。

[!code-csharp[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/csharp/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/CSharp/DialogOwnerWindow.xaml.cs#createnwdialogbox)]
[!code-vb[IntroToNavNavigationWindowSnippets#CreateNWDialogBox](~/samples/snippets/visualbasic/VS_Snippets_Wpf/IntroToNavNavigationWindowSnippets/VisualBasic/DialogOwnerWindow.xaml.vb#createnwdialogbox)]

次の図に、結果を示します。

![ダイアログボックス](./media/navigation-overview/navigation-window-as-dialog-box.png "ダイアログボックスとしてのナビゲーションウィンドウ")

ご覧のように、 <xref:System.Windows.Navigation.NavigationWindow>には、ユーザーが journal を操作できるようにするための Internet Explorer スタイルの **[戻る]** ボタンと **[進む]** ボタンが表示されています。 これらのボタンは、次の図に示されているように、同じユーザー エクスペリエンスを提供します。

![NavigationWindow の [戻る] ボタンと [進む] ボタン](./media/navigation-overview/back-and-forward-buttons-in-navigation-window.png "ナビゲーションウィンドウの [戻る] ボタンと [進む] ボタン")

ページに独自のジャーナルナビゲーションサポートと UI が用意されている場合は、 <xref:System.Windows.Navigation.NavigationWindow.ShowsNavigationUI%2A>プロパティの値を<xref:System.Windows.Navigation.NavigationWindow>に設定する`false`ことによって、によって表示される **[戻る]** と **[進む]** ボタンを非表示にすることができます。

または、のカスタマイズサポート[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]を使用して、 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]の<xref:System.Windows.Navigation.NavigationWindow>を置き換えることもできます。

<a name="Frame_in_Standalone_Applications"></a>

## <a name="the-frame-class"></a>Frame クラス

ブラウザーと<xref:System.Windows.Navigation.NavigationWindow>は、ナビゲーション可能なコンテンツをホストする windows です。 場合によっては、アプリケーションには、ウィンドウ全体でホストする必要のないコンテンツがあることもあります。 このようなコンテンツは、代わりに、他のコンテンツ内でホストされます。 クラスを使用して、 <xref:System.Windows.Controls.Frame>他のコンテンツに誘導可能なコンテンツを挿入できます。 <xref:System.Windows.Controls.Frame>は、と<xref:System.Windows.Navigation.NavigationWindow> [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]と同じサポートを提供します。

次の例は、 <xref:System.Windows.Controls.Frame> `Frame`要素を使用して<xref:System.Windows.Controls.Page>を宣言に追加する方法を示しています。

[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPage.xaml#framehostpagexaml3)]

このマークアップは`Source` 、 `Frame`要素の属性に、の[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] <xref:System.Windows.Controls.Frame>最初の<xref:System.Windows.Controls.Page>移動先ののパックを設定します。 次の図は、 [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] <xref:System.Windows.Controls.Page>と<xref:System.Windows.Controls.Frame> 、複数のページ間を移動するを持つを示しています。

![複数のページ間を移動するフレーム](./media/navigation-overview/frame-navigation-between-multiple-pages.png "これは、複数のページ間のフレームナビゲーションを示しています。")

のコンテンツ内でのみを<xref:System.Windows.Controls.Frame>使用する必要はありません。 <xref:System.Windows.Controls.Page> また、 <xref:System.Windows.Controls.Frame> <xref:System.Windows.Window>のコンテンツ内でをホストすることも一般的です。

既定では<xref:System.Windows.Controls.Frame> 、は別の履歴がない場合にのみ独自の履歴を使用します。 <xref:System.Windows.Navigation.NavigationWindow> <xref:System.Windows.Navigation.NavigationWindow> [!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] <xref:System.Windows.Controls.Frame>がまたはのいずれかの内部でホストされているコンテンツの一部である場合、はまたはに属する履歴を使用します。[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)] <xref:System.Windows.Controls.Frame> 場合によっては<xref:System.Windows.Controls.Frame> 、独自のジャーナルを使用しなければならないこともあります。 その理由の1つは、 <xref:System.Windows.Controls.Frame>によってホストされるページ内での journal ナビゲーションを許可することです。 これを次の図に示します。

![フレームとページのダイアグラム](./media/navigation-overview/journal-navigation-within-pages-hosted-by-a-frame.png "これは、フレームによってホストされるページ内の journal ナビゲーションを示しています。")

<xref:System.Windows.Controls.Frame>この場合、の<xref:System.Windows.Controls.Frame.JournalOwnership%2A>プロパティ<xref:System.Windows.Controls.Frame>をに<xref:System.Windows.Navigation.JournalOwnership.OwnsJournal>設定することによって、独自のジャーナルを使用するようにを構成できます。 これを次のマークアップに示します。

[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageOwnJournalXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnJournal.xaml#framehostpageownjournalxaml3)]

次の図は、独自の履歴を使用<xref:System.Windows.Controls.Frame>する内で移動した場合の影響を示しています。

![独自の履歴を使用するフレーム](./media/navigation-overview/frame-uses-its-own-journal.png "これは、独自の履歴を使用するフレーム内で移動した場合の効果を示しています。")

履歴エントリは、Internet Explorer ではなく、 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]の<xref:System.Windows.Controls.Frame>ナビゲーションによって表示されることに注意してください。

> [!NOTE]
> がでホストされているコンテンツの一部である<xref:System.Windows.Controls.Frame>場合[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]、は独自の履歴を使用します。その結果、によって独自のナビゲーションが表示されます。 <xref:System.Windows.Window> <xref:System.Windows.Controls.Frame>

ユーザーエクスペリエンスで<xref:System.Windows.Controls.Frame> 、ナビゲーション[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]を表示せずに独自の履歴を提供する必要がある場合は[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 、 <xref:System.Windows.Controls.Frame.NavigationUIVisibility%2A>をに<xref:System.Windows.Visibility.Hidden>設定することによって、ナビゲーションを非表示にすることができます。 これを次のマークアップに示します。

[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml1)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml2)]
[!code-xaml[NavigationOverviewSnippets#FrameHostPageHidesUIXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHostPageOwnHiddenJournal.xaml#framehostpagehidesuixaml3)]

<a name="Navigation_Hosts"></a>

## <a name="navigation-hosts"></a>ナビゲーション ホスト

<xref:System.Windows.Controls.Frame>および<xref:System.Windows.Navigation.NavigationWindow>は、ナビゲーションホストと呼ばれるクラスです。 *ナビゲーションホスト*は、コンテンツに移動して表示できるクラスです。 これを実現するために、各ナビゲーションホスト<xref:System.Windows.Navigation.NavigationService>は独自のおよびジャーナルを使用します。 ナビゲーション ホストの基本的な構造を次の図に示します。

![ナビゲーターの図](./media/navigation-overview/navigation-host-construction.png "ナビゲーションホストの基本的な構築")

基本的に、これ<xref:System.Windows.Navigation.NavigationWindow>に<xref:System.Windows.Controls.Frame>より、とは、ブラウザーでホスト[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]されるときにが提供するのと同じナビゲーションサポートを提供できます。

およびジャーナル<xref:System.Windows.Navigation.NavigationService>を使用するだけでなく、ナビゲーションホストは、 <xref:System.Windows.Navigation.NavigationService>を実装するのと同じメンバーを実装します。 これを次の図に示します。

![フレーム内および NavigationWindow 内のジャーナル](./media/navigation-overview/navigation-window-and-frame.png "ナビゲーションウィンドウとフレーム")

これにより、これらのメンバーに対して直接、ナビゲーション サポートをプログラミングできます。 でホストされて[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Controls.Frame> <xref:System.Windows.Window>いるのカスタムナビゲーションを提供する必要がある場合は、この点を考慮してください。 さらに、どちらの種類も`BackStack` 、(<xref:System.Windows.Navigation.NavigationWindow.BackStack%2A?displayProperty=nameWithType>、 <xref:System.Windows.Controls.Frame.BackStack%2A?displayProperty=nameWithType>) および`ForwardStack` (<xref:System.Windows.Navigation.NavigationWindow.ForwardStack%2A?displayProperty=nameWithType>, <xref:System.Windows.Controls.Frame.ForwardStack%2A?displayProperty=nameWithType>) を含む追加のナビゲーション関連のメンバーを実装します。これにより、履歴のエントリを列挙できます。stack と forward stack。

前に述べたように、アプリケーション内に複数の履歴が存在することがあります。 次の図は、この例を示しています。

![1 つのアプリケーション内の複数のジャーナル](./media/navigation-overview/multiple-journals-in-one-application.png "アプリケーション内の複数のジャーナルの例を次に示します。")

<a name="Navigating_to_Content_Other_than_Pages"></a>

## <a name="navigating-to-content-other-than-xaml-pages"></a>XAML ページ以外のコンテンツへのナビゲート

このトピックでは<xref:System.Windows.Controls.Page> 、と[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]パックを使用して、の[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]さまざまなナビゲーション機能を紹介しました。 ただし、アプリケーションにコンパイルされ[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)] たは、移動できるコンテンツの唯一の種類ではなく、パックはコンテンツを識別する唯一の方法ではありません。<xref:System.Windows.Controls.Page>

このセクションで示すように、ルース[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイル、HTML ファイル、およびオブジェクトに移動することもできます。

<a name="Navigating_to_Loose_XAML_Files"></a>

### <a name="navigating-to-loose-xaml-files"></a>Loose XAML ファイルへのナビゲート

圧縮[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]されていないファイルとは、次の特性を持つファイルです。

- (つまり[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 、コードなし) のみを含みます。

- 適切な名前空間宣言がある。

- .xaml ファイル名拡張子を持つ。

たとえば、ルース[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイルとして保存されている次のコンテンツを考えてみます。

[!code-xaml[NavigationOverviewSnippets#LooseXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/Person.xaml#loosexaml)]

ファイルをダブルクリックすると、ブラウザーが開き、コンテンツにナビゲートして、コンテンツを表示します。 これを次の図に示します。

![ユーザー .xaml ファイルの内容の表示](./media/navigation-overview/contents-of-person-xaml-file.png "ユーザーの .xaml ファイルの内容を表示します。")

次のような圧縮[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]されていないファイルを表示できます。

- ローカル コンピューター、イントラネット、またはインターネット上の Web サイト。

- [!INCLUDE[TLA#tla_unc](../../../../includes/tlasharptla-unc-md.md)]ファイル共有。

- ローカル ディスク。

圧縮[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]されていないファイルは、ブラウザーのお気に入りに追加することも、ブラウザーのホームページに追加することもできます。

> [!NOTE]
> ルース[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ページのパブリッシュと起動の詳細については、「 [WPF アプリケーションの配置](deploying-a-wpf-application-wpf.md)」を参照してください。

緩い[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]場合の制限事項の1つは、部分信頼で実行するのが安全なコンテンツのみをホストできることです。 たとえば、は`Window` 、ルース[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイルのルート要素にすることはできません。 詳細については、「 [WPF 部分信頼セキュリティ](../wpf-partial-trust-security.md)」を参照してください。

<a name="Navigating_to_HTML_Files_Using_Frame"></a>

### <a name="navigating-to-html-files-by-using-frame"></a>フレームを使用した HTML ファイルへのナビゲート

ご想像のとおり、HTML に移動することもできます。 Http スキームを使用するを[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]指定するだけで済みます。 たとえば、次[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]の例は、 <xref:System.Windows.Controls.Frame> HTML ページに移動するを示しています。

[!code-xaml[NavigationOverviewSnippets#FrameHtmlNavMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/FrameHTMLNavPage.xaml#framehtmlnavmarkup)]

HTML に移動するには、特殊なアクセス許可が必要です。 たとえば、インターネットゾーン部分信頼セキュリティサンド[!INCLUDE[TLA2#tla_xbap](../../../../includes/tla2sharptla-xbap-md.md)]ボックスで実行されているからは移動できません。 詳細については、「 [WPF 部分信頼セキュリティ](../wpf-partial-trust-security.md)」を参照してください。

<a name="Navigating_to_HTML_Files_Using_WebBrowser"></a>

### <a name="navigating-to-html-files-by-using-the-webbrowser-control"></a>WebBrowser コントロールを使用した HTML ファイルへのナビゲート

コントロール<xref:System.Windows.Controls.WebBrowser>は、HTML ドキュメントのホスト、ナビゲーション、スクリプト/マネージコードの相互運用性をサポートします。 コントロールの<xref:System.Windows.Controls.WebBrowser>詳細については、 <xref:System.Windows.Controls.WebBrowser>「」を参照してください。

と<xref:System.Windows.Controls.Frame>同様に、を使用<xref:System.Windows.Controls.WebBrowser>して HTML に移動するには、特別なアクセス許可が必要です。 たとえば、部分信頼アプリケーションでは、元のサイトにある HTML にのみ移動できます。 詳細については、「 [WPF 部分信頼セキュリティ](../wpf-partial-trust-security.md)」を参照してください。

<a name="Navigating_to_Objects"></a>

### <a name="navigating-to-custom-objects"></a>カスタム オブジェクトへのナビゲート

カスタムオブジェクトとして格納されているデータがある場合、そのデータを表示する方法<xref:System.Windows.Controls.Page>の1つは、それらのオブジェクトにバインドされたコンテンツを使用してを作成することです (「[データバインディングの概要](../data/data-binding-overview.md)」を参照してください)。 オブジェクトを表示するためだけにページ全体を作成するオーバーヘッドが必要ない場合には、代わりに、オブジェクトに直接ナビゲートすることもできます。

次のコードに実装されているクラスについて考えてみます。`Person`

[!code-csharp[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/Person.cs#personclasscode)]
[!code-vb[NavigateToObjectSnippets#PersonClassCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/Person.vb#personclasscode)]

このファイルに移動するには、 <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A?displayProperty=nameWithType>次のコードに示すように、メソッドを呼び出します。

[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject1)]
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject2)]
[!code-xaml[NavigateToObjectSnippets#PageThatNavsToObject3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml#pagethatnavstoobject3)]

[!code-csharp[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/HomePage.xaml.cs#pagethatnavstoobjectcodebehind)]
[!code-vb[NavigateToObjectSnippets#PageThatNavsToObjectCODEBEHIND](~/samples/snippets/visualbasic/VS_Snippets_Wpf/NavigateToObjectSnippets/VisualBasic/HomePage.xaml.vb#pagethatnavstoobjectcodebehind)]

次の図に、結果を示します。

![クラスに移動するページ](./media/navigation-overview/page-navigates-to-an-object.png "これは、オブジェクトに移動するページの例です。")

この図には、役立つものが何も表示されていません。 実際、表示される値は`ToString` **Person**オブジェクトのメソッドの戻り値です。既定では、これはオブジェクトを表すために使用[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]できる唯一の値です。 メソッドを`ToString`オーバーライドして、より意味のある情報を返すこともできますが、それでも文字列値になります。 のプレゼンテーション機能を利用する1つの[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]手法は、データテンプレートを使用することです。 特定の種類のオブジェクトに関連[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]付けることができるデータテンプレートを実装できます。 次のコードは、 `Person`オブジェクトのデータテンプレートを示しています。

[!code-xaml[NavigateToObjectSnippets#DataTemplateMARKUP](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigateToObjectSnippets/CSharp/App.xaml#datatemplatemarkup)]

ここでは、 `Person` `DataType`属性の`x:Type`マークアップ拡張機能を使用して、データテンプレートが型に関連付けられています。 次`TextBlock` に、<xref:System.Windows.Controls.TextBlock>データテンプレートは、要素 (を参照) をクラスのプロパティにバインドします。`Person` 次の図は、 `Person`オブジェクトの更新された外観を示しています。

![データテンプレートを持つクラスへの移動](./media/navigation-overview/navigating-to-a-class.png "データテンプレートを持つクラスへの移動。")

この方法の利点は、データ テンプレートを再利用して、アプリケーションの任意の場所で オブジェクトを一貫して表示できることによって得られる一貫性です。

データテンプレートの詳細については、「データテンプレートの[概要](../data/data-templating-overview.md)」を参照してください。

<a name="Security"></a>

## <a name="security"></a>セキュリティ

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]ナビゲーションサポートに[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]より、がインターネット経由で移動できるようになり、アプリケーションでサードパーティのコンテンツをホストできるようになります。 アプリケーションとユーザーの両方を有害な動作から[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]保護するために、には、[セキュリティ](../security-wpf.md)と[WPF 部分信頼セキュリティ](../wpf-partial-trust-security.md)について説明されているさまざまなセキュリティ機能が用意されています。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Application.SetCookie%2A>
- <xref:System.Windows.Application.GetCookie%2A>
- [アプリケーション管理の概要](application-management-overview.md)
- [WPF におけるパッケージの URI](pack-uris-in-wpf.md)
- [構造化ナビゲーションの概要](structured-navigation-overview.md)
- [ナビゲーション トポロジの概要](navigation-topologies-overview.md)
- [方法トピック](navigation-how-to-topics.md)
- [WPF アプリケーションの配置](deploying-a-wpf-application-wpf.md)
