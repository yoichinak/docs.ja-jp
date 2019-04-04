---
title: バインドのマークアップ拡張機能
ms.date: 03/30/2017
f1_keywords:
- Binding
helpviewer_keywords:
- Binding markup extensions [WPF]
- XAML [WPF], Binding markup extension
ms.assetid: 83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63
ms.openlocfilehash: 960bc953345e3f6ed632b7a136b626978c8a9bce
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57379186"
---
# <a name="binding-markup-extension"></a>バインドのマークアップ拡張機能
プロパティの値を中間式オブジェクトを作成して、要素とそのバインディングを実行時に適用されるデータ コンテキストを解釈する、データ バインドされた値を延期します。  
  
## <a name="binding-expression-usage"></a>バインディング式の使用方法  
  
```  
<object property="{Binding}" .../>  
-or-  
<object property="{Binding  bindProp1=value1[, bindPropN=valueN]*}" ...  
/>  
-or-  
<object property="{Binding path}" .../>  
-or  
<object property="{Binding path[, bindPropN=valueN]*}" .../>  
```  
  
## <a name="syntax-notes"></a>構文のメモ  
 これらの構文を使って、`[]`と`*`リテラルではありません。 いることを示す表記の一部である 0 個以上*含む*`=`*値*のペアを使用できますで、`,`前および間の区切り記号*含む* `=`*値*ペア。  
  
 「バインド プロパティことでく設定で、バインド拡張機能」セクションに示したプロパティのいずれかの代わりに設定できるの属性を使用して、<xref:System.Windows.Data.Binding>オブジェクト要素。 ただし、外にある真のマークアップ拡張機能の使用<xref:System.Windows.Data.Binding>、一般的な CLR のプロパティを設定する属性の XAML 処理だけが<xref:System.Windows.Data.Binding>クラス。 つまり、 `<Binding` *bindProp1*`="`*value1* `"[` *bindPropN*`="`*の値*`"]*/>`の属性と等価の構文は、<xref:System.Windows.Data.Binding>オブジェクトの要素の使用方法の代わりに、`Binding`式の使用。 XAML 属性の使用方法の特定のプロパティの詳細については<xref:System.Windows.Data.Binding>の関連するプロパティの「XAML 属性使用量」セクションを参照して<xref:System.Windows.Data.Binding>.NET Framework クラス ライブラリ。  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`bindProp1, bindPropN`|名前、<xref:System.Windows.Data.Binding>または<xref:System.Windows.Data.BindingBase>プロパティを設定します。 すべて<xref:System.Windows.Data.Binding>でプロパティを設定することができます、`Binding`拡張機能、およびいくつかのプロパティは内で設定可能な`Binding`マークアップ拡張機能がさらを使用してのみ式に入れ子になった。 「バインド プロパティことでく設定で、バインド拡張機能」セクションをご覧ください。|  
|`value1, valueN`|プロパティを設定する値。 属性の値の処理は最終的には、型と、特定のロジックに固有<xref:System.Windows.Data.Binding>プロパティが設定されています。|  
|`path`|暗黙を設定するパス文字列<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>プロパティ。 参照してください[PropertyPath の XAML 構文](propertypath-xaml-syntax.md)します。|  
  
## <a name="unqualified-binding"></a>修飾されていない {binding}  
 `{Binding}` 「バインド式の使用」で示した使用法を作成、<xref:System.Windows.Data.Binding>を含む初期既定値を持つオブジェクト<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>の`null`します。 これは、多くのシナリオにも便利ですので、作成した<xref:System.Windows.Data.Binding>など主要なデータ バインド プロパティに依存する可能性があります<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>と<xref:System.Windows.Data.Binding.Source%2A?displayProperty=nameWithType>実行時のデータ コンテキストで設定されています。 データ コンテキストの概念の詳細については、[データ バインディングの](../data/data-binding-wpf.md)を参照してください。  
  
