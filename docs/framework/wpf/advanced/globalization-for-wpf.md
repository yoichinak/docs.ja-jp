---
title: WPF のグローバリゼーション
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], international user interface
- XAML [WPF], globalization
- international user interface [WPF], XAML
- globalization [WPF]
ms.assetid: 4571ccfe-8a60-4f06-9b37-7ac0b1c2d10f
ms.openlocfilehash: 948d147a0990961a8706298f1112f85882e30119
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015613"
---
# <a name="globalization-for-wpf"></a>WPF のグローバリゼーション
このトピックでは、グローバル市場向けのアプリケーションを作成[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]するときに注意する必要がある問題について説明します。 グローバリゼーションプログラミング要素は、ので[!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)] `System.Globalization`定義されています。

<a name="xaml_globalization"></a>
## <a name="xaml-globalization"></a>XAML グローバリゼーション
 [!INCLUDE[TLA#tla_xaml#initcap](../../../../includes/tlasharptla-xamlsharpinitcap-md.md)]はに[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]基づいており、 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]仕様で定義されているグローバリゼーションサポートを利用しています。 以下のセクションでは[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 、注意すべきいくつかの機能について説明します。

<a name="char_reference"></a>
### <a name="character-references"></a>文字参照
文字参照は、それが表す特定[!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)]の文字の UTF16 コード単位を、10進数または16進数で示します。 次の例では、コプト語の大文字の水平、または ' Ϩ ' の10進文字の参照を示します。

```
&#1000;
```

次の例は、16進数の文字参照を示しています。 16進数の前に**x**があることに注意してください。

```
&#x3E8;
```

<a name="encoding"></a>
### <a name="encoding"></a>エンコード
 によっ[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]てサポートされるエン[!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)]コーディングは、ASCII、utf-16、utf-8 です。 Encoding ステートメントはドキュメントの[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]先頭にあります。 エンコーディング属性が存在せず、バイト順もない場合、パーサーでは既定として UTF-8 が使用されます。 UTF-8 と UTF-16 は優先エンコードです。 UTF-7 には対応していません。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイルで utf-8 エンコーディングを指定する方法を次の例に示します。

```
?xml encoding="UTF-8"?
```

<a name="lang_attrib"></a>
### <a name="language-attribute"></a>言語属性
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]は、 [xml: lang](../../xaml-services/xml-lang-handling-in-xaml.md)を使用して、要素の言語属性を表します。  <xref:System.Globalization.CultureInfo>クラスを利用するには、言語属性の値が、で定義されて<xref:System.Globalization.CultureInfo>いるカルチャ名のいずれかである必要があります。 [xml:lang](../../xaml-services/xml-lang-handling-in-xaml.md) は要素ツリーで継承可能であり (XML ルールによる継承であり、必ずしも依存関係プロパティの継承によるものではありません)、その既定値は、明示的に割り当てられていない場合、空の文字列になります。

 言語属性は、方言を指定するときに非常に役立ちます。 たとえば、フランス語であれば、フランス、ケベック、ベルギー、スイスでスペル、語彙、発音が異なります。 また、中国語、日本語、韓国語はの[!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)]コードポイントを共有しますが、表意文字の形状は異なり、まったく異なるフォントを使用します。

 次[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]の例では`fr-CA` 、language 属性を使用してカナダフランス語を指定しています。

```xml
<TextBlock xml:lang="fr-CA">Découvrir la France</TextBlock>
```

<a name="unicode"></a>
### <a name="unicode"></a>Unicode
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]サロゲートを[!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)]含むすべての機能をサポートします。 文字セットをに[!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)]マップできる限り、サポートされています。 たとえば、GB18030 では、一部の文字が中国語、日本語、韓国語 (CFK) の拡張 A および B とサロゲート ペアにマッピングされているため、完全に対応しています。 アプリケーション[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]では、 <xref:System.Globalization.StringInfo>を使用して、サロゲートペアまたは組み合わせ文字があるかどうかを理解せずに、文字列を操作できます。

