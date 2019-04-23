---
title: WPF から System.Xaml に移行した型
ms.date: 03/30/2017
helpviewer_keywords:
- WPF XAML [XAML Services], migration to System.Xaml
- XAML [XAML Services], System.Xaml and WPF
- System.Xaml [XAML Services], types migrated from WPF
ms.assetid: d79dabf5-a2ec-4e8d-a37a-67c4ba8a2b91
ms.openlocfilehash: dcfad1c2b2f95783e2b348a3a1111501f958143f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59116481"
---
# <a name="types-migrated-from-wpf-to-systemxaml"></a>WPF から System.Xaml に移行した型
[!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)]と[!INCLUDE[net_v30_long](../../../includes/net-v30-long-md.md)]の両方を[!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]Windows Workflow Foundation には、XAML 言語の実装が含まれているとします。 WPF XAML 実装に拡張性を与えていたパブリック型の多くは、WindowsBase、PresentationCore、および PresentationFramework アセンブリに存在していました。 同様に、Windows Workflow Foundation の XAML 機能拡張を提供するパブリック型は System.Workflow.ComponentModel アセンブリに存在します。 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]では、XAML 関連の型の一部が System.Xaml アセンブリに移行されました。 XAML 言語サービスの一般的な .NET Framework 実装では、もともと特定のフレームワークの XAML 実装によって定義されていた XAML 機能拡張のシナリオの多くを、今では全体的な [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] XAML 言語サポートの一部として使用できるようになりました。 このトピックでは、移行された型を紹介し、移行に伴う問題について説明します。  
  
<a name="assemblies_and_namespaces"></a>   
## <a name="assemblies-and-namespaces"></a>アセンブリと名前空間  
 [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] および [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)]では、WPF が XAML をサポートするために実装していた型は、一般に <xref:System.Windows.Markup> 名前空間にありました。 これらの型の多くは WindowsBase アセンブリにありました。  
  
 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]には、新しい <xref:System.Xaml> 名前空間と、新しい System.Xaml アセンブリがあります。 当初は WPF XAML 向けとして実装されていた型の多くが、今では XAML の任意の実装用の機能拡張ポイントまたはサービスとして提供されています。 より一般的なシナリオでも使用できるようにするため、型は元の WPF アセンブリから System.Xaml アセンブリに型転送されました。 これにより XAML 機能拡張シナリオを使用して、他のフレームワーク (WPF や Windows Workflow Foundation) のアセンブリを含める必要はありません。  
  
 移行した型のほとんどは、 <xref:System.Windows.Markup> 名前空間に残っています。 これは、既存の実装で CLR 名前空間マッピングが破損するのをファイルごとに回避するための策でもあります。 その結果、 <xref:System.Windows.Markup> の [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 名前空間には、XAML 言語をサポートする一般的な型 (System.Xaml アセンブリにあったもの) と、XAML の WPF 実装に固有の型 (WindowsBase およびその他の WPF アセンブリにあったもの) が混在しています。 System.Xaml に移行されたものの、以前は WPF アセンブリにあった型は、バージョン 4 の WPF アセンブリで型転送がサポートされています。  
  
### <a name="workflow-xaml-support-types"></a>ワークフロー XAML サポート型  
 Windows Workflow Foundation では、XAML サポート型も提供されており、多くの場合と同じ WPF に同じ短い名前でした。 Windows Workflow Foundation の XAML サポート型の一覧を次には。  
  
-   <xref:System.Workflow.ComponentModel.Serialization.ContentPropertyAttribute>  
  
-   <xref:System.Workflow.ComponentModel.Serialization.RuntimeNamePropertyAttribute>  
  
-   <xref:System.Workflow.ComponentModel.Serialization.XmlnsPrefixAttribute>  
  
 これらのサポートの種類は、Windows Workflow Foundation のアセンブリにまだ存在[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]と特定の Windows Workflow Foundation アプリケーションを引き続き使用できますただし、この属性はアプリケーションまたはフレームワークを使用しないのではない参照する必要があります。Windows Workflow Foundation。  
  
<a name="markupextension"></a>   
## <a name="markupextension"></a>MarkupExtension  
 [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] および [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)]では、WPF の <xref:System.Windows.Markup.MarkupExtension> クラスは WindowsBase アセンブリにありました。 Windows Workflow foundation での並列クラス<xref:System.Workflow.ComponentModel.Serialization.MarkupExtension>、System.Workflow.ComponentModel アセンブリにありました。 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]では、 <xref:System.Windows.Markup.MarkupExtension> クラスは System.Xaml アセンブリに移行されています。 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]では、 <xref:System.Windows.Markup.MarkupExtension> は、特定のフレームワーク上に構築される XAML 機能拡張シナリオだけではなく、.NET Framework XAML サービスを使用する任意の XAML 機能拡張シナリオを対象としています。 特定のフレームワーク、またはフレームワーク内のユーザー コードも、可能な限り、XAML 機能拡張の <xref:System.Windows.Markup.MarkupExtension> クラス上に構築する必要があります。  
  
