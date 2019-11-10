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
ms.openlocfilehash: f0245feb710f33d5fcea2a7125b8753ba6064018
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740435"
---
# <a name="how-to-serialize-and-deserialize-json-in-net"></a>.NET で JSON をシリアル化および逆シリアル化する方法

> [!IMPORTANT]
> JSON シリアル化のドキュメントは構築中です。 この記事では、すべてのシナリオについては説明しません。 詳細については、GitHub の dotnet/corefx リポジトリにある system.string に[関する問題](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json)を調べてください。特に、「 [json 機能-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc)」というラベルが付いています。

この記事では、<xref:System.Text.Json> 名前空間を使用して、JavaScript Object Notation (JSON) との間でシリアル化および逆シリアル化を行う方法について説明します。 指示とサンプルコードは、ライブラリを直接使用します。 [ASP.NET Core](/aspnet/core/)などのフレームワークでは使用されません。

## <a name="namespaces"></a>名前空間

<xref:System.Text.Json> 名前空間には、すべてのエントリポイントと主要な型が含まれます。 <xref:System.Text.Json.Serialization> 名前空間には、シリアル化と逆シリアル化に固有の高度なシナリオとカスタマイズのための属性と Api が含まれています。 この記事に示されているコード例では、次のいずれかまたは両方の名前空間に `using` ディレクティブが必要です。

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<xref:System.Runtime.Serialization> 名前空間の属性は、現在 `System.Text.Json`ではサポートされていません。

## <a name="how-to-write-net-objects-to-json-serialize"></a>.NET オブジェクトを JSON に書き込む方法 (シリアル化)

JSON を文字列またはファイルに書き込むには、<xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> メソッドを呼び出します。

次の例では、JSON を文字列として作成します。

```csharp
string json = JsonSerializer.Serialize(weatherForecast);
```

次の例では、同期コードを使用して JSON ファイルを作成します。

```csharp
File.WriteAllText(outputFileName, JsonSerializer.Serialize(weatherForecast));
```

次の例では、非同期コードを使用して JSON ファイルを作成します。

```csharp
using (FileStream fs = File.Create(outputFileName))
{
    await JsonSerializer.SerializeAsync(fs, weatherForecast);
}
```

前の例では、シリアル化する型の型の推定を使用します。 `Serialize()` のオーバーロードは、ジェネリック型パラメーターを受け取ります。

