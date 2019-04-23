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
ms.openlocfilehash: d07816718ebee2507f1888cffb70e6f8037bb996
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59091409"
---
# <a name="dynamicresource-markup-extension"></a>DynamicResource のマークアップ拡張機能
いずれかの値を提供[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]定義されているリソースへの参照にするには、その値を遅らせることで、プロパティの属性。 そのリソースの検索の動作は、実行時参照に似ています。  
  
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
|`key`|要求されたリソースのキー。 このキーはによって最初に割り当てられた、 [X:key ディレクティブ](../../xaml-services/x-key-directive.md)リソースのマークアップでは、作成されたまたはが指定されているかどうか、`key`パラメーターを呼び出すときに<xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>リソースは、コードで作成した場合。|  
  
## <a name="remarks"></a>Remarks  
 A`DynamicResource`最初のコンパイル中に一時的な式を作成し、要求されたリソースの値が実際にオブジェクトを構築するために必要になるまで遅延リソースの参照。 後にこの可能性があります、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ページが読み込まれます。 リソースの値に対して現在のページ範囲から始まるすべてのアクティブなリソース ディクショナリのキーの検索に基づく検出し、コンパイルのプレース ホルダーの式の代わりに使用します。  
  
> [!IMPORTANT]
>  依存関係プロパティの優先順位の観点から、`DynamicResource`式は、動的リソース参照が適用される位置に相当します。 以前に使用できるプロパティのローカル値を設定するかどうか、 `DynamicResource` 、ローカルの値として式、`DynamicResource`が完全に削除します。 詳細については、「[依存関係プロパティ値の優先順位](dependency-property-value-precedence.md)」を参照してください。  
  
 特定のリソースへのアクセスのシナリオは、特に適して`DynamicResource`ではなく、 [StaticResource マークアップ拡張機能](staticresource-markup-extension.md)します。 参照してください[XAML リソース](xaml-resources.md)相対的なメリットとパフォーマンスの問題についてディスカッションを`DynamicResource`と`StaticResource`します。  
  
 指定した<xref:System.Windows.DynamicResourceExtension.ResourceKey%2A>によって既存のリソースに対応する[X:key ディレクティブ](../../xaml-services/x-key-directive.md)ページ、アプリケーション、使用可能なコントロールのテーマと外部のリソースなどのシステム リソースのいくつかのレベルで、リソースの検索は、この順序で実行されます。 静的および動的なリソースのリソース ルックアップの詳細については、次を参照してください。 [XAML リソース](xaml-resources.md)します。  
  
 リソース キーの任意の文字列で定義されている可能性があります、 [XamlName の文法](../../xaml-services/xamlname-grammar.md)します。 リソース キーがあります、その他のオブジェクトの種類など、<xref:System.Type>します。 A<xref:System.Type>キーがテーマでのコントロールのスタイル方法の基礎です。 詳しくは、「[コントロールの作成の概要](../controls/control-authoring-overview.md)」を参照してください。  
  
 [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)] リソースの値の検索など<xref:System.Windows.FrameworkElement.FindResource%2A>で使用したのと同じリソース ルックアップ ロジックに従う`DynamicResource`。  
  
 リソースを参照するための代替の宣言型の手段は、 [StaticResource マークアップ拡張機能](staticresource-markup-extension.md)します。  
  
 属性構文は、このマークアップ拡張機能で使用される最も一般的な構文です。 `DynamicResource` 識別子文字列の後に設定される文字列トークンは、基になる <xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> 拡張クラスの <xref:System.Windows.DynamicResourceExtension> 値として割り当てられます。  
  
 `DynamicResource` オブジェクト要素構文で使用できます。 この場合は、値を指定する、<xref:System.Windows.DynamicResourceExtension.ResourceKey%2A>プロパティが必要です。  
  
 `DynamicResource` は、<xref:System.Windows.DynamicResourceExtension.ResourceKey%2A> プロパティをプロパティおよび値のペアとして指定する詳細出力属性使用でも使用できます。  
  
```xml  
<object property="{DynamicResource ResourceKey=key}" .../>  
```  
  
 詳細出力の使用は、複数の設定可能プロパティを持つ拡張機能や、一部のプロパティがオプションである場合に役立ちます。 `DynamicResource` には、必須の設定可能プロパティが 1 つしか存在しないため、このような詳細出力の使用は一般的ではありません。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサの実装でこのマークアップ拡張機能の処理が定義されている、<xref:System.Windows.DynamicResourceExtension>クラス。  
  
 `DynamicResource` はマークアップ拡張機能です。 一般にマークアップ拡張機能を実装するのは、属性値をリテラル値やハンドラー名以外にエスケープする要件が存在し、その要件の適用範囲がグローバルで、特定の型やプロパティに型コンバーターを適用するだけにとどまらない場合です。 すべてのマークアップ拡張機能で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を使用して、{および} される規則は、それぞれの属性構文内の文字を[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサを認識するマークアップ拡張機能が、属性を処理する必要があります。 詳細については、次を参照してください。[マークアップ拡張機能と WPF XAML](markup-extensions-and-wpf-xaml.md)します。  
  
## <a name="see-also"></a>関連項目

- [XAML リソース](xaml-resources.md)
- [リソースとコード](resources-and-code.md)
- [x:Key ディレクティブ](../../xaml-services/x-key-directive.md)
- [XAML の概要 (WPF)](xaml-overview-wpf.md)
- [マークアップ拡張機能と WPF XAML](markup-extensions-and-wpf-xaml.md)
- [StaticResource のマークアップ拡張機能](staticresource-markup-extension.md)
- [マークアップ拡張機能と WPF XAML](markup-extensions-and-wpf-xaml.md)
