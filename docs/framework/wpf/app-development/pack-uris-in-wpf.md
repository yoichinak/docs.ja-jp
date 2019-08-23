---
title: WPF におけるパッケージの URI
ms.date: 03/30/2017
helpviewer_keywords:
- pack URI scheme [WPF]
- loading embedded resources [WPF]
- URIs (Uniform Resource Identifiers)
- Uniform Resource Identifiers (URIs)
- loading non-resource files
- application management [WPF]
ms.assetid: 43adb517-21a7-4df3-98e8-09e9cdf764c4
ms.openlocfilehash: ad928fb223ce22c65bb86a78c7d4cd006651a2d5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950753"
---
# <a name="pack-uris-in-wpf"></a>WPF におけるパッケージの URI

Windows Presentation Foundation (WPF) では[!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)] 、を使用して、次のようなさまざまな方法でファイルを識別し、読み込むことができます。

- アプリケーションを[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]初めて起動するときに表示するを指定します。

- イメージの読み込み。

- ページへの移動。

- 実行可能でないデータ ファイルの読み込み。

さらに[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] 、を使用して、次のようなさまざまな場所からファイルを識別し、読み込むことができます。

- 現在のアセンブリ。

- 参照アセンブリ。

- アセンブリに対して相対的な位置。

- アプリケーションの起点サイト。

これらの場所からこれらの種類のファイルを識別して読み込むための一貫[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]したメカニズムを提供するため、では、*パック URI スキーム*の拡張性を活用しています。 このトピックでは、スキームの概要について説明し、 [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]さまざまなシナリオでパックを作成する方法について説明します。また、両方[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]のマークアップからパックを使用する方法を説明する前に、絶対と相対[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]および[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]解決方法について説明します。コードを記述します。

<a name="The_Pack_URI_Scheme"></a>

## <a name="the-pack-uri-scheme"></a>パック URI スキーム

パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]スキームは、コンテンツを整理および識別するためのモデルを記述する[Open パッケージング規則](https://go.microsoft.com/fwlink/?LinkID=71255)(OPC) 仕様によって使用されます。 このモデルの主要な要素はパッケージとパーツで、*パッケージ*は1つ以上の論理*部分*の論理コンテナーです。 この概念を次の図に示します。

![パッケージとパーツのダイアグラム](./media/pack-uris-in-wpf/wpf-package-parts-diagram.png)

パーツを識別するために、OPC 仕様では RFC 2396 (Uniform Resource Identifier (URI)) の拡張性を活用しています。汎用構文) パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]スキームを定義します。

によっ[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]て指定されるスキームは、そのプレフィックスによって定義されます。 http、ftp、および file は、よく知られている例です。 パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]スキームは、スキームとして "pack" を使用し、authority と path という2つのコンポーネントが含まれています。 パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]の形式を次に示します。

pack://*authority*/*パス*

*Authority*は、パーツが含まれているパッケージの種類を指定し、*パス*はパッケージ内のパーツの場所を指定します。

この概念を次の図に示します。

![パッケージ、権限、およびパスの間のリレーションシップ](./media/pack-uris-in-wpf/wpf-relationship-diagram.png)

パッケージとパーツは、アプリケーションとファイルに似ています。つまり、アプリケーション (パッケージ) は、次のような 1 つ以上のファイル (パーツ) を含むことができます。

- ローカル アセンブリにコンパイルされるリソース ファイル。

- 参照センブリにコンパイルされるリソース ファイル。

- 参照元センブリにコンパイルされるリソース ファイル。

- コンテンツ ファイル。

- 起点サイト ファイル。

これらの種類のファイルにアクセス[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]するために、では application:///と siteoforigin:///の2つの機関がサポートされています。 application:/// オーソリティは、リソース ファイルやコンテンツ ファイルなど、コンパイル時に既知のアプリケーション データ ファイルを識別します。 siteoforigin:/// オーソリティは、起点サイト ファイルを識別します。 各オーソリティのスコープを次の図に示します。

