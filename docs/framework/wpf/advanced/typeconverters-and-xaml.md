---
title: TypeConverters および XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], TypeConverter class
ms.assetid: f6313e4d-e89d-497d-ac87-b43511a1ae4b
ms.openlocfilehash: 8c39fe75eea5042657cab533a0a557d966802a1b
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/30/2019
ms.locfileid: "70169018"
---
# <a name="typeconverters-and-xaml"></a>TypeConverters および XAML
このトピックでは、一般的な XAML 言語機能としての文字列からの型変換の目的について説明します。 .NET Framework では、クラス<xref:System.ComponentModel.TypeConverter>は、XAML 属性の使用でプロパティ値として使用できるマネージカスタムクラスの実装の一部として、特定の目的を果たします。 カスタムクラスを作成し、クラスのインスタンスを XAML 設定可能な属性値として使用できるようにする場合は、を<xref:System.ComponentModel.TypeConverterAttribute>クラスに適用するか、カスタム<xref:System.ComponentModel.TypeConverter>クラスを記述するか、またはその両方を使用する必要があります。  

## <a name="type-conversion-concepts"></a>型変換の概念  
  
### <a name="xaml-and-string-values"></a>XAML と文字列値  
 XAML ファイルで属性値を設定すると、その値の最初の型は純粋テキストの文字列になります。 など<xref:System.Double>の他のプリミティブも、XAML プロセッサに対する最初のテキスト文字列です。  
  
 XAML プロセッサは、属性値を処理するために2つの情報を必要とします。 第 1 の情報は、設定しようとしているプロパティの値の型です。 属性値を定義するすべての文字列は、XAML で処理され、最終的にはその型の値に変換 (解決) される必要があります。 値が、XAML パーサーで認識できるプリミティブ (数値など) である場合は、文字列の直接的な変換が試みられます。 値が列挙型の場合、文字列は、その列挙体の名前付き定数に一致する名前があるかどうかを確認するために使用されます。 値がパーサーで認識されるプリミティブでも列挙でもない場合、問題の型は、変換後の文字列に基づいて、型のインスタンスまたは値を提供できる必要があります。 これを行うには、型コンバータークラスを指定します。 型コンバーターは、実際には、XAML シナリオに対しても、.NET コードのコード呼び出しの場合でも、別のクラスの値を提供するためのヘルパークラスです。  
  
### <a name="using-existing-type-conversion-behavior-in-xaml"></a>XAML での既存の型変換動作の使用  
 基になる XAML の概念に関する知識によっては、基本的なアプリケーション XAML で型変換の動作を使用していることがわかっていない場合があります。 たとえば、WPF では、型<xref:System.Windows.Point>の値を受け取る文字どおり数百のプロパティが定義されています。 は、2次元の座標空間の座標を表す値です。 <xref:System.Windows.Point.X%2A>と<xref:System.Windows.Point.Y%2A>の2つの重要なプロパティがあります。 <xref:System.Windows.Point> XAML でポイントを指定する場合は、指定した値と<xref:System.Windows.Point.X%2A> <xref:System.Windows.Point.Y%2A>値の間に区切り記号 (通常はコンマ) を含む文字列として指定します。 たとえば、`<LinearGradientBrush StartPoint="0,0" EndPoint="1,1"/>` のように指定します。  
  
 この単純型と XAML <xref:System.Windows.Point>での単純な使用についても、型コンバーターが必要です。 この場合、はクラス<xref:System.Windows.PointConverter>です。  
  
 クラスレベルで定義<xref:System.Windows.Point>されているの型コンバーターは、によって実行<xref:System.Windows.Point>されるすべてのプロパティのマークアップの使用を効率化します。 ここでは型コンバーターを使用しない場合、前に示したのと同じ例について、より詳細なマークアップが必要になります。  

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
  
 型変換文字列を使用するか、より詳細な同等の構文を使用するかは、通常、コーディングスタイルとして選択します。 XAML ツールワークフローは、値の設定方法にも影響を与える可能性があります。 XAML ツールによっては、デザイナービューや独自のシリアル化機構にラウンドトリップしやすくなるため、最も詳細なマークアップ形式が生成される傾向があります。  
  
 既存の型コンバーターは、通常、クラス (またはプロパティ) が適用さ<xref:System.ComponentModel.TypeConverterAttribute>れているかどうかをチェックすることによって、WPF および .NET Framework 型で検出できます。 この属性は、XAML の目的だけでなく、他の目的でも、その型の値に対してサポートされている型コンバーターであるクラスに名前を付けます。  
  
