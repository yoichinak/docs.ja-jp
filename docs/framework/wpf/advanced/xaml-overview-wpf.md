---
title: XAML の概要 (WPF)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- user interfaces [XAML]
- classes [XAML]
- root element [XAML]
- XAML [WPF], about XAML
- base classes [XAML]
- routed events [WPF]
- code-behind files [WPF], XAML
- collection properties [XAML]
- events [XAML]
- property element [XAML]
- content models [XAML]
- Extensible Application Markup Language (see XAML)
- attribute syntax [XAML]
ms.assetid: a80db4cd-dd0f-479f-a45f-3740017c22e4
ms.openlocfilehash: 56b97170884ef31004b06b0eb50a8d79ad1d041c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102831"
---
# <a name="xaml-overview-wpf"></a>XAML の概要 (WPF)
このトピックでは、XAML 言語の機能について説明し、記述する XAML を使用する方法を示して[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]アプリケーション。 このトピックでは XAML を具体的には説明によって実装される[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]します。 XAML 自体よりも大きく、言語の概念は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]します。  

<a name="what_is_xaml"></a>   
## <a name="what-is-xaml"></a>XAML とは何ですか。  
 XAML は、宣言型マークアップ言語です。 .NET Framework のプログラミング モデルに適用される、XAML が作成を簡素化、 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] .NET Framework アプリケーション用。 表示を作成する[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]宣言型の XAML マークアップでと、別の要素、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]部分クラス定義を通じてマークアップに参加している、分離コード ファイルを使用して、実行時のロジックを定義します。 XAML は、直接バッキング アセンブリで定義されている型の特定のセット内のオブジェクトのインスタンス化を表します。 これは、ほとんどのマークアップ言語は、バッキング型システムに直接結合せずインタープリター言語では通常とは異なりします。 XAML により、別のパーティが取り組むことができます、ワークフロー、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]と異なる可能性のあるツールを使用して、アプリケーションのロジック。  
  
 テキストとして表され、XAML ファイルがある一般的に XML ファイル、`.xaml`拡張機能。 ファイルは、任意の XML エンコードしますが、utf-8 は一般的なエンコードでエンコードできます。  
  
 次の例は、ボタンの一部として作成する方法を示しています、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]します。 この例の目的は XAML の一般的な表示方法のフレーバーを指定するだけ[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]プログラミング メタファ (でない完全なサンプル)。  
  
 [!code-xaml[XAMLOvwSupport#DirtSimple](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]  
  
<a name="xaml_syntax_in_brief"></a>   
## <a name="xaml-syntax-in-brief"></a>XAML 構文の概要  
 次のセクションでは、XAML 構文の基本的な形式を説明し、短いマークアップの例を提供します。 これらのセクションは、これらバッキング型システムでの表現方法など、それぞれの構文形式の完全な情報を提供するものはありません。 このトピックで導入された構文の各の XAML 構文の仕様の詳細については、次を参照してください。 [XAML 構文の詳細](xaml-syntax-in-detail.md)します。  
  
 次のセクションでは、いくつかの内容の大半は、XML 言語に精通していれば、基本になります。 これは、XAML の基本的な設計原則の 1 つの結果です。  XAML 言語には、独自の概念が定義されていますが、これらの概念が XML 言語とマークアップ フォーム内で機能します。  
  
### <a name="xaml-object-elements"></a>XAML オブジェクト要素  
 オブジェクトの要素は、通常、型のインスタンスを宣言します。 その型は、言語として XAML を使用しているテクノロジの場合、バッキング型を提供するアセンブリで定義されます。  
  
 オブジェクト要素構文は、常に角かっこで始まります (\<)。 これは、後が型の名前でインスタンスを作成します。 (名前は、プレフィックス、後で説明した概念を含めることができます可能性があります)。その後、オブジェクト要素の属性をオプションで宣言できます。 オブジェクトの要素を完了するには、終わりの山かっこ (>) で終了します。 代わりにスラッシュでタグを完了し、終わり山かっこを連続して、任意のコンテンツを含まない自己終了のフォームを使用することができます (/>)。 たとえば、先ほどのマークアップ スニペットは、もう一度見てください。  
  
 [!code-xaml[XAMLOvwSupport#DirtSimple](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]  
  
 2 つのオブジェクトの要素を指定します: `<StackPanel>` (コンテンツ、および終了タグを後で) 使用し、 `<Button .../>` (自己終了フォーム、いくつかの属性を持つ)。 オブジェクト要素`StackPanel`と`Button`で定義されているクラスの名前には、各マップ[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]の一部となって、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アセンブリ。 オブジェクト要素タグを指定する場合は、XAML の新しいインスタンスを作成する処理の命令を作成します。 各インスタンスは、解析、XAML の読み込みのときに、基になる型の既定のコンス トラクターを呼び出すことによって作成されます。  
  
### <a name="attribute-syntax-properties"></a>属性の構文 (プロパティ)  
 オブジェクトのプロパティは、オブジェクト要素の属性として多くの場合、表現できます。 属性構文では、代入演算子 (=) の後に、属性構文で設定されるプロパティを名します。 属性の値は常に、引用符内に含まれる文字列として指定します。  
  
 属性構文では、最も効率の高いプロパティ設定の構文し、過去のマークアップ言語を使用していた開発者向けの使用を最も直感的な構文です。 たとえば、次のマークアップは赤いテキストと表示のテキストとして指定だけでなく、青色の背景を持つボタンを作成します。`Content`します。  
  
 [!code-xaml[XAMLOvwSupport#BlueRedButton](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbutton)]  
  
### <a name="property-element-syntax"></a>プロパティ要素構文  
 オブジェクト要素の一部のプロパティのオブジェクトやプロパティ値を提供するために必要な情報を引用符と属性構文の文字列の制限内で適切に表現できないため、属性構文は可能であれば、ありません。 このような場合は、プロパティ要素構文と呼ばれる別の構文を使用していることができます。  
  
 プロパティ要素の開始タグの構文は、 `<` *typeName*`.`*propertyName*`>`します。 一般に、そのタグの内容は、プロパティの値として受け取る型のオブジェクト要素です。 コンテンツを指定した後は、終了タグを持つプロパティ要素を閉じる必要があります。 終了タグの構文は、 `</` *typeName*`.`*propertyName*`>`します。  
  
 属性の構文が可能な場合は、属性構文を使用して通常方が便利ですよりコンパクトなマークアップしますが、多くの場合、スタイル、技術的な制限ではないだけで済みます。 次の例では、同じプロパティのすべてのプロパティのプロパティ要素構文を使用してこの時間が前の属性構文の例のように設定されている、`Button`します。  
  
 [!code-xaml[XAMLOvwSupport#BlueRedButtonPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbuttonpe)]  
  
### <a name="collection-syntax"></a>コレクションの構文  
 XAML 言語には、人間が読みやすいマークアップを生成するいくつかの最適化が含まれています。 このような 1 つの最適化をされていると、特定のプロパティはコレクション型では、その項目コレクションのプロパティの値になる一部内の子要素としてのマークアップで宣言する場合。 ここで子オブジェクトの要素のコレクションは、コレクション プロパティに設定されている値です。  
  
 次の例の値の設定のコレクション構文を示しています、<xref:System.Windows.Media.GradientBrush.GradientStops%2A>プロパティ。  
  
```xaml  
<LinearGradientBrush>  
  <LinearGradientBrush.GradientStops>  
    <!-- no explicit new GradientStopCollection, parser knows how to find or create -->  
    <GradientStop Offset="0.0" Color="Red" />  
    <GradientStop Offset="1.0" Color="Blue" />  
  </LinearGradientBrush.GradientStops>  
</LinearGradientBrush>  
```  
  
### <a name="xaml-content-properties"></a>XAML コンテンツのプロパティ  
 XAML では、クラスが指定のプロパティを XAML コンテンツ プロパティの 1 つだけという言語機能を指定します。 そのオブジェクトの要素の子要素は、そのコンテンツのプロパティの値の設定に使用されます。 つまり、コンテンツのプロパティの一意に XAML マークアップでそのプロパティを設定すると、プロパティ要素を省略できよりわかりやすい親/子のメタファをマークアップを生成できます。  
  
 たとえば、<xref:System.Windows.Controls.Border>の content プロパティを指定します<xref:System.Windows.Controls.Decorator.Child%2A>します。 次の 2 つ<xref:System.Windows.Controls.Border>要素は同一に扱われます。 1 つ目は、コンテンツのプロパティの構文を利用し、省略、`Border.Child`プロパティ要素。 2 つ目を示しています`Border.Child`明示的にします。  
  
```xaml  
<Border>  
  <TextBox Width="300"/>  
</Border>  
<!--explicit equivalent-->  
<Border>  
  <Border.Child>  
    <TextBox Width="300"/>  
  </Border.Child>  
</Border>  
```  
  
 XAML 言語の規則として XAML コンテンツ プロパティの値必要がある前に、またはその他のすべてのプロパティ要素の後に、そのオブジェクト。 たとえば、次のマークアップはコンパイルされません。  
  
```  
<Button>I am a   
  <Button.Background>Blue</Button.Background>  
  blue button</Button>  
```  
  
 XAML コンテンツ プロパティの詳細については、この制限は、の「XAML コンテンツ プロパティ」セクションを参照してください。 [XAML 構文の詳細](xaml-syntax-in-detail.md)します。  
  
### <a name="text-content"></a>テキストの内容  
 XAML 要素の数が少ないは、その内容としてテキストを直接処理できます。 これを有効にするには、場合は true、次の場合のいずれかの必要があります。  
  
-   クラスは、コンテンツのプロパティを宣言する必要があり、そのコンテンツ プロパティが文字列に割り当てることができるにする必要があります (タイプ<xref:System.Object>)。 たとえば、いずれか<xref:System.Windows.Controls.ContentControl>を使用して<xref:System.Windows.Controls.ContentControl.Content%2A>型は、コンテンツのプロパティとして<xref:System.Object>、これは実用的で、次の使用法をサポートし、<xref:System.Windows.Controls.ContentControl>など、 <xref:System.Windows.Controls.Button>:`<Button>Hello</Button>`します。  
  
-   型は、ケースのテキストの内容がその型コンバーターの初期化テキストとして使用される型コンバーターを宣言する必要があります。 たとえば、`<Brush>Blue</Brush>` のようにします。 この場合は、実際にはあまり一般的です。  
  
-   種類は、既知の XAML 言語プリミティブである必要があります。  
  
### <a name="content-properties-and-collection-syntax-combined"></a>コンテンツのプロパティとコレクション構文の結合  
 次の例について考えます。  
  
```xaml  
<StackPanel>  
  <Button>First Button</Button>  
  <Button>Second Button</Button>  
</StackPanel>  
```  
  
 ここでは、各<xref:System.Windows.Controls.Button>の子要素は、<xref:System.Windows.Controls.StackPanel>します。 これは、2 つのさまざまな理由で 2 つのタグを省略する効率的で直感的なマークアップです。  
  
-   **省略された StackPanel.Children プロパティ要素:** <xref:System.Windows.Controls.StackPanel>から派生した<xref:System.Windows.Controls.Panel>します。 <xref:System.Windows.Controls.Panel> 定義<xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType>としてその XAML コンテンツのプロパティ。  
  
-   **省略された UIElementCollection object 要素:**<xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType>プロパティには、型<xref:System.Windows.Controls.UIElementCollection>、実装する<xref:System.Collections.IList>します。 コレクションの処理などの XAML のルールに基づいて、コレクションの要素タグを省略できます<xref:System.Collections.IList>します。 (この場合、<xref:System.Windows.Controls.UIElementCollection>実際にインスタンス化できないため、既定のコンス トラクターは公開されませんしているため、<xref:System.Windows.Controls.UIElementCollection>オブジェクトの要素をコメント アウトされた表示)。  
  
```xaml  
<StackPanel>  
  <StackPanel.Children>  
    <!--<UIElementCollection>-->  
    <Button>First Button</Button>  
    <Button>Second Button</Button>  
    <!--</UIElementCollection>-->  
  </StackPanel.Children>  
</StackPanel>  
```  
  
### <a name="attribute-syntax-events"></a>属性の構文 (イベント)  
 属性構文は、メンバー プロパティではなく、イベントの場合も使用できます。 この場合、属性の名前は、イベントの名前です。 XAML 用のイベントの WPF 実装では、属性の値は、そのイベントのデリゲートを実装するハンドラーの名前です。 たとえば、次のマークアップがのハンドラーを割り当てます、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベントを<xref:System.Windows.Controls.Button>マークアップで作成します。  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]  
  
 イベントと WPF の XAML をこの属性の構文の例だけをよりがあります。 たとえば、疑問に思うかもしれません何、`ClickHandler`および定義方法を表す、ここで参照されています。 これは、近日出版予定の説明は[イベントと XAML コード ビハインド](xaml-overview-wpf.md#events_and_xaml_codebehind)このトピックの「します。  
  
<a name="case_and_white space_in_xaml"></a>   
## <a name="case-and-white-space-in-xaml"></a>ケース テーブルと XAML 内の空白  
 XAML は、大文字と小文字は一般にです。 バッキング型の解決のために、WPF の XAML は、CLR は大文字小文字を区別する、同じルールで大文字小文字を区別します。 名前、アセンブリ内の基になる型または型のメンバーと比較した場合の機密性の高い文字種を使用してには、オブジェクトの要素、プロパティ要素、および属性名のすべてを指定してください。 XAML 言語のキーワードとプリミティブも小文字が区別されます。 値は、常に大文字小文字が区別されません。 値の大文字小文字の区別には、値、またはプロパティ値の型を受け取るプロパティに関連付けられている型コンバーターの動作は異なります。 使用するプロパティなど、<xref:System.Boolean>種類は、いずれかを実行できる`true`または`True`ネイティブの WPF XAML パーサーは入力文字列に変換するためにのみ、同等の値として<xref:System.Boolean>の同等としてこれらを既に許可します。  
  
 WPF XAML プロセッサとシリアライザーを無視するか、伴わないすべての空白文字を削除しは有意の空白を正規化します。 これは、XAML 仕様の空白に対する動作の既定の推奨設定と一致します。 この動作は、通常 XAML コンテンツ プロパティ内の文字列を指定した場合ののみです。 簡単に言うでは、XAML スペース、改行やタブ文字を空白に変換し、領域の場合は 1 つが保持されますが、連続する文字列の両端が見つかりましたします。 XAML の空白文字の処理の詳しい説明については、このトピックでは説明しません。 詳細については、次を参照してください。[スペースで XAML 処理](../../xaml-services/whitespace-processing-in-xaml.md)します。  
  
<a name="markup_extensions"></a>   
## <a name="markup-extensions"></a>マークアップ拡張機能  
 マークアップ拡張機能は、XAML 言語概念です。 属性構文、中かっこの値を提供するために使用する場合 (`{`と`}`) マークアップ拡張機能の使用を示します。 これにより、XAML の属性値のリテラル文字列または文字列に変換できる値のいずれかとして一般的な処理をエスケープするために処理されます。  
  
 使用される最も一般的なマークアップ拡張[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーション プログラミングは[バインド](binding-markup-extension.md)、データ バインド式、およびリソースの参照に使用される[StaticResource](staticresource-markup-extension.md)と[DynamicResource](dynamicresource-markup-extension.md)します。 マークアップ拡張機能を使用すると、そのプロパティが属性構文を一般的にサポートしない場合でも、プロパティの値を指定するのに属性の構文を使用できます。 多くの場合、マークアップ拡張機能では、中間式の型を使用して、値を遅延またはのみ実行時に存在するその他のオブジェクトを参照するなどの機能を有効にします。  
  
 たとえば、次のマークアップの値を設定します。、<xref:System.Windows.FrameworkElement.Style%2A>プロパティ属性の構文を使用します。 <xref:System.Windows.FrameworkElement.Style%2A>プロパティのインスタンスを受け取り、<xref:System.Windows.Style>クラスは、既定では属性構文の文字列によってインスタンス化できませんでした。 この場合、属性を参照して、特定のマークアップ拡張機能が[StaticResource](staticresource-markup-extension.md)します。 そのマークアップ拡張機能が処理されるときに、リソース ディクショナリのキー付きリソースとして既にインスタンス化されているスタイルへの参照を返します。  
  
 [!code-xaml[FEResourceSH_snip#XAMLOvwShortResources](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources)]  
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources2](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources2)]  
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources3](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources3)]  
  
 参照を一覧表示するマークアップ拡張機能のすべての XAML は、WPF で具体的には実装を参照してください。 [WPF XAML 拡張機能](wpf-xaml-extensions.md)します。 System.Xaml と .NET Framework の XAML 実装のより幅広く利用できるは、定義されているマークアップ拡張機能の参照一覧については、次を参照してください[XAML Namespace (x:)。言語機能](../../xaml-services/xaml-namespace-x-language-features.md)します。 マークアップ拡張機能の概念の詳細については、次を参照してください。[マークアップ拡張機能と WPF XAML](markup-extensions-and-wpf-xaml.md)します。  
  
<a name="type_converters"></a>   
## <a name="type-converters"></a>型コンバーター  
 [XAML 構文の概要](xaml-overview-wpf.md#xaml_syntax_in_brief) セクションで、属性の値は文字列で設定できる必要があります、示されていました。 その他のオブジェクト型またはプリミティブ型の値を文字列に変換する方法の基本的なネイティブの処理がに基づいて、<xref:System.String>型自体などの型をネイティブではさらに特定の処理<xref:System.DateTime>または<xref:System.Uri>します。 多く[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]型またはそれらの型のメンバーは、基本的な文字列属性の処理方法のより複雑なオブジェクト型のインスタンスを文字列と属性として指定できることで、動作を拡張します。  
  
 <xref:System.Windows.Thickness>構造を XAML の使用状況を有効になっている型の変換を持つ型の例を示します。 <xref:System.Windows.Thickness> 入れ子になった四角形内での測定値を示しなどのプロパティの値として使用されます<xref:System.Windows.FrameworkElement.Margin%2A>します。 型コンバーターを配置することで<xref:System.Windows.Thickness>、すべてのプロパティを使用する、<xref:System.Windows.Thickness>を簡単に属性として指定されるため、XAML で指定されます。 次の例の値を指定する型の変換と属性の構文を使用して、 <xref:System.Windows.FrameworkElement.Margin%2A>:  
  
 [!code-xaml[XAMLOvwSupport#MarginTCE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#margintce)]  
  
 前の属性構文の例は、次に相当より詳細な構文例では、場所、<xref:System.Windows.FrameworkElement.Margin%2A>プロパティ要素構文を含むによって設定されている代わりに、<xref:System.Windows.Thickness>オブジェクト要素。 4 つのプロパティのキー<xref:System.Windows.Thickness>新しいインスタンスに対して属性として設定されます。  
  
 [!code-xaml[XAMLOvwSupport#MarginVerbose](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#marginverbose)]  
  
> [!NOTE]
>  型変換が、唯一のパブリック型自体に既定のコンス トラクターがあるないため、サブクラスに関連することがなくその型にプロパティを設定する方法であるオブジェクトの数に制限も。 例としては、<xref:System.Windows.Input.Cursor>します。  
  
 型変換およびその使用の属性の詳細については、構文がサポートされているを参照してください[TypeConverters および XAML](typeconverters-and-xaml.md)します。  
  
<a name="xaml_root_elements_and_xaml_namespaces"></a>   
## <a name="xaml-root-elements-and-xaml-namespaces"></a>XAML ルート要素と XAML 名前空間  
 XAML ファイルでは、両方を適切な形式にするためには 1 つだけのルート要素があります[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]ファイルと有効な XAML ファイル。 WPF アプリケーション モデルで著名な意味を持つルート要素を使用する一般的な WPF のシナリオで (たとえば、<xref:System.Windows.Window>または<xref:System.Windows.Controls.Page>ページの  <xref:System.Windows.ResourceDictionary> 、外部のディクショナリのまたは<xref:System.Windows.Application>アプリケーション定義の)。 次の例の一般的な XAML ファイルのルート要素を示しています、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]  ページのルート要素と<xref:System.Windows.Controls.Page>します。  
  
 [!code-xaml[XAMLOvwSupport#RootOnly](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly)]  
[!code-xaml[XAMLOvwSupport#RootOnly2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly2)]  
  
 ルート要素は、属性も含まれています。`xmlns`と`xmlns:x`します。 これらの属性は、XAML 名前空間には、マークアップで要素として参照する型のバックアップの種類の定義が含まれている XAML プロセッサに示します。 `xmlns`属性は、具体的には、既定の XAML 名前空間を示します。 既定の XAML 名前空間内では、プレフィックスなし、マークアップ内のオブジェクトの要素を指定できます。 ほとんどの [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーション シナリオとで示す例のほぼすべての [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のセクションでは、 [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)] 、既定の XAML 名前空間にマップされて、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 名前空間 [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)] 。 `xmlns:x`属性は XAML 名前空間が追加され、XAML 言語の名前空間のマップを示します [!INCLUDE[TLA#tla_xamlxmlnsv1](../../../../includes/tlasharptla-xamlxmlnsv1-md.md)] します。  
  
 この使用法の`xmlns`の使用状況と、名前空間のマッピングのスコープを定義するは、XML 1.0 仕様に一致します。 XAML 名前スコープは、XAML 名前スコープの種類で名前空間の要素がサポートされている型の解決や、XAML を解析する際にする方法について何か意味もその内のみ XML 名前空間からは異なります。  
  
 なお、`xmlns`属性は各 XAML ファイルのルート要素で厳密に必要なだけです。 `xmlns` 定義は、ルート要素のすべての子孫要素に適用されます (この動作は XML 1.0 仕様で一貫性のあるもう一度`xmlns`)。`xmlns`属性は、ルートの下にあるその他の要素では許可されてもと定義の要素のすべての子孫要素に適用されます。 ただし、頻繁に定義または XAML 名前空間の再定義は、読み取りが困難である XAML マークアップ スタイルで結果ことができます。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML プロセッサの実装には、WPF のコア アセンブリの認識のインフラストラクチャが含まれています。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コア アセンブリがサポートする型を含めることが知られて、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]既定の XAML 名前空間へのマッピング。 これは、プロジェクトのビルドの一部である構成により可能にビルドされ、プロジェクト システム ファイルと、WPF します。 そのため、既定値として既定の XAML 名前空間を宣言する`xmlns`に由来する XAML 要素を参照するために必要なは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アセンブリ。  
  
### <a name="the-x-prefix"></a>X: プレフィックス  
 前のルート要素例プレフィックス`x:`XAML 名前空間をマップするために使用された [!INCLUDE[TLA#tla_xamlxmlnsv1](../../../../includes/tlasharptla-xamlxmlnsv1-md.md)] 、これは XAML 言語をサポートする専用の XAML 名前空間を構築します。 これは、`x:`のプロジェクトのテンプレートで、例については、およびこのドキュメントでこの XAML 名前空間のマッピング プレフィックスで使用[!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)]します。 XAML 言語の XAML 名前空間には、XAML で非常に頻繁に使用するいくつかのプログラミング構成要素が含まれます。 最も一般的なの一覧を次に`x:`を使用するプログラミング構成要素のプレフィックスします。  
  
-   [X:key](../../xaml-services/x-key-directive.md):内の各リソースの一意のキーの設定、 <xref:System.Windows.ResourceDictionary> (またはその他のフレームワークのようなディクショナリの概念)。 `x:Key` 90% のアカウントではおそらく、`x:`使用法の一般的な WPF アプリケーションのマークアップに表示されます。  
  
-   [X:class](../../xaml-services/x-class-directive.md):指定します、 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] XAML ページの分離コードを提供するクラスの名前空間とクラス名。 1 つの WPF プログラミング モデルでは、分離コードをサポートするために、このようなクラスがあり、ほぼ常に表示するため`x:`リソースがない場合でも、マップします。  
  
-   [X:name](../../xaml-services/x-name-directive.md):オブジェクト要素が処理された後、実行時のコードに存在するインスタンスの実行時のオブジェクト名を指定します。 WPF 定義されている同等のプロパティを頻繁に使用する一般に、 [X:name](../../xaml-services/x-name-directive.md)します。 このようなプロパティ具体的には CLR バッキング プロパティにマップされ、したがってアプリケーションのプログラミングの方が便利で頻繁に使用するコードの実行時に初期化された XAML から名前付きの要素を検索します。 このようなプロパティは、最も一般的な<xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>します。 使用することもあります[X:name](../../xaml-services/x-name-directive.md)と同等の WPF フレームワーク-レベル<xref:System.Windows.FrameworkElement.Name%2A>プロパティが特定の種類でサポートされていません。 これは、特定のアニメーション シナリオで発生します。  
  
-   [X:static](../../xaml-services/x-static-markup-extension.md):それ以外の場合、XAML と互換性のあるプロパティではない静的な値を返しますの参照を有効にします。  
  
-   [X:type](../../xaml-services/x-type-markup-extension.md):構築、<xref:System.Type>型名の上に基づく参照。 これは、属性を指定に使用<xref:System.Type>など<xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>プロパティが頻繁にネイティブの文字列には、-に-<xref:System.Type>ような方法で変換を[X:type](../../xaml-services/x-type-markup-extension.md)マークアップ拡張機能の使用は、省略可能。  
  
 プログラミング構成要素がある、`x:`プレフィックス/XAML 名前空間は一般的でないです。 詳細については、次を参照してください[XAML Namespace (x:)。言語機能](../../xaml-services/xaml-namespace-x-language-features.md)します。  
  
<a name="custom_prefixes_and_custom_types_in_xaml"></a>   
## <a name="custom-prefixes-and-custom-types-in-xaml"></a>カスタムのプレフィックスと XAML でのカスタムの型  
 カスタムの一部として、アセンブリを指定するには、独自のカスタム アセンブリや WindowsBase、PresentationCore、PresentationFramework の WPF のコアの外部アセンブリでは、`xmlns`マッピングします。 XAML では、そのアセンブリからは、その型が正しく実行しようとして、XAML の使用状況をサポートするために実装されている限り、型を参照できます、します。  
  
 次は、XAML マークアップでのカスタムのプレフィックス作業の非常に基本的な例です。 プレフィックス`custom`ルート要素タグで定義され、パッケージと、アプリケーションには、特定のアセンブリにマップします。 このアセンブリには、型が含まれている`NumericUpDown`、一般的な XAML の使用量だけでなく、XAML の WPF コンテンツ モデルでこの特定の時点でその挿入を許可するクラスの継承を使用してサポートするために実装されます。 このインスタンス`NumericUpDown`コントロールが、オブジェクト要素として宣言されている、名前空間プレフィックスを使用して、XAML パーサーがどのような XAML を認識できるように、型を格納および型定義を含むバッキング アセンブリがあるためです。  
  
```  
<Page  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"   
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"   
    xmlns:custom="clr-namespace:NumericUpDownCustomControl;assembly=CustomLibrary"  
    >  
  <StackPanel Name="LayoutRoot">  
    <custom:NumericUpDown Name="numericCtrl1" Width="100" Height="60"/>  
...  
  </StackPanel>  
</Page>  
```  
  
 XAML でのカスタムの種類の詳細については、次を参照してください。 [XAML とカスタム クラスの WPF](xaml-and-custom-classes-for-wpf.md)します。  
  
 XML 名前空間とアセンブリでバッキング コードの名前空間との関連付けに関する詳細については、次を参照してください。 [XAML 名前空間および WPF XAML のマッピングの Namespace](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)します。  
  
<a name="events_and_xaml_codebehind"></a>   
## <a name="events-and-xaml-code-behind"></a>イベントと XAML 分離コード  
 ほとんど[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]XAML マークアップと分離コードの両方のアプリケーションで構成されます。 として書き込まれますが、XAML、プロジェクト内で、`.xaml`ファイル、および[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]Microsoft Visual Basic や c# などの言語が分離コード ファイルの書き込みに使用します。 XAML のコード ビハインドの場所がファイルの XAML ファイルは、名前空間を指定することによって識別され、クラスの XAML ファイルをマークアップ WPF プログラミングおよびアプリケーション モデルの一部としてコンパイルされるとき、 `x:Class` XAML のルート要素の属性です。  
  
 これまでの例では、いくつかのボタンを見てきましたが、論理的な動作がまだ関連付けられていたこれらのボタンのいずれも。 オブジェクト要素の動作を追加するためのプライマリ アプリケーション レベルのメカニズムは、要素クラスの既存のイベントを使用して、実行時にそのイベントが発生したときに呼び出されるイベントの特定のハンドラーを記述するには。 イベント名および使用するハンドラーの名前は、ハンドラーを実装するコードが分離コードで定義されている一方、マークアップで指定されます。  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]  
  
 [!code-csharp[XAMLOvwSupport#ButtonWithCodeBehindHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml.cs#buttonwithcodebehindhandler)]
 [!code-vb[XAMLOvwSupport#ButtonWithCodeBehindHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#buttonwithcodebehindhandler)]  
  
 分離コード ファイルで CLR 名前空間を使用することに注意してください`ExampleNamespace`宣言と`ExamplePage`名前空間内の部分クラスとして。 これは対応して、`x:Class`属性の値`ExampleNamespace`します。`ExamplePage` マークアップのルートで指定されました。 WPF マークアップ コンパイラはルート要素の型からクラスを派生させることにより、コンパイル済みの XAML ファイルの部分クラスを作成します。 分離コードも同じ部分クラスを定義しているときに、結果のコードは、同じ名前空間と、コンパイルされたアプリケーションのクラス内で組み合わされます。  
  
 WPF における分離コードのプログラミングの要件の詳細については、「分離コード、イベント ハンドラー、および部分クラスの要件」のセクションを参照してください。[分離コードと wpf XAML](code-behind-and-xaml-in-wpf.md)します。  
  
 分離コード ファイルを作成したくない場合は、することもできますインライン XAML ファイルでコード。 ただし、インライン コードは、多くの制限のある小さい汎用的な手法です。 詳細については、「[WPF における分離コードと XAML](code-behind-and-xaml-in-wpf.md)」を参照してください。  
  
### <a name="routed-events"></a>ルーティング イベント  
 特定のイベントの機能の基盤を[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]はルーティング イベントです。 要素がツリーのリレーションシップを介して接続している限り、別の要素で発生したイベントを処理する要素にルーティング イベントを使用します。 XAML 属性使用してイベント処理を指定するときに、ルーティング イベントをリッスンおよびクラスのメンバー テーブルでその特定のイベントが記載されていない要素を含む任意の要素で処理します。 これは、所有しているクラスの名前を持つイベントの名前属性を修飾することによって実現されます。 たとえば、親`StackPanel`、進行中で`StackPanel`  /  `Button`の例は、子要素のボタンのハンドラーを登録できます<xref:System.Windows.Controls.Primitives.ButtonBase.Click>属性を指定することによってイベント`Button.Click`で、 `StackPanel`オブジェクト要素の属性値として、ハンドラー名。 どのようにルーティング イベントの動作の詳細については、次を参照してください。[ルーティング イベントの概要](routed-events-overview.md)します。  
  
<a name="x_name_and_xaml_named_elements"></a>   
## <a name="xaml-named-elements"></a>XAML の名前付き要素  
 既定では、オブジェクト グラフを XAML オブジェクト要素を処理することによって作成されるオブジェクトのインスタンスが所有していないオブジェクト参照の一意識別子。 これに対し、コードでコンス トラクターを呼び出す場合ほぼ常に使用するコンス トラクターの結果構築済みのインスタンスに変数を設定するコードでインスタンスを参照できるようにします。 XAML を定義するマークアップ定義によって作成されたオブジェクトの標準的なアクセスを提供するために、 [X:name 属性](../../xaml-services/x-name-directive.md)します。 値を設定することができます、`x:Name`任意のオブジェクト要素の属性。 コードで指定した識別子は、構築済みのインスタンスを参照するインスタンス変数と同じです。 オブジェクトのインスタンス (名前は、そのインスタンスを参照)、された、分離コードでは、アプリケーション内で実行時の操作を処理するには、名前付きの要素を参照できる場合とすべての点では、要素の関数の名前。 インスタンスと変数の間には、この接続は、WPF XAML マークアップ コンパイラでは、詳細は具体的にが含まれる機能とパターンなど<xref:System.Windows.Markup.IComponentConnector.InitializeComponent%2A>をこのトピックで詳しくは説明しません。  
  
 WPF フレームワーク レベルの XAML 要素を継承する<xref:System.Windows.FrameworkElement.Name%2A>プロパティは、これは定義されている XAML に相当`x:Name`属性。 その他のクラスの対応するプロパティ レベルを提供も`x:Name`、として一般に定義されている、`Name`プロパティ。 見つからない場合、一般的に、`Name`メンバー テーブルに、選択した要素/型を使用してプロパティ`x:Name`代わりにします。 `x:Name`値が使用できる、実行時に特定のサブシステムまたはユーティリティ メソッドのいずれかなど、XAML 要素に識別子を提供<xref:System.Windows.FrameworkElement.FindName%2A>します。  
  
 次の例のセット<xref:System.Windows.FrameworkElement.Name%2A>上、<xref:System.Windows.Controls.StackPanel>要素。 ハンドラーを次に、<xref:System.Windows.Controls.Button>内で<xref:System.Windows.Controls.StackPanel>参照、<xref:System.Windows.Controls.StackPanel>そのインスタンスの参照を使用して`buttonContainer`によって設定<xref:System.Windows.FrameworkElement.Name%2A>します。  
  
 [!code-xaml[XAMLOvwSupport#NamedE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede)]  
[!code-xaml[XAMLOvwSupport#NamedE2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede2)]  
  
 [!code-csharp[XAMLOvwSupport#NameCode](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml.cs#namecode)]
 [!code-vb[XAMLOvwSupport#NameCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#namecode)]  
  
 変数と同様は予測可能な特定のスコープ内で一意名を適用できるようにインスタンスの XAML 名は、スコープの概念によって管理されます。 ページを定義するマークアップをプライマリ XAML 名前スコープの境界がそのページのルート要素に一意の 1 つの XAML スコープを表します。 ただし、マークアップの他のソースがスタイルまたはテンプレート、スタイル内など、実行時にページと対話できます、このようなマークアップ ソース多くの場合とは限りませんが、ページの XAML 名前スコープ接続しないを独自の XAML 名前スコープ。 詳細については`x:Name`XAML 名前スコープを参照してくださいと<xref:System.Windows.FrameworkElement.Name%2A>、 [X:name ディレクティブ](../../xaml-services/x-name-directive.md)、または[WPF XAML 名前スコープ](wpf-xaml-namescopes.md)します。  
  
<a name="attached_properties_and_attached_events"></a>   
## <a name="attached-properties-and-attached-events"></a>添付プロパティおよび添付イベント  
 XAML では、特定のプロパティまたはイベントに設定されている要素の型の定義で、プロパティまたはイベントが存在するかどうかに関係なく、任意の要素で指定できるようにする言語機能を指定します。 この機能のプロパティのバージョンには、添付プロパティを呼び出すと、イベントのバージョンには、添付イベントが呼び出されます。 概念的には、添付プロパティおよび添付イベントの任意の XAML 要素/オブジェクトのインスタンスで設定できるグローバルのメンバーとして考えることができます。 ただし、その要素/クラスや大規模なインフラストラクチャは、接続されている値のバッキング プロパティ ストアをサポートする必要があります。  
  
 XAML の添付プロパティは通常、属性構文で使用されます。 形式で添付プロパティを指定する属性の構文で*ownerType*.*propertyName*します。  
  
 プロパティ要素の使用方法に似ています、一見すると、ここで、 *ownerType*は常に別の種類のオブジェクトの要素よりも、添付プロパティが設定されているを指定します。 *ownerType*を取得または添付プロパティの値を設定するには、XAML プロセッサによって必要なアクセサー メソッドを提供する型です。  
  
 添付プロパティの最も一般的なシナリオでは、それぞれの親要素にプロパティ値を報告する子要素を有効にします。  
  
 次の例を示しています、<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>添付プロパティ。 <xref:System.Windows.Controls.DockPanel>クラスのアクセサーを定義する<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>添付プロパティを所有しています。 <xref:System.Windows.Controls.DockPanel>クラスは、その子要素を反復処理し、主に各要素の値の設定を確認するロジックも含まれています。<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>します。 値が見つかった場合、その値が子要素を配置するレイアウト時に使用されます。 使用、<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>添付プロパティと、この配置機能のスタブに適したシナリオでは実際には、<xref:System.Windows.Controls.DockPanel>クラス。  
  
 [!code-xaml[XAMLOvwSupport#DockAP](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#dockap)]  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、ほとんどまたはすべての添付プロパティは依存関係プロパティとしても実装されます。 詳細については、「[添付プロパティの概要](attached-properties-overview.md)」を参照してください。  
  
 添付イベントを使用して、類似した*ownerType*.*eventName*属性構文の形式。 、非添付イベントと同じようには、XAML の添付イベントの属性の値は、要素のイベントが処理されるときに呼び出されるハンドラー メソッドの名前を指定します。 WPF XAML の添付イベントの使用法は、まれです。 詳細については、次を参照してください。[添付イベントの概要](attached-events-overview.md)します。  
  
<a name="base_classes_and_xaml"></a>   
## <a name="base-types-and-xaml"></a>基本型、および XAML  
 基になる WPF XAML と XAML 名前空間に対応する型のコレクションである[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]に加えて XAML のマークアップ要素オブジェクト。 ただし、すべてのクラスは、要素にマップすることができます。 など、クラスを抽象化<xref:System.Windows.Controls.Primitives.ButtonBase>、における継承の特定の非抽象基本クラスを使用して、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]オブジェクト モデルです。 抽象ものも含めて、基底クラスは、その階層内のいくつかの基本クラスからメンバーを継承、具体的な XAML 要素ごとのため、XAML 開発することも重要です。 多くの場合、これらのメンバーには要素の属性として設定できるプロパティまたは処理できるイベントが含まれます。 <xref:System.Windows.FrameworkElement> 具体的なベースである[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]クラスの[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]WPF フレームワーク レベル。 設計時に[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]、さまざまな図形、パネル、デコレーターを使用するか、すべてのコントロール クラスから派生<xref:System.Windows.FrameworkElement>します。 関連する基本クラスでは、 <xref:System.Windows.FrameworkContentElement>、フロー レイアウトのプレゼンテーションのためも動作するドキュメント指向の要素のサポートを使用して[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]を意図的にミラー化、[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]で<xref:System.Windows.FrameworkElement>します。 要素レベルで属性の組み合わせと[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]は特定の XAML 要素とその基になる型に関係なく、ほとんどの具体的な XAML 要素で設定可能な共通のプロパティのセットを使用するオブジェクト モデルを提供します。  
  
<a name="xaml_security"></a>   
## <a name="xaml-security"></a>XAML セキュリティ  
 XAML は、オブジェクトのインスタンス化と実行を直接表すマークアップ言語です。 そのため、対応する生成 (ネットワーク アクセス、ファイル システムの IO など) のシステム リソースと対話するのと同じ機能のある要素の XAML で作成したコードは。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] サポート、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]セキュリティ フレームワーク[!INCLUDE[TLA#tla_cas](../../../../includes/tlasharptla-cas-md.md)]します。 つまり、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]インターネット ゾーンで実行されているコンテンツが実行のアクセス許可を削減します。 "Loose XAML"(コンパイルされない XAML ページ XAML ビューアーでの読み込み時に解釈) と[!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]このインターネット ゾーンでは、通常実行して、同じアクセス許可セットを使用します。  ただしに完全に信頼されたアプリケーションに読み込まれた XAML では、ホスト アプリケーションのようにシステム リソースに同じアクセス権があります。 詳細については、次を参照してください。 [WPF 部分信頼セキュリティ](../wpf-partial-trust-security.md)します。  
  
<a name="loading_xaml_from_code"></a>   
## <a name="loading-xaml-from-code"></a>コードから XAML の読み込み  
 すべての UI を定義する XAML を使用できますはも XAML で UI の一部だけを定義する適切な場合があります。 この機能は、ビジネス オブジェクト、またはさまざまなシナリオを提供する XAML を使用して、情報のローカル記憶域、部分的なカスタマイズを有効にされる可能性があります。 これらのシナリオにキーが、<xref:System.Windows.Markup.XamlReader>クラスとその<xref:System.Windows.Markup.XamlReader.Load%2A>メソッド。 入力は、XAML ファイルであり、出力は、そのマークアップから作成されたオブジェクトの実行時のツリーのすべてを表すオブジェクト。 アプリケーションに既に存在する別のオブジェクトのプロパティであるオブジェクトを挿入できます。 プロパティは、実行エンジンを通知するが、新しいコンテンツが、アプリケーションに追加されたこと、最終的な表示機能を持つコンテンツ モデルで適切なプロパティが、実行中のアプリケーションのコンテンツを非常に簡単に変更できます。によって XAML の読み込み。 この機能が一般にのみ、完全に信頼されたアプリケーションで使用可能な実行中のアプリケーションにファイルの読み込みの明らかなセキュリティへの影響のために注意してください。  
  
<a name="whats_next"></a>   
## <a name="whats-next"></a>次の内容  
 このトピックでは、WPF に適用される XAML 構文の概念と用語の概要を提供します。 ここで使用される用語の詳細については、次を参照してください。 [XAML 構文の詳細](xaml-syntax-in-detail.md)します。  
  
 この手順をまだ行っていないことは場合、チュートリアルのトピックで行う演習を試す[チュートリアル。初めての WPF デスクトップ アプリケーション](../getting-started/walkthrough-my-first-wpf-desktop-application.md)します。 このチュートリアルで説明されているマークアップを中心としたアプリケーションを作成するときにこのトピックで説明した概念の多くが深まります。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 基づく特定のアプリケーション モデルを使用して、<xref:System.Windows.Application>クラス。 詳細については、次を参照してください。[アプリケーション管理の概要](../app-development/application-management-overview.md)します。  
  
 [WPF アプリケーションのビルド](../app-development/building-a-wpf-application-wpf.md)とコマンド ラインから XAML の包括的なアプリケーションを構築する方法の詳細については、[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]します。  
  
 [依存関係プロパティの概要](dependency-properties-overview.md)でプロパティの用途の詳細については、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、および依存関係プロパティの概念が導入されました。  
  
## <a name="see-also"></a>関連項目

- [XAML 構文の詳細](xaml-syntax-in-detail.md)
- [WPF における XAML とカスタム クラス](xaml-and-custom-classes-for-wpf.md)
- [XAML 名前空間 (x:)言語機能](../../xaml-services/xaml-namespace-x-language-features.md)
- [WPF XAML 拡張機能](wpf-xaml-extensions.md)
- [基本要素の概要](base-elements-overview.md)
- [WPF のツリー](trees-in-wpf.md)
