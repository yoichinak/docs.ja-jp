---
title: .NET Framework XAML サービスで使用するためのカスタム型の定義
ms.date: 03/30/2017
helpviewer_keywords:
- defining custom types [XAML Services]
ms.assetid: c2667cbd-2f46-4a7f-9dfc-53696e35e8e4
ms.openlocfilehash: be9c0e26574a15279ce89af2c7862abaa8713360
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164438"
---
# <a name="defining-custom-types-for-use-with-net-framework-xaml-services"></a>.NET Framework XAML サービスで使用するためのカスタム型の定義
ビジネス オブジェクトであるカスタム型の定義または特定のフレームワークに依存関係がない型には、XAML を利用できるため、特定のベスト プラクティスがあります。 .NET Framework XAML サービスのこれらのプラクティスに従うと、その XAML リーダーと XAML ライターできます型の XAML の特性を検出し、XAML 型システムを使用して XAML ノード ストリームで適切な表現を付けます。 このトピックでは、型定義、メンバーの定義、および CLR 型またはメンバーの属性の設定のベスト プラクティスについて説明します。  
  
## <a name="constructor-patterns-and-type-definitions-for-xaml"></a>コンス トラクター パターンと XAML の種類の定義  
 XAML オブジェクト要素としてインスタンス化される、カスタム クラスは、次の要件を満たす必要があります。  
  
-   カスタムのクラスは、パブリックである必要があり、既定の (パラメーターなしの) パブリック コンス トラクターを公開する必要があります。 (次の構造に関する注意事項のセクションを参照してください)。  
  
-   入れ子になったクラスは、カスタム クラスではなければなりません。 追加の完全名のパスに「ドット」では、あいまいな場合は、名前空間のクラスの除算を作成し、添付プロパティなどの他の XAML 機能に干渉します。  
  
 オブジェクト要素として、オブジェクトをインスタンス化することができます、作成したオブジェクトを基になる型としてオブジェクトを使用する任意のプロパティのプロパティ要素の形式を入力します。  
  
 値コンバーターを有効にした場合は、これらの条件を満たしていない型のオブジェクトの値を行うことができますも。 詳細については、次を参照してください。[型コンバーターと XAML のマークアップ拡張機能](type-converters-and-markup-extensions-for-xaml.md)します。  
  
### <a name="structures"></a>構造体  
 構造体は、XAML で CLR の定義によって構築することが常にします。 これは、CLR コンパイラは構造体の既定のコンス トラクターを暗黙的に作成されるためです。 このコンス トラクターでは、すべてのプロパティ値を既定値を初期化します。  
  
 場合によっては、構造体の既定の構築の動作は望ましくありません。 構造の目的は、共用体と概念的には、値と関数を入力する可能性があります。 、共用体として値を含んでいる場合、排他的な解釈があり、そのため、そのプロパティを設定できます。 WPF ボキャブラリで、このような構造の例は、<xref:System.Windows.GridLength>します。 このような構造は、値は、さまざまな解釈や構造体の値のモードを作成する文字列の規則を使用して属性の形式で表現できるように、型コンバーターを実装する必要があります。 構造体には、既定以外のコンス トラクターを使用してコード構築の同様の動作も公開する必要があります。  
  
### <a name="interfaces"></a>インターフェイス  
 インターフェイスは、基になる型のメンバーとして使用できます。 XAML 型システムでは、割り当て可能な一覧を確認し、インターフェイスに割り当てることができる値として指定されているオブジェクトが必要です。 方法インターフェイスの存在が必要、XAML の型として関連する割り当て可能な型は、XAML の作成要件をサポートしている限りの概念はありません。  
  
### <a name="factory-methods"></a>ファクトリ メソッド  
 ファクトリ メソッドは、XAML 2009 の機能です。 これらは、オブジェクトが既定のコンス トラクターが必要な XAML の原則を変更します。 ファクトリ メソッドは、このトピックに記載されていません。 参照してください[X:factorymethod ディレクティブ](x-factorymethod-directive.md)します。  
  