## <a name="implicit-path"></a>暗黙のパス  
 `Binding`マークアップ拡張機能の使用<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>を概念として"プロパティを default"という`Path=`式に表示する必要はありません。 指定した場合、`Binding`暗黙的なパスを持つ式は、暗黙的なパスを前に、他の式で最初に表示する必要があります`bindProp` = `value`ペアで、<xref:System.Windows.Data.Binding>プロパティは名前によって指定します。 例:`{Binding PathString}`ここで、`PathString`の値に評価される文字列は、<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>で、<xref:System.Windows.Data.Binding>マークアップ拡張機能を使用して作成します。 たとえば、コンマ区切り記号の後に他の名前付きプロパティを持つ暗黙のパスを追加できます`{Binding LastName, Mode=TwoWay}`します。  
  
## <a name="binding-properties-that-can-be-set-with-the-binding-extension"></a>バインドのバインド拡張機能で設定できるプロパティ  
 このトピックで示す構文は、ジェネリックを使用して`bindProp` = `value` approximation の多くの読み取り/書き込みプロパティがあるため、<xref:System.Windows.Data.BindingBase>または<xref:System.Windows.Data.Binding>を設定できる、`Binding`マークアップ拡張機能/式の構文。 暗黙的なを除き、任意の順序で設定できる<xref:System.Windows.Data.Binding.Path%2A?displayProperty=nameWithType>します。 (明示的に指定するオプションが`Path=`、任意の順序で設定する場合)。 基本的で設定できるプロパティの 0 個以上、以下の一覧を使用して`bindProp` = `value`ペアはコンマで区切られました。  
  
 これらのプロパティ値のいくつかは、オブジェクトの種類で、XAML テキスト構文からのネイティブな型変換をサポートしていないため、属性値として設定するためにマークアップ拡張機能を必要する必要があります。 詳細については、各プロパティの .NET Framework クラス ライブラリの XAML 属性の使用方法に関するセクションを確認します。XAML 属性の構文を使用する文字列またはマークアップ拡張機能をさらにせず使用量は基本的で指定した値と同じ、`Binding`式でそれぞれを囲む引用符を配置しないで例外`bindProp` =`value`で、`Binding`式。  
  
-   <xref:System.Windows.Data.BindingBase.BindingGroupName%2A>: バインドできるグループを識別する文字列。 これは、比較的高度なバインドの概念です。リファレンス ページを参照してください。<xref:System.Windows.Data.BindingBase.BindingGroupName%2A>します。  
  
-   <xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A>:ブール値、いずれかになります`true`または`false`します。 既定値は `false` です。  
  
-   <xref:System.Windows.Data.Binding.Converter%2A>: として設定できる、 `bindProp` = `value`文字列式では、これを行うに参照が必要です、オブジェクトの値として、などを[StaticResource マークアップ拡張機能](staticresource-markup-extension.md)します。 ここで、値は、カスタムのコンバーター クラスのインスタンスです。  
  
-   <xref:System.Windows.Data.Binding.ConverterCulture%2A>: 標準ベースの識別子としての式で設定可能リファレンス トピックを参照してください。<xref:System.Windows.Data.Binding.ConverterCulture%2A>します。  
  
-   <xref:System.Windows.Data.Binding.ConverterParameter%2A>: として設定できる、 `bindProp` = `value` 、式がこの文字列が渡されるパラメーターの型に依存します。 この使用量が、入れ子になったなどのオブジェクト参照を必要と値の参照型を渡す場合[StaticResource マークアップ拡張機能](staticresource-markup-extension.md)します。  
  
-   <xref:System.Windows.Data.Binding.ElementName%2A>: と相互に排他的な<xref:System.Windows.Data.Binding.RelativeSource%2A>と<xref:System.Windows.Data.Binding.Source%2A>; 各これらのプロパティをバインドする特定のバインド方法を表します。 参照してください[データ バインディングの概要](../data/data-binding-overview.md)します。  
  
