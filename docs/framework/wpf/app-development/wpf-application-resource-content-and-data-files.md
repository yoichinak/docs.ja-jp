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
ms.openlocfilehash: 57eae5067a72777db2c19331029b6df679a9fdce
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956188"
---
# <a name="wpf-application-resource-content-and-data-files"></a>WPF アプリケーションのリソース ファイル、コンテンツ ファイル、およびデータ ファイル
[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]多くの場合、アプリケーションは[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]、イメージ、ビデオ、オーディオなど、実行可能ではないデータを含むファイルに依存します。 Windows Presentation Foundation (WPF) では、これらの種類のデータファイル (アプリケーションデータファイルと呼ばれます) を構成、識別、および使用するための特別なサポートを提供しています。 このサポートの中心となるのは、次のような特定のアプリケーション データ ファイルの種類のセットです。  
  
- **リソースファイル**:実行可能ファイルまたはライブラリ[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]アセンブリにコンパイルされるデータファイル。  
  
- **コンテンツファイル**:実行可能[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]アセンブリと明示的に関連付けられているスタンドアロンデータファイル。  
  
- **起点サイトファイル**:実行可能[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]アセンブリに関連付けられていないスタンドアロンデータファイル。  
  
 これらの 3 種類のファイルの重要な違いは、リソース ファイルとコンテンツ ファイルはビルド時に認識されるという点です。アセンブリは、これらを明確に認識します。 ただし、起点サイトファイルの場合、アセンブリは、そのアセンブリについての知識を持っていないか、 [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]またはパック参照によって暗黙的な知識を持っていない可能性があります。後者の場合、参照された起点サイトのファイルが実際に存在する保証はありません。  
  
 アプリケーションデータファイルを参照するには、Windows Presentation Foundation (wpf) [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]でパックスキームを使用します。これについては、「 [wpf のパック uri](pack-uris-in-wpf.md)」で詳しく説明されています。  
  
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
 で[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]は、リソースファイルは、Microsoft build engine (MSBuild) プロジェクトに`Resource`項目として含まれているファイルです。  
  
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
> で[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]は、プロジェクトにファイルを追加し、その`Build Action`をに設定する`Resource`ことによって、リソースファイルを作成します。  
  
 プロジェクトがビルドされると、MSBuild はリソースをコンパイルしてアセンブリにします。  
  
### <a name="using-resource-files"></a>リソース ファイルの使用  
 リソースファイルを読み込むには、 <xref:System.Windows.Application.GetResourceStream%2A> <xref:System.Windows.Application>クラスのメソッドを呼び出して、目的のリソースファイル[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]を識別するパックを渡します。 <xref:System.Windows.Application.GetResourceStream%2A><xref:System.Windows.Resources.StreamResourceInfo> は<xref:System.IO.Stream> 、リソースファイルをとして公開し、そのコンテンツタイプを記述するオブジェクトを返します。  
  
 例として、次のコードは、を<xref:System.Windows.Application.GetResourceStream%2A>使用して<xref:System.Windows.Controls.Page>リソースファイルを読み込み、それを<xref:System.Windows.Controls.Frame> (`pageFrame`) のコンテンツとして設定する方法を示しています。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 を呼び<xref:System.Windows.Application.GetResourceStream%2A>出すと、 <xref:System.IO.Stream>にアクセスできるようになりますが、それを設定するプロパティの型に変換する追加作業を実行する必要があります。 代わりに、コードを使用[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]して、リソースファイルを型<xref:System.IO.Stream>のプロパティに直接読み込むことで、を開いて変換することができます。  
  
 次の例は、コードを使用<xref:System.Windows.Controls.Page>してを<xref:System.Windows.Controls.Frame> (`pageFrame`) に直接読み込む方法を示しています。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 次の例は、上の例と同じ意味のマークアップです。  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a>リソース ファイルとしてのアプリケーション コード ファイル  
 アプリケーションコードファイルの[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]特殊なセットは、windows、ページ[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]、フロードキュメント、リソースディクショナリなどのパックを使用して参照できます。 たとえば、アプリケーションの起動時に読み込む<xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>ウィンドウまたはページ[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]を参照するパックを使用して、プロパティを設定できます。  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 これは、XAML ファイルが MSBuild プロジェクトに`Page`項目として含まれている場合に実行できます。  
  
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
> で[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)] <xref:System.Windows.Window>は、新しい、 <xref:System.Windows.Navigation.NavigationWindow> `Page`、、 、また<xref:System.Windows.ResourceDictionary>はをプロジェクト`Build Action`に追加します。マークアップファイルのの既定値はになります。 <xref:System.Windows.Documents.FlowDocument> <xref:System.Windows.Controls.Page>  
  
 項目を含む`Page`プロジェクトがコンパイル[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]されると、項目はバイナリ形式に変換され、関連付けられたアセンブリにコンパイルされます。 したがって、これらのファイルは、通常のリソース ファイルと同様に使用できます。  
  