![Pack URI のダイアグラム](./media/pack-uris-in-wpf/wpf-pack-uri-scheme.png)

> [!NOTE]
> パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]の機関コンポーネントは、パッケージを指す[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]埋め込みで、RFC 2396 に準拠している必要があります。 さらに、"/" 文字は "," 文字に置き換える必要があり、"%" や "?" などの予約文字はエスケープする必要があります。 詳細については、OPC を参照してください。

以下のセクションでは、これらの[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] 2 つの機関を使用して、リソース、コンテンツ、および起点サイトファイルを識別するための適切なパスと共にパックを構築する方法について説明します。

<a name="Resource_File_Pack_URIs___Local_Assembly"></a>

## <a name="resource-file-pack-uris"></a>リソース ファイルのパック URI

リソースファイルは MSBuild `Resource`項目として構成され、アセンブリにコンパイルされます。 WPF は、ローカルアセンブリにコンパイルされるか、ローカルアセンブリから参照されるアセンブリにコンパイルされるリソースファイルを識別するために使用できる、パック Uri の構築をサポートしています。

<a name="Local_Assembly_Resource_File"></a>

### <a name="local-assembly-resource-file"></a>ローカル アセンブリ リソース ファイル

ローカルアセンブリ[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]にコンパイルされるリソースファイルのパックは、次の権限とパスを使用します。

- **オーソリティ**: application:///。

- **パス**:ローカルアセンブリプロジェクトフォルダーのルートに対する相対パスを含む、リソースファイルの名前。

