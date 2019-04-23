---
title: WPF アプリケーションのリソース ファイル、コンテンツ ファイル、およびデータ ファイル
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WPF application [WPF], files
- loose resources [WPF]
- content files [WPF]
- Site of Origin files [WPF]
- resource files [WPF]
- remote files [WPF]
- embedded resources [WPF]
- files [WPF]
- referencing application files [WPF]
- application development [WPF], files
- application management [WPF]
ms.assetid: 7ad2943b-3961-41d3-8fc6-1582d43f5d99
ms.openlocfilehash: 075f70e3ef053507dfe3d408246d179bb57c5891
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59211927"
---
# <a name="wpf-application-resource-content-and-data-files"></a>WPF アプリケーションのリソース ファイル、コンテンツ ファイル、およびデータ ファイル
[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] 多くの場合など、非実行可能ファイルのデータを含むファイルに依存するアプリケーション[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]イメージ、ビデオ、およびオーディオです。 Windows Presentation Foundation (WPF) の構成の識別、およびこれらの種類のアプリケーション データ ファイルと呼ばれる、データ ファイルを使用して特別なサポートを提供します。 このサポートの中心となるのは、次のような特定のアプリケーション データ ファイルの種類のセットです。  
  
-   **リソース ファイル**:データ ファイルも実行可能ファイルまたはライブラリにコンパイルされる[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]アセンブリ。  
  
-   **コンテンツ ファイル**:スタンドアロン データ ファイルを実行可能ファイルとの明示的な関連付けを持つ[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]アセンブリ。  
  
-   **起点サイト ファイル**:実行可能ファイルとの関連付けを持たないスタンドアロン データ ファイル[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]アセンブリ。  
  
 これらの 3 種類のファイルの重要な違いは、リソース ファイルとコンテンツ ファイルはビルド時に認識されるという点です。アセンブリは、これらを明確に認識します。 起点サイト ファイル、ただし、アセンブリがありますそれらの知識、またはパックを使用して暗黙的な知識[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]参照。 後者の場合、参照される起点サイト ファイルが実際に存在する保証はありません。  
  
 Windows Presentation Foundation (WPF) が、パックを使用するにはアプリケーション データ ファイルを参照するには、[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]はで詳しく説明されているスキーム[WPF におけるパック Uri](pack-uris-in-wpf.md))。  
  
 このトピックでは、アプリケーション データ ファイルを構成および使用する方法について説明します。  

<a name="Resource_Files"></a>   
## <a name="resource-files"></a>リソース ファイル (Visual Studio)  
 アプリケーション データ ファイルを常にアプリケーションで使用可能にするには、コンパイルしてアプリケーションのメイン実行可能アセンブリまたはその参照アセンブリの 1 つに組み込む必要があります。 この種類のアプリケーション データ ファイルと呼ばれる、*リソース ファイル*します。  
  
 リソース ファイルは、次のときに使用します。  
  
-   コンパイルしてアセンブリに組み込んだ後に、リソース ファイルのコンテンツを更新する必要がない。  
  
-   ファイルの依存関係の数を減らして、アプリケーション配布の複雑さを軽減する必要がある。  
  
-   アプリケーション データ ファイルがローカライズ可能にする必要があります (を参照してください[WPF のグローバリゼーションおよびローカリゼーションの概要](../advanced/wpf-globalization-and-localization-overview.md))。  
  
> [!NOTE]
>  このセクションで説明されているリソース ファイルは、リソース ファイルで説明されているものと異なる[XAML リソース](../advanced/xaml-resources.md)しで説明されている埋め込みまたはリンクされたリソースとは異なる[管理アプリケーションのリソース (.NET)](/visualstudio/ide/managing-application-resources-dotnet).  
  
### <a name="configuring-resource-files"></a>リソース ファイルの構成  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]、リソース ファイルに含まれているファイルとは、[!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)]プロジェクトとして、`Resource`項目。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Resource Include="ResourceFile.xaml" />  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
>  [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]、リソース ファイルを作成するファイルをプロジェクトの設定を追加してその`Build Action`に`Resource`します。  
  
 プロジェクトのビルド時に[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]リソースをアセンブリにコンパイルされます。  
  