```csharp
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

### <a name="serialization-example"></a>シリアル化の例

コレクションと入れ子になったクラスを含む型の例を次に示します。

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

前の型のインスタンスをシリアル化した JSON 出力は、次の例のようになります。 既定では、JSON 出力が縮小されます。 

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

### <a name="serialize-to-utf-8"></a>UTF-8 にシリアル化する

UTF-8 にシリアル化するには、<xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> メソッドを呼び出します。

```csharp
byte[] jsonUtf8Bytes = JsonSerializer.SerializeToUtf8Bytes<WeatherForecast>(weatherForecast);
```

<xref:System.Text.Json.Utf8JsonWriter> を受け取る <xref:System.Text.Json.JsonSerializer.Serialize%2A> のオーバーロードも使用できます。

UTF-8 へのシリアル化は、文字列ベースのメソッドを使用するよりも約5-10% 高速です。 違いは、バイト (UTF-8) を文字列 (UTF-16) に変換する必要がないためです。

## <a name="serialization-behavior"></a>シリアル化の動作

* 既定では、すべてのパブリックプロパティがシリアル化されます。 [除外するプロパティを指定](#exclude-properties-from-serialization)できます。
* [既定のエンコーダー](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default)は、非 ascii 文字、ascii 範囲内の HTML を区別する文字、および[JSON 仕様](https://tools.ietf.org/html/rfc8259#section-7)に従ってエスケープする必要がある文字をエスケープします。
* 既定では、JSON は縮小されています。 [JSON はかなり印刷](#serialize-to-formatted-json)できます。
* 既定では、JSON 名の大文字と小文字の区別は .NET 名と一致します。 [JSON 名の大文字と小文字](#customize-json-names-and-values)の区別をカスタマイズできます。
* 循環参照が検出され、例外がスローされました。 詳細については、GitHub の dotnet/corefx リポジトリにある[循環参照に関する問題](https://github.com/dotnet/corefx/issues/38579)を参照してください。
* 現在、フィールドは除外されています。

サポートされている種類は次のとおりです。

* 数値型、文字列、ブール値など、JavaScript プリミティブにマップされる .NET プリミティブ。
* ユーザー定義の[Plain OLD CLR オブジェクト (POCOs)](https://stackoverflow.com/questions/250001/poco-definition)。
* 1次元配列とジャグ配列 (`ArrayName[][]`)。
* `Dictionary<string,TValue>` `TValue` が `object`、`JsonElement`、または POCO です。
* 次の名前空間のコレクション。 詳細については、GitHub の dotnet/corefx リポジトリの[コレクションサポートに関する問題](https://github.com/dotnet/corefx/issues/36643)を参照してください。
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

[カスタムコンバーターを実装](system-text-json-converters-how-to.md)して、追加の型を処理したり、組み込みのコンバーターでサポートされていない機能を提供したりすることができます。

## <a name="how-to-read-json-into-net-objects-deserialize"></a>JSON を .NET オブジェクトに読み込む方法 (逆シリアル化)

文字列またはファイルから逆シリアル化するには、<xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> メソッドを呼び出します。

次の例では、文字列から JSON を読み取ります。

```csharp
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(jsonString);
```

同期コードを使用してファイルから逆シリアル化するには、次の例に示すように、ファイルを文字列に読み取ります。

```csharp
string jsonString = File.ReadAllText(inputFileName);
weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(jsonString);
```

非同期コードを使用してファイルから逆シリアル化するには、<xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> メソッドを呼び出します。

```csharp
using (FileStream fs = File.OpenRead(inputFileName))
{
    weatherForecast = await JsonSerializer.DeserializeAsync<WeatherForecast>(fs);
}
```

型とそれに対応する JSON の例については、「[シリアル化の例](#serialization-example)」を参照してください。

### <a name="deserialize-from-utf-8"></a>UTF-8 からの逆シリアル化

UTF-8 から逆シリアル化するには、次の例に示すように、`Utf8JsonReader` または `ReadOnlySpan<byte>`を受け取る <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> オーバーロードを呼び出します。 この例では、JSON が jsonUtf8Bytes という名前のバイト配列にあることを前提としています。

```csharp
var readOnlySpan = new ReadOnlySpan<byte>(jsonUtf8Bytes);
weatherForecast = JsonSerializer.Deserialize<WeatherForecastMin>(readOnlySpan);
```

```csharp
var utf8Reader = new Utf8JsonReader(jsonUtf8Bytes);
weatherForecast = JsonSerializer.Deserialize<WeatherForecastMin>(ref utf8Reader);
```

## <a name="deserialization-behavior"></a>逆シリアル化の動作

* 既定では、プロパティ名の照合では大文字と小文字が区別されます。 [大文字と小文字を区別](#case-insensitive-property-matching)しないように指定できます。
* JSON に読み取り専用プロパティの値が含まれている場合、この値は無視され、例外はスローされません。
* パラメーターなしのコンストラクターを使用しない参照型への逆シリアル化はサポートされていません。
* 変更できないオブジェクトまたは読み取り専用プロパティへの逆シリアル化はサポートされていません。 詳細については、変更できない[オブジェクトのサポートに関する](https://github.com/dotnet/corefx/issues/38569)github の問題と、github の dotnet/corefx リポジトリの[読み取り専用プロパティのサポート](https://github.com/dotnet/corefx/issues/38163)に関する問題を参照してください。
* 既定では、列挙型は数値としてサポートされています。 [列挙型名を文字列としてシリアル化](#enums-as-strings)できます。
* フィールドはサポートされていません。
* 既定では、JSON のコメントまたは末尾のコンマによって例外がスローされます。 [コメントと末尾のコンマを許可](#allow-comments-and-trailing-commas)できます。
* [既定の最大の深さ](xref:System.Text.Json.JsonReaderOptions.MaxDepth)は64です。

組み込みのコンバーターでサポートされていない機能を提供するために、[カスタムコンバーターを実装](system-text-json-converters-how-to.md)することができます。

## <a name="serialize-to-formatted-json"></a>書式設定された JSON にシリアル化する

JSON 出力を整形するには、<xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> を `true`に設定します。

```csharp
var options = new JsonSerializerOptions
{
    WriteIndented = true,
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

シリアル化され、整形された JSON 出力の例を次に示します。

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

## <a name="customize-json-names-and-values"></a>JSON の名前と値をカスタマイズする

既定では、プロパティ名とディクショナリキーは、大文字と小文字を含め、JSON の出力では変更されません。 列挙値は数値として表されます。 このセクションでは、次の方法について説明します。

* 個々のプロパティ名をカスタマイズする
* すべてのプロパティ名を camel 形式に変換します
* カスタムプロパティの名前付けポリシーを実装する
* ディクショナリキーを camel 形式に変換する
* 列挙型を文字列および camel 形式に変換する 

JSON プロパティの名前と値の特別な処理を必要とするその他のシナリオでは、[カスタムコンバーターを実装](system-text-json-converters-how-to.md)できます。

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

すべての JSON プロパティ名にキャメルケースを使用するには、次の例に示すように、<xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> を `JsonNamingPolicy.CamelCase`に設定します。

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
    public int TemperatureCelsius { get; set; }
    public string Summary { get; set; }
    [JsonPropertyName("Wind")]
    public int WindSpeed { get; set; }
}
```

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
  "Wind": 35
}
```

