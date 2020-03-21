---
title: XAML 名前空間と名前空間マッピング
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
ms.openlocfilehash: 9b01643e8f8d77073595253580ebea60fabfd23b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186234"
---
# <a name="xaml-namespaces-and-namespace-mapping-for-wpf-xaml"></a>XAML 名前空間および WPF XAML の名前空間の割り当て
このトピックでは、WPF XAML ファイルのルート タグでよく見られる 2 つの XAML 名前空間マッピングの存在と目的についてさらに説明します。 また、独自のコードで定義された要素や、個別のアセンブリ内で定義されている要素を使用するための同様のマッピングを生成する方法についても説明します。  

## <a name="what-is-a-xaml-namespace"></a>XAML 名前空間とは何ですか?  
 XAML 名前空間は、XML 名前空間の概念の拡張です。 XAML 名前空間を指定する手法は、XML 名前空間構文、名前空間識別子として URI を使用する規則、プレフィックスを使用して、同じマークアップ ソースから複数の名前空間を参照する手段などを使用します。 XML 名前空間の XAML 定義に追加される主な概念は、XAML 名前空間はマークアップの使用に対して一意性のスコープを意味し、マークアップ エンティティが特定の CLR 名前空間によって潜在的にサポートされ、参照される方法に影響を与えるということです。アセンブリ。 この後者の考慮事項は、XAML スキーマ コンテキストの概念によっても影響されます。 しかし、WPF が XAML 名前空間を使用する方法を目的として、XAML 名前空間は、通常、既定の XAML 名前空間、XAML 言語名前空間、および XAML マークアップによって特定のバッキング CLR に直接マップされた XAML 名前空間を考えることができます。名前空間と参照アセンブリ。  
  
<a name="The_WPF_and_XAML_Namespace_Declarations"></a>
## <a name="the-wpf-and-xaml-namespace-declarations"></a>WPF 名前空間宣言と XAML 名前空間宣言  
 多くの XAML ファイルのルート タグ内の名前空間宣言内では、通常 2 つの XML 名前空間宣言があることがわかります。 最初の宣言では、WPF クライアント /フレームワーク XAML 名前空間全体が既定としてマップされます。  
  
 `xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`  
  
 2 番目の宣言は、個別の XAML 名前空間をマップし`x:`、(通常は) プレフィックスに対応付けます。  
  
 `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 これらの宣言間の関係は、`x:`プレフィックス マッピングが XAML 言語定義の一部である組み込み関数[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]をサポートし、XAML を言語として使用し、XAML のオブジェクトのボキャブラリを定義する 1 つの実装です。 WPF ボキャブラリの使用法は XAML 組み込み関数の使用法よりもはるかに一般的であるため、WPF ボキャブラリは既定としてマップされます。  
  
 XAML`x:`言語組み込みサポートをマッピングするためのプレフィックス規則の後には、プロジェクト テンプレート、サンプル コード、およびこの SDK 内の言語機能のドキュメントが続きます。 XAML 名前空間は、基本的な WPF アプリケーションにも必要な、一般的に使用される多くの機能を定義します。 たとえば、部分クラスを通じて分離コードを XAML ファイルに結合するには、関連する XAML ファイルのルート要素`x:Class`の属性としてそのクラスに名前を付ける必要があります。 または、キー付きリソースとしてアクセスする XAML ページで定義されている要素には、対象の`x:Key`要素に属性が設定されている必要があります。 XAML のこれらの側面と他の側面の詳細については、「 [XAML の概要 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)または[XAML 構文の詳細](xaml-syntax-in-detail.md)」を参照してください。  
  
<a name="Mapping_To_Custom_Classes_and_Assemblies"></a>
## <a name="mapping-to-custom-classes-and-assemblies"></a>カスタム クラスおよびカスタム アセンブリへのマッピング  
 標準 WPF および XAML 組み込み XAML 名前空間`xmlns`がプレフィックスにマップされるのと同様に、プレフィックス宣言内の一連のトークンを使用して、XML 名前空間をアセンブリにマップできます。  
  
 構文には、次の名前付きトークンと次の値が使用されます。  
  
 `clr-namespace:`要素として公開するパブリック型を含むアセンブリ内で宣言された CLR 名前空間。  
  
 `assembly=`参照先 CLR 名前空間の一部またはすべてを含むアセンブリ。 この値は、通常、パスではなく、アセンブリの名前に過ぎず、拡張子 (.dll や .exe など) は含まれません。 そのアセンブリへのパスは、マップする XAML を含むプロジェクト ファイル内のプロジェクト参照として確立する必要があります。 バージョニングと厳密な名前の署名を組み込`assembly`むために、値は単純な文字列名<xref:System.Reflection.AssemblyName>ではなく、 で定義された文字列にすることができます。  
  
 トークンとその値を`clr-namespace`区切る文字はコロン (:)一方、トークンとその値`assembly`を区切る文字は等号 (=) です。 これらの 2 つのトークンの間で使用する文字はセミコロンです。 また、宣言のどこにも空白を含まないでください。  
  
### <a name="a-basic-custom-mapping-example"></a>基本的なカスタム マッピングの例  
 次のコードは、カスタム クラスの例を定義しています。  
  
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
  
 このカスタム クラスはライブラリにコンパイルされ、プロジェクト設定 (図示せず) に従って`SDKSampleLibrary`という名前が付けられます。  
  
 このカスタム クラスを参照するには、Visual Studio のソリューション エクスプローラー UI を使用する、現在のプロジェクトの参照としてこのクラスを含める必要があります。  
  
 クラスを含むライブラリとプロジェクト設定での参照ができたので、XAML のルート要素の一部として次のプレフィックス マッピングを追加できます。  
  
 `xmlns:custom="clr-namespace:SDKSample;assembly=SDKSampleLibrary"`  
  
 すべてをまとめると、ルート タグの一般的な既定と x: マッピングと共にカスタム マッピングを含む XAML を次`ExampleClass`に示します。  
  
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
 `assembly`参照先がカスタム クラス`clr-namespace`を参照しているアプリケーション コードと同じアセンブリ内で定義されている場合は省略できます。 または、等号の後に文字列トークンを指定`assembly=`しない、 この場合の同等の構文を指定します。  
  
 同じアセンブリで定義されている場合、カスタム クラスをページのルート要素として使用することはできません。 部分クラスをマップする必要はありません。XAML の要素として参照する場合は、アプリケーションのページの部分クラスではないクラスのみをマップする必要があります。  
  
<a name="Mapping_CLR_Namespaces_to_XML_Namespaces_in_an"></a>
## <a name="mapping-clr-namespaces-to-xml-namespaces-in-an-assembly"></a>CLR 名前空間をアセンブリ内の XML 名前空間にマップする  
 WPF では、複数の CLR 名前空間を 1 つの XAML 名前空間にマップするために、XAML プロセッサによって使用される CLR 属性を定義します。 この属性は<xref:System.Windows.Markup.XmlnsDefinitionAttribute>、アセンブリを生成するソース コードのアセンブリ レベルに配置されます。 WPF アセンブリ ソース コードでは、この属性を使用して、 や<xref:System.Windows><xref:System.Windows.Controls>などのさまざまな一般的`http://schemas.microsoft.com/winfx/2006/xaml/presentation`な名前空間を名前空間にマップします。  
  
 には<xref:System.Windows.Markup.XmlnsDefinitionAttribute>、XML/XAML 名前空間名と CLR 名前空間名の 2 つのパラメーターを使用します。 複数の<xref:System.Windows.Markup.XmlnsDefinitionAttribute>CLR 名前空間を同じ XML 名前空間にマップするために複数存在できます。 いったんマップされた名前空間のメンバーは、部分クラスの分離コード ページに適切な`using`ステートメントを提供することで、必要に応じて完全な修飾なしで参照することもできます。 詳細については、「<xref:System.Windows.Markup.XmlnsDefinitionAttribute>」を参照してください。  
  
