---
title: カスタム型およびライブラリの XAML 関連の CLR 属性
ms.date: 03/30/2017
helpviewer_keywords:
- CLR attributes for custom types [XAML Services]
ms.assetid: 5dfb299a-b6e2-41b8-8694-e6ac987547f1
ms.openlocfilehash: ace1b40b25bd12ff7092459e468a90f382434bf4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59086211"
---
# <a name="xaml-related-clr-attributes-for-custom-types-and-libraries"></a>カスタム型およびライブラリの XAML 関連の CLR 属性
このトピックでは、.NET Framework XAML サービスで定義されている共通言語ランタイム (CLR) の属性について説明します。 他の CLR 属性、.NET Framework で定義されているアセンブリまたは型へのアプリケーションの XAML に関連するシナリオについても説明します。 これらの CLR 属性を持つアセンブリ、型、またはメンバーの属性型に関連する XAML 型システム情報を提供します。 XAML ノード ストリームを直接処理するため、または専用の XAML リーダーと XAML ライターでは、.NET Framework XAML サービスを使用するすべての XAML のコンシューマーに情報が提供されます。  
  
## <a name="xaml-related-clr-attributes-for-custom-types-and-custom-members"></a>カスタム型およびメンバーのカスタム XAML 関連の CLR 属性  
 CLR 属性を使用するには、こと、型を定義する全体的な CLR を使用している場合、それ以外の場合 などの属性は使用できません必要があります。 CLR を使用してバックアップの種類を定義する場合、.NET Framework XAML サービスの XAML ライターで使用される既定の XAML スキーマ コンテキストはバッキング アセンブリに対してリフレクションの CLR 属性を読み取ることができます。  
  
 次のセクションでは、カスタムの型またはカスタムのメンバーに適用できる XAML 関連の属性について説明します。 CLR の各属性は、XAML 型システムに関連する情報を通信します。 読み込みパス、によりか、属性付きの情報が有効な XAML ノード ストリームを形成する XAML リーダーまたは XAML ライターが有効なオブジェクト グラフの生成に役立ちます。 ファイルのパス、XAML 型システム情報を再構成する有効な XAML ノード ストリームを形成する XAML リーダーは、いずれかの属性付きの情報または、シリアル化のヒントまたは XAML ライターまたは XAML その他のコンシューマーの要件を宣言します。  
  
### <a name="ambientattribute"></a>AmbientAttribute  
 **リファレンス ドキュメント。**  <xref:System.Windows.Markup.AmbientAttribute>  
  
 **適用対象:** クラス、プロパティ、または`get`アタッチ可能なプロパティをサポートするアクセサーのメンバー。  
  
 **引数:** なし  
  
 <xref:System.Windows.Markup.AmbientAttribute> XAML でのアンビエント プロパティの概念で解釈する必要があります、プロパティまたは属性付きの型を使用するすべてのプロパティを示します。 アンビエントの概念は XAML プロセッサがメンバーの型の所有者を確認する方法と関連します。 アンビエント プロパティは、即時の XAML ノードが作成されるセットの一般的な型メンバーの参照が中断されているが、オブジェクト グラフを作成するときに、パーサー コンテキストで使用できる値が必要な場合のプロパティです。  
  
 アンビエントの概念は、アタッチ可能なメンバーは、CLR 属性を定義する方法の観点からのプロパティとしては表されないに適用できる<xref:System.AttributeTargets>します。 のみの場合、メソッドの属性の使用を適用する必要があります、 `get` XAML のアタッチの使用をサポートするアクセサー。  
  
### <a name="constructorargumentattribute"></a>ConstructorArgumentAttribute  
 **リファレンス ドキュメント。**  <xref:System.Windows.Markup.ConstructorArgumentAttribute>  
  
 **適用対象:** クラス  
  
 **引数:** 単一のコンス トラクターの引数に一致するプロパティの名前を指定する文字列。  
  
 <xref:System.Windows.Markup.ConstructorArgumentAttribute> オブジェクトは、既定以外のコンス トラクター構文を使用して初期化でき、指定した名前のプロパティが構造情報を提供することを指定します。 この情報は主に XAML シリアル化用です。 詳細については、「 <xref:System.Windows.Markup.ConstructorArgumentAttribute> 」を参照してください。  
  
