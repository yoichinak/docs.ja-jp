---
title: マージされたリソース ディクショナリ
ms.date: 03/30/2017
helpviewer_keywords:
- merged resource dictionaries [WPF]
- dictionaries [WPF], merged resources
ms.assetid: d159531f-05d4-49fd-b951-c332de51e5bc
ms.openlocfilehash: 17dd8e0c02d71fc7e72800fc578866188d03060e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053250"
---
# <a name="merged-resource-dictionaries"></a>マージされたリソース ディクショナリ
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] リソースでは、マージされたリソース ディクショナリ機能がサポートされます。 この機能を使用すると、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションのリソース部分を、コンパイル済み [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] アプリケーションの外部で定義できます。 その後、リソースをアプリケーション間で共有できます。また、ローカライズ用に簡単に切り分けることができます。  
  
## <a name="introducing-a-merged-resource-dictionary"></a>マージされたリソース ディクショナリの導入  
 マークアップでは、マージされたリソース ディクショナリをページに導入するために次の構文を使います。  
  
 [!code-xaml[ResourceMergeDictionary#MergedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/ResourceMergeDictionary/CS/default.xaml#mergedxaml)]  
  
 なお、<xref:System.Windows.ResourceDictionary>要素がありません、 [X:key ディレクティブ](../../xaml-services/x-key-directive.md)、一般に、リソース コレクション内のすべての項目に必要な。 もう 1 つ<xref:System.Windows.ResourceDictionary>内で参照、<xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>コレクションは、特別な場合は、このマージされたリソース ディクショナリのシナリオ用に予約されています。 <xref:System.Windows.ResourceDictionary>導入をマージするリソース ディクショナリを持つことはできません、 [X:key ディレクティブ](../../xaml-services/x-key-directive.md)します。 通常、各<xref:System.Windows.ResourceDictionary>内、<xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>コレクションを指定します、<xref:System.Windows.ResourceDictionary.Source%2A>属性。 値<xref:System.Windows.ResourceDictionary.Source%2A>する必要があります、[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]マージするリソース ファイルの場所に解決されます。 その宛先[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]別である必要があります[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイルで<xref:System.Windows.ResourceDictionary>のルート要素として。  
  
> [!NOTE]
>  内のリソースを定義することは、<xref:System.Windows.ResourceDictionary>として指定する代わりに、マージされたディクショナリとして指定されている<xref:System.Windows.ResourceDictionary.Source%2A>、またはこれに加えて、指定したソースからすべてのリソースが含まれています。 ただし、これは一般的なシナリオではありません。マージされたディクショナリの主要なシナリオは、外部ファイルの場所からリソースをマージすることです。 ページのマークアップ内のリソースを指定する場合が通常定義するこれらのメイン<xref:System.Windows.ResourceDictionary>マージされたディクショナリではなく、します。  
  
## <a name="merged-dictionary-behavior"></a>マージされたディクショナリの動作  
 マージされたディクショナリ内のリソースは、それらのリソースがマージされる先のメイン リソース ディクショナリのスコープの直後のリソース参照スコープの場所全体を占めます。 リソース キーは個々のディクショナリ内で一意である必要がありますが、マージされたディクショナリのセット内に 1 つのキーが複数回存在してもかまいません。 この場合、返されるリソースは、最後に順番にで見つかるディクショナリから取られます、<xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>コレクション。 場合、<xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>コレクションを定義した[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]マークアップで指定された、コレクション内でマージされたディクショナリの順序は、要素の順序。 プライマリ ディクショナリ内とマージされたディクショナリ内の両方でキーが定義されている場合、返されるリソースはプライマリ ディクショナリから取られます。 これらのスコープ規則は、静的なリソース参照と動的なリソース参照の両方に等しく適用されます。  
  
### <a name="merged-dictionaries-and-code"></a>マージされたディクショナリとコード  
 マージされたディクショナリは、コードを使って `Resources` ディクショナリに追加できます。 既定は、最初は空<xref:System.Windows.ResourceDictionary>のいずれかに存在する`Resources`プロパティが、既定で、最初は空にも<xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>プロパティのコレクション。 目的のプライマリへの参照を取得するコードをマージされたディクショナリを追加するに<xref:System.Windows.ResourceDictionary>、取得、<xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>プロパティの値、および呼び出し`Add`、汎用`Collection`に格納されている<xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>します。 新しいオブジェクトを追加する必要があります<xref:System.Windows.ResourceDictionary>します。 コードでは、設定しない、<xref:System.Windows.ResourceDictionary.Source%2A>プロパティ。 代わりに、取得する必要があります、<xref:System.Windows.ResourceDictionary>オブジェクトを作成するか、いずれかをロードします。 既存の読み込みに 1 つの方法<xref:System.Windows.ResourceDictionary>を呼び出す<xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>既存の[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイル ストリームを持つ、<xref:System.Windows.ResourceDictionary>キャストし、ルート、<xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType>に値を返す<xref:System.Windows.ResourceDictionary>します。  
  
### <a name="merged-resource-dictionary-uris"></a>マージされたリソース ディクショナリの URI  
 マージされたリソース ディクショナリを組み込むには、いくつかの手法があります。マージされたリソース ディクショナリは、お使いの [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] 形式で示されます。 大まかに言えば、これらの手法は 2 つのカテゴリに分類できます。プロジェクトの一部としてコンパイルされるリソースと、プロジェクトの一部としてコンパイルされないリソースです。  
  
 プロジェクトの一部としてコンパイルされるリソースの場合は、リソースの場所を参照する相対パスを使うことができます。 相対パスは、コンパイル中に評価されます。 リソースは、リソースのビルド アクションでプロジェクトの一部として定義する必要があります。 リソースの .xaml ファイルをリソースとしてプロジェクトに組み込む場合は、リソース ファイルを出力ディレクトリにコピーする必要がありません。リソースは、コンパイルされたアプリケーション内にあらかじめ組み込まれます。 コンテンツのビルド アクションを使うこともできますが、その場合は、ファイルを出力ディレクトリにコピーして、実行可能ファイルに対して同じパスにリソース ファイルを配置する必要があります。  
  
> [!NOTE]
>  埋め込みリソースのビルド アクションは使用しないでください。 ビルド アクション自体がサポートされている[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、アプリケーションがの解像度<xref:System.Windows.ResourceDictionary.Source%2A>組み込まれない<xref:System.Resources.ResourceManager>、したがって、ストリームから個々 のリソースを分離することはできません。 その他のためにも使用するように、埋め込みリソースを使用することもでした<xref:System.Resources.ResourceManager>リソースにアクセスします。  
  
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
