---
title: WPF のグローバリゼーションおよびローカリゼーションの概要
ms.date: 03/30/2017
helpviewer_keywords:
- globalization [WPF], about globalization
- localization [WPF], about localization
ms.assetid: 56e5a5c8-6c96-4d19-b8e1-a5be1dc564af
ms.openlocfilehash: ce54c3299d599e990fa02abd3cea1460d588e280
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662252"
---
# <a name="wpf-globalization-and-localization-overview"></a>WPF のグローバリゼーションおよびローカリゼーションの概要

1 つだけの言語、製品の可用性を制限する場合は、潜在的な顧客ベースでの世界 6.5 10億人の母集団の割合を制限します。 世界中のユーザーに到達するようにアプリケーションを実行する場合に、製品のコスト効率に優れたローカリゼーションより多くのお客様に最高で最も経済的な方法のいずれか。  
  
 この概要紹介のグローバリゼーションおよびローカリゼーション[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]します。 グローバリゼーションとは、設計と複数の場所で実行するアプリケーションの開発です。 たとえば、グローバリゼーション ローカライズされたユーザー インターフェイスとサポート リージョンのデータの異なるカルチャ内のユーザーの。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] グローバル化されたデザイン機能、自動レイアウト、サテライト アセンブリ、およびローカライズされた属性を含む、コメントを提供します。
  
 ローカリゼーションとは、アプリケーションがサポートする特定のカルチャのローカライズ バージョンへのアプリケーション リソースを変換します。 ローカライズするときに[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]で Api を使用する、<xref:System.Windows.Markup.Localizer>名前空間。 これらの Api の電源、 [LocBaml ツール サンプル](https://go.microsoft.com/fwlink/?LinkID=160016)コマンド ライン ツール。 ビルドして、LocBaml を使用する方法については、次を参照してください。[アプリケーションをローカライズする](how-to-localize-an-application.md)します。
  
## <a name="best-practices-for-globalization-and-localization-in-wpf"></a>WPF のグローバリゼーションおよびローカリゼーションのためのベスト プラクティス

 組み込まれているグローバリゼーションおよびローカリゼーションの機能を最大限に活用できる[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]に従って、UI の設計とこのセクションではローカライズに関するヒント。  
  
### <a name="best-practices-for-wpf-ui-design"></a>WPF の UI デザインのベスト プラクティス

 デザインするとき、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– ベース[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]、これらのベスト プラクティスの実装を検討します。  
  
- 書き込み、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; を作成しないように[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]コード。 作成するときに、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]を使用して[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、組み込まれているローカリゼーション Api を介して公開します。  
  
- コンテンツのレイアウト時に絶対位置および固定サイズを使用しないでください。代わりに、相対パスまたは自動サイズ設定を使用します。
  
    - 使用<xref:System.Windows.Window.SizeToContent%2A>幅と高さの設定を保持および`Auto`します。  
  
    - 使用しないでください<xref:System.Windows.Controls.Canvas>をレイアウトする[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]秒。  
  
    - 使用<xref:System.Windows.Controls.Grid>とそのサイズの共有機能。  
  
- ローカライズされたテキストは多くの場合より多くの領域を必要とするために、余白に余分なスペースを提供します。 突出の文字には、余分なスペースができます。  
  
- 有効にする<xref:System.Windows.Controls.TextBlock.TextWrapping%2A>で<xref:System.Windows.Controls.TextBlock>クリッピングを回避するためにします。
  
- `xml:lang` 属性を設定します。 この属性には、特定の要素とその子要素のカルチャがについて説明します。 このプロパティの値がいくつかの機能の動作を変更[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]します。 たとえば、ハイフネーション、スペル チェック、数値の置換、複雑なスクリプトの整形、およびフォント フォールバックの動作を変更します。 参照してください[WPF のグローバリゼーション](globalization-for-wpf.md)詳細設定については、 [xml:lang XAML 処理](../../xaml-services/xml-lang-handling-in-xaml.md)します。  
  
- さまざまな言語に使用されるフォントをより適切に制御を取得する場合は、カスタマイズされた複合フォントを作成します。 既定では、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Windows\Fonts ディレクトリに GlobalUserInterface.composite フォントを使用します。  
  
- ローカライズがナビゲーション アプリケーションを作成するときに右から左の形式でテキストを表示するカルチャで、明示的に設定、<xref:System.Windows.FlowDirection>ページが継承しないことを確認するには、各ページの<xref:System.Windows.FlowDirection>から、<xref:System.Windows.Navigation.NavigationWindow>します。  
  
- ブラウザー外でホストされているスタンドアロン ナビゲーション アプリケーションを作成するときに設定、<xref:System.Windows.Application.StartupUri%2A>初期アプリケーションに、<xref:System.Windows.Navigation.NavigationWindow>の代わりにページに (たとえば、 `<Application StartupUri="NavigationWindow.xaml">`)。 この設計では、変更することができます、<xref:System.Windows.FlowDirection>ウィンドウとナビゲーション バー。 詳細と例では、次を参照してください。[グローバリゼーション ホームページ サンプル](https://go.microsoft.com/fwlink/?LinkID=159990)します。  
  
### <a name="best-practices-for-wpf-localization"></a>WPF のローカリゼーションのためのベスト プラクティス

 ローカライズする[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]– ベースのアプリケーションは、これらのベスト プラクティスの実装を検討してください。  
  
- ローカリゼーション コメントを使用して、ローカライザーに余分なコンテキストを提供します。  
  
- ローカリゼーション属性を使用して、選択的に省略することではなくローカライズを制御する<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>要素のプロパティ。 参照してください[ローカリゼーション属性とコメント](localization-attributes-and-comments.md)詳細についてはします。  
  
- 使用`msbuild -t:updateuid`と`-t:checkuid`を追加して確認<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>プロパティで、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]します。 使用<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>開発およびローカリゼーションの間の変更を追跡するプロパティ。 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> プロパティを使用して、新しい開発上の変更をローカライズするのに役立ちます。 手動で追加する場合<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>プロパティを[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]タスクが通常面倒で正確性が低下します。  
  
    - 編集または変更しないで<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>ローカライズを開始した後のプロパティ。  
  
    - 重複データを使用しないでください<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>プロパティ (コピーと貼り付けコマンドを使用する場合は、このヒントを思い出してください)。  
  
    - 設定、`UltimateResourceFallback`を適切なフォールバック言語を指定する AssemblyInfo.* 内の場所 (たとえば、 `[assembly: NeutralResourcesLanguage("en-US",   UltimateResourceFallbackLocation.Satellite)]`)。  
  
         省略すると、メイン アセンブリに、ソース言語を含める場合、`<UICulture>`プロジェクト ファイルにタグを付ける、設定、`UltimateResourceFallback`サテライトではなくメイン アセンブリと場所 (たとえば、 `[assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.MainAssembly)]`)。  
  
## <a name="localize-a-wpf-application"></a>WPF アプリケーションをローカライズします。

ローカライズするときに、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションでは、いくつかのオプションがあります。 アプリケーションのローカライズ可能なリソースをバインドするなど、[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]ファイル、resx テーブルでローカライズ可能なテキストを格納または使用して、ローカライザー[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ファイル。 このセクションでは、いくつかの利点を提供する、XAML の BAML 形式を使用するローカリゼーション ワークフローについて説明します。  
  
- ビルドした後はローカライズできます。  
  
- 同時に開発するローカライズできるようにの XAML の BAML 形式は、以前のバージョンから、ローカライズ版では、XAML の BAML 形式の新しいバージョンに更新できます。  
  
- 検証する元のソース要素とセマンティクス コンパイル時に XAML の BAML 形式は、コンパイル済みの形式のため、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]します。  
  
### <a name="localization-build-process"></a>ローカリゼーションのビルド プロセス  

開発する際に、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーション、ローカライズのビルド プロセスは次のようにします。  
  
- 開発者を作成し、グローバル化、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーション。 プロジェクト ファイル開発者セット`<UICulture>en-US</UICulture>`言語中立のメイン アセンブリを生成できるように、アプリケーションがコンパイルされたとき。 このアセンブリのサテライト。 ローカライズ可能なすべてのリソースを含む.resources.dll ファイル。 必要に応じて、ソース言語に保存、メイン アセンブリのためローカリゼーション[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]メイン アセンブリからの抽出をサポートします。  
  
- ファイルは、ビルドにコンパイルされるときに、 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] XAML の BAML 形式に変換されます。 カルチャ的にニュートラル`MyDialog.exe`とカルチャに依存 (英語)`MyDialog.resources.dll`ファイルは、英語圏の顧客にリリースします。  
  