### <a name="contentpropertyattribute"></a>ContentPropertyAttribute  
 **リファレンス ドキュメント。**  <xref:System.Windows.Markup.ContentPropertyAttribute>  
  
 **適用対象:** クラス  
  
 **引数:** 属性付く型のメンバーの名前を指定する文字列。  
  
 <xref:System.Windows.Markup.ContentPropertyAttribute> 引数で指定された名前のプロパティがその型の XAML コンテンツ プロパティとして使用する必要があることを示します。 XAML コンテンツ プロパティの定義を定義する型に割り当て可能なすべての派生型を継承します。 適用することで特定の派生型の定義をオーバーライドできます<xref:System.Windows.Markup.ContentPropertyAttribute>特定の型を派生します。  
  
 XAML の content プロパティとして機能するプロパティの XAML 使用量のプロパティ要素のプロパティのタグ付けを省略できます。 通常、モデルのコンテンツおよびコンテインメントの簡素化された XAML マークアップを促進する XAML コンテンツのプロパティを指定します。 1 つのメンバーは、XAML コンテンツ プロパティとして指定することができます、ために、に関するいくつかのコンテナーの型のプロパティを XAML の content プロパティとして指定する必要がありますさせるデザインの選択肢がある場合があります。 その他のコンテナーのプロパティは、明示的なプロパティ要素で使用する必要があります。  
  
 XAML コンテンツ プロパティでは、XAML ノード ストリーム生成も`StartMember`と`EndMember`のプロパティの名前を使用して、ノード、<xref:System.Xaml.XamlMember>します。 メンバーが XAML コンテンツ プロパティであるかどうかを確認するのには、確認、<xref:System.Xaml.XamlType>値から、`StartObject`位置し、の値を取得<xref:System.Xaml.XamlType.ContentProperty%2A>します。  
  
### <a name="contentwrapperattribute"></a>ContentWrapperAttribute  
 **リファレンス ドキュメント。**  <xref:System.Windows.Markup.ContentWrapperAttribute>  
  
 **適用対象:** クラス、具体的にはコレクション型です。  
  
 **引数:** A<xref:System.Type>外部コンテンツのコンテンツ ラッパー型として使用する型を指定します。  
  
 <xref:System.Windows.Markup.ContentWrapperAttribute> 外部コンテンツをラップするために使用する、関連付けられているコレクション型では、1 つまたは複数の種類を指定します。 外部コンテンツをコンテンツのプロパティの型の型システムの制約がキャプチャされていないすべての所有元の型の XAML の使用状況をサポートするコンテンツ ケースの場合を指します。 XAML のサポートなど、特定の種類のコンテンツは厳密に型指定された汎用文字列をサポートする可能性があります<xref:System.Collections.ObjectModel.Collection%601>します。 コンテンツ ラッパーは、移行のテキスト関連のコンテンツ モデルなどのコレクションに割り当て可能な値の XAML の構想に既存のマークアップ規則を移行するのに役立ちます。  
  
 1 つ以上のコンテンツ ラッパー型を指定するには、複数回、属性を適用します。  
  
### <a name="dependsonattribute"></a>DependsOnAttribute  
 **リファレンス ドキュメント。**  <xref:System.Windows.Markup.DependsOnAttribute>  
  
 **適用対象:** プロパティ  
  
 **引数:** 属性付く型の別のメンバーの名前を指定する文字列。  
  
 <xref:System.Windows.Markup.DependsOnAttribute> 属性付きプロパティが別のプロパティの値に依存していることを示します。 この属性をプロパティ定義に適用する、XAML オブジェクトの記述で依存プロパティが最初に処理されるようにします。 使用状況<xref:System.Windows.Markup.DependsOnAttribute>解析の特定の順序を有効なオブジェクトの作成に従う必要がある型のプロパティの例外的なケースを指定します。  
  
 複数を適用する<xref:System.Windows.Markup.DependsOnAttribute>場合に、プロパティ定義します。  
  
### <a name="markupextensionreturntypeattribute"></a>MarkupExtensionReturnTypeAttribute  
 **リファレンス ドキュメント。**  <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>  
  
 **適用対象:** クラスは、あると想定されます、<xref:System.Windows.Markup.MarkupExtension>派生型。  
  
 **引数:** A<xref:System.Type>として期待する最も正確な型を指定する、`ProvideValue`属性付きの結果<xref:System.Windows.Markup.MarkupExtension>します。  
  