> [!NOTE]
> ファイルが`Resource`項目として構成されていて、分離コードファイルがない場合、未加工[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]は、生のバイナリバージョンで[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]はなく、アセンブリにコンパイルされます。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
<a name="Content_Files"></a>   
## <a name="content-files"></a>コンテンツ ファイル  
 *コンテンツファイル*は、実行可能アセンブリと共に、圧縮されていないファイルとして配布されます。 コンテンツ ファイルはコンパイルされてアセンブリに組み込まれるのではありませんが、アセンブリのコンパイル時に、各コンテンツ ファイルとの関連付けを確立するメタデータが使用されます。  
  
 アプリケーションに必要な特定のアプリケーション データ ファイルのセットが更新されても、そのファイルを使用するアセンブリを再コンパイルせずに、コンテンツ ファイルを使用する必要があります。  
  
### <a name="configuring-content-files"></a>コンテンツ ファイルの構成  
 コンテンツファイルをプロジェクトに追加するには、アプリケーションデータファイルを`Content`項目として含める必要があります。 さらに、コンテンツファイルはアセンブリに直接コンパイルされないため、MSBuild `CopyToOutputDirectory`メタデータ要素を設定して、ビルドされたアセンブリに対して相対的な場所にコンテンツファイルをコピーするように指定する必要があります。 プロジェクトがビルドされるたびにリソースがビルド出力フォルダーにコピーされるようにするには、 `CopyToOutputDirectory`メタデータ要素`Always`に値を設定します。 それ以外の場合は、 `PreserveNewest`値を使用して、リソースの最新バージョンのみがビルド出力フォルダーにコピーされるようにすることができます。  
  
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
> で[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]は、プロジェクトにファイルを追加し、その`Always` `Build Action` `Copy to Output Directory`をに`Content`設定し、を (と同じ) および`Copy if newer` ( `Copy always`と`PreserveNewest`同じ) に設定することによって、コンテンツファイルを作成します。  
  
 プロジェクトがビルドされると、 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>属性は、各コンテンツファイルのアセンブリのメタデータにコンパイルされます。  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 の値は、 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>プロジェクト内のその位置に対するコンテンツファイルへの相対パスを意味します。 たとえば、コンテンツファイルがプロジェクトサブフォルダー内にある場合、追加のパス情報が<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>値に組み込まれます。  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>値は、ビルド出力フォルダー内のコンテンツファイルへのパスの値でもあります。  
  
### <a name="using-content-files"></a>コンテンツ ファイルの使用  
 コンテンツファイルを読み込むには、目的のコンテンツ<xref:System.Windows.Application.GetContentStream%2A>ファイルを識別<xref:System.Windows.Application>するパック[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]を渡して、クラスのメソッドを呼び出すことができます。 <xref:System.Windows.Application.GetContentStream%2A>コンテンツファイルをと<xref:System.IO.Stream>して公開し、そのコンテンツタイプを記述するオブジェクトを返します。<xref:System.Windows.Resources.StreamResourceInfo>  
  
 例として、次のコードは、を<xref:System.Windows.Application.GetContentStream%2A>使用して<xref:System.Windows.Controls.Page>コンテンツファイルを読み込み、それを<xref:System.Windows.Controls.Frame> (`pageFrame`) のコンテンツとして設定する方法を示しています。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 を呼び<xref:System.Windows.Application.GetContentStream%2A>出すと、 <xref:System.IO.Stream>にアクセスできるようになりますが、それを設定するプロパティの型に変換する追加作業を実行する必要があります。 代わりに、コードを使用[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]して、リソースファイルを型<xref:System.IO.Stream>のプロパティに直接読み込むことで、を開いて変換することができます。  
  
 次の例は、コードを使用<xref:System.Windows.Controls.Page>してを<xref:System.Windows.Controls.Frame> (`pageFrame`) に直接読み込む方法を示しています。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 次の例は、上の例と同じ意味のマークアップです。  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>   
## <a name="site-of-origin-files"></a>起点サイト ファイル  
 リソースファイルには、 <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>で定義されているように、と共に配布されるアセンブリとの明示的な関係があります。 ただし、アセンブリとアプリケーション データ ファイル間に暗黙的な関係を持たせる、または関係を持たせない場合があります。たとえば次のような場合です。  
  
- コンパイル時にファイルが存在しません。  
  
- アセンブリが必要とするファイルが、実行時までわからない場合。  
  
- 関連付けられているアセンブリを再コンパイルせずにファイルを更新可能にする場合。  
  