### <a name="localization-workflow"></a>ローカリゼーション ワークフロー

ローカライズ プロセスを開始した後、ローカライズされていない`MyDialog.resources.dll`ファイルをビルドします。 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]要素と、元のプロパティ[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を使用して、キーと値のペアに XAML の BAML 形式から抽出された、 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] <xref:System.Windows.Markup.Localizer>します。 ローカライザーは、キー/値ペアを使用して、アプリケーションをローカライズします。 新しいを生成することができます。 ローカライズが完了したら、新しい値から resource.dll します。
  
 キー/値ペアのキーは、`x:Uid`開発者が、元に配置されている値[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]します。 これら`x:Uid`値が有効にする、[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]を追跡し、ローカライズ中に、開発者と、ローカライザー間に行われる変更をマージします。 たとえば、開発者が変更された場合、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]ローカライザーは、ローカライズを開始した後の最小限の翻訳作業が失われたようにローカライズを既に完了した作業と開発の変更をマージできます。  
  
 次の図は、XAML の BAML 形式に基づいているローカリゼーションの一般的なワークフローを示します。 この図では、開発者は、英語でアプリケーションを記述を前提としています。 開発者は、作成し、WPF アプリケーションのグローバライズします。 プロジェクトの開発者のセットをファイル`<UICulture>en-US</UICulture>`ビルド時に、言語に中立的なメイン アセンブリはサテライトで生成されるようにします。 ローカライズ可能なすべてのリソースを含む resources.dll。 代わりに、WPF のローカリゼーション Api は、メイン アセンブリからの抽出をサポートするため、メイン アセンブリにソース言語に残すいずれかでした。 ビルド プロセスの後、XAML BAML にコンパイルされます。 カルチャ的にニュートラル MyDialog.exe.resources.dll 英語圏の顧客に送付されます。  
  
 ![ローカリゼーション ワークフローを示す図。](./media/wpf-globalization-and-localization-overview/localization-workflow.png)  
  
 ![ローカライズされていないワークフローを示す図。](./media/wpf-globalization-and-localization-overview/unlocalized-workflow.png)  
  