<a name="markupextension_supporting_service_classes"></a>   
## <a name="markupextension-supporting-service-classes"></a>MarkupExtension をサポートするサービス クラス  
 WPF 向けの[!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] と [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)] では、 <xref:System.Windows.Markup.MarkupExtension> implementers と <xref:System.ComponentModel.TypeConverter> の実装が提供されていました。 これらのサービスを次に示します。  
  
-   <xref:System.Windows.Markup.IProvideValueTarget>  
  
-   <xref:System.Windows.Markup.IUriContext>  
  
-   <xref:System.Windows.Markup.IXamlTypeResolver>  
  
> [!NOTE]
>  マークアップ拡張機能に関連するもう 1 つの [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] のサービスとして、 <xref:System.Windows.Markup.IReceiveMarkupExtension> インターフェイスがあります。 <xref:System.Windows.Markup.IReceiveMarkupExtension> は移行されず、 `[Obsolete]` では [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]とマーク付けされています。 以前に <xref:System.Windows.Markup.IReceiveMarkupExtension> を使用していたシナリオは、代わりに <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute> 属性付きコールバックを使用する必要があります。 <xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute> も `[Obsolete]`とマーク付けされています。  
  
<a name="xaml_language_features"></a>   
## <a name="xaml-language-features"></a>XAML 言語機能  
 WPF 向けのいくつかの XAML 言語機能とコンポーネントは、以前は PresentationFramework アセンブリにありました。 これらの機能やコンポーネントは <xref:System.Windows.Markup.MarkupExtension> のサブクラスとして実装され、XAML マークアップでのマークアップ拡張機能の使用を公開していました。 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]では、これらは System.Xaml アセンブリにあるので、WPF アセンブリを組み込んでいないプロジェクトでも、これらの XAML 言語レベルの機能を使用できます。 WPF では、これと同じ実装を [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] アプリケーションに対して使用しています。 このトピックで示す他のケースと同様に、サポート型は <xref:System.Windows.Markup> 名前空間に引き続き存在するので、以前の参照は破損されません。  
  
 System.Xaml で定義されている XAML 機能のサポート クラスを次の表に示します。  
  
|XAML 言語機能|使用法|  
|---------------------------|-----------|  
|<xref:System.Windows.Markup.ArrayExtension>|`<x:Array ...>`|  
|<xref:System.Windows.Markup.NullExtension>|`{x:Null}`|  
|<xref:System.Windows.Markup.StaticExtension>|`{x:Static ...}`|  
|<xref:System.Windows.Markup.TypeExtension>|`{x:Type ...}`|  
  
 System.Xaml には特定のサポート クラスはありませんが、XAML 言語の言語機能を処理するための一般的なロジックは System.Xaml にあり、それを実装した XAML リーダーと XAML ライターにも含まれています。 たとえば、 `x:TypeArguments` は System.Xaml 実装の XAML リーダーと XAML ライターによって処理される属性です。これは XAML ノード ストリームで示すことができ、既定の (CLR ベースの) XAML スキーマ コンテキストに処理があり、XAML 型システム表現があります。 その結果、XAML 言語レベルのすべての機能に関するリファレンス ドキュメントは、WPF ドキュメント セットに属する「 [詳細設定 (Windows Presentation Foundation)](index.md) 」のサブトピックとしてではなく (3.5 のドキュメント セットは今でもここにあります)、 [XAML Services](../wpf/advanced/index.md) と .NET Framework ドキュメント セットの一般分野のサブトピックとして掲載されています。  
  
