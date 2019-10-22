---
title: x:Type のマークアップ拡張機能
ms.date: 03/30/2017
f1_keywords:
- x:TypeExtension
- Type
- x:Type
- xType
- TypeExtension
helpviewer_keywords:
- x:Type markup extension [XAML Services]
- XAML [XAML Services], x:Type markup extension
- XAML [XAML Services], TargetType attribute
- TargetType attribute [XAML Services]
- Type markup extension in XAML [XAML Services]
ms.assetid: e0e0ce6f-e873-49c7-8ad7-8b840eb353ec
ms.openlocfilehash: bf62987c61c1d4f6aefce515f79e997b41272b56
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64622961"
---
# <a name="xtype-markup-extension"></a>x:Type のマークアップ拡張機能
CLR の提供<xref:System.Type>指定の XAML 型の基になる型であるオブジェクト。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```xaml  
<object property="{x:Type prefix:typeNameValue}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a>XAML オブジェクト要素の使用方法  
  
```xaml  
<x:Type TypeName="prefix:typeNameValue"/>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`prefix`|任意。 既定以外の XAML 名前空間にマップされるプレフィックス。 プレフィックスを指定することは頻繁に必要ありません。 「解説」を参照してください。|  
|`typeNameValue`|必須。 現在既定の XAML 名前空間; に解決可能な型名指定した場合、マップのプレフィックスまたは`prefix`を指定します。|  
  
## <a name="remarks"></a>Remarks  
 `x:Type`マークアップ拡張機能は同様の機能を`typeof()`演算子 (C#) または`GetType`Microsoft Visual Basic での演算子。  
  
 `x:Type`マークアップ拡張機能は、型を使用するプロパティの文字列から変換動作を提供<xref:System.Type>します。 入力は、XAML の型です。 XAML の入力と出力の CLR 間のリレーションシップ<xref:System.Type>出力される<xref:System.Type>は、<xref:System.Xaml.XamlType.UnderlyingType%2A>入力の<xref:System.Xaml.XamlType>、ために必要なの検索後<xref:System.Xaml.XamlType>XAML スキーマ コンテキストと、に基づいて<xref:System.Windows.Markup.IXamlTypeResolver>サービス コンテキストを提供します。  
  
 このマークアップ拡張機能の処理がによって定義されている .NET Framework XAML サービスを<xref:System.Windows.Markup.TypeExtension>クラス。  
  
 特定のフレームワークの実装でいくつかのプロパティを受け取る<xref:System.Type>ように、値は、型の名前を直接受け入れることができます (型の文字列値`Name`)。 ただし、この動作を実装するは複雑なシナリオです。 例については、以下の「WPF の使用法」セクションを参照してください。  
  
 属性構文は、このマークアップ拡張機能で使用される最も一般的な構文です。 `x:Type` 識別子文字列の後に設定される文字列トークンは、基になる <xref:System.Windows.Markup.TypeExtension.TypeName%2A> 拡張クラスの <xref:System.Windows.Markup.TypeExtension> 値として割り当てられます。 CLR 型に基づくは、.NET Framework XAML サービスの既定の XAML スキーマ コンテキストでこの属性の値は、いずれか、<xref:System.Reflection.MemberInfo.Name%2A>の目的の型を格納または<xref:System.Reflection.MemberInfo.Name%2A>前に既定以外の XAML 名前空間のプレフィックスマッピングします。  
  
 `x:Type`オブジェクト要素構文でマークアップ拡張機能を使用できます。 この場合は、値を指定する、<xref:System.Windows.Markup.TypeExtension.TypeName%2A>拡張機能を適切に初期化するプロパティが必要です。  
  
 `x:Type`マークアップ拡張機能は、詳細属性としても使用できます。 ただしこのような使用は一般的なはありません。 `<object property="{x:Type TypeName=typeNameValue}" .../>`  
  
## <a name="wpf-usage-notes"></a>WPF の使用上の注意  
  
### <a name="default-xaml-namespace-and-type-mapping"></a>既定の XAML Namespace と型マッピング  
 WPF プログラミングの既定の XAML 名前空間には、XAML の一般的なシナリオに必要な XAML 型の大部分が含まれています。そのため、XAML 型の値を参照するときに、多くの場合、プレフィックスを回避することができます。 カスタム アセンブリから、または既定の XAML 名前空間にマップされませんでした、CLR 名前空間からは WPF アセンブリ内に存在する型の型を参照している場合、プレフィックスをマップする必要があります。 プレフィックス、XAML 名前空間と CLR 名前空間のマッピングの詳細については、次を参照してください。 [XAML 名前空間および WPF XAML の Namespace マッピング](../wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)します。  
  
### <a name="type-properties-that-support-typename-as-string"></a>そのサポート Typename としての文字列のプロパティを入力します。  
 WPF でサポートされる型の一部のプロパティの値を指定できるようにする手法<xref:System.Type>を必要とせず、`x:Type`マークアップ拡張機能を使用します。 代わりに、型に名前を文字列として値を指定することができます。 この機能にはの例については<xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType>と<xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>します。 この動作のサポートは、型コンバーターまたはマークアップ拡張機能は提供されません。 代わりに、これは、遅延の動作を使用して実装を<xref:System.Windows.FrameworkElementFactory>します。  
  
 Silverlight には、同様の規則がサポートしています。 実際には、Silverlight はサポートされていない`{x:Type}`の XAML 言語のサポートでは受け付けられません`{x:Type}`WPF Silverlight XAML の移行をサポートするためのものでは、いくつかの状況の外部で使用します。 そのため、typename に文字列としての動作がすべての Silverlight ネイティブ プロパティの評価に組み込まれている、<xref:System.Type>値です。  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009 のジェネリック型し、の機能の動作を変更します。 その他のサポートを提供します`x:TypeArguments`と`x:Type`このサポートを提供します。  
  
- `x:TypeArguments` ルート以外の要素に関連付けられたオブジェクト要素の汎用オブジェクトのインスタンス化ができます。 詳細については、の「XAML 2009」セクションを参照してください。 [X:typearguments ディレクティブ](x-typearguments-directive.md)します。  
  
- XAML 2009 は、マークアップでジェネリック型の制約を指定するための構文をサポートします。 これで使用できる`x:TypeArguments`により、 `x:Type`、または組み合わせでは、2 つの機能です。  
  
- 負荷は、型を使用する特定のフレームワーク プロパティに対して暗黙的な型変換の動作にこの機能を追加するもの XAML 2009 を処理するときに、WPF XAML 実装<xref:System.Type>します。  
  
 WPF では、loose XAML (XAML マークアップ コンパイルされていない) については、XAML 2009 の機能を使用することができます。 WPF 向けにマークアップ コンパイルされた XAML、および XAML の BAML 形式は、現在、XAML 2009 のキーワードと機能をサポートしていません。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Style>
- [スタイルとテンプレート](../wpf/controls/styling-and-templating.md)
- [XAML の概要 (WPF)](../wpf/advanced/xaml-overview-wpf.md)
- [マークアップ拡張機能と WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
