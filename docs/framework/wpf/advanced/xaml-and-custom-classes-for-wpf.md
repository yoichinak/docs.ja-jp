---
title: XAML クラスとカスタム クラス
ms.date: 03/30/2017
helpviewer_keywords:
- custom classes in XAML [WPF]
- XAML [WPF], custom classes
- classes [WPF], custom classes in XAML
ms.assetid: e7313137-581e-4a64-8453-d44e15a6164a
ms.openlocfilehash: 4cd0ba7fa03d2578f4477c3ccf53188fbbea2dbd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186265"
---
# <a name="xaml-and-custom-classes-for-wpf"></a>WPF における XAML とカスタム クラス
共通言語ランタイム (CLR) フレームワークで実装された XAML は、共通言語ランタイム (CLR) 言語でカスタム クラスまたはカスタム構造を定義し、XAML マークアップを使用してそのクラスにアクセスする機能をサポートしています。 通常は、カスタム型を[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]XAML 名前空間プレフィックスにマップすることで、同じマークアップ ファイル内で -defined 型とカスタム型を組み合わせて使用できます。 このトピックでは、XAML 要素として使用するためにカスタム クラスが満たす必要がある要件について説明します。  

<a name="Custom_Classes_in_Applications_vs__in_Assemblies"></a>
## <a name="custom-classes-in-applications-or-assemblies"></a>アプリケーションまたはアセンブリのカスタム クラス  
 XAML で使用されるカスタム クラスは、分離コード内またはプライマリ[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]アプリケーションを生成する他のコード内、または実行可能ファイルやクラス ライブラリとして使用される DLL などの個別のアセンブリ内のクラスとして、2 つの異なる方法で定義できます。 これらのアプローチには、それぞれ特に長所と短所があります。  
  
- クラス ライブラリを作成する利点は、このようなカスタム クラスをさまざまなアプリケーション間で共有できることです。 また、独立したライブラリを使用すると、アプリケーションのバージョン管理の問題を簡単に制御でき、XAML ページ上のルート要素として使用するクラスを簡単に作成できます。  
  
- アプリケーションでカスタム クラスを定義する利点は、この手法が比較的軽量であり、メイン アプリケーションの実行可能ファイル以外に別のアセンブリを導入するときに発生する配置とテストの問題を最小限に抑える点です。  
  
- XAML で要素として使用するには、同じアセンブリで定義されている場合でも、異なるアセンブリで定義されている場合でも、カスタム クラスを CLR 名前空間と XML 名前空間の間でマップする必要があります。 [「WPF XAML の XAML 名前空間と名前空間マッピング](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)」を参照してください。  
  
<a name="Requirements_for_a_Custom_Class_as_a_XAML_Element"></a>
## <a name="requirements-for-a-custom-class-as-a-xaml-element"></a>XAML 要素としてのカスタム クラスの要件  
 オブジェクト要素としてインスタンス化できるようにするには、クラスが次の要件を満たしている必要があります。  
  
