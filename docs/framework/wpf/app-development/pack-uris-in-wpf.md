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
ms.openlocfilehash: 9e7ded2869e3553eab302e150d80608b8dd7091f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377317"
---
# <a name="pack-uris-in-wpf"></a>WPF におけるパッケージの URI
Windows Presentation Foundation (WPF) では、[!INCLUDE[TLA#tla_uri#plural](../../../../includes/tlasharptla-urisharpplural-md.md)]を識別し、次を含む、さまざまな方法でファイルを読み込むために使用します。  
  
-   指定する、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]を表示するときに、アプリケーションを初めて起動します。  
  
-   イメージの読み込み。  
  
-   ページへの移動。  
  
-   実行可能でないデータ ファイルの読み込み。  
  
 さらに、[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]を識別し、さまざまななど、次の場所からファイルを読み込むために使用できます。  
  
-   現在のアセンブリ。  
  
-   参照アセンブリ。  
  
-   アセンブリに対して相対的な位置。  
  
-   アプリケーションの起点サイト。  
  
 識別し、これらの場所からこの種のファイルを読み込むのため、一貫性のあるメカニズムを提供する[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]の拡張性を活用して、*パック URI スキーム*します。 このトピックでは、スキームの概要を説明します、パックを構築する方法について説明します[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]さまざまなシナリオ、絶対および相対について説明します[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]と[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]パックを使用する方法を表示する前に、解像度[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]両方マークアップからコード。  
  
  
<a name="The_Pack_URI_Scheme"></a>   
## <a name="the-pack-uri-scheme"></a>パック URI スキーム  
 パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]スキームを使って、 [Open Packaging Conventions](https://go.microsoft.com/fwlink/?LinkID=71255) (OPC) 仕様は、整理、およびコンテンツを識別するためのモデルについて説明します。 このモデルの主要な要素には、パッケージとパーツ、場所、*パッケージ*論理的なコンテナーは、1 つまたは複数の論理*パーツ*します。 この概念を次の図に示します。  
  
 ![パッケージとパーツのダイアグラム](./media/wpfpackurischemefigure1.PNG "WPFPackURISchemeFigure1")  
  
 パーツを識別するために、OPC 仕様は RFC 2396 の拡張性を利用 (Uniform Resource Identifier (URI)。ジェネリックの構文)、パックを定義する[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]スキーム。  
  
 指定されたスキーム、[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]そのプレフィックスによって定義されます http、ftp、ファイルはよく知られている例です。 パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]スキーム、スキームとして"pack"を使用して、2 つのコンポーネントが含まれています: オーソリティとパス。 パックの形式は[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]します。  
  
 pack://*機関*/*パス*
  
 *機関*によって、一部が含まれているパッケージの種類を指定します。 中に、*パス*パッケージ内のパーツの場所を指定します。  
  
 この概念を次の図に示します。  
  
 ![パッケージ、オーソリティ、およびパスの関係](./media/wpfpackurischemefigure2.PNG "WPFPackURISchemeFigure2")  
  
 パッケージとパーツは、アプリケーションとファイルに似ています。つまり、アプリケーション (パッケージ) は、次のような 1 つ以上のファイル (パーツ) を含むことができます。  
  
-   ローカル アセンブリにコンパイルされるリソース ファイル。  
  
-   参照センブリにコンパイルされるリソース ファイル。  
  
-   参照元センブリにコンパイルされるリソース ファイル。  
  
-   コンテンツ ファイル。  
  
-   起点サイト ファイル。  
  
 これらの種類のファイルにアクセスする[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]2 つのオーソリティをサポートしています: application:///と siteoforigin:///。 application:/// オーソリティは、リソース ファイルやコンテンツ ファイルなど、コンパイル時に既知のアプリケーション データ ファイルを識別します。 siteoforigin:/// オーソリティは、起点サイト ファイルを識別します。 各オーソリティのスコープを次の図に示します。  
  
 ![パック URI のダイアグラム](./media/wpfpackurischemefigure4.png "WPFPackURISchemeFigure4")  
  