### <a name="using-resource-files"></a>リソース ファイルの使用  
 リソース ファイルを読み込むを呼び出すことができます、<xref:System.Windows.Application.GetResourceStream%2A>のメソッド、<xref:System.Windows.Application>クラス、パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]目的のリソース ファイルを識別します。 <xref:System.Windows.Application.GetResourceStream%2A> 返します、<xref:System.Windows.Resources.StreamResourceInfo>リソース ファイルとして公開するオブジェクト、<xref:System.IO.Stream>とそのコンテンツの種類について説明します。  
  
 たとえば、次のコードが使用する方法を示します<xref:System.Windows.Application.GetResourceStream%2A>を読み込む、<xref:System.Windows.Controls.Page>リソース ファイルし、のコンテンツとして設定する、 <xref:System.Windows.Controls.Frame> (`pageFrame`)。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 呼び出し中に<xref:System.Windows.Application.GetResourceStream%2A>にアクセスすること、 <xref:System.IO.Stream>、それを設定 プロパティの型に変換する余分な作業を実行する必要があります。 代わりに、させることができます[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]注意を開いたり変換したり、<xref:System.IO.Stream>でコードを使用して型のプロパティに直接、リソース ファイルを読み込みます。  
  
 次の例を読み込む方法を示しています、<xref:System.Windows.Controls.Page>に直接、 <xref:System.Windows.Controls.Frame> (`pageFrame`) コードを使用します。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 次の例は、上の例と同じ意味のマークアップです。  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a>リソース ファイルとしてのアプリケーション コード ファイル  
 一連の特殊な[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]パックを使用して、アプリケーション コード ファイルを参照できる[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)](windows、ページ、フロー ドキュメント、リソース ディクショナリなど)。 たとえば、設定、<xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>パック プロパティ[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]ウィンドウまたはアプリケーションの起動時に読み込むしたいページを参照します。  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 場合にこのを行うことができます、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]でファイルが含まれて、[!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)]プロジェクトとして、`Page`項目。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Page Include="MainWindow.xaml" />  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]、追加<xref:System.Windows.Window>、 <xref:System.Windows.Navigation.NavigationWindow>、 <xref:System.Windows.Controls.Page>、 <xref:System.Windows.Documents.FlowDocument>、または<xref:System.Windows.ResourceDictionary>をプロジェクトに、`Build Action`ファイルは既定のマークアップ`Page`します。  
  
 ときに、プロジェクトで`Page`項目がコンパイルされると、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]項目がバイナリ形式に変換され、関連付けられているアセンブリにコンパイルします。 したがって、これらのファイルは、通常のリソース ファイルと同様に使用できます。  
  
> [!NOTE]
>  場合、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]としてファイルが構成されている、`Resource`項目、および分離コード ファイル、生がない[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]は、生のバイナリのバージョンではなく、アセンブリにコンパイル[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]します。  
  
<a name="Content_Files"></a>   
## <a name="content-files"></a>コンテンツ ファイル  
 A*コンテンツ ファイル*は実行可能アセンブリと共に圧縮しないファイルとして配布されます。 コンテンツ ファイルはコンパイルされてアセンブリに組み込まれるのではありませんが、アセンブリのコンパイル時に、各コンテンツ ファイルとの関連付けを確立するメタデータが使用されます。  
  
 アプリケーションに必要な特定のアプリケーション データ ファイルのセットが更新されても、そのファイルを使用するアセンブリを再コンパイルせずに、コンテンツ ファイルを使用する必要があります。  
  
