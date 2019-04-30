---
title: ComponentResourceKey マークアップ拡張機能
ms.date: 03/30/2017
f1_keywords:
- ComponentResourceKey
- ComponentResourceKeyExtension
helpviewer_keywords:
- ComponentResourceKey markup extension [WPF]
- XAML [WPF], ComponentResourceKey markup extension
ms.assetid: d6bcdbe6-61b3-40a7-b381-4e02185b5a85
ms.openlocfilehash: 5f72d6c3273cfda4276383cfe72f90196e5d4340
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62037753"
---
# <a name="componentresourcekey-markup-extension"></a>ComponentResourceKey マークアップ拡張機能
定義し、外部アセンブリから読み込まれたリソースのキーを参照します。 これにより、アセンブリ内、またはクラスの明示的なリソース ディクショナリではなく、アセンブリでは、対象の型を指定するリソースの検索ができます。  
  
## <a name="xaml-attribute-usage-setting-key-compact"></a>XAML 属性の使用法 (設定キー、compact)  
  
```xml  
<object x:Key="{ComponentResourceKey {x:Type targetTypeName}, targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-setting-key-verbose"></a>XAML 属性の使用法 (キー、詳細設定)  
  
```xml  
<object x:Key="{ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-compact"></a>XAML 属性の使用法 (リソース要求、compact)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey {x:Type targetTypeName}, targetID}}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-verbose"></a>XAML 属性の使用法 (リソース要求、詳細)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}}" .../>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`targetTypeName`|パブリック名[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]リソース アセンブリで定義されている型。|  
|`targetID`|リソースのキー。 リソースの問い合わせがあったときに`targetID`に似ていますが、 [X:key ディレクティブ](../../xaml-services/x-key-directive.md)のリソース。|  
  
## <a name="remarks"></a>Remarks  
 使用状況は、上記に示すよう、{`ComponentResourceKey`} マークアップ拡張機能の使用が 2 つの場所が見つかりました。  
  
- コントロールの作成者によって提供される、テーマのリソース ディクショナリ内のキーの定義。  
  
- テーマ リソースにアクセスするアセンブリから、ときにテンプレートを再設定、コントロールがコントロールのテーマによって提供されるリソースから取得したプロパティ値を使用します。  
  
 テーマに由来するコンポーネントのリソースを参照するには、一般にお勧めを使用すること`{DynamicResource}`なく`{StaticResource}`します。 これは、使用法に表示されます。 `{DynamicResource}` ユーザーがそれ自体のテーマを変更できるためお勧めします。 コンポーネント リソース、テーマをサポートするためのコントロールの作成者の意図に最も一致する場合は、コンポーネントのリソース参照も動的であるが有効にする必要があります。  
  
 <xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>リソースが実際に定義されているターゲット アセンブリ内に存在する型を指定します。 A`ComponentResourceKey`定義して正確に知ることとは無関係に使用できる場所、<xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>を定義しても、最終的に参照されたアセンブリから型を解決する必要があります。  
  
 一般的な使用方法<xref:System.Windows.ComponentResourceKey>クラスのメンバーとして、公開されているキーを定義することです。 この方法で使用する、<xref:System.Windows.ComponentResourceKey>クラスのコンス トラクター、マークアップ拡張機能ではありません。 詳細については、次を参照してください。 <xref:System.Windows.ComponentResourceKey>、またはトピックの"定義し、を参照するキーのテーマのリソース"セクション[コントロールの作成の概要](../controls/control-authoring-overview.md)します。  
  
 属性構文は、一般に使用するキーを確立してを参照するキーを持つリソース、用、`ComponentResourceKey`マークアップ拡張機能。  
  
 コンパクトな構文に依存、<xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType>コンス トラクターのシグネチャとマークアップ拡張機能の位置指定パラメーターの使用方法。 順序、`targetTypeName`と`targetID`されたことが重要です。 冗語構文に依存、<xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType>既定のコンス トラクターを設定、<xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>と<xref:System.Windows.ComponentResourceKey.ResourceId%2A>ようには、オブジェクト要素の場合は true。 属性構文に似ています。 詳細な構文では、プロパティが設定されている順序は重要ではありません。 リレーションシップおよびこれら 2 つの選択肢 (compact と詳細な) メカニズムがトピックで詳しく説明されている[マークアップ拡張機能と WPF XAML](markup-extensions-and-wpf-xaml.md)します。  
  
 値では技術的には、`targetID`任意のオブジェクト、文字列にすることはありません。 ただし、WPF の最も一般的な使用方法は、配置する、`targetID`値、文字列であるし、このような文字列が有効ではフォームで、 [XamlName の文法](../../xaml-services/xamlname-grammar.md)します。  
  
 `ComponentResourceKey` オブジェクト要素構文で使用できます。 この場合、両方の値を指定する、<xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>と<xref:System.Windows.ComponentResourceKey.ResourceId%2A>拡張機能を適切に初期化するプロパティが必要です。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]リーダー実装では、このマークアップ拡張機能の処理がによって定義されている、<xref:System.Windows.ComponentResourceKey>クラス。  
  
 `ComponentResourceKey` はマークアップ拡張機能です。 一般にマークアップ拡張機能を実装するのは、属性値をリテラル値やハンドラー名以外にエスケープする要件が存在し、その要件の適用範囲がグローバルで、特定の型やプロパティに型コンバーターを適用するだけにとどまらない場合です。 すべてのマークアップ拡張機能で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を使用して、{および} される規則は、それぞれの属性構文内の文字を[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサを認識するマークアップ拡張機能が、属性を処理する必要があります。 詳細については、次を参照してください。[マークアップ拡張機能と WPF XAML](markup-extensions-and-wpf-xaml.md)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.ComponentResourceKey>
- <xref:System.Windows.Controls.ControlTemplate>
- [コントロールの作成の概要](../controls/control-authoring-overview.md)
- [XAML の概要 (WPF)](xaml-overview-wpf.md)
- [マークアップ拡張機能と WPF XAML](markup-extensions-and-wpf-xaml.md)