> [!NOTE]
>  パックの権限を持つコンポーネント[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]が埋め込まれた[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]パッケージを指すこと、および RFC 2396 に準拠する必要があります。 さらに、"/" 文字は "," 文字に置き換える必要があり、"%" や "?" などの予約文字はエスケープする必要があります。 詳細については、OPC を参照してください。  
  
 次のセクションでは、パックを作成する方法を説明する[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]リソース、コンテンツ、および起点サイト ファイルを識別するための適切なパスと組み合わせてこれら 2 つのオーソリティを使用します。  
  
<a name="Resource_File_Pack_URIs___Local_Assembly"></a>   
## <a name="resource-file-pack-uris"></a>リソース ファイルのパック URI  
 リソース ファイルとして構成されている[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Resource`項目し、アセンブリにコンパイルされます。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] パックの構築をサポート[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]は、ローカル アセンブリにコンパイルされたか、ローカル アセンブリから参照されるアセンブリにコンパイルされるリソース ファイルを識別するために使用できます。  
  
<a name="Local_Assembly_Resource_File"></a>   
### <a name="local-assembly-resource-file"></a>ローカル アセンブリ リソース ファイル  
 パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]次のオーソリティとパスのリソースに対して、ローカル アセンブリにコンパイルされたファイルを使用します。  
  
-   **オーソリティ**: application:///。  
  
-   **パス**:ローカル アセンブリのプロジェクト フォルダーのルートに対する相対パスを含むリソース ファイルの名前。  
  
 次の例は、パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]の[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ローカル アセンブリのプロジェクト フォルダーのルートに配置されているリソース ファイル。  
  
 `pack://application:,,,/ResourceFile.xaml`  
  
 次の例は、パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]の[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ローカル アセンブリのプロジェクト フォルダーのサブフォルダーに配置されているリソース ファイル。  
  
 `pack://application:,,,/Subfolder/ResourceFile.xaml`  
  
<a name="Resource_File_Pack_URIs___Referenced_Assembly"></a>   
### <a name="referenced-assembly-resource-file"></a>参照アセンブリ リソース ファイル  
 パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]次のオーソリティとパスには、リソースの参照アセンブリにコンパイルされたファイルを使用します。  
  
-   **オーソリティ**: application:///。  
  
-   **パス**:参照先アセンブリにコンパイルされるリソース ファイルの名前。 パスは、次の書式に従う必要があります。  
  
     *AssemblyShortName*{*;バージョン*] {*;公開鍵*]; component/*パス*  
  
    -   **AssemblyShortName**: 参照アセンブリの短い名前。  
  
    -   **;Version** (省略可能): リソース ファイルを含む参照アセンブリのバージョン。 これは、同じ短い名前を持つ 2 つ以上の参照アセンブリが読み込まれるときに使用されます。  
  
    -   **;PublicKey** (省略可能): 参照アセンブリの署名に使用された公開鍵。 これは、同じ短い名前を持つ 2 つ以上の参照アセンブリが読み込まれるときに使用されます。  
  
    -   **;component**: 参照されるアセンブリが、ローカル アセンブリから参照されることを指定します。  
  
    -   **/Path**: 参照アセンブリのプロジェクト フォルダーのルートに対して相対的なパスを含むリソース ファイルの名前。  
  
 次の例は、パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]の[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]参照アセンブリのプロジェクト フォルダーのルートに配置されているリソース ファイル。  
  
 `pack://application:,,,/ReferencedAssembly;component/ResourceFile.xaml`  
  
 次の例は、パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]の[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]参照アセンブリのプロジェクト フォルダーのサブフォルダーに配置されているリソース ファイル。  
  
 `pack://application:,,,/ReferencedAssembly;component/Subfolder/ResourceFile.xaml`  
  
 次の例は、パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]の[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、バージョン固有の参照先アセンブリのプロジェクト フォルダーのルート フォルダーにあるリソース ファイル。  
  
 `pack://application:,,,/ReferencedAssembly;v1.0.0.1;component/ResourceFile.xaml`  
  
 なお、パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]参照アセンブリ リソース ファイルの構文は、アプリケーションでのみ使用できます:///オーソリティします。 たとえば、次はサポートされていませんで[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]します。  
  
 `pack://siteoforigin:,,,/SomeAssembly;component/ResourceFile.xaml`  
  
<a name="Content_File_Pack_URIs"></a>   
## <a name="content-file-pack-uris"></a>コンテンツ ファイルのパック URI  
 パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]コンテンツ ファイルは、次のオーソリティとパスを使用します。  
  