<a name="valueserializer_and_supporting_classes"></a>   
## <a name="valueserializer-and-supporting-classes"></a>ValueSerializer とサポートするクラス  
 <xref:System.Windows.Markup.ValueSerializer> クラスは、特に、シリアル化のために出力に複数のモードまたはノードが必要となる XAML シリアル化のケースで、文字列への型変換をサポートしています。 [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] および [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)]では、WPF の <xref:System.Windows.Markup.ValueSerializer> は WindowsBase アセンブリにありました。 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]では、 <xref:System.Windows.Markup.ValueSerializer> クラスは System.Xaml にあり、WPF 上に構築される XAML 機能拡張シナリオだけではなく、すべての XAML 機能拡張シナリオを対象としています。 <xref:System.Windows.Markup.IValueSerializerContext> (サポート サービス) および <xref:System.Windows.Markup.DateTimeValueSerializer> (固有のサブクラス) も System.Xaml に移行されました。  
  
<a name="xamlrelated_attributes"></a>   
## <a name="xaml-related-attributes"></a>XAML 関連の属性  
 WPF XAML には、XAML の動作について何かを示すために CLR 型に適用される属性がいくつか含まれています。 [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] および [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)]で WPF アセンブリ内に存在していた属性の一覧を次に示します。 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]では、これらの属性は System.Xaml に移行されました。  
  
-   <xref:System.Windows.Markup.AmbientAttribute>  
  
-   <xref:System.Windows.Markup.ContentPropertyAttribute>  
  
-   <xref:System.Windows.Markup.ContentWrapperAttribute>  
  
-   <xref:System.Windows.Markup.DependsOnAttribute>  
  
-   <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>  
  
-   <xref:System.Windows.Markup.NameScopePropertyAttribute>  
  
-   <xref:System.Windows.Markup.RootNamespaceAttribute>  
  
-   <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>  
  
-   <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>  
  
-   <xref:System.Windows.Markup.ValueSerializerAttribute>  
  
-   <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>  
  
-   <xref:System.Windows.Markup.XmlLangPropertyAttribute>  
  
-   <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>  
  
-   <xref:System.Windows.Markup.XmlnsDefinitionAttribute>  
  
-   <xref:System.Windows.Markup.XmlnsPrefixAttribute>  
  
<a name="miscellaneous_classes"></a>   
## <a name="miscellaneous-classes"></a>その他のクラス  
 <xref:System.Windows.Markup.IComponentConnector> インターフェイスは、 [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] および [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)]では WindowsBase にありましたが、 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]では System.Xaml にあります。 <xref:System.Windows.Markup.IComponentConnector> は、主にツーリングのサポートと XAML マークアップ コンパイラーを目的としています。  
  
 <xref:System.Windows.Markup.INameScope> インターフェイスは、 [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] および [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)]では WindowsBase にありましたが、 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]では System.Xaml にあります。 <xref:System.Windows.Markup.INameScope> は、XAML 名前空間に対する基本的な操作を定義します。  
  
<a name="xamlrelated_classes_with_shared_names_that_exist_in_wpf_and_systemxaml"></a>   
## <a name="xaml-related-classes-with-shared-names-that-exist-in-wpf-and-systemxaml"></a>WPF と System.Xaml に存在する共通の名前を持つ XAML 関連クラス  
 次に示すクラスは、 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]で、WPF アセンブリと System.Xaml アセンブリの両方に存在します。  
  
 `XamlReader`  
  
 `XamlWriter`  
  
 `XamlParseException`  
  
 WPF 実装は、 <xref:System.Windows.Markup> 名前空間にあり、PresentationFramework アセンブリに含まれています。 System.Xaml 実装は、 <xref:System.Xaml> 名前空間にあります。 WPF 型を使用する場合や、WPF 型から派生する場合は、一般に、System.Xaml 実装ではなく <xref:System.Windows.Markup.XamlReader> および <xref:System.Windows.Markup.XamlWriter> の WPF 実装を使用する必要があります。 詳細については、 <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> および <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>の解説セクションを参照してください。  
  
 WPF アセンブリと System.Xaml の両方を参照しており、 `include` 名前空間と <xref:System.Windows.Markup> 名前空間の両方に対して <xref:System.Xaml> ステートメントを使用している場合は、あいまいさを排除して型を解決するために、これらの API への呼び出しを完全修飾する必要があることがあります。  
  
## <a name="see-also"></a>関連項目

- [XAML サービス](index.md)
