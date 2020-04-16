---
title: XAML 概要
description: XAML 言語が構成され、.NET コアの Windows プレゼンテーション ファンデーション (WPF) によって実装される方法について説明します。
author: thraka
ms.date: 08/08/2019
ms.author: adegeo
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
ms.openlocfilehash: b0a9357b623fbde08731a5b1ddb8fee3a93824c2
ms.sourcegitcommit: 515469828d0f040e01bde01df6b8e4eb43630b06
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2020
ms.locfileid: "81433002"
---
# <a name="xaml-overview-in-wpf"></a>WPF の XAML の概要

この記事では、XAML 言語の機能について説明し、XAML を使用して Windows プレゼンテーション ファンデーション (WPF) アプリを作成する方法を示します。 この記事では、WPF によって実装される XAML について具体的に説明します。 XAML 自体は、WPF よりも大きな言語概念です。

[!INCLUDE [desktop guide under construction](../../../includes/desktop-guide-preview-note.md)]

## <a name="what-is-xaml"></a>XAML とは

XAML は宣言型マークアップ言語です。 .NET Core プログラミング モデルに適用される XAML では、.NET Core アプリの UI の作成が簡略化されます。 宣言型 XAML マークアップで表示可能な UI 要素を作成し、部分クラス定義を通じてマークアップに結合された分離コード ファイルを使用して、UI 定義をランタイム ロジックから分離できます。 XAML は、アセンブリで定義された特定のバッキング型のセット内のオブジェクトのインスタンス化を直接表します。 これは、他のほとんどのマークアップ言語とは異なり、通常は、このような直接の関連付けのない解釈言語で、バッキング型システムです。 XAML では、別のツールを使用して、別々のパーティがアプリの UI とロジックで作業できるワークフローが有効になります。

テキストとして表される場合、XAML ファイルは、通常は拡張子`.xaml`を持つ XML ファイルです。 ファイルは任意の XML エンコードでエンコードできますが、UTF-8 としてエンコードするのが一般的です。

次の例は、UI の一部としてボタンを作成する方法を示しています。 この例は、XAML が一般的な UI プログラミングメタファーを表す方法を示すことを目的としています (完全なサンプルではありません)。

