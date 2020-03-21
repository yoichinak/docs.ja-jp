---
title: アプリケーションリソース、コンテンツ、およびデータファイル
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
ms.openlocfilehash: f17898972eeef66447060db32bae5fae377b710e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186200"
---
# <a name="wpf-application-resource-content-and-data-files"></a>WPF アプリケーションのリソース ファイル、コンテンツ ファイル、およびデータ ファイル
Microsoft Windows アプリケーションは、多くの場合、イメージ、ビデオ、オーディオ[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]などの実行可能でないデータを含むファイルに依存します。 Windows プレゼンテーション ファンデーション (WPF) では、アプリケーション データ ファイルと呼ばれるこれらの種類のデータ ファイルを構成、識別、および使用するための特別なサポートが提供されています。 このサポートの中心となるのは、次のような特定のアプリケーション データ ファイルの種類のセットです。  
  
- **リソース ファイル**: 実行可能な WPF アセンブリまたはライブラリ WPF アセンブリにコンパイルされるデータ ファイル。  
  
- **コンテンツ ファイル**: 実行可能な WPF アセンブリと明示的に関連付けられているスタンドアロン データ ファイル。  
  
- **元のファイルのサイト**: 実行可能な WPF アセンブリと関連付けのないスタンドアロン データ ファイル。  
  
 これらの 3 種類のファイルの重要な違いは、リソース ファイルとコンテンツ ファイルはビルド時に認識されるという点です。アセンブリは、これらを明確に認識します。 ただし、サイト の起点ファイルの場合、アセンブリは、それらの情報をまったく持っていないか、またはパック統一リソース識別子 (URI) 参照を通じて暗黙的な知識を持っている可能性があります。後者の場合、参照元のサイトファイルが実際に存在するという保証はありません。  
  
 アプリケーション データ ファイルを参照するために、Windows プレゼンテーション ファンデーション (WPF) は、パック統一リソース識別子 (URI) スキーム[を](pack-uris-in-wpf.md)使用します。  
  
 このトピックでは、アプリケーション データ ファイルを構成および使用する方法について説明します。  

<a name="Resource_Files"></a>
## <a name="resource-files"></a>リソース ファイル (Visual Studio)  
 アプリケーション データ ファイルを常にアプリケーションで使用可能にするには、コンパイルしてアプリケーションのメイン実行可能アセンブリまたはその参照アセンブリの 1 つに組み込む必要があります。 この種類のアプリケーション データ ファイルは、*リソース ファイル*と呼ばれます。  
  
 リソース ファイルは、次のときに使用します。  
  
- コンパイルしてアセンブリに組み込んだ後に、リソース ファイルのコンテンツを更新する必要がない。  
  
- ファイルの依存関係の数を減らして、アプリケーション配布の複雑さを軽減する必要がある。  
  
- アプリケーション データ ファイルはローカライズ可能である必要があります[(「WPF のグローバリゼーションとローカリゼーションの概要](../advanced/wpf-globalization-and-localization-overview.md)」を参照)。  
  
> [!NOTE]
> このセクションで説明するリソース ファイルは[、XAML リソース](../../../desktop-wpf/fundamentals/xaml-resources-define.md)で説明されているリソース ファイルとは異なり、「[アプリケーション リソースの管理 (.NET)」](/visualstudio/ide/managing-application-resources-dotnet)で説明されている埋め込みリソースやリンクされたリソースとは異なります。  
  
### <a name="configuring-resource-files"></a>リソース ファイルの構成  
 WPF では、リソース ファイルは、Microsoft ビルド エンジン (MSBuild) プロジェクトに項目として`Resource`含まれているファイルです。  
  
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
> Visual Studio では、プロジェクトにファイルを追加し、そのファイルを に設定`Build Action`して`Resource`、リソース ファイルを作成します。  
  
 プロジェクトがビルドされると、MSBuild はリソースをアセンブリにコンパイルします。  
  