次の例は、ローカル[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]アセンブリの[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロジェクトフォルダーのルートにあるリソースファイルのパックを示しています。

`pack://application:,,,/ResourceFile.xaml`

次の例は、ローカル[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]アセンブリの[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロジェクトフォルダーのサブフォルダーにあるリソースファイルのパックを示しています。

`pack://application:,,,/Subfolder/ResourceFile.xaml`

<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>

### <a name="referenced-assembly-resource-file"></a>参照アセンブリ リソース ファイル

参照アセンブリ[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]にコンパイルされるリソースファイルのパックは、次の権限とパスを使用します。

- **オーソリティ**: application:///。

- **パス**:参照アセンブリにコンパイルされるリソースファイルの名前。 パスは、次の書式に従う必要があります。

  *Assemblyshortname*{ *;バージョン*] { *;PublicKey*]、コンポーネント/*パス*

  - **AssemblyShortName**: 参照アセンブリの短い名前。

  - **;Version** (省略可能): リソース ファイルを含む参照アセンブリのバージョン。 これは、同じ短い名前を持つ 2 つ以上の参照アセンブリが読み込まれるときに使用されます。

  - **;PublicKey** (省略可能): 参照アセンブリの署名に使用された公開鍵。 これは、同じ短い名前を持つ 2 つ以上の参照アセンブリが読み込まれるときに使用されます。

  - **;component**: 参照されるアセンブリが、ローカル アセンブリから参照されることを指定します。

  - **/Path**: 参照アセンブリのプロジェクト フォルダーのルートに対して相対的なパスを含むリソース ファイルの名前。

次の例は、参照[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]アセンブリの[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロジェクトフォルダーのルートにあるリソースファイルのパックを示しています。

`pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`

次の例は、参照[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]アセンブリの[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロジェクトフォルダーのサブフォルダーにあるリソースファイルのパックを示しています。

`pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`

次の例は、参照[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]され[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ているバージョン固有のアセンブリのプロジェクトフォルダーのルートフォルダーにあるリソースファイルのパックを示しています。

`pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`

参照されるアセンブリ[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]リソースファイルのパック構文は、application:///authority でのみ使用できます。 たとえば、次のはで[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]はサポートされていません。

`pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`

<a name="Content_File_Pack_URIs"></a>

## <a name="content-file-pack-uris"></a>コンテンツ ファイルのパック URI

コンテンツファイル[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]のパックは、次の証明機関とパスを使用します。

- **オーソリティ**: application:///。

- **パス**:アプリケーションのメインの実行可能アセンブリのファイルシステムの場所を基準としたパスを含む、コンテンツファイルの名前。

次の例は、実行[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]可能アセンブリ[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]と同じフォルダーにあるコンテンツファイルのパックを示しています。

`pack://application:,,,/ContentFile.xaml`

次の例は、アプリケーション[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]の実行[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]可能アセンブリに対して相対的なサブフォルダーにあるコンテンツファイルのパックを示しています。

`pack://application:,,,/Subfolder/ContentFile.xaml`

> [!NOTE]
> HTML コンテンツファイルに移動することはできません。 スキーム[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]では、起点サイトにある HTML ファイルへの移動のみがサポートされます。

<a name="The_siteoforigin_____Authority"></a>

## <a name="site-of-origin-pack-uris"></a>起点サイトのパック URI

起点サイト[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]ファイルのパックは、次の権限とパスを使用します。

- **オーソリティ**: siteoforigin:///。

- **パス**:起点サイトファイルの名前。実行可能アセンブリが起動された場所を基準とした相対パスを含みます。

次の例は、実行[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]可能アセンブリ[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]の起動元の場所に格納されている、起点サイトファイルのパックを示しています。

`pack://siteoforigin:,,,/SiteOfOriginFile.xaml`

次の例は、アプリケーション[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]の実行[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]可能アセンブリの起動元の場所を基準としたサブフォルダーに格納されている、起点サイトファイルのパックを示しています。

`pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`

<a name="Page_Files"></a>

## <a name="page-files"></a>ページ ファイル

MSBuild `Page`項目として構成されている XAML ファイルは、リソースファイルと同じ方法でアセンブリにコンパイルされます。 そのため、 `Page`リソースファイルのパック uri を使用して MSBuild 項目を識別できます。

通常、MSBuild [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] `Page`項目として構成されるファイルの種類は、次のいずれかのルート要素となります。

- <xref:System.Windows.Window?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Page?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.PageFunction%601?displayProperty=nameWithType>

- <xref:System.Windows.ResourceDictionary?displayProperty=nameWithType>

- <xref:System.Windows.Documents.FlowDocument?displayProperty=nameWithType>

- <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>

<a name="Absolute_vs_Relative_Pack_URIs"></a>

## <a name="absolute-vs-relative-pack-uris"></a>絶対および相対パック URI

完全修飾パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]には、スキーム、権限、およびパスが含まれており、これは絶対パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]と見なされます。 開発者のための簡略化[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]として、要素を使用すると、通常は[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]パスのみを含む、相対パックを使用して適切な属性を設定できます。

たとえば、ローカルアセンブリ内のリソースファイル[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]に対する次の絶対パックを考えてみます。

`pack://application:,,,/ResourceFile.xaml`

このリソースファイル[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]を参照する相対パックは、次のようになります。

`/ResourceFile.xaml`

> [!NOTE]
> 起点サイトファイルはアセンブリに関連付けられていないため、絶対パック[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]でのみ参照できます。

既定では、相対パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]は、参照を含むマークアップまたはコードの位置を基準として相対的に見なされます。 ただし、先頭に円記号が使用されている[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]場合、相対パック参照は、アプリケーションのルートを基準として相対的に考慮されます。 たとえば、次のようなプロジェクト構造を考えてみます。

`App.xaml`

`Page2.xaml`

`\SubFolder`

`+ Page1.xaml`

`+ Page2.xaml`

Page1 にルート \SubFolder\Page2.xaml を参照[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]するが含まれている場合、参照は次の相対[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]パックを使用できます。

`Page2.xaml`

Page1 がルートページを参照[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]するを含んでいる場合、参照は次の相対パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]を使用できます。

`/Page2.xaml`

<a name="Pack_URI_Resolution"></a>

## <a name="pack-uri-resolution"></a>パック URI の解決

パック[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]の形式を使用すると、さまざま[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]な種類のファイルのパックを同じように表示できます。 たとえば、次のような絶対パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]を考えてみます。

`pack://application:,,,/ResourceOrContentFile.xaml`