## <a name="enumerations"></a>列挙  
 列挙体では、XAML のネイティブな型変換動作があります。 XAML で指定された列挙定数の名前は、基になる列挙型に対して解決し、XAML オブジェクト ライターに列挙値を返します。  
  
 XAML は、ある列挙型のフラグ スタイルの使用状況をサポートしている<xref:System.FlagsAttribute>適用します。 詳細については、次を参照してください。 [XAML 構文の詳細](../wpf/advanced/xaml-syntax-in-detail.md)します。 ([XAML 構文の詳細](../wpf/advanced/xaml-syntax-in-detail.md)は WPF のユーザー向けに書き込まれますが、そのトピックの情報の大部分は実装する特定のフレームワークに固有ではない XAML に関連します)。  
  
## <a name="member-definitions"></a>メンバーの定義  
 型は、XAML の使用状況のメンバーを定義できます。 その特定の種類が XAML で使用できない場合でも、XAML の使用可能なメンバーを定義する型のことができます。 これは、CLR の継承によって実現します。 限り、メンバーを継承する何らかの種類が XAML の使用法は、型をサポートし、基になる型の XAML の使用状況をサポートしているまたはネイティブの XAML 構文を使用可能なメンバー、そのメンバーが XAML で使用します。  
  
### <a name="properties"></a>プロパティ  
 一般的な CLR を使用して、パブリックの CLR プロパティとしてプロパティを定義するかどうかは`get`と`set`アクセサー パターンおよび言語に応じた keywording、XAML 型システムがのプロパティを適切な情報を持つメンバーとして提供されているを報告することができます<xref:System.Xaml.XamlMember>プロパティなど<xref:System.Xaml.XamlMember.IsReadPublic%2A>と<xref:System.Xaml.XamlMember.IsWritePublic%2A>します。  
  
 特定のプロパティは、適用することで、テキスト構文を有効にできます<xref:System.ComponentModel.TypeConverterAttribute>します。 詳細については、次を参照してください。[型コンバーターと XAML のマークアップ拡張機能](type-converters-and-markup-extensions-for-xaml.md)します。  
  
 テキストの構文またはネイティブの XAML の変換がない場合、マークアップ拡張機能の使用、プロパティの型など、さらに間接的ながない場合は、(<xref:System.Xaml.XamlMember.TargetType%2A> XAML 入力システム) を t を扱うことにより、XAML オブジェクト ライターにインスタンスを返すことがありますarget 型を CLR 型。  
  
 XAML 2009 を使用して場合[X:reference マークアップ拡張機能](x-reference-markup-extension.md)前の考慮事項を満たしていない場合は、値を指定するために使用できます。 ただし、これは、型定義の問題よりも使用率の問題の。  
  
### <a name="events"></a>イベント  
 パブリック CLR イベントとしてイベントを定義する場合、XAML 型システムがのメンバーとしてイベントを報告できます<xref:System.Xaml.XamlMember.IsEvent%2A>として`true`します。 .NET Framework XAML サービスの機能のスコープ内では、イベント ハンドラーを配線これは特定のフレームワークと実装に残しておきます。  
  
### <a name="methods"></a>メソッド  
 メソッドのインライン コードは、既定の XAML 機能ではありません。 ほとんどの場合で直接参照しないメソッドのメンバーから XAML、および XAML でのメソッドの役割は、特定の XAML パターンのサポートを提供するだけです。 [X:factorymethod ディレクティブ](x-factorymethod-directive.md)は例外です。  
  
### <a name="fields"></a>フィールド  
 CLR のデザイン ガイドラインは、非静的フィールドを防止します。 静的フィールドは、静的フィールドの値にアクセスできるを通してのみ[X:static マークアップ拡張機能](x-static-markup-extension.md); ここではないのフィールドを公開する CLR の定義で特別な行っている[X:static](x-static-markup-extension.md)使用法。  
  
