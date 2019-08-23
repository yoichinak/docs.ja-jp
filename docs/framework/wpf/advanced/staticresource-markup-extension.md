---
title: StaticResource のマークアップ拡張機能
ms.date: 03/30/2017
f1_keywords:
- StaticResource
- StaticResourceExtension
helpviewer_keywords:
- XAML [WPF], StaticResource markup extension
- StaticResource markup extensions [WPF]
ms.assetid: 97af044c-71f1-4617-9a94-9064b68185d2
ms.openlocfilehash: 7392be182aedeeebe6b7092f9868c1fabfaafcb7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963456"
---
# <a name="staticresource-markup-extension"></a>StaticResource のマークアップ拡張機能
既に定義され[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ているリソースへの参照を検索することによって、任意のプロパティ属性の値を提供します。 そのリソースの参照動作は、読み込み時の参照に似ています。これにより、現在[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]のページのマークアップから以前に読み込まれたリソースと、その他のアプリケーションソースが検索され、そのリソース値が次のように生成されます。ランタイムオブジェクトのプロパティ値。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```xml  
<object property="{StaticResource key}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a>XAML オブジェクト要素の使用方法  
  
```xml  
<object>  
  <object.property>  
<StaticResource ResourceKey="key" .../>  
  </object.property>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`key`|要求されたリソースのキー。 このキーは、リソースがマークアップで作成された場合、またはコードでリソースが作成`key`された<xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType>場合にを呼び出すときにパラメーターとして指定された場合、最初に[x:Key ディレクティブ](../../xaml-services/x-key-directive.md)によって割り当てられました。|  
  
## <a name="remarks"></a>Remarks  
  
> [!IMPORTANT]
> は`StaticResource` 、 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイル内でさらに構文的に定義されているリソースへの前方参照を作成することはできません。 これを行うことはサポートされていません。このような参照が失敗しない場合でも、前方参照を試行すると、を<xref:System.Windows.ResourceDictionary>表す内部ハッシュテーブルが検索されるときに、読み込み時間のパフォーマンスが低下します。 最良の結果を得るには、前方参照を回避できるように、リソースディクショナリの構成を調整します。 前方参照を回避できない場合は、代わりに[Dynamicresource マークアップ拡張機能](dynamicresource-markup-extension.md)を使用してください。  
  
 指定する<xref:System.Windows.StaticResourceExtension.ResourceKey%2A>は、既存のリソースに対応する必要があります。これは、ページ、アプリケーション、使用可能なコントロールテーマと外部リソース、またはシステムリソースについて、 [x:Key ディレクティブ](../../xaml-services/x-key-directive.md)で識別されます。 リソースルックアップは、この順序で実行されます。 静的リソースと動的リソースのリソース検索動作の詳細については、「 [XAML リソース](xaml-resources.md)」を参照してください。  
  
 リソースキーは、 [XamlName 文法](../../xaml-services/xamlname-grammar.md)で定義されている任意の文字列にすることができます。 リソースキーは、など、他の種類<xref:System.Type>のオブジェクトにすることもできます。 <xref:System.Type>キーは、暗黙的なスタイルキーを使用して、テーマによってコントロールをスタイル設定する方法の基本となります。 詳しくは、「[コントロールの作成の概要](../controls/control-authoring-overview.md)」を参照してください。  
  
 リソースを参照する別の宣言的な方法は、 [Dynamicresource マークアップ拡張機能](dynamicresource-markup-extension.md)です。  
  
 属性構文は、このマークアップ拡張機能で使用される最も一般的な構文です。 `StaticResource` 識別子文字列の後に設定される文字列トークンは、基になる <xref:System.Windows.StaticResourceExtension.ResourceKey%2A> 拡張クラスの <xref:System.Windows.StaticResourceExtension> 値として割り当てられます。  
  
 `StaticResource`オブジェクト要素構文で使用できます。 この場合、 <xref:System.Windows.StaticResourceExtension.ResourceKey%2A>プロパティの値を指定する必要があります。  
  
 `StaticResource` は、<xref:System.Windows.StaticResourceExtension.ResourceKey%2A> プロパティをプロパティおよび値のペアとして指定する詳細出力属性使用でも使用できます。  
  
```xml  
<object property="{StaticResource ResourceKey=key}" .../>  
```  
  
 詳細出力の使用は、複数の設定可能プロパティを持つ拡張機能や、一部のプロパティがオプションである場合に役立ちます。 `StaticResource` には、必須の設定可能プロパティが 1 つしか存在しないため、このような詳細出力の使用は一般的ではありません。  
  
 プロセッサ実装では、このマークアップ<xref:System.Windows.StaticResourceExtension>拡張機能の処理はクラスによって定義されます。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 `StaticResource` はマークアップ拡張機能です。 一般にマークアップ拡張機能を実装するのは、属性値をリテラル値やハンドラー名以外にエスケープする要件が存在し、その要件の適用範囲がグローバルで、特定の型やプロパティに型コンバーターを適用するだけにとどまらない場合です。 のすべての[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]マークアップ拡張機能は、属性構文で {および} 文字を使用します。これ[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]は、マークアップ拡張機能が属性を処理する必要があることをプロセッサが認識する規則です。 詳細については、「[マークアップ拡張機能」および「WPF XAML](markup-extensions-and-wpf-xaml.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [スタイルとテンプレート](../controls/styling-and-templating.md)
- [XAML の概要 (WPF)](xaml-overview-wpf.md)
- [マークアップ拡張機能と WPF XAML](markup-extensions-and-wpf-xaml.md)
- [XAML リソース](xaml-resources.md)
- [リソースとコード](resources-and-code.md)
