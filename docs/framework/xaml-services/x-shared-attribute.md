---
title: x:Shared 属性
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], x:Shared attribute
- x:Shared attribute [XAML Services]
- Shared attribute in XAML [XAML Services]
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
ms.openlocfilehash: 42de341d59e3e70103db765faf3160b5fe3250d3
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2019
ms.locfileid: "58039406"
---
# <a name="xshared-attribute"></a>x:Shared 属性
設定すると`false`、属性付きのリソースの要求は、すべての要求の同じインスタンスを共有することがなく、各要求の新しいインスタンスを作成するために、WPF リソース検索の動作を変更します。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```xaml  
<ResourceDictionary>  
  <object x:Shared="false".../>  
</ResourceDictionary>  
```  
  
## <a name="remarks"></a>Remarks  
 `x:Shared` XAML 言語の XAML 名前空間にマップされ、.NET Framework XAML サービスおよびその XAML リーダーで有効な XAML 言語要素として認識されます。 ただし、示された機能の`x:Shared`は WPF アプリケーションと WPF XAML パーサーに適用します。 WPF では、 `x:Shared` WPF 内に存在するオブジェクトに適用されたときに属性として便利なだけ<xref:System.Windows.ResourceDictionary>です。 その他の方法は解析例外やその他のエラーをスローしませんが、効果はありません。  
  
 意味`x:Shared`XAML 言語仕様で指定されていません。 .NET Framework XAML サービスでは、上に構築されるなど、他の XAML 実装は、必ずしもリソース共有のサポートを提供しません。 このような XAML 実装にも使用するサポートのフレームワークで同様の動作を提供できます`x:Shared`値。  
  
 WPF では、既定で`x:Shared`リソースの条件が`true`します。 この条件は、特定のリソースの要求が常に同じインスタンスを返すことを意味します。  
  
 など、API のリソースから返されるオブジェクトを変更する<xref:System.Windows.FrameworkElement.FindResource%2A>、または内で直接オブジェクトを変更する、 <xref:System.Windows.ResourceDictionary>、元のリソースを変更します。 そのリソースへの参照は、動的リソース参照が、そのリソースのコンシューマーは変更されたリソースを取得します。  
  
 場合、リソースへの参照は静的リソース参照、変更後にリソース[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)]処理時間は関係ありません。 静的および動的リソース参照の詳細については、[XAML リソース](../wpf/advanced/xaml-resources.md)を参照してください。  
  
 明示的に指定する`x:Shared="true"`はあまり一般的には、既定ではないためです。 同等の直接コードがない`x:Shared`WPF では、オブジェクト モデルは、処理する必要がある既定の WPF の動作をするか、読み込みパスで、中間の XAML ノード ストリームで .NET Framework XAML Se を使用して処理する場合、XAML の使用状況でのみ指定できますターゲットおよびその XAML リーダー。  
  
 シナリオ`x:Shared="false"`定義するかどうかは、<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>リソースとしてのクラスを派生し、コンテンツ モデルに要素のリソースを導入します。 `x:Shared="false"` により、複数回、同じコレクションに導入する、要素のリソース (など、 <xref:System.Windows.Controls.UIElementCollection>)。 せず`x:Shared="false"`でない有効なコレクションには、その内容の一意性が強制されるためです。 ただし、`x:Shared="false"`動作が同じインスタンスを返す代わりに、リソースのもう 1 つの同一インスタンスを作成します。  
  
 別のシナリオの`x:Shared="false"`使用するかどうかは、<xref:System.Windows.Freezable>アニメーション値がアニメーションあたりごとにリソースを変更するリソース。  
  
 文字列の処理`false`大文字小文字は区別されません。  
  
 WPF では、`x:Shared`次の条件でのみ有効です。  
  
-   <xref:System.Windows.ResourceDictionary>で項目を含む`x:Shared`コンパイルする必要があります。 <xref:System.Windows.ResourceDictionary> Loose XAML 内にすることはできませんまたはテーマを使用します。  
  
-   <xref:System.Windows.ResourceDictionary>項目を格納する他の中で入れ子にする必要がありますできません<xref:System.Windows.ResourceDictionary>します。 たとえば、使用することはできません`x:Shared`内の項目を<xref:System.Windows.ResourceDictionary>内にある、<xref:System.Windows.Style>にではない、<xref:System.Windows.ResourceDictionary>項目。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.ResourceDictionary>
- [XAML リソース](../wpf/advanced/xaml-resources.md)
- [基本要素](../wpf/advanced/base-elements.md)
