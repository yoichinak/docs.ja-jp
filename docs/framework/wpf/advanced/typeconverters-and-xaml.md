---
title: TypeConverters および XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], TypeConverter class
ms.assetid: f6313e4d-e89d-497d-ac87-b43511a1ae4b
ms.openlocfilehash: ec6eaadae1dd7a7db84538c24e396a14db1a65a4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59164990"
---
# <a name="typeconverters-and-xaml"></a>TypeConverters および XAML
このトピックでは、一般的な XAML 言語機能として、文字列からの型変換の目的について説明します。 .NET Framework で、<xref:System.ComponentModel.TypeConverter>クラスは、特定の目的を XAML 属性の使用法のプロパティの値として使用できる管理対象のカスタム クラスの実装の一部として機能します。 カスタム クラスを作成する XAML 設定可能な属性の値として使用するのには、クラスのインスタンスが必要な場合は、可能性があります、適用する必要があります、<xref:System.ComponentModel.TypeConverterAttribute>カスタムを作成し、クラスに<xref:System.ComponentModel.TypeConverter>クラス、またはその両方です。  

## <a name="type-conversion-concepts"></a>型変換の概念  
  
### <a name="xaml-and-string-values"></a>XAML と文字列値  
 XAML ファイルで属性値を設定するときは、その値の最初の型では、文字列が純粋なテキストです。 などの他のプリミティブ<xref:System.Double>最初は XAML プロセッサにテキスト文字列です。  
  
 XAML プロセッサには、属性値を処理するために 2 つの情報が必要があります。 第 1 の情報は、設定しようとしているプロパティの値の型です。 属性値を定義するすべての文字列は、XAML で処理され、最終的にはその型の値に変換 (解決) される必要があります。 値が、XAML パーサーで認識できるプリミティブ (数値など) である場合は、文字列の直接的な変換が試みられます。 値が列挙体の場合は、文字列を使用して、その列挙体の名前付き定数に一致する名前を確認してください。 値がどちらもパーサーで認識されるプリミティブも列挙体は、その問題の型の場合は、型、または変換後の文字列に基づいて、値のインスタンスを提供できる必要があります。 これは、型コンバーターのクラスを示すことにより行います。 型コンバーターは、事実上、コードが .NET コードの呼び出しに対する XAML シナリオとも可能性がある別のクラスの値を提供するためのヘルパー クラスです。  
  
### <a name="using-existing-type-conversion-behavior-in-xaml"></a>XAML で既存の型変換動作を使用します。  
 基になる XAML の概念に関する知識、に応じてする可能性があります既に型変換動作アプリケーションで使用する基本的な XAML 気付かないうちに。 たとえば、WPF は型の値を使用するプロパティの百を定義します。<xref:System.Windows.Point>します。 A <xref:System.Windows.Point> 2 次元の座標空間内の座標を記述する値は、2 つの重要なプロパティが実際には:<xref:System.Windows.Point.X%2A>と<xref:System.Windows.Point.Y%2A>します。 XAML の時点を指定するときに指定する区切り記号 (コンマ) を使って文字列としての間、<xref:System.Windows.Point.X%2A>と<xref:System.Windows.Point.Y%2A>指定する値。 たとえば、`<LinearGradientBrush StartPoint="0,0" EndPoint="1,1"/>` のように指定します。  
  
 この単純な種類のでも<xref:System.Windows.Point>XAML における単純な使用法が型コンバーターが含まれるとします。 この場合、クラスは<xref:System.Windows.PointConverter>します。  
  
 型コンバーター<xref:System.Windows.Point>マークアップの使用方法を使用するすべてのプロパティのクラス レベルの効率で定義されている<xref:System.Windows.Point>します。 せず、型コンバーターは、ここでは次のとおり、前述の同じ例のマークアップをかなり詳細。  