<a name="design_intl_ui_with_xaml"></a>
## <a name="designing-an-international-user-interface-with-xaml"></a>XAML で各国対応ユーザー インターフェイスを設計する
 ここでは[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 、アプリケーションを作成するときに考慮する必要がある機能について説明します。

<a name="intl_text"></a>
### <a name="international-text"></a>国際対応テキスト
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]には、Microsoft .NET Framework でサポートされているすべての書記体系の組み込み処理が含まれています。

 現在、次の書体がサポートされています。

- アラビア語

- ベンガル語

- デバナガリ

- キリル言語

- ギリシャ語

- グジャラート語

- グルムキー

- ヘブライ語

- 表意文字スクリプト

- カナラ語

- ラオス語

- ラテン語

- マラヤーラム語

- モンゴル語

- オディア語

- シリア語

- タミール語

- テルグ語

- ターナ

- タイ語*

- チベット語

 \* このリリースでは、タイ語テキストを表示し、編集できますが、単語を分割することはできません。

 現在、次のスクリプトはサポートされていません。

- クメール語

- 韓国語の古いハングル

- ミャンマー

- シンハラ語

 すべての書記体系エンジンは、OpenType フォントをサポートしています。 OpenType フォントには OpenType レイアウトテーブルを含めることができます。これにより、フォントの作成者は、より高い言語とハイエンドのタイポグラフィフォントをデザインできます。 OpenType フォントレイアウトテーブルには、グリフの置換、グリフの配置、理由、およびベースラインの配置に関する情報が含まれており、テキスト処理アプリケーションによってテキストのレイアウトが向上します。

 OpenType フォントを使用すると、エンコードを使用[!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)]して大きなグリフセットを処理できます。 このようなエンコードにより、広範な国際対応が可能になり、さまざまなグリフを印刷できます。

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]テキストレンダリングは、解決の独立性をサポートする Microsoft の ClearType サブピクセルテクノロジを利用しています。 これにより読みやすさが大幅に向上し、あらゆる書体で高品質の雑誌スタイルの書面を作成できます。

<a name="intl_layout"></a>
### <a name="international-layout"></a>国際対応レイアウト
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では非常に便利な方法で横書きレイアウト、双方向レイアウト、縦書きレイアウトを作成できます。 プレゼンテーションフレームワークでは<xref:System.Windows.FrameworkElement.FlowDirection%2A> 、プロパティを使用してレイアウトを定義できます。 フローの方向パターン:

- *LeftToRight* - ラテン語や東アジア言語などのための横書きレイアウト。

- *RightToLeft* - アラビア語やヘブライ語などのための双方向レイアウト。

<a name="developing_localizable_apps"></a>
## <a name="developing-localizable-applications"></a>ローカライズ可能なアプリケーションの開発
 世界中で利用されるアプリケーションを開発するときは、アプリケーションをローカライズ可能にすることを忘れてはなりません。 後続のトピックで、考慮事項を指摘します。

<a name="mui"></a>
### <a name="multilingual-user-interface"></a>多言語ユーザー インターフェイス
 多言語ユーザーインターフェイス (MUI) は、ある言語から[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]別の言語に切り替えるための Microsoft サポートです。 アプリケーション[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は、アセンブリモデルを使用して、MUI をサポートします。 1 つのアプリケーションに言語に依存しないアセンブリと言語に依存するサテライト リソース アセンブリが含まれます。 エントリ ポイントはメイン アセンブリのマネージド .EXE です。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]リソースローダーは、 [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)]リソースマネージャーを利用してリソースの参照とフォールバックをサポートします。 多言語サテライト アセンブリは同じメイン アセンブリと連動します。 読み込まれるリソースアセンブリは、現在<xref:System.Globalization.CultureInfo.CurrentUICulture%2A>のスレッドのによって異なります。

