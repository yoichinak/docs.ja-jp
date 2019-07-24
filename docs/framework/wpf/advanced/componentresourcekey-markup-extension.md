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
ms.openlocfilehash: b373b33fcc962e49aa220f31e24b1484a0a8cd98
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401594"
---
# <a name="componentresourcekey-markup-extension"></a>ComponentResourceKey マークアップ拡張機能
外部アセンブリから読み込まれるリソースのキーを定義して参照します。 これにより、リソース検索では、アセンブリ内の明示的なリソースディクショナリやクラスではなく、アセンブリ内の対象の型を指定できます。  
  
## <a name="xaml-attribute-usage-setting-key-compact"></a>XAML 属性の使用法 (キーの設定、コンパクト)  
  
```xml  
<object x:Key="{ComponentResourceKey {x:Type targetTypeName}, targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-setting-key-verbose"></a>XAML 属性の使用法 (キーの設定、詳細)  
  
```xml  
<object x:Key="{ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-compact"></a>XAML 属性の使用法 (要求元のリソース、コンパクト)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey {x:Type targetTypeName}, targetID}}" .../>  
```  
  
## <a name="xaml-attribute-usage-requesting-resource-verbose"></a>XAML 属性の使用法 (要求元のリソース、詳細)  
  
```xml  
<object property="{DynamicResource {ComponentResourceKey TypeInTargetAssembly={x:Type targetTypeName}, ResourceID=targetID}}" .../>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`targetTypeName`|リソースアセンブリで定義されているパブリック共通言語ランタイム (CLR) 型の名前。|  
|`targetID`|リソースのキー。 リソースが検索されると`targetID` 、はリソースの[x:Key ディレクティブ](../../xaml-services/x-key-directive.md)に似ています。|  
  
## <a name="remarks"></a>Remarks  
 上記の使用状況に示されている`ComponentResourceKey`ように、{} マークアップ拡張機能の使用方法は次の2つの場所にあります。  
  
- コントロールの作成者によって提供される、テーマリソースディクショナリ内のキーの定義。  
  
- コントロールをテンプレートするときに、コントロールのテーマによって提供されるリソースからのプロパティ値を使用する場合に、アセンブリからテーマリソースにアクセスします。  
  
 テーマに由来するコンポーネントリソースを参照する場合は、通常は`{DynamicResource}` `{StaticResource}`ではなくを使用することをお勧めします。 これは、使用法で示されています。 `{DynamicResource}`テーマ自体はユーザーが変更できるため、をお勧めします。 テーマをサポートするために、コントロールの作成者の意図に最も近いコンポーネントリソースが必要な場合は、コンポーネントのリソース参照も動的にできるようにする必要があります。  
  
 は<xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A> 、リソースが実際に定義されているターゲットアセンブリに存在する型を識別します。 は、<xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>が定義されている場所を正確に把握することとは別に定義および使用できますが、最終的には参照されるアセンブリを使用して型を解決する必要があります。`ComponentResourceKey`  
  
 の<xref:System.Windows.ComponentResourceKey>一般的な使用方法は、クラスのメンバーとして公開されるキーを定義することです。 この使用法では、マーク<xref:System.Windows.ComponentResourceKey>アップ拡張機能ではなく、クラスコンストラクターを使用します。 詳細については<xref:System.Windows.ComponentResourceKey>、「[コントロールの作成の概要](../controls/control-authoring-overview.md)」の「」または「テーマリソースのキーの定義と参照」セクションを参照してください。  
  
 キーを確立し、キー付きリソースを参照する場合、通常、 `ComponentResourceKey`マークアップ拡張機能に対して属性構文が使用されます。  
  
 表示される compact 構文は、 <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType>マークアップ拡張機能のコンストラクターシグネチャと位置指定パラメーターの使用に依存します。 `targetTypeName` と`targetID`が指定されている順序は重要です。 Verbose 構文は、 <xref:System.Windows.ComponentResourceKey.%23ctor%2A?displayProperty=nameWithType>パラメーターなしのコンストラクターに依存し、オブジェクト要素の真の属性構文に似た方法で<xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>とを<xref:System.Windows.ComponentResourceKey.ResourceId%2A>設定します。 Verbose 構文では、プロパティが設定される順序は重要ではありません。 この2つの代替手段 (compact および verbose) の関係とメカニズムについては、「[マークアップ拡張機能と WPF XAML](markup-extensions-and-wpf-xaml.md)」で詳しく説明されています。  
  
 技術的には、の`targetID`値は任意のオブジェクトにすることができ、文字列である必要はありません。 ただし、WPF での最も一般的な使用方法は、 `targetID`値を文字列であるフォームに揃え、そのような文字列を[XamlName 文法](../../xaml-services/xamlname-grammar.md)で有効にすることです。  
  
 `ComponentResourceKey`オブジェクト要素構文で使用できます。 この場合、拡張機能を正しく初期化するに<xref:System.Windows.ComponentResourceKey.TypeInTargetAssembly%2A>は<xref:System.Windows.ComponentResourceKey.ResourceId%2A> 、プロパティとプロパティの両方の値を指定する必要があります。  
  
 リーダー実装では、このマークアップ<xref:System.Windows.ComponentResourceKey>拡張機能の処理はクラスによって定義されます。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 `ComponentResourceKey` はマークアップ拡張機能です。 一般にマークアップ拡張機能を実装するのは、属性値をリテラル値やハンドラー名以外にエスケープする要件が存在し、その要件の適用範囲がグローバルで、特定の型やプロパティに型コンバーターを適用するだけにとどまらない場合です。 のすべての[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]マークアップ拡張機能は、属性構文で {および} 文字を使用します。これ[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]は、マークアップ拡張機能が属性を処理する必要があることをプロセッサが認識する規則です。 詳細については、「[マークアップ拡張機能」および「WPF XAML](markup-extensions-and-wpf-xaml.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.ComponentResourceKey>
- <xref:System.Windows.Controls.ControlTemplate>
- [コントロールの作成の概要](../controls/control-authoring-overview.md)
- [XAML の概要 (WPF)](xaml-overview-wpf.md)
- [マークアップ拡張機能と WPF XAML](markup-extensions-and-wpf-xaml.md)
