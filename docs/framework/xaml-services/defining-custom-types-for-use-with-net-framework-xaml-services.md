---
title: .NET Framework XAML サービスで使用するためのカスタム型の定義
ms.date: 03/30/2017
helpviewer_keywords:
- defining custom types [XAML Services]
ms.assetid: c2667cbd-2f46-4a7f-9dfc-53696e35e8e4
ms.openlocfilehash: 7437add6795c1bb7f8a59807ebfc51dc2d0f987f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73972021"
---
# <a name="defining-custom-types-for-use-with-net-framework-xaml-services"></a>.NET Framework XAML サービスで使用するためのカスタム型の定義
ビジネスオブジェクトまたは特定のフレームワークに依存しない型のカスタム型を定義する場合は、XAML のベストプラクティスに従うことができます。 これらの方法に従うと、.NET Framework XAML サービスとその XAML リーダーおよび XAML ライターは、型の XAML 特性を検出し、xaml 型システムを使用して XAML ノードストリームに適切な表現を与えることができます。 このトピックでは、型定義、メンバー定義、および型またはメンバーの CLR 属性のベストプラクティスについて説明します。  
  
## <a name="constructor-patterns-and-type-definitions-for-xaml"></a>XAML のコンストラクターパターンと型定義  
 XAML でオブジェクト要素としてインスタンス化するには、カスタムクラスが次の要件を満たしている必要があります。  
  
- カスタムクラスはパブリックである必要があり、パラメーターなしのパブリックコンストラクターを公開する必要があります。 (構造に関する注意事項については、次のセクションを参照してください)。  
  
- カスタムクラスを入れ子にすることはできません。 フルネームパスの余分な "ドット" により、クラス名前空間の除算があいまいになり、添付プロパティなどの他の XAML 機能と干渉します。  
  
 オブジェクトをオブジェクト要素としてインスタンス化できる場合、作成されたオブジェクトは、基になる型としてオブジェクトを受け取るプロパティのプロパティ要素の形式を満たすことができます。  
  
 値コンバーターを有効にした場合でも、これらの条件を満たしていない型のオブジェクト値を提供できます。 詳細については、「 [XAML の型コンバーターとマークアップ拡張機能](type-converters-and-markup-extensions-for-xaml.md)」を参照してください。  
  
### <a name="structures"></a>構造体  
 構造体は、常に CLR 定義によって XAML で構築できます。 これは、CLR コンパイラが構造体のパラメーターなしのコンストラクターを暗黙的に作成するためです。 このコンストラクターは、すべてのプロパティ値を既定値に初期化します。  
  
 場合によっては、構造体の既定の構築動作は望ましくありません。 これは、構造体が値を入力し、概念的に共用体として機能することを意図しているためです。 共用体として、含まれる値は相互に排他的な解釈を持つ場合があります。したがって、プロパティは設定できません。 WPF のボキャブラリにおけるこのような構造の例としては、<xref:System.Windows.GridLength>があります。 このような構造体では、構造体の値の異なる解釈やモードを作成する文字列規則を使用して、値を属性形式で表現できるように、型コンバーターを実装する必要があります。 また、構造体は、パラメーターなしのコンストラクターを使用してコードを構築する場合にも同様の動作を公開する必要があります。  
  
### <a name="interfaces"></a>インターフェイス  
 インターフェイスは、メンバーの基になる型として使用できます。 XAML 型システムは、割り当て可能なリストを確認し、値として指定されたオブジェクトをインターフェイスに割り当てることができることを前提としています。 関連する割り当て可能な型が XAML 構築の要件をサポートしている限り、インターフェイスを XAML 型として提示する方法の概念はありません。  
  
### <a name="factory-methods"></a>ファクトリメソッド  
 ファクトリメソッドは XAML 2009 機能です。 これらは、オブジェクトにパラメーターなしのコンストラクターが必要であることを XAML 原則を変更します。 ファクトリメソッドについては、このトピックでは説明しません。 「 [X:FactoryMethod ディレクティブ](x-factorymethod-directive.md)」を参照してください。  
  
