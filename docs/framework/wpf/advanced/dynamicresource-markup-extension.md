---
title: DynamicResource のマークアップ拡張機能
ms.date: 03/30/2017
f1_keywords:
- DynamicResource
- DynamicResourceExtension
helpviewer_keywords:
- XAML [WPF], DynamicResource markup extension
- DynamicResource markup extensions [WPF]
ms.assetid: 7324f243-03af-4c2b-b0db-26ac6cdfcbe4
ms.openlocfilehash: 06355c64d36d2688ef027c1940688d4c87e51ec8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964799"
---
# <a name="dynamicresource-markup-extension"></a>DynamicResource のマークアップ拡張機能
定義されたリソース[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]への参照としてその値を延期することで、任意のプロパティ属性の値を提供します。 このリソースの参照動作は、ランタイム参照に似ています。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```xml  
<object property="{DynamicResource key}" .../>  
```  
  
## <a name="xaml-property-element-usage"></a>XAML プロパティ要素の使用  
  
```xml  
<object>  
  <object.property>  
    <DynamicResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`key`|要求されたリソースのキー。 このキーは、リソースがマークアップで作成された場合、またはコードでリソースが作成`key`された<xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>場合にを呼び出すときにパラメーターとして指定された場合、最初に[x:Key ディレクティブ](../../xaml-services/x-key-directive.md)によって割り当てられました。|  
  
## <a name="remarks"></a>Remarks  
 は`DynamicResource` 、初期コンパイル中に一時式を作成するため、オブジェクトを構築するために要求されたリソース値が実際に必要になるまで、リソースの参照を延期します。 これは、 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ページが読み込まれた後に発生する可能性があります。 リソース値は、現在のページスコープから始まるすべてのアクティブなリソースディクショナリに対するキー検索に基づいて検出され、コンパイルからのプレースホルダー式の代わりに使用されます。  
  
> [!IMPORTANT]
> 依存関係プロパティの優先順位に関し`DynamicResource`ては、式は動的リソース参照が適用される位置と同じです。 以前にローカル値`DynamicResource` `DynamicResource`として式を持つプロパティのローカル値を設定すると、が完全に削除されます。 詳細については、「[依存関係プロパティ値の優先順位](dependency-property-value-precedence.md)」を参照してください。  
  
 特定のリソースアクセスシナリオは、 `DynamicResource` [StaticResource マークアップ拡張機能](staticresource-markup-extension.md)ではなく、特に適しています。 `DynamicResource`との相対的な利点とパフォーマンスへの影響については、「[XAML リソース](xaml-resources.md)」を参照して`StaticResource`ください。  
  
 指定さ<xref:System.Windows.DynamicResourceExtension.ResourceKey%2A>れたは、ページ、アプリケーション、使用可能なコントロールのテーマと外部リソース、またはシステムリソースについて、 [x:Key ディレクティブ](../../xaml-services/x-key-directive.md)によって決定された既存のリソースに対応する必要があります。この順序で。 静的リソースと動的リソースのリソース検索の詳細については、「 [XAML リソース](xaml-resources.md)」を参照してください。  
  
 リソースキーは、 [XamlName 文法](../../xaml-services/xamlname-grammar.md)で定義されている任意の文字列にすることができます。 リソースキーは、などの他のオブジェクトの種類<xref:System.Type>である場合もあります。 キー <xref:System.Type>は、テーマによってコントロールをスタイル設定する方法の基本となります。 詳しくは、「[コントロールの作成の概要](../controls/control-authoring-overview.md)」を参照してください。  
  
 などのリソース値<xref:System.Windows.FrameworkElement.FindResource%2A>を参照するための api は、で`DynamicResource`使用されるのと同じリソース参照ロジックに従います。  
  
 リソースを参照する別の宣言的な方法は、 [StaticResource マークアップ拡張機能](staticresource-markup-extension.md)です。  
  
 属性構文は、このマークアップ拡張機能で使用される最も一般的な構文です。 `DynamicResource` 識別子文字列の後に設定される文字列トークンは、基になる <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> 拡張クラスの <xref:System.Windows.DynamicResourceExtension> 値として割り当てられます。  
  
 `DynamicResource`オブジェクト要素構文で使用できます。 この場合、 <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A>プロパティの値を指定する必要があります。  
  
 `DynamicResource` は、<xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> プロパティをプロパティおよび値のペアとして指定する詳細出力属性使用でも使用できます。  
  
```xml  
<object property="{DynamicResource ResourceKey=key}" .../>  
```  
  
 詳細出力の使用は、複数の設定可能プロパティを持つ拡張機能や、一部のプロパティがオプションである場合に役立ちます。 `DynamicResource` には、必須の設定可能プロパティが 1 つしか存在しないため、このような詳細出力の使用は一般的ではありません。  
  
 プロセッサ実装では、このマークアップ<xref:System.Windows.DynamicResourceExtension>拡張機能の処理はクラスによって定義されます。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 `DynamicResource` はマークアップ拡張機能です。 一般にマークアップ拡張機能を実装するのは、属性値をリテラル値やハンドラー名以外にエスケープする要件が存在し、その要件の適用範囲がグローバルで、特定の型やプロパティに型コンバーターを適用するだけにとどまらない場合です。 のすべての[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]マークアップ拡張機能は、属性構文で {および} 文字を使用します。これ[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]は、マークアップ拡張機能が属性を処理する必要があることをプロセッサが認識する規則です。 詳細については、「[マークアップ拡張機能」および「WPF XAML](markup-extensions-and-wpf-xaml.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [XAML リソース](xaml-resources.md)
- [リソースとコード](resources-and-code.md)
- [x:Key ディレクティブ](../../xaml-services/x-key-directive.md)
- [XAML の概要 (WPF)](xaml-overview-wpf.md)
- [マークアップ拡張機能と WPF XAML](markup-extensions-and-wpf-xaml.md)
- [StaticResource のマークアップ拡張機能](staticresource-markup-extension.md)
- [マークアップ拡張機能と WPF XAML](markup-extensions-and-wpf-xaml.md)