-   **オーソリティ**: application:///。  
  
-   **パス**:アプリケーションのメイン実行可能アセンブリのファイル システムの場所からの相対パスを含む、コンテンツ ファイルの名前。  
  
 次の例は、パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]の[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]コンテンツ ファイル、実行可能アセンブリと同じフォルダーに配置します。  
  
 `pack://application:,,,/ContentFile.xaml`  
  
 次の例は、パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]の[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]コンテンツ ファイル、アプリケーションの実行可能アセンブリに対して相対的なサブフォルダーにあります。  
  
 `pack://application:,,,/Subfolder/ContentFile.xaml`  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)] コンテンツ ファイルにナビゲートすることはできません。 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]スキームのみへのナビゲーションをサポートする[!INCLUDE[TLA2#tla_html](../../../../includes/tla2sharptla-html-md.md)]起点サイトにあるファイル。  
  
<a name="The_siteoforigin_____Authority"></a>   
## <a name="site-of-origin-pack-uris"></a>起点サイトのパック URI  
 パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]次のオーソリティとパスの起点サイト ファイルを使用します。  
  
-   **オーソリティ**: siteoforigin:///。  
  
-   **パス**:実行可能アセンブリの起動元の場所からの相対パスを含む、配信元のファイルのサイトの名前。  
  
 次の例は、パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]の[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]起点サイト ファイル、実行可能アセンブリの起動元の場所に保存します。  
  
 `pack://siteoforigin:,,,/SiteOfOriginFile.xaml`  
  
 次の例は、パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]の[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]起点サイト ファイル、アプリケーションの実行可能アセンブリの起動元の位置に対して相対的なサブフォルダーに格納されています。  
  
 `pack://siteoforigin:,,,/Subfolder/SiteOfOriginFile.xaml`  
  
<a name="Page_Files"></a>   
## <a name="page-files"></a>ページ ファイル  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] として構成されているファイル[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page`項目は、リソース ファイルと同じ方法でアセンブリにコンパイルされます。 その結果、 [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `Page`パックを使用して項目を識別できます[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]リソース ファイル。  
  
 種類の[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]として一般的に構成されているファイル[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]`Page`がルート要素として次のいずれかの項目があります。  
  
-   <xref:System.Windows.Window?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Page?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Navigation.PageFunction%601?displayProperty=nameWithType>  
  
-   <xref:System.Windows.ResourceDictionary?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Documents.FlowDocument?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.UserControl?displayProperty=nameWithType>  
  
<a name="Absolute_vs_Relative_Pack_URIs"></a>   
## <a name="absolute-vs-relative-pack-uris"></a>絶対および相対パック URI  
 完全修飾されたパック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]スキーム、権限、および、パスが含まれています、絶対パックと見なされます[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]します。 開発者は、簡略化したものとして[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]要素の相対パックを適切な属性を設定することにより通常[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]、パスのみが含まれます。  
  
 たとえば、次のような絶対パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]ローカル アセンブリ内のリソース ファイル。  
  
 `pack://application:,,,/ResourceFile.xaml`  
  
 相対パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]はこのリソースを参照するファイルは、次になります。  
  
 `/ResourceFile.xaml`  
  
> [!NOTE]
>  起点サイト ファイルがアセンブリに関連付けられていないため、それらのみ参照できます絶対パック[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]します。  
  
 既定では、相対パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]マークアップまたは参照を含むコードの位置を基準と見なされます。 先頭にバック スラッシュを使用する場合のただし、相対パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]参照がそのアプリケーションのルートを基準と見なされます。 たとえば、次のようなプロジェクト構造を考えてみます。  
  
 `App.xaml`  
  
 `Page2.xaml`  
  
 `\SubFolder`  
  
 `+ Page1.xaml`  
  
 `+ Page2.xaml`  
  
 Page1.xaml が含まれている場合、[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]を参照する*ルート*\SubFolder\Page2.xaml、参照は、次のような相対パックを使用できます[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]します。  
  
 `Page2.xaml`  
  
 Page1.xaml が含まれている場合、[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]を参照する*ルート*\Page2.xaml、参照は、次のような相対パックを使用できます[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]します。  
  
 `/Page2.xaml`  
  
