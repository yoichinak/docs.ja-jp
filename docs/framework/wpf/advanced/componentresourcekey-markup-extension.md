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
ms.openlocfilehash: 4cdba2a61be4e9686cd2120fd90a213534c222c8
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243363"
---
# <a name="componentresourcekey-markup-extension"></a>ComponentResourceKey マークアップ拡張機能
外部アセンブリから読み込まれるリソースのキーを定義および参照します。 これにより、アセンブリまたはクラスで明示的なリソース ディクショナリではなく、アセンブリ内のターゲット型を指定するリソースルックアップが可能になります。  
  
## <a name="xaml-attribute-usage-setting-key-compact"></a>XAML 属性の使用 (設定キー、コンパクト)  
  
```xml  
<object x:Key="{ComponentResourceKey {x:Type targetTypeName}, targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-setting-key-verbose"></a>XAML 属性の使用 (キー、詳細な設定)  
  
```xml  
<object x:Key="{ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-compact"></a>XAML 属性の使用 (リソースの要求、コンパクト)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey {x:Type targetTypeName}, targetID}}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-verbose"></a>XAML 属性の使用 (リソースの要求、詳細)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}}" .../>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`targetTypeName`|リソース アセンブリで定義されているパブリック共通言語ランタイム (CLR) 型の名前。|  
|`targetID`|リソースのキー。 リソースを検索すると、`targetID`リソースの[x:Key ディレクティブ](../../../desktop-wpf/xaml-services/xkey-directive.md)に類似します。|  
  
## <a name="remarks"></a>解説  
 上記の使用方法で見られるように、 {`ComponentResourceKey`} マークアップ拡張機能の使用は 2 箇所にあります。  
  
- コントロールの作成者が提供する、テーマ リソース ディクショナリ内のキーの定義。  
  
- コントロールを再設定するが、コントロールのテーマによって提供されるリソースから取得したプロパティ値を使用する場合は、アセンブリからテーマ リソースにアクセスします。  
  
 テーマから取得したコンポーネント リソースを参照する場合は、通常、 ではなく`{DynamicResource}``{StaticResource}`を使用することをお勧めします。 これは、使用方法に示されています。 `{DynamicResource}`テーマ自体はユーザーが変更できるため、お勧めします。 テーマをサポートするコントロール作成者の意図に最も近いコンポーネント リソースを使用する場合は、コンポーネント リソース参照も動的にする必要があります。  
  
 リソース<xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>が実際に定義されているターゲット アセンブリに存在する型を識別します。 を`ComponentResourceKey`定義し、定義<xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>されている場所を正確に知ることとは別に使用できますが、最終的には参照アセンブリを通じて型を解決する必要があります。  
  
 一般的な<xref:System.Windows.ComponentResourceKey>用途は、クラスのメンバーとして公開されるキーを定義することです。 この使用法では、マークアップ拡張機能<xref:System.Windows.ComponentResourceKey>ではなくクラス コンストラクターを使用します。 詳細については、「 」<xref:System.Windows.ComponentResourceKey>または トピック「[コントロールオーサリングの概要](../controls/control-authoring-overview.md)」の「テーマリソースのキーの定義と参照」セクションを参照してください。  
  
 キーの確立とキー付きリソースの参照の両方で、属性構文は通常、`ComponentResourceKey`マークアップ拡張機能に使用されます。  
  
 この compact 構文は、コンストラクター<xref:System.Windows.ComponentResourceKey.%23ctor%2A>シグネチャとマークアップ拡張機能の位置指定パラメーターの使用法に依存しています。 と`targetTypeName``targetID`が与えられる順序は重要です。 詳細な構文は、パラメーターなしの<xref:System.Windows.ComponentResourceKey.%23ctor%2A>コンストラクターに依存し、オブジェクト要素の真<xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>の<xref:System.Windows.ComponentResourceKey.ResourceId%2A>属性構文に類似した方法で and を設定します。 詳細な構文では、プロパティが設定される順序は重要ではありません。 これら 2 つの代替手段 (コンパクトと詳細) の関係とメカニズムについては、「[マークアップ拡張機能と WPF XAML」](markup-extensions-and-wpf-xaml.md)のトピックで詳しく説明します。  
  
 技術的には、値は`targetID`任意のオブジェクトにすることができ、文字列である必要はありません。 ただし、WPFWPF で最もよく使用される使用方法は`targetID`、値を文字列で配置し、XamlName[の文法](../../../desktop-wpf/xaml-services/xamlname-grammar.md)でこのような文字列が有効な場所に配置することです。  
  
 `ComponentResourceKey`オブジェクト要素構文で使用できます。 この場合、拡張機能を適切に初期化するには<xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>、 および<xref:System.Windows.ComponentResourceKey.ResourceId%2A>プロパティの両方の値を指定する必要があります。  
  
 リーダーの[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)][!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]実装では、このマークアップ拡張機能の処理は、クラスによって定義されます<xref:System.Windows.ComponentResourceKey>。  
  
 `ComponentResourceKey` はマークアップ拡張機能です。 一般にマークアップ拡張機能を実装するのは、属性値をリテラル値やハンドラー名以外にエスケープする要件が存在し、その要件の適用範囲がグローバルで、特定の型やプロパティに型コンバーターを適用するだけにとどまらない場合です。 すべてのマークアップ拡張機能は[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、属性構文で { と } 文字を使用します[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]。 詳細については、「[マークアップ拡張機能と WPF XAML](markup-extensions-and-wpf-xaml.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.ComponentResourceKey>
- <xref:System.Windows.Controls.ControlTemplate>
- [コントロールの作成の概要](../controls/control-authoring-overview.md)
- [XAML の概要 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [マークアップ拡張機能と WPF XAML](markup-extensions-and-wpf-xaml.md)
