---
title: WPF から System.Xaml に移行した型
ms.date: 03/30/2017
helpviewer_keywords:
- WPF XAML [XAML Services], migration to System.Xaml
- XAML [XAML Services], System.Xaml and WPF
- System.Xaml [XAML Services], types migrated from WPF
ms.assetid: d79dabf5-a2ec-4e8d-a37a-67c4ba8a2b91
ms.openlocfilehash: 03f7e17983e56cc2d2136b38b3402ce689f719ee
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2019
ms.locfileid: "66491075"
---
# <a name="types-migrated-from-wpf-to-systemxaml"></a>WPF から System.Xaml に移行した型
.NET Framework 3.5 と[!INCLUDE[net_v30_long](../../../includes/net-v30-long-md.md)]の両方を[!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]Windows Workflow Foundation には、XAML 言語の実装が含まれているとします。 WPF XAML 実装に拡張性を与えていたパブリック型の多くは、WindowsBase、PresentationCore、および PresentationFramework アセンブリに存在していました。 同様に、Windows Workflow Foundation の XAML 機能拡張を提供するパブリック型は System.Workflow.ComponentModel アセンブリに存在します。 .NET Framework 4 での XAML 関連の型の一部が System.Xaml アセンブリに移行します。 XAML 言語サービスの一般的な .NET Framework の実装により、多くの XAML 機能拡張シナリオ固有のフレームワークの XAML 実装によって定義されていたが、全体的な .NET Framework 4 の XAML 言語のサポートの一部であるようになりました。 このトピックでは、移行された型を紹介し、移行に伴う問題について説明します。  
  
<a name="assemblies_and_namespaces"></a>   
## <a name="assemblies-and-namespaces"></a>アセンブリと名前空間  
 [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] および [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)]では、WPF が XAML をサポートするために実装していた型は、一般に <xref:System.Windows.Markup> 名前空間にありました。 これらの型の多くは WindowsBase アセンブリにありました。  
  
 .NET Framework 4 では、新しい<xref:System.Xaml>名前空間と、新しい System.Xaml アセンブリ。 当初は WPF XAML 向けとして実装されていた型の多くが、今では XAML の任意の実装用の機能拡張ポイントまたはサービスとして提供されています。 より一般的なシナリオでも使用できるようにするため、型は元の WPF アセンブリから System.Xaml アセンブリに型転送されました。 これにより XAML 機能拡張シナリオを使用して、他のフレームワーク (WPF や Windows Workflow Foundation) のアセンブリを含める必要はありません。  
  
 移行した型のほとんどは、 <xref:System.Windows.Markup> 名前空間に残っています。 これは、既存の実装で CLR 名前空間マッピングが破損するのをファイルごとに回避するための策でもあります。 結果として、 <xref:System.Windows.Markup> (System.Xaml アセンブリ) からの一般的な XAML 言語のサポート型の混在が .NET Framework 4 で名前空間に含まれていますと WPF XAML 実装に (WindowsBase およびその他の WPF アセンブリ) から、特定では型です。 System.Xaml に移行されたものの、以前は WPF アセンブリにあった型は、バージョン 4 の WPF アセンブリで型転送がサポートされています。  
  
### <a name="workflow-xaml-support-types"></a>ワークフロー XAML サポート型  
 Windows Workflow Foundation では、XAML サポート型も提供されており、多くの場合と同じ WPF に同じ短い名前でした。 Windows Workflow Foundation の XAML サポート型の一覧を次には。  
  
- <xref:System.Workflow.ComponentModel.Serialization.ContentPropertyAttribute>  
  
- <xref:System.Workflow.ComponentModel.Serialization.RuntimeNamePropertyAttribute>  
  
- <xref:System.Workflow.ComponentModel.Serialization.XmlnsPrefixAttribute>  
  
 これらのサポート型は引き続き .NET Framework 4 向けの Windows Workflow Foundation アセンブリ内に存在し、ことができます。 特定の Windows Workflow Foundation アプリケーションの使用ただし、する必要がありますいないでは参照アプリケーションまたはフレームワークが Windows Workflow Foundation を使用しないでください。  
  
<a name="markupextension"></a>   
## <a name="markupextension"></a>MarkupExtension  
 [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] および [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)]では、WPF の <xref:System.Windows.Markup.MarkupExtension> クラスは WindowsBase アセンブリにありました。 Windows Workflow foundation での並列クラス<xref:System.Workflow.ComponentModel.Serialization.MarkupExtension>、System.Workflow.ComponentModel アセンブリにありました。 .NET Framework 4 で、<xref:System.Windows.Markup.MarkupExtension>クラスは System.Xaml アセンブリに移行されます。 .NET Framework 4 で<xref:System.Windows.Markup.MarkupExtension>の特定のフレームワーク上に構築されるだけでなく、.NET Framework XAML サービスを使用する任意の XAML 機能拡張シナリオ向けです。 特定のフレームワーク、またはフレームワーク内のユーザー コードも、可能な限り、XAML 機能拡張の <xref:System.Windows.Markup.MarkupExtension> クラス上に構築する必要があります。  
  
<a name="markupextension_supporting_service_classes"></a>   
## <a name="markupextension-supporting-service-classes"></a>MarkupExtension をサポートするサービス クラス  
 WPF 向けの[!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] と [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)] では、 <xref:System.Windows.Markup.MarkupExtension> implementers と <xref:System.ComponentModel.TypeConverter> の実装が提供されていました。 これらのサービスを次に示します。  
  
- <xref:System.Windows.Markup.IProvideValueTarget>  
  
- <xref:System.Windows.Markup.IUriContext>  
  
- <xref:System.Windows.Markup.IXamlTypeResolver>  
  