Camel 形式のプロパティの名前付けポリシー:

* シリアル化および逆シリアル化に適用されます。
* は `[JsonPropertyName]` 属性によってオーバーライドされます。 このため、この例の JSON プロパティ名 `Wind` は camel 形式ではありません。

### <a name="use-a-custom-json-property-naming-policy"></a>カスタム JSON プロパティの名前付けポリシーを使用する

カスタム JSON プロパティの名前付けポリシーを使用するには、次の例に示すように、<xref:System.Text.Json.JsonNamingPolicy> から派生するクラスを作成し、<xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> メソッドをオーバーライドします。

```csharp
class UpperCaseNamingPolicy : JsonNamingPolicy
{
    public override string ConvertName(string name)
    {
        return name.ToUpper();
    }
}
```

次に、[<xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType>] プロパティを名前付けポリシークラスのインスタンスに設定します。

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
* は `[JsonPropertyName]` 属性によってオーバーライドされます。 このため、この例の JSON プロパティ名 `Wind` は大文字ではありません。

### <a name="camel-case-dictionary-keys"></a>Camel ケースディクショナリキー

シリアル化するオブジェクトのプロパティが `Dictionary<string,TValue>`型である場合は、`string` キーを camel 形式に変換できます。 これを行うには、次の例に示すように、<xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> を `JsonNamingPolicy.CamelCase`に設定します。

```csharp
var options = new JsonSerializerOptions
{
    DictionaryKeyPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

キーと値の `"ColdMinTemp", 20` ペアを持つ `TemperatureRanges` という名前のディクショナリを使用してオブジェクトをシリアル化すると `"HotMinTemp", 40`、次の例のように JSON 出力が生成されます。

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "coldMinTemp": 20,
    "hotMinTemp": 40
  }
}
```

ディクショナリキーの camel ケースの名前付けポリシーは、シリアル化にのみ適用されます。 ディクショナリを逆シリアル化すると、`DictionaryKeyPolicy`に `JsonNamingPolicy.CamelCase` を指定した場合でも、キーが JSON ファイルと一致します。

### <a name="enums-as-strings"></a>列挙 (文字列として)

既定では、列挙型は数値としてシリアル化されます。 列挙型名を文字列としてシリアル化するには、<xref:System.Text.Json.Serialization.JsonStringEnumConverter>を使用します。

たとえば、列挙型を持つ次のクラスをシリアル化する必要があるとします。

