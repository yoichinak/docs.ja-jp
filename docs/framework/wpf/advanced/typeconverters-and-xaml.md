---
title: TypeConverters および XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], TypeConverter class
ms.assetid: f6313e4d-e89d-497d-ac87-b43511a1ae4b
ms.openlocfilehash: 94cfce44d5702e0550310723ec56184096165436
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187291"
---
# <a name="typeconverters-and-xaml"></a>TypeConverters および XAML
ここでは、文字列からの型変換の目的を XAML 言語の一般的な機能として紹介します。 .NET Framework では、<xref:System.ComponentModel.TypeConverter>クラスは、XAML 属性の使用方法でプロパティ値として使用できるマネージ カスタム クラスの実装の一部として、特定の目的を果たします。 カスタム クラスを記述し、クラスのインスタンスを XAML 設定可能な属性値として使用できるようにする場合は、クラスに a を<xref:System.ComponentModel.TypeConverterAttribute>適用するか、カスタム<xref:System.ComponentModel.TypeConverter>クラスを記述するか、またはその両方を行う必要があります。  

## <a name="type-conversion-concepts"></a>型変換の概念  
  
### <a name="xaml-and-string-values"></a>XAML と文字列値  
 XAML ファイルで属性値を設定すると、その値の初期型は純粋なテキストの文字列になります。 XAML プロセッサに対する<xref:System.Double>最初のテキスト文字列など、他のプリミティブも同様です。  
  
 XAML プロセッサでは、属性値を処理するために 2 つの情報が必要です。 第 1 の情報は、設定しようとしているプロパティの値の型です。 属性値を定義するすべての文字列は、XAML で処理され、最終的にはその型の値に変換 (解決) される必要があります。 値が、XAML パーサーで認識できるプリミティブ (数値など) である場合は、文字列の直接的な変換が試みられます。 値が列挙型の場合、文字列を使用して、その列挙体の名前付き定数と一致する名前を確認します。 値がパーサーが理解できるプリミティブでも列挙型でもない場合、問題の型は、変換された文字列に基づいて型のインスタンスまたは値を提供できる必要があります。 これは、型コンバーター クラスを示すことによって行われます。 型コンバーターは、XAML シナリオと .NET コードのコード呼び出しの両方に対して、別のクラスの値を提供するためのヘルパー クラスです。  
  
### <a name="using-existing-type-conversion-behavior-in-xaml"></a>XAML での既存の型変換動作の使用  
 基になる XAML の概念に精通している場合は、基本アプリケーション XAML で型変換動作を使用している場合もあります。 たとえば、WPF では、type の値を受け取る<xref:System.Windows.Point>プロパティを文字通り何百ものプロパティを定義しています。 A<xref:System.Windows.Point>は 2 次元座標空間で座標を記述する値で、実際には 2 つの重要なプロパティ<xref:System.Windows.Point.X%2A>と<xref:System.Windows.Point.Y%2A>. XAML でポイントを指定する場合は、 と の間<xref:System.Windows.Point.X%2A><xref:System.Windows.Point.Y%2A>に区切り記号 (通常はコンマ) を含む文字列として指定します。 例: `<LinearGradientBrush StartPoint="0,0" EndPoint="1,1"/>`。  
  
 この単純な型の<xref:System.Windows.Point>XAML での単純な使用方法にも、型コンバーターが含まれます。 この場合、それはクラス<xref:System.Windows.PointConverter>です。  
  
 クラス レベルで<xref:System.Windows.Point>定義される型コンバーターを使用すると、を受け取る<xref:System.Windows.Point>すべてのプロパティのマークアップの使用が効率化されます。 ここで型コンバーターを使用しない場合は、前に示した同じ例に対して、次の詳細なマークアップが必要になります。  

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
  
 型変換文字列を使用するか、より詳細な同等の構文を使用するかは、一般的にコーディング スタイルの選択肢です。 XAML ツールワークフローは、値の設定方法にも影響を与える可能性があります。 XAML ツールの中には、デザイナー ビューや独自のシリアル化機構へのラウンド トリップが簡単であるため、マークアップの最も詳細な形式を生成する傾向があります。  
  
 既存の型コンバーターは、通常、WPF 型および .NET Framework 型で、適用<xref:System.ComponentModel.TypeConverterAttribute>されているクラス (またはプロパティ) をチェックすることによって検出できます。 この属性は、XAML の目的と、その他の目的のために、その型の値のサポート型コンバーターであるクラスに名前を付けます。  
  