```xaml
<LinearGradientBrush>
  <LinearGradientBrush.StartPoint>
    <Point X="0" Y="0"/>
  </LinearGradientBrush.StartPoint>
  <LinearGradientBrush.EndPoint>
    <Point X="1" Y="1"/>
  </LinearGradientBrush.EndPoint>
</LinearGradientBrush>
 ```
  
 文字列型の変換または同等のより詳細な構文を使用するかどうかは、一般に、コーディング スタイル選択です。 XAML ツールのワークフローが値の設定方法に影響を与える可能性があります。 一部の XAML ツールは、デザイナーのビューや、独自のシリアル化メカニズムへのラウンドト リップする使いやすいために、最も詳細な形式のマークアップを出力する傾向があります。  
  
 既存の型コンバーターは一般に、適用の有無クラス (またはプロパティ) をチェック WPF と .NET Framework の型で検出された<xref:System.ComponentModel.TypeConverterAttribute>します。 この属性は、クラスの XAML の目的だけでなく可能性のある他の目的で、その型の値のサポート型コンバーターの名前を付けます。  
  
### <a name="type-converters-and-markup-extensions"></a>型コンバーターとマークアップ拡張機能  
 マークアップ拡張機能よぶ型コンバーターは、XAML プロセッサの動作とに適用するシナリオの観点から両方の役割を入力します。 マークアップ拡張機能の使用時にはコンテキストを利用できますが、マークアップ拡張機能が値を提供するプロパティの型変換動作は一般にマークアップ拡張機能の実装ではチェックされません。 つまり、マークアップ拡張機能としてテキスト文字列を返した場合であってもその`ProvideValue`出力するには、特定のプロパティまたはプロパティ値の型に適用されると、その文字列に対する型変換動作は呼び出されません、一般に、マークアップ拡張機能の目的は、プロセスには、文字列と関連する型コンバーターを呼び出さず、オブジェクトを返します。  
  
 マークアップ拡張機能が型コンバーターではなく必要な場合、1 つの一般的な状況は既に存在するオブジェクトへの参照です。 せいぜい、ステートレスな型コンバーターは、望ましいことができない可能性がありますの新しいインスタンスを生成のみでした。 マークアップ拡張機能の詳細については、次を参照してください。[マークアップ拡張機能と WPF XAML](markup-extensions-and-wpf-xaml.md)します。  
  
### <a name="native-type-converters"></a>ネイティブな型コンバーター  
 XAML パーサーの WPF と .NET Framework の実装では、ネイティブ型の変換処理、まだがプリミティブとして考えるが従来どおり型ではない特定の種類があります。 このような型の例として、 <xref:System.DateTime>が挙げられます。 この理由は、.NET Framework のアーキテクチャの動作方法に基づきは: 種類<xref:System.DateTime>mscorlib、.NET で最も基本的なライブラリで定義されます。 <xref:System.DateTime> 属性、依存関係を導入する別のアセンブリから来る属性を設定するのには許可されていません (<xref:System.ComponentModel.TypeConverterAttribute>は System から) ため、属性によって、通常の型コンバーターの検出メカニズムがサポートされることはできません。 代わりに、XAML パーサーでは、このようなネイティブの処理が必要な型のリストがあるし、通常のプリミティブの処理方法と同様にこれらを処理します。 (の場合に<xref:System.DateTime>への呼び出しは、 <xref:System.DateTime.Parse%2A>)。  
  
<a name="Implementing_a_Type_Converter"></a>   
## <a name="implementing-a-type-converter"></a>型コンバーターの実装  
  
### <a name="typeconverter"></a>TypeConverter  
 <xref:System.Windows.Point>以前は、クラスの例<xref:System.Windows.PointConverter>が説明したようにします。 XAML の目的で使用されるすべての型コンバーターは、基底クラスから派生するクラスを XAML の .NET 実装の<xref:System.ComponentModel.TypeConverter>します。 <xref:System.ComponentModel.TypeConverter>クラスは、XAML の存在の前のバージョンの .NET Framework に存在していた; ビジュアル デザイナーでのプロパティ ダイアログ ボックスの文字列変換を提供するその元の使用法の 1 つでした。 XAML の役割の<xref:System.ComponentModel.TypeConverter>を拡張して、文字列の属性値を解析し、可能性がありますの文字列に特定のオブジェクトのプロパティの実行時の値を処理できるようにする文字列に変換して、文字列からの変換の基本クラスには、属性としてシリアル化します。  
  
 <xref:System.ComponentModel.TypeConverter> XAML 処理の目的の文字列から変換するために関連する 4 つのメンバーを定義します。  
  
