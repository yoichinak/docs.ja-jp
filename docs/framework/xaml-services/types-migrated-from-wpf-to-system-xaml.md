---
title: WPF から System.Xaml に移行した型
ms.date: 03/30/2017
helpviewer_keywords:
- WPF XAML [XAML Services], migration to System.Xaml
- XAML [XAML Services], System.Xaml and WPF
- System.Xaml [XAML Services], types migrated from WPF
ms.assetid: d79dabf5-a2ec-4e8d-a37a-67c4ba8a2b91
ms.openlocfilehash: 943cdb2a21cbf2f95ef7fe2feefe6c0e71f57be4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939684"
---
# <a name="types-migrated-from-wpf-to-systemxaml"></a>WPF から System.Xaml に移行した型
.NET Framework 3.5 および .NET Framework 3.0 では、 [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]と Windows Workflow Foundation の両方に XAML 言語の実装が含まれていました。 WPF XAML 実装に拡張性を与えていたパブリック型の多くは、WindowsBase、PresentationCore、および PresentationFramework アセンブリに存在していました。 同様に、Windows Workflow Foundation XAML の機能拡張を提供したパブリック型は System.componentmodel アセンブリに存在していました。 .NET Framework 4 では、XAML 関連の型の一部が、システムの .Xaml アセンブリに移行されます。 XAML 言語サービスの一般的な .NET Framework 実装により、特定のフレームワークの XAML 実装によって最初に定義された XAML 拡張シナリオの多くが可能になりますが、.NET Framework 4 の XAML 言語サポート全体に含まれるようになりました。 このトピックでは、移行された型を紹介し、移行に伴う問題について説明します。  
  
<a name="assemblies_and_namespaces"></a>   
## <a name="assemblies-and-namespaces"></a>アセンブリと名前空間  
 .NET Framework 3.5 および .NET Framework 3.0 では、WPF が XAML をサポートするために実装する型<xref:System.Windows.Markup>は、一般に名前空間にありました。 これらの型の多くは WindowsBase アセンブリにありました。  
  
 .NET Framework 4 では、新しい<xref:System.Xaml>名前空間と新しい app.xaml アセンブリがあります。 当初は WPF XAML 向けとして実装されていた型の多くが、今では XAML の任意の実装用の機能拡張ポイントまたはサービスとして提供されています。 より一般的なシナリオでも使用できるようにするため、型は元の WPF アセンブリから System.Xaml アセンブリに型転送されました。 これにより、他のフレームワーク (WPF や Windows Workflow Foundation など) のアセンブリを含めなくても、XAML 拡張シナリオが可能になります。  
  
 移行した型のほとんどは、 <xref:System.Windows.Markup> 名前空間に残っています。 これは、既存の実装で CLR 名前空間マッピングが破損するのをファイルごとに回避するための策でもあります。 その結果<xref:System.Windows.Markup> 、.NET Framework 4 の名前空間には、xaml 言語の一般的なサポート型 (app.xaml アセンブリ) と wpf xaml の実装に固有の型 (windowsbase およびその他の wpf アセンブリからのもの) が混在しています。 System.Xaml に移行されたものの、以前は WPF アセンブリにあった型は、バージョン 4 の WPF アセンブリで型転送がサポートされています。  
  
### <a name="workflow-xaml-support-types"></a>ワークフロー XAML サポート型  
 Windows Workflow Foundation XAML サポート型も提供されており、多くの場合、同じ短い名前が WPF と同等のものになっていました。 Windows Workflow Foundation XAML サポート型の一覧を次に示します。  
  
- <xref:System.Workflow.ComponentModel.Serialization.ContentPropertyAttribute>  
  
- <xref:System.Workflow.ComponentModel.Serialization.RuntimeNamePropertyAttribute>  
  
- <xref:System.Workflow.ComponentModel.Serialization.XmlnsPrefixAttribute>  
  
 これらのサポートの種類は、.NET Framework 4 の Windows Workflow Foundation アセンブリにまだ存在しており、特定の Windows Workflow Foundation アプリケーションで引き続き使用できます。ただし、Windows Workflow Foundation を使用しないアプリケーションまたはフレームワークによって参照されないようにする必要があります。  
  
<a name="markupextension"></a>   
## <a name="markupextension"></a>MarkupExtension  
 .NET Framework 3.5 と .NET Framework 3.0 <xref:System.Windows.Markup.MarkupExtension>では、WPF のクラスは windowsbase アセンブリにありました。 Windows Workflow Foundation <xref:System.Workflow.ComponentModel.Serialization.MarkupExtension>の並列クラスは、system.componentmodel アセンブリに存在していました。 .NET Framework 4 では、クラス<xref:System.Windows.Markup.MarkupExtension>がシステムの .xaml アセンブリに移行されます。 .NET Framework 4 では、 <xref:System.Windows.Markup.MarkupExtension>は、特定のフレームワーク上に構築される xaml 機能拡張シナリオだけでなく、.NET Framework の xaml サービスを使用するすべての xaml 機能拡張シナリオを対象としています。 特定のフレームワーク、またはフレームワーク内のユーザー コードも、可能な限り、XAML 機能拡張の <xref:System.Windows.Markup.MarkupExtension> クラス上に構築する必要があります。  
  