```csharp
class WeatherForecastWithEnum
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public Summary Summary { get; set; }
}

public enum Summary
{
    Cold, Cool, Warm, Hot
}
```

概要が `Hot`の場合、既定では、シリアル化された JSON の数値は3になります。

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": 3
}
```

次のサンプルコードでは、代わりに列挙型名をシリアル化し、camel 形式に変換します。

```csharp
options = new JsonSerializerOptions();
options.Converters.Add(new JsonStringEnumConverter(JsonNamingPolicy.CamelCase));
jsonWithEnumsAsStrings = JsonSerializer.Serialize(weatherForecastWithEnum, options);
```

結果として得られる JSON は、次の例のようになります。

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "hot"
}
```

文字列としての列挙型のサポートは、次の例に示すように、逆シリアル化にも適用されます。

```csharp
options = new JsonSerializerOptions();
options.Converters.Add(new JsonStringEnumConverter(JsonNamingPolicy.CamelCase));
weatherForecastWithEnum = JsonSerializer.Deserialize<WeatherForecastWithEnum>(jsonWithEnumsAsStrings, options);
```

## <a name="exclude-properties-from-serialization"></a>シリアル化からプロパティを除外する

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

パブリックゲッターが含まれていてもパブリック setter がない場合、プロパティは読み取り専用です。 すべての読み取り専用プロパティを除外するには、次の例に示すように、<xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> を `true`に設定します。

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

このオプションは、シリアル化にのみ適用されます。 逆シリアル化中、読み取り専用プロパティは既定では無視されます。

### <a name="exclude-all-null-value-properties"></a>すべての null 値プロパティを除外する

すべての null 値プロパティを除外するには、次の例に示すように、<xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> プロパティを `true`に設定します。

```csharp
var options = new JsonSerializerOptions
{
    IgnoreNullValues = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

シリアル化し、JSON 出力を行うオブジェクトの例を次に示します。

|property |[値]  |
|---------|---------|
| 日付    | 8/1/2019 12:00:00 AM-07:00|
| TemperatureC| 25 |
| まとめ| null|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25
}
```