-   <xref:System.Windows.Data.BindingBase.FallbackValue%2A>: として設定できる、 `bindProp` = `value` 、式がこの文字列が渡された値の型に依存します。 入れ子になったなどのオブジェクト参照の参照型を渡すことが必要な場合[StaticResource マークアップ拡張機能](staticresource-markup-extension.md)します。  
  
-   <xref:System.Windows.Data.Binding.IsAsync%2A>:ブール値、いずれかになります`true`または`false`します。 既定値は `false` です。  
  
-   <xref:System.Windows.Data.Binding.Mode%2A>:*値*の定数名は、<xref:System.Windows.Data.BindingMode>列挙体。 たとえば、`{Binding Mode=OneWay}` のようにします。  
  
-   <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A>:ブール値、いずれかになります`true`または`false`します。 既定値は `false` です。  
  
-   <xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A>:ブール値、いずれかになります`true`または`false`します。 既定値は `false` です。  
  
-   <xref:System.Windows.Data.Binding.NotifyOnValidationError%2A>:ブール値、いずれかになります`true`または`false`します。 既定値は `false` です。  
  
-   <xref:System.Windows.Data.Binding.Path%2A>: データ オブジェクト、または一般的なオブジェクト モデルへのパスを記述する文字列。 形式は、このトピックでは適切に記述できないオブジェクト モデルの走査のいくつかの異なる規則を提供します。 参照してください[PropertyPath の XAML 構文](propertypath-xaml-syntax.md)します。  
  
-   <xref:System.Windows.Data.Binding.RelativeSource%2A>: ではなく相互に排他的<xref:System.Windows.Data.Binding.ElementName%2A>と<xref:System.Windows.Data.Binding.Source%2A>; 各これらのプロパティをバインドする特定のバインド方法を表します。 参照してください[データ バインディングの概要](../data/data-binding-overview.md)します。 入れ子になった必要があります[RelativeSource のマークアップ拡張機能](relativesource-markupextension.md)使用状況の値を指定します。  
  
-   <xref:System.Windows.Data.Binding.Source%2A>: と相互に排他的な<xref:System.Windows.Data.Binding.RelativeSource%2A>と<xref:System.Windows.Data.Binding.ElementName%2A>; 各これらのプロパティをバインドする特定のバインド方法を表します。 参照してください[データ バインディングの概要](../data/data-binding-overview.md)します。 通常、入れ子になった拡張機能の使用が必要です、 [StaticResource マークアップ拡張機能](staticresource-markup-extension.md)キーを持つリソース ディクショナリからオブジェクト データ ソースを参照します。  
  
-   <xref:System.Windows.Data.BindingBase.StringFormat%2A>: バインドされたデータの文字列形式の表記法を説明する文字列。 これは、比較的高度なバインドの概念です。リファレンス ページを参照してください。<xref:System.Windows.Data.BindingBase.StringFormat%2A>します。  
  
-   <xref:System.Windows.Data.BindingBase.TargetNullValue%2A>: として設定できる、 `bindProp` = `value` 、式がこの文字列が渡されるパラメーターの型に依存します。 入れ子になったなどのオブジェクト参照の値として、参照型を渡すことが必要な場合[StaticResource マークアップ拡張機能](staticresource-markup-extension.md)します。  
  
-   <xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>:*値*の定数名は、<xref:System.Windows.Data.UpdateSourceTrigger>列挙体。 たとえば、`{Binding UpdateSourceTrigger=LostFocus}` のようにします。 特定のコントロールには、このバインドのプロパティの既定値がある可能性があります。 以下を参照してください。<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A>  
  
-   <xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>:ブール値、いずれかになります`true`または`false`します。 既定値は `false` です。 「解説」を参照してください。  
  
-   <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>:ブール値、いずれかになります`true`または`false`します。 既定値は `false` です。 「解説」を参照してください。  
  
-   <xref:System.Windows.Data.Binding.XPath%2A>: XML データ ソースの XMLDOM にパスを説明する文字列。 参照してください[XMLDataProvider と XPath クエリを使用して XML データにバインド](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)します。  
  
 プロパティを次に<xref:System.Windows.Data.Binding>を使用して設定することはできません、`Binding`マークアップ拡張機能/`{Binding}`式のフォームです。  
  