## <a name="enumerations"></a>列挙  
 列挙には、XAML ネイティブ型の変換動作があります。 XAML で指定された列挙定数名は、基になる列挙型に対して解決され、その列挙値を XAML オブジェクトライターに返します。  
  
 XAML では、<xref:System.FlagsAttribute> 適用された列挙体のフラグ形式の使用をサポートしています。 詳細については、「 [XAML 構文の詳細](../wpf/advanced/xaml-syntax-in-detail.md)」を参照してください。 ([Xaml 構文の詳細に](../wpf/advanced/xaml-syntax-in-detail.md)ついては、WPF の対象ユーザー向けに記述されていますが、そのトピックのほとんどの情報は、特定の実装フレームワークに固有ではない xaml に関連しています)。  
  
## <a name="member-definitions"></a>メンバーの定義  
 型は、XAML の使用のためにメンバーを定義できます。 特定の型が XAML で使用できない場合でも、XAML で使用できるメンバーを定義する型を使用できます。 これは、CLR 継承が原因で発生する可能性があります。 メンバーを継承する型が XAML の使用を型としてサポートしていて、そのメンバーが基になる型の XAML の使用をサポートしている場合、またはネイティブ XAML 構文を使用できる場合、そのメンバーは XAML で使用できます。  
  
### <a name="properties"></a>プロパティ  
 一般的な CLR `get` および `set` アクセサーパターンと言語に適したキー表現を使用してパブリック CLR プロパティとしてプロパティを定義すると、XAML 型システムは <xref:System.Xaml.XamlMember.IsReadPublic%2A> や <xref:System.Xaml.XamlMember.IsWritePublic%2A>などの <xref:System.Xaml.XamlMember> プロパティに対して提供される適切な情報を持つメンバーとしてプロパティを報告できます。  
  
 特定のプロパティでは、<xref:System.ComponentModel.TypeConverterAttribute>を適用することによってテキスト構文を有効にすることができます。 詳細については、「 [XAML の型コンバーターとマークアップ拡張機能](type-converters-and-markup-extensions-for-xaml.md)」を参照してください。  
  
 テキスト構文またはネイティブ XAML 変換が存在しない場合、また、マークアップ拡張機能の<xref:System.Xaml.XamlMember.TargetType%2A> 使用など、追加の間接参照が存在しない場合は、ターゲット型を CLR 型として扱うことにより、xaml オブジェクトライターにインスタンスを返すことができる必要があります。  
  
 XAML 2009 を使用している場合、前の考慮事項が満たされていない場合、 [X:Reference マークアップ拡張機能](x-reference-markup-extension.md)を使用して値を指定できます。ただし、これは、型定義の問題よりも使用の問題になります。  
  
### <a name="events"></a>イベント  
 イベントをパブリック CLR イベントとして定義すると、XAML 型システムは、`true`として <xref:System.Xaml.XamlMember.IsEvent%2A> を持つメンバーとしてイベントを報告できます。 イベントハンドラーの配線は、.NET Framework XAML サービスの機能の範囲内ではありません。これは、特定のフレームワークと実装に残されています。  
  
### <a name="methods"></a>メソッド  
 メソッドのインラインコードは、既定の XAML 機能ではありません。 ほとんどの場合、XAML からメソッドメンバーを直接参照するのではなく、XAML のメソッドのロールは特定の XAML パターンのサポートのみを提供します。 [X:FactoryMethod ディレクティブ](x-factorymethod-directive.md)は例外です。  
  
### <a name="fields"></a>フィールド  
 CLR デザインガイドラインでは、非静的フィールドを防ぐことができます。 静的フィールドの場合は、 [X:Static マークアップ拡張機能](x-static-markup-extension.md)を使用してのみ、静的フィールド値にアクセスできます。この場合は、CLR 定義で特別な処理を行わずに、 [x:Static](x-static-markup-extension.md) usage のフィールドを公開しています。  
  