- カスタム クラスはパブリッククラスで、既定の (パラメーターなしの) パブリック コンストラクターをサポートする必要があります。 (構造に関する注意事項については、次のセクションを参照してください。  
  
- カスタム クラスは、入れ子になったクラスであってはなりません。 入れ子になったクラスと、一般的な CLR の使用構文の[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]"ドット" は、添付プロパティなどの他の機能や XAML 機能と干渉します。  
  
 オブジェクト定義では、オブジェクト要素構文を有効にするだけでなく、そのオブジェクトを値型として受け取るその他のパブリック プロパティに対するプロパティ要素構文も有効にします。 これは、オブジェクトがオブジェクト要素としてインスタンス化され、そのようなプロパティのプロパティ要素値を埋めることができるためです。  
  
### <a name="structures"></a>構造体  
 カスタム型として定義した構造体は、 XAML で[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]常に構築できます。これは、CLR コンパイラが、すべてのプロパティ値を既定値に初期化する構造体のパラメーターなしのコンストラクターを暗黙的に作成するためです。 場合によっては、構造の既定の構築動作やオブジェクト要素の使用が望ましくないことがあります。 これは、構造体が値を埋め、概念的に和集合として機能することを意図しているためであり、含まれる値が相互に排他的な解釈を持ち、したがってそのプロパティのいずれも設定可能でない可能性があります。 このような[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]構造の例は<xref:System.Windows.GridLength>です。 一般に、このような構造体は、値が属性形式で表現できるように型コンバーターを実装する必要があります。 構造体は、パラメーターなしのコンストラクターを使用してコード構築の同様の動作を公開する必要もあります。  
  
<a name="Requirements_for_Properties_of_a_Custom_Class_as_XAML"></a>
## <a name="requirements-for-properties-of-a-custom-class-as-xaml-attributes"></a>XAML 属性としてのカスタム クラスのプロパティの要件  
 プロパティは、値による型 (プリミティブなど) を参照するか、XAML プロセッサがアクセスできるパラメーターなしのコンストラクターまたは専用の型コンバーターを持つ型のクラスを使用する必要があります。 CLR XAML 実装では、XAML プロセッサは、言語プリミティブのネイティブ サポートを通じて、または型またはバ<xref:System.ComponentModel.TypeConverterAttribute>ッキング型定義のメンバーへのアプリケーションを通じて、このようなコンバーターを検索します。  
  
 また、プロパティは抽象クラス型またはインターフェイスを参照する場合もあります。 抽象クラスまたはインターフェイスの場合、XAML 解析の期待値は、プロパティ値がインターフェイスを実装する実用的なクラス インスタンス、または抽象クラスから派生する型のインスタンスで満たされる必要があります。  
  
 プロパティは抽象クラスで宣言できますが、抽象クラスから派生する実用的なクラスでのみ設定できます。 これは、クラスのオブジェクト要素を作成するには、クラスに対してパブリック なパラメーターなしのコンストラクターが必要であるためです。  
  
### <a name="typeconverter-enabled-attribute-syntax"></a>型コンバーター有効属性構文  
 クラス レベルで専用の属性付き型コンバーターを提供する場合、適用された型変換は、その型をインスタンス化する必要があるプロパティの属性構文を有効にします。 型コンバーターは、型のオブジェクト要素の使用を有効にしません。その型のパラメーターなしのコンストラクターが存在するだけで、オブジェクト要素の使用が可能になります。 したがって、型コンバーターが有効になっているプロパティは、型自体がオブジェクト要素構文もサポートしていない限り、プロパティ構文では通常使用できません。 ただし、プロパティ要素の構文を指定することはできますが、プロパティ要素に文字列を含めることができます。 この使用法は属性構文の使用と本質的に同等であり、属性値の強固な空白の処理が必要でない限り、このような使用法は一般的ではありません。 たとえば、次に示しているのは、文字列を受け取るプロパティ要素の使用方法と、属性の使用法と同等です。  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe)]  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe2)]  
  
 属性構文が許可されているプロパティの例では、XAML を使用してオブジェクト要素を含むプロパティ要素構文は、型を<xref:System.Windows.Input.Cursor>取得するさまざまなプロパティです。 この<xref:System.Windows.Input.Cursor>クラスには専用の型コンバーター<xref:System.Windows.Input.CursorConverter>がありますが、パラメーターなしのコンストラクターは公開されないため、実際<xref:System.Windows.FrameworkElement.Cursor%2A><xref:System.Windows.Input.Cursor>の型が参照型であっても、プロパティは属性構文を使用してのみ設定できます。  
  
### <a name="per-property-type-converters"></a>プロパティごとの型コンバーター  
 または、プロパティ自体がプロパティ レベルで型コンバーターを宣言することもできます。 これにより、属性の入力文字列値を適切な型に基づいて操作の入力として処理することにより、プロパティの型のオブジェクトを<xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>インラインでインスタンス化する "ミニ言語" が有効になります。 通常、これは便利なアクセサーを提供するために行われ、XAML でプロパティを設定する唯一の手段としては行われません。 ただし、パラメーターなしのコンストラクターまたは属性付き型コンバーターを提供しない既存の CLR 型を使用する場合は、型コンバーターを属性に使用することもできます。 API の[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]例として、型を取得する<xref:System.Globalization.CultureInfo>特定のプロパティがあります。 この場合、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]以前のバージョンのフレームワークで使用されていた<xref:System.Globalization.CultureInfo>互換性と移行シナリオに対応するために既存の Microsoft .NET Framework 型を使用しましたが<xref:System.Globalization.CultureInfo>、XAML プロパティ値として直接使用できるように、必要なコンストラクターや型レベルの型変換をサポートしていません。  
  
 XAML の使用法を持つプロパティを公開する場合は、特にコントロールの作成者である場合は、依存関係プロパティを使用してそのプロパティをバッキングすることを強くお勧めします。 これは、バッキングを使用してパフォーマンスを[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]向上させることができるため、XAML プロセッサの既存の実装を使用<xref:System.Windows.DependencyProperty>する場合に特に当てはまります。 依存関係プロパティは、XAML アクセス可能なプロパティに対してユーザーが期待するプロパティのプロパティ システム機能を公開します。 これには、アニメーション、データ バインディング、スタイル サポートなどの機能が含まれます。 詳細については、「[カスタム依存関係プロパティ](custom-dependency-properties.md)」および「 [XAML の読み込みと依存関係プロパティ](xaml-loading-and-dependency-properties.md)」を参照してください。  
  