- オーディオやビデオなど大容量のデータ ファイルを使用するアプリケーションで、ユーザーが選択した場合にのみファイルをダウンロードする場合。  
  
 File:///や http://などの従来[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]のスキームを使用して、これらの種類のファイルを読み込むことができます。  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 ただし、file:/// スキームや http:// スキームを使用する場合は、アプリケーションに完全信頼が必要です。 アプリケーションが[!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]インターネットまたはイントラネットから起動したで、その場所から起動されたアプリケーションに対して許可されているアクセス許可のセットだけを要求する場合、ルースファイルはアプリケーションの元のサイトからのみ読み込むことができます (起動場所)。 このようなファイルは、*起点サイト*ファイルと呼ばれます。  
  
 起点サイト ファイルは部分信頼アプリケーションの唯一のオプションですが、部分信頼アプリケーション以外でも使用できます。 完全信頼アプリケーションでも、読み込むアプリケーション データ ファイルがビルド時点では不明な場合があります。完全信頼アプリケーションでは file:/// を使用できますが、アプリケーション データ ファイルがアプリケーション アセンブリと同じフォルダーにインストールされることも、サブフォルダーにインストールされることも考えられます。 この場合は、起点サイト参照を使用する方が、file:/// を使用するよりも簡単です。file:/// を使用するには、ファイルの完全パスを指定する必要があるためです。  
  
> [!NOTE]
> コンテンツファイルは、クライアントコンピューターのでは[!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]なく起点サイトファイルにキャッシュされません。 したがって、起点サイト ファイルは明確に要求されたときにのみダウンロードされます。 [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]アプリケーションに大きなメディアファイルがある場合、それらを起点サイトファイルとして構成すると、最初のアプリケーションの起動にかかる時間が大幅に短縮され、ファイルは要求時にのみダウンロードされます。  
  
### <a name="configuring-site-of-origin-files"></a>起点サイト ファイルの構成  
 コンパイル時に起点のサイトファイルが存在しないか不明である場合は、 `XCopy`コマンドラインプログラムを使用するか、またはを使用して、必要なファイルを実行時に確実に使用できるようにするために、従来の[!INCLUDE[TLA#tla_wininstall](../../../../includes/tlasharptla-wininstall-md.md)]配置メカニズムを使用する必要があります.  
  
 発行元のサイトに配置する必要があるファイルがコンパイル時にわかっていても、明示的な依存関係を回避したい場合は、それらのファイルを項目として`None` MSBuild プロジェクトに追加できます。 コンテンツファイルと同様に、MSBuild `CopyToOutputDirectory`属性を設定して、 `Always`値また`PreserveNewest`は値を指定することにより、ビルドされたアセンブリに対して相対的な場所に起点サイトファイルをコピーするように指定する必要があります。  
  
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
> で[!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)]は、プロジェクトにファイルを追加し、その`Build Action`をに設定する`None`ことによって、起点サイトファイルを作成します。  
  
 プロジェクトがビルドされると、MSBuild は、指定されたファイルをビルド出力フォルダーにコピーします。  
  
### <a name="using-site-of-origin-files"></a>起点サイト ファイルの使用  
 起点サイトファイルを読み込むには、 <xref:System.Windows.Application.GetRemoteStream%2A> <xref:System.Windows.Application>クラスのメソッドを呼び出して、目的の起点サイトファイル[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]を識別するパックを渡します。 <xref:System.Windows.Application.GetRemoteStream%2A>起点サイトファイルをと<xref:System.IO.Stream>して公開し、そのコンテンツタイプを記述するオブジェクトを返します。<xref:System.Windows.Resources.StreamResourceInfo>  
  
 例として、次のコードは、を<xref:System.Windows.Application.GetRemoteStream%2A>使用して<xref:System.Windows.Controls.Page>起点サイトファイルを読み込み、それを<xref:System.Windows.Controls.Frame> (`pageFrame`) のコンテンツとして設定する方法を示しています。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 を呼び<xref:System.Windows.Application.GetRemoteStream%2A>出すと、 <xref:System.IO.Stream>にアクセスできるようになりますが、それを設定するプロパティの型に変換する追加作業を実行する必要があります。 代わりに、コードを使用[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]して、リソースファイルを型<xref:System.IO.Stream>のプロパティに直接読み込むことで、を開いて変換することができます。  
  
 次の例は、コードを使用<xref:System.Windows.Controls.Page>してを<xref:System.Windows.Controls.Frame> (`pageFrame`) に直接読み込む方法を示しています。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 次の例は、上の例と同じ意味のマークアップです。  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>   
## <a name="rebuilding-after-changing-build-type"></a>ビルドの種類を変更した後のリビルド  
 アプリケーション データ ファイルのビルドの種類を変更した後は、変更を確実に反映するためにアプリケーション全体をリビルドする必要があります。 アプリケーションのみをビルドしても、変更は適用されません。  
  
## <a name="see-also"></a>関連項目

- [WPF におけるパッケージの URI](pack-uris-in-wpf.md)
