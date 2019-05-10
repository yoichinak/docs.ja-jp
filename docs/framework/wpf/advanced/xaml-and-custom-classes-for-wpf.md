---
title: WPF における XAML とカスタム クラス
ms.date: 03/30/2017
helpviewer_keywords:
- custom classes in XAML [WPF]
- XAML [WPF], custom classes
- classes [WPF], custom classes in XAML
ms.assetid: e7313137-581e-4a64-8453-d44e15a6164a
ms.openlocfilehash: 2f59e7479c856de9b00592d570ca89d2539b0ec4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662232"
---
# <a name="xaml-and-custom-classes-for-wpf"></a>WPF における XAML とカスタム クラス
XAML に実装されている[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]フレームワークは、いずれかで、カスタムのクラスまたは構造体を定義する機能をサポートしている[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]言語、およびしアクセス クラスの XAML マークアップを使用しています。 組み合わせを使用できる[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]-XAML 名前空間のプレフィックスにカスタムの型をマップして、通常の種類と同じマークアップ ファイル内でカスタム型を定義します。 このトピックでは、XAML 要素として使用するのには、カスタム クラスが満たす必要がある要件について説明します。  

<a name="Custom_Classes_in_Applications_vs__in_Assemblies"></a>   
## <a name="custom-classes-in-applications-or-assemblies"></a>アプリケーションまたはアセンブリのカスタム クラス  
 2 つの方法で XAML で使用されるカスタム クラスを定義することができます。 分離コードまたはその他のプライマリを生成するコード内で[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]アプリケーション、または実行可能ファイルなどの別のアセンブリ内のクラスまたはクラス ライブラリとして使用される DLL として。 これらのアプローチのそれぞれは、特定の長所と短所にあります。  
  
- クラス ライブラリを作成する利点は、このような任意のカスタム クラスが異なる多くのアプリケーション間で共有できることです。 別のライブラリもアプリケーションのバージョン管理の問題を簡単に、コントロールと、目的のクラスの使用状況を XAML ページにルート要素としては、クラスの作成を簡素化します。  
  
- アプリケーションのカスタム クラスを定義する利点は、この手法が比較的軽量があり、展開とテストの問題がメイン アプリケーションの実行可能ファイルを超える個別のアセンブリを導入するときに発生しましたが最小限に抑えることです。  
  
- 同じまたは別のアセンブリで定義されているかどうか、カスタム クラスを XAML で要素として使用するには CLR 名前空間と XML 名前空間の間にマップする必要があります。 参照してください[XAML 名前空間および WPF XAML の Namespace マッピング](xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)します。  
  
<a name="Requirements_for_a_Custom_Class_as_a_XAML_Element"></a>   
## <a name="requirements-for-a-custom-class-as-a-xaml-element"></a>XAML 要素としてカスタム クラスの要件  
 オブジェクト要素としてインスタンス化できるようにするには、するには、クラスは、次の要件を満たす必要があります。  
  
- カスタム クラスは、パブリックであるし、既定の (パラメーターなしの) パブリック コンス トラクターをサポートする必要があります。 (次の構造に関する注意事項のセクションを参照してください)。  
  
- 入れ子になったクラスは、カスタム クラスではなければなりません。 入れ子になったクラスおよび CLR 使用する、一般的な構文で「ドット」が他の干渉[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]や添付プロパティなどの XAML 機能。  
  
 オブジェクトの定義はオブジェクト要素構文を有効にするだけでなく、値の型としては、そのオブジェクトを取得するその他のパブリック プロパティのプロパティ要素構文もできます。 これは、オブジェクトがオブジェクト要素としてインスタンス化するようになりましたことができます、このようなプロパティのプロパティ要素の値を入力できるためです。  
  
### <a name="structures"></a>構造体  
 カスタムの種類は、XAML 内で構築することが常として定義する構造体[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]します。これは、ため、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]コンパイラが暗黙的にすべてのプロパティ値を既定値を初期化する構造体の既定のコンス トラクターを作成します。 場合によっては、構造体の既定コンス トラクターの動作やオブジェクト要素の各使用は望ましくありません。 構造体では、fill 値および関数に概念的には、共用体に含まれる値は相互に排他的な解釈を必要があります、そのためのプロパティは設定可能な可能性があります。 A[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]このような構造の例は、<xref:System.Windows.GridLength>します。 一般に、このような構造は、値は、さまざまな解釈や構造体の値のモードを作成する文字列の規則を使用して、属性の形式で表現できるように、型コンバーターを実装する必要があります。 構造体には、既定以外のコンス トラクターを使用してコード構築の同様の動作も公開する必要があります。  
  
