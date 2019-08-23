---
title: WPF のグローバリゼーションおよびローカリゼーションの概要
ms.date: 03/30/2017
helpviewer_keywords:
- globalization [WPF], about globalization
- localization [WPF], about localization
ms.assetid: 56e5a5c8-6c96-4d19-b8e1-a5be1dc564af
ms.openlocfilehash: e34b61e14db1e7839173658d71a70240d63c5f8a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917578"
---
# <a name="wpf-globalization-and-localization-overview"></a>WPF のグローバリゼーションおよびローカリゼーションの概要

製品の利用可能性を1つの言語のみに制限すると、お客様の潜在顧客ベースを世界の65億人口の一部に限定できます。 アプリケーションを世界中のユーザーに提供する場合、製品のコスト効率に優れたローカライズ方法の1つは、より多くの顧客にリーチするための最良で経済的な方法の1つです。

この概要では、での[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]グローバリゼーションとローカライズについて説明します。 グローバリゼーションとは、複数の場所で実行されるアプリケーションの設計および開発です。 たとえば、グローバリゼーションでは、異なるカルチャのユーザーに対して、ローカライズされたユーザーインターフェイスと地域データをサポートしています。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]自動レイアウト、サテライトアセンブリ、ローカライズされた属性、コメントなど、グローバリゼーションのデザイン機能を提供します。