詳細については、[XAML のマークアップ拡張機能の概要](markup-extensions-for-xaml-overview.md) を参照してください。
  
### <a name="namescopepropertyattribute"></a>NameScopePropertyAttribute  
 **リファレンス ドキュメント。**  <xref:System.Windows.Markup.NameScopePropertyAttribute>  
  
 **適用対象:** クラス  
  
 **引数:** 2 つの属性の形式をサポートしています。  
  
-   属性付く型のプロパティの名前を指定する文字列。  
  
-   プロパティの名前を指定する文字列と<xref:System.Type>名前付きプロパティを定義する型。 このフォームでは、XAML 名前スコープのプロパティとして、アタッチ可能なメンバーを指定するためです。  
  
 <xref:System.Windows.Markup.NameScopePropertyAttribute> 属性付きクラスの XAML 名前スコープの値を提供するプロパティを指定します。 実装するオブジェクトを参照する XAML 名前スコープのプロパティが期待どおり<xref:System.Windows.Markup.INameScope>し、実際の XAML 名前スコープ、そのストアとその動作を保持します。  
  
### <a name="runtimenamepropertyattribute"></a>RuntimeNamePropertyAttribute  
 **リファレンス ドキュメント。**  <xref:System.Windows.Markup.RuntimeNamePropertyAttribute>  
  
 **適用対象:** クラス  
  
 **引数:** 属性付く型の実行時の name プロパティの名前を指定する文字列。  
  
 <xref:System.Windows.Markup.RuntimeNamePropertyAttribute> XAML にマップする属性付く型のプロパティを報告[X:name ディレクティブ](x-name-directive.md)します。 プロパティは、型でなければなりません<xref:System.String>読み取り/書き込みをする必要があります。  
  
 定義を定義する型に割り当て可能なすべての派生型を継承します。 適用することで特定の派生型の定義をオーバーライドできます<xref:System.Windows.Markup.RuntimeNamePropertyAttribute>特定の型を派生します。  
  
### <a name="trimsurroundingwhitespaceattribute"></a>TrimSurroundingWhitespaceAttribute  
 **リファレンス ドキュメント。**  <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute>  
  
 **適用対象:** 種類  
  
 **引数:** なし。  
  
 <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> 空白の重要なコンテンツ内の子要素として表示される特定の種類に適用されます (コンテンツが含まれるコレクションによって保持されている<xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>)。 <xref:System.Windows.Markup.TrimSurroundingWhitespaceAttribute> 主に、保存に関連は、パスが利用できる、読み込みパスで XAML 型システムで調べることで<xref:System.Xaml.XamlType.TrimSurroundingWhitespace%2A?displayProperty=nameWithType>します。 詳細については、次を参照してください。[空白 XAML 処理](whitespace-processing-in-xaml.md)します。  
  
### <a name="typeconverterattribute"></a>TypeConverterAttribute  
 **リファレンス ドキュメント。**  <xref:System.ComponentModel.TypeConverterAttribute>  
  
 **適用対象:** クラス、プロパティ、メソッド (唯一 XAML 有効なメソッドの場合は、`get`アクセサー、アタッチ可能なメンバーをサポートする)。  
  
 **引数:**<xref:System.ComponentModel.TypeConverter> の <xref:System.Type>。  
  
 <xref:System.ComponentModel.TypeConverterAttribute> コンテキストのカスタムの参照を XAML で<xref:System.ComponentModel.TypeConverter>します。 これは、<xref:System.ComponentModel.TypeConverter>カスタムの型、またはその型のメンバーの型変換動作を提供します。  
  
 適用する、<xref:System.ComponentModel.TypeConverterAttribute>属性を型、型コンバーターの実装を参照します。 クラス、構造体、またはインターフェイスで、XAML の型コンバーターを定義できます。 変換がネイティブで有効である列挙体の場合、型変換を提供する必要はありません。  
  
 型コンバーターを目的の型に属性またはマークアップでは、初期化テキストに使用される文字列に変換することがあります。 詳細については、次を参照してください。 [TypeConverters および XAML](../wpf/advanced/typeconverters-and-xaml.md)します。  
  
 型のすべての値に適用するではなくに、特定のプロパティに XAML の型コンバーターの動作を確立することもできます。 この場合は、適用<xref:System.ComponentModel.TypeConverterAttribute>プロパティ定義 (外側の定義、固有ではない`get`と`set`定義)。  
  
 カスタムのアタッチ可能なメンバーの XAML の使用状況の型コンバーターの動作を適用することで割り当てることができる<xref:System.ComponentModel.TypeConverterAttribute>を`get`XAML の使用状況をサポートするメソッド アクセサー。  
  
 ような<xref:System.ComponentModel.TypeConverter>、 <xref:System.ComponentModel.TypeConverterAttribute> XAML の存在の前に .NET Framework に存在し、型コンバーターのモデルが他の目的で提供されます。 参照および使用するために<xref:System.ComponentModel.TypeConverterAttribute>、完全に修飾または提供する必要があります、`using`ステートメント<xref:System.ComponentModel>します。 システム アセンブリは、プロジェクトでも含める必要があります。  
  
