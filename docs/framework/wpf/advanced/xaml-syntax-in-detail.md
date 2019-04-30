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
ms.openlocfilehash: bf4118c6e811f409715b7b6684851b8b3e8bbb25
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61981371"
---
# <a name="xaml-syntax-in-detail"></a>XAML 構文の詳細
このトピックでは、XAML 構文の要素の説明に使用される用語を定義します。 これらの用語は、具体的には、XAML または System.Xaml レベルでの XAML 言語のサポートを有効になっている XAML の基本的な概念を使用する他のフレームワークも、このドキュメントは、WPF のドキュメントの両方の残りの部分でよく使用されます。 このトピックでは、トピックで導入された基本的な用語で展開[XAML の概要 (WPF)](xaml-overview-wpf.md)します。  

<a name="the_xaml_language_specification"></a>   
## <a name="the-xaml-language-specification"></a>XAML 言語仕様  
 ここで定義されている XAML 構文の用語の定義または、XAML 言語仕様内で参照されてもします。 XAML では、依存しか、拡張 XML の構造上のルールは XML に基づく言語です。 一部の用語はから共有されてまたは XML 言語または XML ドキュメント オブジェクト モデルを記述する場合によく使用する用語に基づきます。  
  
 XAML 言語仕様の詳細については、ダウンロード[ \[MS XAML\] ](https://go.microsoft.com/fwlink/?LinkId=114525) Microsoft ダウンロード センターから。  
  
<a name="xaml_and_clr"></a>   
## <a name="xaml-and-clr"></a>XAML と CLR  
 XAML は、マークアップ言語です。 [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]、として、名前により、ランタイムの実行によって暗黙的に指定します。 XAML は単独で、CLR ランタイムによって直接使用される一般的な言語のいずれか。 代わりに、XAML の型システムをサポートするいると考えることができます。 WPF で使用される特定の XAML 解析システムは、CLR および CLR 型システムに基づいて構築されます。 XAML の型は、WPF の XAML が解析される際、実行時の表現をインスタンス化する CLR 型にマップされます。 このため、このドキュメントの構文のディスカッションの残りの部分は、XAML 言語仕様で同等の構文の説明がない場合でも、CLR 型システムへの参照を含まれます。 (あたり、XAML 言語仕様レベルでは、XAML 型でしたにマップするその他の型システムに、CLR では、これはありませんが、作成とさまざまな XAML パーサーの使用を必要とする。)  
  
#### <a name="members-of-types-and-class-inheritance"></a>型とクラスの継承メンバー  
 プロパティおよびの XAML メンバーとして表示されますが、イベント、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]型が基本型から継承された多くの場合。 たとえば、次の例:`<Button Background="Blue" .../>`します。 <xref:System.Windows.Controls.Control.Background%2A>プロパティは、すぐに宣言されたプロパティで、<xref:System.Windows.Controls.Button>クラス、クラス定義、リフレクションの結果、またはドキュメントを確認した場合。 代わりに、<xref:System.Windows.Controls.Control.Background%2A>ベースから継承されて<xref:System.Windows.Controls.Control>クラス。  
  
 クラスの継承動作[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]XAML 要素が XML マークアップの解釈を スキーマの適用から大きな出発します。 クラスの継承は中間の基本クラスは抽象クラスで特に場合、またはインターフェイスが含まれている場合、複雑になることができます。 これは、1 つの理由の XAML 要素およびその許容属性のセットが正確かつ完全には、スキーマ型を使用して表さ難しくは通常の使用を[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]プログラミングでは、DTD または XSD 形式などです。 別の理由は、その機能を拡張し、XAML 言語自体の型のマッピング機能は、許容される型とメンバーのすべての固定表現の完全性を妨げるものでいます。  
  
<a name="object_element_syntax"></a>   
## <a name="object-element-syntax"></a>オブジェクト要素構文  
 *オブジェクト要素構文*XML 要素を宣言することで、CLR クラスまたは構造体をインスタンス化する XAML マークアップ構文です。 この構文では、HTML などの他のマークアップ言語の要素の構文に似ています。 オブジェクト要素構文は、左の山かっこで始まります (\<)、クラスまたはインスタンス化されている構造体の型名ですぐにその後にします。 0 個以上のスペースは、型の名前、および 0 個以上の属性を宣言することも、オブジェクト要素上の各属性の名前を分離する 1 つまたは複数のスペースを含む ="value"ペア。 最後に、次のいずれかが true でする必要があります。  
  
- 要素とタグは、右の山かっこ (>) をすぐに続くフォワード スラッシュ (/) で閉じる必要があります。  
  
