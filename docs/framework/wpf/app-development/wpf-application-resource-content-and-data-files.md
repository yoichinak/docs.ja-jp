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
ms.openlocfilehash: e50f542086aadc2f61412fe409d7df0f49422718
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920362"
---
# <a name="wpf-application-resource-content-and-data-files"></a>WPF アプリケーションのリソース ファイル、コンテンツ ファイル、およびデータ ファイル
[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] アプリケーションは、多くの場合、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]、イメージ、ビデオ、オーディオなど、実行可能ではないデータを含むファイルに依存します。 Windows Presentation Foundation (WPF) では、これらの種類のデータファイル (アプリケーションデータファイルと呼ばれます) を構成、識別、および使用するための特別なサポートを提供しています。 このサポートの中心となるのは、次のような特定のアプリケーション データ ファイルの種類のセットです。  
  
- **リソースファイル**: 実行可能ファイルまたはライブラリ [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アセンブリのいずれかにコンパイルされるデータファイル。  
  
- **コンテンツファイル**: 実行可能ファイル [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アセンブリに明示的に関連付けられているスタンドアロンデータファイル。  
  
- **起点サイトファイル**: 実行可能ファイル [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アセンブリに関連付けられていないスタンドアロンデータファイル。  
  
 これらの 3 種類のファイルの重要な違いは、リソース ファイルとコンテンツ ファイルはビルド時に認識されるという点です。アセンブリは、これらを明確に認識します。 ただし、起点サイトファイルの場合、アセンブリについての情報がないか、またはパッケージ URI (uniform resource identifier) 参照によって暗黙的に認識されている可能性があります。後者の場合、参照されている起点サイトファイルが実際に存在する保証はありません。  
  
 アプリケーションデータファイルを参照するために、Windows Presentation Foundation (WPF) は、パッケージ uri (uniform resource identifier) スキームを使用します。これについては、「 [wpf のパック uri](pack-uris-in-wpf.md)」で詳しく説明されています。  
  
 このトピックでは、アプリケーション データ ファイルを構成および使用する方法について説明します。  

<a name="Resource_Files"></a>   
## <a name="resource-files"></a>リソース ファイル (Visual Studio)  
 アプリケーション データ ファイルを常にアプリケーションで使用可能にするには、コンパイルしてアプリケーションのメイン実行可能アセンブリまたはその参照アセンブリの 1 つに組み込む必要があります。 この種類のアプリケーションデータファイルは、*リソースファイル*と呼ばれます。  
  
 リソース ファイルは、次のときに使用します。  
  
- コンパイルしてアセンブリに組み込んだ後に、リソース ファイルのコンテンツを更新する必要がない。  
  
- ファイルの依存関係の数を減らして、アプリケーション配布の複雑さを軽減する必要がある。  
  
- アプリケーションデータファイルはローカライズ可能である必要があります (「 [WPF のグローバリゼーションとローカライズの概要](../advanced/wpf-globalization-and-localization-overview.md)」を参照してください)。  
  
> [!NOTE]
> このセクションで説明するリソースファイルは、「 [XAML リソース](../advanced/xaml-resources.md)」で説明されているリソースファイルとは異なり、「[アプリケーションリソースの管理 (.net)](/visualstudio/ide/managing-application-resources-dotnet)」で説明されている埋め込みリソースまたはリンクされたリソースとは異なります。  
  
### <a name="configuring-resource-files"></a>リソース ファイルの構成  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]では、リソースファイルは、`Resource` 項目として Microsoft build engine (MSBuild) プロジェクトに含まれるファイルです。  
  
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
> Visual Studio では、プロジェクトにファイルを追加し、その `Build Action` を `Resource`に設定することによって、リソースファイルを作成します。  
  
 プロジェクトがビルドされると、MSBuild はリソースをコンパイルしてアセンブリにします。  
  
### <a name="using-resource-files"></a>リソース ファイルの使用  
 リソースファイルを読み込むには、<xref:System.Windows.Application> クラスの <xref:System.Windows.Application.GetResourceStream%2A> メソッドを呼び出して、目的のリソースファイルを識別するパック URI を渡します。 <xref:System.Windows.Application.GetResourceStream%2A> は <xref:System.Windows.Resources.StreamResourceInfo> オブジェクトを返します。このオブジェクトは、リソースファイルを <xref:System.IO.Stream> として公開し、そのコンテンツの種類について説明します。  
  
 例として、次のコードは、<xref:System.Windows.Application.GetResourceStream%2A> を使用して <xref:System.Windows.Controls.Page> リソースファイルを読み込み、<xref:System.Windows.Controls.Frame> (`pageFrame`) のコンテンツとして設定する方法を示しています。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 <xref:System.Windows.Application.GetResourceStream%2A> を呼び出すと <xref:System.IO.Stream>にアクセスできますが、それを設定するプロパティの型に変換する追加作業を実行する必要があります。 代わりに、コードを使用して、リソースファイルを型のプロパティに直接読み込むことによって、<xref:System.IO.Stream> を開いて変換できるように [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] できます。  
  
 次の例は、コードを使用して <xref:System.Windows.Controls.Frame> (`pageFrame`) に <xref:System.Windows.Controls.Page> を直接読み込む方法を示しています。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 次の例は、上の例と同じ意味のマークアップです。  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a>リソース ファイルとしてのアプリケーション コード ファイル  
 Windows、ページ、フロードキュメント、リソースディクショナリなどのパック Uri を使用して、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] アプリケーションコードファイルの特殊なセットを参照できます。 たとえば、アプリケーションの起動時に読み込むウィンドウまたはページを参照するパック URI を使用して、<xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> プロパティを設定できます。  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 これは、XAML ファイルが MSBuild プロジェクトに `Page` 項目として含まれている場合に行うことができます。  
  
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
> Visual Studio では、新しい <xref:System.Windows.Window>、<xref:System.Windows.Navigation.NavigationWindow>、<xref:System.Windows.Controls.Page>、<xref:System.Windows.Documents.FlowDocument>、または <xref:System.Windows.ResourceDictionary> をプロジェクトに追加すると、マークアップファイルの `Build Action` が既定で `Page`されます。  
  
 `Page` 項目を含むプロジェクトがコンパイルされると、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 項目はバイナリ形式に変換され、関連付けられたアセンブリにコンパイルされます。 したがって、これらのファイルは、通常のリソース ファイルと同様に使用できます。  
  
> [!NOTE]
> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイルが `Resource` の項目として構成されていて、分離コードファイルがない場合、生の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] は、生の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]のバイナリバージョンではなく、アセンブリにコンパイルされます。  
  
