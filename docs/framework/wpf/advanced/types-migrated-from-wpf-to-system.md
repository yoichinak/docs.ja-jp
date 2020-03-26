---
title: WPF から System.Xaml に移行した型
ms.date: 03/30/2017
helpviewer_keywords:
- WPF XAML [XAML Services], migration to System.Xaml
- XAML [XAML Services], System.Xaml and WPF
- System.Xaml [XAML Services], types migrated from WPF
ms.assetid: d79dabf5-a2ec-4e8d-a37a-67c4ba8a2b91
ms.openlocfilehash: 5aa2d8a39be47d9affb97c3b60e53c4722c63cce
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249814"
---
# <a name="types-migrated-from-wpf-to-systemxaml"></a>WPF から System.Xaml に移行された型

NET Framework 3.5 および .NET Framework 3.0 では、WINDOWS プレゼンテーション ファンデーション (WPF) と Windows ワークフロー ファンデーションの両方に XAML 言語の実装が含まれていました。 WPF XAML 実装に拡張性を与えていたパブリック型の多くは、WindowsBase、PresentationCore、および PresentationFramework アセンブリに存在していました。 同様に、Windows ワークフローファンデーション XAML の機能拡張を提供するパブリック型が、System.Workflow.ComponentModel アセンブリに存在しました。 NET Framework 4 では、いくつかの XAML 関連の型が System.Xaml アセンブリに移行されました。 XAML 言語サービスの一般的な .NET Framework 実装では、最初は特定のフレームワークの XAML 実装によって定義されたが、現在は .NET Framework 4 XAML 言語サポート全体の一部となる多くの XAML 拡張シナリオを実現できます。 この記事では、移行された種類の一覧と、移行に関連する問題について説明します。

## <a name="assemblies-and-namespaces"></a>アセンブリと名前空間

.NET Framework 3.5 および .NET Framework 3.0 では、WPF が XAML<xref:System.Windows.Markup>をサポートするために実装した型は、通常、名前空間に含まれています。 これらの型の多くは WindowsBase アセンブリにありました。

NET Framework 4 では、新<xref:System.Xaml>しい名前空間と新しい System.Xaml アセンブリがあります。 当初は WPF XAML 向けとして実装されていた型の多くが、今では XAML の任意の実装用の機能拡張ポイントまたはサービスとして提供されています。 より一般的なシナリオでも使用できるようにするため、型は元の WPF アセンブリから System.Xaml アセンブリに型転送されました。 これにより、他のフレームワーク (WPF や Windows ワークフロー ファンデーションなど) のアセンブリを含めなくても XAML 拡張シナリオが可能になります。

移行した型のほとんどは、 <xref:System.Windows.Markup> 名前空間に残っています。 これは、既存の実装で CLR 名前空間マッピングが破損するのをファイルごとに回避するための策でもあります。 その結果、.NET <xref:System.Windows.Markup> Framework 4 の名前空間には、一般的な XAML 言語サポートの型 (System.Xaml アセンブリから) と (WindowsBase とその他の WPF アセンブリから) WPF XAML 実装に固有の型が混在しています。 System.Xaml に移行されたものの、以前は WPF アセンブリにあった型は、バージョン 4 の WPF アセンブリで型転送がサポートされています。

### <a name="workflow-xaml-support-types"></a>ワークフロー XAML サポート型

Windows ワークフロー ファンデーションは XAML サポートの種類も提供し、多くの場合、WPF と同等の短い名前が同じでした。 次に示す一覧は、Windows ワークフローファンデーション XAML サポートの種類です。

- <xref:System.Workflow.ComponentModel.Serialization.ContentPropertyAttribute>

- <xref:System.Workflow.ComponentModel.Serialization.RuntimeNamePropertyAttribute>

- <xref:System.Workflow.ComponentModel.Serialization.XmlnsPrefixAttribute>

これらのサポートの種類は、.NET Framework 4 の Windows ワークフロー ファウンデーション アセンブリにまだ存在し、特定の Windows ワークフロー ファンデーション アプリケーションに対して引き続き使用できます。ただし、Windows ワークフロー ファンデーションを使用しないアプリケーションやフレームワークでは参照しないでください。