### <a name="writing-and-attributing-a-type-converter"></a>型コンバーターの記述と帰属  
 場合によっては、プロパティ型の型変換<xref:System.ComponentModel.TypeConverter>を提供するカスタム派生クラスを記述する必要があります。 XAML の使用法をサポートする型コンバーターを派生および作成する方法、および<xref:System.ComponentModel.TypeConverterAttribute>を適用する方法については[、「TypeConverters と XAML](typeconverters-and-xaml.md)」を参照してください。  
  
<a name="Requirements_for_Events_of_a_Custom_Class_as_XAML"></a>
## <a name="requirements-for-xaml-event-handler-attribute-syntax-on-events-of-a-custom-class"></a>カスタム クラスのイベントに関する XAML イベント ハンドラー属性構文の要件  
 CLR イベントとして使用できるようにするには、パラメーターなしのコンストラクターをサポートするクラス、または派生クラスでイベントにアクセスできる抽象クラスで、イベントをパブリック イベントとして公開する必要があります。 ルーティング`add`イベントとして便利に使用するには、CLR`remove`<xref:System.Windows.UIElement.AddHandler%2A><xref:System.Windows.UIElement.RemoveHandler%2A>イベントに明示的なメソッドとメソッドを実装する必要があります。 これらのメソッドは、イベントがアタッチされているインスタンスのルーティング イベント ハンドラー ストアにハンドラーを追加または削除します。  
  
> [!NOTE]
> を使用して<xref:System.Windows.UIElement.AddHandler%2A>ルーティング イベントのハンドラーを直接登録し、ルーティング イベントを公開する CLR イベントを意図的に定義しないようにすることができます。 イベントは、ハンドラーをアタッチするための XAML 属性構文を有効にせず、結果のクラスは、その型の機能のあまり透過的な XAML ビューを提供するため、一般的には推奨されません。  
  
<a name="Collection_Properties"></a>
## <a name="writing-collection-properties"></a>コレクションプロパティの書き込み  
 コレクション型を受け取るプロパティには、コレクションに追加されるオブジェクトを指定できる XAML 構文があります。 この構文には、2 つの注目すべき機能があります。  
  
- コレクション オブジェクトであるオブジェクトは、オブジェクト要素構文で指定する必要はありません。 コレクション型を受け取る XAML でプロパティを指定すると、そのコレクション型が暗黙的に存在します。  
  
