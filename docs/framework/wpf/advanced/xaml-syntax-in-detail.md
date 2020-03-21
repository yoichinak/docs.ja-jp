---
title: XAML 構文の詳細
ms.date: 03/30/2017
helpviewer_keywords:
- XML [WPF], namespaces
- XAML [WPF], parsing of attributes
- parsing of attributes [WPF]
- XAML [WPF], markup extensions
- attached properties [WPF]
- tag syntax [XAML]
- markup extensions [WPF]
- XAML [WPF], object element syntax
- XAML [WPF], syntax terminology
- attached events [WPF]
- lookup semantics [WPF]
- XAML [WPF], attached events
- XAML [WPF], content syntax
- XAML [WPF], lookup semantics
- content syntax [WPF]
- object element syntax [WPF]
- syntax terminology [XAML]
- XAML [WPF], attached properties
- attributes [XAML], parsing
- XAML [WPF], tag syntax
- XAML [WPF], attribute syntax
- property element syntax [WPF]
- terminology [XAML]
- namespaces [WPF], XML
- attribute syntax [XAML]
- XAML [WPF], property element syntax
ms.assetid: 67cce290-ca26-4c41-a797-b68aabc45479
ms.openlocfilehash: dbff4bed59c8d1e861555676578b52528e2aebbe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186186"
---
# <a name="xaml-syntax-in-detail"></a>XAML 構文の詳細
このトピックでは、XAML 構文の要素を記述するために使用される用語を定義します。 これらの用語は、このドキュメントの残りの部分で、特に WPF ドキュメントと、XAML を使用する他のフレームワーク、または System.Xaml レベルで XAML 言語サポートによって有効になる基本的な XAML 概念の両方で頻繁に使用されます。 このトピックでは、[トピック「XAML の概要 (WPF)」](../../../desktop-wpf/fundamentals/xaml.md)で紹介されている基本的な用語について説明します。  