### <a name="configuring-content-files"></a>コンテンツ ファイルの構成  
 コンテンツ ファイルをプロジェクトに追加するには、アプリケーション データ ファイルでとして指定する必要があります、`Content`項目。 さらに、コンテンツ ファイルがアセンブリに直接コンパイルされていないため、設定する必要が、 [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `CopyToOutputDirectory`メタデータ要素をコンテンツ ファイルがビルドされたアセンブリに対して相対的な場所にコピーされたことを指定します。 プロジェクトをビルド、リソースを毎回ビルド出力フォルダーにコピーする場合は、設定、`CopyToOutputDirectory`メタデータ要素を`Always`値。 使用してビルド出力フォルダーにリソースの最新バージョンのみがコピーされたことを確認する場合は、`PreserveNewest`値。  
  
 次に示すファイルは、新しいバージョンのリソースがプロジェクトに追加された場合にのみビルド出力フォルダーにコピーされるコンテンツ ファイルとして構成されています。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Content Include="ContentFile.xaml">  
      <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>  
    </Content>  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]、ファイルをプロジェクトの設定を追加して、コンテンツ ファイルを作成するその`Build Action`に`Content`、設定とその`Copy to Output Directory`に`Copy always`(と同じ`Always`) と`Copy if newer`(と同じ`PreserveNewest`)。  
  
 プロジェクトをビルドするとき、<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>属性は各コンテンツ ファイルのアセンブリのメタデータにコンパイルされます。  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 値、<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>プロジェクト内の位置に対して相対的なコンテンツのファイルへのパスを意味します。 たとえば、コンテンツ ファイルは、プロジェクトのサブフォルダーにありますが、追加パス情報に組み込む、<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>値。  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>値も、ビルド出力フォルダー内のコンテンツのファイルへのパスの値。  
  
### <a name="using-content-files"></a>コンテンツ ファイルの使用  
 コンテンツ ファイルを読み込むを呼び出すことができます、<xref:System.Windows.Application.GetContentStream%2A>のメソッド、<xref:System.Windows.Application>クラス、パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]目的のコンテンツ ファイルを識別します。 <xref:System.Windows.Application.GetContentStream%2A> 返します、<xref:System.Windows.Resources.StreamResourceInfo>コンテンツ ファイルとして公開するオブジェクト、<xref:System.IO.Stream>とそのコンテンツの種類について説明します。  
  
 たとえば、次のコードが使用する方法を示します<xref:System.Windows.Application.GetContentStream%2A>を読み込む、<xref:System.Windows.Controls.Page>ファイルのコンテンツし、のコンテンツとして設定する、 <xref:System.Windows.Controls.Frame> (`pageFrame`)。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 呼び出し中に<xref:System.Windows.Application.GetContentStream%2A>にアクセスすること、 <xref:System.IO.Stream>、それを設定 プロパティの型に変換する余分な作業を実行する必要があります。 代わりに、させることができます[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]注意を開いたり変換したり、<xref:System.IO.Stream>でコードを使用して型のプロパティに直接、リソース ファイルを読み込みます。  
  
 次の例を読み込む方法を示しています、<xref:System.Windows.Controls.Page>に直接、 <xref:System.Windows.Controls.Frame> (`pageFrame`) コードを使用します。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 次の例は、上の例と同じ意味のマークアップです。  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>   
## <a name="site-of-origin-files"></a>起点サイト ファイル  
 リソース ファイルで定義されている、共に配布されるアセンブリを使用した明示的な関連付けがある場合、<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>します。 ただし、アセンブリとアプリケーション データ ファイル間に暗黙的な関係を持たせる、または関係を持たせない場合があります。たとえば次のような場合です。  
  
-   ファイルは、コンパイル時に存在しません。  
  
-   アセンブリが必要とするファイルが、実行時までわからない場合。  
  
-   関連付けられているアセンブリを再コンパイルせずにファイルを更新可能にする場合。  
  
-   オーディオやビデオなど大容量のデータ ファイルを使用するアプリケーションで、ユーザーが選択した場合にのみファイルをダウンロードする場合。  
  
 この種の従来型を使用してファイルをロードすることは[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]file:/// http:// 方式などのスキーム。  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 ただし、file:/// スキームや http:// スキームを使用する場合は、アプリケーションに完全信頼が必要です。 アプリケーションの場合、[!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]がインターネットまたはイントラネットから起動して、圧縮しないファイルは、配信元 (アプリケーションのサイトからのみ読み込むことが、それらの場所から起動するアプリケーションの許可されるアクセス許可のセットのみを要求場所を起動) します。 このようなファイルと呼びます*起点サイト*ファイル。  
  
 起点サイト ファイルは部分信頼アプリケーションの唯一のオプションですが、部分信頼アプリケーション以外でも使用できます。 完全信頼アプリケーションでも、読み込むアプリケーション データ ファイルがビルド時点では不明な場合があります。完全信頼アプリケーションでは file:/// を使用できますが、アプリケーション データ ファイルがアプリケーション アセンブリと同じフォルダーにインストールされることも、サブフォルダーにインストールされることも考えられます。 この場合は、起点サイト参照を使用する方が、file:/// を使用するよりも簡単です。file:/// を使用するには、ファイルの完全パスを指定する必要があるためです。  
  