## <a name="markupextension"></a>MarkupExtension

NET フレームワーク 3.5 および .NET Framework 3.0 では、WPF の<xref:System.Windows.Markup.MarkupExtension>クラスは WindowsBase アセンブリ内に含まれています。 Windows ワークフロー ファウンデーション<xref:System.Workflow.ComponentModel.Serialization.MarkupExtension>のパラレル クラスが、System.Workflow.ComponentModel アセンブリに存在しました。 NET Framework 4 では、<xref:System.Windows.Markup.MarkupExtension>クラスは System.Xaml アセンブリに移行されます。 .NET Framework 4<xref:System.Windows.Markup.MarkupExtension>では、特定のフレームワークを構築する XAML サービスだけでなく、.NET XAML サービスを使用する XAML 拡張シナリオを対象としています。 特定のフレームワーク、またはフレームワーク内のユーザー コードも、可能な限り、XAML 機能拡張の <xref:System.Windows.Markup.MarkupExtension> クラス上に構築する必要があります。

## <a name="markupextension-supporting-service-classes"></a>MarkupExtension をサポートするサービス クラス

.NET Framework 3.5 および .NET Framework 3.0 WPF<xref:System.Windows.Markup.MarkupExtension>では、XAML<xref:System.ComponentModel.TypeConverter>で型/プロパティの使用をサポートする実装および実装で利用できるいくつかのサービスが提供されました。 これらのサービスを次に示します。

- <xref:System.Windows.Markup.IProvideValueTarget>

- <xref:System.Windows.Markup.IUriContext>

- <xref:System.Windows.Markup.IXamlTypeResolver>

> [!NOTE]
> マークアップ拡張機能に関連する .NET Framework 3.5 の別<xref:System.Windows.Markup.IReceiveMarkupExtension>のサービスは、インターフェイスです。 <xref:System.Windows.Markup.IReceiveMarkupExtension>は移行されず、.NET `[Obsolete]` Framework 4 のマークが付けられます。 以前に <xref:System.Windows.Markup.IReceiveMarkupExtension> を使用していたシナリオは、代わりに <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute> 属性付きコールバックを使用する必要があります。 <xref:System.Windows.Markup.AcceptedMarkupExtensionExpressionTypeAttribute> も `[Obsolete]`とマーク付けされています。

## <a name="xaml-language-features"></a>XAML 言語機能

WPF 向けのいくつかの XAML 言語機能とコンポーネントは、以前は PresentationFramework アセンブリにありました。 これらの機能やコンポーネントは <xref:System.Windows.Markup.MarkupExtension> のサブクラスとして実装され、XAML マークアップでのマークアップ拡張機能の使用を公開していました。 .NET Framework 4 では、これらの WPF アセンブリを含まないプロジェクトがこれらの XAML 言語レベルの機能を使用できるように、System.Xaml アセンブリに存在します。 WPF では、.NET Framework 4 アプリケーションに対して同じ実装を使用します。 このトピックで示す他のケースと同様に、サポート型は <xref:System.Windows.Markup> 名前空間に引き続き存在するので、以前の参照は破損されません。

System.Xaml で定義されている XAML 機能のサポート クラスを次の表に示します。

|XAML 言語機能|使用法|
|---------------------------|-----------|
|<xref:System.Windows.Markup.ArrayExtension>|`<x:Array ...>`|
|<xref:System.Windows.Markup.NullExtension>|`{x:Null}`|
|<xref:System.Windows.Markup.StaticExtension>|`{x:Static ...}`|
|<xref:System.Windows.Markup.TypeExtension>|`{x:Type ...}`|