## <a name="attachable-members"></a>アタッチ可能なメンバー  
 アタッチ可能なメンバーは、XAML に定義する型のアクセサー メソッド パターンを通じて公開されます。 定義の型自体は、オブジェクトとして、XAML で使用する必要はありません。 実際には、一般的なパターンでは、ロールがあるサービス クラスを宣言するアタッチ可能メンバーを所有し、関連する動作を実装が UI 表現などの他の関数は使用されません。 次のセクションで、プレース ホルダーの*PropertyName*アタッチ可能なメンバーの名前を表します。 その名前で有効である必要があります、 [XamlName の文法](xamlname-grammar.md)します。  
  
 これらのパターンと型の他のメソッドの名前の衝突の注意があります。 パターンのいずれかに一致するメンバーが存在する場合に解釈できますアタッチ可能なメンバーの使用状況経路として XAML プロセッサによって場合でも、意図したものでした。  
  
#### <a name="the-getpropertyname-accessor"></a>GetPropertyName アクセサー  
 `Get`*PropertyName* アクセサーのシグネチャは次の形式にする必要があります。  
  
 `public static object Get` *PropertyName* `(object`  `target` `)`  
  
-   `target` オブジェクトは、実装のより具体的な型として指定することができます。 これを使用するには、アタッチ可能メンバーの使用状況のスコープをする使用状況、目的のスコープ外 XAML 解析エラーが表示される、無効なキャスト例外がスローされます。 パラメーター名`target`、必須ではありませんが、名前は`target`の規約では、ほとんどの実装。  
  
-   戻り値は、実装のより具体的な型として指定することができます。  
  
 サポートするために、 <xref:System.ComponentModel.TypeConverter> 、アタッチ可能なメンバーの属性の使用方法の有効なテキスト構文は適用<xref:System.ComponentModel.TypeConverterAttribute>を`Get` *PropertyName*アクセサー。 適用する、`get`の代わりに、`set`直感; かもしれませんただし、この規則は、概念をサポートできますのシリアル化可能である読み取り専用のアタッチ可能なメンバー、これはデザイナーのシナリオで有用です。  
  
#### <a name="the-setpropertyname-accessor"></a>SetPropertyName アクセサー  
 セットの署名*PropertyName*アクセサーを指定する必要があります。  
  
 `public static void Set` *PropertyName* `(object`  `target` `, object`  `value` `)`  
  
-   `target`オブジェクトは、前のセクションで説明したロジックと結果が同じで、実装のより具体的な型として指定できます。  
  
-   `value` オブジェクトは、実装のより具体的な型として指定することができます。  
  
 このメソッドの値は属性の形式では通常、XAML の使用から生じる入力であることに注意してください。 属性の形式から値コンバーターが、テキスト構文のサポートおよび必要する属性を`Get` *PropertyName*アクセサー。  
  
### <a name="attachable-member-stores"></a>アタッチ可能なメンバー ストア  
 アクセサー メソッドは通常されませんがアタッチ可能なメンバーの値をオブジェクト グラフに配置するか、オブジェクト グラフから値を取得し、適切にシリアル化する手段を提供するには不十分です。 この機能を提供する、`target`アクセサーの以前のシグネチャ内のオブジェクトの値を格納できる必要があります。 ストレージ メカニズムは、メンバーがアタッチ可能メンバーがないメンバー リストでターゲットにアタッチ可能なアタッチ可能なメンバーの原則と一致する必要があります。 .NET framework XAML サービス api のアタッチ可能なメンバー ストアについて、実装方法を提供します<xref:System.Xaml.IAttachedPropertyStore>と<xref:System.Xaml.AttachablePropertyServices>します。 <xref:System.Xaml.IAttachedPropertyStore> ストアの実装を検出する XAML ライターによって使用され、ある型に実装する必要があります、`target`アクセサー。 静的な<xref:System.Xaml.AttachablePropertyServices>Api は、アクセサーの本文内で使用され、アタッチ可能メンバーを参照してください、<xref:System.Xaml.AttachableMemberIdentifier>します。  
  