-   <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>  
  
-   <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>  
  
 最も重要なメソッドは、これらのうち、<xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>します。 このメソッドは、入力文字列を必要なオブジェクト型に変換します。 厳密に言えば、<xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>幅広い範囲の型をコンバーターの目的の型に変換、そのため、実行時の変換をサポートするなど、XAML の目的で XAML 以外の目的を提供するメソッドを実装する可能性があります処理できるコード パスのみである、<xref:System.String>重要な入力します。  
  
 [次へ] の最も重要なメソッドは<xref:System.ComponentModel.TypeConverter.ConvertTo%2A>します。 かどうか、アプリケーションは、マークアップ表現に変換されます (たとえば、ファイルとして XAML に保存されます) 場合、<xref:System.ComponentModel.TypeConverter.ConvertTo%2A>はマークアップ表現を生成を担当します。 この場合は、XAML の重要なコード パスは、渡すときに、`destinationType`の<xref:System.String>します。  
  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> と <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> は、サービスが <xref:System.ComponentModel.TypeConverter> の実装の機能を照会する時に使用されるサポート メソッドです。 これらのメソッドは、その型について、相当する変換メソッドをコンバーターがサポートしている場合に `true` を返すように実装する必要があります。 XAML の目的では、通常、 <xref:System.String> 型であることを意味します。  
  