### <a name="uidpropertyattribute"></a>UidPropertyAttribute  
 **リファレンス ドキュメント。**  <xref:System.Windows.Markup.UidPropertyAttribute>  
  
 **適用対象:** クラス  
  
 **引数:** 関連するプロパティを名前で参照する文字列。  
  
 エイリアスを表すクラスの CLR プロパティを示す、 [X:uid ディレクティブ](x-uid-directive.md)します。  
  
### <a name="usableduringinitializationattribute"></a>UsableDuringInitializationAttribute  
 **リファレンス ドキュメント。**  <xref:System.Windows.Markup.UsableDuringInitializationAttribute>  
  
 **適用対象:** クラス  
  
 **引数:** ブール値。 属性の使用目的に使用すると場合、常に指定として`true`します。  
  
 この型が XAML オブジェクト グラフの作成中に上から下に組み込まれるかどうかを示します。 これは、高度な概念、プログラミング モデルの定義に関連性が高い可能性があります。 詳細については、「 <xref:System.Windows.Markup.UsableDuringInitializationAttribute> 」を参照してください。  
  
### <a name="valueserializerattribute"></a>ValueSerializerAttribute  
 **リファレンス ドキュメント。**  <xref:System.Windows.Markup.ValueSerializerAttribute>  
  
 **適用対象:** クラス、プロパティ、メソッド (唯一 XAML 有効なメソッドの場合は、`get`アクセサー、アタッチ可能なメンバーをサポートする)。  
  
 **引数:** A<xref:System.Type>属性付きの型のすべてのプロパティをシリアル化するときに使用するには、値シリアライザーのサポート クラスを指定するか、属性付きプロパティを特定します。  
  
 <xref:System.Windows.Markup.ValueSerializer> 詳細の状態とよりもコンテキストが必要な値のシリアル化クラスを指定します、<xref:System.ComponentModel.TypeConverter>は。 <xref:System.Windows.Markup.ValueSerializer> 適用することで、アタッチ可能なメンバーに関連付けることができます、<xref:System.Windows.Markup.ValueSerializerAttribute>属性を静的な`get`アタッチ可能メンバーのアクセサー メソッド。 値のシリアル化が該当するもの列挙体、インターフェイスおよび構造体、デリゲートではなく。  
  
### <a name="whitespacesignificantcollectionattribute"></a>WhitespaceSignificantCollectionAttribute  
 **リファレンス ドキュメント。**  <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute>  
  
 **適用対象:** クラス、具体的にはオブジェクト要素の周囲の空白文字が表示される UI の重要なあります混合のコンテンツをホストする予想されるコレクション型です。  
  
 **引数:** なし。  
  
 <xref:System.Windows.Markup.WhitespaceSignificantCollectionAttribute> コレクション内の XAML ノード ストリームの値ノードの構築に影響は、XAML プロセッサによって空白大きなとしてコレクション型を処理する必要があることを示します。 詳細については、次を参照してください。[空白 XAML 処理](whitespace-processing-in-xaml.md)します。  
  
### <a name="xamldeferloadattribute"></a>XamlDeferLoadAttribute  
 **リファレンス ドキュメント。**  <xref:System.Windows.Markup.XamlDeferLoadAttribute>  
  
 **適用対象:** クラスのプロパティ。  
  
 **引数:** サポートする 2 つの属性の型を文字列としてのフォームまたはとして型<xref:System.Type>します。 以下を参照してください。<xref:System.Windows.Markup.XamlDeferLoadAttribute>  
  
 クラスまたはプロパティ (テンプレート動作) などの XAML の遅延読み込みの使用を持つし、遅延の動作とその宛先/コンテンツ タイプをできるようにするクラスのレポートを示します。  
  