<a name="markupextension_supporting_service_classes"></a>   
## <a name="markupextension-supporting-service-classes"></a>MarkupExtension をサポートするサービス クラス  
 .NET Framework 3.5 および .NET Framework 3.0 for WPF では、XAML での型<xref:System.Windows.Markup.MarkupExtension>とプロパティ<xref:System.ComponentModel.TypeConverter>の使用をサポートするために実装および実装で利用できるいくつかのサービスが提供されています。 これらのサービスを次に示します。  
  
- <xref:System.Windows.Markup.IProvideValueTarget>  
  
- <xref:System.Windows.Markup.IUriContext>  
  
- <xref:System.Windows.Markup.IXamlTypeResolver>  
  
> [!NOTE]
> マークアップ拡張機能に関連する .NET Framework 3.5 の別のサービス<xref:System.Windows.Markup.IReceiveMarkupExtension>は、インターフェイスです。 <xref:System.Windows.Markup.IReceiveMarkupExtension>は移行されなかった`[Obsolete]`ため、.NET Framework 4 用にマークされています。 以前に <xref:System.Windows.Markup.IReceiveMarkupExtension> を使用していたシナリオは、代わりに <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute> 属性付きコールバックを使用する必要があります。 <xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute> も `[Obsolete]`とマーク付けされています。  
  
<a name="xaml_language_features"></a>   
## <a name="xaml-language-features"></a>XAML 言語機能  
 WPF 向けのいくつかの XAML 言語機能とコンポーネントは、以前は PresentationFramework アセンブリにありました。 これらの機能やコンポーネントは <xref:System.Windows.Markup.MarkupExtension> のサブクラスとして実装され、XAML マークアップでのマークアップ拡張機能の使用を公開していました。 .NET Framework 4 では、これらは app.xaml アセンブリに存在するため、WPF アセンブリを含まないプロジェクトでこれらの XAML 言語レベルの機能を使用できます。 WPF では、これらの同じ実装を .NET Framework 4 アプリケーションに使用します。 このトピックで示す他のケースと同様に、サポート型は <xref:System.Windows.Markup> 名前空間に引き続き存在するので、以前の参照は破損されません。  
  
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
 <xref:System.Windows.Markup.ValueSerializer> クラスは、特に、シリアル化のために出力に複数のモードまたはノードが必要となる XAML シリアル化のケースで、文字列への型変換をサポートしています。 .NET Framework 3.5 および .NET Framework 3.0 では、 <xref:System.Windows.Markup.ValueSerializer> WPF のは windowsbase アセンブリにありました。 .NET Framework 4 <xref:System.Windows.Markup.ValueSerializer>では、クラスは app.xaml にあり、WPF 上に構築されたものだけでなく、すべての xaml 機能拡張シナリオを対象としています。 <xref:System.Windows.Markup.IValueSerializerContext> (サポート サービス) および <xref:System.Windows.Markup.DateTimeValueSerializer> (固有のサブクラス) も System.Xaml に移行されました。  
  
<a name="xamlrelated_attributes"></a>   
## <a name="xaml-related-attributes"></a>XAML 関連の属性  
 WPF XAML には、XAML の動作について何かを示すために CLR 型に適用される属性がいくつか含まれています。 .NET Framework 3.5 および .NET Framework 3.0 の WPF アセンブリに存在していた属性の一覧を次に示します。 これらの属性は .NET Framework 4 の Page.xaml に移行されます。  
  
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
 この<xref:System.Windows.Markup.IComponentConnector>インターフェイスは、.NET Framework 3.5 および .NET Framework 3.0 の windowsbase にありましたが、.NET Framework 4 の page.xaml に存在します。 <xref:System.Windows.Markup.IComponentConnector> は、主にツーリングのサポートと XAML マークアップ コンパイラーを目的としています。  
  
 この<xref:System.Windows.Markup.INameScope>インターフェイスは、.NET Framework 3.5 および .NET Framework 3.0 の windowsbase にありましたが、.NET Framework 4 の page.xaml に存在します。 <xref:System.Windows.Markup.INameScope> は、XAML 名前空間に対する基本的な操作を定義します。  
  
<a name="xamlrelated_classes_with_shared_names_that_exist_in_wpf_and_systemxaml"></a>   
## <a name="xaml-related-classes-with-shared-names-that-exist-in-wpf-and-systemxaml"></a>WPF と System.Xaml に存在する共通の名前を持つ XAML 関連クラス  
 次のクラスは、.NET Framework 4 の WPF アセンブリと .Xaml アセンブリの両方に存在します。  
  
 `XamlReader`  
  
 `XamlWriter`  
  
 `XamlParseException`  
  
 WPF 実装は、 <xref:System.Windows.Markup> 名前空間にあり、PresentationFramework アセンブリに含まれています。 System.Xaml 実装は、 <xref:System.Xaml> 名前空間にあります。 WPF 型を使用する場合や、WPF 型から派生する場合は、一般に、System.Xaml 実装ではなく <xref:System.Windows.Markup.XamlReader> および <xref:System.Windows.Markup.XamlWriter> の WPF 実装を使用する必要があります。 詳細については、 <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> および <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>の解説セクションを参照してください。  
  
 WPF アセンブリと System.Xaml の両方を参照しており、 `include` 名前空間と <xref:System.Windows.Markup> 名前空間の両方に対して <xref:System.Xaml> ステートメントを使用している場合は、あいまいさを排除して型を解決するために、これらの API への呼び出しを完全修飾する必要があることがあります。  
  
## <a name="see-also"></a>関連項目

- [XAML サービス](index.md)
