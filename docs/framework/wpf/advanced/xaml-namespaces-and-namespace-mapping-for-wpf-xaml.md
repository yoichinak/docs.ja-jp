---
title: XAML 名前空間および WPF XAML の名前空間の割り当て
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom classes [WPF], mapping namespaces to
- XAML [WPF], namespaces
- namespace mapping [WPF]
- assemblies [WPF], mapping namespaces to
- mapping namespaces [WPF]
- XAML [WPF], namespace mapping
- classes [WPF], mapping namespaces to
- namespaces [WPF]
ms.assetid: 5c0854e3-7470-435d-9fe2-93eec9d3634e
ms.openlocfilehash: 4fc88f1e32b8ddce6abccad085b0c44a5c716e8b
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400806"
---
# <a name="xaml-namespaces-and-namespace-mapping-for-wpf-xaml"></a>XAML 名前空間および WPF XAML の名前空間の割り当て
このトピックでは、WPF XAML ファイルのルートタグでよく見られる2つの XAML 名前空間マッピングの存在と目的について詳しく説明します。 また、独自のコードで定義されている要素、または別のアセンブリ内に定義されている要素を使用するために、同様のマッピングを生成する方法についても説明します。  

## <a name="what-is-a-xaml-namespace"></a>XAML 名前空間とは何ですか。  
 XAML 名前空間は、実際には XML 名前空間の概念を拡張したものです。 XAML 名前空間を指定する方法は、XML 名前空間の構文、Uri を名前空間の識別子として使用する規則、同じマークアップソースから複数の名前空間を参照する手段を提供するプレフィックスを使用する方法などに依存します。 XML 名前空間の XAML 定義に追加される主な概念は、XAML 名前空間がマークアップ使用の一意性の範囲を示すことです。また、特定の CLR 名前空間および参照によってマークアップエンティティがどのようにサポートされるかにも影響します。アセンブリ. この2つ目の考慮事項は、XAML スキーマコンテキストの概念にも影響を受けます。 ただし、WPF で XAML 名前空間を使用する方法については、一般に、xaml 名前空間、xaml 言語の名前空間、および XAML マークアップによって特定のバッキング CLR に直接マップされる xaml 名前空間に関して、xaml 名前空間について考えることができます。名前空間と参照されるアセンブリ。  
  
<a name="The_WPF_and_XAML_Namespace_Declarations"></a>   
## <a name="the-wpf-and-xaml-namespace-declarations"></a>WPF および XAML 名前空間の宣言  
 多くの XAML ファイルのルートタグ内の名前空間宣言内では、通常、2つの XML 名前空間宣言があることがわかります。 最初の宣言は、WPF クライアント/フレームワークの全体的な XAML 名前空間を既定値としてマップします。  
  
 `xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`  
  
 2番目の宣言は、別の XAML 名前空間をマップし、 `x:`これを (通常は) プレフィックスに割り当てます。  
  
 `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 これらの宣言の間の関係は`x:` 、プレフィックスマッピングが xaml 言語定義の一部である組み込みをサポートする[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ことです。また、xaml を言語として使用する1つの実装で、XAML のオブジェクト。 WPF のボキャブラリの使用は XAML 組み込みの使用法よりはるかに一般的であるため、WPF のボキャブラリは既定値としてマップされます。  
  
 XAML 言語の組み込みサポートをマップするための[!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)]プレフィックス規則には、プロジェクトテンプレート、サンプルコード、およびこの内の言語機能のドキュメントが続きます。`x:` XAML 名前空間は、基本的な WPF アプリケーションでも必要な一般的に使用される多くの機能を定義します。 たとえば、部分クラスを使用して xaml ファイルに分離コードを結合するには、そのクラスに関連する xaml ファイルの`x:Class`ルート要素の属性として名前を付ける必要があります。 または、キー付きリソースとしてアクセスする XAML ページで定義されている要素は、 `x:Key`対象の要素に対して属性を設定する必要があります。 これらの XAML の詳細については、「 [xaml の概要 (WPF)](xaml-overview-wpf.md) 」または「 [Xaml 構文の詳細](xaml-syntax-in-detail.md)」を参照してください。  
  
<a name="Mapping_To_Custom_Classes_and_Assemblies"></a>   
## <a name="mapping-to-custom-classes-and-assemblies"></a>カスタムクラスとアセンブリへのマッピング  
 `xmlns`プレフィックス宣言内の一連のトークンを使用して、XML 名前空間をアセンブリにマップできます。これは、標準の WPF および xaml 組み込みの xaml 名前空間をプレフィックスにマップする方法と似ています。  
  
 構文では、次の名前付きトークンと次の値を使用できます。  
  
 `clr-namespace:`要素として公開するパブリック型を格納しているアセンブリ内で宣言されている CLR 名前空間。  
  
 `assembly=`参照されている CLR 名前空間の一部またはすべてを含むアセンブリ。 通常、この値はパスではなくアセンブリの名前にすぎず、拡張子 (.dll や .exe など) は含まれません。 このアセンブリへのパスは、マップしようとしている XAML を含むプロジェクトファイル内のプロジェクト参照として設定する必要があります。 バージョン管理と厳密な名前の署名`assembly`を組み込むために、値には、単純な文字列名ではなく、で<xref:System.Reflection.AssemblyName>定義されている文字列を指定できます。  
  
 `clr-namespace`トークンを値から区切る文字がコロン (:) であることに注意してください。一方、トークンを`assembly`値から区切る文字は等号 (=) です。 これら2つのトークンの間で使用する文字はセミコロンです。 また、宣言のどこにも空白を入れないでください。  
  
### <a name="a-basic-custom-mapping-example"></a>基本的なカスタムマッピングの例  
 次のコードでは、カスタムクラスの例を定義しています。  
  
```csharp  
namespace SDKSample {  
    public class ExampleClass : ContentControl {  
        public ExampleClass() {  
        ...  
        }  
    }  
}  
```  
  
```vb  
Namespace SDKSample  
    Public Class ExampleClass  
        Inherits ContentControl  
         ...  
        Public Sub New()  
        End Sub  
    End Class  