## <a name="xaml-related-clr-attributes"></a>XAML 関連の CLR 属性  
 正しく、型、メンバー、およびアセンブリの属性を設定することは、レポートには、.NET Framework XAML サービスの XAML 型システムの情報で重要です。 これは、型に直接基づく .NET Framework XAML サービスの XAML リーダーと XAML ライターでは、XAML システムを使用する場合、または定義またはそれらの XAML リーダーと XAML ライターに基づいている XAML 利用するフレームワークを使用する場合です。  
  
 カスタム型の XAML のサポートに関連する各 XAML 関連の属性の一覧については、次を参照してください。[カスタム型およびライブラリの CLR 属性を XAML-Related](xaml-related-clr-attributes-for-custom-types-and-libraries.md)します。  
  
## <a name="usage"></a>使用法  
 カスタム型を使用するには、マークアップの作成者がカスタム型を含むアセンブリと CLR 名前空間のプレフィックスをマップする必要がありますが必要です。 この手順は、このトピックでは説明しません。  
  
## <a name="access-level"></a>アクセス レベル  
 XAML 読み込みおよびを持つ型をインスタンス化する手段を提供する、`internal`アクセス レベル。 ユーザー コードが、独自の型を定義し、同じユーザー コードのスコープの一部でもあるマークアップからこれらのクラスのインスタンスを作成できるように、この機能は提供されています。  
  
 WPF の例は、ユーザー コードを定義するたびに、 <xref:System.Windows.Controls.UserControl> UI の動作をリファクターする方法としてではないとサポート クラスを宣言することによって出される可能性がある任意の拡張メカニズムの一部としている`public`アクセス レベル。 このような<xref:System.Windows.Controls.UserControl>で宣言できます`internal`バッキング コードは、元の XAML 型として参照されている同じアセンブリにコンパイルされる場合にアクセスします。  
  
 完全な信頼での XAML の読み込みを使用しているアプリケーションの<xref:System.Xaml.XamlObjectWriter>を持つクラスを読み込んで`internal`アクセス レベルが常に有効にします。  
  
 XAML を部分信頼で読み込まれるアプリケーションのアクセス レベルの特性を制御を使用して、 <xref:System.Xaml.Permissions.XamlAccessLevel> API。 また、遅延メカニズム (など、WPF テンプレート システム) できる必要があります、アクセス レベルのアクセス許可を反映し、最終的な実行時の評価; 保持するために渡すことによって内部的にこの処理は、<xref:System.Xaml.Permissions.XamlAccessLevel>情報。  
  
### <a name="wpf-implementation"></a>WPF の実装  
 WPF XAML モデルを使用して、部分信頼のアクセス、BAML が部分信頼で読み込まれると、アクセスに制限されます<xref:System.Xaml.Permissions.XamlAccessLevel.AssemblyAccessTo%2A>BAML ソースであるアセンブリ。 WPF を使用して、遅延の<xref:System.Xaml.IXamlObjectWriterFactory.GetParentSettings%2A?displayProperty=nameWithType>アクセス レベルの情報を渡すためのメカニズムとして。  
  
 WPF XAML の用語では、*内部型*は参照元の XAML も含まれており、同じアセンブリで定義されている型です。 アセンブリを意図的に省略する XAML 名前空間を通じてこのような型をマップできる、マッピングの一部を =`xmlns:local="clr-namespace:WPFApplication1"`します。  BAML が内部の型を参照するかどうかとが型にある`internal`アクセス レベル、これが生成されます、`GeneratedInternalTypeHelper`アセンブリのクラス。 避けたい場合`GeneratedInternalTypeHelper`、いずれかを使用する必要がある`public`アクセス レベル、またはする必要があります別のアセンブリに関連するクラスを考慮し、そのアセンブリが依存するようにします。  
  
## <a name="see-also"></a>関連項目

- [カスタム型およびライブラリの XAML 関連の CLR 属性](xaml-related-clr-attributes-for-custom-types-and-libraries.md)
- [XAML サービス](index.md)