System.Xaml には特定のサポート クラスはありませんが、XAML 言語の言語機能を処理するための一般的なロジックは System.Xaml にあり、それを実装した XAML リーダーと XAML ライターにも含まれています。 たとえば、 `x:TypeArguments` は System.Xaml 実装の XAML リーダーと XAML ライターによって処理される属性です。これは XAML ノード ストリームで示すことができ、既定の (CLR ベースの) XAML スキーマ コンテキストに処理があり、XAML 型システム表現があります。 その結果、XAML 言語レベルのすべての機能のリファレンス ドキュメントは[、Windows プレゼンテーションファンデーション (WPF) のデスクトップ ガイド](../../../desktop-wpf/overview/index.md)で[XAML サービス](../../../desktop-wpf/xaml-services/index.md)のサブトピックです。

## <a name="valueserializer-and-supporting-classes"></a>ValueSerializer とサポートするクラス

<xref:System.Windows.Markup.ValueSerializer> クラスは、特に、シリアル化のために出力に複数のモードまたはノードが必要となる XAML シリアル化のケースで、文字列への型変換をサポートしています。 NET フレームワーク 3.5 および .NET Framework 3.0 では、WPF<xref:System.Windows.Markup.ValueSerializer>は WindowsBase アセンブリ内に含まれています。 .NET Framework 4 では<xref:System.Windows.Markup.ValueSerializer>、クラスは System.Xaml にあり、WPF 上で構築する XAML 拡張シナリオだけでなく、すべての XAML 拡張シナリオを対象としています。 <xref:System.Windows.Markup.IValueSerializerContext> (サポート サービス) および <xref:System.Windows.Markup.DateTimeValueSerializer> (固有のサブクラス) も System.Xaml に移行されました。

## <a name="xaml-related-attributes"></a>XAML 関連の属性

WPF XAML には、XAML の動作について何かを示すために CLR 型に適用される属性がいくつか含まれています。 次の一覧は、.NET Framework 3.5 および .NET Framework 3.0 の WPF アセンブリに存在する属性の一覧です。 これらの属性は、.NET Framework 4 の System.Xaml に移行されます。

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

## <a name="miscellaneous-classes"></a>その他のクラス

インターフェイス<xref:System.Windows.Markup.IComponentConnector>は、.NET Framework 3.5 および .NET Framework 3.0 の WindowsBase に存在しましたが、.NET フレームワーク 4 の System.Xaml に存在します。 <xref:System.Windows.Markup.IComponentConnector> は、主にツーリングのサポートと XAML マークアップ コンパイラーを目的としています。

インターフェイス<xref:System.Windows.Markup.INameScope>は、.NET Framework 3.5 および .NET Framework 3.0 の WindowsBase に存在しましたが、.NET フレームワーク 4 の System.Xaml に存在します。 <xref:System.Windows.Markup.INameScope> は、XAML 名前空間に対する基本的な操作を定義します。

## <a name="xaml-related-classes-with-shared-names-that-exist-in-wpf-and-systemxaml"></a>WPF と System.Xaml に存在する共通の名前を持つ XAML 関連クラス

次のクラスは、WPF アセンブリと .NET Framework 4 の System.Xaml アセンブリの両方に存在します。

`XamlReader`

`XamlWriter`

`XamlParseException`

WPF 実装は、 <xref:System.Windows.Markup> 名前空間にあり、PresentationFramework アセンブリに含まれています。 System.Xaml 実装は、 <xref:System.Xaml> 名前空間にあります。 WPF 型を使用する場合や、WPF 型から派生する場合は、一般に、System.Xaml 実装ではなく <xref:System.Windows.Markup.XamlReader> および <xref:System.Windows.Markup.XamlWriter> の WPF 実装を使用する必要があります。 詳細については、 <xref:System.Windows.Markup.XamlReader?displayProperty=nameWithType> および <xref:System.Windows.Markup.XamlWriter?displayProperty=nameWithType>の解説セクションを参照してください。

WPF アセンブリと System.Xaml の両方を参照しており、 `include` 名前空間と <xref:System.Windows.Markup> 名前空間の両方に対して <xref:System.Xaml> ステートメントを使用している場合は、あいまいさを排除して型を解決するために、これらの API への呼び出しを完全修飾する必要があることがあります。
