---
title: .Net を使用してC# JSON をシリアル化および逆シリアル化する方法
author: tdykstra
ms.author: tdykstra
ms.date: 09/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 3c988a0151f57b67db19f41aeb88c6fb9b808cb3
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/09/2019
ms.locfileid: "72179199"
---
# <a name="how-to-serialize-and-deserialize-json-in-net"></a>.NET で JSON をシリアル化および逆シリアル化する方法

> [!IMPORTANT]
> JSON シリアル化のドキュメントは構築中です。 この記事では、すべてのシナリオについては説明しません。 詳細については、GitHub の dotnet/corefx リポジトリにある system.string に[関する問題](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json)を調べてください。特に、「 [json 機能-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc)」というラベルが付いています。

この記事では、<xref:System.Text.Json> 名前空間を使用して、JavaScript Object Notation (JSON) との間でシリアル化および逆シリアル化を行う方法について説明します。 指示とサンプルコードは、ライブラリを直接使用します。 [ASP.NET Core](/aspnet/core/)などのフレームワークでは使用されません。

## <a name="namespaces"></a>名前空間

@No__t-0 名前空間には、すべてのエントリポイントと主な型が含まれています。 @No__t-0 名前空間には、シリアル化と逆シリアル化に固有の高度なシナリオとカスタマイズのための属性と Api が含まれています。 したがって、この記事に示されているコード例では、次のいずれかまたは両方の `using` ディレクティブが必要です。

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

@No__t-0 名前空間の属性は、`System.Text.Json` では現在サポートされていません。

## <a name="how-to-write-net-objects-to-json-serialize"></a>.NET オブジェクトを JSON に書き込む方法 (シリアル化)

JSON を文字列に書き込むには、<xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> メソッドを呼び出します。 次の例では、ジェネリック型パラメーターと共にオーバーロードを使用しています。

```csharp
WeatherForecast weatherForecast;
//...
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

ジェネリック型パラメーターを省略し、代わりにジェネリック型の推定を使用することができます。

```csharp
WeatherForecast weatherForecast;
//...
string json = JsonSerializer.Serialize(weatherForecast);
```

シリアル化される型の例を次に示します。これには、コレクションと入れ子になったクラスが含まれます。

```csharp
public class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    public IList<DateTimeOffset> DatesAvailable { get; set;}
    public Dictionary<string, HighLowTemperatures> TemperatureRanges { get; set; }
    public string [] SummaryWords { get; set; }
}

public class HighLowTemperatures
{
    public Temperature High { get; set; }
    public Temperature Low { get; set; }
}

public class Temperature
{
    public int DegreesCelsius { get; set; }
}
```

既定では、JSON 出力が縮小されます。 

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureC":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":{"DegreesCelsius":20},"Low":{"DegreesCelsius":-10}},"Hot":{"High":{"DegreesCelsius":60},"Low":{"DegreesCelsius":20}}},"SummaryWords":["Cool","Windy","Humid"]}
```

次の例では、同じ JSON が書式設定されています (空白とインデントで整形されています)。

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "TemperatureRanges": {
    "Cold": {
      "High": {
        "DegreesCelsius": 20
      },
      "Low": {
        "DegreesCelsius": -10
      }
    },
    "Hot": {
      "High": {
        "DegreesCelsius": 60
      },
      "Low": {
        "DegreesCelsius": 20
      }
    }
  },
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

@No__t-0 のオーバーロードを使用すると、<xref:System.IO.Stream> にシリアル化できます。 @No__t-0 のオーバーロードの非同期バージョンを使用できます。

### <a name="serialize-to-utf-8"></a>UTF-8 にシリアル化する

UTF-8 にシリアル化するには、<xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> メソッドを呼び出します。

```csharp
byte[] utf8Json = JsonSerializer.SerializeToUtf8Bytes<WeatherForecast>(weatherForecast);
```

別の方法として、<xref:System.Text.Json.Utf8JsonWriter> を受け取る @no__t 0 のオーバーロードを使用することもできます。

UTF-8 へのシリアル化は、文字列ベースのメソッドを使用するよりも約 5-10% 高速です。 違いは、バイト (UTF-8) を文字列 (UTF-16) に変換する必要がないためです。

## <a name="serialization-behavior"></a>シリアル化の動作