<a name="Content_Files"></a>   
## <a name="content-files"></a>コンテンツ ファイル  
 *コンテンツファイル*は、実行可能アセンブリと共に、圧縮されていないファイルとして配布されます。 コンテンツ ファイルはコンパイルされてアセンブリに組み込まれるのではありませんが、アセンブリのコンパイル時に、各コンテンツ ファイルとの関連付けを確立するメタデータが使用されます。  
  
 アプリケーションに必要な特定のアプリケーション データ ファイルのセットが更新されても、そのファイルを使用するアセンブリを再コンパイルせずに、コンテンツ ファイルを使用する必要があります。  
  
### <a name="configuring-content-files"></a>コンテンツ ファイルの構成  
 コンテンツファイルをプロジェクトに追加するには、アプリケーションデータファイルが `Content` 項目として含まれている必要があります。 さらに、コンテンツファイルはアセンブリに直接コンパイルされないため、MSBuild `CopyToOutputDirectory` メタデータ要素を設定して、ビルドされたアセンブリに対して相対的な場所にコンテンツファイルをコピーするように指定する必要があります。 プロジェクトをビルドするたびにリソースをビルド出力フォルダーにコピーする場合は、`CopyToOutputDirectory` メタデータ要素に `Always` 値を設定します。 それ以外の場合は、`PreserveNewest` 値を使用して、リソースの最新バージョンのみがビルド出力フォルダーにコピーされるようにすることができます。  
  
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
> Visual Studio では、ファイルをプロジェクトに追加し、その `Build Action` を `Content`に設定し、その `Copy to Output Directory` を `Copy always` (`Always`と同じ) および `Copy if newer` (`PreserveNewest`と同じ) に設定することによって、コンテンツファイルを作成します。  
  
 プロジェクトがビルドされると、<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> 属性が、各コンテンツファイルのアセンブリのメタデータにコンパイルされます。  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> の値は、プロジェクト内のその位置に対するコンテンツファイルへの相対パスを意味します。 たとえば、コンテンツファイルがプロジェクトサブフォルダー内にある場合、追加のパス情報が <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> の値に組み込まれます。  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> 値は、ビルド出力フォルダー内のコンテンツファイルへのパスの値でもあります。  
  