<a name="Pack_URI_Resolution"></a>   
## <a name="pack-uri-resolution"></a>パック URI の解決  
 パックの形式[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]可能パック[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]さまざまな種類のファイルを同じになります。 たとえば、次のような絶対パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]します。  
  
 `pack://application:,,,/ResourceOrContentFile.xaml`  
  
 この絶対パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]でした、ローカル アセンブリにリソース ファイルまたはコンテンツ ファイルを参照してください。 これは次の相対当てはまります[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]します。  
  
 `/ResourceOrContentFile.xaml`  
  
 決定するために、ファイルの種類をパック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]が参照する[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]解決[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]ローカル アセンブリと、次のヒューリスティックを使用して、コンテンツ ファイルのリソース ファイルの。  
  
1.  プローブのアセンブリのメタデータ、 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> 、パックと一致する属性[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]します。  
  
2.  場合、<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>属性が見つかると、パックのパス[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]はコンテンツ ファイルを参照します。  
  
3.  場合、<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>属性が見つからない場合は、ローカル アセンブリにコンパイルされる設定リソース ファイルをプローブします。  
  
4.  場合、パックのパスに一致するリソース ファイル[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]が見つかると、パックのパス[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]はリソース ファイルを参照します。  
  
5.  リソースが見つからない場合、内部で作成された<xref:System.Uri>が無効です。  
  
 [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] 解決は適用されない[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]するには、次を参照してください。  
  
-   参照されたアセンブリ内のコンテンツ ファイル: では、これらのファイルの種類はサポートされていない[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]します。  
  
-   参照されたアセンブリ内の埋め込みファイル:[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]これらを識別する参照アセンブリの名前の両方を含めるためには、一意と`;component`サフィックス。  
  
-   起点サイト ファイル:[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]これらを識別するパックによって識別できるファイルのみであるために、固有[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]を含む、siteoforigin:///オーソリティします。  
  
 パックの 1 つの単純化[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]解決によって、リソースやコンテンツ ファイルの場所に依存するコードです。 たとえば、コンテンツ ファイルをパックするように再構成するローカル アセンブリ内のリソース ファイルがある場合[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]は、パックを使用するコードも同じですが、リソースは[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]します。  
  
<a name="Programming_with_Pack_URIs"></a>   
## <a name="programming-with-pack-uris"></a>パック URI を使用したプログラミング  
 多く[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]パックで設定できるプロパティを実装するクラス[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]など。  
  
-   <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Frame.Source%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Navigation.NavigationWindow.Source%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Documents.Hyperlink.NavigateUri%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Window.Icon%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.Controls.Image.Source%2A?displayProperty=nameWithType>  
  
 これらのプロパティは、マークアップとコードのどちらからでも設定できます。 このセクションでは、両方の基本構造について説明してから、一般的なシナリオの例を示します。  
  
<a name="Using_Pack_URIs_in_Markup"></a>   
### <a name="using-pack-uris-in-markup"></a>マークアップでのパック URI の使用  
 パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]、パックを使用して属性の要素を設定してマークアップで指定[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]します。 例:  
  
 `<element attribute="pack://application:,,,/File.xaml" />`  
  
 表 1 は、さまざまな絶対パックを示しています。[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]マークアップで指定することができます。  
  
 表 1:マークアップで絶対パック Uri  
  
