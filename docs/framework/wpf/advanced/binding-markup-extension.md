---
title: バインドのマークアップ拡張機能
ms.date: 03/30/2017
f1_keywords:
- Binding
helpviewer_keywords:
- Binding markup extensions [WPF]
- XAML [WPF], Binding markup extension
ms.assetid: 83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63
ms.openlocfilehash: 6776c89db474668b3aed0e38a3e18359bf93399d
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991478"
---
# <a name="binding-markup-extension"></a>バインドのマークアップ拡張機能
プロパティ値をデータバインド値にして、中間式オブジェクトを作成し、実行時に要素とそのバインディングに適用されるデータコンテキストを解釈します。  
  
## <a name="binding-expression-usage"></a>バインディング式の使用法  
  
```xaml  
<object property="{Binding}" .../>  
-or-  
<object property="{Binding  bindProp1=value1[, bindPropN=valueN]*}" ...  
/>  
-or-  
<object property="{Binding path}" .../>  
-or  
<object property="{Binding path[, bindPropN=valueN]*}" .../>  
```  
  
## <a name="syntax-notes"></a>構文に関する注意事項  
 これらの構文`[]`では、 `*`とはリテラルではありません。 これらは、0個以上の*bindprop*`=`*値*のペアを使用`,`できることを示す表記の一部であり、これらのペアと前の*bindprop*`=`*値*のペアの間に区切り記号が付きます。  
  
 "バインディング拡張機能で設定できるバインディングプロパティ" セクションに示されているプロパティは、 <xref:System.Windows.Data.Binding>オブジェクト要素の属性を使用して設定できます。 ただし、これは実際にはのマークアップ拡張<xref:System.Windows.Data.Binding>機能の使用ではなく、CLR <xref:System.Windows.Data.Binding>クラスのプロパティを設定する属性の一般的な XAML 処理にすぎません。 つまり、 `<Binding` *bindProp1*`="`*value1* `"[` *bindPropN*`="`*の値*`"]*/>`の属性と等価の構文は、<xref:System.Windows.Data.Binding>オブジェクトの要素の使用方法の代わりに、`Binding`式の使用。 の<xref:System.Windows.Data.Binding>特定のプロパティの xaml 属性の使用方法については、.NET Framework クラスライブラリのの<xref:System.Windows.Data.Binding>関連プロパティの「xaml 属性の使用方法」セクションを参照してください。  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`bindProp1, bindPropN`|設定するプロパティ<xref:System.Windows.Data.Binding>または<xref:System.Windows.Data.BindingBase>プロパティの名前。 すべて<xref:System.Windows.Data.Binding>のプロパティを`Binding`拡張で設定することはできません。また、一部`Binding`のプロパティは、さらに入れ子になったマークアップ拡張機能を使用することによってのみ、式の中で設定できます。 「バインディング拡張機能で設定できるバインディングプロパティ」を参照してください。|  
|`value1, valueN`|プロパティに設定する値。 属性値の処理は、最終的には、設定される特定<xref:System.Windows.Data.Binding>のプロパティの型とロジックに固有です。|  
|`path`|暗黙的<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>なプロパティを設定するパス文字列。 「 [PROPERTYPATH XAML 構文](propertypath-xaml-syntax.md)」も参照してください。|  
  
## <a name="unqualified-binding"></a>修飾なし {Binding}  
 「バインディング式の使用」に示されている<xref:System.Windows.Data.Binding> <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> `null`使用法では、の初期値を含むオブジェクトが既定値で作成されます。 `{Binding}` これは、作成さ<xref:System.Windows.Data.Binding>れたがランタイムデータコンテキストで設定されているなど<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>のキーデータバインディング<xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType>プロパティに依存している可能性があるため、多くのシナリオで役立ちます。 データコンテキストの概念の詳細については、「[データバインディング](../data/data-binding-wpf.md)」を参照してください。  
  
