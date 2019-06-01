---
title: XAML の型コンバーターおよびマークアップ拡張機能
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converter services
- XAML [XAML Services], value converters
- XAML [XAML Services], markup extension services
- value converters for XAML [XAML Services]
- XAML [XAML Services], service context
ms.assetid: db07a952-05ce-4aa4-b6f9-aac7397d0326
ms.openlocfilehash: d1cc6043afb7f795bb1208d2cf333aeca321462f
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2019
ms.locfileid: "66457373"
---
# <a name="type-converters-and-markup-extensions-for-xaml"></a>XAML の型コンバーターおよびマークアップ拡張機能
型コンバーターとマークアップ拡張機能は、XAML 型システムと XAML ライターが、オブジェクト グラフ コンポーネントを生成するために使用する 2 つの手法です。 型コンバーターとマークアップ拡張機能は、一部の特性を共有しますが、XAML ノード ストリームでは異なる方法で表現されます。 このドキュメント セットでは、型コンバーター、マークアップ拡張機能、およびこれに類似したコンストラクトを、値コンバーターと総称することがあります。  
  
<a name="value_converters"></a>   
## <a name="value-converters"></a>値コンバーター  
 XAML では、さまざまなシナリオで値コンバーターが使用されます。 XAML におけるさまざまな種類の値コンバーターは次のとおりです。  
  
- 型コンバーター  
  
- マークアップ拡張機能  
  
- 値シリアライザー  
  
- XAML テキスト構文のロジックを提供する関連クラスまたはサポート クラス  
  
