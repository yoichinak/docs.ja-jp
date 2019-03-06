---
title: WPF のグローバリゼーション
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], international user interface
- XAML [WPF], globalization
- international user interface [WPF], XAML
- globalization [WPF]
ms.assetid: 4571ccfe-8a60-4f06-9b37-7ac0b1c2d10f
ms.openlocfilehash: dee1df1e122e47ea67618da5a1e4349e28d90447
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377366"
---
# <a name="globalization-for-wpf"></a>WPF のグローバリゼーション
このトピックで作成する際に注意する必要がある問題が発生する[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]グローバル市場向けアプリケーション。 グローバリゼーション プログラミングの要素がで定義されている[!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)]で`System.Globalization`します。



<a name="xaml_globalization"></a>
## <a name="xaml-globalization"></a>XAML グローバリゼーション
 [!INCLUDE[TLA#tla_xaml#initcap](../../../../includes/tlasharptla-xamlsharpinitcap-md.md)] に基づいて[!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)]で定義されているグローバリゼーション サポートを利用して、[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]仕様。 次のセクションでは、いくつか説明[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を意識する必要がある機能です。

<a name="char_reference"></a>
### <a name="character-references"></a>文字参照
文字参照では、特定の UTF16 コード単位[!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)]文字、10 進数または 16 進数のいずれかを表します。 次の例では、コプト文字の大文字に、または 'Ϩ' の参照を 10 進数の文字を示しています。

```
&#1000;
```

次の例では、16 進数の文字の一覧を示します。 持つことに注意してください、 **x** 16 進数の前にします。

```
&#x3E8;
```

<a name="encoding"></a>
### <a name="encoding"></a>エンコード
 サポートされているエンコード[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]は[!INCLUDE[TLA#tla_ascii](../../../../includes/tlasharptla-ascii-md.md)]、 [!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)] utf-16 と utf-8 です。 エンコード ステートメントがの先頭に[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ドキュメント。 エンコーディング属性が存在せず、バイト順もない場合、パーサーでは既定として UTF-8 が使用されます。 UTF-8 と UTF-16 は優先エンコードです。 UTF-7 には対応していません。 次の例で utf-8 エンコードを指定する方法を示します、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイル。

```
?xml encoding="UTF-8"?
```

<a name="lang_attrib"></a>
### <a name="language-attribute"></a>言語属性
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 使用して[xml:lang](../../xaml-services/xml-lang-handling-in-xaml.md)を要素の language 属性を表します。  活用するために、<xref:System.Globalization.CultureInfo>クラス、言語属性の値で定義済みカルチャ名のいずれかを指定する必要がある<xref:System.Globalization.CultureInfo>します。 [xml:lang](../../xaml-services/xml-lang-handling-in-xaml.md) は要素ツリーで継承可能であり (XML ルールによる継承であり、必ずしも依存関係プロパティの継承によるものではありません)、その既定値は、明示的に割り当てられていない場合、空の文字列になります。

 言語属性は、方言を指定するときに非常に役立ちます。 たとえば、フランス語であれば、フランス、ケベック、ベルギー、スイスでスペル、語彙、発音が異なります。 中国語、日本語、および韓国語のコード ポイントを共有することも[!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)]が、表意文字の形が異なるため、まったく別のフォントを使用します。

 次[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]の例では、`fr-CA`言語属性をカナダ フランス語を指定します。

```xml
<TextBlock xml:lang="fr-CA">Découvrir la France</TextBlock>
```

<a name="unicode"></a>
### <a name="unicode"></a>Unicode
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] サポートされているすべて[!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)]サロゲートを含む機能。 文字セットにマップできる限り[!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)]、サポートされています。 たとえば、GB18030 では、一部の文字が中国語、日本語、韓国語 (CFK) の拡張 A および B とサロゲート ペアにマッピングされているため、完全に対応しています。 A[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションが使用できる<xref:System.Globalization.StringInfo>サロゲート ペアがあるかどうかを理解することや、組み合わせ文字なし文字列を操作します。

<a name="design_intl_ui_with_xaml"></a>
## <a name="designing-an-international-user-interface-with-xaml"></a>XAML で各国対応ユーザー インターフェイスを設計する
 このセクションについて説明します[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]機能アプリケーションを作成するときに考慮する必要があります。

<a name="intl_text"></a>
### <a name="international-text"></a>国際対応テキスト
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] サポートされている Microsoft .NET Framework のすべての書き込みのシステムの組み込みの処理が含まれています。

 現在、次の書体がサポートされています。

