---
title: マージされたリソース ディクショナリ
ms.date: 03/30/2017
helpviewer_keywords:
- merged resource dictionaries [WPF]
- dictionaries [WPF], merged resources
ms.assetid: d159531f-05d4-49fd-b951-c332de51e5bc
ms.openlocfilehash: 466a18a58acfebf6d779a1d0eba3d2637743806e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911723"
---
# <a name="merged-resource-dictionaries"></a>マージされたリソース ディクショナリ
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] リソースでは、マージされたリソース ディクショナリ機能がサポートされます。 この機能を使用すると、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションのリソース部分を、コンパイル済み [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] アプリケーションの外部で定義できます。 その後、リソースをアプリケーション間で共有できます。また、ローカライズ用に簡単に切り分けることができます。  
  
## <a name="introducing-a-merged-resource-dictionary"></a>マージされたリソース ディクショナリの導入  
 マークアップでは、マージされたリソース ディクショナリをページに導入するために次の構文を使います。  
  
 [!code-xaml[ResourceMergeDictionary#MergedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceMergeDictionary/CS/default.xaml#mergedxaml)]  
  
 要素に<xref:System.Windows.ResourceDictionary>は[x:Key ディレクティブ](../../xaml-services/x-key-directive.md)がないことに注意してください。これは、リソースコレクション内のすべての項目に対して通常必要となります。 ただし、 <xref:System.Windows.ResourceDictionary> <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>コレクション内の別の参照は特殊なケースで、このマージされたリソースディクショナリのシナリオ用に予約されています。 マージ<xref:System.Windows.ResourceDictionary>されたリソースディクショナリを導入するには、 [x:Key ディレクティブ](../../xaml-services/x-key-directive.md)を含めることはできません。 通常、 <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>コレクション<xref:System.Windows.ResourceDictionary>内の各は<xref:System.Windows.ResourceDictionary.Source%2A>属性を指定します。 の<xref:System.Windows.ResourceDictionary.Source%2A>値は、 [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]マージされるリソースファイルの場所に解決されるである必要があります。 をルート要素<xref:System.Windows.ResourceDictionary>とする別[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]のファイルにする必要がある。[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]  
  
> [!NOTE]
> を指定<xref:System.Windows.ResourceDictionary> <xref:System.Windows.ResourceDictionary.Source%2A>する代わりとして、または指定したソースに含まれるリソースに加えて、マージされたディクショナリとして指定された内のリソースを定義することは有効です。 ただし、これは一般的なシナリオではありません。マージされたディクショナリの主要なシナリオは、外部ファイルの場所からリソースをマージすることです。 ページのマークアップ内にリソースを指定する場合は、通常、マージされたディクショナリで<xref:System.Windows.ResourceDictionary>はなく、メインでこれらを定義する必要があります。  
  
## <a name="merged-dictionary-behavior"></a>マージされたディクショナリの動作  
 マージされたディクショナリ内のリソースは、それらのリソースがマージされる先のメイン リソース ディクショナリのスコープの直後のリソース参照スコープの場所全体を占めます。 リソース キーは個々のディクショナリ内で一意である必要がありますが、マージされたディクショナリのセット内に 1 つのキーが複数回存在してもかまいません。 この場合、返されるリソースは、 <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>コレクション内で最後に見つかったディクショナリから取得されます。 コレクションがで[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]定義されている場合、コレクション内のマージされたディクショナリの順序は、マークアップで指定された要素の順序になります。 <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> プライマリ ディクショナリ内とマージされたディクショナリ内の両方でキーが定義されている場合、返されるリソースはプライマリ ディクショナリから取られます。 これらのスコープ規則は、静的なリソース参照と動的なリソース参照の両方に等しく適用されます。  
  
### <a name="merged-dictionaries-and-code"></a>マージされたディクショナリとコード  
 マージされたディクショナリは、コードを使って `Resources` ディクショナリに追加できます。 既定では、すべて<xref:System.Windows.ResourceDictionary> `Resources`のプロパティに存在する空の既定値には、 <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>既定の空のコレクションプロパティもあります。 コードを使用してマージされたディクショナリを追加するには、 <xref:System.Windows.ResourceDictionary>目的のプライマリ<xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>への参照を取得し、その`Collection`プロパティ値を取得<xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>して、に格納されているジェネリックに対してを呼び出し`Add`ます。 追加するオブジェクトは、新しい<xref:System.Windows.ResourceDictionary>である必要があります。 コードでは、 <xref:System.Windows.ResourceDictionary.Source%2A>プロパティを設定しません。 代わりに、オブジェクトを作成する<xref:System.Windows.ResourceDictionary>か、オブジェクトを読み込むことによって、オブジェクトを取得する必要があります。 <xref:System.Windows.ResourceDictionary>既存のを読み込み、ルートを<xref:System.Windows.ResourceDictionary>持つ<xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>既存[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]のファイルストリームでを呼び出すための1つの<xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>方法。その<xref:System.Windows.ResourceDictionary>後、戻り値をにキャストします。  
  
### <a name="merged-resource-dictionary-uris"></a>マージされたリソース ディクショナリの URI  
 マージされたリソース ディクショナリを組み込むには、いくつかの手法があります。マージされたリソース ディクショナリは、お使いの [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] 形式で示されます。 大まかに言えば、これらの手法は 2 つのカテゴリに分類できます。プロジェクトの一部としてコンパイルされるリソースと、プロジェクトの一部としてコンパイルされないリソースです。  
  
 プロジェクトの一部としてコンパイルされるリソースの場合は、リソースの場所を参照する相対パスを使うことができます。 相対パスは、コンパイル中に評価されます。 リソースは、リソースのビルド アクションでプロジェクトの一部として定義する必要があります。 リソースの .xaml ファイルをリソースとしてプロジェクトに組み込む場合は、リソース ファイルを出力ディレクトリにコピーする必要がありません。リソースは、コンパイルされたアプリケーション内にあらかじめ組み込まれます。 コンテンツのビルド アクションを使うこともできますが、その場合は、ファイルを出力ディレクトリにコピーして、実行可能ファイルに対して同じパスにリソース ファイルを配置する必要があります。  
  
> [!NOTE]
> 埋め込みリソースのビルド アクションは使用しないでください。 ビルドアクション自体は[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションでサポートされていますが、の<xref:System.Windows.ResourceDictionary.Source%2A>解決<xref:System.Resources.ResourceManager>には組み込まれていないため、個々のリソースをストリームから分離することはできません。 リソースへのアクセスにも使用<xref:System.Resources.ResourceManager>している限り、埋め込みリソースを他の目的に使用することもできます。  
  
 これと関連して、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイルに対するパック URI を使い、その URI をソースとして参照する手法もあります。 パック URI を使用すると、参照したアセンブリのコンポーネントを参照したり、その他の手法を利用したりできます。 パック URI の詳細については、「[WPF アプリケーションのリソース ファイル、コンテンツ ファイル、およびデータ ファイル](../app-development/wpf-application-resource-content-and-data-files.md)」を参照してください。  
  
 プロジェクトの一部としてコンパイルされないリソースでは、URI が実行時に評価されます。 リソース ファイルを参照するために、file: や http: などの一般的な URI トランスポートを使うことができます。 コンパイルされないリソースの手法を使うことの欠点は、file: アクセスには追加の配置手順が必要になることと、http: アクセスはインターネット セキュリティ ゾーンを意味することです。  
  
### <a name="reusing-merged-dictionaries"></a>マージされたディクショナリの再利用  
 マージするリソース ディクショナリは、すべての有効な [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] を使って参照できるため、マージされたリソース ディクショナリをアプリケーション間で再利用または共有することができます。 これを行うための具体的な方法は、アプリケーションの配置方法と、採用するアプリケーション モデルによって異なります。 前述のパック URI の手法を使うと、開発中にアセンブリ参照を共有することにより、マージされたリソースを複数のプロジェクトから取得する一般的な方法を利用することができます。 このシナリオでは、リソースはまだクライアントによって配布されるため、少なくとも 1 つのアプリケーションで参照先のアセンブリを配置する必要があります。 また、http プロトコルを使う分散 URI によって、マージされたリソースを参照することもできます。  
  
 マージされたディクショナリ/アプリケーションの配置で考えられる別のシナリオは、マージされたディクショナリをローカル アプリケーション ファイルとして、またはローカルの共有記憶域に書き出すことです。  
  
### <a name="localization"></a>ローカリゼーション  
 ローカライズする必要のあるリソースが、プライマリ ディクショナリにマージされたディクショナリに分離されて、Loose [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイルとして保持されている場合、これらのファイルを別個にローカライズすることができます。 これは、サテライト リソース アセンブリをローカライズするよりも簡易な手法です。 詳細については、「[WPF のグローバリゼーションおよびローカリゼーションの概要](wpf-globalization-and-localization-overview.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.ResourceDictionary>
- [XAML リソース](xaml-resources.md)
- [リソースとコード](resources-and-code.md)
- [WPF アプリケーションのリソース ファイル、コンテンツ ファイル、およびデータ ファイル](../app-development/wpf-application-resource-content-and-data-files.md)