|ファイル|絶対パック [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
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
  
 表 2 は、さまざまな相対パックを示しています。[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]マークアップで指定することができます。  
  
 表 2:マークアップで相対パック Uri  
  
|ファイル|相対パック [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|ローカル アセンブリ内のリソース ファイル|`"/ResourceFile.xaml"`|  
|ローカル アセンブリのサブフォルダー内のリソース ファイル|`"/Subfolder/ResourceFile.xaml"`|  
|参照アセンブリ内のリソース ファイル|`"/ReferencedAssembly;component/ResourceFile.xaml"`|  
|参照アセンブリのサブフォルダー内のリソース ファイル|`"/ReferencedAssembly;component/Subfolder/ResourceFile.xaml"`|  
|コンテンツ ファイル|`"/ContentFile.xaml"`|  
|サブフォルダー内のコンテンツ ファイル|`"/Subfolder/ContentFile.xaml"`|  
  
<a name="Using_Pack_URIs_in_Code"></a>   
### <a name="using-pack-uris-in-code"></a>コードでのパック URI の使用  
 パックを指定する[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]をインスタンス化するコードの中で、<xref:System.Uri>クラスと、パックを渡す[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]コンス トラクターにパラメーターとして。 このコード例を次に示します。  
  
```csharp  
Uri uri = new Uri("pack://application:,,,/File.xaml");  
```  
  
 既定で、<xref:System.Uri>クラスが考慮パック[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]を絶対です。 インスタンスとその結果、例外が発生、<xref:System.Uri>相対パックのクラスが作成される[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]します。  
  
```csharp  
Uri uri = new Uri("/File.xaml");  
```  
  
 幸いにも、<xref:System.Uri.%23ctor%28System.String%2CSystem.UriKind%29>のオーバー ロード、<xref:System.Uri>クラスのコンス トラクターが型のパラメーターを受け取る<xref:System.UriKind>指定することを許可するかどうか、パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]が絶対か相対。  
  
```csharp  
// Absolute URI (default)  
Uri absoluteUri = new Uri("pack://application:,,,/File.xaml", UriKind.Absolute);  
// Relative URI  
Uri relativeUri = new Uri("/File.xaml",   
                        UriKind.Relative);  
```  
  
 のみを指定する必要があります<xref:System.UriKind.Absolute>または<xref:System.UriKind.Relative>が特定される、指定されたパック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]はどちらか一方です。 パックの種類がわからない場合[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]など、ユーザーがパッケージに入ったとき、使用される[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]、実行時に使用<xref:System.UriKind.RelativeOrAbsolute>代わりにします。  
  
```csharp  
// Relative or Absolute URI provided by user via a text box  
TextBox userProvidedUriTextBox = new TextBox();  
Uri uri = new Uri(userProvidedUriTextBox.Text, UriKind.RelativeOrAbsolute);  
```  
  
 表 3 は、さまざまな相対パックを示しています。[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]を使用してコードで指定できる<xref:System.Uri?displayProperty=nameWithType>します。  
  
 表 3:コードでの絶対パック Uri  
  
|ファイル|絶対パック [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
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
  
 表 4 は、さまざまな相対パックを示しています。[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]を使用してコードで指定できる<xref:System.Uri?displayProperty=nameWithType>します。  
  
 表 4:コード内の相対パック Uri  
  
|ファイル|相対パック [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]|  
|----------|-------------------------------------------------------------------------------------------------------------------------|  
|リソース ファイル - ローカル アセンブリ|`Uri uri = new Uri("/ResourceFile.xaml", UriKind.Relative);`|  
|サブフォルダー内のリソース ファイル - ローカル アセンブリ|`Uri uri = new Uri("/Subfolder/ResourceFile.xaml", UriKind.Relative);`|  
|リソース ファイル - 参照アセンブリ|`Uri uri = new Uri("/ReferencedAssembly;component/ResourceFile.xaml", UriKind.Relative);`|  
|サブフォルダー内のリソース ファイル - 参照アセンブリ|`Uri uri = new Uri("/ReferencedAssembly;component/Subfolder/ResourceFile.xaml", UriKind.Relative);`|  
|コンテンツ ファイル|`Uri uri = new Uri("/ContentFile.xaml", UriKind.Relative);`|  
|サブフォルダー内のコンテンツ ファイル|`Uri uri = new Uri("/Subfolder/ContentFile.xaml", UriKind.Relative);`|  
  
<a name="Common_Pack_URI_Scenarios"></a>   
### <a name="common-pack-uri-scenarios"></a>一般的なパック URI のシナリオ  
 前のセクションでは、パックを作成する方法を説明して[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]リソース、コンテンツ、および起点サイト ファイルを識別するためにします。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]さまざまな方法でこのような構築を使用し、次のセクションでは、いくつかの一般的な使用法をについて説明します。  
  
