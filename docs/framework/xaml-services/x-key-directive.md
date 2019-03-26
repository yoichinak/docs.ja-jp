---
title: x:Key ディレクティブ
ms.date: 03/30/2017
f1_keywords:
- xKey
- Key
- x:Key
helpviewer_keywords:
- x:Key attribute [XAML Services]
- Key attribute in XAML [XAML Services]
- XAML [XAML Services], x:Key attribute
ms.assetid: 1985cd45-f197-42d5-b75e-886add64b248
ms.openlocfilehash: 8474fd5ee6f9f6e6dccda5fb57fbed9ddd787c26
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2019
ms.locfileid: "58046209"
---
# <a name="xkey-directive"></a>x:Key ディレクティブ
XAML で定義されたディクショナリで作成および参照される要素を一意に識別します。 
  `x:Key` 値を XAML オブジェクトに追加するのは、リソース ディクショナリ (<xref:System.Windows.ResourceDictionary> など) のリソースを識別するための最も一般的な方法です。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```  
<object x:Key="stringKeyValue".../>  
-or-  
<object x:Key="{markupExtensionUsage}".../>  
```  
  
## <a name="xaml-attribute-usage-wpf-specific"></a>XAML 属性の使用方法 (WPF 固有)  
  
```  
<object.Resources>  
  <object x:Key="stringKeyValue".../>  
</object.Resources>  
-or-  
<object.Resources>  
  <object x:Key="{markupExtensionUsage}".../>  
</object.Resources>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`stringKeyValue`|キーとして使用するテキスト文字列。 テキスト文字列に準拠する必要があります、 [XamlName の文法](xamlname-grammar.md)します。|  
|`markupExtensionUsage`|マークアップ拡張機能の区切り記号内{}、マークアップ拡張機能の使用をキーとして使用するオブジェクトを提供します。 「解説」を参照してください。|  
  
## <a name="remarks"></a>Remarks  
 `x:Key` は XAML のリソース ディクショナリの概念をサポートしています。 言語としての XAML ではリソース ディクショナリの実装は定義されていません。特定の UI フレーム ワークによって定義されています。 WPF における XAML リソース ディクショナリを実装する方法の詳細については、[XAML リソース](../wpf/advanced/xaml-resources.md)を参照してください。  
  
 XAML 2006 および WPF では、`x:Key`属性として指定する必要があります。 文字列ではないキーも使用できますが、文字列ではない値を属性形式で提供するためには、マークアップ拡張機能を使用する必要があります。 XAML 2009 を使用している場合`x:Key`以外のオブジェクトの種類をキーとするディクショナリを明示的にサポートするために文字列の中間マークアップ拡張機能を必要とせずを要素として指定できます。 このトピックの「XAML 2009」のセクションを参照してください。 XAML 2006 の実装に具体的には、「解説」セクションの残りの部分が適用されます。  
  
 属性値`x:Key`任意の文字列で定義できる、 [XamlName の文法](xamlname-grammar.md)またはマークアップ拡張機能を使用して評価されたオブジェクトを指定できます。 WPF の例については、「WPF の使用上の注意」を参照してください。  
  
 通常、<xref:System.Collections.IDictionary> の実装である親要素の子要素には、そのディクショナリ内の一意のキー値を指定する `x:Key` 属性を含める必要があります。 フレームワークでは、特定の型の `x:Key` を代用するために、エイリアス化されたキー プロパティを実装する場合があります。このようなプロパティを定義する型には、<xref:System.Windows.Markup.DictionaryKeyPropertyAttribute> 属性を設定する必要があります。  
  
 
  `x:Key` の指定に相当するコードは、基になる <xref:System.Collections.IDictionary> で使用されるキーです。 たとえば、マークアップで適用される WPF のリソースの `x:Key` は、コードでリソースを WPF の `key` に追加する場合、<xref:System.Windows.ResourceDictionary.Add%2A?displayProperty=nameWithType> の <xref:System.Windows.ResourceDictionary> パラメーターの値と同等です。  
  
## <a name="wpf-usage-notes"></a>WPF の使用上の注意  
 通常、WPF の <xref:System.Collections.IDictionary> などの <xref:System.Windows.ResourceDictionary> の実装である親オブジェクトの子オブジェクトには、`x:Key` 属性を含める必要があります。また、キー値は、そのディクショナリ内で一意である必要があります。 ただし、次のように 2 つの重要な例外があります。  
  
-   一部の WPF 型は、ディクショナリの使用に対して暗黙のキーを宣言します。 たとえば、<xref:System.Windows.Style> が設定された <xref:System.Windows.Style.TargetType%2A> や、<xref:System.Windows.DataTemplate> が設定された <xref:System.Windows.DataTemplate.DataType%2A> は、<xref:System.Windows.ResourceDictionary> に格納して、暗黙のキーを使用できます。  
  
-   WPF は、マージされたリソース ディクショナリの概念をサポートしています。 キーは、マージされたディクショナリ間で共有できます。また、共有されたキーの動作には、<xref:System.Windows.FrameworkContentElement.FindResource%2A> を使用してアクセスできます。 詳細については、「[Merged Resource Dictionaries](../wpf/advanced/merged-resource-dictionaries.md)」を参照してください。  
  
 通常、WPF XAML の実装およびアプリケーション モデルでは、キーの一意性が XAML マークアップ コンパイラによってチェックされることはありません。 その代わり、`x:Key` 値が指定されていない場合や一意でない場合は、読み込み時に XAML パーサー エラーが発生します。 ただし、WPF のディクショナリの処理を Visual Studio できます多くの場合、このようなエラー、設計フェーズで。  
  
 ここに示す構文において、<xref:System.Windows.ResourceDictionary> オブジェクトは WPF XAML プロセッサが <xref:System.Windows.FrameworkElement.Resources%2A> コレクションを取得するためのコレクションを生成する方法を暗黙的に決定することに注意してください。 
  <xref:System.Windows.ResourceDictionary> は、通常はマークアップで要素として明示的に指定されませんが、わかりやすくするために必要に応じて明示的に指定することもできます (その場合、このオブジェクトは、<xref:System.Windows.FrameworkElement.Resources%2A> プロパティ要素とディクショナリに設定される項目間のコレクション オブジェクト要素になります)。 なぜコレクション オブジェクトがほぼ常に暗黙の要素にマークアップの詳細については、[XAML 構文の詳細](../wpf/advanced/xaml-syntax-in-detail.md)を参照してください。  
  
 WPF XAML 実装では、リソース ディクショナリ キーの処理は、<xref:System.Windows.ResourceKey> 抽象クラスによって定義されます。 ただし、WPF XAML プロセッサは、使用方法に基づいてキーごとに別の基になる拡張型を生成します。 たとえば、<xref:System.Windows.DataTemplate> または任意の派生クラスのキーは個別に処理され、異なる <xref:System.Windows.DataTemplateKey> オブジェクトを生成します。  
  
 基本的な XAML 定義では、キーと名前で異なるディレクティブと言語要素 (`x:Key` と `x:Name`) が使用されます。 また、キーと名前は、それらの概念の WPF 定義およびアプリケーションにより異なる状況において使用されます。 詳細については、[WPF XAML 名前スコープ](../wpf/advanced/wpf-xaml-namescopes.md)を参照してください。  
  
 既に説明したように、キー値はマークアップ拡張機能によって指定され、文字列値以外になる場合があります。 WPF シナリオの例は、の値を提供する`x:Key`可能性があります、 [ComponentResourceKey](../wpf/advanced/componentresourcekey-markup-extension.md)します。 特定のコントロールでは、スタイルを完全に置き換えることなく、そのコントロールの外観と動作の一部に影響を与えるカスタム スタイル リソースの型に対応するスタイル キーが公開されます。 このようなキーの例として、<xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A> が挙げられます。  
  
 WPF のマージされたディクショナリ機能では、キーの一意性およびキーの検索動作について考慮を要する点があります。 詳細については、「[Merged Resource Dictionaries](../wpf/advanced/merged-resource-dictionaries.md)」を参照してください。  
  
## <a name="xaml-2009"></a>XAML 2009  
 XAML 2009 は、制限を緩和する`x:Key`属性形式で常に提供されます。  
  
 WPF では、マークアップ コンパイルされていない XAML については、XAML 2009 の機能を使用することができます。 WPF 向けにマークアップ コンパイルされた XAML、および XAML の BAML 形式は、現在、XAML 2009 のキーワードと機能をサポートしていません。  
  
 XAML 2009 で指定できます`x:Key`次の使用法を使用して要素。  
  
### <a name="xaml-element-usage-xaml-2009-only"></a>XAML 要素の使用 (XAML 2009 のみ)  
  
```  
<object>  
  <x:Key>  