- マークアップ内のコレクション プロパティの子要素は、コレクションのメンバーになるように処理されます。 通常、コレクションのメンバーへのコード アクセスは、 などの`Add`リスト/ディクショナリ メソッドを通じて、またはインデクサーを通じて実行されます。 ただし、XAML 構文はメソッドやインデクサーをサポートしていません (例外: XAML 2009 ではメソッドをサポートできますが、XAML 2009 を使用すると、WPF の使用法が制限[されます。](../../../desktop-wpf/xaml-services/xaml-2009-language-features.md) コレクションは、明らかに要素のツリーを構築するための非常に一般的な要件であり、宣言型 XAML でこれらのコレクションを設定する何らかの方法が必要です。 したがって、コレクション プロパティの子要素は、コレクション プロパティ型の値であるコレクションに追加することによって処理されます。  
  
 .NET Framework XAML サービスの実装、つまり、WPF XAML プロセッサは、コレクション プロパティを構成するものに対して次の定義を使用します。 プロパティのプロパティ型は、次のいずれかを実装する必要があります。  
  
- <xref:System.Collections.IList> を実装します。  
  
- 実装または<xref:System.Collections.IDictionary>汎用同等の (<xref:System.Collections.Generic.IDictionary%602>) を実装します。  
  
- 派生元<xref:System.Array>(XAML の配列の詳細については、「 [x:配列マークアップ拡張機能](../../../desktop-wpf/xaml-services/xarray-markup-extension.md)」を参照してください)。  
  
- 実装<xref:System.Windows.Markup.IAddChild>( によって定義される[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]インターフェイス ) 。  
  
 CLR のこれらの型にはメソッドがあり`Add`、オブジェクト グラフを作成するときに、XAML プロセッサが基になるコレクションに項目を追加するために使用します。  
  
> [!NOTE]
> ジェネリック`List`インターフェイス`Dictionary`およびインターフェイス<xref:System.Collections.Generic.IList%601> <xref:System.Collections.Generic.IDictionary%602>( および ) は、XAML[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]プロセッサによるコレクション検出ではサポートされていません。 ただし<xref:System.Collections.Generic.List%601>、直接実装<xref:System.Collections.IList>するため、クラスを基本クラスとして使用することも<xref:System.Collections.Generic.Dictionary%602>、基底クラスとして使用<xref:System.Collections.IDictionary>することもできます。  
  
 コレクションを受け取るプロパティを宣言する場合は、その型の新しいインスタンスでそのプロパティ値がどのように初期化されるかについて注意してください。 依存関係プロパティとしてプロパティを実装していない場合は、コレクション型のコンストラクターを呼び出すバッキング フィールドを使用するプロパティを使用する必要があります。 プロパティが依存関係プロパティの場合は、既定の型コンストラクターの一部としてコレクション プロパティを初期化する必要があります。 これは、依存関係プロパティはメタデータから既定値を取得し、通常はコレクション プロパティの初期値を静的な共有コレクションにしたくないためです。 各包含型インスタンスごとにコレクション インスタンスが存在する必要があります。 詳細については、「[カスタム依存関係プロパティ](custom-dependency-properties.md)」を参照してください。  
  
 コレクション プロパティにカスタム コレクション型を実装できます。 暗黙的なコレクション プロパティの処理のため、カスタム コレクション型は、XAML で暗黙的に使用するためにパラメーターなしのコンストラクターを提供する必要はありません。 ただし、オプションでコレクション型のパラメーターなしのコンストラクターを指定できます。 これはやりがいのある練習です。 パラメーターなしのコンストラクターを指定しない限り、コレクションをオブジェクト要素として明示的に宣言することはできません。 マークアップ作成者によっては、明示的なコレクションをマークアップ スタイルの問題として表示する方が好まれます。 また、パラメーターなしのコンストラクターは、コレクション型をプロパティ値として使用する新しいオブジェクトを作成するときに、初期化要件を簡略化できます。  
  
<a name="XAMLCONtent"></a>
## <a name="declaring-xaml-content-properties"></a>XAML コンテンツ プロパティの宣言  
 XAML 言語は、コンテンツ プロパティ[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]の概念を定義します。 オブジェクト構文で使用できる各クラスには、1 つの XAML コンテンツ プロパティを持つことができます。 クラスの XAML コンテンツ プロパティとしてプロパティを宣言するには、クラス定義<xref:System.Windows.Markup.ContentPropertyAttribute>の一部として を適用します。 目的の XAML コンテンツ プロパティの名前を<xref:System.Windows.Markup.ContentPropertyAttribute.Name%2A>属性で指定します。 プロパティは、リフレクション構造として<xref:System.Reflection.PropertyInfo>ではなく、名前で文字列として指定されます。  
  
 コレクション プロパティを XAML コンテンツ プロパティとして指定できます。 その結果、オブジェクト要素は、コレクション オブジェクト要素またはプロパティ要素タグを介さずに、1 つ以上の子要素を持つことができるプロパティを使用します。 これらの要素は、XAML コンテンツ プロパティの値として扱われ、バッキング コレクション インスタンスに追加されます。  
  
 一部の既存の XAML コンテンツ`Object`プロパティでは、 のプロパティの種類を使用します。 これにより、XAML コンテンツ プロパティは、 などのプリミティブ値を<xref:System.String>取得でき、単一の参照オブジェクト値を取得できます。 このモデルに従う場合、使用するタイプは、型決定と可能な型の処理を担当します。 <xref:System.Object>コンテンツ タイプの一般的な理由は、オブジェクト コンテンツを文字列として追加する単純な方法 (既定のプレゼンテーション処理を受ける) と、既定以外のプレゼンテーションや追加データを指定するオブジェクト コンテンツを追加する高度な方法の両方をサポートするためです。  
  
<a name="Serializing"></a>
## <a name="serializing-xaml"></a>XAML のシリアル化  
 コントロールの作成者など、特定のシナリオでは、XAML でインスタンス化できるオブジェクト表現を、同等の XAML マークアップにシリアル化して戻すこともできます。 シリアル化の要件については、このトピックでは説明しません。 [「コントロールの作成の概要](../controls/control-authoring-overview.md)」および[「要素ツリー」と「シリアル化](element-tree-and-serialization.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [XAML の概要 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [カスタム依存関係プロパティ](custom-dependency-properties.md)
- [コントロールの作成の概要](../controls/control-authoring-overview.md)
- [基本要素の概要](base-elements-overview.md)
- [XAML 読み込みと依存関係プロパティ](xaml-loading-and-dependency-properties.md)