## <a name="attachable-members"></a>アタッチ可能なメンバー  
 アタッチ可能なメンバーは、定義する型のアクセサーメソッドパターンを通じて XAML に公開されます。 定義する型自体は、オブジェクトとして XAML で使用できる必要はありません。 実際、一般的なパターンは、アタッチ可能なメンバーを所有し、関連する動作を実装する役割を持つサービスクラスを宣言することですが、UI 表現などの他の機能は提供しません。 次のセクションでは、プレースホルダー *PropertyName*はアタッチ可能なメンバーの名前を表しています。 この名前は、 [XamlName 文法](xamlname-grammar.md)で有効である必要があります。  
  
 これらのパターンと型の他のメソッドとの間で名前の競合が発生している場合は注意してください。 いずれかのパターンに一致するメンバーが存在する場合、そのメンバーは、意図していない場合でも、XAML プロセッサによってアタッチ可能なメンバーの使用経路として解釈されます。  
  
#### <a name="the-getpropertyname-accessor"></a>GetPropertyName アクセサー  
 `Get`*PropertyName* アクセサーのシグネチャは次の形式にする必要があります。  
  
 `public static object Get` *PropertyName* `(object`  `target` `)`  
  
- `target` オブジェクトは、実装のより具体的な型として指定することができます。 これを使用して、アタッチ可能なメンバーの使用をスコープすることができます。意図したスコープ外の使用法は、XAML 解析エラーによって表示される無効なキャスト例外をスローします。 パラメーター名 `target` は要件ではありませんが、ほとんどの実装では、規則によって `target` という名前が付けられます。  
  
- 戻り値は、実装のより具体的な型として指定することができます。  
  
 アタッチ可能なメンバーの属性使用に対して <xref:System.ComponentModel.TypeConverter> 有効なテキスト構文をサポートするには、<xref:System.ComponentModel.TypeConverterAttribute> を `Get`*PropertyName*アクセサーに適用します。 `set` ではなく `get` に適用すると、nonintuitive のように見えます。ただし、この規則では、シリアル化可能な読み取り専用のアタッチ可能なメンバーの概念をサポートできます。これは、デザイナーのシナリオで役立ちます。  
  
#### <a name="the-setpropertyname-accessor"></a>SetPropertyName アクセサー  
 Set*PropertyName*アクセサーのシグネチャは次のようにする必要があります。  
  
 `public static void Set` *PropertyName* `(object`  `target` `, object`  `value` `)`  
  
- `target` オブジェクトは、前のセクションで説明したのと同じロジックと結果を使用して、実装でより具体的な型として指定できます。  
  
- `value` オブジェクトは、実装のより具体的な型として指定することができます。  
  
 このメソッドの値は、XAML の使用 (通常は属性の形式) からの入力であることに注意してください。 属性形式では、テキスト構文に対して値コンバーターがサポートされている必要があります。また、`Get`*PropertyName*アクセサーに対して属性を指定する必要があります。  
  
### <a name="attachable-member-stores"></a>アタッチ可能なメンバーストア  
 アクセサーメソッドは、通常、アタッチ可能なメンバー値をオブジェクトグラフに配置したり、オブジェクトグラフから値を取得して適切にシリアル化したりするための手段を提供するためのものではありません。 この機能を提供するには、前のアクセサーシグネチャの `target` オブジェクトが値を格納できる必要があります。 ストレージメカニズムは、アタッチ可能なメンバーがメンバーリストに含まれていないターゲットにアタッチできるメンバーである、アタッチ可能なメンバープリンシパルと一致している必要があります。 .NET Framework XAML サービスは、Api <xref:System.Xaml.IAttachedPropertyStore> と <xref:System.Xaml.AttachablePropertyServices>を通じて、アタッチ可能なメンバーストアの実装手法を提供します。 <xref:System.Xaml.IAttachedPropertyStore> は、ストアの実装を検出するために XAML ライターによって使用され、アクセサーの `target` である型に実装する必要があります。 静的 <xref:System.Xaml.AttachablePropertyServices> Api は、アクセサーの本体内で使用され、<xref:System.Xaml.AttachableMemberIdentifier>によってアタッチ可能なメンバーを参照します。  
  