keyObject  
  </x:Key>  
...  
</object>  
```  
  
### <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`keyObject`|専用のディクショナリで指定された `object` のキーとして使用されるオブジェクトの、オブジェクト要素。|  
  
-   この種類の使用方法のコンテナー/親は、ここには示しません。 `object` は、専用のディクショナリの実装を表すオブジェクト要素の子であると想定されます。 `keyObject` は、その専用のディクショナリの実装のキーとして適切なオブジェクト インスタンス (または値の型の値) であると想定されます。  
  
-   WPF は、この使用方法を必要とするディクショナリを実装しません。 オブジェクト キーは XAML 言語のより一般的な機能であり、カスタム ディクショナリのシナリオで XAML でのディクショナリ作成が望まれる場合に有益であることがあります。 リソースに対して文字列以外のキーを使用する暗黙的なスタイルなどの WPF 機能については、別の方法によってキーを確立、または指定することができるので、オブジェクト キーを使用する必要はありません。  
  
-   *keyObject*直接オブジェクト インスタンスではなく、オブジェクト要素の形式でマークアップ拡張機能の使用可能性があります。  
  
## <a name="silverlight-usage-notes"></a>Silverlight の使用上の注意  
 Silverlight 用の `x:Key` に関しては、別途ドキュメントが用意されています。 詳細については、次を参照してください[XAML Namespace (x:)。言語機能 (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=199081)します。  
  
## <a name="see-also"></a>関連項目
- [XAML リソース](../wpf/advanced/xaml-resources.md)
- [リソースとコード](../wpf/advanced/resources-and-code.md)
- [StaticResource のマークアップ拡張機能](../wpf/advanced/staticresource-markup-extension.md)