## <a name="examples-of-wpf-localization"></a>WPF のローカリゼーションの例

 このセクションには、ローカライズされたアプリケーションをビルドおよびローカライズする方法を理解するための例が含まれています。[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーション。  
  
#### <a name="run-dialog-box-example"></a>ダイアログ ボックスの例を実行します。

 次の図の出力を表示する、**実行**ダイアログ ボックスのサンプルです。  
  
 **英語：**  
  
 ![[英語での実行] ダイアログ ボックスを示すスクリーン ショット。](./media/wpf-globalization-and-localization-overview/run-dialog-box-english.png)  
  
 **ドイツ語：**  
  
 ![ドイツ語の実行 ダイアログ ボックスを表示するスクリーン ショット。](./media/wpf-globalization-and-localization-overview/run-dialog-box-german.png)  
  
 **グローバルの実行 ダイアログ ボックスのデザイン**  
  
 この例で生成する**実行** ダイアログ ボックスを使用して[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]と[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]します。 このダイアログ ボックスは、**実行** ダイアログ ボックスから使用できる、 [!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] [スタート] メニュー。  
  
 グローバルなダイアログ ボックスを行うためのいくつかの要点は次のとおりです。  
  
 **自動レイアウト**  
  
 *で Window1.xaml:*  
  
 `<Window SizeToContent="WidthAndHeight">`  
  
 前のウィンドウのプロパティには、コンテンツのサイズに従ってウィンドウが自動的にサイズ変更します。 このプロパティは、ローカリゼーション後にサイズが大きくなるコンテンツ、ウィンドウを防止します。コンテンツ ローカライズ後のサイズが減少したら、不要なスペースも削除されます。  
  
 `<Grid x:Uid="Grid_1">`  
  
 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> プロパティは、のために必要な[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ローカリゼーション[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]正常に動作します。  
  
 使用されている[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ローカリゼーション[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]開発およびローカリゼーションの間の変更を追跡するために、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]します。 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A> プロパティを使用すると、新しいバージョンのマージ、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]のローカライズを古い、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]します。 追加する、<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>プロパティを使用して`msbuild -t:updateuid RunDialog.csproj`コマンド シェルでします。 これは、追加の推奨される方法<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>プロパティそれらを手動で追加するには通常は時間がかかると正確さに欠けるためです。 確認できます<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>プロパティを実行して正しく設定`msbuild -t:checkuid RunDialog.csproj`します。
  
 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]を使用して構造化、<xref:System.Windows.Controls.Grid>自動レイアウトの活用の便利なコントロールであるコントロールで[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]します。 ダイアログ ボックスは次の 3 つの行と 5 つの列に分割されていることに注意してください。 行と列の定義のない 1 つが、固定サイズです。そのため、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]各セルに配置された要素が増加に合わせて調整でき、ローカライズ中にサイズが減少します。  
  
 [!code-xaml[GlobalizationRunDialog#GridColumnDef](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationRunDialog/CS/Window1.xaml#gridcolumndef)]  
  
 最初の 2 つの列で、**オープン:** ラベルと<xref:System.Windows.Controls.ComboBox>に配置されますの 10% を使用して、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]幅の合計します。  
  
 [!code-xaml[GlobalizationRunDialog#GridColumnDef2](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationRunDialog/CS/Window1.xaml#gridcolumndef2)]  
  
 メモの共有のサイズ変更機能を使用する例では、<xref:System.Windows.Controls.Grid>します。 最後の 3 つの列が同じ自体を配置することでこの方法の利点を実行<xref:System.Windows.Controls.DefinitionBase.SharedSizeGroup%2A>します。 プロパティの名前の 1 つと同様に、これにより、同じサイズを共有する列。 これより長い文字列「Durchsuchen…」に「参照…」ローカライズされたとき、すべてのボタンは、小さい"OK"ボタンと過度に大規模な「Durchsuchen...」ボタンではなく幅拡張します。  
  
 **xml:lang**
  
 `xml:lang="en-US"`  
  
 通知、 [xml:lang XAML 処理](../../xaml-services/xml-lang-handling-in-xaml.md)のルート要素に配置、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]します。 このプロパティには、指定された要素とその子のカルチャがについて説明します。 この値は、いくつかの機能によって使用されます[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ローカライズ中に適切に変更する必要があります。 この値は、どのような言語の辞書が使用して単語を区切るし、スペル チェックを変更します。 また、数字、およびフォント フォールバック システムが使用するフォントを選択する方法の表示も影響します。 最後に、方法の数字を表示するプロパティの影響と複雑なスクリプトで記述された、方法テキストを整形します。 既定値は、"EN-US"です。  
  
 **サテライト リソース アセンブリの構築**  
  
 *In .csproj:*  

 編集、`.csproj`ファイルを開き、次のタグを追加するには無条件に`<PropertyGroup>`:
 
 `<UICulture>en-US</UICulture>`  
  
 追加に注意してください、`UICulture`値。 設定を有効な<xref:System.Globalization.CultureInfo>EN-US、プロジェクトのビルドなどの値がローカライズ可能なすべてのリソースのサテライト アセンブリを生成します。  
  
 `<Resource Include="RunIcon.JPG">`  
  
 `<Localizable>False</Localizable>`  
  
 `</Resource>`  
  
 `RunIcon.JPG`のすべてのカルチャで同じで表示されるため、ローカライズする必要はありません。 `Localizable` 設定されている`false`サテライト アセンブリではなく言語中立的なメイン アセンブリに残るようにします。 Noncompilable のすべてのリソースの既定値は`Localizable`設定`true`します。  
  
 **ローカライズの実行 ダイアログ**  
  
 **Parse**  
  
 これをローカライズする最初の手順のアプリケーションをビルドした後はサテライト アセンブリからのローカライズ可能なリソースが解析しています。 このトピックの目的にあるサンプル LocBaml ツールを使用して、 [LocBaml ツール サンプル](https://go.microsoft.com/fwlink/?LinkID=160016)します。 LocBaml は、ローカライズ プロセスに合ったローカライズ ツールの構築を開始するため、サンプル ツールだけであることに注意してください。 LocBaml を使用して、解析するには、次を実行します。**LocBaml/RunDialog.resources.dll を解析/アウト:** "RunDialog.resources.dll.CSV"ファイルを生成します。  
  
 **ローカライズします。**  
  
 このファイルを編集する Unicode をサポートする任意の CSV エディターを使用します。 ローカライズのカテゴリが"None"のすべてのエントリを除外します。 次のエントリが表示されます。  
  
|リソース キー|ローカライズのカテゴリ|[値]|  
|-|-|-| 
|Button_1:System.Windows.Controls.Button.$Content|ボタン|OK|  
|Button_2:System.Windows.Controls.Button.$Content|ボタン|キャンセル|  
|Button_3:System.Windows.Controls.Button.$Content|ボタン|参照...|  
|ComboBox_1:System.Windows.Controls.ComboBox.$Content|ComboBox||  
|TextBlock_1:System.Windows.Controls.TextBlock.$Content|テキスト|プログラム、フォルダー、ドキュメント、またはインターネット リソースの名前を入力して、Windows がそれを開きます。|  
|TextBlock_2:System.Windows.Controls.TextBlock.$Content|テキスト|開いています。|  
|Window_1:System.Windows.Window.Title|Title|実行|  
  
 ドイツ語にアプリケーションをローカライズするにを実行すると次の変換が必要です。  
  
|リソース キー|ローカライズのカテゴリ|[値]|  
|-|-|-| 
|Button_1:System.Windows.Controls.Button.$Content|ボタン|OK|  
|Button_2:System.Windows.Controls.Button.$Content|ボタン|Abbrechen|  
|Button_3:System.Windows.Controls.Button.$Content|ボタン|Durchsuchen.|  
|ComboBox_1:System.Windows.Controls.ComboBox.$Content|ComboBox||  
|TextBlock_1:System.Windows.Controls.TextBlock.$Content|テキスト|Geben Sie den Namen eines Programms Ordners、Dokuments 並べ替えた einer Internetresource、します。|  
|TextBlock_2:System.Windows.Controls.TextBlock.$Content|テキスト|Öffnen:|  
|Window_1:System.Windows.Window.Title|Title|実行|  
  
 **生成します。**  
  
 ローカライズの最後の手順では、新しくローカライズされたサテライト アセンブリを作成する必要があります。 LocBaml の次のコマンドでは、これを実行できます。  
  
 **LocBaml.exe/生成 RunDialog.resources.dll/trans:RunDialog.resources.dll.CSV/out: です。/cul:de-DE**  
  
 ドイツ語で[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]、このリソースが EN-US フォルダー内ではなく自動的に負荷をこの resources.dll をメイン アセンブリの横にある DE-DE フォルダーに配置すると、場合。 ドイツ語版があるない場合[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]これをテストするには、どのカルチャのカルチャを設定[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]を使用する (たとえば、 `en-US`)、元のリソース DLL を置き換えるとします。  
  
 **サテライト リソースの読み込み**  
  
|MyDialog.exe|en-US\MyDialog.resources.dll|de-DE\MyDialog.resources.dll|  
|------------------|------------------------------------|------------------------------------|  
|コード|元の英語 BAML|ローカライズされた BAML|  
|カルチャ ニュートラル リソース|英語での他のリソース|ドイツ語にローカライズされたその他のリソース|  
  
 .NET framework はサテライト リソース アセンブリを読み込むアプリケーションのに基づいて自動的に選択`Thread.CurrentThread.CurrentUICulture`します。 既定値は、カルチャの[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]OS。 ドイツ語を使用している場合は、その[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]、英語を使用している場合、de-DE\MyDialog.resources.dll が読み込まれる[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]、en-US\MyDialog.resources.dll を読み込みます。 プロジェクトの AssemblyInfo.*、NeutralResourcesLanguage を指定することで、アプリケーションの最終的なフォールバック リソースを設定できます。 指定した場合の例。  
  
 `[assembly: NeutralResourcesLanguage("en-US", UltimateResourceFallbackLocation.Satellite)]`  
  
 de-DE\MyDialog.resources.dll または de\MyDialog.resources.dll はどちらも使用できない場合に、en-US\MyDialog.resources.dll ドイツ語の Windows で使用されます。  
  
### <a name="microsoft-saudi-arabia-homepage"></a>Microsoft サウジアラビア ホーム ページ  
 次の図は、英語とアラビア語のホーム ページを表示します。 これらのグラフィックスを生成する完全なサンプルを参照してください。[グローバリゼーション ホームページ サンプル](https://go.microsoft.com/fwlink/?LinkID=159990)します。  
  
 **英語：**  
  
 ![英語版のホーム ページを示すスクリーン ショット。](./media/wpf-globalization-and-localization-overview/english-home-page-sample.jpg)  
  
 **アラビア語：**  
  
 ![アラビア語のホーム ページを示すスクリーン ショット。](./media/wpf-globalization-and-localization-overview/arabic-home-page-sample.jpg)  
  
### <a name="designing-a-global-microsoft-home-page"></a>グローバル Microsoft ホーム ページのデザイン  
 モックの Microsoft サウジアラビア web サイトは RightToLeft 言語に提供されるグローバリゼーション機能を示しています。 ヘブライ語やアラビア語などの言語がそのため、右から左への読み取り順序をあるレイアウトの[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]する必要がありますレイアウトする多くの場合、英語などの左から右の言語の場合よりも大きく異なります。 右から左の言語またはその逆に、左から右言語からのローカライズは非常に困難なことができます。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] このようなローカライズを簡単に設計されています。  
  
 **FlowDirection**  
  
 *Homepage.xaml:*  
  
 [!code-xaml[GlobalizationHomepage#Homepage](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#homepage)]  
  
 通知、<xref:System.Windows.FrameworkElement.FlowDirection%2A>プロパティ<xref:System.Windows.Controls.Page>します。 このプロパティを変更する<xref:System.Windows.FlowDirection.RightToLeft>が変更されます、<xref:System.Windows.FrameworkElement.FlowDirection%2A>の<xref:System.Windows.Controls.Page>とその子要素ようにこのレイアウト[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]アラビア語のユーザーの予想どおり右から左に反転します。 明示的な指定することで継承の動作をオーバーライドできる 1 つ<xref:System.Windows.FrameworkElement.FlowDirection%2A>任意の要素。 <xref:System.Windows.FrameworkElement.FlowDirection%2A>プロパティがいずれかで利用<xref:System.Windows.FrameworkElement>または関連する要素をドキュメントし、の暗黙の型の値を持つ<xref:System.Windows.FlowDirection.LeftToRight>します。  
  
 背景のグラデーション ブラシでもに反転するときに正しくことを確認します。 ルート<xref:System.Windows.FrameworkElement.FlowDirection%2A>が変更されました。  
  
 **FlowDirection="LeftToRight"**  
  
 ![左から右へのグラデーションのフローを示すスクリーン ショット。](./media/wpf-globalization-and-localization-overview/gradient-flow-left-right.png)  
  
 **FlowDirection="RightToLeft"**  
  
 ![右から左へのグラデーションのフローを示すスクリーン ショット。](./media/wpf-globalization-and-localization-overview/gradient-flow-right-left.png)  
  
 **パネルとコントロールの固定サイズを使用しないでください。**  
  
 Homepage.xaml を通してくださいとは別に固定幅と高さが全体で指定されていることを確認[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]上にある<xref:System.Windows.Controls.DockPanel>、他の固定サイズではありません。 ソース テキストを超える可能性のあるローカライズされたテキストをクリッピングを防ぐために、固定サイズを使用しないでください。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] パネルとコントロールが自動的に含まれている内容に基づいてサイズ変更します。 ほとんどのコントロールも詳細に制御を設定できる最小値と最大の大きさである (たとえば、MinWidth =「20」)。 <xref:System.Windows.Controls.Grid>を使用して、相対的な幅と高さを設定することも '\*' (たとえば、 `Width="0.25*"`) または共有機能のセルのサイズを使用します。  
  
 **ローカリゼーション コメント**  
  
 コンテンツがあいまいなと変換が困難な場合、多くの場合があります。 開発者またはデザイナーは、ローカリゼーション コメントによりローカライザーに追加のコンテキストやコメントを提供する機能を持っています。 文字の使用状況を明確に以下の Localization.Comments たとえば '&#124;'。  
  
 [!code-xaml[GlobalizationHomepage#LocalizationComment](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#localizationcomment)]  
  
 このコメントがの場合は、LocBaml ツール TextBlock_1 のコンテンツに関連付けられます (を参照してください[アプリケーションをローカライズする](how-to-localize-an-application.md)) には、出力の .csv ファイルに TextBlock_1 行の 6 番目の列に表示されることができます。  
  
|リソース キー|Category|読み取り可能です|変更可能です|コメント|[値]|  
|-|-|-|-|-|-|  
|TextBlock_1:System.Windows.Controls.TextBlock.$Content|テキスト|true|true|この文字は、装飾的な規則として使用されます。|&#124;|  
  
 コメントは、コンテンツまたは、次の構文を使用して任意の要素のプロパティに配置できます。  
  
 [!code-xaml[GlobalizationHomepage#LocalizationCommentsProp](~/samples/snippets/csharp/VS_Snippets_Wpf/GlobalizationHomepage/CS/Homepage.xaml#localizationcommentsprop)]  
  
 **ローカリゼーション属性**  
  
 多くの場合、開発者またはローカライズ マネージャーには、どのようなローカライザーを読み取り、変更の制御が必要があります。 たとえば、ローカライザーに、会社や法的な表現の名前を変換しない可能性があります。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 読みやすさ、変更可能性、および要素のコンテンツや、ローカリゼーション ツールは、ロック、非表示、または要素の並べ替えに使用できるプロパティのカテゴリを設定するための属性を提供します。 詳細については、「 <xref:System.Windows.Localization.Attributes%2A> 」を参照してください。 このサンプルの目的で、LocBaml ツールはこれらの属性の値を出力するだけです。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] すべてのコントロールは、これらの属性の既定値がそれらをオーバーライドするには。 たとえば、次の例がの既定のローカリゼーション属性をオーバーライド`TextBlock_1`およびローカライザーの判読できるコンテンツが変更不可能な状態を設定します。  
  
 [!code-xaml[LocalizationComAtt#LocalizationAttributes](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationComAtt/CSharp/Attributes.xaml#localizationattributes)]  
  
 読みやすさと、変更できる属性に加えて[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]UI の一般的なカテゴリの列挙を提供します (<xref:System.Windows.LocalizationCategory>) を使用して、ローカライザーに詳細なコンテキストを与えることができます。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]でプラットフォーム コントロールの既定のカテゴリをオーバーライドできる[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]も。  
  
 [!code-xaml[LocalizationComAtt#LocalizationAttributesOverridden](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationComAtt/CSharp/Attributes.xaml#localizationattributesoverridden)]  
  
 既定のローカリゼーション属性を[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]提供カスタム コントロールの適切な既定値を正しく設定できるようにも、コードにオーバーライドできます。 例:  

```csharp 
[Localizability(Readability = Readability.Readable, Modifiability=Modifiability.Unmodifiable, LocalizationCategory.None)] 
public class CorporateLogo : TextBlock
{
    // ...
}
``` 
 
 インスタンスの属性で設定あたり[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]カスタム コントロールのコードで設定された値より優先します。 属性とコメントの詳細については、次を参照してください。[ローカリゼーション属性とコメント](localization-attributes-and-comments.md)します。  
  
 **フォント フォールバックと複合フォント**  
  
 指定されたコード ポイント範囲をサポートしていないフォントを指定する場合[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は Windows\Fonts ディレクトリ内にあるグローバル ユーザー Interface.compositefont を使用している 1 つに自動的にフォールバックします。 複合フォントだけその他のフォントの動作し、要素の設定で明示的に使用できる`FontFamily`(たとえば、 `FontFamily="Global User Interface"`)。 独自の複合フォントを作成し、特定のコード ポイント範囲および言語を使用するフォントを指定して、独自のフォント フォールバック設定を指定できます。  
  
 複合フォントの詳細については、次を参照してください。<xref:System.Windows.Media.FontFamily>します。  
  
 **Microsoft のホーム ページのローカライズ**  
  
 このアプリケーションのローカライズを実行 ダイアログ ボックスの例と同じ手順を行うことができます。 アラビア語のローカライズされた .csv ファイルが使用可能で、[グローバリゼーション ホームページ サンプル](https://go.microsoft.com/fwlink/?LinkID=159990)します。
