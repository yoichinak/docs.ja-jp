---
title: x:Type マークアップ拡張機能
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
ms.openlocfilehash: df0b3fe53cb8f284fc6e2d79a9b2cea86318d701
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459919"
---
# <a name="xtype-markup-extension"></a>x:Type マークアップ拡張機能
指定された XAML 型の基になる型である CLR <xref:System.Type> オブジェクトを提供します。  
  
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
|`prefix`|省略可能です。 既定以外の XAML 名前空間をマップするプレフィックス。 多くの場合、プレフィックスを指定する必要はありません。 「解説」を参照してください。|  
|`typeNameValue`|必須です。 現在の既定の XAML 名前空間に解決可能な型名。`prefix` が指定されている場合は、指定したマップ済みプレフィックス。|  
  
## <a name="remarks"></a>Remarks  
 `x:Type` マークアップ拡張機能には、のC# `typeof()` 演算子、または Microsoft Visual Basic の `GetType` 演算子と同様の機能があります。  
  
 `x:Type` マークアップ拡張機能は、型 <xref:System.Type>を受け取るプロパティに対して、文字列変換動作を提供します。 入力は XAML 型です。 入力 XAML 型と出力 CLR <xref:System.Type> の関係は、出力 <xref:System.Type> が入力 <xref:System.Xaml.XamlType>の <xref:System.Xaml.XamlType.UnderlyingType%2A> であることです。これは、XAML スキーマコンテキストとコンテキストによって提供される <xref:System.Xaml.XamlType> サービスに基づいて必要な <xref:System.Windows.Markup.IXamlTypeResolver> を検索した後に実行されます。  
  
 .NET Framework XAML サービスでは、このマークアップ拡張機能の処理は <xref:System.Windows.Markup.TypeExtension> クラスによって定義されます。  
  
 特定のフレームワーク実装では、値として <xref:System.Type> を受け取る一部のプロパティは、型の名前 (`Name`型の文字列値) を直接受け取ることができます。 ただし、この動作の実装は複雑なシナリオです。 例については、後述の「WPF の使用に関する注意事項」を参照してください。  
  
 属性構文は、このマークアップ拡張機能で使用される最も一般的な構文です。 `x:Type` 識別子文字列の後に設定される文字列トークンは、基になる <xref:System.Windows.Markup.TypeExtension.TypeName%2A> 拡張クラスの <xref:System.Windows.Markup.TypeExtension> 値として割り当てられます。 CLR 型に基づく .NET Framework XAML サービスの既定の XAML スキーマコンテキストでは、この属性の値は目的の型の <xref:System.Reflection.MemberInfo.Name%2A> のいずれかになります。または、その前に、既定以外の XAML 名前空間マッピングのプレフィックスが付いた <xref:System.Reflection.MemberInfo.Name%2A> を含んでいます。  
  
 `x:Type` マークアップ拡張機能は、オブジェクト要素構文で使用できます。 この場合、拡張機能を正しく初期化するには、<xref:System.Windows.Markup.TypeExtension.TypeName%2A> プロパティの値を指定する必要があります。  
  
 `x:Type` マークアップ拡張機能は、verbose 属性としても使用できます。ただし、この使用は一般的ではありません。 `<object property="{x:Type TypeName=typeNameValue}" .../>`  
  
## <a name="wpf-usage-notes"></a>WPF の使用上の注意  
  
### <a name="default-xaml-namespace-and-type-mapping"></a>既定の XAML 名前空間と型のマッピング  
 WPF プログラミングの既定の XAML 名前空間には、一般的な XAML シナリオに必要な XAML 型の大部分が含まれています。そのため、多くの場合、XAML 型の値を参照するときにプレフィックスを避けることができます。 カスタムアセンブリの型を参照している場合、または WPF アセンブリに存在するが、既定の XAML 名前空間にマップされていない CLR 名前空間の型を参照している場合は、プレフィックスの割り当てが必要になることがあります。 プレフィックス、XAML 名前空間、および CLR 名前空間のマッピングの詳細については、「 [WPF xaml の Xaml 名前空間と名前空間のマッピング](../wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)」を参照してください。  
  
### <a name="type-properties-that-support-typename-as-string"></a>文字列型としての Typename をサポートする型プロパティ  
 WPF は、`x:Type` マークアップ拡張機能の使用を必要とせずに <xref:System.Type> 型の一部のプロパティの値を指定できるようにする手法をサポートしています。 代わりに、型に名前を付けた文字列として値を指定できます。 この例として、<xref:System.Windows.Controls.ControlTemplate.TargetType%2A?displayProperty=nameWithType> および <xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>があります。 この動作のサポートは、型コンバーターまたはマークアップ拡張機能では提供されません。 代わりに、これは <xref:System.Windows.FrameworkElementFactory>で実装される遅延動作です。  
  
 Silverlight は同様の規則をサポートしています。 実際、Silverlight は、XAML 言語サポートの `{x:Type}` を現在サポートしていません。また、WPF と Silverlight の XAML 移行をサポートするように設計されたいくつかの状況では `{x:Type}` 使用を受け入れません。 そのため、typename としての typename の動作は、<xref:System.Type> が値であるすべての Silverlight ネイティブプロパティ評価に組み込まれています。  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009 は、ジェネリック型の追加サポートを提供し、このサポートを提供するために `x:TypeArguments` および `x:Type` の機能の動作を変更します。  
  
- `x:TypeArguments` と、ジェネリックオブジェクトのインスタンス化に関連付けられたオブジェクト要素は、ルート以外の要素にすることができます。 詳細については、 [X:TypeArguments ディレクティブ](x-typearguments-directive.md)の「XAML 2009」セクションを参照してください。  
  
- XAML 2009 では、マークアップでジェネリック型の制約を指定するための構文がサポートされています。 これは、`x:TypeArguments`、`x:Type`、または2つの機能の組み合わせによって使用できます。  
  
- XAML 2009 を読み込み用に処理するときの WPF XAML の実装では、型 <xref:System.Type>を使用する特定のフレームワークプロパティの暗黙的な型変換動作にもこの機能が追加されます。  
  
 WPF では、XAML 2009 の機能を使用できますが、ルース XAML (マークアップコンパイルされていない XAML) に対してのみ使用できます。 WPF 向けにマークアップ コンパイルされた XAML、および XAML の BAML 形式は、現在、XAML 2009 のキーワードと機能をサポートしていません。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Style>
- [スタイルとテンプレート](../wpf/controls/styling-and-templating.md)
- [XAML の概要 (WPF)](../../desktop-wpf/fundamentals/xaml.md)
- [マークアップ拡張機能と WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