## <a name="implicit-path"></a>暗黙的なパス  
 マーク`Binding`アップ拡張機能<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>は、"既定のプロパティ" の概念`Path=`としてを使用します。ここでは、を式に記述する必要はありません。 暗黙的`Binding`なパスを使用して式を指定する場合は、 <xref:System.Windows.Data.Binding>プロパティが name で指定されている他`bindProp`のペアの= `value`前に、暗黙的なパスを式の先頭に記述する必要があります。 たとえば`{Binding PathString}` <xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType> 、の<xref:System.Windows.Data.Binding>ようになります。は、マークアップ拡張機能の使用によって作成されたの値として評価される文字列です。`PathString` コンマ区切り記号の後に他の名前付きプロパティを含む暗黙のパスを追加`{Binding LastName, Mode=TwoWay}`できます。たとえば、のようになります。  
  
## <a name="binding-properties-that-can-be-set-with-the-binding-extension"></a>バインディング拡張機能を使用して設定できるバインディングプロパティ  
 このトピックで示す構文では、一般的`bindProp` <xref:System.Windows.Data.Binding> = `value`な近似値を使用します。これは、 `Binding`マーク<xref:System.Windows.Data.BindingBase>アップ拡張機能を使用して設定できるまたはの読み取り/書き込みプロパティが多数あるためです。式の構文。 暗黙的<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>なを除き、任意の順序で設定できます。 (を明示的に指定`Path=`することもできます。この場合、任意の順序で設定できます)。 基本的に、コンマで区切られたペアを使用して`bindProp` = `value` 、以下の一覧の0個以上のプロパティを設定できます。  
  
 これらのプロパティ値のいくつかには、XAML のテキスト構文からのネイティブな型変換をサポートしていないオブジェクト型が必要であり、属性値として設定するためにマークアップ拡張機能が必要です。 詳細については、各プロパティの .NET Framework クラスライブラリにある XAML 属性の使用方法に関するセクションを参照してください。XAML 属性構文に使用する文字列は、マークアップ拡張機能の使用を追加しない場合と基本的には、 `Binding`式で指定した値とほぼ同じです。ただし、それぞれ`bindProp` =に引用符を付けないでください。式内。 `value` `Binding`  
  
- <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>: 使用可能なバインドグループを識別する文字列。 これは、比較的高度なバインド概念です。のリファレンスページを<xref:System.Windows.Data.BindingBase.BindingGroupName%2A>参照してください。  
  
- <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A>:ブール値は、また`true`は`false`のいずれかになります。 既定値は `false` です。  
  
- <xref:System.Windows.Data.Binding.Converter%2A>: 式に`bindProp` `value`文字列として=設定できますが、そのためには、 [StaticResource マークアップ拡張機能](staticresource-markup-extension.md)など、値のオブジェクト参照が必要です。 この場合の値は、カスタムコンバータークラスのインスタンスです。  
  
- <xref:System.Windows.Data.Binding.ConverterCulture%2A>: 標準ベースの識別子として式で設定できます。の<xref:System.Windows.Data.Binding.ConverterCulture%2A>リファレンストピックを参照してください。  
  
- <xref:System.Windows.Data.Binding.ConverterParameter%2A>: 式の中で`bindProp` `value`文字列として設定できますが、これは渡されるパラメーターの型によって=異なります。 値の参照型を渡す場合、この使用法には、入れ子になった[StaticResource マークアップ拡張機能](staticresource-markup-extension.md)などのオブジェクト参照が必要です。  
  
- <xref:System.Windows.Data.Binding.ElementName%2A>: 相互排他的<xref:System.Windows.Data.Binding.RelativeSource%2A>また<xref:System.Windows.Data.Binding.Source%2A>はと。これらの各バインドプロパティは、特定のバインディング方法を表します。 「[データバインディングの概要](../data/data-binding-overview.md)」を参照してください。  
  