End Namespace  
```  
  
 このカスタムクラスは、プロジェクト設定 (図に示されていません) ごとにという`SDKSampleLibrary`名前のライブラリにコンパイルされます。  
  
 このカスタムクラスを参照するには、現在のプロジェクトの参照としても含める必要があります。これは通常、Visual Studio のソリューションエクスプローラー UI を使用します。  
  
 クラスが含まれているライブラリと、プロジェクト設定にそのライブラリへの参照があるので、次のプレフィックスマッピングを XAML のルート要素の一部として追加できます。  
  
 `xmlns:custom="clr-namespace:SDKSample;assembly=SDKSampleLibrary"`  
  
 すべてをまとめて配置するには、次の XAML を使用します。これには、ルートタグ内の一般的な default および x: マッピングと共にカスタム`ExampleClass`マッピングが含まれます。その後、プレフィックス付きの参照を使用して、その UI でインスタンス化します。  
  
```xaml  
<Page x:Class="WPFApplication1.MainPage"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"   
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:custom="clr-namespace:SDKSample;assembly=SDKSampleLibrary">  
  ...  
  <custom:ExampleClass/>  
...  
</Page>  
```  
  
### <a name="mapping-to-current-assemblies"></a>現在のアセンブリへのマッピング  
 `assembly`参照先のが、 `clr-namespace`カスタムクラスを参照しているアプリケーションコードと同じアセンブリ内に定義されている場合は、を省略できます。 または、この場合と同等の構文では`assembly=`、等号の後に文字列トークンを指定せずに、を指定します。  
  
 カスタムクラスは、同じアセンブリ内で定義されている場合、ページのルート要素として使用することはできません。 部分クラスをマップする必要はありません。XAML の要素として参照する場合は、アプリケーション内のページの部分クラスではないクラスのみをマップする必要があります。  
  
<a name="Mapping_CLR_Namespaces_to_XML_Namespaces_in_an"></a>   
## <a name="mapping-clr-namespaces-to-xml-namespaces-in-an-assembly"></a>アセンブリ内の XML 名前空間への CLR 名前空間のマッピング  
 WPF では、複数の CLR 名前空間を1つの XAML 名前空間にマップするために XAML プロセッサによって使用される CLR 属性を定義します。 この属性<xref:System.Windows.Markup.XmlnsDefinitionAttribute>は、アセンブリを生成するソースコードのアセンブリレベルに配置されます。 WPF アセンブリソースコードは、この属性を使用して<xref:System.Windows> 、や<xref:System.Windows.Controls>などのさまざまな共通名前空間[!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)]を名前空間にマップします。  
  
 は<xref:System.Windows.Markup.XmlnsDefinitionAttribute> 、XML/XAML 名前空間名と CLR 名前空間名の2つのパラメーターを受け取ります。 複数の CLR 名前空間を同じ XML 名前空間にマップするために、複数存在することができます。<xref:System.Windows.Markup.XmlnsDefinitionAttribute> マッピングが完了すると、部分クラスの分離コードページに適切な`using`ステートメントを指定することで、必要に応じて完全修飾なしでこれらの名前空間のメンバーを参照することもできます。 詳細については、「<xref:System.Windows.Markup.XmlnsDefinitionAttribute>」を参照してください。  
  
## <a name="designer-namespaces-and-other-prefixes-from-xaml-templates"></a>デザイナーの名前空間と XAML テンプレートからのその他のプレフィックス  
 WPF XAML 用の開発環境やデザインツールで作業している場合は、xaml マークアップ内に他の定義済みの XAML 名前空間/プレフィックスがあることがわかります。  
  
 [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)]は、通常、プレフィックス`d:`にマップされているデザイナーの名前空間を使用します。 WPF の新しいプロジェクトテンプレートでは、この xaml 名前空間を事前にマップして、と[!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)]他のデザイン環境間での xaml のインターチェンジをサポートすることができます。 このデザインの XAML 名前空間は、デザイナーの XAML ベースの UI を roundtripping しながら、デザイン状態を perpetuate するために使用されます。 また`d:IsDataSource`、デザイナーでランタイムデータソースを有効にするなどの機能にも使用されます。  
  
 マップされていると思わ`mc:`れるもう1つのプレフィックスはです。 `mc:`は、マークアップ互換性のためのものであり、必ずしも XAML 固有ではないマークアップ互換性パターンを利用しています。 また、マークアップ互換性機能を使用して、フレームワーク間、またはバッキング実装の他の境界間で XAML を交換したり、XAML スキーマコンテキスト間で作業したり、デザイナーで制限されたモードの互換性を提供したりすることができます。 マークアップ互換性の概念と WPF との関係の詳細について[は、「マークアップの互換性 (mc:)」を参照してください。言語機能](markup-compatibility-mc-language-features.md)。  
  
## <a name="wpf-and-assembly-loading"></a>WPF とアセンブリの読み込み  
 WPF の XAML スキーマコンテキストは WPF アプリケーションモデルと統合され、さらにの<xref:System.AppDomain>CLR 定義概念が使用されます。 次に、XAML スキーマコンテキストで、WPF の<xref:System.AppDomain>使用方法やその他の要因に基づいて、アセンブリを読み込む方法、または実行時に型を検索する方法について説明します。  
  
1. を反復処理し、最後に読み込まれたアセンブリから開始して、名前のすべての側面に一致する、既に読み込まれているアセンブリを探します。<xref:System.AppDomain>  
  
2. 名前が修飾されている<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>場合は、修飾名でを呼び出します。  
  
3. 修飾名の短い名前と公開キートークンが、マークアップが読み込まれたアセンブリと一致する場合は、そのアセンブリを返します。  
  
4. を呼び出す<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>には、短い名前と公開キートークンを使用します。  
  
5. 名前が修飾されてい<xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>ない場合は、を呼び出します。  
  
 ルース XAML では、手順 3; が使用されません。アセンブリが読み込まれていません。  
  
 WPF 用にコンパイルされた XAML (xamlbuildtask を使用して生成) では<xref:System.AppDomain> 、既に読み込まれているアセンブリ (手順 1) は使用されません。 また、XamlBuildTask の出力から名前を修飾しないでください。そのため、手順5は適用されません。  
  
 (プレゼンテーション Buildtask によって生成される) コンパイル済みの BAML はすべての手順を使用しますが、BAML には修飾されていないアセンブリ名を含めることはできません。  
  
## <a name="see-also"></a>関連項目

- [XML 名前空間について](https://go.microsoft.com/fwlink/?LinkId=98069)
- [XAML の概要 (WPF)](xaml-overview-wpf.md)