### <a name="type-converters-and-markup-extensions"></a>型コンバーターとマークアップ拡張機能  
 マークアップ拡張機能と型コンバーターは、XAML プロセッサの動作と、それらが適用されるシナリオに関して直交ロールを設定します。 マークアップ拡張機能の使用時にはコンテキストを利用できますが、マークアップ拡張機能が値を提供するプロパティの型変換動作は一般にマークアップ拡張機能の実装ではチェックされません。 つまり、マークアップ拡張機能が`ProvideValue`出力としてテキスト文字列を返す場合でも、特定のプロパティまたはプロパティ値型に適用される、その文字列に対する型変換動作は呼び出されません。一般に、マークアップ拡張機能の目的は、文字列を使用して、型コンバーターを含まないオブジェクトを返します。  
  
 型コンバーターではなく、マークアップ拡張機能が必要となる一般的な状況の1つは、既に存在するオブジェクトへの参照を作成することです。 最良の場合、ステートレスな型コンバーターは新しいインスタンスを生成するだけで、望ましくない可能性があります。 マークアップ拡張機能の詳細については、「[マークアップ拡張機能」および「WPF XAML](markup-extensions-and-wpf-xaml.md)」を参照してください。  
  
### <a name="native-type-converters"></a>ネイティブな型コンバーター  
 XAML パーサーの WPF および .NET Framework 実装では、ネイティブ型の変換処理を持つ特定の型がありますが、プリミティブとして考えられる型ではありません。 このような型の例として、 <xref:System.DateTime>が挙げられます。 この理由は、.NET Framework アーキテクチャの動作に基づいています。この<xref:System.DateTime>型は、.net の最も基本的なライブラリである mscorlib で定義されています。 <xref:System.DateTime>は、依存関係を導入する (<xref:System.ComponentModel.TypeConverterAttribute>システムからの) 別のアセンブリからの属性で属性を設定することは許可されていないため、属性による通常の型コンバーターの検出メカニズムはサポートできません。 代わりに、XAML パーサーには、このようなネイティブ処理を必要とする型のリストがあり、これらは真のプリミティブの処理方法と同様に処理されます。 ( <xref:System.DateTime>この場合は、を<xref:System.DateTime.Parse%2A>呼び出す必要があります)。  
  
<a name="Implementing_a_Type_Converter"></a>   
## <a name="implementing-a-type-converter"></a>型コンバーターの実装  
  