- <xref:System.Windows.Data.BindingBase.FallbackValue%2A>: 式の中で`bindProp` `value`文字列として=設定できますが、これは渡される値の型に依存します。 参照型を渡す場合、には、入れ子になった[StaticResource マークアップ拡張機能](staticresource-markup-extension.md)などのオブジェクト参照が必要です。  
  
- <xref:System.Windows.Data.Binding.IsAsync%2A>:ブール値は、また`true`は`false`のいずれかになります。 既定値は `false` です。  
  
- <xref:System.Windows.Data.Binding.Mode%2A>:*値*は、 <xref:System.Windows.Data.BindingMode>列挙体の定数名です。 たとえば、`{Binding Mode=OneWay}` のようにします。  
  
- <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A>:ブール値は、また`true`は`false`のいずれかになります。 既定値は `false` です。  
  
- <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A>:ブール値は、また`true`は`false`のいずれかになります。 既定値は `false` です。  
  
- <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A>:ブール値は、また`true`は`false`のいずれかになります。 既定値は `false` です。  
  
- <xref:System.Windows.Data.Binding.Path%2A>: データオブジェクトまたは一般的なオブジェクトモデルへのパスを記述する文字列。 この形式は、このトピックでは適切に記述できないオブジェクトモデルを走査するためのさまざまな規則を提供します。 「 [PROPERTYPATH XAML 構文](propertypath-xaml-syntax.md)」を参照してください。  
  
- <xref:System.Windows.Data.Binding.RelativeSource%2A>: とと<xref:System.Windows.Data.Binding.ElementName%2A> <xref:System.Windows.Data.Binding.Source%2A>の相互排他的な比較。これらの各バインドプロパティは、特定のバインディング方法を表します。 「[データバインディングの概要](../data/data-binding-overview.md)」を参照してください。 値を指定するには、入れ子になった[RelativeSource MarkupExtension](relativesource-markupextension.md)の使用が必要です。  
  
- <xref:System.Windows.Data.Binding.Source%2A>: 相互排他的<xref:System.Windows.Data.Binding.RelativeSource%2A>また<xref:System.Windows.Data.Binding.ElementName%2A>はと。これらの各バインドプロパティは、特定のバインディング方法を表します。 「[データバインディングの概要](../data/data-binding-overview.md)」を参照してください。 入れ子になった拡張機能の使用が必要です。通常は、キー付きリソースディクショナリからオブジェクトデータソースを参照する[StaticResource マークアップ拡張機能](staticresource-markup-extension.md)です。  
  
- <xref:System.Windows.Data.BindingBase.StringFormat%2A>: バインドされたデータの文字列形式規則を記述する文字列。 これは、比較的高度なバインド概念です。のリファレンスページを<xref:System.Windows.Data.BindingBase.StringFormat%2A>参照してください。  
  
- <xref:System.Windows.Data.BindingBase.TargetNullValue%2A>: 式の中で`bindProp` `value`文字列として設定できますが、これは渡されるパラメーターの型によって=異なります。 値の参照型を渡す場合、には、入れ子になった[StaticResource マークアップ拡張機能](staticresource-markup-extension.md)などのオブジェクト参照が必要です。  
  
- <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>:*値*は、 <xref:System.Windows.Data.UpdateSourceTrigger>列挙体の定数名です。 たとえば、`{Binding UpdateSourceTrigger=LostFocus}` のようにします。 特定のコントロールには、このバインディングプロパティの既定値が異なる可能性があります。 以下を参照してください。<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>  
  
- <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>:ブール値は、また`true`は`false`のいずれかになります。 既定値は `false` です。 「解説」を参照してください。  
  
- <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>:ブール値は、また`true`は`false`のいずれかになります。 既定値は `false` です。 「解説」を参照してください。  
  
- <xref:System.Windows.Data.Binding.XPath%2A>: XML データソースの XMLDOM へのパスを記述する文字列。 「 [XMLDataProvider と XPath クエリを使用して XML データにバインドする](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)」を参照してください。  
  
 マークアップ拡張機能/ <xref:System.Windows.Data.Binding> `{Binding}`式フォームを使用して設定できないのプロパティを次に示します。 `Binding`  
  
