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
ms.openlocfilehash: ee5318b8ba1284f2805b80b3e41fab3ae739158c
ms.sourcegitcommit: 3eeea78f52ca771087a6736c23f74600cc662658
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/31/2019
ms.locfileid: "68672006"
---
# <a name="xaml-overview-wpf"></a>XAML の概要 (WPF)

このトピックでは、xaml 言語の機能について説明し、xaml を使用[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]してアプリケーションを記述する方法を示します。 このトピックでは、によっ[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]て実装される XAML について説明します。 XAML 自体は、よりも[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]大きな言語の概念です。  

<a name="what_is_xaml"></a>   
## <a name="what-is-xaml"></a>XAML とは  
 XAML は、宣言型マークアップ言語です。 .NET Framework プログラミングモデルに適用されているように、 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] XAML を使用すると、.NET Framework アプリケーションのを簡単に作成できます。 宣言型の XAML [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]マークアップで可視要素を作成し、部分クラス[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]定義を通じてマークアップに結合された分離コードファイルを使用して、ランタイムロジックから定義を分離することができます。 XAML は、アセンブリで定義されている特定のバッキング型のセットに含まれるオブジェクトのインスタンス化を直接表します。 これは、多くの他のマークアップ言語とは異なります。通常、これは、バッキング型システムに直接関連付けることなく、解釈される言語です。 XAML を使用すると、独立したパーティが[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 、異なるツールを使用して、アプリケーションのロジックを操作できるワークフローを有効にすることができます。  
  
 XAML ファイルは、テキストとして表現された場合、 `.xaml`通常は拡張子を持つ XML ファイルです。 ファイルは任意の XML エンコーディングでエンコードできますが、UTF-8 としてエンコードするのが一般的です。  
  
 次の例は、 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]の一部としてボタンを作成する方法を示しています。 この例は、XAML が共通[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]のプログラミングメタファ (完全なサンプルではありません) を表す方法を説明することを目的としています。  
  
 [!code-xaml[XAMLOvwSupport#DirtSimple](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]  
  
<a name="xaml_syntax_in_brief"></a>   
## <a name="xaml-syntax-in-brief"></a>XAML 構文の概要  
 次のセクションでは、XAML 構文の基本的な形式について説明し、短いマークアップの例を示します。 これらのセクションは、各構文形式についての完全な情報を提供するためのものではありません。たとえば、バッキング型システムでこれらがどのように表現されるかなどです。 このトピックで紹介する各構文フォームの XAML 構文の詳細については、「 [Xaml 構文の詳細](xaml-syntax-in-detail.md)」を参照してください。  
  
 XML 言語に慣れている場合は、次のいくつかのセクションの内容の多くが基本になります。 これは、XAML の基本的なデザイン原則の1つによる結果です。  XAML 言語では独自の概念が定義されていますが、これらの概念は XML 言語とマークアップ形式で動作します。  
  
### <a name="xaml-object-elements"></a>XAML オブジェクト要素  
 オブジェクト要素は、通常、型のインスタンスを宣言します。 この型は、XAML を言語として使用するテクノロジのバッキング型を提供するアセンブリで定義されています。  
  
 オブジェクト要素の構文は、常に開始山かっこ\<() で始まります。 この後に、インスタンスを作成する型の名前が続きます。 (名前にプレフィックスを含めることができます。これについては後で説明します)。その後、必要に応じて、object 要素の属性を宣言できます。 オブジェクト要素タグを完成させるには、終わり山かっこ (>) で終了します。 代わりに、スラッシュと終わり山かっこ (/>) を使用してタグを完了することで、コンテンツのない自己終了フォームを使用することができます。 たとえば、前に示したマークアップスニペットをもう一度見てみましょう。  
  
 [!code-xaml[XAMLOvwSupport#DirtSimple](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]  
  
 2つのオブジェクト要素`<StackPanel>` (コンテンツと終了タグを含む)、および`<Button .../>` (自己終了フォーム (複数の属性を含む)) を指定します。 オブジェクト要素と`StackPanel` `Button`各要素は、によっ[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]て定義されるクラスの名前にマップされ、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アセンブリの一部になります。 オブジェクト要素タグを指定するときは、XAML 処理の命令を作成して新しいインスタンスを作成します。 各インスタンスは、XAML を解析および読み込みするときに、基になる型のパラメーターなしのコンストラクターを呼び出すことによって作成されます。  
  
### <a name="attribute-syntax-properties"></a>属性の構文 (プロパティ)  
 オブジェクトのプロパティは、多くの場合、オブジェクト要素の属性として表現できます。 属性構文は、属性構文で設定されているプロパティに名前を付け、その後に代入演算子 (=) を指定します。 属性の値は、常に引用符で囲まれた文字列として指定されます。  
  
 属性構文は、最も効率的なプロパティ設定の構文であり、過去にマークアップ言語を使用した開発者に使用する最も直感的な構文です。 たとえば、次のマークアップは、として`Content`指定された表示テキストに加えて、赤いテキストと青の背景を持つボタンを作成します。  
  
 [!code-xaml[XAMLOvwSupport#BlueRedButton](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbutton)]  
  
### <a name="property-element-syntax"></a>Property 要素の構文  
 オブジェクト要素の一部のプロパティでは、属性構文は使用できません。これは、プロパティ値を指定するために必要なオブジェクトまたは情報を、属性構文の引用符および文字列制限内で適切に表現できないためです。 このような場合は、property 要素の構文として知られている別の構文を使用できます。  
  
 Property 要素の開始タグの`<`構文は、 *typeName*`.`*propertyName*`>`です。 通常、そのタグの内容は、プロパティが値として受け取る型のオブジェクト要素です。 コンテンツを指定した後は、終了タグを持つ property 要素を閉じる必要があります。 終了タグの`</`構文は、 *typeName*`.`*propertyName*`>`です。  
  
 属性構文が可能な場合は、通常、属性構文を使用する方が便利で、よりコンパクトなマークアップが可能ですが、多くの場合、技術的な制限はありません。 次の例では、前の属性構文の例でと同じプロパティが設定されてい`Button`ますが、今回はのすべてのプロパティに対してプロパティ要素構文を使用します。  
  
 [!code-xaml[XAMLOvwSupport#BlueRedButtonPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbuttonpe)]  
  
### <a name="collection-syntax"></a>コレクションの構文  
 XAML 言語には、より人間が判読できるマークアップを生成するいくつかの最適化が含まれています。 このような最適化の1つとして、特定のプロパティがコレクション型を受け取る場合、そのプロパティの値内の子要素としてマークアップで宣言する項目がコレクションの一部になります。 この場合、子オブジェクト要素のコレクションは、コレクションプロパティに設定されている値になります。  
  
 次の例は、 <xref:System.Windows.Media.GradientBrush.GradientStops%2A>プロパティの値を設定するためのコレクション構文を示しています。  
  
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
 XAML では、そのプロパティの1つを XAML コンテンツプロパティとして指定できる言語機能を指定します。 そのオブジェクト要素の子要素は、そのコンテンツプロパティの値を設定するために使用されます。 つまり、コンテンツプロパティが一意になるように、XAML マークアップでそのプロパティを設定するときにプロパティ要素を省略し、マークアップ内でより参照可能な親/子のメタファを生成することができます。  
  
 たとえば、は<xref:System.Windows.Controls.Border> 、の<xref:System.Windows.Controls.Decorator.Child%2A>コンテンツプロパティを指定します。 次の 2 <xref:System.Windows.Controls.Border>つの要素は、同じように扱われます。 最初の1つは、コンテンツプロパティの構文を利用し`Border.Child` 、property 要素を省略します。 2つ目は`Border.Child` 、明示的に表示されます。  
  
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
  
 XAML 言語の規則として、XAML コンテンツプロパティの値は、そのオブジェクト要素の他のプロパティ要素の前または全体のいずれかに指定する必要があります。 たとえば、次のマークアップはコンパイルされません。  
  
```xaml
<Button>I am a   
  <Button.Background>Blue</Button.Background>  
  blue button</Button>  
```  
  
 XAML コンテンツプロパティに対するこの制限の詳細については、「xaml[構文の詳細](xaml-syntax-in-detail.md)」の「xaml コンテンツのプロパティ」セクションを参照してください。  
  
### <a name="text-content"></a>テキストコンテンツ  
 XAML 要素の数が少ないと、テキストをコンテンツとして直接処理できます。 これを有効にするには、次のいずれかのケースが満たされている必要があります。  
  
- クラスはコンテンツプロパティを宣言する必要があり、そのコンテンツプロパティは文字列に割り当てることができる型である必要が<xref:System.Object>あります (型である可能性があります)。 たとえば<xref:System.Windows.Controls.ContentControl> 、はコンテンツプロパティ<xref:System.Windows.Controls.ContentControl.Content%2A>としてを使用し、は<xref:System.Object>型です`<Button>Hello</Button>`。これにより、などの実用<xref:System.Windows.Controls.ContentControl> <xref:System.Windows.Controls.Button>的なで次の使用がサポートされます。  
  
- 型は型コンバーターを宣言する必要があります。この場合、テキストの内容は、その型コンバーターの初期化テキストとして使用されます。 たとえば、`<Brush>Blue</Brush>` のようにします。 この場合、実際にはあまり一般的ではありません。  
  
- 型は、既知の XAML 言語プリミティブである必要があります。  
  
### <a name="content-properties-and-collection-syntax-combined"></a>コンテンツのプロパティとコレクション構文の組み合わせ  
 次の例について考えます。  
  
```xaml  
<StackPanel>  
  <Button>First Button</Button>  
  <Button>Second Button</Button>  
</StackPanel>  
```  
  
 ここでは<xref:System.Windows.Controls.Button> 、それぞれがの<xref:System.Windows.Controls.StackPanel>子要素です。 これは、2つの異なる理由から2つのタグを除外する、合理化された直感的なマークアップです。  
  
- **StackPanel プロパティ要素を省略します。** <xref:System.Windows.Controls.StackPanel> から<xref:System.Windows.Controls.Panel>派生します。 <xref:System.Windows.Controls.Panel>を<xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType> XAML コンテンツプロパティとして定義します。  
  
- **UIElementCollection object 要素を省略します。** プロパティ<xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType>は、を実装<xref:System.Windows.Controls.UIElementCollection> <xref:System.Collections.IList>する型を受け取ります。 コレクションの要素タグは、などのコレクション<xref:System.Collections.IList>を処理する XAML ルールに基づいて省略できます。 (この場合、パラメーター <xref:System.Windows.Controls.UIElementCollection>なしのコンストラクターが公開されていないため、実際にインスタンス化すること<xref:System.Windows.Controls.UIElementCollection>はできません。また、オブジェクト要素がコメントアウトされて表示されます)。  
  
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
 属性構文は、プロパティではなくイベントであるメンバーに対しても使用できます。 この場合、属性の名前はイベントの名前です。 XAML のイベントの WPF 実装では、属性の値は、そのイベントのデリゲートを実装するハンドラーの名前です。 たとえば、次のマークアップは、マークアップで<xref:System.Windows.Controls.Primitives.ButtonBase.Click> <xref:System.Windows.Controls.Button>作成されたにイベントのハンドラーを割り当てます。  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]  
  
 WPF のイベントと XAML には、属性構文のこの例だけではありません。 たとえば、ここで参照されて`ClickHandler`いるがどのように表され、どのように定義されているかがわかります。 これについては、このトピックの「今後の[イベントと XAML の分離コード](xaml-overview-wpf.md#events_and_xaml_codebehind)」セクションで説明します。  
  
<a name="case_and_white space_in_xaml"></a>   
## <a name="case-and-white-space-in-xaml"></a>XAML の大文字と小文字と空白  
 XAML は、一般に大文字と小文字を区別します。 バッキング型を解決するために、WPF XAML では、CLR で大文字と小文字が区別されるのと同じ規則によって大文字と小文字が区別されます。 オブジェクト要素、プロパティ要素、および属性名は、名前によってアセンブリ内の基になる型または型のメンバーに比較するときに、常に区別される大文字と小文字の区別を使用して指定する必要があります。 XAML 言語のキーワードとプリミティブでも大文字と小文字が区別されます。 値は常に大文字小文字を区別しません。 値の大文字と小文字の区別は、値を受け取るプロパティに関連付けられている型コンバーターの動作、またはプロパティ値の型によって異なります。 <xref:System.Boolean>たとえば、型を取得するプロパティは、同等の値`True`としてまたはのどちらか`true`を受け取ることができます。ただし、 <xref:System.Boolean> string のネイティブ WPF XAML パーサーの型変換では、これらが同等として既に許可されているためです。  
  
 WPF XAML プロセッサおよびシリアライザーは、すべての重要でない空白文字を無視または削除し、有意の空白を正規化します。 これは、XAML 仕様の既定の空白動作に関する推奨事項と一致します。 この動作は、通常、XAML コンテンツプロパティ内で文字列を指定した場合にのみ、結果として使用されます。 単純に、XAML では、スペース、改行、およびタブ文字をスペースに変換した後、連続する文字列の両端で1つのスペースを保持します。 XAML の空白の処理の詳細については、このトピックでは説明しません。 詳細については、「 [XAML での空白の処理](../../xaml-services/whitespace-processing-in-xaml.md)」を参照してください。  
  
<a name="markup_extensions"></a>   
## <a name="markup-extensions"></a>マークアップ拡張機能  
 マークアップ拡張機能は、XAML 言語の概念です。 属性構文の値を指定するために使用する場合、中`{`かっこ`}`(および) はマークアップ拡張機能の使用を示します。 この使用法は、リテラル文字列または文字列変換可能な値のいずれかとして、属性値の一般的な処理からエスケープするように XAML 処理を指示します。  
  
 アプリケーション[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]プログラミングで使用される最も一般的なマークアップ拡張は[バインド](binding-markup-extension.md)で、データバインディング式に使用され、リソースは[StaticResource](staticresource-markup-extension.md)および[dynamicresource](dynamicresource-markup-extension.md)を参照します。 マークアップ拡張機能を使用すると、属性構文を使用して、プロパティが一般に属性構文をサポートしていない場合でも、プロパティの値を指定できます。 マークアップ拡張機能では、多くの場合、中間の式の型を使用して、値の遅延や、実行時にのみ存在する他のオブジェクトの参照などの機能を有効にします。  
  
 たとえば、次のマークアップは、属性構文を<xref:System.Windows.FrameworkElement.Style%2A>使用してプロパティの値を設定します。 プロパティ<xref:System.Windows.FrameworkElement.Style%2A>は、 <xref:System.Windows.Style>クラスのインスタンスを取得します。このクラスは、既定では、属性構文文字列によってインスタンス化できませんでした。 ただし、この場合、属性は特定のマークアップ拡張機能[StaticResource](staticresource-markup-extension.md)を参照します。 このマークアップ拡張機能が処理されると、リソースディクショナリのキー付きリソースとして既にインスタンス化されていたスタイルへの参照が返されます。  
  
 [!code-xaml[FEResourceSH_snip#XAMLOvwShortResources](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources)]  
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources2](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources2)]  
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources3](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources3)]  
  
 WPF で特に実装される XAML のすべてのマークアップ拡張機能のリファレンスリストについては、「 [WPF Xaml 拡張機能](wpf-xaml-extensions.md)」を参照してください。 .Xaml によって定義されているマークアップ拡張機能のリファレンスリストについては、「xaml 名前空間 ( [x:)」を参照してください .NET Framework。言語機能](../../xaml-services/xaml-namespace-x-language-features.md)。 マークアップ拡張機能の概念の詳細については、「[マークアップ拡張機能と WPF XAML](markup-extensions-and-wpf-xaml.md)」を参照してください。  
  
<a name="type_converters"></a>   
## <a name="type-converters"></a>型コンバーター  
 Brief セクションの[XAML 構文](xaml-overview-wpf.md#xaml_syntax_in_brief)では、属性値を文字列で設定できる必要があることが示されていました。 文字列を他のオブジェクト型またはプリミティブ値に変換する方法の基本的なネイティブな処理は<xref:System.String> 、型自体に加えて、や<xref:System.Uri>など<xref:System.DateTime>の特定の型のネイティブ処理に基づいています。 ただし、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]これらの型の多くの型またはメンバーは、文字列と属性としてより複雑なオブジェクト型のインスタンスを指定できるように、基本的な文字列属性処理動作を拡張します。  
  
 <xref:System.Windows.Thickness>構造体は、XAML の使用に対して型変換が有効になっている型の例です。 <xref:System.Windows.Thickness>入れ子になった四角形内の測定値を示し<xref:System.Windows.FrameworkElement.Margin%2A>ます。などのプロパティの値として使用されます。 型コンバーターをに<xref:System.Windows.Thickness>配置すると、を<xref:System.Windows.Thickness>使用するすべてのプロパティは、属性として指定できるため、XAML で簡単に指定できます。 次の例では、型変換と属性構文を使用して、 <xref:System.Windows.FrameworkElement.Margin%2A>の値を指定しています。  
  
 [!code-xaml[XAMLOvwSupport#MarginTCE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#margintce)]  
  
 前の属性構文の例は、次のより詳細な構文の例に<xref:System.Windows.FrameworkElement.Margin%2A>相当します。ここで、は、 <xref:System.Windows.Thickness>オブジェクト要素を含む property 要素構文によって設定されます。 の4つの<xref:System.Windows.Thickness>主要なプロパティは、新しいインスタンスの属性として設定されます。  
  
 [!code-xaml[XAMLOvwSupport#MarginVerbose](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#marginverbose)]  
  
> [!NOTE]
> 型自体にパラメーターなしのコンストラクターがないため、型変換がサブクラスを使用せずにその型にプロパティを設定する唯一のパブリックな方法であるオブジェクトの数も制限されています。 たとえば、の<xref:System.Windows.Input.Cursor>ようになります。  
  
 型変換と属性構文の使用方法の詳細については、「 [TypeConverters AND XAML](typeconverters-and-xaml.md)」を参照してください。  
  
<a name="xaml_root_elements_and_xaml_namespaces"></a>   
## <a name="xaml-root-elements-and-xaml-namespaces"></a>XAML ルート要素と XAML 名前空間  
 Xaml ファイルは、適切な形式[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]のファイルと有効な XAML ファイルの両方にするために、ルート要素を1つだけ持つ必要があります。 一般的な wpf のシナリオでは、wpf アプリケーションモデルで目立つ意味を持つルート要素を使用します (たとえば<xref:System.Windows.Window> 、 <xref:System.Windows.Controls.Page>ページ<xref:System.Windows.ResourceDictionary>の場合は、外部ディクショナリ<xref:System.Windows.Application>の場合は、アプリケーション定義の場合は)。 次の例は、の[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page>ルート要素を使用して、ページの一般的な XAML ファイルのルート要素を示しています。  
  
 [!code-xaml[XAMLOvwSupport#RootOnly](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly)]  
[!code-xaml[XAMLOvwSupport#RootOnly2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly2)]  
  
 ルート要素には、属性`xmlns`と`xmlns:x`も含まれます。 これらの属性は XAML プロセッサに対して、マークアップが要素として参照するバッキング型の型定義を含む XAML 名前空間を示します。 属性`xmlns`は、特に既定の XAML 名前空間を示します。 既定の XAML 名前空間内では、マークアップ内のオブジェクト要素をプレフィックスなしで指定できます。 ほとんどの [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーション シナリオとで示す例のほぼすべての [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のセクションでは、 [!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)] 、既定の XAML 名前空間にマップされて、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 名前空間 [!INCLUDE[TLA#tla_wpfxmlnsv1](../../../../includes/tlasharptla-wpfxmlnsv1-md.md)] 。 `xmlns:x`属性は XAML 名前空間が追加され、XAML 言語の名前空間のマップを示します [!INCLUDE[TLA#tla_xamlxmlnsv1](../../../../includes/tlasharptla-xamlxmlnsv1-md.md)] します。  
  
 の`xmlns`この使用方法は、名前スコープの使用とマッピングのスコープを定義するために、XML 1.0 仕様と一致します。 Xaml 名前スコープは、XML 名前スコープとは異なります。 xaml 名前スコープは、型の解決および XAML の解析に関して、型によって名前スコープの要素がどのようにサポートされるかについても意味します。  
  
 属性は、 `xmlns`各 XAML ファイルのルート要素に対してのみ厳密に必要であることに注意してください。 `xmlns`定義は、ルート要素のすべての子孫要素に適用されます (この動作は、の`xmlns`XML 1.0 仕様と同じになります)。`xmlns`属性は、ルートの下にある他の要素でも許可され、定義要素の子孫要素に適用されます。 ただし、XAML 名前空間を頻繁に定義または再定義すると、XAML マークアップスタイルが読みにくくなる可能性があります。  
  
 XAML [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]プロセッサの実装には、WPF コアアセンブリを認識するインフラストラクチャが含まれています。 コアアセンブリには、既定の XAML 名前空間への[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]マッピングをサポートする型が含まれていることがわかっています。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] これは、プロジェクトビルドファイルの一部である構成と、WPF ビルドおよびプロジェクトシステムによって有効になります。 したがって、既定の xaml 名前空間を既定`xmlns`として宣言することは、アセンブリから[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]の xaml 要素を参照するために必要なすべてのものです。  
  
### <a name="the-x-prefix"></a>X: プレフィックス  
 前のルート要素例プレフィックス`x:`XAML 名前空間をマップするために使用された [!INCLUDE[TLA#tla_xamlxmlnsv1](../../../../includes/tlasharptla-xamlxmlnsv1-md.md)] 、これは XAML 言語をサポートする専用の XAML 名前空間を構築します。 このプレフィックスは、この XAML 名前空間をプロジェクトのテンプレート、例、およびドキュメント[!INCLUDE[TLA2#tla_sdk](../../../../includes/tla2sharptla-sdk-md.md)]でマッピングするために使用されます。 `x:` Xaml 言語の XAML 名前空間には、XAML で非常に頻繁に使用するプログラミング構成要素がいくつか含まれています。 次に、使用する最も一般的な`x:`プレフィックスのプログラミング構成要素の一覧を示します。  
  
- [x:Key](../../xaml-services/x-key-directive.md):<xref:System.Windows.ResourceDictionary> (または他のフレームワークの同様の辞書の概念) の各リソースに一意のキーを設定します。 `x:Key`通常の WPF アプリケーションのマークアップに`x:`表示される使用量の 90% が考慮されます。  
  
- [x:Class](../../xaml-services/x-class-directive.md):XAML ページの分離コードを提供するクラスの CLR 名前空間とクラス名を指定します。 WPF プログラミングモデルごとの分離コードをサポートするには、このようなクラスが必要です。したがって`x:` 、リソースがない場合でも、ほとんどの場合、マップされていることがわかります。  
  
- [x:Name](../../xaml-services/x-name-directive.md):オブジェクト要素が処理された後に実行時コードに存在するインスタンスのランタイムオブジェクト名を指定します。 一般に、 [x:Name](../../xaml-services/x-name-directive.md)には WPF で定義された同等のプロパティを頻繁に使用します。 このようなプロパティは、特に CLR バッキングプロパティにマップされるため、アプリケーションプログラミングで便利です。この場合、初期化された XAML から名前付き要素を検索するために、実行時のコードを頻繁に使用します。 最も一般的なプロパティは<xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>です。 同等の WPF フレームワークレベル<xref:System.Windows.FrameworkElement.Name%2A>のプロパティが特定の型でサポートされていない場合でも、[x:Name](../../xaml-services/x-name-directive.md) を使用できます。 これは、特定のアニメーションシナリオで発生します。  
  
- [x:Static](../../xaml-services/x-static-markup-extension.md):それ以外の場合は、XAML と互換性のあるプロパティではない静的な値を返す参照を有効にします。  
  
- [x:Type](../../xaml-services/x-type-markup-extension.md):型名<xref:System.Type>に基づいて参照を構築します。 これは、など<xref:System.Type>の属性<xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>を指定するために使用されます。ただし、 [x:Type](../../xaml-services/x-type-markup-extension.md)マークアップ拡張機能の使用がオプションであるように、プロパティには<xref:System.Type>ネイティブの文字列変換が含まれることがよくあります。  
  
 `x:`プレフィックス/XAML 名前空間には、一般的ではないプログラミング構成要素が追加されています。 詳細について[は、「XAML 名前空間 (x:)」を参照してください。言語機能](../../xaml-services/xaml-namespace-x-language-features.md)。  
  
<a name="custom_prefixes_and_custom_types_in_xaml"></a>   
## <a name="custom-prefixes-and-custom-types-in-xaml"></a>XAML でのカスタムプレフィックスとカスタム型  
 独自のカスタムアセンブリ、またはプレゼンテーションコア、プレゼンテーションフレームワーク、および windowsbase の WPF コアの外部にあるアセンブリの場合、アセンブリをカスタム`xmlns`マッピングの一部として指定できます。 その後、XAML でそのアセンブリの型を参照できます。ただし、その型が正しく実装されている限り、試行する XAML の使用をサポートすることができます。  
  
 次に、XAML マークアップでのカスタムプレフィックスの動作の基本的な例を示します。 プレフィックス`custom`は、ルート要素タグで定義され、アプリケーションでパッケージ化され、使用可能な特定のアセンブリにマップされます。 このアセンブリには型`NumericUpDown`が含まれています。この型は、xaml の一般的な使用をサポートするために実装されています。また、WPF xaml コンテンツモデルの特定のポイントで挿入を許可するクラスの継承を使用することもできます。 この`NumericUpDown`コントロールのインスタンスは、オブジェクト要素として宣言されます。これは、xaml パーサーがどの xaml 名前空間に型が含まれているかを認識し、そのためバッキングアセンブリに型定義が含まれていることを示します。  
  
```xaml
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
  
 XAML におけるカスタム型の詳細については、「 [WPF の xaml およびカスタムクラス](xaml-and-custom-classes-for-wpf.md)」を参照してください。  
  
 アセンブリ内のバッキングコードの XML 名前空間と名前空間の関連付けの詳細については、「 [WPF xaml の Xaml 名前空間と名前空間の割り当て](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)」を参照してください。  
  
<a name="events_and_xaml_codebehind"></a>   
## <a name="events-and-xaml-code-behind"></a>イベントと XAML 分離コード  
 ほとんど[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]のアプリケーションは、XAML マークアップと分離コードの両方で構成されています。 プロジェクト内では、XAML は`.xaml`ファイルとして記述され、Microsoft Visual Basic やC#などの CLR 言語が分離コードファイルの書き込みに使用されます。 Xaml ファイルが WPF プログラミングモデルとアプリケーションモデルの一部としてコンパイルされている場合、xaml ファイルの xaml 分離コードファイルの場所は、xaml のルート要素の`x:Class`属性として名前空間とクラスを指定することによって識別されます。  
  
 ここまでの例ではいくつかのボタンが表示されていましたが、これらのボタンのいずれにも論理動作が関連付けられていませんでした。 オブジェクト要素の動作を追加するための主要なアプリケーションレベルのメカニズムは、要素クラスの既存のイベントを使用し、実行時にそのイベントが発生したときに呼び出されるイベントの特定のハンドラーを記述することです。 イベント名と使用するハンドラーの名前はマークアップで指定されますが、ハンドラーを実装するコードは分離コードで定義されます。  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]  
  
 [!code-csharp[XAMLOvwSupport#ButtonWithCodeBehindHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml.cs#buttonwithcodebehindhandler)]
 [!code-vb[XAMLOvwSupport#ButtonWithCodeBehindHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#buttonwithcodebehindhandler)]  
  
 分離コードファイルは CLR 名前空間`ExampleNamespace`を使用し、その名前空間内の部分クラスとしてを宣言`ExamplePage`していることに注意してください。 これは、 `x:Class`の`ExampleNamespace`属性値と同じです。`ExamplePage` これはマークアップルートで提供されました。 WPF マークアップコンパイラは、ルート要素型からクラスを派生することによって、コンパイルされた XAML ファイルの部分クラスを作成します。 同じ部分クラスも定義する分離コードを指定すると、生成されるコードは、コンパイル済みアプリケーションの同じ名前空間とクラス内で結合されます。  
  
 WPF での分離コードプログラミングの要件の詳細については、「 [wpf の分離コードと XAML](code-behind-and-xaml-in-wpf.md)」の「分離コード、イベントハンドラー、および部分クラスの要件」セクションを参照してください。  
  
 分離コードファイルを作成しない場合は、XAML ファイルでコードをインライン化することもできます。 ただし、インラインコードは、大幅な制限がある、汎用性の低い手法です。 詳細については、「[WPF における分離コードと XAML](code-behind-and-xaml-in-wpf.md)」を参照してください。  
  
### <a name="routed-events"></a>ルーティングイベント  
 の基礎[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]となる特定のイベント機能は、ルーティングイベントです。 ルーティングイベントを使用すると、要素がツリーリレーションシップによって接続されている限り、別の要素によって発生したイベントを要素で処理できます。 XAML 属性を使用してイベント処理を指定する場合、ルーティングイベントは、クラスメンバーテーブル内の特定のイベントを一覧表示しない要素など、任意の要素に対してリッスンおよび処理することができます。 これは、イベント名属性を所有クラス名で修飾することで実現されます。 `StackPanel`たとえば、実行中`StackPanel`  /  <xref:System.Windows.Controls.Primitives.ButtonBase.Click>の例の親は、の`Button.Click` 属性を指定することによって、子要素ボタンのイベントのハンドラーを登録できます。`StackPanel` `Button`オブジェクト要素。ハンドラー名を属性値として指定します。 ルーティングイベントの動作の詳細については、「[ルーティングイベントの概要](routed-events-overview.md)」を参照してください。  
  
<a name="x_name_and_xaml_named_elements"></a>   
## <a name="xaml-named-elements"></a>XAML の名前付き要素  
 既定では、XAML オブジェクト要素を処理することによってオブジェクトグラフに作成されたオブジェクトインスタンスには、一意の識別子またはオブジェクト参照がありません。 これに対して、コードでコンストラクターを呼び出す場合、ほとんどの場合、コンストラクターの結果を使用して、作成されたインスタンスに変数を設定します。これにより、後でコードのインスタンスを参照できるようになります。 マークアップ定義によって作成されたオブジェクトへの標準化されたアクセスを提供するために、XAML は[x:Name 属性](../../xaml-services/x-name-directive.md)を定義します。 任意のオブジェクト要素の`x:Name`属性の値を設定できます。 分離コードでは、選択した識別子は、構築されたインスタンスを参照するインスタンス変数に相当します。 あらゆる点で、名前付き要素はオブジェクトインスタンスであるかのように機能します (名前はそのインスタンスを参照します)。分離コードは、名前付き要素を参照して、アプリケーション内での実行時のやり取りを処理できます。 このインスタンスと変数間の接続は、WPF XAML マークアップコンパイラによって実現されます。具体的に<xref:System.Windows.Markup.IComponentConnector.InitializeComponent%2A>は、このトピックで詳しく説明されていない機能やパターンについても説明します。  
  
 WPF フレームワークレベルの xaml 要素は、 <xref:System.Windows.FrameworkElement.Name%2A>プロパティを継承します。これは、 `x:Name` xaml で定義された属性に相当します。 また、特定のプロパティ`x:Name` `Name`としても定義されている、のプロパティレベルの同等のクラスも用意されています。 一般に、選択した要素/ `Name`型の members テーブルでプロパティが見つからない場合は、代わりに`x:Name`を使用します。 値`x:Name`は、特定のサブシステムまたはなどのユーティリティメソッド<xref:System.Windows.FrameworkElement.FindName%2A>によって実行時に使用できる XAML 要素の識別子を提供します。  
  
 次の例<xref:System.Windows.Controls.StackPanel>で<xref:System.Windows.FrameworkElement.Name%2A>は、要素にを設定します。 次に、によっ<xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.StackPanel> `buttonContainer` <xref:System.Windows.Controls.StackPanel> て設定されたインスタンス参照を介してを参照する、内<xref:System.Windows.FrameworkElement.Name%2A>ののハンドラー。  
  
 [!code-xaml[XAMLOvwSupport#NamedE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede)]  
[!code-xaml[XAMLOvwSupport#NamedE2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede2)]  
  
 [!code-csharp[XAMLOvwSupport#NameCode](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml.cs#namecode)]
 [!code-vb[XAMLOvwSupport#NameCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#namecode)]  
  
 変数と同じように、インスタンスの XAML 名はスコープの概念によって管理されるので、予測可能な特定のスコープ内で名前を一意にすることができます。 ページを定義するプライマリマークアップは、1つの一意の XAML 名前スコープを意味します。 XAML 名前スコープの境界は、そのページのルート要素です。 ただし、他のマークアップソースは、スタイル内のスタイルやテンプレートなど、実行時にページと対話できます。また、多くの場合、このようなマークアップソースには、ページの XAML 名前スコープとは必ずしも接続しない独自の XAML 名前スコープがあります。 `x:Name`および XAML 名前スコープの詳細について<xref:System.Windows.FrameworkElement.Name%2A>は、「」、「 [x:Name ディレクティブ](../../xaml-services/x-name-directive.md)」、または「 [WPF xaml 名前スコープ](wpf-xaml-namescopes.md)」を参照してください。  
  
<a name="attached_properties_and_attached_events"></a>   
## <a name="attached-properties-and-attached-events"></a>添付プロパティと添付イベント  
 XAML は、プロパティまたはイベントが設定されている要素の型の定義に存在するかどうかにかかわらず、任意の要素で特定のプロパティまたはイベントを指定できるようにする言語機能を指定します。 この機能のプロパティのバージョンは添付プロパティと呼ばれ、イベントのバージョンは添付イベントと呼ばれます。 概念的には、添付プロパティと添付イベントは、任意の XAML 要素/オブジェクトインスタンスに設定できるグローバルメンバーと考えることができます。 ただし、その要素/クラスまたはより大規模なインフラストラクチャでは、添付値のバッキングプロパティストアがサポートされている必要があります。  
  
 XAML の添付プロパティは、通常、属性構文を通じて使用されます。 属性構文では、添付プロパティを*ownerType*の形式で指定します。*propertyName*。  
  
 、一見、はプロパティ要素の使用法に似ていますが、この場合、指定する*ownerType*は、添付プロパティが設定されているオブジェクト要素とは常に異なる型になります。 *ownerType*は、添付プロパティ値を取得または設定するために XAML プロセッサで必要とされるアクセサーメソッドを提供する型です。  
  
 添付プロパティの最も一般的なシナリオは、子要素が親要素にプロパティ値を報告できるようにすることです。  
  
 添付プロパティの<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>例を次に示します。 クラス<xref:System.Windows.Controls.DockPanel>は、の<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>アクセサーを定義するため、添付プロパティを所有します。 また<xref:System.Windows.Controls.DockPanel> 、クラスには、子要素を反復処理し、各要素がの<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>セット値をチェックするロジックも含まれます。 値が見つかった場合、その値はレイアウト中に子要素を配置するために使用されます。 添付プロパティを使用すると、この配置機能は実際には<xref:System.Windows.Controls.DockPanel>クラスのスタブシナリオになります。 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>  
  
 [!code-xaml[XAMLOvwSupport#DockAP](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#dockap)]  
  
 で[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は、添付プロパティのほとんどまたはすべてが依存関係プロパティとして実装されます。 詳細については、「[添付プロパティの概要](attached-properties-overview.md)」を参照してください。  
  
 添付イベントでは、同様の*ownerType*が使用されます。属性構文の*eventName*フォーム。 アタッチされていないイベントと同様に、XAML の添付イベントの属性値は、要素でイベントが処理されるときに呼び出されるハンドラーメソッドの名前を指定します。 WPF XAML での添付イベントの使用はあまり一般的ではありません。 詳細については、「[添付イベントの概要](attached-events-overview.md)」を参照してください。  
  
<a name="base_classes_and_xaml"></a>   
## <a name="base-types-and-xaml"></a>基本型と XAML  
 基になる WPF XAML とその XAML 名前空間は、XAML のマークアップ要素に加えて、CLR オブジェクトに対応する型のコレクションです。 ただし、すべてのクラスを要素にマップできるわけではありません。 などの抽象クラス<xref:System.Windows.Controls.Primitives.ButtonBase>や、CLR オブジェクトモデルでの継承には、特定の非抽象基底クラスが使用されます。 抽象型のクラスは、具象 XAML の各要素がその階層内の基底クラスからメンバーを継承するため、XAML 開発にも重要です。 多くの場合、これらのメンバーには、要素の属性として設定できるプロパティや、処理できるイベントが含まれます。 <xref:System.Windows.FrameworkElement>は、WPF フレームワーク[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]レベルの[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]の具象基本クラスです。 デザイン[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]時には、さまざまな図形、パネル、デコレータ、またはコントロールクラスを使用します<xref:System.Windows.FrameworkElement>。これらはすべてから派生します。 関連する基本クラス<xref:System.Windows.FrameworkContentElement>は、の<xref:System.Windows.FrameworkElement>api を意図的にミラー化する api を使用して、フローレイアウトプレゼンテーションに適したドキュメント指向の要素をサポートします。 要素レベルと CLR オブジェクトモデルの属性の組み合わせにより、特定の XAML 要素とその基になる型に関係なく、ほとんどの具象 XAML 要素に対して設定可能な共通プロパティのセットが提供されます。  
  
<a name="xaml_security"></a>   
## <a name="xaml-security"></a>XAML のセキュリティ  
 XAML は、オブジェクトのインスタンス化と実行を直接表すマークアップ言語です。 そのため、XAML で作成された要素は、同じように生成されたコードと同じように、システムリソース (ネットワークアクセス、ファイルシステム IO など) と対話することができます。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]では、.NET Framework 4 セキュリティフレームワークのコードアクセスセキュリティ (CAS) がサポートされています。 これは、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]インターネットゾーンで実行されているコンテンツの実行アクセス許可が低下していることを意味します。 "疎 xaml" (xaml ビューアーによって読み込み時に解釈[!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)]される、コンパイルされていない xaml のページ)。通常は、このインターネットゾーンで実行され、同じアクセス許可セットを使用します。  ただし、完全に信頼されたアプリケーションに読み込まれる XAML は、ホストアプリケーションと同じようにシステムリソースにアクセスできます。 詳細については、「 [WPF 部分信頼セキュリティ](../wpf-partial-trust-security.md)」を参照してください。  
  
<a name="loading_xaml_from_code"></a>   
## <a name="loading-xaml-from-code"></a>コードからの XAML の読み込み  
 XAML は、すべての UI を定義するために使用できますが、XAML で UI の一部だけを定義することが適切な場合もあります。 この機能を使用すると、部分的なカスタマイズ、情報のローカルストレージ、XAML を使用したビジネスオブジェクトの提供、またはさまざまなシナリオに対応できます。 これらのシナリオにとって重要<xref:System.Windows.Markup.XamlReader>なのは<xref:System.Windows.Markup.XamlReader.Load%2A> 、クラスとそのメソッドです。 入力は XAML ファイルで、出力は、そのマークアップから作成されたオブジェクトのすべての実行時ツリーを表すオブジェクトです。 その後、オブジェクトを挿入して、アプリケーションに既に存在する別のオブジェクトのプロパティにすることができます。 プロパティがコンテンツモデル内の適切なプロパティであり、最終的な表示機能があり、新しいコンテンツがアプリケーションに追加されたことを実行エンジンに通知する場合は、実行中のアプリケーションの内容を非常に簡単に変更できます。XAML で読み込みます。 この機能は通常、完全に信頼されたアプリケーションでのみ使用できます。これは、ファイルを実行時にアプリケーションに読み込むことによってセキュリティが明らかに影響するためです。  
  
<a name="whats_next"></a>   
## <a name="whats-next"></a>次の内容  
 このトピックでは、WPF に適用される XAML 構文の概念と用語の基本的な概要について説明します。 ここで使用される用語の詳細については、「 [XAML 構文の詳細](xaml-syntax-in-detail.md)」を参照してください。  
  
 まだ行っていない場合は、チュートリアルのトピック「 [チュートリアル:初めての WPF デスクトップ](../getting-started/walkthrough-my-first-wpf-desktop-application.md)アプリケーション。 このチュートリアルで説明されているマークアップ中心のアプリケーションを作成する場合は、このトピックで説明する多くの概念を補強することができます。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は、 <xref:System.Windows.Application>クラスに基づく特定のアプリケーションモデルを使用します。 詳細については、「[アプリケーション管理の概要](../app-development/application-management-overview.md)」を参照してください。  
  
 [WPF アプリケーションを](../app-development/building-a-wpf-application-wpf.md)ビルドすると、コマンドラインおよびを使用して、XAML 包括アプリケーションを構築する[!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]方法についての詳細情報を得ることができます。  
  
 [依存関係プロパティの概要](dependency-properties-overview.md)で[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は、のプロパティの汎用性に関する詳細情報が提供され、依存関係プロパティの概念が導入されています。  
  
## <a name="see-also"></a>関連項目

- [XAML 構文の詳細](xaml-syntax-in-detail.md)
- [WPF における XAML とカスタム クラス](xaml-and-custom-classes-for-wpf.md)
- [XAML 名前空間 (x:)言語機能](../../xaml-services/xaml-namespace-x-language-features.md)
- [WPF XAML 拡張機能](wpf-xaml-extensions.md)
- [基本要素の概要](base-elements-overview.md)
- [WPF のツリー](trees-in-wpf.md)