<a name="Requirements_for_Properties_of_a_Custom_Class_as_XAML"></a>   
## <a name="requirements-for-properties-of-a-custom-class-as-xaml-attributes"></a>XAML の属性としてカスタム クラスのプロパティの要件  
 プロパティは、(プリミティブ) など、値の型を参照または型を持つ既定のコンス トラクターまたは XAML プロセッサがアクセスできる専用の型コンバーターのいずれかのクラスを使用する必要があります。 CLR の XAML の実装で XAML プロセッサか検索言語プリミティブのネイティブ サポート、またはアプリケーションのを通じてこのようなコンバーター<xref:System.ComponentModel.TypeConverterAttribute>型またはメンバーの種類の定義をバックアップする  
  
 または、プロパティは、抽象クラス型またはインターフェイスを参照できます。 抽象クラスまたはインターフェイスは、XAML を解析するための予測は、インターフェイスを実装する実際的なクラスのインスタンスまたは抽象クラスから派生した型のインスタンスでプロパティ値を入力する必要があります。  
  
 プロパティは、抽象クラスで宣言することができますが、抽象クラスから派生したクラスでのみ設定できます。 これは、クラスのパブリックの既定のコンス トラクター クラスのオブジェクトの要素をまったく作成する必要があるためにです。  
  
### <a name="typeconverter-enabled-attribute-syntax"></a>TypeConverter 属性構文を有効になっています。  
 クラス レベルで専用の属性付きの型コンバーターを指定すると、適用される型変換はその型のインスタンスを作成する必要がある任意のプロパティの属性構文を使用できます。 型コンバーターが、型のオブジェクト要素の使用を有効にしません。その型の既定のコンス トラクターの存在だけでは、オブジェクト要素の使用を有効します。 そのため、型コンバーターが有効になっているプロパティは、その型自体には、オブジェクト要素構文もサポートしている場合を除き、一般にプロパティの構文では使用できません。 この例外は、プロパティ要素構文では、指定しますが、プロパティ要素に文字列を含めることができますです。 使用状況は、属性構文の使用に非常に基本的に相当し、属性の値のより堅牢な空白の処理の必要性がない場合は一般的ではありません。 たとえば、次に、文字列を受け取るプロパティ要素による使用と同等の属性の使用。  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe)]  
  
 [!code-xaml[XamlOvwSupport#GoofyTCPE2](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page8.xaml#goofytcpe2)]  
  
 属性の構文が許可されているオブジェクトの要素を含むプロパティ要素構文は XAML で許可されていませんプロパティの例を使用するさまざまなプロパティ、<xref:System.Windows.Input.Cursor>型。 <xref:System.Windows.Input.Cursor>クラスには専用の型コンバーター <xref:System.Windows.Input.CursorConverter>、既定のコンス トラクターを公開しないため、<xref:System.Windows.FrameworkElement.Cursor%2A>プロパティのみ設定できます属性構文で場合でも、実際<xref:System.Windows.Input.Cursor>型は参照型です。  
  
### <a name="per-property-type-converters"></a>プロパティの型コンバーター  
 または、プロパティ自体は、プロパティ レベルでの型コンバーターを宣言できます。 これにより、入力として受信する属性の文字列値を処理することによって、プロパティ、インラインでの型のオブジェクトをインスタンス化「ミニ言語」を<xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>操作、適切な型に基づきます。 便利なアクセサーを提供するこれは、通常、XAML でプロパティの設定を有効にする唯一の手段ではありません。 ただし、既存を使用する属性の型コンバーターを使用することがも[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]既定のコンス トラクターまたは、属性付きの型コンバーターのいずれかを指定しない型です。 例から、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] API は、特定のプロパティ、<xref:System.Globalization.CultureInfo>型。 この場合、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]既存の Microsoft .NET Framework を使用する<xref:System.Globalization.CultureInfo>より以前のバージョンのフレームワークを使用した互換性と移行のシナリオに対応する型が、<xref:System.Globalization.CultureInfo>型では、必要ながサポートされていませんでしたコンス トラクターまたは直接 XAML プロパティの値として使用できるようにする型レベルの型変換。  
  
 XAML の使用状況を持つプロパティを公開するたびにコントロールの作成者がいる場合に特に厳密に検討してください、依存関係プロパティとそのプロパティをバックアップします。 これは、既存を使用する場合に特に当てはまります[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]、XAML プロセッサの実装を使用してパフォーマンスを向上させることができますので<xref:System.Windows.DependencyProperty>をバックアップします。 依存関係プロパティには、XAML のアクセス可能なプロパティに対して期待するユーザーが付属、プロパティのプロパティ システムの機能が公開されます。 これには、アニメーション、データ バインディング、およびスタイルのサポートなどの機能が含まれます。 詳細については、次を参照してください。[カスタム依存関係プロパティ](custom-dependency-properties.md)と[XAML 読み込みと依存関係プロパティ](xaml-loading-and-dependency-properties.md)します。  
  