> [!NOTE]
>  ファイルがでキャッシュされません起点サイト、[!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]コンテンツ ファイルは、クライアント コンピューター上です。 したがって、起点サイト ファイルは明確に要求されたときにのみダウンロードされます。 場合、[!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]アプリケーションが大量のメディア ファイル、起点サイト ファイルは、初期のアプリケーションの起動がはるかに高速でありオンデマンド ファイルのダウンロードのみを意味として構成します。  
  
### <a name="configuring-site-of-origin-files"></a>起点サイト ファイルの構成  
 起点サイト ファイルがコンパイル時に存在しないか不明な場合は、従来の展開を使用する必要がありますいずれかの使用など、実行時に、必要なファイルを確保するためのメカニズムが使用可能な、`XCopy`コマンド ライン プログラム、または、 [!INCLUDE[TLA#tla_wininstall](../../../../includes/tlasharptla-wininstall-md.md)].  
  
 それらのファイルを追加することがわかっている場合はコンパイル時にファイルを元のサイトに配置されるような場合は明示的な依存関係をしないように、[!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)]プロジェクトとして`None`項目。 コンテンツのファイルで設定する必要がある、 [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `CopyToOutputDirectory`元のファイルのサイトがいずれかを指定することによってビルドされたアセンブリに対応する場所にコピーされていることを指定する属性、`Always`値または`PreserveNewest`値。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <None Include="PageSiteOfOriginFile.xaml">  
    <CopyToOutputDirectory>Always</CopyToOutputDirectory>  
  </None>  
  ...  
</Project>  
```  
  
> [!NOTE]
>  [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]、ファイルをプロジェクトの設定を追加して元のファイルのサイトを作成するその`Build Action`に`None`します。  
  
 プロジェクトのビルド時に[!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)]ビルド出力フォルダーに、指定されたファイルをコピーします。  
  
### <a name="using-site-of-origin-files"></a>起点サイト ファイルの使用  
 呼び出すことができます、起点サイト ファイルを読み込むには、<xref:System.Windows.Application.GetRemoteStream%2A>のメソッド、<xref:System.Windows.Application>クラス、パック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]元のファイルの目的のサイトを識別します。 <xref:System.Windows.Application.GetRemoteStream%2A> 返します、<xref:System.Windows.Resources.StreamResourceInfo>としてファイルを配信元のサイトを公開するには、オブジェクト、<xref:System.IO.Stream>とそのコンテンツの種類について説明します。  
  
 たとえば、次のコードが使用する方法を示します<xref:System.Windows.Application.GetRemoteStream%2A>を読み込む、<xref:System.Windows.Controls.Page>起点サイト ファイルし、のコンテンツとして設定、 <xref:System.Windows.Controls.Frame> (`pageFrame`)。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 呼び出し中に<xref:System.Windows.Application.GetRemoteStream%2A>にアクセスすること、 <xref:System.IO.Stream>、それを設定 プロパティの型に変換する余分な作業を実行する必要があります。 代わりに、させることができます[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]注意を開いたり変換したり、<xref:System.IO.Stream>でコードを使用して型のプロパティに直接、リソース ファイルを読み込みます。  
  
 次の例を読み込む方法を示しています、<xref:System.Windows.Controls.Page>に直接、 <xref:System.Windows.Controls.Frame> (`pageFrame`) コードを使用します。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 次の例は、上の例と同じ意味のマークアップです。  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>   
## <a name="rebuilding-after-changing-build-type"></a>ビルドの種類を変更した後のリビルド  
 アプリケーション データ ファイルのビルドの種類を変更した後は、変更を確実に反映するためにアプリケーション全体をリビルドする必要があります。 アプリケーションのみをビルドしても、変更は適用されません。  
  
## <a name="see-also"></a>関連項目

- [WPF におけるパッケージの URI](pack-uris-in-wpf.md)
