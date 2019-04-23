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
ms.openlocfilehash: c238bd3c014c07c541bed0c8f7bc12fc5a910f1b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59301036"
---
# <a name="xaml-namespaces-and-namespace-mapping-for-wpf-xaml"></a>XAML 名前空間および WPF XAML の名前空間の割り当て
さらに、このトピックでは、プレゼンスと WPF XAML ファイルのルート タグによく見られる 2 つの XAML 名前空間マッピングの目的について説明します。 また、独自のコードで、または個別のアセンブリ内に定義されている要素を使用するためのようなマッピングを生成する方法も説明します。  

## <a name="what-is-a-xaml-namespace"></a>XAML Namespace とは何ですか。  
 XAML 名前空間は、実際には、XML 名前空間の概念の拡張です。 XAML 名前空間を指定するための手法では、XML 名前空間の構文、Uri を使用して、同じマークアップ ソースから複数の名前空間を参照するための手段を提供するプレフィックスを使用して、名前空間の識別子としての規則に依存しにします。 XML 名前空間の XAML 定義に追加される主要な概念は XAML 名前空間が両方の一意性のスコープ マークアップの使用を意味し、マークアップのエンティティが可能性のある特定の CLR 名前空間に支えし、参照されている方法にも影響を与えますアセンブリ。 後者の考慮事項は、XAML スキーマ コンテキストの概念の影響も受けます。 WPF の XAML 名前空間を持つ動作方法のために、考えることができます一般に、既定の XAML 名前空間、言語の XAML 名前空間、およびさらに XAML 名前空間によって、XAML マークアップは、特定のバッキング CLR を直接マップされるよう面での XAML 名前空間が、名前空間と参照アセンブリ。  
  