-   アラビア語

-   ベンガル語

-   デバナガリ

-   キリル言語

-   ギリシャ語

-   グジャラート語

-   グルムキー

-   ヘブライ語

-   表意文字スクリプト

-   カナラ語

-   ラオス語

-   ラテン語

-   マラヤーラム語

-   モンゴル語

-   オディア語

-   シリア語

-   タミール語

-   テルグ語

-   ターナ

-   タイ語*

-   チベット語

 * このリリースでは、タイ語テキストを表示し、編集できますが、単語を分割することはできません。

 現在、次のスクリプトはサポートされていません。

-   クメール語

-   韓国語の古いハングル

-   ミャンマー

-   シンハラ語

 すべての書記体系エンジン サポート[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]フォント。 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] フォントを含めることができます、[!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)]より国際的およびハイエンドなタイポグラフィ フォントのデザイン、フォントの作成を有効にするレイアウト テーブル。 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)]フォント レイアウト テーブルは、テキストのレイアウトを向上させるためにテキスト処理アプリケーションを有効にするグリフ代用、グリフ配置、位置揃え、基線配置に関する情報を含めることができます。

 [!INCLUDE[TLA2#tla_opentype](../../../../includes/tla2sharptla-opentype-md.md)] 大量のグリフの処理の設定を使用してフォントを許可する[!INCLUDE[TLA2#tla_unicode](../../../../includes/tla2sharptla-unicode-md.md)]エンコードします。 このようなエンコードにより、広範な国際対応が可能になり、さまざまなグリフを印刷できます。

 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] テキストのレンダリングが提要[!INCLUDE[TLA#tla_ct](../../../../includes/tlasharptla-ct-md.md)]サブピクセル技術解決の独立性をサポートします。 これにより読みやすさが大幅に向上し、あらゆる書体で高品質の雑誌スタイルの書面を作成できます。

<a name="intl_layout"></a>
### <a name="international-layout"></a>国際対応レイアウト
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では非常に便利な方法で横書きレイアウト、双方向レイアウト、縦書きレイアウトを作成できます。 プレゼンテーション フレームワークで、<xref:System.Windows.FrameworkElement.FlowDirection%2A>レイアウトを定義するプロパティを使用できます。 フローの方向パターン:

-   *LeftToRight* - ラテン語や東アジア言語などのための横書きレイアウト。

-   *RightToLeft* - アラビア語やヘブライ語などのための双方向レイアウト。

<a name="developing_localizable_apps"></a>
## <a name="developing-localizable-applications"></a>ローカライズ可能なアプリケーションの開発
 世界中で利用されるアプリケーションを開発するときは、アプリケーションをローカライズ可能にすることを忘れてはなりません。 後続のトピックで、考慮事項を指摘します。

<a name="mui"></a>
### <a name="multilingual-user-interface"></a>多言語ユーザー インターフェイス
 多言語ユーザー インターフェイス (MUI) は、[!INCLUDE[TLA#tla_ms](../../../../includes/tlasharptla-ms-md.md)]の切り替えをサポートして[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]別の 1 つの言語から。 A[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションはアセンブリ モデルを使用して、MUI をサポートします。 1 つのアプリケーションに言語に依存しないアセンブリと言語に依存するサテライト リソース アセンブリが含まれます。 エントリ ポイントはメイン アセンブリのマネージド .EXE です。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] リソース ローダーは活用、[!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)]のリソース ルックアップとフォールバックをサポートするためにリソース マネージャー。 多言語サテライト アセンブリは同じメイン アセンブリと連動します。 読み込まれるリソース アセンブリに依存、<xref:System.Globalization.CultureInfo.CurrentUICulture%2A>現在のスレッド。

<a name="localizable_ui"></a>
### <a name="localizable-user-interface"></a>ローカライズ可能なユーザー インターフェイス
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションを使用して、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を定義する、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]します。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] で開発すると、オブジェクトの階層に一連のプロパティとロジックを指定できます。 主な用途[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を開発する[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションが、これを使用して、任意の階層の指定[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]オブジェクト。 ほとんどの開発者が使用して[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]アプリケーションを指定する[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]c# などのプログラミング言語を使用して、ユーザーとの対話に応答するとします。

 リソースの観点から、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイルの説明の言語に依存するように設計[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]リソース要素は、そのため、最終的な配布形式が外国の言語にローカライズ可能にする必要があります。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]多くようにイベントが処理できない[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]アプリケーションは、これを行うコードのブロックを含めることができます。 詳細については、次を参照してください。 [XAML の概要 (WPF)](xaml-overview-wpf.md)します。 コードが除去し、異なるバイナリにコンパイル時に、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイルが XAML の BAML 形式にトークン化します。 XAML ファイル、画像、その他の種類の管理対象リソース オブジェクトの BAML 形式はサテライト リソース アセンブリに組み込まれます。サテライト リソース アセンブリに組み込むことで、他の言語にローカライズできます。ローカライズが必要なければ、メイン アセンブリに組み込まれます。

> [!NOTE]
>  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] すべてのアプリケーション サポート、 [!INCLUDE[TLA2#tla_netframewk](../../../../includes/tla2sharptla-netframewk-md.md)] [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]文字列テーブルやイメージなどのリソース。

<a name="building_localizable_apps"></a>
### <a name="building-localizable-applications"></a>ローカライズ可能なアプリケーションの構築
 ローカライズを調整すること、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]を異なるカルチャにします。 させる、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションをローカライズ可能で、開発者がローカライズ可能なすべてのリソースをリソース アセンブリにビルドする必要があります。 さまざまな言語にローカライズされたリソース アセンブリと分離コードは リソース管理を使用して[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]を読み込めません。 必要なファイルのいずれかを[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションは、プロジェクト ファイル (.proj) です。 アプリケーションで使用するすべてのリソースをプロジェクト ファイルに含める必要があります。 その方法を .csproj ファイルからの次の例で示します。

```xml
<Resource Include="data\picture1.jpg"/>
<EmbeddedResource Include="data\stringtable.en-US.restext"/>
```

 使用する、アプリケーションでリソースをインスタンス化、<xref:System.Resources.ResourceManager>を使用するリソースを読み込むとします。 この方法を次の例に示します。

 [!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]

<a name="using_clickonce"></a>
## <a name="using-clickonce-with-localized-applications"></a>ローカライズされたアプリケーションで ClickOnce を使用する
 ClickOnce は、Visual Studio 2005 に付属するは、新しい Windows フォーム展開テクノロジです。 アプリケーションをインストールしたり、Web アプリケーションをアップグレードしたりできます。 ClickOnce で展開されたアプリケーションがローカライズされると、ローカライズされたカルチャでのみ表示できます。 たとえば、デプロイされたアプリケーションが日本語にローカライズされている場合にのみ表示できる日本語で[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]英語版の Windows ではなく。 これにより、英語版の Windows を実行する日本のユーザーの一般的なシナリオのため、問題を表示します。

 この問題の解決策は、非依存言語フォールバック属性を設定することです。 アプリケーション開発者はメイン アセンブリからリソースを任意で削除し、特定のカルチャに対応するサテライト アセンブリでそのリソースを見つけられるように指定できます。 このプロセスの使用を制御する、<xref:System.Resources.NeutralResourcesLanguageAttribute>します。 コンス トラクター、<xref:System.Resources.NeutralResourcesLanguageAttribute>クラスには 2 つの署名を受け取る 1 つ、<xref:System.Resources.UltimateResourceFallbackLocation>場所を指定するパラメーターを<xref:System.Resources.ResourceManager>フォールバック リソースを抽出する必要があります: メイン アセンブリまたはサテライト アセンブリ。 この属性を使用する方法の例を次に示します。 最終的なフォールバックの場所のコードと、<xref:System.Resources.ResourceManager>現在実行中のアセンブリのディレクトリのサブディレクトリ"de"でリソースを見つけます。

```
[assembly: NeutralResourcesLanguageAttribute(
    "de" , UltimateResourceFallbackLocation.Satellite)]
```

## <a name="see-also"></a>関連項目
- [WPF のグローバリゼーションおよびローカリゼーションの概要](wpf-globalization-and-localization-overview.md)