### <a name="culture-information-and-type-converters-for-xaml"></a>カルチャ情報と XAML の型コンバーター  
 各<xref:System.ComponentModel.TypeConverter>実装ことができます、変換に対して有効な文字列の構成要素の独自の解釈があるとも使用したり、パラメーターとして渡された型の説明を無視します。 カルチャと XAML 型の変換に関して重要な考慮事項があります。 XAML では、ローカライズ可能な文字列を使用して属性値としてはサポートされて完全。 XAML 属性値の型コンバーターが、必ずしも特定の言語の解析動作が関与するための特定のカルチャ要件型コンバーターの入力がサポートされていないためにそのローカライズ可能な文字列を使用して、使用して、`en-US`カルチャ。 この制限の設計上の理由の詳細については、XAML 言語仕様を参照してください ([\[MS XAML\]](https://go.microsoft.com/fwlink/?LinkId=114525))。  
  
 カルチャが問題になることなどに、一部のカルチャが数値の小数点記号としてコンマを使用します。 WPF XAML の型コンバーターの多くが、これは、区切り記号としてコンマを使用する動作と競合がこの (一般的な X などの従来の慣習に基づき、Y フォーム、またはコンマ区切りリスト)。 周囲の XAML でカルチャを渡すことも (設定`Language`または`xml:lang`を`sl-SI`カルチャ、この方法で小数点のコンマを使用するカルチャの例) で問題が解決しません。  
  
### <a name="implementing-convertfrom"></a>ConvertFrom の実装  
 XAML をサポートする <xref:System.ComponentModel.TypeConverter> の実装としてコンバーターを使用できるようにするためには、そのコンバーターの <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> メソッドが `value` パラメーターとして文字列を受け入れる必要があります。 書式設定、およびによって変換できる有効な文字列がかどうか、<xref:System.ComponentModel.TypeConverter>実装し、返されたオブジェクトはプロパティによって予期される型へのキャストをサポートする必要があります。 それ以外の場合、 <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> 実装は `null`を返す必要があります。  
  
 各<xref:System.ComponentModel.TypeConverter>実装ことができます、変換に対して有効な文字列の構成要素の独自の解釈があるとも使用したり、パラメーターとして渡された型の説明やカルチャ コンテキストを無視します。 ただし、処理、WPF XAML の場合は、型の説明コンテキストに値を渡さない場合がありますに基づくカルチャを渡さない場合がありますも`xml:lang`します。  
  
> [!NOTE]
>  特に、中かっこ文字を使用しないでください {、文字列の書式の要素として。 これらの文字は、マークアップ拡張シーケンスの開始および終了を示す文字として予約されています。  
  
### <a name="implementing-convertto"></a>ConvertTo の実装  
 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> は、シリアル化のサポートで使用される可能性があります。 カスタム型およびその型コンバーターに対して <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> によるシリアル化をサポートすることは、絶対要件ではありません。 ただし、コントロールを実装する場合、またはクラスの機能または設計の一部としてシリアル化を使用する場合は、 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>を実装する必要があります。  
  
 として使用するのには、 <xref:System.ComponentModel.TypeConverter> 、XAML をサポートする実装、<xref:System.ComponentModel.TypeConverter.ConvertTo%2A>としてそのコンバーターのメソッドがサポートされている型 (または値) のインスタンスを受け入れる必要があります、`value`パラメーター。 ときに、`destinationType`パラメーターは、型<xref:System.String>、返されるオブジェクトとしてキャストできる必要がありますし、<xref:System.String>します。 返される文字列は、 `value`のシリアル化された値を表している必要があります。 理想的には、シリアル化形式を選択する必要がありますにその文字列が渡された場合は、同じ値を生成できるが、<xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>重要な情報が失われることがなく、同じコンバーターの実装。  
  
 値をシリアル化することはできません、またはコンバーターがシリアル化をサポートしていない場合、<xref:System.ComponentModel.TypeConverter.ConvertTo%2A>実装を返す必要があります`null`、ここでは例外をスローすることはできます。 例外をスローする場合は、一部としてその変換を使用できないことを報告する必要がありますが、<xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>実装ようにチェックのベスト プラクティス<xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>例外を回避するためにはサポートされて最初。  
  
 場合`destinationType`型のパラメーターがない<xref:System.String>、独自のコンバーター処理を選択できます。 通常、基本の実装、basemost での処理を元に戻すには<xref:System.ComponentModel.TypeConverter.ConvertTo%2A>特定の例外を発生させます。  
  
### <a name="implementing-canconvertto"></a>CanConvertTo の実装  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> の実装は、 `true` が `destinationType` 型の場合は <xref:System.String>を返し、それ以外の場合は基底の実装に任せる必要があります。  
  
### <a name="implementing-canconvertfrom"></a>CanConvertFrom の実装  
 <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> の実装は、 `true` が `sourceType` 型の場合は <xref:System.String>を返し、それ以外の場合は基底の実装に任せる必要があります。  
  
<a name="Applying_the_TypeConverterAttribute"></a>   
## <a name="applying-the-typeconverterattribute"></a>TypeConverterAttribute の適用  
 カスタム型コンバーターとして使用するために適用する必要があります、XAML プロセッサによってカスタム クラスの型コンバーター、 [!INCLUDE[TLA#tla_netframewkattr](../../../../includes/tlasharptla-netframewkattr-md.md)] <xref:System.ComponentModel.TypeConverterAttribute>クラス定義にします。 属性を通して指定する <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A> は、カスタム型コンバーターの型名である必要があります。 この属性を適用するには、XAML プロセッサは、プロパティの型が、カスタム クラスの型を使用して値を処理する場合、入力文字列と、オブジェクトのインスタンスを返します。  
  
 また、プロパティごとに型コンバーターを提供することもできます。 クラス定義に [!INCLUDE[TLA#tla_netframewkattr](../../../../includes/tlasharptla-netframewkattr-md.md)] <xref:System.ComponentModel.TypeConverterAttribute> を適用する代わりに、プロパティ定義 (メイン定義内の `get`/`set` 実装ではなくメイン定義自体) に適用します。 プロパティの型は、カスタム型コンバーターによって処理される型と一致する必要があります。 この属性を適用するには、Xaml では、そのプロパティの値を処理する場合、入力文字列を処理し、オブジェクト インスタンスを返します。 プロパティの型コンバーターの手法は Microsoft .NET Framework とは、クラス定義を制御することはできませんし、適用できません他のいくつかのライブラリからプロパティの型を使用する場合に特に便利です、<xref:System.ComponentModel.TypeConverterAttribute>があります。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ComponentModel.TypeConverter>
- [XAML の概要 (WPF)](xaml-overview-wpf.md)
- [マークアップ拡張機能と WPF XAML](markup-extensions-and-wpf-xaml.md)
- [XAML 構文の詳細](xaml-syntax-in-detail.md)