### <a name="using-resource-files"></a>リソース ファイルの使用  
 リソース ファイルを読み込むには、<xref:System.Windows.Application.GetResourceStream%2A>クラスのメソッド<xref:System.Windows.Application>を呼び出して、目的のリソース ファイルを識別する pack URI を渡します。 <xref:System.Windows.Application.GetResourceStream%2A>は、<xref:System.Windows.Resources.StreamResourceInfo>リソース ファイルを a<xref:System.IO.Stream>として公開し、そのコンテンツ タイプを記述するオブジェクトを返します。  
  
 たとえば、次の<xref:System.Windows.Application.GetResourceStream%2A>コードは、<xref:System.Windows.Controls.Page>リソース ファイルを読み込み、それを<xref:System.Windows.Controls.Frame>( )`pageFrame`の内容として設定する方法を示しています。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 呼び<xref:System.Windows.Application.GetResourceStream%2A>出しを使用すると<xref:System.IO.Stream>、 にアクセスできます。 代わりに、コードを使用して型のプロパティにリソース<xref:System.IO.Stream>ファイルを直接読み込むことで、 WPF でのを開いて変換できます。  
  
 コードを使用して ()<xref:System.Windows.Controls.Page><xref:System.Windows.Controls.Frame>`pageFrame`に直接読み込む方法を次の例に示します。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 次の例は、上の例と同じ意味のマークアップです。  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a>リソース ファイルとしてのアプリケーション コード ファイル  
 WPF アプリケーション コード ファイルの特別なセットは、ウィンドウ、ページ、フロー ドキュメント、リソース ディクショナリなど、pack URI を使用して参照できます。 たとえば、アプリケーションの起動時に<xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType>読み込むウィンドウまたはページを参照する pack URI を使用してプロパティを設定できます。  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 これは、XAML ファイルが項目として MSBuild プロジェクトに含まれている場合`Page`に実行できます。  
  
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
> Visual Studio では<xref:System.Windows.Window>、新しい<xref:System.Windows.Navigation.NavigationWindow>、 <xref:System.Windows.Controls.Page> <xref:System.Windows.Documents.FlowDocument>、、、または 、<xref:System.Windows.ResourceDictionary>プロジェクト`Build Action`を追加すると、マークアップ ファイル`Page`の が既定でに設定されます。  
  
 項目を含む`Page`プロジェクトがコンパイルされると、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]項目はバイナリ形式に変換され、関連付けられたアセンブリにコンパイルされます。 したがって、これらのファイルは、通常のリソース ファイルと同様に使用できます。  
  
> [!NOTE]
> ファイルが[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]`Resource`項目として構成され、分離コード ファイルがない場合、raw[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]は、raw[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]のバイナリ バージョンではなく、アセンブリにコンパイルされます。  
  
<a name="Content_Files"></a>
## <a name="content-files"></a>コンテンツ ファイル  
 *コンテンツ ファイル*は、実行可能アセンブリと共に、ルーズ ファイルとして配布されます。 コンテンツ ファイルはコンパイルされてアセンブリに組み込まれるのではありませんが、アセンブリのコンパイル時に、各コンテンツ ファイルとの関連付けを確立するメタデータが使用されます。  
  
 アプリケーションに必要な特定のアプリケーション データ ファイルのセットが更新されても、そのファイルを使用するアセンブリを再コンパイルせずに、コンテンツ ファイルを使用する必要があります。  
  