<a name="the_xaml_language_specification"></a>
## <a name="the-xaml-language-specification"></a>XAML 言語仕様  
 ここで定義されている XAML 構文用語も、XAML 言語仕様の中で定義または参照されます。 XAML は XML に基づく言語であり、XML 構造規則に従ったり、XML 構造ルールに従ったり拡張したりします。 用語の一部は、XML 言語または XML ドキュメント オブジェクト モデルを記述するときによく使用される用語に基づいて共有されます。  
  
 XAML 言語仕様の詳細については、マイクロソフト ダウンロード センターから[\[MS-XAML\]](https://download.microsoft.com/download/0/A/6/0A6F7755-9AF5-448B-907D-13985ACCF53E/[MS-XAML].pdf)をダウンロードしてください。  
  
<a name="xaml_and_clr"></a>
## <a name="xaml-and-clr"></a>XAML と CLR  
 XAML はマークアップ言語です。 共通言語ランタイム (CLR) は、その名前で示されるように、ランタイムの実行を有効にします。 XAML は、CLR ランタイムによって直接使用される共通言語の 1 つだけではありません。 代わりに、XAML は独自の型システムをサポートしていると考えることができます。 WPF で使用される特定の XAML 解析システムは、CLR 型システムと CLR 型システム上に構築されます。 XAML 型は CLR 型にマップされ、WPF XAML が解析されるときにランタイム表現をインスタンス化します。 このため、このドキュメントの構文の残りの部分では、XAML 言語仕様での対応する構文の説明では含めていなくても、CLR 型システムへの参照が含まれます。 XAML 言語仕様レベルに従って、XAML 型は他の型システムにマップできます。  
  
#### <a name="members-of-types-and-class-inheritance"></a>型のメンバとクラスの継承  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]型の XAML メンバーとして表示されるプロパティとイベントは、多くの場合、基本型から継承されます。 たとえば、次の例を考`<Button Background="Blue" .../>`えてみましょう。 クラス<xref:System.Windows.Controls.Control.Background%2A>定義、リフレクション結果、またはドキュメント<xref:System.Windows.Controls.Button>を参照する場合、このプロパティはクラスですぐに宣言されたプロパティではありません。 代わりに<xref:System.Windows.Controls.Control.Background%2A>、基本<xref:System.Windows.Controls.Control>クラスから継承されます。  
  
 XAML 要素の[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]クラス継承動作は、スキーマによって適用される XML マークアップの解釈から大幅に逸脱しています。 クラスの継承は、特に中間基底クラスが抽象クラスである場合や、インターフェイスが関係している場合に複雑になる可能性があります。 これは、XAML 要素とその許容属性のセットが、DTD や XSD 形式などの XML プログラミングに通常使用されるスキーマ型を使用して正確かつ完全に表現することが困難である理由の 1 つです。 もう 1 つの理由は、XAML 言語自体の機能拡張および型マッピングによって、許容される型とメンバーの固定表現の完全性が妨げられます。  
  
<a name="object_element_syntax"></a>
## <a name="object-element-syntax"></a>オブジェクト要素構文  
 *オブジェクト要素構文*は、XML 要素を宣言することによって CLR クラスまたは CLR 構造体をインスタンス化する XAML マークアップ構文です。 この構文は、HTML などの他のマークアップ言語の要素構文に似ています。 オブジェクト要素の構文は、左山かっこ\<( ) で始まり、その直後にインスタンス化されるクラスまたは構造体の型名が続きます。 0 個以上のスペースが型名の後に続く場合があり、オブジェクト要素で 0 個以上の属性を宣言し、各属性名= "value" の組み合わせを区切る 1 つ以上のスペースを使用することもできます。 最後に、次のいずれかが当てはまる必要があります。  
  
- 要素とタグは、スラッシュ (/) の直後に右山かっこ (>) で閉じる必要があります。  
  
- 開始タグは、右山かっこ (>) で完了する必要があります。 他のオブジェクト要素、プロパティ要素、または内部テキストは、開始タグの後に続けることができます。 この中に含まれるコンテンツは、通常、要素のオブジェクト モデルによって制約されます。 オブジェクト要素の同等の終了タグも、適切なネストと他の開始タグと終了タグのペアとのバランスで存在する必要があります。  
  
 .NET によって実装される XAML には、オブジェクト要素を型、属性をプロパティまたはイベントに、XAML 名前空間を CLR 名前空間とアセンブリにマップする一連の規則があります。 WPF および .NET の場合、XAML オブジェクト要素は参照アセンブリで定義されている .NET 型にマップされ、属性はそれらの型のメンバーにマップされます。 XAML で CLR 型を参照すると、その型の継承されたメンバーにもアクセスできます。  
  
 たとえば、次の例は、<xref:System.Windows.Controls.Button>クラスの新しいインスタンスをインスタンス化するオブジェクト要素構文であり、その属性の<xref:System.Windows.FrameworkElement.Name%2A>属性と値も指定します。  
  
 [!code-xaml[XAMLOvwSupport#SyntaxOE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxoe)]  
  
 次の例は、XAML コンテンツ プロパティ構文も含むオブジェクト要素構文です。 内部テキストは、 XAML コンテンツ プロパティ<xref:System.Windows.Controls.TextBox><xref:System.Windows.Controls.TextBox.Text%2A>を設定するために使用されます。  
  
 [!code-xaml[XAMLOvwSupport#ThisIsATextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#thisisatextbox)]  
  
### <a name="content-models"></a>コンテンツ モデル  
 クラスは、構文の観点から XAML オブジェクト要素としての使用法をサポートする場合がありますが、その要素は、全体的なコンテンツ モデルまたは要素ツリーの予想される位置に配置された場合にのみ、アプリケーションまたはページで適切に機能します。 たとえば、 a<xref:System.Windows.Controls.MenuItem>は通常、 などの<xref:System.Windows.Controls.Primitives.MenuBase><xref:System.Windows.Controls.Menu>派生クラスの子としてのみ配置する必要があります。 特定の要素のコンテンツ モデルは、コントロールや XAML 要素として使用できるその他[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]のクラスのクラス ページの注釈の一部として文書化されています。  
  
<a name="properties_of_object_elements"></a>
## <a name="properties-of-object-elements"></a>オブジェクト要素のプロパティ  
 XAML のプロパティは、さまざまな構文で設定されます。 特定のプロパティに使用できる構文は、設定するプロパティの基になる型システムの特性によって異なります。  
  
 プロパティの値を設定すると、実行時オブジェクト グラフに存在するオブジェクトにフィーチャまたは特性を追加できます。 オブジェクト要素から作成されたオブジェクトの初期状態は、パラメーターなしのコンストラクターの動作に基づきます。 通常、アプリケーションは、任意のオブジェクトの完全に既定のインスタンス以外のものを使用します。  
  
<a name="attribute_syntax_properties"></a>
## <a name="attribute-syntax-properties"></a>属性構文 (プロパティ)  
 属性構文は、既存のオブジェクト要素に属性を宣言することによってプロパティの値を設定する XAML マークアップ構文です。 属性名は、関連するオブジェクト要素をバックするクラスのプロパティの CLR メンバー名と一致する必要があります。 属性名の後に代入演算子 (=) が続きます。 属性値は、引用符で囲まれた文字列である必要があります。  
  
> [!NOTE]
> 交互引用符を使用して、属性内にリテラル引用符を配置できます。 たとえば、単一引用符を使用して、二重引用符を含む文字列を宣言できます。 単一引用符または二重引用符のどちらを使用する場合でも、属性値文字列を開いたり閉じたりするには、一致するペアを使用する必要があります。 また、特定の XAML 構文によって課される文字制限を回避するために、エスケープ シーケンスやその他のテクニックを使用することもできます。 [XML 文字エンティティと XAML](../../../desktop-wpf/xaml-services/xml-character-entities.md)を参照してください。  
  
 属性構文を使用して設定するには、プロパティがパブリックで、書き込み可能である必要があります。 バッキング型システムのプロパティの値は、値型であるか、関連するバッキング型にアクセスするときに XAML プロセッサによってインスタンス化または参照できる参照型である必要があります。  
  
 WPF XAML イベントの場合、属性名として参照されるイベントはパブリックで、パブリック デリゲートを持つ必要があります。  
  
 プロパティまたはイベントは、含むオブジェクト要素によってインスタンス化されるクラスまたは構造体のメンバーである必要があります。  
  
### <a name="processing-of-attribute-values"></a>属性値の処理  
 開始引用符と終了引用符に含まれる文字列値は、XAML プロセッサによって処理されます。 プロパティの既定の処理動作は、基になる CLR プロパティの型によって決まります。  
  
 属性値は、この処理順序を使用して、次のいずれかによって入力されます。  
  
1. XAML プロセッサが中かっこまたはから<xref:System.Windows.Markup.MarkupExtension>派生したオブジェクト要素を検出した場合、参照されるマークアップ拡張機能は、文字列として値を処理するのではなく、最初に評価され、マークアップ拡張機能によって返されるオブジェクトが値として使用されます。 マークアップ拡張機能によって返されるオブジェクトは、多くの場合、既存のオブジェクトへの参照、または実行時まで評価を延期する式であり、新しくインスタンス化されたオブジェクトではありません。  
  
2. プロパティが 属性付<xref:System.ComponentModel.TypeConverter>きで宣言されている場合、またはそのプロパティの値型が属性<xref:System.ComponentModel.TypeConverter>付きで宣言されている場合、属性の文字列値は変換入力として型コンバーターに送信され、コンバーターは新しいオブジェクト インスタンスを返します。  
  
3. が存在しない<xref:System.ComponentModel.TypeConverter>場合は、プロパティ型への直接変換が試行されます。 この最終レベルは、XAML 言語プリミティブ型間のパーサーネイティブ値での直接変換、または列挙型の名前付き定数の名前のチェック (パーサーは、一致する値にアクセスします) です。  
  
#### <a name="enumeration-attribute-values"></a>列挙属性値  
 XAML の列挙型は、XAML パーサーによって本質的に処理され、列挙型のメンバーは、列挙型の名前付き定数の 1 つの文字列名を指定して指定する必要があります。  
  
 非フラグ列挙値の場合、ネイティブ動作では、属性値の文字列を処理し、列挙値のいずれかに解決します。 列挙の形式で*列挙を*指定しません。*コード*で行う場合と同じ値。 代わりに *、Value*のみを指定し、*列挙型*は、設定するプロパティの型によって推論されます。 *[ 列挙 ]* で属性を指定する場合*値*フォームは、正しく解決されません。  
  
 フラグ列挙型の場合、動作はメソッドに<xref:System.Enum.Parse%2A?displayProperty=nameWithType>基づいています。 各値をコンマで区切ることで、フラグ列挙型に複数の値を指定できます。 ただし、フラグを設定していない列挙値を組み合わせることはできません。 たとえば、コンマ構文を使用して、非フラグ列挙体の<xref:System.Windows.Trigger>複数の条件に対して動作する を作成することはできません。  
  
```xaml  
<!--This will not compile, because Visibility is not a flagwise enumeration.-->  
...  
<Trigger Property="Visibility" Value="Collapsed,Hidden">  
  <Setter ... />  
</Trigger>  
...  
```  
  
 XAML で設定可能な属性をサポートするフラグ列挙は、WPF ではまれです。 ただし、このような列挙型の<xref:System.Windows.Media.StyleSimulations>1 つは です。 たとえば、コンマ区切りのフラグ属性構文を使用して、クラスの「解説」で示されている例を<xref:System.Windows.Documents.Glyphs>変更できます。`StyleSimulations = "BoldSimulation"`になる可能性`StyleSimulations = "BoldSimulation,ItalicSimulation"`があります。 <xref:System.Windows.Input.KeyBinding.Modifiers%2A?displayProperty=nameWithType>は、複数の列挙値を指定できる別のプロパティです。 ただし、<xref:System.Windows.Input.ModifierKeys>列挙体が独自の型コンバーターをサポートするため、このプロパティは特殊なケースになります。 修飾子の型コンバーターでは、コンマ (,) ではなく、区切り記号としてプラス記号 (+) を使用します。 この変換では、"Ctrl+Alt" などの Microsoft Windows プログラミングでキーの組み合わせを表す従来の構文がサポートされています。  
  
### <a name="properties-and-event-member-name-references"></a>プロパティとイベント メンバー名の参照  
 属性を指定する場合、格納オブジェクト要素に対してインスタンス化した CLR 型のメンバーとして存在するプロパティまたはイベントを参照できます。  
  
 または、添付プロパティまたは添付イベントを、含んでいるオブジェクト要素とは無関係に参照できます。 (添付プロパティについては、今後のセクションで説明します)。  
  
 typeName を使用して、既定の名前空間を介してアクセスできる任意のオブジェクトからイベントに名前を*付*けることもできます。*イベント*部分修飾名。この構文は、ハンドラーが子要素からのイベント ルーティングを処理することを目的としているが、親要素はメンバー テーブルにはそのイベントも含まないルーティング イベントのハンドラーのアタッチをサポートします。 この構文は、添付イベントの構文に似ていますが、ここでのイベントは、実際の添付イベントではありません。 代わりに、修飾名を持つイベントを参照しています。 詳細については、「[ルーティング イベントの概要](routed-events-overview.md)」を参照してください。  
  
 一部のシナリオでは、プロパティ名は属性名ではなく属性の値として指定される場合があります。 そのプロパティ名には、フォーム*ownerType*で指定されたプロパティなどの修飾子を含めることができます。*プロパティ名を指定します*。 このシナリオは、XAML でスタイルまたはテンプレートを作成する場合に一般的です。 属性値として提供されるプロパティ名の処理規則は異なり、設定されるプロパティの型、または特定の WPF サブシステムの動作によって制御されます。 詳細については、「[スタイルとテンプレート」を](../controls/styling-and-templating.md)参照してください。  
  
 プロパティ名の別の用途は、属性値がプロパティとプロパティの関係を記述する場合です。 この機能は、データ バインディングとストーリーボード ターゲットに使用され、<xref:System.Windows.PropertyPath>クラスとその型コンバーターによって有効になります。 参照セマンティクスの詳細については、「 [PropertyPath XAML 構文](propertypath-xaml-syntax.md)」を参照してください。  
  
<a name="property_element_syntax"></a>
## <a name="property-element-syntax"></a>プロパティ要素構文  
 *プロパティ要素構文*は、要素の基本的な XML 構文規則と多少異なる構文です。 XML では、属性の値は事実上の文字列であり、使用されている文字列エンコーディング形式は唯一のバリエーションです。 XAML では、プロパティの値として他のオブジェクト要素を割り当てることができます。 この機能は、プロパティ要素構文によって有効になります。 プロパティは、要素タグ内の属性として指定されるのではなく *、elementTypeName*の開始要素タグを使用して指定されます。*プロパティの*値が指定されているプロパティの値が指定されている場合、プロパティ要素が閉じられます。  
  
 具体的には、構文は左山かっこ (\<) で始まり、その直後にプロパティ要素の構文が含まれているクラスまたは構造体の型名が続きます。 この直後に 1 つのドット (.) が続き、次にプロパティの名前が続き、次に右山かっこ (>) が続きます。 属性構文と同様に、そのプロパティは、指定された型の宣言されたパブリック メンバー内に存在する必要があります。 プロパティに割り当てられる値は、プロパティ要素内に含まれます。 通常、値は 1 つ以上のオブジェクト要素として指定されます。 最後に、同じ要素を指定する同等の終了タグ*TypeName*。*プロパティNameの*組み合わせは、適切な入れ子と他の要素タグとのバランスで提供する必要があります。  
  
 たとえば、次のプロパティ要素構文は<xref:System.Windows.FrameworkElement.ContextMenu%2A>、 のプロパティのプロパティ<xref:System.Windows.Controls.Button>要素構文です。  
  
 [!code-xaml[XAMLOvwSupport#ContextMenu](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#contextmenu)]  
  
 プロパティ要素内の値は、指定されるプロパティの型がプリミティブ値型 (<xref:System.String>など) または名前が指定されている列挙体である場合に、内部テキストとして指定することもできます。 これらの 2 つの使用法は、これらの各ケースで単純な属性構文を使用する可能性があるため、多少珍しい方法です。 プロパティ要素を文字列で埋めるシナリオの 1 つは、XAML コンテンツ プロパティではないが、UI テキストの表現に使用されるプロパティの場合です。 属性構文では、ライン フィードを保持できませんが、プロパティ要素の構文は、重要な空白の保持がアクティブである限り、可能です (詳細については[、XAML での空白の処理](../../../desktop-wpf/xaml-services/white-space-processing.md)を参照してください)。 もう 1 つのシナリオは、プロパティ要素に[x:Uid ディレクティブ](../../../desktop-wpf/xaml-services/xuid-directive.md)を適用し、その値を WPF 出力 BAML またはその他の手法でローカライズする値としてマークすることです。  
  
 プロパティ要素は、WPF 論理ツリーでは表されません。 プロパティ要素は、プロパティを設定するための特定の構文であり、それを裏付けているインスタンスまたはオブジェクトを持つ要素ではありません。 (論理ツリーの概念の詳細については[、「WPF のツリー](trees-in-wpf.md)」を参照してください)。  
  
 属性とプロパティ要素の構文の両方がサポートされているプロパティの場合、2 つの構文は一般的に同じ結果になりますが、空白文字の処理などの微妙な部分は構文によって若干異なる場合があります。  
  
<a name="collection_syntax"></a>
## <a name="collection-syntax"></a>コレクション構文  
 XAML 仕様では、値型がコレクションであるプロパティを識別するために XAML プロセッサの実装が必要です。 .NET の一般的な XAML プロセッサ実装は、マネージ コードと CLR に基づいており、次のいずれかを通じてコレクション型を識別します。  
  
- 型は実装<xref:System.Collections.IList>します。  
  
- 型は実装<xref:System.Collections.IDictionary>します。  
  
- 型の派生元<xref:System.Array>(XAML の配列の詳細については、「 [x: 配列マークアップ拡張機能](../../../desktop-wpf/xaml-services/xarray-markup-extension.md)」を参照してください)。  
  
 プロパティの型がコレクションの場合、推定されるコレクション型をオブジェクト要素としてマークアップで指定する必要はありません。 代わりに、コレクション内の項目となる要素は、プロパティ要素の 1 つ以上の子要素として指定されます。 このような各項目は、読み込み中にオブジェクトに評価され、暗黙の`Add`コレクションのメソッドを呼び出すことによってコレクションに追加されます。 たとえば、 の<xref:System.Windows.Style.Triggers%2A><xref:System.Windows.Style>プロパティは、 を実装する特殊<xref:System.Windows.TriggerCollection>なコレクション型<xref:System.Collections.IList>を受け取ります。 マークアップ内のオブジェクト要素を<xref:System.Windows.TriggerCollection>インスタンス化する必要はありません。 代わりに、プロパティ要素内の<xref:System.Windows.Trigger>要素として 1`Style.Triggers`つ以上の項目<xref:System.Windows.Trigger>を指定します。 <xref:System.Windows.TriggerCollection>  
  
 [!code-xaml[XAMLOvwSupport#SyntaxPECollection](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxpecollection)]  
  
 プロパティは、コレクション型と、その型の XAML コンテンツ プロパティ、および派生型の両方である可能性があります。  
  
 暗黙的なコレクション要素は、要素としてマークアップに表示されない場合でも、論理ツリー表現にメンバーを作成します。 通常、親型のコンストラクターは、そのプロパティの 1 つであるコレクションのインスタンス化を実行し、最初に空のコレクションがオブジェクト ツリーの一部になります。  
  
> [!NOTE]
> 汎用リストおよびディクショナリ インターフェイス<xref:System.Collections.Generic.IList%601>(<xref:System.Collections.Generic.IDictionary%602>および ) は、コレクション検出ではサポートされていません。 ただし<xref:System.Collections.Generic.List%601>、直接実装<xref:System.Collections.IList>するため、クラスを基本クラスとして使用することも<xref:System.Collections.Generic.Dictionary%602>、基底クラスとして使用<xref:System.Collections.IDictionary>することもできます。  
  
 コレクション型の .NET Reference ページでは、コレクションのオブジェクト要素が意図的に省略されたこの構文は、XAML 構文のセクションで暗黙的なコレクション構文として示される場合があります。  
  
 ルート要素を除き、XAML ファイル内の他の要素の子要素として入れ子になっているすべてのオブジェクト要素は、実際には、次のケースのいずれかまたは両方の要素です。、または親要素の XAML コンテンツ プロパティの値を指定する要素 (XAML コンテンツ プロパティについては、今後のセクションで説明します)。 つまり、マークアップ ページ内の親要素と子要素のリレーションシップは、ルートの 1 つのオブジェクトであり、ルートの下にある各オブジェクト要素は、親のプロパティ値を提供する単一のインスタンスか、または親のコレクション型プロパティ値でもあるコレクション。 この単一ルートの概念は XML で共通しており、XAML を読み込む API の<xref:System.Windows.Markup.XamlReader.Load%2A>動作で強化されることが多い 。  
  
 次の例は、明示的に指定されたコレクション (<xref:System.Windows.Media.GradientStopCollection>) のオブジェクト要素を使用した構文です。  
  
```xaml  
<LinearGradientBrush>  
  <LinearGradientBrush.GradientStops>  
    <GradientStopCollection>  
      <GradientStop Offset="0.0" Color="Red" />  
      <GradientStop Offset="1.0" Color="Blue" />  
    </GradientStopCollection>  
  </LinearGradientBrush.GradientStops>  
</LinearGradientBrush>  
```  
  
 コレクションを明示的に宣言できるわけではないことに注意してください。 たとえば、前に示<xref:System.Windows.TriggerCollection><xref:System.Windows.Style.Triggers%2A>した例で明示的に宣言しようとすると失敗します。 コレクションを明示的に宣言するには、コレクション クラスがパラメーターなしのコンストラクターをサポートする<xref:System.Windows.TriggerCollection>必要があり、パラメーターなしのコンストラクターを持たない必要があります。  
  
<a name="xaml_content_properties"></a>
## <a name="xaml-content-properties"></a>XAML コンテンツ プロパティ  
 XAML コンテンツ構文は、クラス宣言の一部として を<xref:System.Windows.Markup.ContentPropertyAttribute>指定するクラスでのみ有効になる構文です。 この<xref:System.Windows.Markup.ContentPropertyAttribute>プロパティは、その型の要素 (派生クラスを含む) のコンテンツ プロパティを参照します。 XAML プロセッサによって処理される場合、オブジェクト要素の開始タグと終了タグの間に見つかった子要素または内部テキストは、そのオブジェクトの XAML コンテンツ プロパティの値として割り当てられます。 コンテンツ プロパティに明示的なプロパティ要素を指定することは許可されていますが、この使用方法は一般に、.NET リファレンスの XAML 構文セクションには示されていません。 明示的/冗長手法は、マークアップの明瞭さやマークアップ スタイルの問題として時折値を持ちますが、通常、コンテンツ プロパティの目的は、親子として直感的に関連付けられている要素を直接入れ子にできるようにマークアップを簡素化することです。 要素の他のプロパティのプロパティ要素タグは、厳密な XAML 言語定義では "コンテンツ" として割り当てられません。これらは、以前は XAML パーサーの処理順序で処理され、"コンテンツ" とは見なされません。  
  
### <a name="xaml-content-property-values-must-be-contiguous"></a>XAML コンテンツ プロパティの値は連続している必要があります  
 XAML コンテンツ プロパティの値は、そのオブジェクト要素の他のプロパティ要素の前または後に完全に指定する必要があります。 これは、XAML コンテンツ プロパティの値が文字列として指定されているか、1 つ以上のオブジェクトとして指定されているかに関係なく、この場合です。 たとえば、次のマークアップは解析されません。  
  
```xaml  
<Button>I am a
  <Button.Background>Blue</Button.Background>  
  blue button</Button>  
```  
  
 これは、この構文が content プロパティのプロパティ要素構文を使用して明示的に行われた場合、content プロパティが 2 回設定されるため、基本的に不正です。  
  
```xaml  
<Button>  
  <Button.Content>I am a </Button.Content>  
  <Button.Background>Blue</Button.Background>  
  <Button.Content> blue button</Button.Content>  
</Button>  
```  
  
 同様に、コンテンツ プロパティがコレクションであり、子要素にプロパティ要素が散在している場合も、不正な例です。  
  
```xaml  
<StackPanel>  
  <Button>This example</Button>  
  <StackPanel.Resources>  
    <SolidColorBrush x:Key="BlueBrush" Color="Blue"/>  
  </StackPanel.Resources>  
  <Button>... is illegal XAML</Button>  
</StackPanel>  
```  
  
<a name="content_properties_and_collection_syntax_combined"></a>
## <a name="content-properties-and-collection-syntax-combined"></a>コンテンツ プロパティとコレクション構文の組み合わせ  
 複数のオブジェクト要素をコンテンツとして受け入れるには、content プロパティの型がコレクション型である必要があります。 コレクション型のプロパティ要素構文と同様に、XAML プロセッサはコレクション型の型を識別する必要があります。 要素に XAML コンテンツ プロパティがあり、XAML コンテンツ プロパティの型がコレクションである場合、暗黙のコレクション型をマークアップでオブジェクト要素として指定する必要はありません。要素。 したがって、マークアップ内の見かけのコンテンツ モデルには、コンテンツとして割り当てられた複数の子要素を持つことができます。 派生クラスのコンテンツ構文を次<xref:System.Windows.Controls.Panel>に示します。 すべての<xref:System.Windows.Controls.Panel>派生クラスは、<xref:System.Windows.Controls.Panel.Children%2A>型の値を必要とする XAML コンテンツ<xref:System.Windows.Controls.UIElementCollection>プロパティを確立します。  
  
 [!code-xaml[XAMLOvwSupport#SyntaxContent](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page5.xaml#syntaxcontent)]  
  
 マークアップでは、 の<xref:System.Windows.Controls.Panel.Children%2A>プロパティ要素も 要素<xref:System.Windows.Controls.UIElementCollection>も必要ありません。 これは XAML のデザイン機能であり、プロパティ要素タグやコレクション オブジェクト[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]を介さずに、 を定義する要素を、親子要素の直接リレーションシップを持つ要素のツリーとして、より直感的に表されます。 実際、<xref:System.Windows.Controls.UIElementCollection>マークアップでは、デザインによってオブジェクト要素として明示的に指定することはできません。 その目的は暗黙的なコレクションとしてだけであるため、<xref:System.Windows.Controls.UIElementCollection>パブリック パラメーターなしのコンストラクターを公開しないため、オブジェクト要素としてインスタンス化することはできません。  
  
### <a name="mixing-property-elements-and-object-elements-in-an-object-with-a-content-property"></a>オブジェクト内のプロパティ要素とオブジェクト要素とコンテンツ プロパティの混在  
 XAML 仕様では、XAML プロセッサが、XAML コンテンツ プロパティをオブジェクト要素内で埋めるために使用されるオブジェクト要素を、連続する必要があり、混在させてはならないことを強制できることを宣言しています。 プロパティ要素とコンテンツの混在に対するこの制限は[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、XAML プロセッサによって適用されます。  
  
 子オブジェクト要素は、オブジェクト要素内の最初の即時マークアップとして持つことができます。 次に、プロパティ要素を導入できます。 または、1 つ以上のプロパティ要素を指定してから、コンテンツを指定してから、さらに多くのプロパティ要素を指定することもできます。 ただし、プロパティ要素がコンテンツに従うと、それ以上のコンテンツを導入することはできません。  
  
 このコンテンツ/プロパティ要素の順序要件は、コンテンツとして使用される内部テキストには適用されません。 ただし、プロパティ要素に内部テキストが散在している場合、マークアップ内で有意な空白を視覚的に検出することは困難であるため、内部テキストを連続的に保つのは良いマークアップ スタイルです。  
  
<a name="xaml_namespaces"></a>
## <a name="xaml-namespaces"></a>XAML 名前空間  
 上記の構文例では、既定の XAML 名前空間以外の XAML 名前空間が指定されていません。 一般的[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]なアプリケーションでは、既定の XAML 名前空間が[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]名前空間として指定されます。 既定の XAML 名前空間以外の XAML 名前空間を指定しても、同様の構文を使用できます。 ただし、既定の XAML 名前空間内でアクセスできないクラス名の場合は、そのクラス名の前に、対応する CLR 名前空間にマップされた XAML 名前空間のプレフィックスを付ける必要があります。 たとえば、`<custom:Example/>``Example`クラスのインスタンスをインスタンス化するオブジェクト要素構文で、そのクラス (および場合によっては、バッキング型を含む外部アセンブリ情報) を含む CLR 名前空間`custom`がプレフィックスに事前にマップされている場合です。  
  
 XAML 名前空間の詳細については、「 [XAML 名前空間と WPF XAML の名前空間マッピング](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)」を参照してください。  
  
<a name="markup_extensions"></a>
## <a name="markup-extensions"></a>マークアップ拡張機能  
 XAML は、文字列属性値またはオブジェクト要素の通常の XAML プロセッサ処理からのエスケープを可能にするマークアップ拡張機能プログラミング エンティティを定義し、その処理をバッキング クラスに延期します。 属性構文を使用する場合に XAML プロセッサに対するマークアップ拡張機能を識別する文字は、左中かっこ ({) で、その後に中かっこ (}) 以外の文字が続きます。 左中かっこの後の最初の文字列は、特定の拡張動作を提供するクラスを参照する必要があります。 その後、1 つのスペースが現れ、次に、後続の各文字が、右中かっこが検出されるまで、拡張実装によって入力として使用されます。  
  
 .NET XAML 実装では<xref:System.Windows.Markup.MarkupExtension>、抽象クラスを、他のフレームワークやテクノロジでサポートされているすべての[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]マークアップ拡張機能のベースとして使用します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]マークアップ拡張機能を具体的に実装する場合は、他の既存のオブジェクトを参照する手段を提供したり、実行時に評価されるオブジェクトへの遅延参照を行ったりすることを目的としています。 たとえば、単純な WPF データ バインディングは、特定の`{Binding}`プロパティが通常使用する値の代わりにマークアップ拡張機能を指定することによって実現されます。 WPF マークアップ拡張機能の多くは、属性構文が使用できないプロパティの属性構文を有効にします。 たとえば、<xref:System.Windows.Style>オブジェクトは、入れ子になった一連のオブジェクトとプロパティを含む比較的複雑な型です。 WPF のスタイルは通常、 で<xref:System.Windows.ResourceDictionary>リソースとして定義され、リソースを要求する 2 つの WPF マークアップ拡張機能のいずれかを通じて参照されます。 マークアップ拡張機能は、プロパティ値の評価をリソース 検索に延期し、次の例のように属性構文<xref:System.Windows.FrameworkElement.Style%2A>で type<xref:System.Windows.Style>を取得してプロパティの値を提供できるようにします。  
  
 `<Button Style="{StaticResource MyStyle}">My button</Button>`  
  
 ここでは、`StaticResource`マークアップ拡張機能の<xref:System.Windows.StaticResourceExtension>実装を提供するクラスを示します。 次の文字列`MyStyle`は、既定<xref:System.Windows.StaticResourceExtension>以外のコンストラクターの入力として使用され、拡張文字列から取得されたパラメーターが要求された<xref:System.Windows.ResourceKey>. `MyStyle`は、リソースとして<xref:System.Windows.Style>定義された[x:Key](../../../desktop-wpf/xaml-services/xkey-directive.md)値であると想定されます。 [静的リソースのマークアップ拡張機能](staticresource-markup-extension.md)の使用は、読み込み時に<xref:System.Windows.Style>静的なリソース参照ロジックを使用してプロパティ値を提供するためにリソースを使用することを要求します。  
  
 マークアップ拡張機能の詳細については、 「[マークアップ拡張機能と WPF XAML](markup-extensions-and-wpf-xaml.md)」を参照してください。 マークアップ拡張機能と一般的な .NET XAML 実装で有効になっているその他の XAML プログラミング機能のリファレンスについては[、「XAML 名前空間 (x:)」を参照してください。言語機能](../../../desktop-wpf/xaml-services/namespace-language-features.md): WPF 固有のマークアップ拡張機能については、「 [WPF XAML 拡張機能](wpf-xaml-extensions.md)」を参照してください。  
  
<a name="attached_properties"></a>
## <a name="attached-properties"></a>アタッチされるプロパティ  
 添付プロパティは、XAML で導入されたプログラミング概念であり、それによって、プロパティは特定の型で所有および定義できますが、任意の要素の属性またはプロパティ要素として設定できます。 添付プロパティが意図されている主なシナリオは、マークアップ構造内の子要素が、すべての要素にわたって広範囲に共有されるオブジェクト モデルを必要とせずに、親要素に情報を報告できるようにすることです。 反対に、親要素が添付プロパティを使用して、子要素に情報を報告することができます。 添付プロパティの目的と独自の添付プロパティの作成方法の詳細については、「[添付プロパティの概要](attached-properties-overview.md)」を参照してください。  
  
 添付プロパティは、プロパティ要素構文に表面的に似た*構文を使用*します。*プロパティ名の*組み合わせ。 次の 2 つの重要な違いがあります。  
  
- 型を使用できます *。* 属性構文を使用して添付プロパティを設定する場合でも、*プロパティ名*の組み合わせ。 添付プロパティは、プロパティ名の修飾が属性構文の要件である唯一の場合です。  
  
- 添付プロパティには、プロパティ要素構文を使用することもできます。 ただし、一般的なプロパティ要素構文では、指定する*typeName*はプロパティ要素を含むオブジェクト要素です。 添付プロパティを参照している場合 *、typeName*は添付プロパティを定義するクラスであり、オブジェクト要素を含む要素ではありません。  
  
<a name="attached_events"></a>
## <a name="attached-events"></a>アタッチされるイベント  
 添付イベントは、XAML で導入されたもう 1 つのプログラミング概念で、特定の型でイベントを定義できますが、ハンドラーは任意のオブジェクト要素にアタッチできます。 WOF 実装では、アタッチされたイベントを定義する型がサービスを定義する静的な型であることが多く、場合によっては、そのサービスを公開する型のルーティング イベント エイリアスによって添付イベントが公開されることもあります。 添付イベントのハンドラーは、属性構文を使用して指定します。 添付イベントと同様に、属性構文は *、typeName*を許可するように、添付イベントに対して拡張されます。*eventName の*使用法は *、typeName*が`Add`、`Remove`添付イベント インフラストラクチャのアクセサーとイベント ハンドラー アクセサーを提供するクラスであり *、eventName*はイベント名です。  
  
<a name="anatomy_of_a_xaml_page_root_element"></a>
## <a name="anatomy-of-a-xaml-root-element"></a>XAML ルート要素の解剖学  
 次の表は、ルート要素の特定の属性を示す、一般的な XAML ルート要素を示しています。  
  
|||  
|-|-|  
|`<Page`|ルート要素のオブジェクト要素を開く|  
|`xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`|既定の[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]( ) XAML 名前空間|  
|`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`|XAML 言語 XAML 名前空間|  
|`x:Class="ExampleNamespace.ExampleCode"`|部分クラスに定義されている分離コードにマークアップを接続する部分クラス宣言|  
|`>`|ルートのオブジェクト要素の終わり。 要素に子要素が含まれているため、オブジェクトはまだ閉じられていない|  
  
<a name="optional_and_nonrecommended_xaml_usages"></a>
## <a name="optional-and-nonrecommended-xaml-usages"></a>オプションおよび推奨外の XAML の使用法  
 次のセクションでは、XAML プロセッサで技術的にサポートされているが、XAML ソースを含むアプリケーションを開発するときに、人間が読み取り可能な状態のままの XAML ファイルを妨げる詳細やその他の美的問題を生成する XAML の使用方法について説明します。  
  
### <a name="optional-property-element-usages"></a>オプションのプロパティ要素の使用方法  
 オプションのプロパティ要素の使用方法には、XAML プロセッサが暗黙的と見なす要素コンテンツ プロパティを明示的に書き出す機能が含まれます。 たとえば、<xref:System.Windows.Controls.Menu>の内容を宣言する場合、 の<xref:System.Windows.Controls.ItemsControl.Items%2A>コレクションを<xref:System.Windows.Controls.Menu>`<Menu.Items>`プロパティ要素タグとして明示的に宣言し、 の子要素をすべてに配置する<xref:System.Windows.Controls.MenuItem>`<Menu.Items>`<xref:System.Windows.Controls.Menu>必要がある暗黙的な XAML プロセッサ動作を<xref:System.Windows.Controls.MenuItem>使用するのではなく、 内に配置<xref:System.Windows.Controls.ItemsControl.Items%2A>できます。 オプションの使用法は、マークアップで表されるオブジェクト構造を視覚的に明確にするのに役立つ場合があります。 また、明示的なプロパティ要素の使用により、属性値内の入れ子になったマークアップ拡張機能など、技術的には機能するが視覚的に混乱するマークアップを回避できる場合もあります。  
  
### <a name="full-typenamemembername-qualified-attributes"></a>完全な型名.メンバー名修飾属性  
 *型名*。属性の*memberName*フォームは、実際にはルーティング イベントのケースよりも汎用的に機能します。 しかし、他の状況では、フォームは余分であり、マークアップスタイルと読みやすさの理由だけであれば、それを避けるべきです。 次の例では、<xref:System.Windows.Controls.Control.Background%2A>属性への 3 つの参照のそれぞれが完全に同じになります。  
  
 [!code-xaml[XAMLOvwSupport#TypeNameProp](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenameprop)]  
  
 `Button.Background`そのプロパティの修飾検索<xref:System.Windows.Controls.Button>が成功し (Control<xref:System.Windows.Controls.Control.Background%2A>から継承された)、<xref:System.Windows.Controls.Button>オブジェクト要素または基本クラスのクラスであるために機能します。 `Control.Background`クラスが実際<xref:System.Windows.Controls.Control>に定義<xref:System.Windows.Controls.Control.Background%2A>し、<xref:System.Windows.Controls.Control>基本クラス<xref:System.Windows.Controls.Button>であるために機能します。  
  
 ただし、次の*型は名前*です。*memberName*フォームの例は動作しないため、コメントが表示されます。  
  
 [!code-xaml[XAMLOvwSupport#TypeNameBadProp](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenamebadprop)]  
  
 <xref:System.Windows.Controls.Label>は の派生クラス<xref:System.Windows.Controls.Control>であり、オブジェクト要素内で`Label.Background`<xref:System.Windows.Controls.Label>指定した場合、この使用法は機能していたでしょう。 ただし、クラス<xref:System.Windows.Controls.Label>または基本クラス<xref:System.Windows.Controls.Button>ではないため、指定された XAML プロセッサの動作は、添付プロパティ`Label.Background`として処理します。 `Label.Background`は利用できる添付プロパティではないので、この使用は失敗します。  
  
### <a name="basetypenamemembername-property-elements"></a>プロパティ要素  
 *どのように型に*似た方法で名前を付けます。*メンバー名*フォームは、属性構文 、*基本型名*に対して機能します。*メンバー名*構文は、プロパティ要素構文に対して機能します。 たとえば、次の構文が機能します。  
  
 [!code-xaml[XAMLOvwSupport#GoofyPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofype)]  
  
 ここでは、プロパティ要素が`Control.Background``Button`に含まれている場合でも、プロパティ要素が与えられました。  
  
 しかし、*ちょうどタイプ名*のように.*属性のメンバ名*フォーム、*基本型名*。*memberName*マークアップではスタイルが不適切なので、使用しないでください。  
  
## <a name="see-also"></a>関連項目

- [XAML の概要 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [XAML 名前空間 (x:) 言語機能](../../../desktop-wpf/xaml-services/namespace-language-features.md)
- [WPF XAML 拡張機能](wpf-xaml-extensions.md)
- [依存関係プロパティの概要](dependency-properties-overview.md)
- [TypeConverters および XAML](typeconverters-and-xaml.md)
- [WPF における XAML とカスタム クラス](xaml-and-custom-classes-for-wpf.md)