この絶対パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]は、ローカルアセンブリまたはコンテンツファイル内のリソースファイルを参照できます。 これは、次の相対[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]にも当てはまります。

`/ResourceOrContentFile.xaml`

では、パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]が参照するファイルの種類を特定するために、次のヒューリスティックを使用して、 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]ローカルアセンブリおよびコンテンツファイル内のリソースファイルが解決[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]されます。

1. <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> パッケージ[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]に一致する属性のアセンブリメタデータをプローブします。

2. 属性が見つかった場合、パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]のパスはコンテンツファイルを参照します。 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>

3. <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>属性が見つからない場合は、ローカルアセンブリにコンパイルされる set リソースファイルを調べます。

4. パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]のパスに一致するリソースファイルが見つかった場合、パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]のパスはリソースファイルを参照します。

5. リソースが見つからない場合は、内部で作成<xref:System.Uri>されたが無効です。

[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]次を参照するに[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]は、解決策が適用されません。

- 参照アセンブリ内のコンテンツファイル: これらのファイルの種類は[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]、ではサポートされていません。

- 参照されたアセンブリ内[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]の埋め込みファイル: 参照されるアセンブリの名前`;component`とサフィックスの両方が含まれているため、一意であることを識別します。

- 起点サイトファイル: siteoforigin:/// [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]機関を含むパック[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]によって識別できる唯一のファイルであるため、一意であることがわかります。

パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]の解決方法の1つとして、コードがリソースファイルとコンテンツファイルの場所から多少独立していることが挙げられます。 たとえば、ローカルアセンブリ内にコンテンツファイルとして再構成されたリソースファイルがある場合、そのパック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]を使用するコードと同じように、リソースのパックは変わりません。

<a name="Programming_with_Pack_URIs"></a>

## <a name="programming-with-pack-uris"></a>パック URI を使用したプログラミング

多く[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]のクラスには、次のような[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]パックで設定できるプロパティが実装されています。

- <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>

- <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=nameWithType>

- <xref:System.Windows.Window.Icon%2A?displayProperty=nameWithType>

- <xref:System.Windows.Controls.Image.Source%2A?displayProperty=nameWithType>

これらのプロパティは、マークアップとコードのどちらからでも設定できます。 このセクションでは、両方の基本構造について説明してから、一般的なシナリオの例を示します。

<a name="Using_Pack_URIs_in_Markup"></a>

### <a name="using-pack-uris-in-markup"></a>マークアップでのパック URI の使用