## <a name="designer-namespaces-and-other-prefixes-from-xaml-templates"></a>XAML テンプレートからのデザイナー名前空間とその他のプレフィックス  
 WPF XAML の開発環境やデザイン ツールを使用している場合は、XAML マークアップ内に他の定義済みの XAML 名前空間やプレフィックスがあることに気付く場合があります。  
  
 Visual Studio の WPF デザイナーでは、通常はプレフィックス`d:`にマップされるデザイナー名前空間を使用します。 WPF の最近のプロジェクト テンプレートでは、この XAML 名前空間を事前にマップして、Visual Studio 用 WPF デザイナーと他のデザイン環境との間で XAML の交換をサポートする場合があります。 このデザイン XAML 名前空間は、デザイナーで XAML ベースの UI をラウンドしながらデザイン状態を永続化するために使用されます。 また、デザイナーでランタイム データ`d:IsDataSource`ソースを有効にする などの機能にも使用されます。  
  
 マップされたもう 1 つのプレフィックス`mc:`は です。 `mc:`はマークアップの互換性を保つために使用され、必ずしも XAML 固有ではないマークアップ互換性パターンを利用しています。 ある程度、マークアップ互換性機能を使用して、フレームワーク間またはバッキング実装の他の境界を越えて XAML を交換したり、XAML スキーマ コンテキスト間での作業、デザイナーのモードが制限されている場合に互換性を提供したりできます。 マークアップ互換性の概念と、それらが WPF とどのように関連しているかについて詳しくは、[マークアップ互換性 (mc:) を参照してください。言語機能](markup-compatibility-mc-language-features.md):  
  
## <a name="wpf-and-assembly-loading"></a>WPF とアセンブリの読み込み  
 WPF の XAML スキーマ コンテキストは、WPF アプリケーション モデルと統合され、CLR で定義<xref:System.AppDomain>された概念の を使用します。 次のシーケンスでは、実行時またはデザイン時に、WPF の使用やその他の要因に基づいて、XAML スキーマ コンテキストがどのようにしてアセンブリを読<xref:System.AppDomain>み込むか、またはデザイン時に型を検索するかを解釈する方法について説明します。  
  
1. <xref:System.AppDomain>を反復処理して、最後に読み込まれたアセンブリから始めて、名前のすべての側面に一致する既に読み込まれたアセンブリを探します。  
  
2. 名前が修飾されている場合は、<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>修飾名を呼び出します。  
  
3. 修飾名の短縮名 + 公開キー トークンが、マークアップの読み込み元のアセンブリと一致する場合は、そのアセンブリを返します。  
  
4. 短縮名 + 公開鍵トークンを使用<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>して を呼び出します。  
  
5. 名前が修飾されていない場合は、<xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>を呼び出します。  
  
 ルーズ XAML では手順 3 は使用されません。読み込みからアセンブリがありません。  
  
 WPF 用にコンパイルされた XAML (XamlBuildTask を使用して生成) は<xref:System.AppDomain>、既に読み込まれているアセンブリを使用しません (手順 1)。 また、名前は XamlBuildTask 出力から修飾されないようにする必要があるため、手順 5 は適用されません。  
  
 コンパイルされた BAML (プレゼンテーションビルドタスクを介して生成された) はすべての手順を使用しますが、BAML には非修飾のアセンブリ名も含めるべきではありません。  
  
## <a name="see-also"></a>関連項目

- [XML 名前空間について](https://docs.microsoft.com/previous-versions/aa468565(v=msdn.10))
- [XAML の概要 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