- 開始タグは、右の山かっこ (>) で完了する必要があります。 その他のオブジェクト要素、プロパティ要素、または内部のテキストは、開始タグをフォローできます。 通常、どのようなコンテンツをここで含めることが正確には要素のオブジェクト モデルによって制限されます。 対応するオブジェクト要素のタグを終了する必要がありますも適切な入れ子でが存在し、他の開始と終了タグのペアとバランスを取る。  
  
 .NET で実装されている XAML では、オブジェクトの要素を型、プロパティまたはイベント、および CLR 名前空間とアセンブリに XAML 名前空間への属性にマッピングする規則のセットがあります。 WPF と .NET Framework では、XAML オブジェクト要素にマップされる[!INCLUDE[TLA#tla_net](../../../../includes/tlasharptla-net-md.md)]で定義された型には、アセンブリが参照されているし、属性、それらの型のメンバーにマップされます。 XAML で CLR 型を参照する場合も、その型の継承されたメンバーへのアクセスがあります。  
  
 たとえば、次の例は、の新しいインスタンスをインスタンス化するオブジェクト要素構文、<xref:System.Windows.Controls.Button>クラスし、も指定します、<xref:System.Windows.FrameworkElement.Name%2A>属性とその属性の値。  
  
 [!code-xaml[XAMLOvwSupport#SyntaxOE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxoe)]  
  
 次の例は、オブジェクト要素構文にも XAML コンテンツ プロパティの構文が含まれます。 内部テキ スト内に含まれる設定に使用される、 <xref:System.Windows.Controls.TextBox> XAML コンテンツ プロパティ、<xref:System.Windows.Controls.TextBox.Text%2A>します。  
  
 [!code-xaml[XAMLOvwSupport#ThisIsATextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#thisisatextbox)]  
  
### <a name="content-models"></a>コンテンツ モデル  
 クラスは、構文の観点から XAML オブジェクト要素としての使用方法をサポートする場合がありますが、その要素のみ正常に機能をアプリケーションまたはページに、全体的なコンテンツ モデルまたは要素ツリーの適切な位置に配置されます。 たとえば、<xref:System.Windows.Controls.MenuItem>の子としてのみ配置通常、<xref:System.Windows.Controls.Primitives.MenuBase>などのクラスを派生<xref:System.Windows.Controls.Menu>します。 コンテンツ コントロールおよびその他のクラスのページで、「解説」の一部として特定要素モデルが記載されている[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]XAML 要素として使用できるクラス。  
  
<a name="properties_of_object_elements"></a>   
## <a name="properties-of-object-elements"></a>オブジェクトの要素のプロパティ  
 XAML のプロパティは、さまざまな構文で設定されます。 どの構文は、特定のプロパティを使用できる異なりますは、設定するプロパティの基になる型システムの特性に基づいています。  
  
 プロパティの値を設定する機能や追加特性オブジェクトに、実行時のオブジェクト グラフ内に存在します。 オブジェクトの要素から作成されたオブジェクトの初期状態は、既定のコンス トラクターの動作に基づきます。 通常、アプリケーションは、完全に既定のインスタンスを任意のオブジェクト以外のものに使用されます。  
  
<a name="attribute_syntax_properties"></a>   
## <a name="attribute-syntax-properties"></a>属性の構文 (プロパティ)  
 属性構文は、既存のオブジェクト要素の属性を宣言することで、プロパティの値を設定する XAML マークアップ構文です。 属性名は、関連するオブジェクトの要素をサポートするクラスのプロパティの CLR メンバー名と一致する必要があります。 属性名には、代入演算子 (=) が続きます。 属性の値は引用符で囲まれた文字列である必要があります。  
  
> [!NOTE]
>  リテラル属性内の引用符を配置するのに代替の引用符を使用できます。 インスタンスの内部に二重引用符文字を含む文字列を宣言するのに手段として単一引用符を使用することができます。 一重または二重引用符を使用するかどうか、属性値の文字列を開いたり、閉じたりすると一致するペアを使用する必要があります。 エスケープ シーケンスやその他の手法、特定の XAML 構文によって課される文字の制限を回避するために使用できます。 参照してください[XML 文字エンティティと XAML](../../xaml-services/xml-character-entities-and-xaml.md)します。  
  
 属性構文で設定するには、プロパティはパブリックである必要があり、書き込み可能である必要があります。 バッキング型システムのプロパティの値は、値型である必要があります。 またはする必要がありますの参照型をインスタンス化されたか、関連するのにアクセスする場合は、XAML プロセッサによって参照されていることがバックアップの種類。  
  
 WPF XAML のイベント属性名として参照されているイベントではパブリックであることし、パブリック デリゲートを用意する必要があります。  
  
 プロパティまたはイベント クラスまたはオブジェクトのコンテナーの要素によってインスタンス化される構造体のメンバーである必要があります。  
  
### <a name="processing-of-attribute-values"></a>属性値の処理  
 開始タグと終わりの引用符内に含まれる文字列値は、XAML プロセッサによって処理されます。 プロパティの場合、既定の動作の処理は、基になる CLR プロパティの型によって決まります。  
  
 属性の値は、次のいずれかで塗りつぶされます次の処理順序を使用します。  
  
1. XAML プロセッサは、中かっこをまたはから派生したオブジェクトの要素が発生した場合<xref:System.Windows.Markup.MarkupExtension>を文字列として値の処理ではなくの参照先のマークアップ拡張機能の最初の評価、およびマークアップ拡張機能によって返されるオブジェクトとして使用します値。 多くの場合は、既存のオブジェクト、または実行時まで評価されないし、新しくインスタンス化されたオブジェクトではない式への参照がマークアップ拡張機能によって返されるオブジェクトになります。  
  
2. プロパティが宣言されている場合、属性付きで<xref:System.ComponentModel.TypeConverter>、またはそのプロパティの値の型が宣言されていると、属性付き<xref:System.ComponentModel.TypeConverter>属性の文字列値が変換の入力としての型コンバーターに送信され、コンバーターを返します、新しいオブジェクト インスタンス。  
  
3. 存在する場合ありません<xref:System.ComponentModel.TypeConverter>プロパティの型への直接変換が試行されます。 この最後のレベルは、XAML 言語プリミティブ型、または列挙型 (、パーサーは、一致する値をその後、アクセス) の名前付き定数の名前のチェックの間のパーサー ネイティブ値に直接変換です。  
  
#### <a name="enumeration-attribute-values"></a>列挙型の属性値  
 XAML の列挙体は、XAML パーサーで本質的に処理され、列挙型の名前付き定数のいずれかの文字列名を指定して列挙体のメンバーを指定する必要があります。  
  
 フラグ列挙値では、ネイティブな動作は属性値の文字列を処理する列挙値のいずれかに解決してです。 形式で、列挙型を指定しない*列挙*.*値*コードと同様、します。 代わりに、指定のみ*値*、および*列挙*を設定するプロパティの型が推論されます。 内の属性を指定する場合、*列挙*.*値*形式が正しく解決されません。  
  
 フラグ列挙体の場合、動作がに基づいて、<xref:System.Enum.Parse%2A?displayProperty=nameWithType>メソッド。 フラグ列挙体の複数の値を指定するには、それぞれの値をコンマで区切ります。 ただし、フラグはない列挙値を組み合わせることはできません。 たとえば、コンマ構文を使用して作成しようとすることはできません、<xref:System.Windows.Trigger>フラグ列挙体の複数の条件に機能します。  
  
```  
<!--This will not compile, because Visibility is not a flagwise enumeration.-->  
...  
<Trigger Property="Visibility" Value="Collapsed,Hidden">  
  <Setter ... />  
</Trigger>  
...  
```  
  
 XAML で設定できる属性をサポートするフラグ列挙体は、WPF 内で珍しいものです。 ただし、このような 1 つの列挙体は<xref:System.Windows.Media.StyleSimulations>します。 たとえばの「解説」で提供される例を変更するフラグ属性のコンマ区切り構文を使用できますが、、<xref:System.Windows.Documents.Glyphs>クラスです。`StyleSimulations = "BoldSimulation"`なる可能性があります`StyleSimulations = "BoldSimulation,ItalicSimulation"`します。 <xref:System.Windows.Input.KeyBinding.Modifiers%2A?displayProperty=nameWithType> 別のプロパティは、1 つ以上の列挙値を指定できます。 ただし、このプロパティがある特殊なケースでは、ため、<xref:System.Windows.Input.ModifierKeys>列挙体は、独自の型コンバーターをサポートします。 修飾子の型コンバーターは、プラス記号 (+) をコンマ (,) ではなく、区切り記号として使用します。 この変換では、"Ctrl + Alt"などの Microsoft Windows プログラミングでキーの組み合わせを表す従来の構文をサポートします。  
  
### <a name="properties-and-event-member-name-references"></a>プロパティとイベント メンバー名の参照  
 属性を指定する場合は、任意のプロパティまたはオブジェクトのコンテナーの要素をインスタンス化する CLR 型のメンバーとして存在するイベントを参照できます。  
  
 または、添付イベントの格納オブジェクト要素の独立したか、添付プロパティを参照できます。 (添付プロパティは、以下のセクションで説明しますが)。  
  
 使用して既定の名前空間を介してアクセス可能な任意のオブジェクトからすべてのイベントを付けることができます、 *typeName*.*イベント*部分的に修飾名。 この構文のルーティング イベントのハンドラーのアタッチをサポートしています、子要素が親要素からルーティング イベントを処理するために、ハンドラーは、場所もがそのイベントのメンバー テーブルにします。 この構文には、添付イベント構文が似ていますが、ここで、イベントが true の添付イベントではありません。 代わりに、修飾名を持つイベントを参照しています。 詳細については、次を参照してください。[ルーティング イベントの概要](routed-events-overview.md)します。  
  
 一部のシナリオでは、プロパティ名は属性名ではなく、属性の値として提供場合があります。 プロパティ名は、フォームで指定されたプロパティなどの修飾子を含めることができますも*ownerType*.*dependencyPropertyName*します。 XAML でスタイルまたはテンプレートを記述するとき、このシナリオが一般的です。 属性値として指定したプロパティ名の処理ルールが異なると、設定されるプロパティのタイプまたは特定の WPF サブシステムの動作によって制御されます。 詳細については、次を参照してください。[スタイルとテンプレート](../controls/styling-and-templating.md)します。  
  
 プロパティ名の別の使用方法では、属性値がプロパティ間のリレーションシップについて説明します。 この機能は、データ バインディングとストーリー ボードのターゲットに使用されで有効になって、<xref:System.Windows.PropertyPath>クラスとその型コンバーター。 検索セマンティクスの詳細については、次を参照してください。 [PropertyPath の XAML 構文](propertypath-xaml-syntax.md)します。  
  
<a name="property_element_syntax"></a>   
## <a name="property-element-syntax"></a>プロパティ要素構文  
 *プロパティ要素構文*やや要素の基本的な XML 構文規則から逸脱した構文です。 XML では、属性の値が事実上の文字列には、可能な唯一のバリエーションを持つされる文字列エンコード方式が使用されています。 XAML、他のオブジェクトの要素をプロパティの値を割り当てることができます。 この機能は、プロパティ要素構文で有効です。 開始要素を使用してプロパティを指定、要素タグ内の属性として指定されているプロパティの代わりにタグを付ける*elementTypeName*.*propertyName*フォーム内で、プロパティの値が指定され、プロパティ要素が閉じられるします。  
  
 構文が左の山かっこで始まる具体的には、(\<)、クラスまたはプロパティ要素構文が含まれる構造体の型名ですぐにその後にします。 これが続きますすぐに 1 つのドット (.)、プロパティの名前で、右の山かっこ (>)。 属性構文と同様、そのプロパティは、指定した型の宣言されたパブリック メンバーに配置する必要があります。 プロパティに割り当てられる値は、プロパティ要素内に含まれています。 通常、値が、1 つ以上のオブジェクトの要素を指定、アドレスにプロパティ要素構文は、シナリオは、値としてオブジェクトを指定するためです。 最後に、同じを指定する同等の終了タグ*elementTypeName*.*propertyName*入れ子とその他の要素タグとのバランスが適切な組み合わせも指定する必要があります。  
  
 次のプロパティ要素構文は、たとえば、<xref:System.Windows.FrameworkElement.ContextMenu%2A>のプロパティを<xref:System.Windows.Controls.Button>します。  
  
 [!code-xaml[XAMLOvwSupport#ContextMenu](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#contextmenu)]  
  
 プロパティ要素内の値も指定できます、プリミティブ値型が指定されているプロパティの型である場合に、内部テキ ストとしてなど<xref:System.String>、または名前が指定されている列挙体。 構文がシンプルで属性を使用する可能性がありますもこれらの各ケースがあるために、これら 2 つの使用方法はあまり一般的ではありません。 文字列にプロパティ要素を 1 つのシナリオは、XAML コンテンツ プロパティではありませんが、UI のテキストの表示のために使用されるプロパティと、改行など特定の空白要素は、その UI テキストに表示される必要があります。 属性構文はラインフィード、保持することはできませんが、プロパティ要素構文は、重要なは、空白の維持がアクティブになっている限り (詳細については、次を参照してください。[スペースで XAML 処理](../../xaml-services/whitespace-processing-in-xaml.md))。 別のシナリオはように[X:uid ディレクティブ](../../xaml-services/x-uid-directive.md)プロパティ要素に適用できるし、したがってを BAML の出力を WPF でローカライズする必要がある値、またはその他の技法によって内の値をマークします。  
  
 Property 要素は、WPF の論理ツリーでは表されません。 プロパティ要素は、プロパティを設定するため構文だけでインスタンスまたはオブジェクトのバックアップがある要素ではありません。 (論理ツリーの概念について詳しくは、次を参照してください[WPF のツリー](trees-in-wpf.md)。)。  
  
 プロパティの属性とプロパティの両方の要素の構文がサポートされている場合、2 つの構文では、構文の間で若干異なる空白文字の処理などの微妙なが、同じ結果が一般にあります。  
  
<a name="collection_syntax"></a>   
## <a name="collection-syntax"></a>コレクションの構文  
 XAML 仕様では、XAML プロセッサ実装で、値の型がコレクションのプロパティを識別する必要があります。 .NET での一般的な XAML プロセッサ実装をマネージ コードと、CLR に基づいておりで、次のいずれかのコレクション型を識別します。  
  
- 実装の入力<xref:System.Collections.IList>します。  
  
- 実装の入力<xref:System.Collections.IDictionary>します。  
  
- 型から派生して<xref:System.Array>(XAML での配列の詳細については、次を参照してください[X:array マークアップ拡張機能](../../xaml-services/x-array-markup-extension.md)。)。  
  
 プロパティの型がコレクションの場合、推論されるコレクション型をマークアップにはオブジェクト要素として指定する必要はありません。 代わりに、コレクション内の項目となる要素は、プロパティ要素の 1 つまたは複数の子要素として指定されます。 それらの各項目が読み込み時にオブジェクトを評価し、呼び出すことによって、コレクションに追加、`Add`暗黙のコレクションのメソッド。 たとえば、<xref:System.Windows.Style.Triggers%2A>プロパティの<xref:System.Windows.Style>は特殊なコレクション型を受け取ります<xref:System.Windows.TriggerCollection>、実装する<xref:System.Collections.IList>します。 インスタンスを作成する必要はありません、<xref:System.Windows.TriggerCollection>マークアップ内のオブジェクト要素。 1 つまたは複数を指定する代わりに、<xref:System.Windows.Trigger>項目内の要素として、`Style.Triggers`プロパティ要素を<xref:System.Windows.Trigger>(または派生クラス) は厳密に型指定されたと暗黙的な項目の種類として期待される型です。 <xref:System.Windows.TriggerCollection>。  
  
 [!code-xaml[XAMLOvwSupport#SyntaxPECollection](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/Page1.xaml#syntaxpecollection)]  
  
 プロパティは、コレクション型とその型の XAML コンテンツ プロパティの両方があり、派生型のこのトピックの次のセクションで説明されるは。  
  
 暗黙的なコレクションの要素は、要素としてのマークアップでない場合でも、論理ツリー表現でメンバーを作成します。 通常は親の型のコンス トラクターは、そのプロパティの 1 つであるコレクションのインスタンス化を実行して、最初は空のコレクション オブジェクト ツリーの一部になります。  
  
> [!NOTE]
>  ジェネリック リストとディクショナリ インターフェイス (<xref:System.Collections.Generic.IList%601>と<xref:System.Collections.Generic.IDictionary%602>) コレクションの検出はサポートされていません。 ただし、使用することができます、<xref:System.Collections.Generic.List%601>クラスの基底クラスとして実装するため、<xref:System.Collections.IList>を直接または<xref:System.Collections.Generic.Dictionary%602>基底クラスとして実装するため、<xref:System.Collections.IDictionary>直接します。  
  
 コレクション型の .NET リファレンス ページをコレクションのオブジェクト要素の意図的に省略は、この構文は、場合によっては XAML 構文のセクションで暗黙の型のコレクション構文として説明します。  
  
 を除き、ルート要素が実際には、次の場合の一方または両方を要素に別の要素の子要素として入れ子になっている XAML ファイル内のすべてのオブジェクト要素その親要素のコレクションの暗黙的なプロパティのメンバー。、または親要素 (XAML コンテンツ プロパティは、以下のセクションで説明) の XAML コンテンツ プロパティの値を指定する要素。 つまり、親要素とマークアップ ページ内の子要素のリレーションシップは、ルートにある 1 つのオブジェクトと、ルートの下にあるすべてのオブジェクト要素は、親のプロパティ値を提供する 1 つのインスタンスか、列内の項目のいずれか親のコレクション型プロパティ値でもある lection します。 このシングル ルート概念は、XML、および XAML の負荷の Api の動作の強化は頻繁に<xref:System.Windows.Markup.XamlReader.Load%2A>します。  
  
 次の例は、コレクションのオブジェクト要素構文 (<xref:System.Windows.Media.GradientStopCollection>) を明示的に指定します。  
  
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
  
 常に、コレクションを明示的に宣言することに注意してください。 宣言しようとして、<xref:System.Windows.TriggerCollection>前に示したで明示的に<xref:System.Windows.Style.Triggers%2A>の例は失敗します。 コレクションを明示的に宣言する必要があります、コレクション クラスが既定のコンス トラクターをサポートする必要がありますと<xref:System.Windows.TriggerCollection>既定コンス トラクターがありません。  
  
<a name="xaml_content_properties"></a>   
## <a name="xaml-content-properties"></a>XAML コンテンツのプロパティ  
 XAML のコンテンツ構文は、指定のクラスでのみ有効になっている構文、<xref:System.Windows.Markup.ContentPropertyAttribute>クラス宣言の一部として。 <xref:System.Windows.Markup.ContentPropertyAttribute>要素 (派生クラスを含む) の種類のコンテンツ プロパティであるプロパティ名を参照します。 XAML プロセッサによって処理された、すべての子要素またはオブジェクトの要素の終了タグとの間で検出された内部テキ ストは、そのオブジェクトの XAML コンテンツ プロパティの値に割り当てるは。 コンテンツのプロパティの明示的なプロパティ要素を指定することは、この使用法は、一般に .NET リファレンスの XAML 構文のセクションでは表示されません。 明示的な/verbose 手法がマークアップをわかりやすくするため、またはマークアップのスタイルの問題を親と子として直感的に関連する要素を直接はネストされるように、マークアップを効率化するコンテンツ プロパティの目的は、通常は。 厳密な XAML 言語の定義; ごとには、"content"として他のプロパティ要素のプロパティ要素タグが割り当てられていません。以前、XAML パーサーの処理順序で処理され、「コンテンツ」であると見なされない。  
  
### <a name="xaml-content-property-values-must-be-contiguous"></a>XAML コンテンツ プロパティの値が連続する必要があります。  
 XAML コンテンツ プロパティの値は、そのオブジェクト要素の前に、またはその他のすべてのプロパティ要素の後、指定する必要があります。 これは、文字列、または 1 つまたは複数のオブジェクトとして、XAML コンテンツ プロパティの値が指定されているかどうか。 たとえば、次のマークアップを解析できません。  
  
```  
<Button>I am a   
  <Button.Background>Blue</Button.Background>  
  blue button</Button>  
```  
  
 これは基本的には正しくない場合、この構文は、コンテンツのプロパティのプロパティ要素構文を使用して明示的に行われた、し、コンテンツのプロパティが 2 回設定するためです。  
  
```xml  
<Button>  
  <Button.Content>I am a </Button.Content>  
  <Button.Background>Blue</Button.Background>  
  <Button.Content> blue button</Button.Content>  
</Button>  
```  
  
 同様に無効な例は、コンテンツのプロパティは、コレクションと、プロパティ要素が子要素が混じっているかどうかには。  
  
```xml  
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
 そのまま使用するために複数のコンテンツとして 1 つのオブジェクト要素コンテンツのプロパティの型する必要があります具体的にはコレクション型であります。 XAML プロセッサする必要があります特定コレクション型である型をコレクション型のプロパティ要素構文と同様に、します。 要素に XAML コンテンツ プロパティがあり、ユーザーが XAML コンテンツ プロパティの型がコレクションは、暗黙的なコレクション型はオブジェクト要素としてのマークアップで指定する必要はありません。 し、XAML コンテンツ プロパティがプロパティ el として指定する必要はありません。ement します。 そのため、マークアップで明らかなコンテンツ モデル コンテンツとして割り当てられている 1 つ以上の子要素を指定できます。 コンテンツの構文を次に、<xref:System.Windows.Controls.Panel>クラスを派生します。 すべて<xref:System.Windows.Controls.Panel>派生クラス設定の XAML コンテンツ プロパティを<xref:System.Windows.Controls.Panel.Children%2A>、型の値がありますが、<xref:System.Windows.Controls.UIElementCollection>します。  
  
 [!code-xaml[XAMLOvwSupport#SyntaxContent](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page5.xaml#syntaxcontent)]  
  
 注意のどちらも、プロパティ要素<xref:System.Windows.Controls.Panel.Children%2A>もの要素、<xref:System.Windows.Controls.UIElementCollection>マークアップが必要です。 再帰的に定義する要素に含まれているようにこれは、XAML のデザイン機能、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]より直感的に、プロパティ要素タグの介在することがなく、直接の親の子要素の関係を持つ入れ子になった要素のツリーとして表される、またはコレクション オブジェクト。 実際、<xref:System.Windows.Controls.UIElementCollection>できません明示的に指定するマークアップでオブジェクト要素として設計できます。 唯一の意図された用途は、暗黙の型のコレクションとしてため<xref:System.Windows.Controls.UIElementCollection>はパブリックの既定のコンス トラクターを公開しませんし、そのため、オブジェクト要素としてインスタンス化できることはできません。  
  
### <a name="mixing-property-elements-and-object-elements-in-an-object-with-a-content-property"></a>プロパティ要素とコンテンツのプロパティを持つオブジェクトのオブジェクト要素の混在  
 XAML 仕様は、XAML プロセッサは、オブジェクト要素内の XAML コンテンツ プロパティに使用されるオブジェクトの要素は、連続する必要があり、混在できません適用することができますを宣言します。 プロパティ要素とコンテンツの混在に対するこの制限が適用される、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML プロセッサ。  
  
 オブジェクトの子要素は、オブジェクト要素内の最初の即時マークアップとして設定できます。 プロパティ要素を導入できます。 または、1 つまたは複数のプロパティ要素では、コンテンツ、プロパティ要素を指定することができます。 プロパティ要素コンテンツに依存して、さらに、コンテンツを導入することはできません、プロパティ要素にのみ追加することができます。  
  
 このコンテンツをコンテンツとして使用される内部のテキストはプロパティ要素の順序の要件は適用されません。 ただし、有意の空白はプロパティ要素内部のテキストが混在している場合に、マークアップで視覚的に検出を困難になるために、内部テキ ストを連続して、保持するマークアップ スタイルではまだ。  
  
<a name="xaml_namespaces"></a>   
## <a name="xaml-namespaces"></a>XAML 名前空間  
 上記の構文例の既定の XAML 名前空間以外の XAML 名前空間を指定しなければ。 一般的な[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]に指定する XAML 名前空間の既定のアプリケーション、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]名前空間。 既定の XAML 名前空間以外の XAML 名前空間を指定し、同様の構文を引き続き使用できます。 次に、任意の場所で、クラスの名前が既定の XAML 名前空間内でアクセス可能でないクラス名にする必要がありますの前に、XAML 名前空間のプレフィックスに対応する CLR 名前空間にマップします。 たとえば、`<custom:Example/>`のインスタンスをインスタンス化するオブジェクト要素構文には、`Example`クラス、そのクラス (および場合によってバッキング型を含む外部アセンブリ情報) を含む CLR 名前空間を以前に割り当てられて、`custom`プレフィックス。  
  
 XAML 名前空間の詳細については、次を参照してください。 [XAML 名前空間および WPF XAML のマッピングの Namespace](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)します。  
  
<a name="markup_extensions"></a>   
## <a name="markup-extensions"></a>マークアップ拡張機能  
 XAML では、通常 XAML プロセッサの処理は、文字列属性値またはオブジェクトの要素からエスケープを有効にし、バッキング クラスに処理を延期するエンティティをプログラミングするマークアップ拡張機能を定義します。 この文字は、右中かっこ (}) 以外の任意の文字が続く開く中かっこ ({}) は、属性構文を使用するときに、XAML プロセッサにマークアップ拡張機能を確認します。 中かっこの後の最初の文字列には、その部分文字列が真のクラス名の一部である場合、特定の拡張機能の動作は、参照が、部分文字列を省略できます"Extension"を提供するクラスを参照する必要があります。 その後は単一の空白が表示されますし、後続の各文字が入力として使用拡張機能の実装で中かっこが検出されるまで。  
  
 .NET の XAML 実装を使用して、<xref:System.Windows.Markup.MarkupExtension>でサポートされているマークアップ拡張機能のすべての基礎として抽象クラス[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]他のフレームワークやテクノロジとします。 マークアップ拡張機能を[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]具体的には実装が他の既存のオブジェクトを参照する、または実行時に評価されるオブジェクトに遅延の参照を作成する手段を提供する多くの場合、対象としています。 たとえば、単純な WPF データ バインドが指定して行うこと、`{Binding}`を通常、特定のプロパティ値の代わりに、マークアップ拡張機能。 WPF のマークアップ拡張機能の多くには、属性構文は属性構文を利用できないプロパティが有効にします。 たとえば、<xref:System.Windows.Style>オブジェクトは、比較的複雑な型を入れ子になった一連オブジェクトおよびプロパティにはが含まれています。 通常、WPF でのスタイルはリソースとして定義を<xref:System.Windows.ResourceDictionary>、リソースを要求する WPF のマークアップの 2 つの拡張機能のいずれかで参照します。 マークアップ拡張機能リソースの検索、プロパティ値の評価を延期し、値を提供できるように、<xref:System.Windows.FrameworkElement.Style%2A>プロパティ、型を取得<xref:System.Windows.Style>で、次の例に示す構文を属性します。  
  
 `<Button Style="{StaticResource MyStyle}">My button</Button>`  
  
 ここでは、`StaticResource`識別、<xref:System.Windows.StaticResourceExtension>マークアップ拡張機能の実装を提供するクラス。 次の文字列`MyStyle`既定以外の入力として使用<xref:System.Windows.StaticResourceExtension>コンス トラクター、拡張機能の文字列から取得されているパラメーターが、要求された宣言して<xref:System.Windows.ResourceKey>します。 `MyStyle` 必要です、 [X:key](../../xaml-services/x-key-directive.md)の値を<xref:System.Windows.Style>をリソースとして定義されます。 [StaticResource マークアップ拡張機能](staticresource-markup-extension.md)使用状況が提供する、リソースを使用することを要求、<xref:System.Windows.Style>読み込み時に静的リソースの検索ロジックを使用してプロパティ値。  
  
 マークアップ拡張機能の詳細については、 「[マークアップ拡張機能と WPF XAML](markup-extensions-and-wpf-xaml.md)」を参照してください。 マークアップ拡張機能とプログラミング機能の一般的な .NET の XAML 実装で有効になっている他の XAML の参照を次を参照してください[XAML Namespace (x:)。言語機能](../../xaml-services/xaml-namespace-x-language-features.md)します。 WPF 固有のマークアップ拡張機能を参照してください。 [WPF XAML 拡張機能](wpf-xaml-extensions.md)します。  
  
<a name="attached_properties"></a>   
## <a name="attached-properties"></a>アタッチされるプロパティ  
 添付プロパティは XAML のプロパティを所有しているし、特定の型によって定義されたで導入された、プログラミングの概念上の任意の要素が属性またはプロパティ要素として設定します。 主に、すべての要素の間で、広範囲に共有されたオブジェクト モデルを必要とせず、親要素に情報を報告するマークアップの構造内の子要素を有効にするのには、添付プロパティを意図しています。 逆に、添付プロパティは、子要素に情報を報告する親要素によって使用できます。 目的の添付プロパティと、独自に作成する方法の詳細については、プロパティを接続を参照してください。[添付プロパティの概要](attached-properties-overview.md)します。  
  
 添付プロパティは、一見プロパティ要素構文のような構文を使用で指定することも、 *typeName*.*propertyName*の組み合わせ。 次の 2 つの重要な違いがあります。  
  
- 使用することができます、 *typeName*.*propertyName*属性構文で添付プロパティを設定するときに、偶数の組み合わせ。 添付プロパティは、唯一のケースはプロパティ名を修飾する、属性構文の要件です。  
  
- 添付プロパティのプロパティ要素構文を使用することもできます。 ただし、一般的なプロパティ要素構文での*typeName*プロパティ要素が含まれるオブジェクトの要素を指定します。 添付プロパティを指定する場合、 *typeName*はオブジェクト要素ではなく、添付プロパティを定義するクラスです。  
  
<a name="attached_events"></a>   
## <a name="attached-events"></a>アタッチされるイベント  
 添付イベントは、イベントは、特定の種類で定義できますが、オブジェクト要素のハンドラーが接続されている XAML で導入されたもう 1 つのプログラミング概念です。 WOF の実装で多くの場合、添付イベントを定義する型は、サービスを定義する静的な型と、サービスを公開する型でルーティング イベントのエイリアスを使用してこれらの添付イベントを公開することがあります。 添付イベントのハンドラーは、属性構文で指定されます。 許可する添付イベントの属性の構文を展開する添付イベントは、使用、 *typeName*.*eventName*の使用状況、 *typeName*を提供するクラスは、`Add`と`Remove`、添付イベント インフラストラクチャのためのイベント ハンドラーのアクセサーと*eventName*イベントの名前を指定します。  
  
<a name="anatomy_of_a_xaml_page_root_element"></a>   
## <a name="anatomy-of-a-xaml-root-element"></a>XAML ルート要素の構造  
 次の表は、一般的な XAML ルート要素は、ルート要素の特定の属性の表示を示しています。  
  
|||  
|-|-|  
|`<Page`|ルート要素の開始オブジェクトの要素|  
|`xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"`|既定値 ([!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]) XAML 名前空間|  
|`xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`|XAML 言語の XAML 名前空間|  
|`x:Class="ExampleNamespace.ExampleCode"`|部分クラスに定義されたマークアップを分離コードに接続する部分クラス宣言|  
|`>`|ルートのオブジェクト要素の終了。 要素に子要素が含まれているために、オブジェクトはまだ閉じられていません|  
  
<a name="optional_and_nonrecommended_xaml_usages"></a>   
## <a name="optional-and-nonrecommended-xaml-usages"></a>省略可能で、非推奨の XAML の使用法  
 次のセクションでは、技術的には、XAML プロセッサでサポートされているが、詳細やその他の XAML ソースを含むアプリケーションを開発するときに、人間が判読できる残りの XAML ファイルに干渉する見た目の問題を生成する XAML の使用法について説明します。  
  
### <a name="optional-property-element-usages"></a>省略可能なプロパティ要素の使用状況  
 省略可能なプロパティ要素の使用状況にで、XAML プロセッサが暗黙の型は考慮要素のコンテンツ プロパティを明示的に記述が含まれます。 内容を宣言する場合など、<xref:System.Windows.Controls.Menu>を明示的に宣言することもできます、<xref:System.Windows.Controls.ItemsControl.Items%2A>のコレクション、<xref:System.Windows.Controls.Menu>として、`<Menu.Items>`プロパティ要素のタグおよび配置<xref:System.Windows.Controls.MenuItem>内`<Menu.Items>`ではなく、暗黙的な XAML プロセッサの動作を使用するよりものすべての子要素を<xref:System.Windows.Controls.Menu>必要があります、<xref:System.Windows.Controls.MenuItem>に配置し、<xref:System.Windows.Controls.ItemsControl.Items%2A>コレクション。 場合がありますの省略可能な使用状況を視覚的に、マークアップで表されるオブジェクトの構造が明確にできます。 または、明示的なプロパティ要素の使用は技術的には、属性値内の入れ子になったマークアップ拡張機能など、視覚的に混乱しますが、機能するマークアップを回避することがあります。  
  
### <a name="full-typenamemembername-qualified-attributes"></a>完全な typeName.memberName 属性の修飾  
 *TypeName*.*memberName*フォームは、属性、実際には、ルーティング イベント ケースのみより汎用的です。 他の状況ではそのフォームは不要でありのみマークアップ スタイルと読みやすさの原因の場合、それを避ける必要があります。 参照、3 つ次の例では、<xref:System.Windows.Controls.Control.Background%2A>属性は完全に同等です。  
  
 [!code-xaml[XAMLOvwSupport#TypeNameProp](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenameprop)]  
  
 `Button.Background` 有効では、そのプロパティの修飾参照<xref:System.Windows.Controls.Button>が成功すると (<xref:System.Windows.Controls.Control.Background%2A>コントロールから継承された) と<xref:System.Windows.Controls.Button>はオブジェクト要素のクラスまたは基本クラス。 `Control.Background` 動作のため、<xref:System.Windows.Controls.Control>クラスは、実際に定義<xref:System.Windows.Controls.Control.Background%2A>と<xref:System.Windows.Controls.Control>は、<xref:System.Windows.Controls.Button>基本クラス。  
  
 ただし、次*typeName*.*memberName* form の例は行われず、コメントがあるため表示されます。  
  
 [!code-xaml[XAMLOvwSupport#TypeNameBadProp](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#typenamebadprop)]  
  
 <xref:System.Windows.Controls.Label> 別の派生クラスは、 <xref:System.Windows.Controls.Control>、指定した場合と`Label.Background`内、<xref:System.Windows.Controls.Label>オブジェクト要素の場合は、この使用法がならばします。 ただし、ため<xref:System.Windows.Controls.Label>クラスまたは基底クラスのない<xref:System.Windows.Controls.Button>を処理し、指定した XAML プロセッサの動作は、`Label.Background`添付プロパティとして。 `Label.Background` 使用可能な添付プロパティでないし、この使用法が失敗します。  
  
### <a name="basetypenamemembername-property-elements"></a>baseTypeName.memberName プロパティ要素  
 方法と同様の方法で、 *typeName*.*memberName*属性構文では、フォームの動作を*baseTypeName*.*memberName*プロパティ要素構文の構文の動作します。 たとえば、次の構文は動作します。  
  
 [!code-xaml[XAMLOvwSupport#GoofyPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofype)]  
  
 ここでは、property 要素は、として指定された`Control.Background`にプロパティ要素が含まれている場合でも`Button`します。  
  
 同じように、 *typeName*.*memberName*属性について、フォーム*baseTypeName*.*memberName*マークアップでは、不適切なスタイルは、これを避ける必要があります。  
  
## <a name="see-also"></a>関連項目

- [XAML の概要 (WPF)](xaml-overview-wpf.md)
- [XAML Namespace (x:)言語機能](../../xaml-services/xaml-namespace-x-language-features.md)
- [WPF XAML 拡張機能](wpf-xaml-extensions.md)
- [依存関係プロパティの概要](dependency-properties-overview.md)
- [TypeConverters および XAML](typeconverters-and-xaml.md)
- [WPF における XAML とカスタム クラス](xaml-and-custom-classes-for-wpf.md)