### <a name="using-content-files"></a>コンテンツ ファイルの使用  
 コンテンツファイルを読み込むには、<xref:System.Windows.Application> クラスの <xref:System.Windows.Application.GetContentStream%2A> メソッドを呼び出して、目的のコンテンツファイルを識別するパック URI を渡します。 <xref:System.Windows.Application.GetContentStream%2A> は <xref:System.Windows.Resources.StreamResourceInfo> オブジェクトを返します。これにより、コンテンツファイルが <xref:System.IO.Stream> として公開され、コンテンツの種類が記述されます。  
  
 例として、次のコードは、<xref:System.Windows.Application.GetContentStream%2A> を使用して <xref:System.Windows.Controls.Page> コンテンツファイルを読み込み、<xref:System.Windows.Controls.Frame> (`pageFrame`) のコンテンツとして設定する方法を示しています。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 <xref:System.Windows.Application.GetContentStream%2A> を呼び出すと <xref:System.IO.Stream>にアクセスできますが、それを設定するプロパティの型に変換する追加作業を実行する必要があります。 代わりに、コードを使用して、リソースファイルを型のプロパティに直接読み込むことによって、<xref:System.IO.Stream> を開いて変換できるように [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] できます。  
  
 次の例は、コードを使用して <xref:System.Windows.Controls.Frame> (`pageFrame`) に <xref:System.Windows.Controls.Page> を直接読み込む方法を示しています。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 次の例は、上の例と同じ意味のマークアップです。  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>   
## <a name="site-of-origin-files"></a>起点サイト ファイル  
 リソースファイルには、<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> による定義に従って、配布されるアセンブリと共に明示的な関係があります。 ただし、アセンブリとアプリケーション データ ファイル間に暗黙的な関係を持たせる、または関係を持たせない場合があります。たとえば次のような場合です。  
  
- コンパイル時にファイルが存在しません。  
  
- アセンブリが必要とするファイルが、実行時までわからない場合。  
  
- 関連付けられているアセンブリを再コンパイルせずにファイルを更新可能にする場合。  
  
- オーディオやビデオなど大容量のデータ ファイルを使用するアプリケーションで、ユーザーが選択した場合にのみファイルをダウンロードする場合。  
  
 これらの種類のファイルは、file:///スキームや http://スキームなどの従来の URI スキームを使用して読み込むことができます。  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 ただし、file:/// スキームや http:// スキームを使用する場合は、アプリケーションに完全信頼が必要です。 アプリケーションがインターネットまたはイントラネットから起動した [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] であり、その場所から起動されたアプリケーションに対して許可されているアクセス許可のセットだけを要求する場合、ルースファイルはアプリケーションの起点サイトからのみ読み込むことができます (起動場所)。 このようなファイルは、*起点サイト*ファイルと呼ばれます。  
  
 起点サイト ファイルは部分信頼アプリケーションの唯一のオプションですが、部分信頼アプリケーション以外でも使用できます。 完全信頼アプリケーションでも、読み込むアプリケーション データ ファイルがビルド時点では不明な場合があります。完全信頼アプリケーションでは file:/// を使用できますが、アプリケーション データ ファイルがアプリケーション アセンブリと同じフォルダーにインストールされることも、サブフォルダーにインストールされることも考えられます。 この場合は、起点サイト参照を使用する方が、file:/// を使用するよりも簡単です。file:/// を使用するには、ファイルの完全パスを指定する必要があるためです。  
  