### <a name="typeconverter"></a>TypeConverter  
 前に<xref:System.Windows.PointConverter>示した例では、クラスについて説明しました。 <xref:System.Windows.Point> XAML の .NET 実装では、XAML の目的で使用されるすべての型コンバーターは、基底クラス<xref:System.ComponentModel.TypeConverter>から派生するクラスです。 この<xref:System.ComponentModel.TypeConverter>クラスは、XAML の存在前に .NET Framework のバージョンに存在しています。元の使用方法の1つは、ビジュアルデザイナーのプロパティダイアログに文字列変換を提供することでした。 XAML の場合、の<xref:System.ComponentModel.TypeConverter>ロールは、文字列属性値の解析を有効にし、場合によっては特定のオブジェクトプロパティの実行時の値を文字列に変換するために、次のような文字列変換の基底クラスとなるように展開されます。属性としてのシリアル化。  
  
 <xref:System.ComponentModel.TypeConverter>XAML 処理のために文字列との間の変換に関連する4つのメンバーを定義します。  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>  
  
 これらのうち、最も重要なメソッド<xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>はです。 このメソッドは、入力文字列を必要なオブジェクト型に変換します。 厳密に言え<xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>ば、メソッドを実装して、より広範な型をコンバーターの目的の型に変換することができます。これにより、実行時の変換をサポートするような xaml を超えて、xaml の目的での処理が可能になります。これは、重要な入力を<xref:System.String>処理できるコードパスにすぎません。  
  
 次に重要なメソッドは<xref:System.ComponentModel.TypeConverter.ConvertTo%2A>です。 アプリケーションがマークアップ表現に変換された場合 (たとえば、ファイルとして XAML に保存されて<xref:System.ComponentModel.TypeConverter.ConvertTo%2A>いる場合)、はマークアップ表現を生成します。 この場合、XAML にとって重要なコードパスは、の`destinationType` <xref:System.String>を渡したときです。  
  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> と <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> は、サービスが <xref:System.ComponentModel.TypeConverter> の実装の機能を照会する時に使用されるサポート メソッドです。 これらのメソッドは、その型について、相当する変換メソッドをコンバーターがサポートしている場合に `true` を返すように実装する必要があります。 XAML の目的では、通常、 <xref:System.String> 型であることを意味します。  
  
