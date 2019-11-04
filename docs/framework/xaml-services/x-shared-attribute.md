---
title: x:Shared 属性
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], x:Shared attribute
- x:Shared attribute [XAML Services]
- Shared attribute in XAML [XAML Services]
ms.assetid: c8cff434-2785-405f-9f95-16deb34c9e64
ms.openlocfilehash: c820a9b1d9708e24b1460378199a6addc1e20899
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459928"
---
# <a name="xshared-attribute"></a>x:Shared 属性
`false`に設定すると、WPF のリソース取得動作を変更して、すべての要求に対して同じインスタンスを共有するのではなく、属性付きリソースの要求によって要求ごとに新しいインスタンスが作成されるようにします。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```xaml  
<ResourceDictionary>  
  <object x:Shared="false".../>  
</ResourceDictionary>  
```  
  
## <a name="remarks"></a>Remarks  
 `x:Shared` は xaml 言語の XAML 名前空間にマップされ、xaml サービスとその XAML リーダー .NET Framework によって有効な XAML 言語要素として認識されます。 ただし、`x:Shared` に示されている機能は、WPF アプリケーションと WPF XAML パーサーにのみ関連します。 WPF では、WPF <xref:System.Windows.ResourceDictionary>内に存在するオブジェクトに適用される場合、`x:Shared` は属性としてのみ役立ちます。 その他の使用方法では、解析例外やその他のエラーはスローされませんが、効果はありません。  
  
 `x:Shared` の意味は、XAML 言語仕様では指定されていません。 .NET Framework XAML サービス上に構築されるようなその他の XAML 実装は、必ずしもリソース共有のサポートを提供するわけではありません。 このような XAML 実装は、値の `x:Shared` も使用する、サポートフレームワークで同様の動作を提供する可能性があります。  
  
 WPF では、リソースの既定の `x:Shared` 条件が `true`ます。 この条件は、特定のリソース要求が常に同じインスタンスを返すことを意味します。  
  
 リソース API によって返されたオブジェクト (<xref:System.Windows.FrameworkElement.FindResource%2A>など) を変更したり、<xref:System.Windows.ResourceDictionary>内のオブジェクトを直接変更したりすると、元のリソースが変更されます。 そのリソースへの参照が動的リソース参照であった場合、そのリソースのコンシューマーは、変更されたリソースを取得します。  
  
 リソースへの参照が静的リソース参照であった場合、[!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] の処理時間の後にリソースを変更することはできません。 静的リソース参照と動的リソース参照の詳細については、「 [XAML Resources](../../desktop-wpf/fundamentals/xaml-resources-define.md)」を参照してください。  
  
 `x:Shared="true"` は、既に既定値であるため、明示的に指定することはほとんどありません。 WPF オブジェクトモデルの `x:Shared` に対応するダイレクトコードはありません。XAML の使用でのみ指定でき、既定の WPF の動作、または .NET Framework XAML サービスとその XAML リーダーを使用して処理された場合は、読み込みパスの中間 XAML ノードストリームで処理する必要があります。  
  
 `x:Shared="false"` のシナリオは、<xref:System.Windows.FrameworkElement> または <xref:System.Windows.FrameworkContentElement> 派生クラスをリソースとして定義し、要素リソースをコンテンツモデルに導入する場合です。 `x:Shared="false"` を使用すると、要素リソースを同じコレクション (<xref:System.Windows.Controls.UIElementCollection>など) に複数回導入できます。 `x:Shared="false"` がない場合、コレクションはその内容の一意性を強制するため無効です。 ただし、`x:Shared="false"` の動作では、同じインスタンスを返す代わりに、リソースの同じインスタンスがもう1つ作成されます。  
  
 `x:Shared="false"` のもう1つのシナリオは、<xref:System.Windows.Freezable> リソースをアニメーション値に使用し、アニメーションごとにリソースを変更する場合です。  
  
 `false` の文字列処理では、大文字と小文字は区別されません。  
  
 WPF では、`x:Shared` は次の条件下でのみ有効です。  
  
- `x:Shared` を持つ項目を含む <xref:System.Windows.ResourceDictionary> をコンパイルする必要があります。 <xref:System.Windows.ResourceDictionary> をルース XAML の内側に配置したり、テーマに使用したりすることはできません。  
  
- 項目を含む <xref:System.Windows.ResourceDictionary> を別の <xref:System.Windows.ResourceDictionary>内で入れ子にすることはできません。 たとえば、既に <xref:System.Windows.ResourceDictionary> 項目である <xref:System.Windows.Style> 内にある <xref:System.Windows.ResourceDictionary> 内の項目に対して `x:Shared` を使用することはできません。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.ResourceDictionary>
- [XAML リソース](../../desktop-wpf/fundamentals/xaml-resources-define.md)
- [基本要素](../wpf/advanced/base-elements.md)