## <a name="xaml-related-clr-attributes"></a>XAML 関連の CLR 属性  
 XAML 型システム情報を XAML サービス .NET Framework に報告するには、型、メンバー、およびアセンブリを正しく属性することが重要です。 これは、.NET Framework XAML サービスの XAML リーダーと XAML ライターに直接基づいている XAML システムで型を使用する場合、または xaml リーダーと XAML ライターに基づく XAML を使用するフレームワークを定義または使用する場合に関連します。  
  
 カスタム型の XAML サポートに関連する各 XAML 関連の属性の一覧については、「[カスタム型およびライブラリの Xaml 関連の CLR 属性](xaml-related-clr-attributes-for-custom-types-and-libraries.md)」を参照してください。  
  
## <a name="usage"></a>使用方法  
 カスタム型を使用するには、マークアップの作成者が、カスタム型を含むアセンブリと CLR 名前空間のプレフィックスをマップする必要があります。 この手順については、このトピックでは説明しません。  
  
## <a name="access-level"></a>アクセスレベル  
 XAML には、`internal` アクセスレベルを持つ型を読み込んでインスタンス化するための手段が用意されています。 この機能は、ユーザーコードが独自の型を定義し、同じユーザーコードスコープの一部でもあるマークアップからそれらのクラスをインスタンス化できるようにするために用意されています。  
  
 WPF の例として、ユーザーコードで UI 動作をリファクターする手段として使用する <xref:System.Windows.Controls.UserControl> を定義する場合があります。ただし、サポートクラスを `public` アクセスレベルで宣言することによって暗黙になる可能性のある拡張機能の一部としては使用できません。 バッキングコードを XAML 型として参照される同じアセンブリにコンパイルする場合は、このような <xref:System.Windows.Controls.UserControl> を `internal` アクセスで宣言できます。  
  
 完全信頼で XAML を読み込み、<xref:System.Xaml.XamlObjectWriter>を使用するアプリケーションの場合、`internal` アクセスレベルを持つクラスの読み込みは常に有効になります。  
  
 部分信頼で XAML を読み込むアプリケーションの場合は、<xref:System.Xaml.Permissions.XamlAccessLevel> API を使用してアクセスレベルの特性を制御できます。 また、遅延メカニズム (WPF テンプレートシステムなど) は、すべてのアクセスレベルのアクセス許可を伝達し、最終的な実行時の評価のためにそれらを保持できる必要があります。これは <xref:System.Xaml.Permissions.XamlAccessLevel> 情報を渡すことによって内部的に処理されます。  
  
### <a name="wpf-implementation"></a>WPF の実装  
 WPF XAML では、部分信頼アクセスモデルが使用されます。この場合、BAML が部分信頼で読み込まれると、BAML ソースであるアセンブリのアクセスが <xref:System.Xaml.Permissions.XamlAccessLevel.AssemblyAccessTo%2A> に制限されます。 遅延の場合、WPF はアクセスレベル情報を渡すためのメカニズムとして <xref:System.Xaml.IXamlObjectWriterFactory.GetParentSettings%2A?displayProperty=nameWithType> を使用します。  
  
 WPF XAML 用語では、*内部型*は、参照元の xaml も含む同じアセンブリによって定義される型です。 このような型は、`xmlns:local="clr-namespace:WPFApplication1"`など、割り当てのアセンブリを意図的に省略する XAML 名前空間を使用してマップできます。  BAML が内部型を参照し、その型に `internal` アクセスレベルがある場合、アセンブリの `GeneratedInternalTypeHelper` クラスが生成されます。 `GeneratedInternalTypeHelper`を回避するには、`public` アクセスレベルを使用するか、関連するクラスを別のアセンブリに分けて、そのアセンブリを依存させる必要があります。  
  
## <a name="see-also"></a>関連項目

- [カスタム型およびライブラリの XAML 関連の CLR 属性](xaml-related-clr-attributes-for-custom-types-and-libraries.md)
- [XAML サービス](index.md)