-   <xref:System.Windows.Data.Binding.UpdateSourceExceptionFilter%2A>: このプロパティがコールバック実装への参照が必要です。 イベント ハンドラー以外のコールバック/メソッドは、XAML 構文では参照できません。  
  
-   <xref:System.Windows.Data.Binding.ValidationRules%2A>: プロパティのジェネリック コレクションを受け取る<xref:System.Windows.Controls.ValidationRule>オブジェクト。 プロパティ要素として表現できるこの、<xref:System.Windows.Data.Binding>要素、オブジェクトしますが、すぐに使用できる属性の解析の手法での使用を持たない、`Binding`式。 リファレンス トピックを参照してください。<xref:System.Windows.Data.Binding.ValidationRules%2A>します。  
  
-   <xref:System.Windows.Data.Binding.XmlNamespaceManager%2A>  
  
## <a name="remarks"></a>Remarks  
  
> [!IMPORTANT]
>  依存関係プロパティの優先順位の観点から、`Binding`式がローカルに設定したのと同じ値です。 以前に使用できるプロパティのローカル値を設定するかどうか、`Binding`式、`Binding`が完全に削除します。 詳細については、「[依存関係プロパティ値の優先順位](dependency-property-value-precedence.md)」を参照してください。  
  
 基本的なレベルでのデータ バインディングについては、このトピックでは説明しません。 参照してください[データ バインディングの概要](../data/data-binding-overview.md)します。  
  
> [!NOTE]
>  <xref:System.Windows.Data.MultiBinding> <xref:System.Windows.Data.PriorityBinding>をサポートしていない、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]拡張構文。 代わりに、プロパティ要素を使用します。 参照トピックを参照してください。<xref:System.Windows.Data.MultiBinding>と<xref:System.Windows.Data.PriorityBinding>します。  
  
 XAML のブール値は大文字小文字を区別します。 たとえばいずれかを指定できます`{Binding NotifyOnValidationError=true}`または`{Binding NotifyOnValidationError=True}`します。  
  
 データの検証に関連するバインドは、通常、明示的な指定`Binding`要素ではなくとして、`{Binding ...}`式、および設定<xref:System.Windows.Data.Binding.ValidatesOnDataErrors%2A>または<xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>式ではあまりありません。 これは、ため、コンパニオン プロパティ<xref:System.Windows.Data.Binding.ValidationRules%2A>式の形式で簡単に設定することはできません。 詳細については、[実装バインド検証](../data/how-to-implement-binding-validation.md)を参照してください。  
  
 `Binding` はマークアップ拡張機能です。 通常、マークアップ拡張機能は、属性値の名前、リテラル値やハンドラー以外にエスケープする必要があるし、要件が特定の種類またはプロパティで属性付きの型コンバーターよりも多くのグローバルに実装されます。 XAML の使用中のすべてのマークアップ拡張機能、`{`と`}`マークアップ拡張機能が文字列の内容を処理する必要がありますを XAML プロセッサが認識する規則は、それぞれの属性構文内の文字。 詳細については、[マークアップ拡張機能と WPF XAML](markup-extensions-and-wpf-xaml.md)を参照してください。  
  
 `Binding` 特殊なマークアップ拡張機能は、 <xref:System.Windows.Data.Binding> WPF の XAML 実装の拡張機能を実装するクラスは、その他のいくつかのメソッドと XAML に関連していないプロパティにも実装します。 他のメンバーにするは<xref:System.Windows.Data.Binding>汎用性と自己完結型のクラスで、XAML マークアップ拡張機能として機能しているだけでなく多くのデータ バインディングのシナリオに対処できます。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Data.Binding>
- [データ バインディングの概要](../data/data-binding-overview.md)
- [XAML の概要 (WPF)](xaml-overview-wpf.md)
- [マークアップ拡張機能と WPF XAML](markup-extensions-and-wpf-xaml.md)