パックをマークアップで指定するに[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]は、パッケージの属性の要素を設定します。[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 例:

`<element attribute="pack://application:,,,/File.xaml" />`

表1は、マークアップで[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]指定できるさまざまな絶対パックを示しています。

表 1:マークアップでの絶対パック Uri

|ファイル|絶対パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|リソース ファイル - ローカル アセンブリ|`"pack://application:,,,/ResourceFile.xaml"`|
|サブフォルダー内のリソース ファイル - ローカル アセンブリ|`"pack://application:,,,/Subfolder/ResourceFile.xaml"`|
|リソース ファイル - 参照アセンブリ|`"pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml"`|
|参照アセンブリのサブフォルダー内のリソース ファイル|`"pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|バージョン管理された参照アセンブリ内のリソース ファイル|`"pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml"`|
|コンテンツ ファイル|`"pack://application:,,,/ContentFile.xaml"`|
|サブフォルダー内のコンテンツ ファイル|`"pack://application:,,,/Subfolder/ContentFile.xaml"`|
|起点サイト ファイル|`"pack://siteoforigin:,,,/SOOFile.xaml"`|
|サブフォルダー内の起点サイト ファイル|`"pack://siteoforigin:,,,/Subfolder/SOOFile.xaml"`|

表2は、マークアップで[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]指定できるさまざまな相対パックを示しています。

表 2:マークアップでの相対パック Uri

|ファイル|相対パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|ローカル アセンブリ内のリソース ファイル|`"/ResourceFile.xaml"`|
|ローカル アセンブリのサブフォルダー内のリソース ファイル|`"/Subfolder/ResourceFile.xaml"`|
|参照アセンブリ内のリソース ファイル|`"/ReferencedAssembly;component/ResourceFile.xaml"`|
|参照アセンブリのサブフォルダー内のリソース ファイル|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|
|コンテンツ ファイル|`"/ContentFile.xaml"`|
|サブフォルダー内のコンテンツ ファイル|`"/Subfolder/ContentFile.xaml"`|

<a name="Using_Pack_URIs_in_Code"></a>

### <a name="using-pack-uris-in-code"></a>コードでのパック URI の使用

コードでパック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]を指定するには、 <xref:System.Uri>クラスをインスタンス化し[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 、そのパックをパラメーターとしてコンストラクターに渡します。 このコード例を次に示します。

```csharp
Uri uri = new Uri("pack://application:,,,/File.xaml");
```

既定では、 <xref:System.Uri>クラスはパック[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]を絶対値と見なします。 その結果、 <xref:System.Uri>クラスのインスタンスが相対パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]を使用して作成されると、例外が発生します。

```csharp
Uri uri = new Uri("/File.xaml");
```

幸いにも<xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29> 、 <xref:System.Uri>クラスコンストラクターのオーバーロードは、型<xref:System.UriKind>のパラメーターを受け取り、パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]が絶対か相対かを指定できます。

```csharp
// Absolute URI (default)
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);
// Relative URI
Uri relativeUri = new Uri("/File.xaml",
                        UriKind.Relative);
```

指定された<xref:System.UriKind.Absolute>パック<xref:System.UriKind.Relative> [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]がいずれかであることがわかっている場合にのみ、またはを指定する必要があります。 実行時にユーザーがパック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]を入力したときなど、使用されているパックの種類がわからない場合<xref:System.UriKind.RelativeOrAbsolute>は、代わりにを使用します。

```csharp
// Relative or Absolute URI provided by user via a text box
TextBox userProvidedUriTextBox = new TextBox();
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);
```

表3は、を使用[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] <xref:System.Uri?displayProperty=nameWithType>してコードで指定できるさまざまな相対パックを示しています。

表 3:コード内の絶対パック Uri

|ファイル|絶対パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|リソース ファイル - ローカル アセンブリ|`Uri uri = new Uri("pack://application:,,,/ResourceFile.xaml", UriKind.Absolute);`|
|サブフォルダー内のリソース ファイル - ローカル アセンブリ|`Uri uri = new Uri("pack://application:,,,/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|
|リソース ファイル - 参照アセンブリ|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Absolute);`|
|参照アセンブリのサブフォルダー内のリソース ファイル|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Absolute);`|
|バージョン管理された参照アセンブリ内のリソース ファイル|`Uri uri = new Uri("pack://application:,,,/ReferencedAssembly;v1.0.0.0;component/ResourceFile.xaml", UriKind.Absolute);`|
|コンテンツ ファイル|`Uri uri = new Uri("pack://application:,,,/ContentFile.xaml", UriKind.Absolute);`|
|サブフォルダー内のコンテンツ ファイル|`Uri uri = new Uri("pack://application:,,,/Subfolder/ContentFile.xaml", UriKind.Absolute);`|
|起点サイト ファイル|`Uri uri = new Uri("pack://siteoforigin:,,,/SOOFile.xaml", UriKind.Absolute);`|
|サブフォルダー内の起点サイト ファイル|`Uri uri = new Uri("pack://siteoforigin:,,,/Subfolder/SOOFile.xaml", UriKind.Absolute);`|

表4は、を使用し[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]てコードで指定できるさまざまな<xref:System.Uri?displayProperty=nameWithType>相対パックを示しています。

表 4:コード内の相対パック Uri