ローカライズとは、アプリケーションがサポートする特定のカルチャに合わせて、アプリケーションリソースをローカライズされたバージョンに変換することです。 で[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ローカライズする場合は、 <xref:System.Windows.Markup.Localizer>名前空間の api を使用します。 これらの Api は、 [LocBaml ツールサンプル](https://go.microsoft.com/fwlink/?LinkID=160016)コマンドラインツールを活用しています。 LocBaml を構築して使用する方法の詳細については、「[アプリケーションをローカライズ](how-to-localize-an-application.md)する」を参照してください。

## <a name="best-practices-for-globalization-and-localization-in-wpf"></a>WPF でのグローバリゼーションとローカライズのベストプラクティス

に[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]組み込まれているグローバリゼーションおよびローカリゼーション機能の多くは、このセクションで説明する UI デザインとローカリゼーション関連のヒントに従って作成できます。

### <a name="best-practices-for-wpf-ui-design"></a>WPF UI デザインのベストプラクティス

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]設計するときは、次のベストプラクティスを実装することを検討してください。

- を[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 記述します。コードで作成することは避けてください。[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] を使用[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]してを作成する場合は、組み込みのローカライズ api を使用してを公開します。

- コンテンツのレイアウトに絶対位置と固定サイズを使用することは避けてください。代わりに、相対サイズまたは自動サイズ設定を使用します。

  - を<xref:System.Windows.Window.SizeToContent%2A>使用し、幅と高さを`Auto`に設定したままにします。

  - S[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]を<xref:System.Windows.Controls.Canvas>レイアウトするためにを使用しないでください。

  - と<xref:System.Windows.Controls.Grid>そのサイズ共有機能を使用します。

- ローカライズされたテキストには多くの領域が必要になるため、余白に余分なスペースを用意します。 余分なスペースを使用すると、使用できる文字数を増やすことができます。

- クリッピング<xref:System.Windows.Controls.TextBlock.TextWrapping%2A>を<xref:System.Windows.Controls.TextBlock>回避するには、[オン] を有効にします。

- `xml:lang` 属性を設定します。 この属性は、特定の要素とその子要素のカルチャを表します。 このプロパティの値は、のいくつかの機能[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]の動作を変更します。 たとえば、ハイフネーション、スペルチェック、数字の置換、複雑なスクリプトの整形、およびフォントフォールバックの動作を変更します。 [XAML での xml: lang の処理](../../xaml-services/xml-lang-handling-in-xaml.md)の設定の詳細については、「 [WPF のグローバリゼーション](globalization-for-wpf.md)」を参照してください。

- さまざまな言語で使用されるフォントをより適切に制御できるように、カスタマイズされた複合フォントを作成します。 既定では[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 、は Windows\Fonts ディレクトリ内の GlobalUserInterface フォントを使用します。

- テキストを右から左の形式で表示するカルチャでローカライズされる可能性のあるナビゲーションアプリケーションを作成する場合は、ページ<xref:System.Windows.FlowDirection>がから<xref:System.Windows.Navigation.NavigationWindow>継承<xref:System.Windows.FlowDirection>されないように、すべてのページのを明示的に設定します。

- ブラウザーの外部でホストされているスタンドアロンナビゲーションアプリケーションを作成する場合<xref:System.Windows.Application.StartupUri%2A>は、最初のアプリケーション<xref:System.Windows.Navigation.NavigationWindow>のを`<Application StartupUri="NavigationWindow.xaml">`ページではなくに設定します (例:)。 このデザインでは、ウィンドウと<xref:System.Windows.FlowDirection>ナビゲーションバーのを変更できます。 詳細と例については、「[グローバリゼーションのホームページのサンプル](https://go.microsoft.com/fwlink/?LinkID=159990)」を参照してください。

### <a name="best-practices-for-wpf-localization"></a>WPF のローカライズのベストプラクティス

ベースのアプリケーション[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]をローカライズする場合は、次のベストプラクティスを実装することを検討してください。

- ローカライズコメントを使用して、ローカライザーに追加のコンテキストを提供します。

- ローカリゼーション属性を使用して、要素のプロパティ<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>を選択的に省略するのではなく、ローカリゼーションを制御します。 詳細については[、「ローカリゼーションの属性とコメント](localization-attributes-and-comments.md)」を参照してください。

- および`msbuild -t:updateuid` <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を使用して、のプロパティを追加および確認します。 `-t:checkuid` 開発<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>とローカリゼーションの間の変更を追跡するには、プロパティを使用します。 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>プロパティは、新しい開発変更をローカライズするのに役立ちます。 プロパティを<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]に手動で追加した場合、タスクは通常、単調で正確ではなくなります。

  - ローカライズを開始した<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>後は、プロパティを編集または変更しないでください。

  - 重複<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>するプロパティを使用しないでください (コピーと貼り付けコマンドを使用する場合は、この点に注意してください)。

  - AssemblyInfo. * の`[assembly: NeutralResourcesLanguage("en-US",   UltimateResourceFallbackLocation.Satellite)]`場所を設定して、フォールバックに適した言語を指定します(たとえば、)。`UltimateResourceFallback`

    プロジェクトファイル内の`<UICulture>`タグを省略して、メインアセンブリにソース言語を含める場合は、サテライトではなくメインアセンブリとして`UltimateResourceFallback`場所を設定します (たとえば`[assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.MainAssembly)]`、)。

## <a name="localize-a-wpf-application"></a>WPF アプリケーションのローカライズ

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションをローカライズする場合、いくつかのオプションがあります。 たとえば、アプリケーション内のローカライズ可能なリソースを[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]ファイルにバインドしたり、ローカライズ可能なテキストを resx テーブルに格納したり、ローカライザーでファイルを使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]したりすることができます。 このセクションでは、XAML の BAML 形式を使用するローカライズワークフローについて説明します。これには、いくつかの利点があります。

- をビルドした後でローカライズできます。

- 開発時にローカライズできるように、以前のバージョンの XAML の baml 形式のローカライズを使用して、新しいバージョンの XAML 形式に更新できます。

- XAML の BAML 形式はコンパイルされた形式[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]であるため、コンパイル時に元のソース要素とセマンティクスを検証できます。

### <a name="localization-build-process"></a>ローカリゼーションビルドプロセス

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションを開発する場合、ローカリゼーションのビルドプロセスは次のようになります。

- 開発者は、アプリケーションを[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]作成して globalizes します。 開発者がアプリケーションをコンパイルする`<UICulture>en-US</UICulture>`ときに、言語に依存しないメインアセンブリが生成されるように、プロジェクトファイルでを設定します。 このアセンブリには、ローカライズ可能なすべてのリソースを含むサテライトファイルがあります。 必要に応じて、ローカライズ Api がメインアセンブリからの抽出をサポートしているため、ソース言語をメインアセンブリに保持できます。

- ファイルがビルドにコンパイルされると、は[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 、XAML の BAML 形式に変換されます。 カルチャに中立的`MyDialog.exe`なファイルとカルチャに依存する`MyDialog.resources.dll` (英語) ファイルは、英語圏の顧客にリリースされます。

### <a name="localization-workflow"></a>ローカライズワークフロー

ローカライズプロセスは、unlocalized `MyDialog.resources.dll`ファイルのビルド後に開始されます。 元[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Markup.Localizer>のの要素とプロパティは、の api を使用して、XAML の BAML 形式からキーと値のペアに抽出されます。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ローカライザーは、キーと値のペアを使用してアプリケーションをローカライズします。 ローカライズが完了したら、新しい値から新しい. resource .dll を生成することができます。

キーと値のペアのキーは、 `x:Uid`開発者によって元[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]のに配置される値です。 これら`x:Uid`の値により、API はローカリゼーション中に開発者とローカライザーの間で発生した変更を追跡およびマージできます。 たとえば、ローカライザーがローカライズを開始し[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]た後に、開発者がを変更した場合、開発の変更を既に完了したローカライズ作業にマージして、最小限の翻訳作業が失われるようにすることができます。

次の図は、XAML の BAML 形式に基づく一般的なローカライズワークフローを示しています。 この図は、開発者がアプリケーションを英語で書いていることを前提としています。 開発者は、WPF アプリケーションを作成して globalizes します。 開発者がを設定`<UICulture>en-US</UICulture>`するプロジェクトファイルで、言語に依存しないメインアセンブリが、ローカライズ可能なすべてのリソースを含むサテライトと共に生成されるようにします。 または、WPF のローカライズ Api がメインアセンブリからの抽出をサポートしているため、メインアセンブリにソース言語を保持することもできます。 ビルドプロセスの後、XAML は BAML にコンパイルされます。 カルチャに依存しない MyDialog .exe は、英語のお客様に送付されます。

![ローカライズワークフローを示す図。](./media/wpf-globalization-and-localization-overview/localization-workflow.png)

![Unlocalized ワークフローを示す図。](./media/wpf-globalization-and-localization-overview/unlocalized-workflow.png)

## <a name="examples-of-wpf-localization"></a>WPF のローカライズの例

このセクションには、アプリケーションをビルドおよびローカライズ[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]する方法を理解するのに役立つ、ローカライズされたアプリケーションの例が含まれています。

#### <a name="run-dialog-box-example"></a>[実行] ダイアログボックスの例

次の図は、 **[実行]** ダイアログボックスのサンプルの出力を示しています。

**英語：**

![英語版の [実行] ダイアログボックスを示すスクリーンショット。](./media/wpf-globalization-and-localization-overview/run-dialog-box-english.png)

**ドイツ語：**

![ドイツ語版の [実行] ダイアログボックスを示すスクリーンショット。](./media/wpf-globalization-and-localization-overview/run-dialog-box-german.png)

**[グローバル実行] ダイアログボックスのデザイン**

この例では、およびを使用[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]して[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、 **[実行]** ダイアログボックスを生成します。 このダイアログボックスは、[ [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]スタート] メニューから使用できる **[実行]** ダイアログボックスに相当します。

グローバルダイアログボックスを作成するためのいくつかの特徴を次に示します。

**自動レイアウト**

*Window1.xaml で、次のようにします。*

`<Window SizeToContent="WidthAndHeight">`

前のウィンドウプロパティは、コンテンツのサイズに応じてウィンドウのサイズを自動的に変更します。 このプロパティは、ローカライズ後にサイズが大きくなるコンテンツがウィンドウに表示されないようにします。また、ローカライズ後にコンテンツのサイズを小さくすると、不要な領域が削除されます。

`<Grid x:Uid="Grid_1">`

<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ローカライズ api が正しく機能するためには、プロパティが必要です。

これらは、の[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]開発とローカライズの間の変更を追跡するために[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]、ローカライズ api によって使用されます。 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>プロパティを使用すると、の新しいバージョン[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]との古いローカライズ[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]をマージできます。 コマンドシェルで<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>を実行`msbuild -t:updateuid RunDialog.csproj`して、プロパティを追加します。 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>プロパティを手動で追加すると、通常は時間がかかり、正確さが低下するため、この方法を使用することをお勧めします。 を実行<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> `msbuild -t:checkuid RunDialog.csproj`して、プロパティが正しく設定されていることを確認できます。

はコントロールを[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]使用して構造化されています。これは、の自動レイアウトを利用するための便利なコントロールです。[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Controls.Grid> ダイアログボックスは、3つの行と5つの列に分割されることに注意してください。 行と列の定義のいずれかが固定サイズではありません。そのため、 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]各セルに配置されている要素は、ローカリゼーション時のサイズの増減に合わせて調整できます。

[!code-xaml[GlobalizationRunDialog#GridColumnDef](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationRunDialog/CS/Window1.xaml#gridcolumndef)]

**Open:** label と<xref:System.Windows.Controls.ComboBox>が配置されている最初の2つの列は[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 、合計幅の 10% を使用します。

[!code-xaml[GlobalizationRunDialog#GridColumnDef2](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationRunDialog/CS/Window1.xaml#gridcolumndef2)]

この例では、の<xref:System.Windows.Controls.Grid>共有サイズ設定機能を使用することに注意してください。 最後の3つの列は、同じ<xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A>に配置することによってこれを利用します。 これにより、プロパティの名前と同じように、列が同じサイズを共有できるようになります。 "Browse..."長い文字列 "Durchsuchen..." にローカライズされているので、すべてのボタンの幅が大きくなります。小さい "OK" ボタンと、大規模な "Durchsuchen..." を指定する必要はありません。;.

**xml:lang**

`xml:lang="en-US"`

[XAML での xml: lang の処理](../../xaml-services/xml-lang-handling-in-xaml.md)が、 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]のルート要素に配置されていることに注意してください。 このプロパティは、指定された要素とその子のカルチャを記述します。 この値は、のいくつかの[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]機能で使用されており、ローカリゼーション時に適切に変更する必要があります。 この値によって、ハイフネーションおよびスペルチェックの単語に使用する言語辞書が変更されます。 また、数字の表示や、フォントフォールバックシステムが使用するフォントを選択する方法にも影響します。 最後に、プロパティは数値の表示方法に影響を及ぼし、複雑なスクリプトで記述されたテキストの整形方法に影響します。 既定値は "en-us" です。

**サテライトリソースアセンブリのビルド**

*.Csproj:*

ファイルを編集し、次のタグを無条件`<PropertyGroup>`に追加します。 `.csproj`

`<UICulture>en-US</UICulture>`

`UICulture`値が追加されていることに注目してください。 これが en-us などの有効な<xref:System.Globalization.CultureInfo>値に設定されている場合、プロジェクトをビルドすると、ローカライズ可能なすべてのリソースを含むサテライトアセンブリが生成されます。

`<Resource Include="RunIcon.JPG">`

`<Localizable>False</Localizable>`

`</Resource>`

は`RunIcon.JPG` 、すべてのカルチャで同じように表示される必要があるため、ローカライズする必要はありません。 `Localizable`は、サテライト`false`アセンブリではなく、言語に依存しないメインアセンブリに保持されるようにに設定されています。 コンパイルされていないすべてのリソース`Localizable`の既定`true`値は、に設定されます。

**[実行] ダイアログのローカライズ**

**Parse**

アプリケーションをビルドした後、ローカライズするための最初の手順として、ローカライズ可能なリソースをサテライトアセンブリから解析します。 このトピックでは、 [Locbaml ツールサンプル](https://go.microsoft.com/fwlink/?LinkID=160016)にある locbaml ツールのサンプルを使用します。 LocBaml は、ローカライズプロセスに適したローカリゼーションツールの構築を開始するのに役立つサンプルツールでのみあることに注意してください。 LocBaml を使用して、次のように実行して解析します。**LocBaml/Parse RunDialog. .resources/out:** "rundialog. .resources. .RESOURCES. .csv" ファイルを生成します。

**地域**

Unicode をサポートしているお気に入りの CSV エディターを使用して、このファイルを編集します。 ローカライズカテゴリが "なし" のすべてのエントリを除外します。 次のエントリが表示されます。

|リソースキー|ローカライズのカテゴリ|[値]|
|-|-|-|
|Button_1: $Content を実行します。|ボタン|OK|
|Button_2: $Content を実行します。|ボタン|キャンセル|
|Button_3:System.Windows.Controls.Button.$Content|ボタン|参照...|
|ComboBox_1:System.Windows.Controls.ComboBox.$Content|ComboBox||
|TextBlock_1: $Content を実行します。|テキスト|プログラム、フォルダー、ドキュメント、またはインターネットリソースの名前を入力すると、Windows によってファイルが開きます。|
|TextBlock_2: $Content を実行します。|テキスト|開き|
|Window_1:System.Windows.Window.Title|Title|実行|

アプリケーションをドイツ語にローカライズするには、次の変換が必要です。

|リソースキー|ローカライズのカテゴリ|[値]|
|-|-|-|
|Button_1: $Content を実行します。|ボタン|OK|
|Button_2: $Content を実行します。|ボタン|Abbrechen|
|Button_3:System.Windows.Controls.Button.$Content|ボタン|Durchsuchen...|
|ComboBox_1:System.Windows.Controls.ComboBox.$Content|ComboBox||
|TextBlock_1: $Content を実行します。|テキスト|Geben Sie den namen eines programms、Ordners、Dokuments 順番 einer internetresource an。|
|TextBlock_2: $Content を実行します。|テキスト|Öffnen:|
|Window_1:System.Windows.Window.Title|Title|実行|

**生み**

ローカリゼーションの最後の手順では、新たにローカライズされたサテライトアセンブリを作成します。 これは、次の LocBaml コマンドを使用して実現できます。

**LocBaml/generate RunDialog. .resources. .resources:... .resources. .resources. .CSV:./cul: デデュープ**

ドイツ語のウィンドウでは、このリソース .dll がメインアセンブリの横にある de 以外のフォルダーに配置されている場合、このリソースは en-us フォルダーにあるものではなく、自動的に読み込まれます。 これをテストするためにドイツ語版の windows がインストールされていない場合は、使用している windows の任意の`en-US`カルチャ (たとえば、) にカルチャを設定し、元のリソース DLL を置き換えます。

**サテライトリソースの読み込み**

|MyDialog.exe|en-US\MyDialog.resources.dll|de-DE\MyDialog.resources.dll|
|------------------|------------------------------------|------------------------------------|
|コード|元の英語の BAML|ローカライズされた BAML|
|カルチャに依存しないリソース|英語のその他のリソース|ドイツ語にローカライズされたその他のリソース|

.NET framework は、アプリケーションの`Thread.CurrentThread.CurrentUICulture`に基づいて、どのサテライトリソースアセンブリを読み込むかを自動的に選択します。 これは、既定では、Windows OS のカルチャになります。 そのため、ドイツ語版の Windows を使用している場合は、de-DE\MyDialog.resources.dll が読み込まれます。英語版の Windows を使用している場合は、en-US\MyDialog.resources.dll が読み込まれます。 プロジェクトの AssemblyInfo. * で NeutralResourcesLanguage を指定することにより、アプリケーションの最終的なフォールバックリソースを設定できます。 たとえば、次のように指定します。

`[assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]`

de-DE\MyDialog.resources.dll または de\MyDialog.resources.dll が両方とも使用できない場合、en-US\MyDialog.resources.dll はドイツ語のウィンドウで使用されます。

### <a name="microsoft-saudi-arabia-homepage"></a>Microsoft サウジアラビアホームページ

次の図は、英語とアラビアのホームページを示しています。 これらのグラフィックスを生成する完全なサンプルについては、「[グローバリゼーションのホームページのサンプル](https://go.microsoft.com/fwlink/?LinkID=159990)」を参照してください。

**英語：**

![英語のホームページを示すスクリーンショット。](./media/wpf-globalization-and-localization-overview/english-home-page-sample.jpg)

**アラビア語：**

![アラビアのホームページを示すスクリーンショット。](./media/wpf-globalization-and-localization-overview/arabic-home-page-sample.jpg)

### <a name="designing-a-global-microsoft-home-page"></a>グローバルな Microsoft ホームページを設計する

Microsoft サウジアラビア web サイトのこのモックアップでは、RightToLeft 言語用に提供されているグローバリゼーション機能について説明しています。 ヘブライ語やアラビア語などの言語では、右から左への読み取り順序が[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]使用されます。そのため、のレイアウトは、英語などの左から右に記述する言語とはまったく異なるレイアウトになることがよくあります。 左から右に記述する言語から右から左の言語へのローカライズや、その逆の変換は、非常に困難な場合があります。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は、このようなローカライズをはるかに簡単にするように設計されています。

**FlowDirection**

*ホームページ:*

[!code-xaml[GlobalizationHomepage#Homepage](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#homepage)]

<xref:System.Windows.FrameworkElement.FlowDirection%2A> の<xref:System.Windows.Controls.Page>プロパティに注目してください。 このプロパティをに<xref:System.Windows.FlowDirection.RightToLeft>変更する<xref:System.Windows.Controls.Page>と<xref:System.Windows.FrameworkElement.FlowDirection%2A> 、とその[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]子要素のが変更され、アラビア語のユーザーが期待するとおりに右から左に移動するようになります。 任意の要素に明示的<xref:System.Windows.FrameworkElement.FlowDirection%2A>なを指定することで、継承の動作をオーバーライドできます。 プロパティは、 <xref:System.Windows.FrameworkElement>またはドキュメント関連の要素で使用でき、の<xref:System.Windows.FlowDirection.LeftToRight>暗黙的な値を持ちます。 <xref:System.Windows.FrameworkElement.FlowDirection%2A>

ルート<xref:System.Windows.FrameworkElement.FlowDirection%2A>が変更されたときに、背景のグラデーションブラシが正しく反転されていることを確認します。

**FlowDirection="LeftToRight"**

![グラデーションフローを左から右に示すスクリーンショット。](./media/wpf-globalization-and-localization-overview/gradient-flow-left-right.png)

**FlowDirection="RightToLeft"**

![右から左へのグラデーションフローを示すスクリーンショット。](./media/wpf-globalization-and-localization-overview/gradient-flow-right-left.png)

**パネルとコントロールに固定ディメンションを使用しない**

ホームページを見てみましょう。上部[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] <xref:System.Windows.Controls.DockPanel>の全体に対して指定されている固定幅と高さ以外に、他の固定ディメンションはありません。 ソーステキストより長い可能性のあるローカライズされたテキストをクリップしないように、固定ディメンションを使用しないようにします。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]パネルとコントロールは、含まれているコンテンツに基づいて自動的にサイズが変更されます。 ほとんどのコントロールには、より詳細な制御を設定できる最小値と最大値もあります (たとえば、MinWidth = "20")。 で<xref:System.Windows.Controls.Grid>は、\* '`Width="0.25*"`' (たとえば) を使用して相対幅と高さを設定したり、セルサイズの共有機能を使用したりすることもできます。

**ローカリゼーションコメント**

コンテンツがあいまいになり、翻訳が困難な場合があります。 開発者またはデザイナーは、ローカライズコメントを使用してローカライザーに追加のコンテキストとコメントを提供できます。 たとえば、次のようなローカライズは、文字 '&#124;' の使用法を明確にします。

[!code-xaml[GlobalizationHomepage#LocalizationComment](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#localizationcomment)]

このコメントは TextBlock_1's コンテンツに関連付けられ、LocBaml ツール (「[アプリケーションのローカライズ](how-to-localize-an-application.md)」を参照) の場合は、出力 .csv ファイルの TextBlock_1 行の6番目の列に表示されます。

|リソースキー|Category|できる|修正|コメント|[値]|
|-|-|-|-|-|-|
|TextBlock_1: $Content を実行します。|テキスト|true|true|この文字は、装飾規則として使用されます。|&#124;|

コメントは、次の構文を使用して、任意の要素のコンテンツまたはプロパティに配置できます。

[!code-xaml[GlobalizationHomepage#LocalizationCommentsProp](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#localizationcommentsprop)]

**ローカリゼーション属性**

多くの場合、開発者またはローカライズマネージャーは、ローカライザーの読み取りと変更を制御する必要があります。 たとえば、ローカライザーが会社の名前や法律上の表現を翻訳したくない場合があります。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]要素のコンテンツまたはプロパティの読みやすさ、変更可能性、およびカテゴリを設定するための属性を提供します。この属性は、ローカリゼーションツールで要素のロック、非表示、または並べ替えに使用できます。 詳細については、「 <xref:System.Windows.Localization.Attributes%2A> 」を参照してください。 このサンプルでは、LocBaml ツールはこれらの属性の値のみを出力します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールにはこれらの属性の既定値がありますが、ではこれらの属性をオーバーライドできます。 たとえば、次の例では、の`TextBlock_1`既定のローカリゼーション属性をオーバーライドし、コンテンツを読み取り可能に設定しますが、ローカライザーでは変更できないように設定します。

[!code-xaml[LocalizationComAtt#LocalizationAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationComAtt/CSharp/Attributes.xaml#localizationattributes)]

読みやすさと変更可能性属性に加えて、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]には共通の UI カテゴリ (<xref:System.Windows.LocalizationCategory>) の列挙型が用意されています。これを使用すると、ローカライザーにより多くのコンテキストを与えることができます。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]は、プラットフォームコントロールの既定のカテゴリもオーバーライドできます。

[!code-xaml[LocalizationComAtt#LocalizationAttributesOverridden](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationComAtt/CSharp/Attributes.xaml#localizationattributesoverridden)]

によって提供さ[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]れる既定のローカリゼーション属性は、コードを使用してオーバーライドすることもできます。これにより、カスタムコントロールに適切な既定値を正しく設定できます。 例:

```csharp
[Localizability(Readability = Readability.Readable, Modifiability=Modifiability.Unmodifiable, LocalizationCategory.None)]
public class CorporateLogo : TextBlock
{
    // ...
}
```

で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]設定されたインスタンスごとの属性は、カスタムコントロールのコードで設定した値よりも優先されます。 属性とコメントの詳細については、「[ローカリゼーション属性とコメント](localization-attributes-and-comments.md)」を参照してください。

**フォントフォールバックと複合フォント**

特定のコードポイントの範囲をサポートしていないフォントを[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]指定した場合、は、Windows\Fonts ディレクトリにある compositefont グローバルユーザーインターフェイスを使用して実行されるものに自動的にフォールバックします。 複合フォントは他のフォントと同様に動作し、要素の`FontFamily`を設定することによって明示的に使用することができます (たとえば、 `FontFamily="Global User Interface"`)。 独自の複合フォントを作成し、特定のコードポイントの範囲と言語に使用するフォントを指定することで、独自のフォントフォールバック設定を指定できます。

複合フォントの詳細について<xref:System.Windows.Media.FontFamily>は、「」を参照してください。

**Microsoft ホームページのローカライズ**

このアプリケーションをローカライズするには、[実行] ダイアログの例と同じ手順に従います。 アラビア語用のローカライズされた .csv ファイルは、[グローバリゼーションホームページのサンプル](https://go.microsoft.com/fwlink/?LinkID=159990)でご利用いただけます。