[!code-xaml[XAMLOvwSupport#DirtSimple](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]

## <a name="xaml-syntax-in-brief"></a>簡単に XAML 構文

次のセクションでは、XAML 構文の基本的な形式について説明し、簡単なマークアップの例を示します。 これらのセクションは、バッキング型システムでの表記方法など、各構文形式に関する完全な情報を提供することを目的としていません。 XAML 構文の詳細については、「XAML[構文の詳細](../../framework/wpf/advanced/xaml-syntax-in-detail.md)」を参照してください。

XML 言語に慣れている場合は、次のいくつかのセクションの資料の多くが基本的なものになります。 これは、XAML の基本的な設計原則の 1 つに基づいています。 XAML 言語は独自の概念を定義しますが、これらの概念は XML 言語とマークアップ形式で機能します。

### <a name="xaml-object-elements"></a>XAML オブジェクト要素

オブジェクト要素は、通常、型のインスタンスを宣言します。 この型は、XAML を言語として使用するテクノロジによって参照されるアセンブリで定義されます。

オブジェクト要素構文は、常に始まる山かっこ`<`( ) で始まります。 この後に、インスタンスを作成する型の名前が続きます。 (名前には、後で説明する概念であるプレフィックスを含めることができます。この後、必要に応じてオブジェクト要素の属性を宣言できます。 オブジェクト要素タグを完成するには、終わりには右山かっこ`>`( ) を付けます。 代わりに、連続してスラッシュと終了山かっこでタグを入力することで、コンテンツを持たない自己閉鎖フォームを使用できます(`/>`) 。 たとえば、前に表示したマークアップ スニペットをもう一度見てください。

[!code-xaml[XAMLOvwSupport#DirtSimple](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#dirtsimple)]

これは、(コンテンツと終了`<StackPanel>`タグを後で)、および`<Button .../>`(自己閉じる形式、いくつかの属性を持つ)の2つのオブジェクト要素を指定します。 オブジェクト要素`StackPanel`と各`Button`マップは、WPF によって定義され、WPF アセンブリの一部であるクラスの名前に対応します。 オブジェクト要素タグを指定する場合は、XAML 処理の命令を作成して、基になる型の新しいインスタンスを作成します。 各インスタンスは、XAML の解析と読み込み時に、基になる型のパラメーターなしのコンストラクターを呼び出すことによって作成されます。

### <a name="attribute-syntax-properties"></a>属性構文 (プロパティ)

オブジェクトのプロパティは、多くの場合、オブジェクト要素の属性として表現できます。 属性構文では、設定されているオブジェクト プロパティの名前、その後に代入演算子 (=) を指定します。 属性の値は、常に引用符で囲まれた文字列として指定されます。

属性構文は、最も合理化されたプロパティ設定構文であり、過去にマークアップ言語を使用した開発者にとって最も直感的な構文です。 たとえば、次のマークアップは、次のように指定されたテキストを表示するほかに、赤いテキストと青の`Content`背景を持つボタンを作成します。

[!code-xaml[XAMLOvwSupport#BlueRedButton](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbutton)]

### <a name="property-element-syntax"></a>プロパティ要素構文

オブジェクト要素の一部のプロパティでは、プロパティ値を提供するために必要なオブジェクトまたは情報が、属性構文の引用符および文字列の制限内で適切に表現できないため、属性構文は使用できません。 このような場合は、プロパティ要素構文と呼ばれる別の構文を使用できます。

プロパティ要素開始タグの構文は です`<TypeName.PropertyName>`。 通常、そのタグの内容は、プロパティがその値として受け取る型のオブジェクト要素です。 コンテンツを指定した後、終了タグを使用してプロパティ要素を閉じる必要があります。 終了タグの構文は`</TypeName.PropertyName>`です。

属性構文が可能な場合、属性構文を使用する方が通常は便利で、よりコンパクトなマークアップが可能になりますが、多くの場合、技術的な制限ではなく、スタイルの問題です。 次の例では、前の属性構文の例と同じプロパティが設定されていますが、今回は プロパティ要素構文を使用して`Button`すべてのプロパティを使用しています。

[!code-xaml[XAMLOvwSupport#BlueRedButtonPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#blueredbuttonpe)]

### <a name="collection-syntax"></a>コレクション構文

XAML 言語には、人間が読み取り可能なマークアップを生成するいくつかの最適化が含まれています。 このような最適化の 1 つは、特定のプロパティがコレクション型を受け取る場合、マークアップで宣言する項目がそのプロパティの値内の子要素としてコレクションの一部になるということです。 この場合、子オブジェクト要素のコレクションは、コレクション プロパティに設定される値です。

プロパティの値を設定するためのコレクション構文を次の<xref:System.Windows.Media.GradientBrush.GradientStops%2A>例に示します。

```xaml
<LinearGradientBrush>
  <LinearGradientBrush.GradientStops>
    <!-- no explicit new GradientStopCollection, parser knows how to find or create -->
    <GradientStop Offset="0.0" Color="Red" />
    <GradientStop Offset="1.0" Color="Blue" />
  </LinearGradientBrush.GradientStops>
</LinearGradientBrush>
```

### <a name="xaml-content-properties"></a>XAML コンテンツ プロパティ

XAML は、クラスが XAML_コンテンツ_プロパティとしてそのプロパティの 1 つだけを指定できる言語機能を指定します。 そのオブジェクト要素の子要素は、そのコンテンツ プロパティの値を設定するために使用されます。 つまり、コンテンツ プロパティの場合は、XAML マークアップでそのプロパティを設定するときにプロパティ要素を省略し、マークアップで親子メタファを生成できます。

たとえば、<xref:System.Windows.Controls.Border>の_コンテンツ_プロパティを<xref:System.Windows.Controls.Decorator.Child%2A>指定します。 次の<xref:System.Windows.Controls.Border>2 つの要素は、同じように扱われます。 最初の 1 つは、コンテンツ プロパティの構文を利用`Border.Child`し、プロパティ要素を省略します。 2 番目の`Border.Child`図は明示的に示しています。

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

XAML 言語の規則として、XAML コンテンツ プロパティの値は、そのオブジェクト要素の他のプロパティ要素の前または後に完全に指定する必要があります。 たとえば、次のマークアップはコンパイルされません。

```xaml
<Button>I am a
  <Button.Background>Blue</Button.Background>
  blue button</Button>
```

XAML 構文の詳細については、「XAML[構文の詳細](../../framework/wpf/advanced/xaml-syntax-in-detail.md)」を参照してください。

### <a name="text-content"></a>テキストコンテンツ

少数の XAML 要素は、テキストをコンテンツとして直接処理できます。 これを有効にするには、次のケースのいずれかが true である必要があります。

- クラスは、コンテンツ プロパティを宣言する必要があり、そのコンテンツ プロパティは、文字列に割り当て可能な型<xref:System.Object>である必要があります ( 型は ) 。 <xref:System.Windows.Controls.ContentControl>たとえば、コンテンツ プロパティ<xref:System.Windows.Controls.ContentControl.Content%2A>として使用し、type を使用<xref:System.Object>すると、 <xref:System.Windows.Controls.ContentControl> <xref:System.Windows.Controls.Button>:`<Button>Hello</Button>`などの使用法がサポートされます。

- 型は型コンバーターを宣言する必要があります。 たとえば、`<Brush>Blue</Brush>`コンテンツ値をブラシ`Blue`に変換します。 このケースは実際にはあまり一般的ではありません。

- 型は、既知の XAML 言語プリミティブである必要があります。

### <a name="content-properties-and-collection-syntax-combined"></a>コンテンツ プロパティとコレクション構文の組み合わせ

この例を考えてみましょう。

```xaml
<StackPanel>
  <Button>First Button</Button>
  <Button>Second Button</Button>
</StackPanel>
```

ここでは、それぞれが<xref:System.Windows.Controls.Button>の子要素です<xref:System.Windows.Controls.StackPanel>。 これは、2 つの異なる理由で 2 つのタグを省略する、合理化された直感的なマークアップです。

- **省略された StackPanel.Children プロパティ要素:** <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.Controls.Panel>から派生します。 <xref:System.Windows.Controls.Panel>XAML<xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType>コンテンツ プロパティとして定義します。

- **省略された UIElement コレクションオブジェクト要素:** プロパティ<xref:System.Windows.Controls.Panel.Children%2A?displayProperty=nameWithType>は、 を<xref:System.Windows.Controls.UIElementCollection>実装する型を<xref:System.Collections.IList>受け取ります。 コレクションの要素タグは、コレクションを<xref:System.Collections.IList>処理するための XAML ルールに基づいて省略できます。 (この場合、<xref:System.Windows.Controls.UIElementCollection>実際には、パラメーターなしのコンストラクターを公開しないため、<xref:System.Windows.Controls.UIElementCollection>インスタンス化できません。

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

### <a name="attribute-syntax-events"></a>属性構文 (イベント)

属性構文は、プロパティではなくイベントであるメンバーにも使用できます。 この場合、属性の名前はイベントの名前です。 XAML のイベントの WPF 実装では、属性の値は、そのイベントのデリゲートを実装するハンドラーの名前です。 たとえば、次のマークアップは、マークアップで作成されたイベント<xref:System.Windows.Controls.Primitives.ButtonBase.Click>のハンドラーを<xref:System.Windows.Controls.Button>割り当てます。

[!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]

WPF のイベントと XAML には、この属性構文の例以外にも多くのものがあります。 たとえば、ここで参照されている内容と`ClickHandler`、その定義方法を疑問に思うかもしれません。 これについては、この記事の今後の[イベントと XAML 分離コード](#events-and-xaml-code-behind)セクションで説明します。

## <a name="case-and-white-space-in-xaml"></a>XAML の大文字と小文字と空白

一般に、XAML では大文字と小文字が区別されます。 バッキング型を解決するために、WPF XAML では、CLR で大文字と小文字が区別されるのと同じ規則で大文字と小文字が区別されます。 名前をアセンブリの基になる型または型のメンバーと比較する場合は、オブジェクト要素、プロパティ要素、および属性名をすべて、名前で比較する場合は、大文字と小文字を区別して指定する必要があります。 XAML 言語のキーワードとプリミティブも大文字と小文字を区別します。 値は、常に大文字と小文字を区別するわけではありません。 値の大文字と小文字の区別は、値を受け取るプロパティに関連付けられている型コンバーターの動作、またはプロパティ値の型によって異なります。 たとえば、<xref:System.Boolean>型を受け取るプロパティは、`true`いずれか`True`または同等の値として受け取ることができますが、文字列のネイティブ WPF <xref:System.Boolean> XAML パーサー型変換では、既に同等として許可されているためです。

WPF XAML プロセッサとシリアライザーは、重要でない空白をすべて無視または削除し、重要な空白を正規化します。 これは、XAML 仕様の既定の空白の動作に関する推奨事項と一致しています。 この動作は、XAML コンテンツ プロパティ内で文字列を指定した場合にのみ発生します。 最も簡単に言うと、XAML はスペース、改行、およびタブ文字をスペースに変換し、連続した文字列の両端に見つかった場合は 1 つのスペースを保持します。 この記事では、XAML の空白の処理の詳細については説明しません。 詳細については、「 [XAML での空白の処理](../xaml-services/white-space-processing.md)」を参照してください。

## <a name="markup-extensions"></a>マークアップ拡張機能

マークアップ拡張機能は、XAML 言語の概念です。 属性構文の値を指定するために使用する場合は、マークアップ拡張機能の使用`{`法`}`を中かっこ ( および ) で示します。 この使用法により、属性値の一般的な処理からリテラル文字列または文字列変換可能値のいずれかから抜け出す XAML 処理が指示されます。

WPF アプリプログラミングで使用される最も一般的な[`Binding`](../../framework/wpf/advanced/binding-markup-extension.md)マークアップ拡張機能は、データ バインディング式、およびリソース[`StaticResource`](../../framework/wpf/advanced/staticresource-markup-extension.md)参照[`DynamicResource`](../../framework/wpf/advanced/dynamicresource-markup-extension.md)および . マークアップ拡張機能を使用すると、属性構文を使用して、プロパティが一般的な属性構文をサポートしていない場合でも、プロパティの値を指定できます。 マークアップ拡張機能では、多くの場合、中間式の型を使用して、値の遅延や実行時にのみ存在する他のオブジェクトの参照などの機能を有効にします。

たとえば、次のマークアップは、属性構文を使用<xref:System.Windows.FrameworkElement.Style%2A>してプロパティの値を設定します。 この<xref:System.Windows.FrameworkElement.Style%2A>プロパティは<xref:System.Windows.Style>、既定では属性構文文字列ではインスタンス化できなかったクラスのインスタンスを受け取ります。 ただし、この場合、属性は特定のマークアップ拡張機能を`StaticResource`参照します。 マークアップ拡張機能が処理されると、以前にリソース ディクショナリ内のキー付きリソースとしてインスタンス化されたスタイルへの参照を返します。

[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources)]
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources2](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources2)]
[!code-xaml[FEResourceSH_snip#XAMLOvwShortResources3](~/samples/snippets/csharp/VS_Snippets_Wpf/FEResourceSH_snip/CS/page1.xaml#xamlovwshortresources3)]

WPF で特に実装された XAML のすべてのマークアップ拡張機能のリファレンス リストについては、「 [WPF XAML 拡張機能](../../framework/wpf/advanced/wpf-xaml-extensions.md)」を参照してください。 System.Xaml によって定義され、.NET Core XAML 実装でより広く利用できるマークアップ拡張機能のリファレンス リストについては[、「XAML 名前空間 (x:)」を参照してください。言語機能](../xaml-services/namespace-language-features.md): マークアップ拡張機能の概念の詳細については、「[マークアップ拡張機能と WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)」を参照してください。

## <a name="type-converters"></a>型コンバーター

「[簡単な XAML 構文」](#xaml-syntax-in-brief)セクションでは、属性値を文字列で設定できる必要があると説明しました。 文字列を他のオブジェクト型またはプリミティブ値に変換する基本的なネイティブ処理は、<xref:System.String>型自体に基づくもので、特定の型のネイティブ処理に加えて<xref:System.DateTime>、<xref:System.Uri>や などの特定の型に対するネイティブ処理にも依存します。 ただし、多くの WPF 型またはこれらの型のメンバーは、より複雑なオブジェクト型のインスタンスを文字列および属性として指定できるように、基本的な文字列属性処理動作を拡張します。

構造体<xref:System.Windows.Thickness>は、XAML の使用に対して型変換が有効になっている型の例です。 <xref:System.Windows.Thickness>は、入れ子になった四角形内の測定値を示し、 などの<xref:System.Windows.FrameworkElement.Margin%2A>プロパティの値として使用されます。 型コンバーターを に<xref:System.Windows.Thickness>配置すると、 を<xref:System.Windows.Thickness>使用するすべてのプロパティを XAML で簡単に指定できます。 次の例では、型変換と属性構文を使用して、 の<xref:System.Windows.FrameworkElement.Margin%2A>値を指定します。

[!code-xaml[XAMLOvwSupport#MarginTCE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#margintce)]

前の属性構文の例は、オブジェクト要素を含む<xref:System.Windows.FrameworkElement.Margin%2A><xref:System.Windows.Thickness>プロパティ要素構文を使用して設定される、次の詳細な構文の例と同じです。 の 4 つの<xref:System.Windows.Thickness>主要なプロパティは、新しいインスタンスの属性として設定されます。

[!code-xaml[XAMLOvwSupport#MarginVerbose](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#marginverbose)]

> [!NOTE]
> また、型自体にはパラメーターなしのコンストラクターがないため、型変換がサブクラスを含まずにその型にプロパティを設定する唯一のパブリックな方法であるオブジェクトの数も制限されています。 たとえば <xref:System.Windows.Input.Cursor> です。

型変換の詳細については、「[型コンバーターと XAML](../../framework/wpf/advanced/typeconverters-and-xaml.md)」を参照してください。

## <a name="xaml-root-elements-and-xaml-namespaces"></a>XAML ルート要素と XAML 名前空間

整形式の XML ファイルと有効な XAML ファイルの両方を使用するには、XAML ファイルにルート要素が 1 つだけ必要です。 一般的な WPF シナリオでは、WPF アプリ モデルで顕著な意味を持つルート要素 (<xref:System.Windows.Window>ページ<xref:System.Windows.Controls.Page>、外部辞書、<xref:System.Windows.ResourceDictionary>アプリ<xref:System.Windows.Application>定義など) を使用します。 次の例は、WPF ページの一般的な XAML ファイルのルート要素と、ルート<xref:System.Windows.Controls.Page>要素を示しています。

[!code-xaml[XAMLOvwSupport#RootOnly](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly)]
[!code-xaml[XAMLOvwSupport#RootOnly2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page2.xaml#rootonly2)]

ルート要素には、属性`xmlns`と`xmlns:x`. これらの属性は、マークアップが要素として参照するバッキング型の型定義を含む XAML 名前空間を XAML プロセッサに示します。 属性`xmlns`は、既定の XAML 名前空間を具体的に示します。 既定の XAML 名前空間内では、マークアップ内のオブジェクト要素をプレフィックスなしで指定できます。 ほとんどの WPF アプリ のシナリオ、および SDK の WPF セクションで示されているほぼすべての例では、既定の XAML 名前空間は WPF`http://schemas.microsoft.com/winfx/2006/xaml/presentation`名前空間にマップされます。 属性`xmlns:x`は、XAML 言語の名前空間をマップする追加の`http://schemas.microsoft.com/winfx/2006/xaml`XAML 名前空間を示します。

名前スコープの`xmlns`使用とマッピングのスコープを定義するこの使用法は、XML 1.0 仕様と一致します。 XAML 名前スコープは、型解決と XAML の解析に関して、名前スコープの要素が型によってどのようにサポートされるかについても暗黙に示す点だけで、XML 名前スコープとは異なります。

属性`xmlns`は、各 XAML ファイルのルート要素でのみ厳密に必要です。 `xmlns`定義は、ルート要素のすべての子孫要素に適用されます (この動作は、XML 1.0 仕様の`xmlns`.と再び一致しています)。`xmlns`属性はルートの下の他の要素にも許可され、定義要素の子孫要素にも適用されます。 ただし、XAML 名前空間の頻繁な定義や再定義は、読みにくい XAML マークアップ スタイルを生成できます。

WPF の XAML プロセッサの実装には、WPF コア アセンブリを認識するインフラストラクチャが含まれています。 WPF コア アセンブリには、既定の XAML 名前空間への WPF マッピングをサポートする型が含まれていることが知られています。 これは、プロジェクトビルドファイルと WPF ビルドおよびプロジェクト システムの一部である構成によって有効になります。 したがって、既定の XAML 名前空間を既定`xmlns`として宣言する必要があるのは、WPF アセンブリから取得した XAML 要素を参照するために必要なすべてです。

### <a name="the-x-prefix"></a>x: プレフィックス

前のルート要素の例では、プレフィックス`x:`を使用して XAML 名前空間`http://schemas.microsoft.com/winfx/2006/xaml`をマップします。 この`x:`プレフィックスは、プロジェクトのテンプレート、例、およびこの SDK 全体のドキュメントでこの XAML 名前空間をマッピングするために使用されます。 XAML 言語の XAML 名前空間には、XAML で頻繁に使用するプログラミング構成要素がいくつか含まれています。 使用する最も一般的な`x:`プレフィックス プログラミング構成要素の一覧を次に示します。

- [x:Key](../xaml-services/xkey-directive.md): 各リソースに対して一意<xref:System.Windows.ResourceDictionary>のキーを設定します (または、他のフレームワークの同様のディクショナリ概念)。 `x:Key`通常の WPF アプリのマークアップで`x:`表示される使用状況の 90% を占める可能性があります。

- [x:Class](../xaml-services/xclass-directive.md): XAML ページの分離コードを提供するクラスの CLR 名前空間とクラス名を指定します。 WPF プログラミング モデルごとに分離コードをサポートするには、このようなクラスが必要です`x:`。

- [x:Name](../xaml-services/xname-directive.md): オブジェクト要素の処理後にランタイム コードに存在するインスタンスのランタイム オブジェクト名を指定します。 一般に、 [x: Name](../xaml-services/xname-directive.md)に対しては、WPF で定義された同等のプロパティを頻繁に使用します。 このようなプロパティは CLR バッキング プロパティに特に対応するため、初期化された XAML から名前付き要素を検索するためにランタイム コードを頻繁に使用するアプリ プログラミングの方が便利です。 最も一般的なプロパティ<xref:System.Windows.FrameworkElement.Name%2A?displayProperty=nameWithType>は です。 特定の型で対応する WPF フレームワーク レベル<xref:System.Windows.FrameworkElement.Name%2A>のプロパティがサポートされていない場合は[、x:Name](../xaml-services/xname-directive.md)を使用できます。 これは、特定のアニメーション シナリオで発生します。

- [x:Static](../xaml-services/xstatic-markup-extension.md): XAML 互換プロパティ以外の静的な値を返す参照を有効にします。

- [x:Type](../xaml-services/xtype-markup-extension.md): 型<xref:System.Type>名に基づいて参照を構築します。 これは<xref:System.Type>、 などの<xref:System.Windows.Style.TargetType%2A?displayProperty=nameWithType>属性を指定するために使用されますが、プロパティには[、x:Type](../xaml-services/xtype-markup-extension.md)マークアップ拡張機能の使用<xref:System.Type>法がオプションであるように、ネイティブの文字列から変換への変換が頻繁に含まれます。

プレフィックス/XAML 名前空間には、一般的`x:`ではない追加のプログラミング構成要素があります。 詳細については[、「XAML 名前空間 (x:)」を参照してください。言語機能](../xaml-services/namespace-language-features.md):

## <a name="custom-prefixes-and-custom-types-in-xaml"></a>XAML でのカスタム プレフィックスとカスタム型

独自のカスタム アセンブリ、または**プレゼンテーションコア、プレゼンテーション****フレームワーク**、**および WindowsBase**の WPF コアの外部にあるアセンブリの場合は、カスタム`xmlns`マッピングの一部としてアセンブリを指定できます。 その後、XAML で、そのアセンブリから型を参照できます。

次に、XAML マークアップでカスタム プレフィックスがどのように機能するかを示す基本的な例を示します。 プレフィックス`custom`は、ルート要素タグで定義され、パッケージ化され、アプリで使用できる特定のアセンブリにマップされます。 このアセンブリには、一`NumericUpDown`般的な XAML の使用法をサポートするために実装される型、および WPF XAML コンテンツ モデルの特定のポイントでの挿入を許可するクラス継承が含まれています。 この`NumericUpDown`コントロールのインスタンスは、XAML パーサーが型を含む XAML 名前空間を認識し、型定義を含むバッキング アセンブリの場所を知ることができるように、プレフィックスを使用してオブジェクト要素として宣言されます。

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

XAML のカスタム型の詳細については、「 [XAML と WPF のカスタム クラス](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)」を参照してください。

アセンブリ内の XML 名前空間とコード名前空間の関連の詳細については、「 WPF [XAML の XAML 名前空間と名前空間マッピング](../../framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)」を参照してください。

## <a name="events-and-xaml-code-behind"></a>イベントと XAML 分離コード

ほとんどの WPF アプリは、XAML マークアップと分離コードの両方で構成されています。 プロジェクト内では、XAML は`.xaml`ファイルとして記述され、Microsoft Visual Basic や C# などの CLR 言語を使用して分離コード ファイルを記述します。 XAML ファイルが WPF プログラミングおよびアプリケーション モデルの一部としてマークアップ コンパイルされる場合、XAML ファイルの XAML 分離コード ファイルの場所は、名前空間とクラスを XAML`x:Class`のルート要素の属性として指定することによって識別されます。

これまでの例では、いくつかのボタンを見てきましたが、これらのボタンのどれも論理的な動作がまだ関連付けされていません。 オブジェクト要素の動作を追加するための主なアプリケーション レベルのメカニズムは、要素クラスの既存のイベントを使用し、実行時にイベントが発生したときに呼び出されるそのイベントの特定のハンドラーを記述することです。 使用するイベント名とハンドラーの名前はマークアップで指定されますが、ハンドラーを実装するコードは分離コードで定義されます。

[!code-xaml[XAMLOvwSupport#ButtonWithCodeBehind](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml#buttonwithcodebehind)]

[!code-csharp[XAMLOvwSupport#ButtonWithCodeBehindHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page3.xaml.cs#buttonwithcodebehindhandler)]
[!code-vb[XAMLOvwSupport#ButtonWithCodeBehindHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#buttonwithcodebehindhandler)]

分離コード ファイルは CLR 名前空間を使用`ExampleNamespace`し、その`ExamplePage`名前空間内の部分クラスとして宣言します。 これは、 の`x:Class`属性値と`ExampleNamespace`並行します。`ExamplePage` マークアップ ルートで指定されました。 WPF マークアップ コンパイラは、ルート要素の型からクラスを派生させることによって、コンパイル済み XAML ファイルの部分クラスを作成します。 同じ部分クラスも定義する分離コードを指定すると、コンパイルされたアプリの同じ名前空間とクラス内で、結果のコードが結合されます。

WPF での分離コード プログラミングの要件の詳細については、「 [WPF の分離コード、イベント ハンドラー、および部分クラスの要件](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md#code-behind-event-handler-and-partial-class-requirements-in-wpf)」を参照してください。

分離コード ファイルを作成しない場合は、XAML ファイル内のコードをインラインで記述することもできます。 ただし、インライン コードは、あまり多目的な手法で、大きな制限があります。 その他の情報については、「 [WPF の分離コードと XAML](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)」を参照してください。

### <a name="routed-events"></a>ルーティング イベント

WPF の基本となる特定のイベント機能は、ルーティング イベントです。 ルーティング イベントを使用すると、要素がツリーリレーションシップを介して接続されている場合に限り、別の要素によって発生したイベントを要素で処理できます。 XAML 属性を使用してイベント処理を指定する場合、クラス メンバー テーブルに特定のイベントを一覧表示しない要素を含む、任意の要素でルーティング イベントをリッスンして処理できます。 これは、イベント名属性を所有クラス名で修飾することによって実現されます。 たとえば、`StackPanel`進行中`StackPanel` / `Button`の例の親は<xref:System.Windows.Controls.Primitives.ButtonBase.Click>、`Button.Click``StackPanel`オブジェクト要素の属性を属性値として指定することで、子要素ボタンのイベントのハンドラーを登録できます。 詳細については、「[ルーティング イベントの概要](../../framework/wpf/advanced/routed-events-overview.md)」を参照してください。

## <a name="xaml-named-elements"></a>XAML 名前付き要素

既定では、XAML オブジェクト要素を処理してオブジェクト グラフに作成されるオブジェクト インスタンスには、一意の識別子またはオブジェクト参照は含まれません。 これに対し、コードでコンストラクターを呼び出す場合は、コンストラクターの結果を使用して、構築されたインスタンスに変数を設定し、コードの後でインスタンスを参照できるようにします。 マークアップ定義を通じて作成されたオブジェクトへの標準化されたアクセスを提供するために、XAML は[x:Name 属性](../xaml-services/xname-directive.md)を定義します。 任意のオブジェクト要素に対して`x:Name`属性の値を設定できます。 分離コードでは、選択した識別子は、構築されたインスタンスを参照するインスタンス変数と同じです。 すべての点で、名前付き要素はオブジェクト インスタンス (そのインスタンスの名前参照) であるかのように機能し、コード ビハインドは、アプリ内での実行時の対話を処理するために名前付き要素を参照できます。 インスタンスと変数の間のこの接続は、WPF XAML マークアップ コンパイラによって実現され、より具体的には、<xref:System.Windows.Markup.IComponentConnector.InitializeComponent%2A>この記事で詳しく説明しないような機能やパターンが含まれます。

WPF フレームワーク レベルの XAML<xref:System.Windows.FrameworkElement.Name%2A>要素は、XAML で定義`x:Name`された属性と同等のプロパティを継承します。 また、一般にプロパティとしても`x:Name``Name`定義されているプロパティ レベルのクラスもあります。 一般的に、選択した要素/`Name`型のメンバー テーブルにプロパティが見つからない場合は、`x:Name`代わりに使用します。 値`x:Name`は、特定のサブシステムまたはなどの<xref:System.Windows.FrameworkElement.FindName%2A>ユーティリティ メソッドによって実行時に使用できる XAML 要素に識別子を提供します。

要素に設定<xref:System.Windows.FrameworkElement.Name%2A>する例を<xref:System.Windows.Controls.StackPanel>次に示します。 次に、<xref:System.Windows.Controls.Button>によって<xref:System.Windows.Controls.StackPanel><xref:System.Windows.Controls.StackPanel>`buttonContainer`<xref:System.Windows.FrameworkElement.Name%2A>設定されたとおりに、 のインスタンス参照を参照する 内部の ハンドラー。

[!code-xaml[XAMLOvwSupport#NamedE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede)]
[!code-xaml[XAMLOvwSupport#NamedE2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml#namede2)]

[!code-csharp[XAMLOvwSupport#NameCode](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page7.xaml.cs#namecode)]
[!code-vb[XAMLOvwSupport#NameCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/XAMLOvwSupport/VisualBasic/Page1.xaml.vb#namecode)]

変数と同様に、インスタンスの XAML 名はスコープの概念によって管理されるため、予測可能な特定のスコープ内で名前を一意に適用できます。 ページを定義するプライマリ マークアップは、XAML 名前スコープの境界がそのページのルート要素である、1 つの一意の XAML 名前スコープを表します。 ただし、スタイル内のスタイルやテンプレートなど、他のマークアップ ソースは実行時にページと対話できます。 XAML 名前スコープ`x:Name`の詳細については、「 [x:Name ディレクティブ](../xaml-services/xname-directive.md)、または[WPF XAML 名前スコープ](../../framework/wpf/advanced/wpf-xaml-namescopes.md)」を参照<xref:System.Windows.FrameworkElement.Name%2A>してください。

## <a name="attached-properties-and-attached-events"></a>添付プロパティと添付イベント

XAML は、プロパティまたはイベントが設定されている要素の型の定義に存在するかどうかに関係なく、任意の要素に特定のプロパティまたはイベントを指定できるようにする言語機能を指定します。 この機能のプロパティ バージョンは添付プロパティと呼ばれ、イベント バージョンは添付イベントと呼ばれます。 概念的には、添付プロパティと添付イベントは、任意の XAML 要素/オブジェクト インスタンスに設定できるグローバル メンバーと考えることができます。 ただし、その要素/クラスまたは大規模なインフラストラクチャは、アタッチされた値のバッキング プロパティ ストアをサポートする必要があります。

XAML の添付プロパティは、通常、属性構文を使用して使用されます。 属性構文では、添付プロパティを フォーム`ownerType.propertyName`で指定します。

表面的には、これはプロパティ要素の使用方法に似ていますが、この場合`ownerType`、指定する型は、添付プロパティが設定されているオブジェクト要素とは常に異なる型です。 `ownerType`は、添付プロパティ値を取得または設定するために XAML プロセッサが必要とするアクセサー メソッドを提供する型です。

添付プロパティの最も一般的なシナリオは、子要素が親要素にプロパティ値を報告できるようにすることです。

添付プロパティの例を次<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>に示します。 この<xref:System.Windows.Controls.DockPanel>クラスは、アタッチされたプロパティ<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>を所有するアクセサーを定義します。 この<xref:System.Windows.Controls.DockPanel>クラスには、子要素を反復処理し、各要素の set 値を具体的に<xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>チェックするロジックも含まれています。 値が見つかった場合、その値はレイアウト時に子要素の位置に使用されます。 <xref:System.Windows.Controls.DockPanel.Dock%2A?displayProperty=nameWithType>添付プロパティとこの位置決め機能の使用は、実際にはクラスの動機付け<xref:System.Windows.Controls.DockPanel>のシナリオです。

[!code-xaml[XAMLOvwSupport#DockAP](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#dockap)]

WPF では、アタッチされたプロパティの大部分またはすべてが依存関係プロパティとしても実装されます。 詳細については、「[添付プロパティの概要](../../framework/wpf/advanced/attached-properties-overview.md)」を参照してください。

添付イベントは、似`ownerType.eventName`たような形式の属性構文を使用します。 アタッチされていないイベントと同様に、XAML の添付イベントの属性値は、要素でイベントが処理されるときに呼び出されるハンドラー メソッドの名前を指定します。 WPF XAML での添付イベントの使用法はあまり一般的ではありません。 詳細については、「[添付イベントの概要](../../framework/wpf/advanced/attached-events-overview.md)」を参照してください。

## <a name="base-types-and-xaml"></a>基本型と XAML

基になる WPF XAML とその XAML 名前空間は、XAML のマークアップ要素に加えて、CLR オブジェクトに対応する型のコレクションです。 ただし、すべてのクラスを要素にマップできるわけではありません。 などの<xref:System.Windows.Controls.Primitives.ButtonBase>抽象クラス、および特定の非抽象基本クラスは、CLR オブジェクト モデルの継承に使用されます。 具体的な XAML 要素のそれぞれが階層内の基本クラスからメンバーを継承するため、抽象クラスを含む基本クラスは XAML 開発にとって重要です。 多くの場合、これらのメンバーには、要素の属性として設定できるプロパティや、処理できるイベントが含まれます。 <xref:System.Windows.FrameworkElement>は、WPF フレームワーク レベルでの WPF の具体的な基本 UI クラスです。 UI を設計する際には、さまざまなシェイプ、パネル、デコレータ、コントロール クラスを使用<xref:System.Windows.FrameworkElement>します。 関連する基本クラス<xref:System.Windows.FrameworkContentElement>は、フロー レイアウトのプレゼンテーションに適したドキュメント指向要素をサポートし、API を意図的に でミラーリングする<xref:System.Windows.FrameworkElement>API を使用します。 要素レベルの属性と CLR オブジェクト モデルの組み合わせにより、特定の XAML 要素とその基になる型に関係なく、ほとんどの具象 XAML 要素で設定可能な共通プロパティのセットが提供されます。

## <a name="xaml-security"></a>XAML セキュリティ

XAML は、オブジェクトのインスタンス化と実行を直接表すマークアップ言語です。 したがって、XAML で作成された要素は、生成された同等のコードと同様に、システム リソース (ネットワーク アクセス、ファイル システム IO など) と対話する機能を持ちます。 完全に信頼されたアプリに読み込まれた XAML は、ホスト アプリと同様にシステム リソースにアクセスできます。

### <a name="code-access-security-cas-in-wpf"></a>WPF のコード アクセス セキュリティ (CAS)

**このセクションは.NET Framework にのみ適用されます。.NET コアの WPF は CAS をサポートしていません。詳細については、「コード[アクセス セキュリティの相違点](../migration/differences-from-net-framework.md#code-access-security)」を参照してください。**

.NET フレームワークの WPF では、コード アクセス セキュリティ (CAS) がサポートされています。 つまり、インターネット ゾーンで実行されている WPF コンテンツは実行権限を減らします。 "Loose XAML" (XAML ビューアーによって読み込み時に解釈されるコンパイルされていない XAML のページ) と XBAP は通常、このインターネット ゾーンで実行され、同じアクセス許可セットを使用します。 ただし、完全に信頼されたアプリケーションに読み込まれた XAML は、ホスト アプリケーションと同様にシステム リソースにアクセスできます。 詳細については、「 [WPF 部分信頼セキュリティ](../../framework/wpf/wpf-partial-trust-security.md)」を参照してください。

## <a name="loading-xaml-from-code"></a>コードから XAML を読み込む

XAML を使用してすべての UI を定義できますが、XAML で UI の一部だけを定義することも適切な場合があります。 この機能を使用すると、部分的なカスタマイズ、情報のローカルストレージ、XAML を使用したビジネス オブジェクトの提供、またはさまざまなシナリオを実現できます。 これらのシナリオの鍵は、<xref:System.Windows.Markup.XamlReader>クラスとその<xref:System.Windows.Markup.XamlReader.Load%2A>メソッドです。 入力は XAML ファイルであり、出力は、そのマークアップから作成されたオブジェクトのすべての実行時ツリーを表すオブジェクトです。 その後、アプリケーションに既に存在する別のオブジェクトのプロパティとしてオブジェクトを挿入できます。 プロパティが、最終的な表示機能を持ち、新しいコンテンツがアプリに追加されたことを実行エンジンに通知するコンテンツ モデルの適切なプロパティである限り、XAML で読み込むことで、実行中のアプリのコンテンツを簡単に変更できます。 .NET Framework では、この機能は、実行時にアプリケーションにファイルを読み込む場合の明らかなセキュリティ上の影響を受けるため、通常、完全信頼アプリケーションでのみ使用できます。

## <a name="see-also"></a>関連項目

- [XAML 構文の詳細](../../framework/wpf/advanced/xaml-syntax-in-detail.md)
- [WPF における XAML とカスタム クラス](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [XAML 名前空間 (x:)言語機能](../xaml-services/namespace-language-features.md)
- [WPF XAML 拡張機能](../../framework/wpf/advanced/wpf-xaml-extensions.md)
- [基本要素の概要](../../framework/wpf/advanced/base-elements-overview.md)
- [WPF のツリー](../../framework/wpf/advanced/trees-in-wpf.md)