この設定は、シリアル化と逆シリアル化に適用されます。 逆シリアル化に対する影響については、「[逆シリアル化するときに null を無視する](#ignore-null-when-deserializing)」を参照してください。

## <a name="customize-character-encoding"></a>文字エンコードのカスタマイズ

既定では、シリアライザーは ASCII 以外のすべての文字をエスケープします。  つまり、`xxxxx` が文字の Unicode コードである `\uxxxx` に置き換えます。  たとえば、`Summary` プロパティがキリルжаркоに設定されている場合、次の例に示すように `WeatherForecast` オブジェクトがシリアル化されます。

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a>言語文字セットのシリアル化

1つ以上の言語の文字セットをシリアル化するには、次の例に示すように、<xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>のインスタンスを作成するときに[Unicode 範囲](xref:System.Text.Unicode.UnicodeRanges)を指定します。

```csharp
using System.Text.Encodings.Web;
using System.Text.Json;
using System.Text.Unicode;
```

```csharp
var options = new JsonSerializerOptions
{
    Encoder = JavaScriptEncoder.Create(UnicodeRanges.Cyrillic, UnicodeRanges.GreekExtended)
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

このコードは、キリル文字とギリシャ文字をシリアル化します。 キリル文字は、次の例のようになります。

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "жарко",
}
```

すべての言語を指定するには、<xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>を使用します。

### <a name="serialize-specific-characters"></a>特定の文字のシリアル化

別の方法として、エスケープせずにを使用して許可する個々の文字を指定する方法もあります。 次の例では、жаркоの最初の2つの文字のみをシリアル化します。

```csharp
using System.Text.Encodings.Web;
using System.Text.Json;
using System.Text.Unicode;
```

```csharp
var encoderSettings = new TextEncoderSettings();
encoderSettings.AllowCharacters('\u0436', '\u0430');
options = new JsonSerializerOptions
{
    Encoder = JavaScriptEncoder.Create(encoderSettings)
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

上記のコードによって生成される JSON の例を次に示します。

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a>すべての文字をシリアル化する

エスケープを最小限に抑えるには、次の例に示すように <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>を使用します。

```csharp
using System.Text.Encodings.Web;
using System.Text.Json;
```

```csharp
options = new JsonSerializerOptions
{
    Encoder = JavaScriptEncoder.UnsafeRelaxedJsonEscaping
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

> [!CAUTION]
> 既定のエンコーダーとは異なり、`UnsafeRelaxedJsonEscaping` エンコーダーは次のようになります。
>
> * では、`<`、`>`、`&`、`'`など、HTML に依存する文字はエスケープされません。
> * では、クライアントとサーバーが*文字セット*に対して無効になった場合に発生する可能性のある、XSS または情報漏えい攻撃に対する追加の多層防御は提供されていません。
> * は、エスケープ解除された文字の通過を許可する既定のエンコーダーよりも制限があります。
>
> クライアントが結果のペイロードを UTF-8 でエンコードされた JSON として解釈することがわかっている場合にのみ、unsafe エンコーダーを使用します。 たとえば、サーバーが応答ヘッダー `Content-Type: application/json; charset=utf-8`を送信している場合に使用できます。 未加工の `UnsafeRelaxedJsonEscaping` 出力が HTML ページまたは `<script>` 要素に出力されないようにします。

## <a name="serialize-properties-of-derived-classes"></a>派生クラスのプロパティのシリアル化

コンパイル時にシリアル化する型を指定する場合、ポリモーフィックシリアル化はサポートされません。 たとえば、`WeatherForecast` クラスと派生クラス `WeatherForecastWithWind`があるとします。

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

また、コンパイル時に `Serialize` メソッドの型引数が `WeatherForecast`であるとします。

```csharp
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

このシナリオでは、`weatherForecast` オブジェクトが実際には `WeatherForecastWithWind` オブジェクトであっても、`WindSpeed` プロパティはシリアル化されません。 基本クラスのプロパティのみがシリアル化されます。

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

この動作は、派生したランタイムによって作成された型でデータが誤って公開されるのを防ぐためのものです。

派生型のプロパティをシリアル化するには、次のいずれかの方法を使用します。

* 実行時に型を指定できるようにする <xref:System.Text.Json.JsonSerializer.Serialize%2A> のオーバーロードを呼び出します。

  ```csharp
  json = JsonSerializer.Serialize(weatherForecast, weatherForecast.GetType());
  ```

* `object`としてシリアル化するオブジェクトを宣言します。

  ```csharp
  json = JsonSerializer.Serialize<object>(weatherForecast);
  ```

前の例のシナリオでは、どちらの方法でも、`WindSpeed` プロパティが JSON 出力に含まれるようになっています。

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "WindSpeed": 35
}
```

ポリモーフィックな逆シリアル化については、「[ポリモーフィックな逆シリアル化のサポート](system-text-json-converters-how-to.md#support-polymorphic-deserialization)」を参照してください。

## <a name="allow-comments-and-trailing-commas"></a>コメントと末尾のコンマを許可する

JSON では、コメントと末尾のコンマは既定で許可されていません。 JSON でコメントを許可するには、<xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> プロパティを `JsonCommentHandling.Skip`に設定します。 また、末尾のコンマを許可するには、<xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> プロパティを `true`に設定します。 次の例では、両方を許可する方法を示します。

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

## <a name="case-insensitive-property-matching"></a>大文字と小文字を区別しないプロパティ照合

既定では、逆シリアル化では、JSON とターゲットオブジェクトのプロパティの間で大文字と小文字が区別されるプロパティ名の一致が検索されます。 この動作を変更するには、<xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> を `true`に設定します。

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

示されている型に表示されている JSON を逆シリアル化すると、`DatesAvailable` と `SummaryWords` のプロパティがなくなり、失われます。 これらのプロパティなどの追加データをキャプチャするには、 [Jsonextensiondata](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute)属性を `Dictionary<string,object>` 型または `Dictionary<string,JsonElement>`型のプロパティに適用します。

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

|property |[値]  |ノート  |
|---------|---------|---------|
| 日付    | 8/1/2019 12:00:00 AM-07:00||
| TemperatureC| 0 | 大文字と小文字が区別されない (JSON で`temperatureC`) ため、プロパティが設定されていません。 |
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

JSON には `ExtensionData` プロパティ名が表示されないことに注意してください。 この動作により、JSON は、逆シリアル化されない余分なデータを失うことなく、ラウンドトリップを行うことができます。

## <a name="ignore-null-when-deserializing"></a>逆シリアル化時に null を無視する

既定では、JSON のプロパティが null の場合、対象オブジェクト内の対応するプロパティは null に設定されます。 場合によっては、ターゲットプロパティに既定値が設定されていて、null 値を使用して既定値をオーバーライドしないことがあります。

たとえば、次のコードがターゲットオブジェクトを表しているとします。

```csharp
class WeatherForecastWithDefault
{
    public WeatherForecastWithDefault()
    {
        Summary = "No summary";
    }
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

次の JSON が逆シリアル化されたとします。

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": null,
}
```

逆シリアル化後、`WeatherForecastWithDefault` オブジェクトの `Summary` プロパティは null になります。

この動作を変更するには、次の例に示すように、<xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> を `true`に設定します。

```csharp
var options = new JsonSerializerOptions
{
    IgnoreNullValues = true
};
weatherForecast = JsonSerializer.Deserialize<WeatherForecastWithDefault>(json, options);
```

このオプションを使用すると、逆シリアル化後に、`WeatherForecastWithDefault` オブジェクトの `Summary` プロパティが既定値の "No summary" になります。

JSON 内の Null 値は、有効な場合にのみ無視されます。 Null 非許容値型に対して Null 値を指定すると、例外が発生します。 詳細については、GitHub の dotnet/corefx リポジトリにある[null 非許容の値型に関する問題](https://github.com/dotnet/corefx/issues/40922)を参照してください。

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a>Utf8JsonReader、Utf8JsonWriter、JsonDocument

<xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> は、UTF-8 でエンコードされた JSON テキスト用の高パフォーマンス、低割り当て、転送のみのリーダーです。`ReadOnlySpan<byte>` から読み取られます。 `Utf8JsonReader` は、カスタムパーサーとデシリアライザーを構築するために使用できる低レベルの型です。 <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> メソッドは、内部で `Utf8JsonReader` を使用します。

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> は、`String`、`Int32`、`DateTime`などの一般的な .NET 型から、UTF-8 でエンコードされた JSON テキストを書き込むための高パフォーマンスの方法です。 ライターは、カスタムシリアライザーを構築するために使用できる低レベルの型です。 <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> メソッドは、内部で `Utf8JsonWriter` を使用します。

<xref:System.Text.Json.JsonDocument?displayProperty=fullName> は、`Utf8JsonReader`を使用して、読み取り専用ドキュメントオブジェクトモデル (DOM) を構築する機能を提供します。 DOM は、JSON ペイロード内のデータへのランダムアクセスを提供します。 ペイロードを構成する JSON 要素には、<xref:System.Text.Json.JsonElement> の種類を使用してアクセスできます。 `JsonElement` には、JSON テキストを共通の .NET 型に変換するための Api と共に配列とオブジェクトの列挙子が用意されています。 `JsonDocument` は <xref:System.Text.Json.JsonDocument.RootElement> プロパティを公開します。

以下のセクションでは、これらのツールを使用して JSON の読み取りと書き込みを行う方法について説明します。

## <a name="use-jsondocument-for-access-to-data"></a>データへのアクセスに JsonDocument を使用する

次の例は、<xref:System.Text.Json.JsonDocument> クラスを使用して、データへのランダムアクセスを行う方法を示しています。

```csharp
double sum = 0;
int count = 0;

using (JsonDocument document = JsonDocument.Parse(jsonString))
{
    JsonElement root = document.RootElement;
    JsonElement studentsElement = root.GetProperty("Students");
    foreach (JsonElement student in studentsElement.EnumerateArray())
    {
        if (student.TryGetProperty("Grade", out JsonElement gradeElement))
        {
            sum += gradeElement.GetDouble();
        }
        else
        {
            sum += 70;
        }
        count++;
    }
}

double average = sum / count;
Console.WriteLine($"Average grade: {average}");
```

上記のコードでは次の操作が行われます。

* は、分析する JSON が `jsonString`という名前の文字列に含まれていると想定します。
* `Grade` プロパティを持つ `Students` 配列内のオブジェクトの平均グレードを計算します。 
* 学年のない学生に対して既定のグレード70を割り当てます。
* 各イテレーションで `count` 変数をインクリメントして生徒をカウントします。 別の方法として、<xref:System.Text.Json.JsonElement.GetArrayLength%2A>を呼び出すこともできます。

  ```csharp
  count = studentsElement.GetArrayLength();
  ```

このコードで処理される JSON の例を次に示します。

```json
{
  "Class Name": "Science",
  "Teacher's Name": "Jane",
  "Semester": "2019-01-01",
  "Students": [
    {
      "Name": "John",
      "Grade": 94.3
    },
    {
      "Name": "James",
      "Grade": 81.0
    },
    {
      "Name": "Julia",
      "Grade": 91.9
    },
    {
      "Name": "Jessica",
      "Grade": 72.4
    },
    {
      "Name": "Johnathan"
    }
  ],
  "Final": true
}
```

## <a name="use-jsondocument-to-write-json"></a>JsonDocument を使用した JSON の記述

次の例は、<xref:System.Text.Json.JsonDocument>から JSON を書き込む方法を示しています。

```csharp
string jsonString = File.ReadAllText(inputFileName);

var writerOptions = new JsonWriterOptions { Indented = true };
var documentOptions = new JsonDocumentOptions { CommentHandling = JsonCommentHandling.Skip };

using (FileStream fs = File.Create(outputFileName))
using (var writer = new Utf8JsonWriter(fs, options: writerOptions))
using (JsonDocument document = JsonDocument.Parse(jsonString, documentOptions))
{
    JsonElement root = document.RootElement;

    if (root.ValueKind == JsonValueKind.Object)
    {
        writer.WriteStartObject();
    }
    else
    {
        return;
    }

    foreach (JsonProperty property in root.EnumerateObject())
    {
        property.WriteTo(writer);
    }

    writer.WriteEndObject();

    writer.Flush();
}
```

上記のコードでは次の操作が行われます。

* JSON ファイルを読み取り、データを `JsonDocument`に読み込み、書式設定された (非常に印刷された) JSON をファイルに書き込みます。
* <xref:System.Text.Json.JsonDocumentOptions> を使用して、入力 JSON 内のコメントを許可しますが、無視することを指定します。
* 完了すると、はライターで <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> を呼び出します。 別の方法として、破棄されたときにライターを autoflush することもできます。 

コード例によって処理される JSON 入力の例を次に示します。

```json
{"Class Name": "Science","Teacher's Name": "Jane","Semester": "2019-01-01","Students": [{"Name": "John","Grade": 94.3},{"Name": "James","Grade": 81.0},{"Name": "Julia","Grade": 91.9},{"Name": "Jessica","Grade": 72.4},{"Name": "Johnathan"}],"Final": true}
```

その結果、次のような整形出力の JSON 出力が生成されます。

```json
{
  "Class Name": "Science",
  "Teacher\u0027s Name": "Jane",
  "Semester": "2019-01-01",
  "Students": [
    {
      "Name": "John",
      "Grade": 94.3
    },
    {
      "Name": "James",
      "Grade": 81.0
    },
    {
      "Name": "Julia",
      "Grade": 91.9
    },
    {
      "Name": "Jessica",
      "Grade": 72.4
    },
    {
      "Name": "Johnathan"
    }
  ],
  "Final": true
}
```

## <a name="use-utf8jsonwriter"></a>Utf8JsonWriter を使用する

次の例は、<xref:System.Text.Json.Utf8JsonWriter> クラスの使用方法を示しています。

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

## <a name="use-utf8jsonreader"></a>Utf8JsonReader を使用する

次の例は、<xref:System.Text.Json.Utf8JsonReader> クラスの使用方法を示しています。

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

上記のコードでは、`jsonUtf8` 変数が、UTF-8 としてエンコードされた有効な JSON を含むバイト配列であることを前提としています。

### <a name="filter-data-using-utf8jsonreader"></a>Utf8JsonReader を使用してデータをフィルター処理する

次の例は、ファイルを同期的に読み取り、値を検索する方法を示しています。

```csharp
class Program
{
    private static readonly byte[] s_nameUtf8 = Encoding.UTF8.GetBytes("name");
    private static readonly byte[] s_universityUtf8 = Encoding.UTF8.GetBytes("University");

    private static void ReaderFromFileSync(string fileName)
    {
         string jsonString = File.ReadAllText(fileName);
         ReadOnlySpan<byte> jsonReadOnlySpan = Encoding.UTF8.GetBytes(jsonString);

        int count = 0;
        int total = 0;

        var json = new Utf8JsonReader(jsonReadOnlySpan, isFinalBlock: true, state: default);

        while (json.Read())
        {
            JsonTokenType tokenType = json.TokenType;

            switch (tokenType)
            {
                case JsonTokenType.StartObject:
                    total++;
                    break;
                case JsonTokenType.PropertyName:
                    if (json.ValueSpan.SequenceEqual(s_nameUtf8))
                    {
                        bool result = json.Read();

                        Debug.Assert(result);  // Assume valid JSON
                        Debug.Assert(json.TokenType == JsonTokenType.String);   // Assume known, valid JSON schema

                        if (json.ValueSpan.EndsWith(s_universityUtf8))
                        {
                            count++;
                        }
                    }
                    break;
            }
        }
        Console.WriteLine($"{count} out of {total} have names that end with 'University'");
    }
}
```

上記のコードでは次の操作が行われます。

* は、ファイルが UTF-16 としてエンコードされているものと想定し、UTF-8 にトランスコードします。 UTF-8 としてエンコードされたファイルは、次のコードを使用して、`ReadOnlySpan<byte>`に直接読み取ることができます。

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName); 
  ```

* JSON にオブジェクトの配列が含まれており、各オブジェクトに文字列型の "name" プロパティが含まれていると仮定します。
* オブジェクトをカウントし、"大学" で終わるプロパティ値を `name` します。

上記のコードが読み取ることができる JSON のサンプルを次に示します。 結果として生成される概要メッセージは、"2 ~ 4 個の名前が ' 大学 ' で終わっています" です。

```json
[
  {
    "web_pages": [ "https://contoso.edu/" ],
    "alpha_two_code": "US",
    "state-province": null,
    "country": "United States",
    "domains": [ "contoso.edu" ],
    "name": "Contoso Community College"
  },
  {
    "web_pages": [ "http://fabrikam.edu/" ],
    "alpha_two_code": "US",
    "state-province": null,
    "country": "United States",
    "domains": [ "fabrikam.edu" ],
    "name": "Fabrikam Community College"
  },
  {
    "web_pages": [ "http://www.contosouniversity.edu/" ],
    "alpha_two_code": "US",
    "state-province": null,
    "country": "United States",
    "domains": [ "contosouniversity.edu" ],
    "name": "Contoso University"
  },
  {
    "web_pages": [ "http://www.fabrikamuniversity.edu/" ],
    "alpha_two_code": "US",
    "state-province": null,
    "country": "United States",
    "domains": [ "fabrikamuniversity.edu" ],
    "name": "Fabrikam University"
  }
]
```

## <a name="additional-resources"></a>その他の技術情報

* [System.string の概要](system-text-json-overview.md)
* [System.string API リファレンス](xref:System.Text.Json)
* [System.string のカスタムコンバーターを作成する](system-text-json-converters-how-to.md)
* [System.string での DateTime と DateTimeOffset のサポート](../datetime/system-text-json-support.md)
