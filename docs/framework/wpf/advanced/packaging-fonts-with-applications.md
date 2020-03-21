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
ms.openlocfilehash: cef2ae26ec4fccd25ca193ba7d441969f36b25a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187087"
---
# <a name="packaging-fonts-with-applications"></a>アプリケーションでのフォントのパッケージング
このトピックでは、アプリケーションでフォントをパッケージ化する方法[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]の概要を説明します。  
  
> [!NOTE]
> 多くの種類のソフトウェアと同様に、フォント ファイルは、販売されるのではなくライセンスされます。 フォントの使用を管理するライセンスは、ベンダによって異なりますが、一般的に、Microsoft がアプリケーションや Windows で提供するフォントをカバーするライセンスを含むほとんどのライセンスでは、フォントをアプリケーションに埋め込んだり、再配布したりすることはできません。 したがって、開発者としては、フォントをアプリケーション内に埋め込む場合や別の方法でフォントを再頒布する場合、それらフォントに必要なライセンス権限を取得する責任があります。  

<a name="introduction_to_packaging_fonts"></a>
## <a name="introduction-to-packaging-fonts"></a>フォントのパッケージングの概要  
 フォントを[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーション内のリソースとして簡単にパッケージ化して、ユーザー インターフェイステキストやその他の種類のテキスト ベースのコンテンツを表示できます。 フォントは、アプリケーションのアセンブリ ファイルと別にすることも、その中に埋め込むこともできます。 アプリケーションから参照できる、リソース専用のフォント ライブラリを作成することもできます。  
  
 OpenType および TrueType® フォントには、フォントのフォント埋め込みライセンス権を示す型フラグ fsType が含まれています。 しかし、この型フラグはドキュメントに格納された埋め込みフォントのみを参照し、アプリケーションに埋め込まれたフォントは参照しません。 オブジェクトを作成し、その<xref:System.Windows.Media.GlyphTypeface><xref:System.Windows.Media.GlyphTypeface.EmbeddingRights%2A>プロパティを参照することで、フォントのフォント埋め込み権限を取得できます。 fsType フラグの詳細については[、OpenType 仕様](https://www.microsoft.com/typography/otspec/os2.htm)の「OS/2 および Windows メトリック」セクションを参照してください。  
  
 [Microsoft のタイポグラフィ](https://docs.microsoft.com/typography/)Web サイトには、特定のフォント ベンダを検索したり、カスタム作業用のフォント ベンダを検索したりするのに役立つ連絡先情報が含まれています。  
  
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
  
 アプリケーションが実行時にフォントを使用できるようにするには、アプリケーションの展開ディレクトリでフォントをアクセス可能にする必要があります。 アプリケーション`<CopyToOutputDirectory>`のプロジェクト ファイル内の要素を使用すると、ビルドプロセス中に自動的にフォントをアプリケーション配置ディレクトリにコピーできます。 展開ディレクトリにフォントをコピーする方法を次のプロジェクト ファイル例に示します。  
  
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
> フォントをリソースとしてアプリケーションに追加する場合は、アプリケーションの`<Resource>`プロジェクト ファイルの要素ではなく、要素`<EmbeddedResource>`を設定していることを確認してください。 ビルド`<EmbeddedResource>`アクションの要素はサポートされていません。  
  
 アプリケーションのフォント リソースを参照する方法を次のマークアップ例に示します。  
  
 [!code-xaml[FontSnippets#FontPackageSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml#fontpackagesnippet1)]  
  
### <a name="referencing-font-resource-items-from-code"></a>コードからのフォント リソース項目の参照  
 コードからフォント リソース項目を参照するには、2 つの部分から構成されるフォント リソース参照 (基本統一リソース識別子 (URI) を指定する必要があります。フォントの場所の参照を指定します。 これらの値は、<xref:System.Windows.Media.FontFamily.%23ctor%2A>メソッドのパラメーターとして使用されます。 プロジェクト サブディレクトリ内のアプリケーションのフォント リソースを参照する方法を次のコード例に`resources`示します。  
  
 [!code-csharp[FontSnippets#FontPackageSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontPackageSnippets.xaml.cs#fontpackagesnippet2)]
 [!code-vb[FontSnippets#FontPackageSnippet2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontpackagesnippets.xaml.vb#fontpackagesnippet2)]  
  
 基本統一リソース識別子 (URI) には、フォント リソースが存在するアプリケーション サブディレクトリを含めることができます。 この場合、フォントの場所の参照はディレクトリを指定する必要はありませんが、フォント リソースがベースユニフォーム`./`リソース識別子 (URI) で指定されたディレクトリと同じディレクトリ内にあることを示す先頭の " " を含める必要があります。 次のコード例は、フォント リソース項目を参照する別の方法を示しています。これは前のコード例と同等です。  
  
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
 アプリケーションでフォントをリソース項目として列挙するには、 または<xref:System.Windows.Media.Fonts.GetFontFamilies%2A><xref:System.Windows.Media.Fonts.GetTypefaces%2A>メソッドを使用します。 <xref:System.Windows.Media.Fonts.GetFontFamilies%2A>メソッドを使用して、アプリケーションフォントの場所からオブジェクトのコレクションを<xref:System.Windows.Media.FontFamily>返す方法を次の例に示します。 ここでは、アプリケーションに "resources" という名前のサブディレクトリが含まれています。  
  
 [!code-csharp[FontSnippets#FontsSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/FontSnippets/CSharp/FontFamilySnippets.xaml.cs#fontssnippet3)]
 [!code-vb[FontSnippets#FontsSnippet3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FontSnippets/visualbasic/fontfamilysnippets.xaml.vb#fontssnippet3)]  
  
 <xref:System.Windows.Media.Fonts.GetTypefaces%2A>メソッドを使用して、アプリケーションフォントの場所からオブジェクトのコレクションを<xref:System.Windows.Media.Typeface>返す方法を次の例に示します。 ここでは、アプリケーションに "resources" という名前のサブディレクトリが含まれています。  
  
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
> この SDK には、アプリケーションで[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]使用できる OpenType フォントのサンプル セットが含まれています。 フォントはリソース専用ライブラリで定義されています。 詳細については、「[OpenType フォント パックのサンプル](sample-opentype-font-pack.md)」を参照してください。  
  
<a name="limitations_on_font_usage"></a>
## <a name="limitations-on-font-usage"></a>フォントの使用に関する制限事項  
 以下のリストでは、アプリケーションでのフォントのパッケージ化と使用に関[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]するいくつかの制限事項について説明します。  
  
- **フォント埋め込みアクセス許可ビット:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションはフォント埋め込みアクセス許可ビットのチェックも確認もしません。 詳細については[、「Introduction_to_Packingフォント](#introduction_to_packaging_fonts)」セクションを参照してください。  
  
- **原産地フォント:**[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションは、http または ftp の統一リソース識別子 (URI) へのフォント参照を許可しません。  
  
- **パックを使用する絶対 URI: 表記:**[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションでは、フォントへの<xref:System.Windows.Media.FontFamily>絶対統一リソース識別子 (URI) 参照の一部として "pack:" を使用して、プログラムでオブジェクトを作成することはできません。 たとえば、`"pack://application:,,,/resources/#Pericles Light"`無効なフォント参照です。  
  
- **自動フォント埋め込み:** デザイン時に、アプリケーションのフォントの使用を検索したり、アプリケーションのリソースにフォントを自動的に埋め込んだりすることはサポートされていません。  
  
- **フォント サブセット:** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションでは、固定ドキュメント以外でフォント サブセットの作成はサポートされていません。  
  
- 正しくない参照がある場合、アプリケーションは使用可能なフォントの使用に戻ります。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Documents.Typography>
- <xref:System.Windows.Media.FontFamily>
- [Microsoft Typography: Links, News, and Contacts (Microsoft タイポグラフィ: リンク、ニュース、連絡先)](https://docs.microsoft.com/typography/)
- [OpenType の仕様](https://www.microsoft.com/typography/otspec/)
- [OpenType フォントの機能](opentype-font-features.md)
- [OpenType フォント パックのサンプル](sample-opentype-font-pack.md)