- <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>: このプロパティは、コールバックの実装への参照を必要とします。 イベントハンドラー以外のコールバック/メソッドは、XAML 構文で参照できません。  
  
- <xref:System.Windows.Data.Binding.ValidationRules%2A>: プロパティは、オブジェクトの<xref:System.Windows.Controls.ValidationRule>ジェネリックコレクションを受け取ります。 これは<xref:System.Windows.Data.Binding> object 要素の property 要素として表すことができますが、 `Binding`式で使用するための属性解析手法はすぐに使用できません。 のリファレンストピックを<xref:System.Windows.Data.Binding.ValidationRules%2A>参照してください。  
  
- <xref:System.Windows.Data.Binding.XmlNamespaceManager%2A>  
  
## <a name="remarks"></a>Remarks  
  
> [!IMPORTANT]
> 依存関係プロパティの優先順位に関し`Binding`ては、式はローカルに設定された値と同じです。 以前に式を`Binding`持っていたプロパティのローカル値を設定した場合`Binding` 、は完全に削除されます。 詳細については、「[依存関係プロパティ値の優先順位](dependency-property-value-precedence.md)」を参照してください。  
  
 基本レベルでのデータバインディングの記述については、このトピックでは説明しません。 「[データバインディングの概要](../data/data-binding-overview.md)」を参照してください。  
  
> [!NOTE]
> <xref:System.Windows.Data.MultiBinding>および<xref:System.Windows.Data.PriorityBinding>では、拡張[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]構文はサポートされていません。 代わりに、プロパティ要素を使用します。 <xref:System.Windows.Data.MultiBinding> および<xref:System.Windows.Data.PriorityBinding>のリファレンストピックを参照してください。  
  
 XAML のブール値では大文字と小文字が区別されません。 たとえば、または`{Binding NotifyOnValidationError=true}` `{Binding NotifyOnValidationError=True}`のいずれかを指定できます。  
  
 データの検証を伴うバインド`Binding`は、通常、 `{Binding ...}`式としてではなく明示的な要素<xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>によって指定され、式でまたはを設定<xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>することは珍しくありません。 これは、"コンパニオン" <xref:System.Windows.Data.Binding.ValidationRules%2A>プロパティを式の形式で簡単に設定できないためです。 詳細については、「[バインディングの検証の実装](../data/how-to-implement-binding-validation.md)」を参照してください。  
  
 `Binding` はマークアップ拡張機能です。 マークアップ拡張機能は、通常、属性値をリテラル値またはハンドラー名以外にエスケープする必要があり、その要件が特定の型またはプロパティに属性が設定された型コンバーターよりもグローバルである場合に実装されます。 Xaml のすべてのマークアップ拡張`{`機能`}`は、属性構文でおよび文字を使用します。これは、マークアップ拡張機能が文字列の内容を処理する必要があることを xaml プロセッサが認識する規則です。 詳細については、「[マークアップ拡張機能」および「WPF XAML](markup-extensions-and-wpf-xaml.md)」を参照してください。  
  
 `Binding`は、WPF の xaml 実装の拡張<xref:System.Windows.Data.Binding>機能を実装するクラスが xaml に関連しない他のいくつかのメソッドとプロパティも実装することを示す、例外的なマークアップ拡張機能です。 他のメンバーは、XAML マーク<xref:System.Windows.Data.Binding>アップ拡張機能として機能するだけでなく、多くのデータバインディングシナリオに対応できる、より汎用性のある自己完結型クラスを作成することを目的としています。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Data.Binding>
- [データ バインディングの概要](../data/data-binding-overview.md)
- [XAML の概要 (WPF)](xaml-overview-wpf.md)
- [マークアップ拡張機能と WPF XAML](markup-extensions-and-wpf-xaml.md)