> [!NOTE]
> 起点サイトファイルは、クライアントコンピューターに [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] と共にキャッシュされることはありませんが、コンテンツファイルはです。 したがって、起点サイト ファイルは明確に要求されたときにのみダウンロードされます。 [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] アプリケーションに大きなメディアファイルが含まれている場合は、それらを起点サイトファイルとして構成すると、最初のアプリケーションの起動にかかる時間が大幅に短縮され、ファイルは要求時にのみダウンロードされます。  
  
### <a name="configuring-site-of-origin-files"></a>起点サイト ファイルの構成  
 コンパイル時に起点サイトファイルが存在しないか不明な場合は、`XCopy` コマンドラインプログラムまたは [!INCLUDE[TLA#tla_wininstall](../../../../includes/tlasharptla-wininstall-md.md)]を使用するなど、必要なファイルを実行時に確実に使用できるようにするために、従来の配置メカニズムを使用する必要があります。  
  
 発行元のサイトに配置する必要があるファイルがコンパイル時にわかっていても、明示的な依存関係を回避したい場合は、それらのファイルを `None` 項目として MSBuild プロジェクトに追加できます。 コンテンツファイルと同様に、MSBuild `CopyToOutputDirectory` 属性を設定して、`Always` 値または `PreserveNewest` 値を指定することによって、ビルドされたアセンブリに対して相対的な場所に起点サイトファイルをコピーするように指定する必要があります。  
  
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
> Visual Studio では、プロジェクトにファイルを追加し、その `Build Action` を `None`に設定することによって、起点サイトファイルを作成します。  
  
 プロジェクトがビルドされると、MSBuild は、指定されたファイルをビルド出力フォルダーにコピーします。  
  
### <a name="using-site-of-origin-files"></a>起点サイト ファイルの使用  
 起点サイトファイルを読み込むには、<xref:System.Windows.Application> クラスの <xref:System.Windows.Application.GetRemoteStream%2A> メソッドを呼び出して、目的の起点サイトファイルを識別するパック URI を渡します。 <xref:System.Windows.Application.GetRemoteStream%2A> は <xref:System.Windows.Resources.StreamResourceInfo> オブジェクトを返します。これにより、起点サイトファイルが <xref:System.IO.Stream> として公開され、そのコンテンツの種類が記述されます。  
  
 例として、次のコードは、<xref:System.Windows.Application.GetRemoteStream%2A> を使用して元のファイルの <xref:System.Windows.Controls.Page> サイトを読み込み、<xref:System.Windows.Controls.Frame> (`pageFrame`) のコンテンツとして設定する方法を示しています。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 <xref:System.Windows.Application.GetRemoteStream%2A> を呼び出すと <xref:System.IO.Stream>にアクセスできますが、それを設定するプロパティの型に変換する追加作業を実行する必要があります。 代わりに、コードを使用して、リソースファイルを型のプロパティに直接読み込むことによって、<xref:System.IO.Stream> を開いて変換できるように [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] できます。  
  
 次の例は、コードを使用して <xref:System.Windows.Controls.Frame> (`pageFrame`) に <xref:System.Windows.Controls.Page> を直接読み込む方法を示しています。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 次の例は、上の例と同じ意味のマークアップです。  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>   
## <a name="rebuilding-after-changing-build-type"></a>ビルドの種類を変更した後のリビルド  
 アプリケーション データ ファイルのビルドの種類を変更した後は、変更を確実に反映するためにアプリケーション全体をリビルドする必要があります。 アプリケーションのみをビルドしても、変更は適用されません。  
  
## <a name="see-also"></a>関連項目

- [WPF におけるパッケージの URI](pack-uris-in-wpf.md)