> [!NOTE]
>  マークアップ拡張機能に関連するもう 1 つの [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] のサービスとして、 <xref:System.Windows.Markup.IReceiveMarkupExtension> インターフェイスがあります。 <xref:System.Windows.Markup.IReceiveMarkupExtension> 移行されなかったし、マークされて`[Obsolete]`の .NET Framework 4。 以前に <xref:System.Windows.Markup.IReceiveMarkupExtension> を使用していたシナリオは、代わりに <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute> 属性付きコールバックを使用する必要があります。 <xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute> も `[Obsolete]`とマーク付けされています。  
  
<a name="xaml_language_features"></a>   
## <a name="xaml-language-features"></a>XAML 言語機能  
 WPF 向けのいくつかの XAML 言語機能とコンポーネントは、以前は PresentationFramework アセンブリにありました。 これらの機能やコンポーネントは <xref:System.Windows.Markup.MarkupExtension> のサブクラスとして実装され、XAML マークアップでのマークアップ拡張機能の使用を公開していました。 .NET Framework 4 では、WPF アセンブリを組み込んでいないプロジェクトは、XAML 言語レベルのこれらの機能を使用できるようにこれらのコンピューターが System.Xaml アセンブリに存在します。 WPF では、.NET Framework 4 アプリケーションのこれらの同じ実装を使用します。 このトピックで示す他のケースと同様に、サポート型は <xref:System.Windows.Markup> 名前空間に引き続き存在するので、以前の参照は破損されません。  
  
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
 <xref:System.Windows.Markup.ValueSerializer> クラスは、特に、シリアル化のために出力に複数のモードまたはノードが必要となる XAML シリアル化のケースで、文字列への型変換をサポートしています。 [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] および [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)]では、WPF の <xref:System.Windows.Markup.ValueSerializer> は WindowsBase アセンブリにありました。 .NET Framework 4 で、<xref:System.Windows.Markup.ValueSerializer>クラスは System.Xaml と WPF 上に構築するためだけでなく、XAML 機能拡張シナリオを対象としています。 <xref:System.Windows.Markup.IValueSerializerContext> (サポート サービス) および <xref:System.Windows.Markup.DateTimeValueSerializer> (固有のサブクラス) も System.Xaml に移行されました。  
  
<a name="xamlrelated_attributes"></a>   
## <a name="xaml-related-attributes"></a>XAML 関連の属性  
 WPF XAML には、XAML の動作について何かを示すために CLR 型に適用される属性がいくつか含まれています。 [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)] および [!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)]で WPF アセンブリ内に存在していた属性の一覧を次に示します。 これらの属性は、.NET Framework 4 では System.Xaml に移行されます。  
  
- <xref:System.Windows.Markup.AmbientAttribute>  
  
- <xref:System.Windows.Markup.ContentPropertyAttribute>  
  
- <xref:System.Windows.Markup.ContentWrapperAttribute>  
  
- <xref:System.Windows.Markup.DependsOnAttribute>  
  
- <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>  
  
- <xref:System.Windows.Markup.NameScopePropertyAttribute>  
  
- <xref:System.Windows.Markup.RootNamespaceAttribute>  
  
- <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>  
  
- <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>  
  
- <xref:System.Windows.Markup.ValueSerializerAttribute>  
  
- <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>  
  
- <xref:System.Windows.Markup.XmlLangPropertyAttribute>  
  
- <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>  
  
- <xref:System.Windows.Markup.XmlnsDefinitionAttribute>  
  
- <xref:System.Windows.Markup.XmlnsPrefixAttribute>  
  
<a name="miscellaneous_classes"></a>   
## <a name="miscellaneous-classes"></a>その他のクラス  
 <xref:System.Windows.Markup.IComponentConnector>では windowsbase にありましたインターフェイスが存在していた、[!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)]と[!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)]、.NET Framework 4 では System.Xaml に存在しますが、します。 <xref:System.Windows.Markup.IComponentConnector> は、主にツーリングのサポートと XAML マークアップ コンパイラーを目的としています。  
  
 <xref:System.Windows.Markup.INameScope>では windowsbase にありましたインターフェイスが存在していた、[!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)]と[!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)]、.NET Framework 4 では System.Xaml に存在しますが、します。 <xref:System.Windows.Markup.INameScope> は、XAML 名前空間に対する基本的な操作を定義します。  
  
<a name="xamlrelated_classes_with_shared_names_that_exist_in_wpf_and_systemxaml"></a>   
## <a name="xaml-related-classes-with-shared-names-that-exist-in-wpf-and-systemxaml"></a>WPF と System.Xaml に存在する共通の名前を持つ XAML 関連クラス  
 次のクラスは、WPF アセンブリと .NET Framework 4 では System.Xaml アセンブリの両方に存在します。  
  
 `XamlReader`  
  
 `XamlWriter`  
  
 `XamlParseException`  
  
 WPF 実装は、 <xref:System.Windows.Markup> 名前空間にあり、PresentationFramework アセンブリに含まれています。 System.Xaml 実装は、 <xref:System.Xaml> 名前空間にあります。 WPF 型を使用する場合や、WPF 型から派生する場合は、一般に、System.Xaml 実装ではなく <xref:System.Windows.Markup.XamlReader> および <xref:System.Windows.Markup.XamlWriter> の WPF 実装を使用する必要があります。 詳細については、 <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> および <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>の解説セクションを参照してください。  
  
 WPF アセンブリと System.Xaml の両方を参照しており、 `include` 名前空間と <xref:System.Windows.Markup> 名前空間の両方に対して <xref:System.Xaml> ステートメントを使用している場合は、あいまいさを排除して型を解決するために、これらの API への呼び出しを完全修飾する必要があることがあります。  
  
## <a name="see-also"></a>関連項目

- [XAML サービス](index.md)