<a name="The_WPF_and_XAML_Namespace_Declarations"></a>   
## <a name="the-wpf-and-xaml-namespace-declarations"></a>WPF と XAML Namespace 宣言  
 多くの XAML ファイルのルート タグにある名前空間宣言内では、2 つの XML 名前空間宣言は通常、参照してください。 最初の宣言のマップ全体の WPF クライアント/フレームワーク、既定値としての XAML 名前空間。  
  
 `xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`  
  
 2 番目の宣言にマップされます (通常は) にマップすること、別の XAML 名前空間、`x:`プレフィックス。  
  
 `xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 これらの宣言の間のリレーションシップは、`x:`プレフィックスのマッピングは、組み込み XAML 言語の定義の一部であるをサポートしていると[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]言語として XAML を使用しのボキャブラリの定義を 1 つの実装は、そのXAML のオブジェクト。 WPF の語彙の使用は XAML の組み込みの使用よりもはるかに一般的になる、ために、WPF ボキャブラリは、既定値としてマップされます。  
  
 `x:`プレフィックス規則、プロジェクト テンプレートの後に、XAML 言語の組み込みサポートをマッピングのサンプル コード、および言語のドキュメントがこの機能[!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)]します。 XAML 名前空間は、基本的な WPF アプリケーションにも必要なは一般的に使用される多くの機能を定義します。 たとえば、部分クラスを XAML ファイルに分離コードを結合するには名前を付けてとしてそのクラス、`x:Class`関連する XAML ファイルのルート要素の属性。 または、任意の要素へのアクセス キーを持つリソースが必要とする XAML ページで定義されている、`x:Key`属性が「問題の要素に設定します。 これらやその他のさまざまな XAML の詳細については、次を参照してください。 [XAML の概要 (WPF)](xaml-overview-wpf.md)または[XAML 構文の詳細](xaml-syntax-in-detail.md)します。  
  
<a name="Mapping_To_Custom_Classes_and_Assemblies"></a>   
## <a name="mapping-to-custom-classes-and-assemblies"></a>カスタム クラスとアセンブリへのマッピング  
 XML 名前空間をマップするには、一連の内のトークンを使用してアセンブリを`xmlns`プレフィックスの宣言では、標準的な WPF および XAML 組み込み XAML 名前空間をプレフィックスにマップする方法に似ています。  
  
 構文には、次の考えられる名前付きのトークンと次の値の場合:  
  
 `clr-namespace:` CLR 名前空間は、要素として公開するパブリック型を含むアセンブリ内で宣言します。  
  
 `assembly=` 参照先の一部またはすべてを含むアセンブリ[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]名前空間。 この値は、パスではなく、アセンブリの名前だけでは、通常、(.dll または .exe) などの拡張機能は含まれません。 マップしようとして XAML を含むプロジェクト ファイル内のプロジェクト参照としては、そのアセンブリへのパスを確立する必要があります。 バージョン管理と厳密な名前の署名を反映するために、`assembly`で定義されている値が文字列を指定できる<xref:System.Reflection.AssemblyName>、単純な文字列名ではなく。  
  
 区切る文字に注意してください、`clr-namespace`値からトークンがありますが、コロン (:) 文字の分離、`assembly`トークンその値からは、等号 (=)。 これら 2 つのトークンの間で使用する文字は、セミコロンです。 また、任意の空白任意の場所に含めない宣言。  
  
### <a name="a-basic-custom-mapping-example"></a>基本的なカスタム マッピング例  
 次のコードでは、サンプルのカスタム クラスを定義します。  
  
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
  
 このカスタム クラスは、プロジェクトの設定 (非表示) と呼ばれるライブラリにコンパイルし、`SDKSampleLibrary`します。  
  
 このカスタム クラスを参照するためにも含める必要があることは、現在のプロジェクトへの参照として Visual Studio のソリューション エクスプ ローラーの UI を使用します。  
  
 クラス、およびへの参照をプロジェクト設定を含むライブラリがある場合は、できた XAML ルート要素の一部として、次のプレフィックス マッピングを追加できます。  
  
 `xmlns:custom="clr-namespace:SDKSample;assembly=SDKSampleLibrary"`  
  
 次にルート タグに代表的な既定とカスタム マッピングと x: マッピングが含まれていますし、プレフィックス付きの参照を使用して、インスタンス化する XAML をまとめて配置する`ExampleClass`その UI で。  
  
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
 `assembly` 場合は省略可能、`clr-namespace`参照されているカスタム クラスを参照しているアプリケーション コードと同じアセンブリ内で定義されています。 この場合の同等の構文は、指定することです。 または、 `assembly=`、なし文字列トークンを、等号の後にします。  
  
 カスタム クラスは、同じアセンブリで定義されている場合は、ページのルート要素として使用できません。 部分クラスが割り当てる必要はありません。アプリケーションが必要となる XAML で要素として参照する場合にマップするページの部分クラスではないクラスのみです。  
  
<a name="Mapping_CLR_Namespaces_to_XML_Namespaces_in_an"></a>   
## <a name="mapping-clr-namespaces-to-xml-namespaces-in-an-assembly"></a>アセンブリ内の XML 名前空間への CLR 名前空間のマッピング  
 WPF では、複数の CLR 名前空間を単一の XAML 名前空間にマップするために、XAML プロセッサによって使用される CLR 属性を定義します。 この属性は、<xref:System.Windows.Markup.XmlnsDefinitionAttribute>アセンブリを生成するソース コードにアセンブリ レベルで配置されます。 WPF アセンブリのソース コードでは、この属性を使用するなど、さまざまな一般的な名前空間をマップ<xref:System.Windows>と<xref:System.Windows.Controls>を[!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)]名前空間。  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute>は 2 つのパラメーターを受け取ります。 XML と XAML 名前空間の名前と CLR 名前空間の名前。 1 つ以上<xref:System.Windows.Markup.XmlnsDefinitionAttribute>同じ XML 名前空間に複数の CLR 名前空間にマップする存在できます。 マップされると、それらの名前空間のメンバーもせずに参照できる完全に修飾、適切な提供することで必要な場合は`using`部分クラスの分離コード ページ内のステートメント。 詳細については、「<xref:System.Windows.Markup.XmlnsDefinitionAttribute>」を参照してください。  
  
## <a name="designer-namespaces-and-other-prefixes-from-xaml-templates"></a>デザイナーの名前空間と XAML テンプレートから他のプレフィックス  
 WPF XAML の開発環境やデザイン ツールで操作している場合、他の定義済みの XAML 名前空間があることを確認する]、[XAML マークアップ内のプレフィックスします。  
  
 [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] 通常、プレフィックスにマップされるデザイナー名前空間を使用して`d:`します。 WPF の最近のプロジェクト テンプレートは、XAML との間の交換をサポートするためにこの XAML 名前空間をマップ事前可能性があります[!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)]や他のデザイン環境。 このデザインの XAML 名前空間は、デザイナーで XAML ベースの UI をラウンドト リップのときにデザイン状態を永続化に使用されます。 などの機能を使用するがも、`d:IsDataSource`デザイナーでの実行時データ ソースを有効にします。  
  
 マップされている別のプレフィックス「可能性がありますが`mc:`します。 `mc:` マークアップの互換性、必ずしも XAML に固有でないマークアップ互換性パターンを活用することです。 ある程度はマークアップの互換性機能は、フレームワーク間または他の境界のバッキング実装の間で XAML を交換するために使用できます XAML スキーマ コンテキスト間での作業、デザイナーでは、制限付きのモードの互換性を提供および具合です。 マークアップの互換性の概念とどのように関連する WPF の詳細については、次を参照してください[マークアップの互換性 (mc:)。言語機能](markup-compatibility-mc-language-features.md)します。  
  
## <a name="wpf-and-assembly-loading"></a>WPF およびアセンブリの読み込み  
 WPF の XAML スキーマ コンテキストと統合の CLR で定義された概念を使用して、WPF アプリケーション モデル、<xref:System.AppDomain>します。 次の順序は、XAML スキーマ コンテキストでアセンブリを読み込むかの WPF の使用状況に基づいて実行時またはデザイン時に、型を検索する方法を解釈する方法について説明します<xref:System.AppDomain>およびその他の要因です。  
  
1. 反復処理、<xref:System.AppDomain>名前のすべての側面に一致する読み込み済みアセンブリを探して、読み込まれたアセンブリを最近開始します。  
  
2. 名前が修飾されている場合に呼び出す<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>修飾名にします。  
  
3. 短い名前と修飾名の公開キー トークンは、マークアップから読み込まれたアセンブリに一致すると、そのアセンブリを返します。  
  
4. 短い名前と公開キー トークンを使用して呼び出す<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>します。  
  
5. 名前が修飾されていない場合は、呼び出す<xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=nameWithType>します。  
  
 Loose XAML は、手順 3; を使用しません読み込まれたアセンブリがありません。  
  
 WPF (XamlBuildTask 経由で生成された) にコンパイルされた XAML がから既に読み込まれたアセンブリを使用しない<xref:System.AppDomain>(ステップ 1)。 また、名前べきでは、XamlBuildTask 出力から不適切なため、手順 5 が適用されません。  
  
 BAML にはもする必要がありますが含まれていない非修飾アセンブリ名が、コンパイル済みの BAML (PresentationBuildTask を使用して生成) は、すべての手順を使用します。  
  
## <a name="see-also"></a>関連項目

- [XML 名前空間を理解します。](https://go.microsoft.com/fwlink/?LinkId=98069)
- [XAML の概要 (WPF)](xaml-overview-wpf.md)