### <a name="configuring-content-files"></a>コンテンツ ファイルの構成  
 コンテンツ ファイルをプロジェクトに追加するには、アプリケーション データ ファイルを`Content`項目として含める必要があります。 さらに、コンテンツ ファイルはアセンブリに直接コンパイルされないため、MSBuild`CopyToOutputDirectory`メタデータ要素を設定して、ビルドされたアセンブリに対して相対的な場所にコンテンツ ファイルをコピーするように指定する必要があります。 プロジェクトをビルドするたびにリソースをビルド出力フォルダーにコピーする場合は、値をメタデータ要素に`CopyToOutputDirectory`設定します。 `Always` それ以外の場合は、値を使用`PreserveNewest`して、リソースの最新バージョンのみがビルド出力フォルダーにコピーされるようにすることができます。  
  
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
> Visual Studio では、プロジェクトにファイルを追加し、`Build Action`そのファイルを`Content`に設定してコンテンツ ファイルを`Copy to Output Directory`作成`Copy always`し、その`Always`ファイルを`Copy if newer`(`PreserveNewest`と 同じ ) に設定します。  
  
 プロジェクトがビルドされると、<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>属性は各コンテンツ ファイルのアセンブリのメタデータにコンパイルされます。  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 の値は、<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>プロジェクト内での位置を基準としたコンテンツ ファイルへのパスを意味します。 たとえば、コンテンツ ファイルがプロジェクトのサブフォルダにある場合、追加のパス情報が値に<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>組み込まれます。  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 この<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>値は、ビルド出力フォルダー内のコンテンツ ファイルへのパスの値でもあります。  
  
### <a name="using-content-files"></a>コンテンツ ファイルの使用  
 コンテンツ ファイルを読み込むには、<xref:System.Windows.Application.GetContentStream%2A>クラスのメソッド<xref:System.Windows.Application>を呼び出して、目的のコンテンツ ファイルを識別する pack URI を渡します。 <xref:System.Windows.Application.GetContentStream%2A>は、<xref:System.Windows.Resources.StreamResourceInfo>コンテンツ ファイルを a<xref:System.IO.Stream>として公開し、そのコンテンツ タイプを記述するオブジェクトを返します。  
  
 例として、次の<xref:System.Windows.Application.GetContentStream%2A>コードは、<xref:System.Windows.Controls.Page>コンテンツ ファイルを読み込み、それを<xref:System.Windows.Controls.Frame>( )`pageFrame`のコンテンツとして設定する方法を示しています。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 呼び<xref:System.Windows.Application.GetContentStream%2A>出しを使用すると<xref:System.IO.Stream>、 にアクセスできます。 代わりに、コードを使用して型のプロパティにリソース<xref:System.IO.Stream>ファイルを直接読み込むことで、 WPF でのを開いて変換できます。  
  
 コードを使用して ()<xref:System.Windows.Controls.Page><xref:System.Windows.Controls.Frame>`pageFrame`に直接読み込む方法を次の例に示します。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 次の例は、上の例と同じ意味のマークアップです。  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>
## <a name="site-of-origin-files"></a>起点サイト ファイル  
 リソース ファイルは、で定義されているとおりに、配布されるアセンブリと明示的に関係しています<xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>。 ただし、アセンブリとアプリケーション データ ファイル間に暗黙的な関係を持たせる、または関係を持たせない場合があります。たとえば次のような場合です。  
  
- コンパイル時にファイルが存在しません。  
  
- アセンブリが必要とするファイルが、実行時までわからない場合。  
  
- 関連付けられているアセンブリを再コンパイルせずにファイルを更新可能にする場合。  
  
- オーディオやビデオなど大容量のデータ ファイルを使用するアプリケーションで、ユーザーが選択した場合にのみファイルをダウンロードする場合。  
  
 file:///やhttp://スキームなどの従来の URI スキームを使用して、これらの種類のファイルを読み込むことができます。  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 ただし、file:/// スキームや http:// スキームを使用する場合は、アプリケーションに完全信頼が必要です。 アプリケーションがインターネットまたはイントラネットから起動された XAML ブラウザー アプリケーション (XBAP) であり、その場所から起動されたアプリケーションに許可されているアクセス許可のセットのみを要求する場合、ルーズ ファイルは、アプリケーションの起点のサイト(起動場所)。 このようなファイルは、*サイトの起点*ファイルとして知られています。  
  
 起点サイト ファイルは部分信頼アプリケーションの唯一のオプションですが、部分信頼アプリケーション以外でも使用できます。 完全信頼アプリケーションでも、読み込むアプリケーション データ ファイルがビルド時点では不明な場合があります。完全信頼アプリケーションでは file:/// を使用できますが、アプリケーション データ ファイルがアプリケーション アセンブリと同じフォルダーにインストールされることも、サブフォルダーにインストールされることも考えられます。 この場合は、起点サイト参照を使用する方が、file:/// を使用するよりも簡単です。file:/// を使用するには、ファイルの完全パスを指定する必要があるためです。  
  