### <a name="culture-information-and-type-converters-for-xaml"></a>カルチャ情報と XAML の型コンバーター  
 各<xref:System.ComponentModel.TypeConverter>実装は、変換の有効な文字列を構成するものを独自に解釈できます。また、パラメーターとして渡される型の説明を使用したり無視したりすることもできます。 カルチャと XAML の型変換に関しては、重要な考慮事項があります。 属性値としてローカライズ可能な文字列を使用することは、XAML で完全にサポートされています。 ただし、このローカライズ可能な文字列を特定のカルチャ要件で型コンバーター入力として使用することはサポートされていません。これは、 `en-US` XAML 属性値の型コンバーターには、カルチャを使用した、必ずしも固定言語の解析動作が含まれるためです。 この制限の設計上の理由の詳細については、「xaml 言語仕様 ([\[MS xaml\]](https://go.microsoft.com/fwlink/?LinkId=114525))」を参照してください。  
  
 カルチャが問題になる可能性のある例として、一部のカルチャでは、数値の小数点の区切り記号としてコンマを使用しています。 これは、WPF XAML 型コンバーターの多くが持つ動作と競合します。これは、コンマを区切り記号として使用します。これは、共通の X、Y 形式、またはコンマ区切りの一覧などの履歴の参照元に基づいています。 周囲の XAML でカルチャを渡すこともでき`Language`ます`xml:lang` (また`sl-SI`はカルチャに設定またはカルチャを設定しますが、このように decimal にコンマを使用するカルチャの例)、問題は解決されません。  
  
### <a name="implementing-convertfrom"></a>ConvertFrom の実装  
 XAML をサポートする <xref:System.ComponentModel.TypeConverter> の実装としてコンバーターを使用できるようにするためには、そのコンバーターの <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> メソッドが `value` パラメーターとして文字列を受け入れる必要があります。 文字列が有効な形式であり、 <xref:System.ComponentModel.TypeConverter>実装で変換できる場合、返されるオブジェクトは、プロパティで想定される型へのキャストをサポートする必要があります。 それ以外の場合、 <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> 実装は `null`を返す必要があります。  
  
 各<xref:System.ComponentModel.TypeConverter>実装では、変換のために有効な文字列を構成する内容を独自に解釈できます。また、パラメーターとして渡される型の説明またはカルチャコンテキストを使用したり無視したりすることもできます。 ただし、WPF XAML 処理では、常に型の説明のコンテキストに値を渡さないことがあります。また、 `xml:lang`に基づくカルチャを渡すこともできません。  
  
> [!NOTE]
> 中かっこ文字 (特に {) は、文字列形式の可能な要素として使用しないでください。 これらの文字は、マークアップ拡張シーケンスの開始および終了を示す文字として予約されています。  
  
### <a name="implementing-convertto"></a>ConvertTo の実装  
 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> は、シリアル化のサポートで使用される可能性があります。 カスタム型およびその型コンバーターに対して <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> によるシリアル化をサポートすることは、絶対要件ではありません。 ただし、コントロールを実装する場合、またはクラスの機能または設計の一部としてシリアル化を使用する場合は、 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>を実装する必要があります。  
  
 XAML <xref:System.ComponentModel.TypeConverter> をサポートするの`value`実装として使用できるようにするには、そのコンバーターのメソッドが、パラメーターとしてサポートされている型(または値)のインスタンスを受け入れる必要があります。<xref:System.ComponentModel.TypeConverter.ConvertTo%2A> パラメーターが型<xref:System.String>の場合、返されるオブジェクトはとして<xref:System.String>キャストできる必要があります。 `destinationType` 返される文字列は、 `value`のシリアル化された値を表している必要があります。 理想的には、選択したシリアル化形式で、同じコンバーターの<xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>実装にその文字列が渡された場合、情報が大幅に失われることなく、同じ値を生成できるようにする必要があります。  
  
 値をシリアル化できない場合、またはコンバーターがシリアル化をサポート<xref:System.ComponentModel.TypeConverter.ConvertTo%2A>してい`null`ない場合、実装はを返す必要があり、この場合は例外をスローすることが許可されます。 ただし、例外をスローする場合は、 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>実装の一部としてその変換を使用できないことを報告して、例外を回避するために<xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>最初にチェックすることをお勧めします。  
  
 パラメーター `destinationType`が型<xref:System.String>でない場合は、独自のコンバーター処理を選択できます。 通常は、基本実装の処理に戻します。これにより、 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> basemost では、特定の例外が最も発生します。  
  
### <a name="implementing-canconvertto"></a>CanConvertTo の実装  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> の実装は、 `true` が `destinationType` 型の場合は <xref:System.String>を返し、それ以外の場合は基底の実装に任せる必要があります。  
  
### <a name="implementing-canconvertfrom"></a>CanConvertFrom の実装  
 <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> の実装は、 `true` が `sourceType` 型の場合は <xref:System.String>を返し、それ以外の場合は基底の実装に任せる必要があります。  
  
<a name="Applying_the_TypeConverterAttribute"></a>   
## <a name="applying-the-typeconverterattribute"></a>TypeConverterAttribute の適用  
 カスタム型コンバーターを XAML プロセッサによってカスタムクラスの動作する型コンバーターとして使用するには、をクラス定義<xref:System.ComponentModel.TypeConverterAttribute>に適用する必要があります。 属性を通して指定する <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A> は、カスタム型コンバーターの型名である必要があります。 この属性を適用すると、プロパティ型がカスタムクラス型を使用する値を XAML プロセッサが処理するときに、入力文字列を入力して、オブジェクトインスタンスを返すことができます。  
  
 また、プロパティごとに型コンバーターを提供することもできます。 を<xref:System.ComponentModel.TypeConverterAttribute>クラス定義に適用する代わりに、プロパティ定義 (メイン定義内の`set`実装では`get` /なく、メイン定義) に適用します。 プロパティの型は、カスタム型コンバーターによって処理される型と一致する必要があります。 この属性を適用すると、プロパティの値を XAML プロセッサが処理する際に、入力文字列を処理して、オブジェクトのインスタンスを返すことができます。 プロパティごとの型コンバーターの手法は、Microsoft .NET Framework またはその他のライブラリからプロパティの型を使用する場合に特に便利です。クラス定義を制御すること<xref:System.ComponentModel.TypeConverterAttribute>はできず、その中にを適用することもできません。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ComponentModel.TypeConverter>
- [XAML の概要 (WPF)](xaml-overview-wpf.md)
- [マークアップ拡張機能と WPF XAML](markup-extensions-and-wpf-xaml.md)
- [XAML 構文の詳細](xaml-syntax-in-detail.md)
