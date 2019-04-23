---
title: アプリケーションでのフォントのパッケージング
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applications [WPF], packaging fonts with
- fonts [WPF], packaging with applications
- typography [WPF], packaging fonts with applications
- packaging fonts with applications [WPF]
ms.assetid: db15ee48-4d24-49f5-8b9d-a64460865286
ms.openlocfilehash: fb91d4b413db512021b90f0d4ba3049fe7333601
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59123799"
---
# <a name="packaging-fonts-with-applications"></a>アプリケーションでのフォントのパッケージング
このトピックでは、フォントをパッケージングする方法の概要を示します、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]アプリケーション。  
  
> [!NOTE]
>  多くの種類のソフトウェアと同様に、フォント ファイルは、販売されるのではなくライセンスされます。 フォントの使用を管理するライセンス異なるベンダーが、一般に、フォントをカバーするものも含め、ほとんどのライセンス[!INCLUDE[TLA#tla_ms#initcap](../../../../includes/tlasharptla-mssharpinitcap-md.md)]連携してアプリケーションと[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]アプリケーション内で埋め込みまたはそれ以外の場合にフォントを許可しません。再配布します。 したがって、開発者としては、フォントをアプリケーション内に埋め込む場合や別の方法でフォントを再頒布する場合、それらフォントに必要なライセンス権限を取得する責任があります。  

<a name="introduction_to_packaging_fonts"></a>   
## <a name="introduction-to-packaging-fonts"></a>フォントのパッケージングの概要  
 内のリソースとしてフォントをパッケージ化することが簡単に、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ベースのアプリケーションにユーザー インターフェイス テキストとその他の種類のテキストを表示するコンテンツ。 フォントは、アプリケーションのアセンブリ ファイルと別にすることも、その中に埋め込むこともできます。 アプリケーションから参照できる、リソース専用のフォント ライブラリを作成することもできます。  
  
 [!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)] [!INCLUDE[TLA#tla_truetype](../../../../includes/tlasharptla-truetype-md.md)]フォントには、型フラグ fsType、フォントのフォント埋め込みライセンス権利を示すが含まれます。 しかし、この型フラグはドキュメントに格納された埋め込みフォントのみを参照し、アプリケーションに埋め込まれたフォントは参照しません。 フォントの埋め込みを作成して、フォントの権限を取得することができます、<xref:System.Windows.Media.GlyphTypeface>オブジェクトとを参照するその<xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A>プロパティ。 「Os/2 と Windows メトリック」セクションを参照してください、 [OpenType の仕様](https://www.microsoft.com/typography/otspec/os2.htm)fsType フラグの詳細についてはします。  
  
 [Microsoft タイポグラフィ](https://docs.microsoft.com/typography/)Web サイトには、特定のフォント ベンダーを検索またはカスタムの作業のフォント ベンダーを検索するのに役立つ連絡先の情報が含まれています。  
  
<a name="adding_fonts_as_content_items"></a>   
## <a name="adding-fonts-as-content-items"></a>コンテンツ項目としてのフォントの追加  
 フォントは、アプリケーションのアセンブリ ファイルとは別のプロジェクト コンテンツ項目としてアプリケーションに追加できます。 つまり、コンテンツ項目はアセンブリ内にリソースとして埋め込まれません。 コンテンツ項目を定義する方法を次のプロジェクト ファイル例に示します。  
  
```xml  
<Project DefaultTargets="Build"  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- Other project build settings ... -->  
  
  <ItemGroup>  
    <Content Include="Peric.ttf" />  
    <Content Include="Pericl.ttf" />  
  </ItemGroup>  
</Project>  
```  
  
 アプリケーションが実行時にフォントを使用できるようにするには、アプリケーションの展開ディレクトリでフォントをアクセス可能にする必要があります。 `<CopyToOutputDirectory>`アプリケーションのプロジェクト ファイル内の要素を使用すると、ビルド プロセス中に、アプリケーションの展開ディレクトリにフォントを自動的にコピーします。 展開ディレクトリにフォントをコピーする方法を次のプロジェクト ファイル例に示します。  
  
```xml  
<ItemGroup>  
  <Content Include="Peric.ttf">  
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>  
  </Content>  
  <Content Include="Pericl.ttf">  
    <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>  
  </Content>  
</ItemGroup>  
```  
  
 次のコード例は、アプリケーションのフォントをコンテンツ項目として参照する方法を示しています。参照されるコンテンツ項目は、アプリケーションのアセンブリ ファイルと同じディレクトリ内に存在する必要があります。  
  
 [!code-xaml[FontSnippets#FontPackageSnippet8](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet8)]  
  
<a name="adding_fonts_as_resource_items"></a>   
## <a name="adding-fonts-as-resource-items"></a>リソース項目としてのフォントの追加  
 フォントは、アプリケーションのアセンブリ ファイルに埋め込まれたプロジェクト リソース項目としてアプリケーションに追加できます。 リソース用として別のサブディレクトリを使用することは、アプリケーションのプロジェクト ファイルの整理に役立ちます。 フォントを別サブディレクトリ内のリソース項目として定義する方法を、次のプロジェクト ファイル例に示します。  
  
```xml  
<Project DefaultTargets="Build"  
                xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <!-- Other project build settings ... -->  
  
  <ItemGroup>  
    <Resource Include="resources\Peric.ttf" />  
    <Resource Include="resources\Pericl.ttf" />  
  </ItemGroup>  
</Project>  
```  
  
> [!NOTE]
>  アプリケーションにリソースとしてフォントを追加するときに設定して確認、`<Resource>`要素、および not、`<EmbeddedResource>`アプリケーションのプロジェクト ファイル内の要素。 `<EmbeddedResource>`ビルド アクションで要素がサポートされていません。  
  
 アプリケーションのフォント リソースを参照する方法を次のマークアップ例に示します。  
  
 [!code-xaml[FontSnippets#FontPackageSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet1)]  
  
### <a name="referencing-font-resource-items-from-code"></a>コードからのフォント リソース項目の参照  
 コードからフォント リソース項目を参照するためには、リソースの参照を 2 つの部分のフォントを指定する必要があります。 基本[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]; とフォントの場所の参照。 これらの値のパラメーターとして使用する、<xref:System.Windows.Media.FontFamily.%23ctor%2A>メソッド。 次のコード例と呼ばれるプロジェクトのサブディレクトリに、アプリケーションのフォント リソースを参照する方法を示しています。`resources`します。  
  
 [!code-csharp[FontSnippets#FontPackageSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet2)]
 [!code-vb[FontSnippets#FontPackageSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet2)]  
  
 基本[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]フォント リソースが存在するアプリケーションのサブディレクトリを含めることができます。 この場合は、フォントの場所の参照はディレクトリを指定する必要はありませんが、主要なを含める必要があります"`./`"、ベースで指定した同じディレクトリには、フォント リソースを示す[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]します。 次のコード例は、フォント リソース項目を参照する別の方法を示しています。これは前のコード例と同等です。  
  
 [!code-csharp[FontSnippets#FontPackageSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet5)]
 [!code-vb[FontSnippets#FontPackageSnippet5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet5)]  
  
### <a name="referencing-fonts-from-the-same-application-subdirectory"></a>同じアプリケーション サブディレクトリからのフォントの参照  
 アプリケーションのコンテンツとリソース ファイルは、アプリケーション プロジェクトのユーザー定義の同じサブディレクトリに配置できます。 同じサブディレクトリで定義されたコンテンツ ページとフォント リソースを次のプロジェクト ファイル例に示します。  
  
```xml  
<ItemGroup>  
  <Page Include="pages\HomePage.xaml" />  
</ItemGroup>  
<ItemGroup>  
  <Resource Include="pages\Peric.ttf" />  
  <Resource Include="pages\Pericl.ttf" />  
</ItemGroup>  
```  
  
 アプリケーション コンテンツとフォントが同じサブディレクトリ内にあるので、フォント参照はアプリケーション コンテンツから見た相対参照となります。 次の例では、フォントがアプリケーションと同じディレクトリ内にある場合にアプリケーションのフォント リソースを参照する方法を示します。  
  
 [!code-xaml[FontSnippets#FontPackageSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml#fontpackagesnippet3)]  
  
 [!code-csharp[FontSnippets#FontPackageSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/pages/HomePage.xaml.cs#fontpackagesnippet4)]
 [!code-vb[FontSnippets#FontPackageSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/pages/homepage.xaml.vb#fontpackagesnippet4)]  
  
### <a name="enumerating-fonts-in-an-application"></a>アプリケーションでのフォントの列挙  
 アプリケーション内のリソース項目としてフォントを列挙するためにいずれかの操作を使用して、<xref:System.Windows.Media.Fonts.GetFontFamilies%2A>または<xref:System.Windows.Media.Fonts.GetTypefaces%2A>メソッド。 次の例は、使用する方法を示します、<xref:System.Windows.Media.Fonts.GetFontFamilies%2A>メソッドのコレクションを返す<xref:System.Windows.Media.FontFamily>アプリケーション フォントの場所からのオブジェクト。 ここでは、アプリケーションに "resources" という名前のサブディレクトリが含まれています。  
  
 [!code-csharp[FontSnippets#FontsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet3)]
 [!code-vb[FontSnippets#FontsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet3)]  
  
 次の例は、使用する方法を示します、<xref:System.Windows.Media.Fonts.GetTypefaces%2A>メソッドのコレクションを返す<xref:System.Windows.Media.Typeface>アプリケーション フォントの場所からのオブジェクト。 ここでは、アプリケーションに "resources" という名前のサブディレクトリが含まれています。  
  
 [!code-csharp[FontSnippets#FontsSnippet7](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet7)]
 [!code-vb[FontSnippets#FontsSnippet7](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet7)]  
  
<a name="creating_a_font_resource_library"></a>   
## <a name="creating-a-font-resource-library"></a>フォント リソース ライブラリの作成  
 フォントのみを含むリソース専用ライブラリを作成できます。この種類のライブラリ プロジェクトにはコードは含まれません。 リソース専用ライブラリの作成は、リソースを使用するアプリケーション コードからリソースを切り離すための一般的な手法です。 また、これにより、複数のアプリケーション プロジェクトでこのライブラリ アセンブリを組み込むことができます。 次のプロジェクト ファイル例に、リソース専用ライブラリ プロジェクトの主要部分を示します。  
  
```xml  
<PropertyGroup>  
  <AssemblyName>FontLibrary</AssemblyName>  
  <OutputType>library</OutputType>  
  ...  
</PropertyGroup>  
...  
<ItemGroup>  
  <Resource Include="Kooten.ttf" />  
  <Resource Include="Pesca.ttf" />  
</ItemGroup  
```  
  
### <a name="referencing-a-font-in-a-resource-library"></a>リソース ライブラリ内のフォントの参照  
 アプリケーションからリソース ライブラリ内のフォントを参照するには、フォント参照の前にライブラリ アセンブリの名前を付加する必要があります。 ここでは、フォント リソース アセンブリは "FontLibrary" です。 アセンブリ名をアセンブリ内の参照と区切るために、';' 文字を使用します。 キーワード "Component" の後にフォント名への参照を続けて追加すると、フォント ライブラリのリソースへの完全参照が完成します。 次のコード例では、リソース ライブラリ アセンブリ内のフォントを参照する方法を示します。  
  
 [!code-xaml[OpenTypeFontsSample#OpenTypeFontsSample1](~/samples/snippets/csharp/VS_Snippets_Wpf/OpenTypeFontsSample/CS/Kootenay.xaml#opentypefontssample1)]  
  
> [!NOTE]
>  この SDK には、一連サンプルにはが含まれています。[!INCLUDE[TLA#tla_opentype](../../../../includes/tlasharptla-opentype-md.md)]で使用できるフォント[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーション。 フォントはリソース専用ライブラリで定義されています。 詳細については、「[OpenType フォント パックのサンプル](sample-opentype-font-pack.md)」をご覧ください。  
  
<a name="limitations_on_font_usage"></a>   
## <a name="limitations-on-font-usage"></a>フォントの使用に関する制限事項  
 次の一覧でフォントの使用、パッケージでいくつかの制限をについて説明します[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーション。  
  
-   **フォント埋め込みアクセス許可ビット:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションはフォント埋め込みアクセス許可ビットのチェックも確認もしません。 参照してください、[フォントのパッケージングの概要](#introduction_to_packaging_fonts)詳細についてはします。  
  
-   **フォントの起点サイト:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションには、http または ftp へのフォント参照は許可しない[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]します。  
  
-   **パックを使用して絶対 URI: 表記:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションでは作成することはできません、<xref:System.Windows.Media.FontFamily>オブジェクトを使用してプログラムで"pack:"、絶対パスの一部として[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]フォントへの参照。 たとえば、`"pack://application:,,,/resources/#Pericles Light"`は無効なフォント参照です。  
  
-   **自動フォント埋め込み:** 設計時に、アプリケーションのフォントの使用を検索して、自動的にアプリケーションのリソースで、フォントの埋め込みのサポートはありません。  
  
-   **フォント サブセット:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションでは、固定ドキュメント以外でフォント サブセットの作成はサポートされていません。  
  
-   正しくない参照がある場合、アプリケーションは使用可能なフォントの使用に戻ります。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Documents.Typography>
- <xref:System.Windows.Media.FontFamily>
- [Microsoft タイポグラフィ:リンク、ニュース、および連絡先](https://docs.microsoft.com/typography/)
- [OpenType の仕様](https://www.microsoft.com/typography/otspec/)
- [OpenType フォントの機能](opentype-font-features.md)
- [OpenType フォント パックのサンプル](sample-opentype-font-pack.md)