### <a name="writing-and-attributing-a-type-converter"></a>作成と型コンバーターの割り当て  
 場合によっては必要がありますにカスタム<xref:System.ComponentModel.TypeConverter>プロパティの型の型変換を提供するクラスを派生します。 派生し、XAML の使用方法をサポートする型コンバーターを作成する方法、および適用する方法についての<xref:System.ComponentModel.TypeConverterAttribute>を参照してください[TypeConverters および XAML](typeconverters-and-xaml.md)します。  
  
<a name="Requirements_for_Events_of_a_Custom_Class_as_XAML"></a>   
## <a name="requirements-for-xaml-event-handler-attribute-syntax-on-events-of-a-custom-class"></a>XAML でカスタム クラスのイベントのイベント ハンドラー属性構文の要件  
 として使用するのには、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]イベント、イベントが既定のコンス トラクターをサポートするクラスのパブリック イベントとして公開する必要がありますまたはで抽象クラス イベントを派生クラスでアクセスできます。 ルーティング イベントとして簡単に使用するために、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]イベントを明示的に実装する必要があります`add`と`remove`メソッドは、追加のハンドラーと削除、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]イベントのシグネチャ、にこれらのハンドラーを前後<xref:System.Windows.UIElement.AddHandler%2A>と<xref:System.Windows.UIElement.RemoveHandler%2A>メソッド。 これらのメソッドは、追加またはインスタンスに関連付けられているイベントのルーティング イベント ハンドラー ストアにハンドラーを削除します。  
  
> [!NOTE]
>  ハンドラーを使用して、ルーティング イベントを直接登録することは<xref:System.Windows.UIElement.AddHandler%2A>は意図的に定義して、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]ルーティング イベントを公開するイベントです。 これは一般的に使用しないでイベントにハンドラーをアタッチするための XAML 属性の構文が有効になりませんし、結果として得られるクラスはその型の機能の透明度が減少 XAML ビューを提供するためです。  
  
<a name="Collection_Properties"></a>   
## <a name="writing-collection-properties"></a>コレクション プロパティの作成  
 コレクション型を使用するプロパティには、コレクションに追加されるオブジェクトを指定することができる XAML 構文があります。 この構文では、2 つの注目すべき機能があります。  
  
- コレクション オブジェクトであるオブジェクトは、オブジェクト要素構文で指定する必要はありません。 コレクション型を受け取る XAML でプロパティを指定するには、そのコレクションの種類の存在は暗黙的です。  
  
- マークアップでコレクションのプロパティの子要素は、コレクションのメンバーに処理されます。 通常、コレクションのメンバーにコード アクセスは、リストのディクショナリ/メソッドを通じて実行など`Add`、またはインデクサーを使用します。 XAML 構文ではメソッドまたはインデクサーをサポートしていませんが、(例外。XAML 2009 は、メソッドをサポートできますが、可能な WPF の使用法は XAML 2009 を使用して制限されます。参照してください[XAML 2009 言語機能](../../xaml-services/xaml-2009-language-features.md))。 コレクションは、要素のツリーを構築するための非常に一般的な要件と、宣言型の XAML でこれらのコレクションを設定する手段が必要です。 そのため、コレクション プロパティの子要素は、コレクション プロパティの型の値は、コレクションに追加することによって処理されます。  
  
 .NET Framework XAML サービス実装および WPF XAML プロセッサは、コレクション プロパティの構成内容を次の定義を使用します。 プロパティのプロパティの型には、次のいずれかを実装する必要があります。  
  
- 実装<xref:System.Collections.IList>します。  
  
- 実装<xref:System.Collections.IDictionary>または同等のジェネリック (<xref:System.Collections.Generic.IDictionary%602>)。  
  
- 派生した<xref:System.Array>(XAML での配列の詳細については、次を参照してください[X:array マークアップ拡張機能](../../xaml-services/x-array-markup-extension.md)。)。  
  
- 実装<xref:System.Windows.Markup.IAddChild>(によって定義されたインターフェイス[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)])。  
  
 CLR でこれらの型のそれぞれに、`Add`メソッドは、XAML プロセッサによって、オブジェクト グラフを作成するときに、基になるコレクションに項目を追加するために使用します。  
  