<a name="Specifying_the_UI_to_Show_when_an_Application_Starts"></a>   
#### <a name="specifying-the-ui-to-show-when-an-application-starts"></a>アプリケーションの起動時に表示する UI の指定  
 <xref:System.Windows.Application.StartupUri%2A> 1 つ目を指定します[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]に表示する、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]アプリケーションが起動します。 スタンドアロン アプリケーションの場合、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]次の例に示すように、ウィンドウにすることができます。  
  
 [!code-xaml[PackURIOverviewSnippets#StartupUriWindow](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/Copy of App.xaml#startupuriwindow)]  
  
 スタンドアロン アプリケーションと[!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)]次の例に示すように、最初の UI としてページを指定もできます。  
  
 [!code-xaml[PackURIOverviewSnippets#StartupUriPage](~/samples/snippets/csharp/VS_Snippets_Wpf/PackURIOverviewSnippets/CS/App.xaml#startupuripage)]  
  
 かどうか、アプリケーションは、スタンドアロン アプリケーションと、ページを指定した<xref:System.Windows.Application.StartupUri%2A>、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]開きます、<xref:System.Windows.Navigation.NavigationWindow>ページをホストします。 [!INCLUDE[TLA2#tla_xbap#plural](../../../../includes/tla2sharptla-xbapsharpplural-md.md)]ページは、ホスト ブラウザーに表示します。  
  
<a name="Navigating_to_a_Page"></a>   
#### <a name="navigating-to-a-page"></a>ページへのナビゲート  
 次の例は、ページにナビゲートする方法を示しています。  
  
 [!code-xaml[NavigationOverviewSnippets#HyperlinkXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml1)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml2)]  
[!code-xaml[NavigationOverviewSnippets#HyperlinkXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/NavigationOverviewSnippets/CSharp/PageWithHyperlink.xaml#hyperlinkxaml3)]  
  
 内で移動するさまざまな方法の詳細については[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]を参照してください[ナビゲーションの概要](navigation-overview.md)します。  
  
<a name="Specifying_a_Window_Icon"></a>   
#### <a name="specifying-a-window-icon"></a>ウィンドウ アイコンの指定  
 次の例は、URI を使用してウィンドウのアイコンを指定する方法を示しています。  
  
 [!code-xaml[WindowIconSnippets#WindowIconSetXAML](~/samples/snippets/xaml/VS_Snippets_Wpf/WindowIconSnippets/XAML/MainWindow.xaml#windowiconsetxaml)]  
  
 詳細については、「 <xref:System.Windows.Window.Icon%2A> 」を参照してください。  
  
<a name="Loading_Image__Audio__and_Video_Files"></a>   
#### <a name="loading-image-audio-and-video-files"></a>イメージ ファイル、オーディオ ファイル、およびビデオ ファイルの読み込み  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] により、アプリケーションを使用して、さまざまなメディアの種類、これらはすべてを識別してパックに読み込まれる[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]次の例のようにします。  
  
 [!code-xaml[MediaPlayerVideoSample#VideoPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerVideoSample/CS/HomePage.xaml#videopackuriatsoo)]  
  
 [!code-xaml[MediaPlayerAudioSample#AudioPackURIAtSOO](~/samples/snippets/csharp/VS_Snippets_Wpf/MediaPlayerAudioSample/CS/HomePage.xaml#audiopackuriatsoo)]  
  
 [!code-xaml[ImageSample#ImagePackURIContent](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageSample/CS/HomePage.xaml#imagepackuricontent)]  
  
 メディア コンテンツの操作方法の詳細については、次を参照してください。[グラフィックスとマルチ メディア](../graphics-multimedia/index.md)します。  
  
<a name="Loading_a_Resource_Dictionary_from_the_Site_of_Origin"></a>   
#### <a name="loading-a-resource-dictionary-from-the-site-of-origin"></a>起点サイトからのリソース ディクショナリの読み込み  
 リソース ディクショナリ (<xref:System.Windows.ResourceDictionary>) アプリケーションのテーマをサポートするために使用できます。 テーマを作成し、管理する方法の 1 つは、複数のテーマをリソース ディクショナリとして作成して、アプリケーションの起点サイトに配置することです。 これにより、アプリケーションを再コンパイルして再配置しなくても、テーマの追加と交信が可能です。 これらのリソース ディクショナリを特定でき、pack を使用して読み込む[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]、次の例を示します。  
  
 [!code-xaml[ResourceDictionarySnippets#ResourceDictionaryPackURI](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceDictionarySnippets/CS/App.xaml#resourcedictionarypackuri)]  
  
 テーマの概要について[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]を参照してください[スタイルとテンプレート](../controls/styling-and-templating.md)します。  
  
## <a name="see-also"></a>関連項目
- [WPF アプリケーションのリソース ファイル、コンテンツ ファイル、およびデータ ファイル](wpf-application-resource-content-and-data-files.md)