* 既定では、すべてのパブリックプロパティがシリアル化されます。 [除外するプロパティを指定](#exclude-properties)できます。
* [既定のエンコーダー](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default)は、非 ascii 文字、ascii 範囲内の HTML を区別する文字、および[JSON 仕様](https://tools.ietf.org/html/rfc8259#section-7)に従ってエスケープする必要がある文字をエスケープします。
* 既定では、JSON は縮小されています。 [JSON はかなり印刷](#serialize-to-formatted-json)できます。
* 既定では、JSON 名の大文字と小文字の区別は .NET 名と一致します。 [JSON 名の大文字と小文字](#customize-json-names)の区別をカスタマイズできます。
* 循環参照が検出され、例外がスローされました。 詳細については、GitHub の dotnet/corefx リポジトリにある[循環参照に関する問題](https://github.com/dotnet/corefx/issues/38579)を参照してください。
* 現在、フィールドは除外されています。

サポートされている種類は次のとおりです。

* 数値型、文字列、ブール値など、JavaScript プリミティブにマップされる .NET プリミティブ。
* ユーザー定義の[Plain OLD CLR オブジェクト (POCOs)](https://stackoverflow.com/questions/250001/poco-definition)。
* 1次元配列とジャグ配列 (`ArrayName[][]`)。
* `Dictionary<string,TValue>` `TValue` は `object`、`JsonElement`、または POCO です。
* 次の名前空間のコレクション。 詳細については、GitHub の dotnet/corefx リポジトリの[コレクションサポートに関する問題](https://github.com/dotnet/corefx/issues/36643)を参照してください。
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

## <a name="how-to-read-json-into-net-objects-deserialize"></a>JSON を .NET オブジェクトに読み込む方法 (逆シリアル化)

文字列から逆シリアル化するには、次の例に示すように、<xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> メソッドを呼び出します。

```csharp
string json = ... ;

var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json);
```

例については、「 [serialize](#how-to-write-net-objects-to-json-serialize) 」セクションを参照してください。 JSON オブジェクトと .NET オブジェクトは同じですが、方向が逆になっています。

@No__t-0 のオーバーロードを使用すると、`Stream` から逆シリアル化できます。  @No__t-0 のオーバーロードの非同期バージョンを使用できます。

### <a name="deserialize-from-utf-8"></a>UTF-8 からの逆シリアル化

UTF-8 から逆シリアル化するには、次の例に示すように、`Utf8JsonReader` または `ReadOnlySpan<byte>` を受け取る @no__t 0 のオーバーロードを呼び出します。

```csharp
byte[] utf8Json;
//...
var readOnlySpan = new ReadOnlySpan<byte>(utf8Json);
weatherForecast = JsonSerializer.Deserialize<WeatherForecastMin>(readOnlySpan);
```

```csharp
byte[] utf8Json;
//...
var utf8Reader = new Utf8JsonReader(utf8Json);
weatherForecast = JsonSerializer.Deserialize<WeatherForecastMin>(ref utf8Reader);
```

## <a name="deserialization-behavior"></a>逆シリアル化の動作

* 既定では、プロパティ名の照合では大文字と小文字が区別されます。 [大文字と小文字を区別](#case-insensitive-property-matching)しないように指定できます。
* JSON に読み取り専用プロパティの値が含まれている場合、この値は無視され、例外はスローされません。
* パラメーターなしのコンストラクターを使用しない参照型への逆シリアル化はサポートされていません。
* 変更できないオブジェクトまたは読み取り専用プロパティへの逆シリアル化はサポートされていません。 詳細については、変更できない[オブジェクトのサポートに関する](https://github.com/dotnet/corefx/issues/38569)github の問題と、github の dotnet/corefx リポジトリの[読み取り専用プロパティのサポート](https://github.com/dotnet/corefx/issues/38163)に関する問題を参照してください。
* 既定では、列挙型は数値としてサポートされています。
* フィールドはサポートされていません。
* 既定では、JSON のコメントまたは末尾のコンマによって例外がスローされます。 必要に応じ[て、コメントと末尾のコンマを許可](#allow-comments-and-trailing-commas)できます。
* [既定の最大の深さ](xref:System.Text.Json.JsonReaderOptions.MaxDepth)は64です。

## <a name="serialize-to-formatted-json"></a>書式設定された JSON にシリアル化する

JSON 出力を整形するには、<xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> を `true` に設定します。

```csharp
var options = new JsonSerializerOptions
{
    WriteIndented = true,
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

シリアル化される型と JSON 出力の例を次に示します。

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

## <a name="allow-comments-and-trailing-commas"></a>コメントと末尾のコンマを許可する

JSON では、既定でコメントと末尾のコンマは使用できません。 JSON でコメントを許可するには、<xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> プロパティを `JsonCommentHandling.Skip` に設定します。 また、末尾のコンマを許可するには、<xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> プロパティを `true` に設定します。 次の例では、両方を許可する方法を示します。

```csharp
var options = new JsonSerializerOptions
{
    ReadCommentHandling = JsonCommentHandling.Skip,
    AllowTrailingCommas = true
};
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json);
```

次に、コメントと末尾のコンマを含む JSON の例を示します。

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="customize-json-names"></a>JSON 名のカスタマイズ

既定では、プロパティ名とディクショナリキーは、大文字と小文字を含め、JSON の出力では変更されません。 このセクションでは、次の方法について説明します。

* 個々のプロパティ名をカスタマイズする
* すべてのプロパティ名を camel 形式に変換します
* カスタムプロパティの名前付けポリシーを実装する
* ディクショナリキーを camel 形式に変換する

現在、列挙型からキャメルケースへの自動変換はサポートされていません。 詳細については、GitHub の dotnet/corefx リポジトリでの[列挙型 camel ケースのサポートに関する問題](https://github.com/dotnet/corefx/issues/37725)を参照してください。

### <a name="customize-individual-property-names"></a>個々のプロパティ名をカスタマイズする

個々のプロパティの名前を設定するには、 [[Jsonpropertyname]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute)属性を使用します。

シリアル化し、結果として得られる JSON の例を次に示します。

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    [JsonPropertyName("Wind")]
    public int WindSpeed { get; set; }
}
```

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

この属性によって設定されるプロパティ名:

* シリアル化と逆シリアル化の両方の方向で適用されます。
* は、プロパティの名前付けポリシーよりも優先されます。

### <a name="use-camel-case-for-all-json-property-names"></a>すべての JSON プロパティ名にキャメルケースを使用する

すべての JSON プロパティ名にキャメルケースを使用するには、次の例に示すように、<xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> を `JsonNamingPolicy.CamelCase` に設定します。

```csharp
var options = new JsonSerializerOptions
{
    PropertyNamingPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

シリアル化と JSON 出力の例を次に示します。

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    [JsonPropertyName("Wind")]
    public int WindSpeed { get; set; }
}
```

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureC": 25,
  "summary": "Hot",
  "Wind": 35
}
```

Camel 形式のプロパティの名前付けポリシー:

* シリアル化および逆シリアル化に適用されます。
* は `[JsonPropertyName]` 属性によってオーバーライドされます。

### <a name="use-a-custom-json-property-naming-policy"></a>カスタム JSON プロパティの名前付けポリシーを使用する

カスタム JSON プロパティの名前付けポリシーを使用するには、次の例に示すように、<xref:System.Text.Json.JsonNamingPolicy> から派生し、<xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> メソッドをオーバーライドするクラスを作成します。

```csharp
class UpperCaseNamingPolicy : JsonNamingPolicy
{
    public override string ConvertName(string name)
    {
        return name.ToUpper();
    }
}
```

次に、<xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> プロパティを名前付けポリシークラスのインスタンスに設定します。

```csharp
var options = new JsonSerializerOptions
{
    PropertyNamingPolicy = new UpperCaseNamingPolicy()
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

シリアル化と JSON 出力の例を次に示します。

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    [JsonPropertyName("Wind")]
    public int WindSpeed { get; set; }
}
```

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATUREC": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

JSON プロパティの名前付けポリシー:

* シリアル化および逆シリアル化に適用されます。
* は `[JsonPropertyName]` 属性によってオーバーライドされます。

### <a name="camel-case-dictionary-keys"></a>Camel ケースディクショナリキー

シリアル化するオブジェクトのプロパティの型が `Dictionary<string,TValue>` の場合、`string` キーを camel 形式に変換できます。 これを行うには、次の例に示すように、<xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> を `JsonNamingPolicy.CamelCase` に設定します。

```csharp
var options = new JsonSerializerOptions
{
    DictionaryKeyPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

シリアル化し、JSON 出力を行うオブジェクトの例を次に示します。

|プロパティ |値  |
|---------|---------|
| date    | 8/1/2019 12:00:00 AM-07:00|
| TemperatureC| 25 |
| まとめ| 熱い|
| TemperatureRanges | コールド、20<br>ホット、40|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "cold": 20,
    "hot": 40
  }
}
```

Camel 形式の名前付けポリシーは、シリアル化にのみ適用されます。

## <a name="exclude-properties"></a>プロパティを除外する

既定では、すべてのパブリックプロパティがシリアル化されます。 一部のオプションが JSON 出力に表示されないようにするには、いくつかのオプションがあります。 ここでは、を除外する方法について説明します。

* 個々のプロパティ
* すべての読み取り専用プロパティ
* すべての null 値プロパティ 

### <a name="exclude-individual-properties"></a>個々のプロパティを除外する

個々のプロパティを無視するには、 [[Jsonignore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute)属性を使用します。

シリアル化する型と JSON 出力の例を次に示します。

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    [JsonIgnore]
    public int WindSpeed { get; set; }
}
```

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

### <a name="exclude-all-read-only-properties"></a>すべての読み取り専用プロパティを除外する

すべての読み取り専用プロパティを除外するには、次の例に示すように、<xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> を `true` に設定します。

```csharp
var options = new JsonSerializerOptions
{
    IgnoreReadOnlyProperties = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

シリアル化する型と JSON 出力の例を次に示します。

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    public int WindSpeed { get; private set; }
}
```

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
}
```

このオプションは、シリアル化にのみ適用されます。 逆シリアル化中、読み取り専用プロパティは既定では無視されます。 パブリックゲッターが含まれていてもパブリック setter がない場合、プロパティは読み取り専用です。

### <a name="exclude-all-null-value-properties"></a>すべての null 値プロパティを除外する

すべての null 値プロパティを除外するには、次の例に示すように、<xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> プロパティを `true` に設定します。

```csharp
var options = new JsonSerializerOptions
{
    IgnoreNullValues = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

シリアル化し、JSON 出力を行うオブジェクトの例を次に示します。

|プロパティ |値  |
|---------|---------|
| date    | 8/1/2019 12:00:00 AM-07:00|
| TemperatureC| 25 |
| まとめ| null|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25
}
```

この設定は、シリアル化と逆シリアル化に適用されます。 逆シリアル化中、JSON 内の null 値は、有効な場合にのみ無視されます。 Null 非許容値型に対して Null 値を指定すると、例外が発生します。 詳細については、GitHub の dotnet/corefx リポジトリにある[null 非許容の値型に関する問題](https://github.com/dotnet/corefx/issues/40922)を参照してください。

## <a name="case-insensitive-property-matching"></a>大文字と小文字を区別しないプロパティ照合

既定では、逆シリアル化では、JSON とターゲットオブジェクトのプロパティの間で大文字と小文字が区別されるプロパティ名の一致が検索されます。 この動作を変更するには、<xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> を `true` に設定します。

```csharp
var options = new JsonSerializerOptions
{
    PropertyNameCaseInsensitive = true,
};
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(weatherForecast, options);
```

Camel 形式のプロパティ名を持つ JSON の例を次に示します。 Pascal 形式のプロパティ名を持つ次の型に逆シリアル化できます。

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureC": 25,
  "summary": "Hot",
}
```

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

## <a name="include-properties-of-derived-classes"></a>派生クラスのプロパティを含める

コンパイル時にシリアル化する型を指定する場合、ポリモーフィックシリアル化はサポートされません。 たとえば、@no__t 0 クラスと派生クラス `WeatherForecastWithWind` があるとします。

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
class WeatherForecastWithWind : WeatherForecast
{
    public int WindSpeed { get; set; }
}
```

また、コンパイル時にに渡される型またはによって推論される型が、`WeatherForecast` であるとします。 @no__t は、

```csharp
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

```csharp
WeatherForecast weatherForecast;
//...
json = JsonSerializer.Serialize(weatherForecast);
```

このシナリオでは、@no__t 1 のオブジェクトが実際に @no__t 2 のオブジェクトであっても、`WindSpeed` プロパティはシリアル化されません。 基本クラスのプロパティのみがシリアル化されます。

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

この動作は、派生したランタイムによって作成された型でデータが誤って公開されるのを防ぐためのものです。

派生型のプロパティをシリアル化するには、次のいずれかの方法を使用します。

* 実行時に型を指定できるように、<xref:System.Text.Json.JsonSerializer.Serialize%2A> のオーバーロードを呼び出します。

  ```csharp
  json = JsonSerializer.Serialize(weatherForecast, weatherForecast.GetType());
  ```

* @No__t-0 としてシリアル化するオブジェクトを宣言します。

  ```csharp
  json = JsonSerializer.Serialize<object>(weatherForecast);
  ```

前の例のシナリオでは、両方の方法で `WindSpeed` プロパティが JSON 出力に含まれるようになっています。

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "WindSpeed": 35
}
```

## <a name="handle-overflow-json"></a>Overflow JSON の処理

逆シリアル化中に、対象の型のプロパティで表されないデータを JSON で受け取ることがあります。 たとえば、対象の型が次のようになっているとします。

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

逆シリアル化される JSON は次のとおりです。

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "temperatureC": 25,
  "Summary": "Hot",
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

示されている型に示されている JSON を逆シリアル化すると、`DatesAvailable` および `SummaryWords` の各プロパティには何も表示されなくなり、失われます。 これらのプロパティなどの追加データをキャプチャするには、 [Jsonextensiondata](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute)属性を型 `Dictionary<string,object>` または `Dictionary<string,JsonElement>` のプロパティに適用します。

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    [JsonExtensionData]
    public Dictionary<string, object> ExtensionData { get; set; }
}
```

前に示した JSON をこのサンプル型に逆シリアル化すると、余分なデータが `ExtensionData` プロパティのキーと値のペアになります。

|プロパティ |値  |メモ  |
|---------|---------|---------|
| date    | 8/1/2019 12:00:00 AM-07:00||
| TemperatureC| 0 | 大文字と小文字が区別されない (JSON の `temperatureC`) ため、プロパティが設定されていません。 |
| まとめ | 熱い ||
| ExtensionData | temperatureC:25 |大文字と小文字が一致しなかったため、この JSON プロパティは余分で、ディクショナリ内のキーと値のペアになります。|
|| 使用可能な日:<br>  8/1/2019 12:00:00 AM-07:00<br>8/2/2019 12:00:00 AM-07:00 |JSON からの追加のプロパティはキーと値のペアになり、値オブジェクトとして配列が使用されます。|
| |概要語:<br>Cool<br>強風<br>Humid |JSON からの追加のプロパティはキーと値のペアになり、値オブジェクトとして配列が使用されます。|

ターゲットオブジェクトがシリアル化されると、拡張データのキーと値のペアは、受信 JSON の場合と同様に JSON プロパティになります。

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 0,
  "Summary": "Hot",
  "temperatureC": 25,
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

@No__t-0 のプロパティ名が JSON に表示されないことに注意してください。 この動作により、JSON は、逆シリアル化されない余分なデータを失うことなく、ラウンドトリップを行うことができます。

## <a name="use-utf8jsonwriter-directly"></a>Utf8JsonWriter を直接使用する

次の例は、<xref:System.Text.Json.Utf8JsonWriter> クラスを直接使用する方法を示しています。

```csharp
var options = new JsonWriterOptions
{
    Indented = true
};

using (var stream = new MemoryStream())
{
    using (var writer = new Utf8JsonWriter(stream, options))
    {
        writer.WriteStartObject();
        writer.WriteString("date", DateTimeOffset.UtcNow);
        writer.WriteNumber("temp", 42);
        writer.WriteEndObject();
    }

    string json = Encoding.UTF8.GetString(stream.ToArray());
    Console.WriteLine(json);
}
```

## <a name="use-utf8jsonreader-directly"></a>Utf8JsonReader を直接使用する

次の例は、<xref:System.Text.Json.Utf8JsonReader> クラスを直接使用する方法を示しています。 このコードでは、@no__t 0 の変数が、UTF-8 としてエンコードされた有効な JSON を含むバイト配列であることを前提としています。

```csharp
var options = new JsonReaderOptions
{
    AllowTrailingCommas = true,
    CommentHandling = JsonCommentHandling.Skip
};
Utf8JsonReader reader = new Utf8JsonReader(jsonUtf8, options);

while (reader.Read())
{
    Console.Write(reader.TokenType);

    switch (reader.TokenType)
    {
        case JsonTokenType.PropertyName:
        case JsonTokenType.String:
            {
                string text = reader.GetString();
                Console.Write(" ");
                Console.Write(text);
                break;
            }

        case JsonTokenType.Number:
            {
                int value = reader.GetInt32();
                Console.Write(" ");
                Console.Write(value);
                break;
            }

            // Other token types elided for brevity
    }

    Console.WriteLine();
}
```

## <a name="additional-resources"></a>その他の技術情報

* [System.string の概要](system-text-json-overview.md)
* [System.string API リファレンス](xref:System.Text.Json)
* [System.string での DateTime と DateTimeOffset のサポート](../datetime/system-text-json-support.md)