### <a name="xamlsetmarkupextensionattribute"></a>XamlSetMarkupExtensionAttribute  
 **リファレンス ドキュメント。**  <xref:System.Windows.Markup.XamlSetMarkupExtensionAttribute>  
  
 **適用対象:** クラス  
  
 **引数:** コールバックの名前を付けます。  
  
 クラスはマークアップ拡張機能を使用して、そのプロパティの 1 つ以上の値を指定することができ、XAML ライターがクラスの任意のプロパティでマークアップ拡張機能のセットの操作を実行する前に呼び出す必要のあるハンドラーを参照を示します。  
  
### <a name="xamlsettypeconverterattribute"></a>XamlSetTypeConverterAttribute  
 **リファレンス ドキュメント。**  <xref:System.Windows.Markup.XamlSetTypeConverterAttribute>  
  
 **適用対象:** クラス  
  
 **引数:** コールバックの名前を付けます。  
  
 クラスが XAML ライターは、任意のプロパティ、クラスの型コンバーターの設定操作を実行する前に呼び出す必要のあるハンドラーを参照、そのプロパティの 1 つ以上の値を指定する型コンバーターを使用できることを示します。  
  
### <a name="xmllangpropertyattribute"></a>XmlLangPropertyAttribute  
 **リファレンス ドキュメント。**  <xref:System.Windows.Markup.XmlLangPropertyAttribute>  
  
 **適用対象:** クラス  
  
 **引数:** エイリアスのプロパティの名前を指定する文字列`xml:lang`属性付く型。  
  
 <xref:System.Windows.Markup.XmlLangPropertyAttribute> XML にマップする属性付く型のプロパティを報告`lang`ディレクティブ。 プロパティが必ずしも型の<xref:System.String>が (実行するには、プロパティの型、または特定のプロパティの型コンバーターを関連付けることによって) 文字列から割り当てることがあります。 プロパティは、読み取り/書き込みをする必要があります。  
  
 マッピングのシナリオは、`xml:lang`ランタイム オブジェクト モデルは、具体的には、XMLDOM を処理することがなく XML が指定した言語の情報へのアクセスを持つようにします。  
  
 定義を定義する型に割り当て可能なすべての派生型を継承します。 適用することで特定の派生型の定義をオーバーライドできます<xref:System.Windows.Markup.XmlLangPropertyAttribute>特定の派生型、これは、一般的ではないシナリオには。  
  
## <a name="xaml-related-clr-attributes-at-the-assembly-level"></a>アセンブリ レベルでの XAML 関連の CLR 属性  
 次のセクションでは、型またはメンバーの定義には適用されませんが、アセンブリに適用される代わりに、XAML 関連の属性について説明します。 これらの属性は、XAML で使用するカスタム型を含むライブラリを定義する全体的な目標に関連します。 一部の属性には影響を与える、XAML ノード ストリームを直接が、ノード ストリームを使用するには、その他のユーザー内で渡されます。 情報のコンシューマーには、デザイン環境やし、XAML 名前空間の情報が必要なプレフィックスの情報に関連付けられているシリアル化プロセスが含まれます。 XAML スキーマ コンテキストを (.NET Framework XAML サービスの既定値を含む) もこの情報を使用します。  
  
### <a name="xmlnscompatiblewithattribute"></a>XmlnsCompatibleWithAttribute  
 **リファレンス ドキュメント。**  <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute>  
  
 **引数:**  
  
-   包含する XAML 名前空間の識別子を指定する文字列。  
  
-   前の引数から XAML 名前空間を包含できる XAML 名前空間の識別子を指定する文字列。  
  
 <xref:System.Windows.Markup.XmlnsCompatibleWithAttribute> XAML 名前空間を別の XAML 名前空間によって包括できることを指定します。 通常、包含する側の XAML 名前空間は、あらかじめ定義した <xref:System.Windows.Markup.XmlnsDefinitionAttribute> で示されます。 この方法は、以前に定義されたマークアップに対して以前のバージョン管理されたボキャブラリとの互換性には、ライブラリでは、XAML ボキャブラリのバージョン管理に使用します。  
  