> [!NOTE]
>  ジェネリック`List`と`Dictionary`インターフェイス (<xref:System.Collections.Generic.IList%601>と<xref:System.Collections.Generic.IDictionary%602>) によるコレクションの検出はサポートされていません、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML プロセッサ。 ただし、使用することができます、<xref:System.Collections.Generic.List%601>クラスの基底クラスとして実装するため、<xref:System.Collections.IList>を直接または<xref:System.Collections.Generic.Dictionary%602>基底クラスとして実装するため、<xref:System.Collections.IDictionary>直接します。  
  
 コレクションを受け取るプロパティを宣言するときに、そのプロパティ値を型の新しいインスタンスで初期化する方法について注意してください。 依存関係プロパティとしてプロパティを実装しない場合、コレクション型のコンス トラクターを呼び出すバッキング フィールドを使用してプロパティを持つは十分です。 プロパティが依存関係プロパティの場合は、既定の型コンス トラクターの一部として、コレクション プロパティを初期化する必要があります。 依存関係プロパティは、メタデータから既定値を受け取るし、通常たくない、静的な共有コレクションのコレクション プロパティの初期値であるためにです。 包含型のインスタンスごとにコレクション インスタンスが必要です。 詳細については、「[カスタム依存関係プロパティ](custom-dependency-properties.md)」を参照してください。  
  
 コレクション プロパティには、カスタム コレクション型を実装できます。 暗黙の型のコレクション プロパティの処理のため、カスタム コレクション型は XAML で暗黙的に使用するために既定のコンス トラクターを提供するには必要ありません。 ただし、コレクション型の既定のコンス トラクターを必要に応じて指定できます。 これは、価値のあるプラクティスです。 既定のコンス トラクターを用意する場合を除き、オブジェクト要素としてコレクションを明示的に宣言することはできません。 マークアップ スタイルの問題として明示的なコレクションを表示するは、いくつかのマークアップの作成者をお勧めします。 また、既定のコンス トラクターは、プロパティの値として、コレクション型を使用する新しいオブジェクトを作成するときに、初期化要件を簡略化できます。  
  
<a name="XAMLCONtent"></a>   
## <a name="declaring-xaml-content-properties"></a>XAML コンテンツ プロパティを宣言します。  
 XAML 言語の概念を定義する、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]コンテンツのプロパティ。 オブジェクト構文で使用可能な各クラスには、1 つの XAML コンテンツ プロパティを持つことができます。 クラスの XAML コンテンツ プロパティのプロパティを宣言するには、適用、<xref:System.Windows.Markup.ContentPropertyAttribute>クラス定義の一部として。 として目的の XAML コンテンツ プロパティの名前を指定、<xref:System.Windows.Markup.ContentPropertyAttribute.Name%2A>属性。 プロパティを文字列として名前で指定した、リフレクション コンストラクトとしてではなくなど<xref:System.Reflection.PropertyInfo>します。  
  
 XAML コンテンツ プロパティのコレクション プロパティを指定できます。 これにより、オブジェクト要素が介在するコレクション オブジェクトの要素またはプロパティ要素タグなし、1 つまたは複数の子要素が、そのプロパティの使用量。 これらの要素は、XAML コンテンツ プロパティの値として扱われ、バッキング コレクションに追加されます。  
  
 いくつかの既存の XAML コンテンツ プロパティのプロパティの型を使用して、`Object`します。 これにより、XAML のコンテンツなどのプリミティブが可能なプロパティ値を<xref:System.String>と 1 つの参照オブジェクトの値を取得します。 このモデルに従うと場合の種類は型の判定と使用可能な型の処理を担当します。 一般的な理由は、<xref:System.Object>コンテンツの種類は、(これが既定のプレゼンテーションの処理を受け取る) を文字列としてオブジェクトのコンテンツの追加の両方を簡単な手段をサポートするまたは高度な手段を追加するオブジェクトの既定以外のプレゼンテーションを指定するコンテンツまたは追加のデータ。  
  
<a name="Serializing"></a>   
## <a name="serializing-xaml"></a>XAML のシリアル化  
 場合など、特定のシナリオがコントロールの作成者は、XAML でインスタンス化できる任意のオブジェクト表現が同等の XAML マークアップにシリアル化もできるようにすることもできます。 シリアル化の要件は、このトピックでは説明しません。 参照してください[概要の作成を管理して](../controls/control-authoring-overview.md)と[要素のツリーおよびシリアル化](element-tree-and-serialization.md)します。  
  
## <a name="see-also"></a>関連項目

- [XAML の概要 (WPF)](xaml-overview-wpf.md)
- [カスタム依存関係プロパティ](custom-dependency-properties.md)
- [コントロールの作成の概要](../controls/control-authoring-overview.md)
- [基本要素の概要](base-elements-overview.md)
- [XAML 読み込みと依存関係プロパティ](xaml-loading-and-dependency-properties.md)