<a name="localizable_ui"></a>
### <a name="localizable-user-interface"></a>ローカライズ可能なユーザー インターフェイス
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションは[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 、 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]を使用してを定義します。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] で開発すると、オブジェクトの階層に一連のプロパティとロジックを指定できます。 の[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]主な用途は、アプリケーション[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を開発することですが、これを使用して共通言語ランタイム (CLR) オブジェクトの階層を指定することもできます。 ほとんどの開発[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]者は、を使用[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]してアプリケーションを指定し、 C#などのプログラミング言語を使用してユーザーの操作に応答します。

 リソースの観点からは、言語に[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]依存[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]するように設計されたファイルはリソース要素であるため、その最終的な配布形式はローカライズ可能である必要があります。 は[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]イベントを処理でき[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ないため、多くのアプリケーションにはこの処理を行うためのコードブロックが含まれています。 詳細については、「 [XAML の概要 (WPF)](xaml-overview-wpf.md)」を参照してください。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイルが XAML の BAML 形式にトークン化されると、コードは削除され、別のバイナリにコンパイルされます。 XAML ファイル、画像、その他の種類の管理対象リソース オブジェクトの BAML 形式はサテライト リソース アセンブリに組み込まれます。サテライト リソース アセンブリに組み込むことで、他の言語にローカライズできます。ローカライズが必要なければ、メイン アセンブリに組み込まれます。

> [!NOTE]
> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションでは、 [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)]文字列テーブルや画像など、すべての CLR リソースがサポートされます。

<a name="building_localizable_apps"></a>
### <a name="building-localizable-applications"></a>ローカライズ可能なアプリケーションの構築
 ローカリゼーションとは、を[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]別のカルチャに適合させることを意味します。 アプリケーションを[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ローカライズ可能にするには、開発者はローカライズ可能なすべてのリソースをリソースアセンブリに組み込む必要があります。 リソースアセンブリは異なる言語にローカライズされ、コードビハインドはリソース管理 API を使用して読み込みます。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションに必要なファイルの1つは、プロジェクトファイル (proj) です。 アプリケーションで使用するすべてのリソースをプロジェクト ファイルに含める必要があります。 その方法を .csproj ファイルからの次の例で示します。

```xml
<Resource Include="data\picture1.jpg"/>
<EmbeddedResource Include="data\stringtable.en-US.restext"/>
```

 アプリケーションでリソースを使用するには、 <xref:System.Resources.ResourceManager>をインスタンス化し、使用するリソースを読み込みます。 この方法を次の例に示します。

 [!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]

<a name="using_clickonce"></a>
## <a name="using-clickonce-with-localized-applications"></a>ローカライズされたアプリケーションで ClickOnce を使用する
 ClickOnce は、Visual Studio 2005 に付属する新しい Windows フォームデプロイテクノロジです。 アプリケーションをインストールしたり、Web アプリケーションをアップグレードしたりできます。 ClickOnce で展開されたアプリケーションがローカライズされると、ローカライズされたカルチャでのみ表示できます。 たとえば、展開されたアプリケーションが日本語にローカライズされている場合、英語[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]版の Windows では、日本語でのみ表示できます。 これは、日本語ユーザーが英語版の Windows を実行する一般的なシナリオであるため、問題が発生します。

 この問題の解決策は、非依存言語フォールバック属性を設定することです。 アプリケーション開発者はメイン アセンブリからリソースを任意で削除し、特定のカルチャに対応するサテライト アセンブリでそのリソースを見つけられるように指定できます。 このプロセスを制御するに<xref:System.Resources.NeutralResourcesLanguageAttribute>は、を使用します。 <xref:System.Resources.NeutralResourcesLanguageAttribute>クラスのコンストラクターには、2つのシグネチャがあります<xref:System.Resources.UltimateResourceFallbackLocation> 。1つはパラメーターを受け取り<xref:System.Resources.ResourceManager> 、がフォールバックリソースを抽出する場所を指定します。メインアセンブリまたはサテライトアセンブリです。 この属性を使用する方法の例を次に示します。 最終的なフォールバックの場所では、は、 <xref:System.Resources.ResourceManager>現在実行中のアセンブリのディレクトリの "de" サブディレクトリにあるリソースを検索します。

```
[assembly: NeutralResourcesLanguageAttribute(
    "de" , UltimateResourceFallbackLocation.Satellite)]
```

## <a name="see-also"></a>関連項目

- [WPF のグローバリゼーションおよびローカリゼーションの概要](wpf-globalization-and-localization-overview.md)