### <a name="xmlnsdefinitionattribute"></a>XmlnsDefinitionAttribute  
 **リファレンス ドキュメント。**  <xref:System.Windows.Markup.XmlnsDefinitionAttribute>  
  
 **引数:**  
  
-   定義する XAML 名前空間の識別子を指定する文字列。  
  
-   CLR 名前空間の名前を示す文字列。 CLR 名前空間は、独自のアセンブリでパブリック型を定義する必要があり、CLR 名前空間の型の少なくとも 1 つを XAML の使用状況を想定する必要があります。  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> XAML 名前空間と CLR 名前空間は、XAML オブジェクト ライターまたは XAML スキーマ コンテキストによって使用される型の解決し、アセンブリごとに、マッピングを指定します。  
  
 1 つ以上<xref:System.Windows.Markup.XmlnsDefinitionAttribute>をアセンブリに適用できます。 これは、次の理由の任意の組み合わせの実行可能性があります。  
  
-   ライブラリ デザインには、実行時に API アクセス; の論理構造の複数の CLR 名前空間が含まれています。ただし、それらの名前空間内のすべての型と同じ XAML 名前空間を参照することによって XAML-使用できるようにします。 この場合は、いくつか適用<xref:System.Windows.Markup.XmlnsDefinitionAttribute>属性を使用して同じ<xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A>値しますが、異なる<xref:System.Windows.Markup.XmlnsDefinitionAttribute.ClrNamespace%2A>値。 これは、アプリケーション、フレームワークは、一般的な使用方法の既定の XAML 名前空間を意図している XAML 名前空間のマッピングを定義する場合に特に便利です。  
  
-   ライブラリ デザインには、複数の CLR 名前空間が含まれていますが、その CLR 名前空間の型の使用状況の間で意図的な XAML 名前空間の分離をたいとします。  
  
-   アセンブリの CLR 名前空間を定義して、1 つ以上の XAML 名前空間を介してアクセスできるようにします。 このシナリオでは、同じコードベースで複数のボキャブラリをサポートしているときに発生します。  
  
-   XAML 言語のサポートは、1 つまたは複数の CLR 名前空間で定義します。 これらの場合、<xref:System.Windows.Markup.XmlnsDefinitionAttribute.XmlNamespace%2A>値は`http://schemas.microsoft.com/winfx/2006/xaml`します。  
  
### <a name="xmlnsprefixattribute"></a>XmlnsPrefixAttribute  
 **リファレンス ドキュメント。**  <xref:System.Windows.Markup.XmlnsPrefixAttribute>  
  
 **引数:**  
  
-   XAML 名前空間の識別子を指定する文字列。  
  
-   推奨されるプレフィックスを指定する文字列。  
  
 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> XAML 名前空間を使用する推奨されるプレフィックスを指定します。 プレフィックスは、.NET Framework XAML サービスによってシリアル化される XAML ファイルで要素と属性を記述するときに便利です<xref:System.Xaml.XamlXmlWriter>、または XAML を実装するライブラリを XAML を持つデザイン環境で操作するときの機能を編集します。  
  
 1 つ以上<xref:System.Windows.Markup.XmlnsPrefixAttribute>をアセンブリに適用できます。 これは、次の理由の任意の組み合わせの実行可能性があります。  
  
-   アセンブリは、1 つ以上の XAML 名前空間の種類を定義します。 この場合は XAML 名前空間ごとに別のプレフィックス値を定義する必要があります。  
  
-   複数のボキャブラリをサポートしているし、ボキャブラリおよび XAML 名前空間ごとに異なるプレフィックスを使用します。  
  
-   アセンブリに XAML 言語のサポートを定義している、<xref:System.Windows.Markup.XmlnsDefinitionAttribute>の`http://schemas.microsoft.com/winfx/2006/xaml`します。 この場合、通常必要がありますを昇格するプレフィックス`x`します。  
  
> [!NOTE]
>  .NET framework XAML サービスでは、XAML 関連の属性も定義します<xref:System.Windows.Markup.RootNamespaceAttribute>します。 この属性は、プロジェクト システム サポートについては、アセンブリ レベル属性と、XAML のカスタム型に関係はありません。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Attribute>
- [.NET Framework XAML サービスで使用するためのカスタム型の定義](defining-custom-types-for-use-with-net-framework-xaml-services.md)