|ファイル|相対パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|
|----------|-------------------------------------------------------------------------------------------------------------------------|
|リソース ファイル - ローカル アセンブリ|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|
|サブフォルダー内のリソース ファイル - ローカル アセンブリ|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|リソース ファイル - 参照アセンブリ|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|
|サブフォルダー内のリソース ファイル - 参照アセンブリ|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|
|コンテンツ ファイル|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|
|サブフォルダー内のコンテンツ ファイル|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|

<a name="Common_Pack_URI_Scenarios"></a>

### <a name="common-pack-uri-scenarios"></a>一般的なパック URI のシナリオ

前のセクションでは、リソース、コンテンツ[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] 、および起点サイトファイルを識別するためにパックを構築する方法について説明しました。 で[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]は、これらの構造はさまざまな方法で使用されます。次のセクションでは、いくつかの一般的な使用方法について説明します。

<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>

#### <a name="specifying-the-ui-to-show-when-an-application-starts"></a>アプリケーションの起動時に表示する UI の指定

<xref:System.Windows.Application.StartupUri%2A>アプリケーションが起動[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]されたときに表示する最初のを指定します。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] スタンドアロンアプリケーションの場合[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]は、次の例に示すように、をウィンドウにすることができます。

[!code-xaml[PackURIOverviewSnippets#StartupUriWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]

スタンドアロンアプリケーション[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]とでは、次の例に示すように、初期 UI としてページを指定することもできます。

[!code-xaml[PackURIOverviewSnippets#StartupUriPage](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]

アプリケーションがスタンドアロンアプリケーションであり、で<xref:System.Windows.Application.StartupUri%2A>ページが指定されている場合、 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]はを開き<xref:System.Windows.Navigation.NavigationWindow> 、ページをホストします。 の[!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]場合、ページはホストブラウザーに表示されます。

<a name="Navigating_to_a_Page"></a>

#### <a name="navigating-to-a-page"></a>ページへのナビゲート

次の例は、ページにナビゲートする方法を示しています。

[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]

移動[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]するさまざまな方法の詳細については、「[ナビゲーションの概要](navigation-overview.md)」を参照してください。

<a name="Specifying_a_Window_Icon"></a>

#### <a name="specifying-a-window-icon"></a>ウィンドウ アイコンの指定

次の例は、URI を使用してウィンドウのアイコンを指定する方法を示しています。

[!code-xaml[WindowIconSnippets#WindowIconSetXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]

詳細については、「 <xref:System.Windows.Window.Icon%2A> 」を参照してください。

<a name="Loading_Image__Audio__and_Video_Files"></a>

#### <a name="loading-image-audio-and-video-files"></a>イメージ ファイル、オーディオ ファイル、およびビデオ ファイルの読み込み

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]では、次の例に示すように、アプリケーションでさまざまな種類のメディアを使用し[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]て、そのすべてを特定し、パックで読み込むことができます。

[!code-xaml[MediaPlayerVideoSample#VideoPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]

[!code-xaml[MediaPlayerAudioSample#AudioPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]

[!code-xaml[ImageSample#ImagePackURIContent](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]

メディアコンテンツの操作の詳細については、「[グラフィックスとマルチメディア](../graphics-multimedia/index.md)」を参照してください。

<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>

#### <a name="loading-a-resource-dictionary-from-the-site-of-origin"></a>起点サイトからのリソース ディクショナリの読み込み

リソースディクショナリ (<xref:System.Windows.ResourceDictionary>) は、アプリケーションテーマをサポートするために使用できます。 テーマを作成し、管理する方法の 1 つは、複数のテーマをリソース ディクショナリとして作成して、アプリケーションの起点サイトに配置することです。 これにより、アプリケーションを再コンパイルして再配置しなくても、テーマの追加と交信が可能です。 これらのリソースディクショナリは、次の例に[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]示すように、pack を使用して識別および読み込むことができます。

[!code-xaml[ResourceDictionarySnippets#ResourceDictionaryPackURI](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]

のテーマ[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]の概要については、「[スタイルとテンプレート](../controls/styling-and-templating.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [WPF アプリケーションのリソース ファイル、コンテンツ ファイル、およびデータ ファイル](wpf-application-resource-content-and-data-files.md)