> [!NOTE]
> コンテンツ ファイルが格納されている間、サイトの起点ファイルは、XAML ブラウザー アプリケーション (XBAP) をクライアント コンピューターにキャッシュされません。 したがって、起点サイト ファイルは明確に要求されたときにのみダウンロードされます。 XAML ブラウザー アプリケーション (XBAP) アプリケーションに大きなメディア ファイルがある場合、それらをサイト のサイト ファイルとして構成すると、アプリケーションの最初の起動がはるかに高速になり、ファイルはオンデマンドでのみダウンロードされます。  
  
### <a name="configuring-site-of-origin-files"></a>起点サイト ファイルの構成  
 サイトのファイルがコンパイル時に存在しない場合や不明な場合は、`XCopy`コマンド ライン プログラムや Microsoft Windows インストーラを使用するなど、実行時に必要なファイルを使用できるようにするための従来の展開メカニズムを使用する必要があります。  
  
 コンパイル時に、元のサイトに配置するファイルがわかっているが、明示的な依存関係を回避したい場合は、それらのファイルを項目として`None`MSBuild プロジェクトに追加できます。 コンテンツ ファイルと同様に、MSBuild`CopyToOutputDirectory`属性を設定して、`Always`作成元のサイト ファイルを、ビルド`PreserveNewest`したアセンブリに対して相対的な場所にコピーするように指定する必要があります。  
  
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
> Visual Studio では、プロジェクトにファイルを追加し、ファイルを に設定して、サイト`Build Action`の`None`サイト ファイルを作成します。  
  
 プロジェクトがビルドされると、指定したファイルがビルド出力フォルダーにコピーされます。  
  
### <a name="using-site-of-origin-files"></a>起点サイト ファイルの使用  
 サイトの起点ファイルをロードするには、クラスのメソッド<xref:System.Windows.Application.GetRemoteStream%2A>を<xref:System.Windows.Application>呼び出して、目的のサイトの起点ファイルを識別するパック URI を渡します。 <xref:System.Windows.Application.GetRemoteStream%2A>は、<xref:System.Windows.Resources.StreamResourceInfo>サイトのサイト ファイルを a<xref:System.IO.Stream>として公開し、そのコンテンツ タイプを記述するオブジェクトを返します。  
  
 たとえば、次の<xref:System.Windows.Application.GetRemoteStream%2A>コードは、<xref:System.Windows.Controls.Page>サイトの起点ファイルを読み込み、それを<xref:System.Windows.Controls.Frame>( )`pageFrame`の内容として設定する方法を示しています。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 呼び<xref:System.Windows.Application.GetRemoteStream%2A>出しを使用すると<xref:System.IO.Stream>、 にアクセスできます。 代わりに、コードを使用して型のプロパティにリソース<xref:System.IO.Stream>ファイルを直接読み込むことで、 WPF でのを開いて変換できます。  
  
 コードを使用して ()<xref:System.Windows.Controls.Page><xref:System.Windows.Controls.Frame>`pageFrame`に直接読み込む方法を次の例に示します。  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 次の例は、上の例と同じ意味のマークアップです。  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>
## <a name="rebuilding-after-changing-build-type"></a>ビルドの種類を変更した後のリビルド  
 アプリケーション データ ファイルのビルドの種類を変更した後は、変更を確実に反映するためにアプリケーション全体をリビルドする必要があります。 アプリケーションのみをビルドしても、変更は適用されません。  
  
## <a name="see-also"></a>関連項目

- [WPF におけるパッケージの URI](pack-uris-in-wpf.md)