### <a name="type-converters-and-markup-extensions"></a>型コンバーターとマークアップ拡張機能  
 マークアップ拡張機能と型コンバーターは、XAML プロセッサの動作と適用されるシナリオの観点から直交する役割を満たします。 マークアップ拡張機能の使用時にはコンテキストを利用できますが、マークアップ拡張機能が値を提供するプロパティの型変換動作は一般にマークアップ拡張機能の実装ではチェックされません。 つまり、マークアップ拡張機能が出力としてテキスト文字列を`ProvideValue`返す場合でも、特定のプロパティまたはプロパティ値型に適用される文字列の型変換動作は呼び出されません。  
  
 型コンバーターではなくマークアップ拡張機能が必要な一般的な状況の 1 つは、既に存在するオブジェクトへの参照を作成することです。 ステートレス型コンバーターは、新しいインスタンスしか生成できなかったので、望ましくない場合があります。 マークアップ拡張機能の詳細については、「[マークアップ拡張機能と WPF XAML](markup-extensions-and-wpf-xaml.md)」を参照してください。  
  
### <a name="native-type-converters"></a>ネイティブな型コンバーター  
 XAML パーサーの WPF および .NET Framework の実装では、ネイティブ型変換処理を持つ型がありますが、従来はプリミティブと考えられる型ではありません。 このような型の例として、 <xref:System.DateTime>が挙げられます。 この理由は、.NET Framework アーキテクチャのしくみに基づいています。 <xref:System.DateTime> <xref:System.DateTime>は、依存関係<xref:System.ComponentModel.TypeConverterAttribute>を導入する別のアセンブリ (System からのもの) からの属性を持つ属性を使用することは許可されていないので、属性による通常の型コンバーター検出メカニズムはサポートできません。 代わりに、XAML パーサーには、このようなネイティブ処理を必要とする型のリストがあり、実際のプリミティブの処理方法と同様に処理されます。 (<xref:System.DateTime>この場合、呼び出しが含<xref:System.DateTime.Parse%2A>まれます。  
  
<a name="Implementing_a_Type_Converter"></a>
## <a name="implementing-a-type-converter"></a>型コンバーターの実装  
  
### <a name="typeconverter"></a>TypeConverter  
 前に<xref:System.Windows.Point>示した例では、クラス<xref:System.Windows.PointConverter>が言及されました。 XAML の .NET 実装では、XAML の目的で使用されるすべての型コンバーターは、基本クラス<xref:System.ComponentModel.TypeConverter>から派生するクラスです。 クラス<xref:System.ComponentModel.TypeConverter>は、XAML の存在に先立つ .NET Framework のバージョンに存在します。元の使用方法の 1 つは、ビジュアル デザイナーでプロパティ ダイアログに文字列変換を提供することでした。 XAML のロールは、<xref:System.ComponentModel.TypeConverter>文字列属性値の解析を可能にする文字列変換と文字列変換元の変換の基本クラスであること、および特定のオブジェクト プロパティの実行時の値を属性としてシリアル化する文字列に戻すなどの役割を含むように拡張されます。  
  
 <xref:System.ComponentModel.TypeConverter>XAML 処理のために文字列との変換に関連する 4 つのメンバーを定義します。  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>  
  
- <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>  
  
 このうち、最も重要な方法<xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>は です。 このメソッドは、入力文字列を必要なオブジェクト型に変換します。 厳密に言うと<xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>、このメソッドは、より広い範囲の型をコンバーターの目的の型に変換し、ランタイム変換をサポートするなど XAML 以外にも拡張する目的を果たすように実装できますが、XAML の目的では<xref:System.String>、重要な入力を処理できるコード パスにすぎません。  
  
 次に重要な方法は<xref:System.ComponentModel.TypeConverter.ConvertTo%2A>です。 アプリケーションがマークアップ表現に変換される場合 (たとえば、XAML にファイルとして保存される場合)、<xref:System.ComponentModel.TypeConverter.ConvertTo%2A>マークアップ表現を生成する必要があります。 この場合、XAML にとって重要なコード パスは、 のを`destinationType`渡<xref:System.String>すときです。  
  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> と <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> は、サービスが <xref:System.ComponentModel.TypeConverter> の実装の機能を照会する時に使用されるサポート メソッドです。 これらのメソッドは、その型について、相当する変換メソッドをコンバーターがサポートしている場合に `true` を返すように実装する必要があります。 XAML の目的では、通常、 <xref:System.String> 型であることを意味します。  
  
### <a name="culture-information-and-type-converters-for-xaml"></a>カルチャ情報と XAML の型コンバーター  

 各<xref:System.ComponentModel.TypeConverter>実装は、変換に有効な文字列を構成するものの独自の解釈を持ち、パラメーターとして渡される型の説明を使用または無視することもできます。 カルチャと XAML 型変換に関しては、重要な考慮事項があります。 ローカライズ可能な文字列を属性値として使用することは、XAML で完全にサポートされています。 ただし、XAML 属性値の型コンバーターにはカルチャを使用した必ずしも固定言語解析動作が含まれるため、特定のカルチャ要件を持つ型コンバーター入力としてそのローカライズ`en-US`可能な文字列を使用することはサポートされていません。 この制限の設計上の理由の詳細については、XAML 言語仕様 ([\[MS-XAML\]](https://download.microsoft.com/download/0/A/6/0A6F7755-9AF5-448B-907D-13985ACCF53E/[MS-XAML].pdf).  
  
 カルチャが問題になる例として、カルチャによっては、数値の小数点区切り記号としてコンマを使用する場合があります。 これは、多くの WPF XAML 型コンバーターが持つ動作と競合します( 一般的な X、Y フォーム、コンマ区切りリストなどの履歴判例に基づいて) コンマを区切り文字として使用します。 周辺の XAML でカルチャを渡す`Language`場合`xml:lang`でも`sl-SI`(設定またはカルチャに、この方法で小数点にコンマを使用するカルチャの例)、問題は解決しません。  
  
### <a name="implementing-convertfrom"></a>ConvertFrom の実装  
 XAML をサポートする <xref:System.ComponentModel.TypeConverter> の実装としてコンバーターを使用できるようにするためには、そのコンバーターの <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> メソッドが `value` パラメーターとして文字列を受け入れる必要があります。 文字列が有効な形式で、<xref:System.ComponentModel.TypeConverter>実装によって変換できる場合、返されるオブジェクトは、プロパティで予期される型へのキャストをサポートする必要があります。 それ以外の場合、 <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> 実装は `null`を返す必要があります。  
  
 各<xref:System.ComponentModel.TypeConverter>実装は、変換に有効な文字列を構成するものの独自の解釈を持ち、パラメーターとして渡される型の説明またはカルチャ コンテキストを使用または無視することもできます。 ただし、WPF XAML 処理では、型の説明コンテキストに値を渡さない場合や、 に基づくカルチャを`xml:lang`渡さない場合があります。  
  
> [!NOTE]
> 文字列形式の要素として、中かっこ ({) を使用しないでください。 これらの文字は、マークアップ拡張シーケンスの開始および終了を示す文字として予約されています。  
  
### <a name="implementing-convertto"></a>ConvertTo の実装  
 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> は、シリアル化のサポートで使用される可能性があります。 カスタム型およびその型コンバーターに対して <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> によるシリアル化をサポートすることは、絶対要件ではありません。 ただし、コントロールを実装する場合、またはクラスの機能または設計の一部としてシリアル化を使用する場合は、 <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>を実装する必要があります。  
  
 XAML をサポートする<xref:System.ComponentModel.TypeConverter>実装として使用できるようにするには、そのコンバーター<xref:System.ComponentModel.TypeConverter.ConvertTo%2A>のメソッドがパラメーターとしてサポートされている型 (または値) のインスタンスを`value`受け入れる必要があります。 パラメーターが`destinationType`type<xref:System.String>の場合、返されるオブジェクトは<xref:System.String>としてキャストできる必要があります。 返される文字列は、 `value`のシリアル化された値を表している必要があります。 理想的には、選択したシリアル化形式は、同じコンバーターの<xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>実装に文字列が渡された場合、情報を大幅に失うことなく同じ値を生成できる必要があります。  
  
 値をシリアル化できない場合、またはコンバーターがシリアル化をサポートしていない場合、<xref:System.ComponentModel.TypeConverter.ConvertTo%2A>実装はを`null`返す必要があり、この場合は例外をスローできます。 ただし、例外をスローする場合は、例外を回避するために<xref:System.ComponentModel.TypeConverter.CanConvertTo%2A><xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>最初にチェックするベスト プラクティスがサポートされるように、その変換を実装の一部として使用できないことを報告する必要があります。  
  
 パラメータ`destinationType`が型<xref:System.String>でない場合は、独自のコンバータ処理を選択できます。 通常は、基本の実装処理に戻しますが、その処理は、<xref:System.ComponentModel.TypeConverter.ConvertTo%2A>最も基本的に特定の例外を発生させます。  
  
### <a name="implementing-canconvertto"></a>CanConvertTo の実装  
 <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> の実装は、 `true` が `destinationType` 型の場合は <xref:System.String>を返し、それ以外の場合は基底の実装に任せる必要があります。  
  
### <a name="implementing-canconvertfrom"></a>CanConvertFrom の実装  
 <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> の実装は、 `true` が `sourceType` 型の場合は <xref:System.String>を返し、それ以外の場合は基底の実装に任せる必要があります。  
  
<a name="Applying_the_TypeConverterAttribute"></a>
## <a name="applying-the-typeconverterattribute"></a>TypeConverterAttribute の適用  
 カスタム型コンバーターを XAML プロセッサによってカスタム クラスの代理型コンバーターとして使用するには、 を<xref:System.ComponentModel.TypeConverterAttribute>クラス定義に適用する必要があります。 属性を通して指定する <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A> は、カスタム型コンバーターの型名である必要があります。 この属性を適用すると、プロパティ型がカスタム クラス型を使用する値を XAML プロセッサが処理するときに、文字列を入力してオブジェクト インスタンスを返すことができます。  
  
 また、プロパティごとに型コンバーターを提供することもできます。 を<xref:System.ComponentModel.TypeConverterAttribute>クラス定義に適用するのではなく、プロパティ定義 (その中の`get`/`set`実装ではなく、メイン定義) に適用します。 プロパティの型は、カスタム型コンバーターによって処理される型と一致する必要があります。 この属性を適用すると、プロパティの値を XAML プロセッサが処理する際に、入力文字列を処理して、オブジェクトのインスタンスを返すことができます。 プロパティごとの型コンバーターの手法は、Microsoft .NET Framework またはクラス定義を制御できず、そのライブラリからプロパティ型を使用する場合に特に便利です<xref:System.ComponentModel.TypeConverterAttribute>。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ComponentModel.TypeConverter>
- [XAML の概要 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [マークアップ拡張機能と WPF XAML](markup-extensions-and-wpf-xaml.md)
- [XAML 構文の詳細](xaml-syntax-in-detail.md)