<a name="type_converters"></a>   
## <a name="type-converters"></a>型コンバーター  
 .NET Framework XAML サービスの定義では、型コンバーターは CLR の <xref:System.ComponentModel.TypeConverter> クラスから派生したクラスです。 <xref:System.ComponentModel.TypeConverter> XAML が導入される前に、Microsoft .NET Framework にあったクラスです。 当初の目的は、プロパティ ウィンドウや、[!INCLUDE[TLA2#tla_ide](../../../includes/tla2sharptla-ide-md.md)] プロパティの同様のテキスト ベースの編集をサポートすることでした。 XAML への .NET Framework の導入では、<xref:System.ComponentModel.TypeConverter> を使用して、テキスト構文 (属性値または XAML 値ノードに含まれる) をオブジェクトに変換します。 <xref:System.ComponentModel.TypeConverter> オブジェクトの値をテキスト構文にシリアル化にも使用できます。 <xref:System.ComponentModel.TypeConverter> でも Windows Presentation Foundation (WPF) や Windows Communication Foundation (WCF) で以前のフレームワーク固有 XAML 実装で使用されていました。 XAML の <xref:System.ComponentModel.TypeConverter> の詳細については、「[XAML の型コンバーターの概要](type-converters-for-xaml-overview.md) といった以前のフレームワーク固有の XAML 実装でも使用されていました。  
  
<a name="markup_extensions"></a>   
## <a name="markup-extensions"></a>マークアップ拡張機能  
 .NET Framework XAML サービスの実装では、マークアップ拡張機能は <xref:System.Windows.Markup.MarkupExtension> クラスから派生したクラスです。 この形式のマークアップ拡張機能は、XAML 言語で考案された概念です。 マークアップ拡張機能は、サービス クラスを呼び出してロジックを提供する、拡張性を持ったエスケープ シーケンスのようなものと考えることができます。 マークアップの観点からすると、XAML プロセッサは、テキスト文字列内の左中かっこ ({) で始まるテキスト シーケンスによってマークアップ拡張機能を汎用的に認識します。  
  
 マークアップ拡張機能は、型コンバーターとは異なります。 型コンバーターは、通常、型またはメンバーに関連付けられ、 オブジェクト グラフの作成またはシリアル化においてそれらのエンティティに関連付けられたテキスト構文が検出されると呼び出されます。  
  
 マークアップ拡張機能は、単一のサポート サービス クラスに関連付けられますが、任意のメンバー値に適用できます。 (ただし、マークアップ拡張機能の実装では、サービス コンテキストを使用することにより、その用途を特定のメンバーまたは変換先の型に意図的に制限することもできます。)マークアップ拡張機能は、型コンバーターの関連付けをオーバーライドできます。 または、テキスト構文をサポートしないメンバーの属性値を指定するためにマークアップ拡張機能を使用することもできます。  
  
 XAML でのマークアップ拡張機能の実装パターンの詳細については、「[XAML のマークアップ拡張機能の概要](markup-extensions-for-xaml-overview.md)」を参照してください。  
  
> [!NOTE]
>  <xref:System.Windows.Markup.MarkupExtension> 型と <xref:System.Windows.Markup.ValueSerializer> 型はどちらも、 <xref:System.Windows.Markup> 名前空間ではなく、 <xref:System.Xaml> 名前空間にあります。 これらの型がそれ以外の場合、文字列を含む CLR 名前空間を設定、WPF、または Windows フォームのいずれかのテクノロジに固有であるわけ`Windows`します。 <xref:System.Windows.Markup.MarkupExtension> と <xref:System.Windows.Markup.ValueSerializer> は System.Xaml アセンブリにあり、特定のフレームワークとの依存関係はありません。 これらの型が CLR 名前空間に存在していた[!INCLUDE[net_v30_short](../../../includes/net-v30-short-md.md)]と既存の WPF プロジェクトの参照は破損を回避するために .NET Framework 4 の CLR 名前空間に残ります。 詳細については、「 [Types Migrated from WPF to System.Xaml](types-migrated-from-wpf-to-system-xaml.md)」を参照してください。  
  
<a name="value_serializers"></a>   
## <a name="value-serializers"></a>値シリアライザー  
 <xref:System.Windows.Markup.ValueSerializer> は、オブジェクトを文字列に変換するために最適化された特殊な型コンバーターです。 XAML の <xref:System.Windows.Markup.ValueSerializer> は、 `ConvertFrom` メソッドを一切実装しません。 <xref:System.Windows.Markup.ValueSerializer> 実装は、 <xref:System.ComponentModel.TypeConverter> 実装と同様の方法でサービスを取得します 仮想メソッドは入力 `context` パラメーターを提供しています。 `context` パラメーターの型は <xref:System.Windows.Markup.IValueSerializerContext>であり、 <xref:System.IServiceProvider> インターフェイスを継承し、 <xref:System.IServiceProvider.GetService%2A> メソッドを持ちます。  
  
 XAML 型システムと、シリアル化のために XAML ノード ループ処理を使用する XAML ライターの実装では、型またはメンバーに関連付けられた値コンバーターは、独自の <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> プロパティによって報告されます。 シリアル化を実行する XAML ライターにとっては、 <xref:System.Xaml.XamlType.TypeConverter%2A?displayProperty=nameWithType> と <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> が存在する場合には、読み込みパス用に型コンバーターを使用し、保存パス用に値シリアライザーを使用する必要があるということを意味しています。 <xref:System.Xaml.XamlType.TypeConverter%2A?displayProperty=nameWithType> は存在するものの、 <xref:System.Xaml.XamlType.ValueSerializer%2A?displayProperty=nameWithType> が `null`の場合は、保存パス用にも型コンバーターを使用します。  
  
<a name="other_value_converters"></a>   
## <a name="other-value-converters"></a>その他の値コンバーター  
 値コンバーターは、型コンバーターまたはマークアップ拡張機能の特定のパターンを超えて拡張できます。 ただし、このカスタマイズを行うには、.NET Framework XAML サービスによって提供される XAML 型システムも再定義する必要があります。 既存の XAML 型システムには、型コンバーター、マークアップ拡張機能、および値シリアライザー向けの表現とレポート システムがありますが、値変換のカスタム形式向けの表現とレポート システムはありません。 カスタム値コンバーターを作成する場合は、 <xref:System.Xaml.Schema.XamlValueConverter%601> 型を使用します。  
  
<a name="type_converters_and_markup_extensions_in_combination"></a>   
## <a name="type-converters-and-markup-extensions-in-combination"></a>型コンバーターとマークアップ拡張機能の組み合わせ  
 マークアップ拡張機能と型コンバーターは、XAML の異なる状況で使用されます。 マークアップ拡張機能の使用時にはコンテキストを利用できますが、マークアップ拡張機能が値を提供するプロパティの型変換動作は一般にマークアップ拡張機能の実装ではチェックされません。 つまり、マークアップ拡張機能が `ProvideValue` 出力としてテキスト文字列を返す場合でも、特定のプロパティまたはプロパティ値型に適用される、その文字列に対する型変換動作は呼び出されません。 一般に、マークアップ拡張機能の目的は、型コンバーターを呼び出さずに文字列を処理してオブジェクトを返すことです。  
  
<a name="service_context_for_a_value_converter"></a>   
## <a name="service-context-for-a-value-converter"></a>値コンバーターのサービス コンテキスト  
 値コンバーターを実装する際には、通常、値コンバーターが適用されるコンテキストにアクセスする必要があります。 このコンテキストは、サービス コンテキストと呼ばれます。 サービス コンテキストには、アクティブな XAML スキーマ コンテキスト、XAML スキーマ コンテキストや XAML オブジェクト ライターが提供する型マッピング システムへのアクセスなどの情報が含まれます。 値コンバーターで使用可能なサービス コンテキストとサービス コンテキストが提供するサービスへのアクセス方法の詳細については、「[型コンバーターおよびマークアップ拡張機能で使用できるサービス コンテキスト](service-contexts-available-to-type-converters-and-markup-extensions.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Markup.MarkupExtension>
- <xref:System.Xaml.XamlObjectWriter>
- [XAML のマークアップ拡張機能の概要](markup-extensions-for-xaml-overview.md)
- [XAML の型コンバーターの概要](type-converters-for-xaml-overview.md)
- [Service Contexts Available to Type Converters and Markup Extensions](service-contexts-available-to-type-converters-and-markup-extensions.md)
