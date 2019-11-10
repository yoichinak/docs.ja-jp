---
title: JSON シリアル化のカスタムコンバーターを記述する方法-.NET
author: tdykstra
ms.author: tdykstra
ms.date: 10/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
- converters
ms.openlocfilehash: 361818a0bda8863f8878b86e5fb377dc0faf5246
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/07/2019
ms.locfileid: "73741904"
---
# <a name="how-to-write-custom-converters-for-json-serialization-in-net"></a>.NET で JSON シリアル化のカスタムコンバーターを記述する方法

この記事では、<xref:System.Text.Json> 名前空間に用意されている JSON シリアル化クラスのカスタムコンバーターを作成する方法について説明します。 `System.Text.Json`の概要については、「 [.net で JSON をシリアル化および逆シリアル化する方法](system-text-json-how-to.md)」を参照してください。

*コンバーター*は、オブジェクトまたは値を JSON との間で変換するクラスです。 `System.Text.Json` 名前空間には、JavaScript プリミティブにマップされるほとんどのプリミティブ型用の組み込みのコンバーターがあります。 カスタムコンバーターは、次のように記述できます。

* 組み込みのコンバーターの既定の動作をオーバーライドする場合は。 たとえば、既定の ISO 8601-1:2019 形式ではなく、`DateTime` 値を mm/dd/yyyy 形式で表すようにすることができます。
* カスタム値型をサポートする場合は。 たとえば、`PhoneNumber` 構造体などです。

また、カスタムコンバーターを作成して、現在のリリースに含まれていない機能を使用して `System.Text.Json` を拡張することもできます。 この記事の後半では、次のシナリオについて説明します。

* 推論された[型をオブジェクトのプロパティに逆シリアル](#deserialize-inferred-types-to-object-properties)化します。
* [文字列以外のキーを使用した辞書をサポート](#support-dictionary-with-non-string-key)します。
* [ポリモーフィック逆シリアル化をサポート](#support-polymorphic-deserialization)します。

## <a name="custom-converter-patterns"></a>カスタムコンバーターパターン

カスタムコンバーターを作成するには、基本パターンとファクトリパターンという2つのパターンがあります。 ファクトリパターンは、型 `Enum` またはオープンジェネリックを処理するコンバーター用です。 基本パターンは、非ジェネリックおよびクローズジェネリック型用です。  たとえば、次の型のコンバーターには、ファクトリパターンが必要です。

* `Dictionary<TKey, TValue>`
* `Enum`
* `List<T>`

基本的なパターンによって処理できる型の例を次に示します。

* `Dictionary<int, string>`
* `WeekdaysEnum`
* `List<DateTimeOffset>`
* `DateTime`
* `Int32`

基本パターンでは、1つの型を処理できるクラスが作成されます。 ファクトリパターンは、実行時に特定の型が必要であることを判断し、適切なコンバーターを動的に作成するクラスを作成します。

## <a name="sample-basic-converter"></a>基本的なコンバーターのサンプル

次のサンプルは、既存のデータ型の既定のシリアル化をオーバーライドするコンバーターです。 コンバーターでは、`DateTimeOffset` プロパティに mm/dd/yyyy 形式が使用されます。

```csharp
private class ExampleDateTimeOffsetConverter : JsonConverter<DateTimeOffset>
{
    public override DateTimeOffset Read(
        ref Utf8JsonReader reader, 
        Type typeToConvert, 
        JsonSerializerOptions options)
    {
        return DateTimeOffset.ParseExact(reader.GetString(), 
            "MM/dd/yyyy", CultureInfo.InvariantCulture);
    }

    public override void Write(
        Utf8JsonWriter writer, 
        DateTimeOffset value, 
        JsonSerializerOptions options)
    {
        writer.WriteStringValue(value.ToString(
            "MM/dd/yyyy", CultureInfo.InvariantCulture));
    }
}
```

## <a name="sample-factory-pattern-converter"></a>サンプルファクトリパターンコンバーター

次のコードは、`Dictionary<Enum,TValue>`で動作するカスタムコンバーターを示しています。 このコードは、最初のジェネリック型パラメーターが `Enum`、2番目のジェネリック型パラメーターが開いているため、ファクトリパターンに従います。 `CanConvert` メソッドは、2つのジェネリックパラメーターを持つ `Dictionary` に対してのみ `true` を返します。最初のパラメーターは `Enum` 型です。 内部コンバーターは、`TValue`に対して実行時に提供されるいずれかの型を処理する既存のコンバーターを取得します。 

```csharp
using System;
using System.Collections.Generic;
using System.Reflection;
using System.Text.Json;
using System.Text.Json.Serialization;

namespace SystemTextJsonSamples
{
    public class ConverterDictionaryTKeyEnumTValue : JsonConverterFactory
    {
        public override bool CanConvert(Type typeToConvert)
        {
            if (!typeToConvert.IsGenericType)
            {
                return false;
            }

            if (typeToConvert.GetGenericTypeDefinition() != typeof(Dictionary<,>))
            {
                return false;
            }

            return typeToConvert.GetGenericArguments()[0].IsEnum;
        }

        public override JsonConverter CreateConverter(
            Type type, 
            JsonSerializerOptions options)
        {
            Type keyType = type.GetGenericArguments()[0];
            Type valueType = type.GetGenericArguments()[1];

            JsonConverter converter = (JsonConverter)Activator.CreateInstance(
                typeof(DictionaryEnumConverterInner<,>).MakeGenericType(
                    new Type[] { keyType, valueType }),
                BindingFlags.Instance | BindingFlags.Public,
                binder: null,
                args: new object[] { options },
                culture: null);

            return converter;
        }

        private class DictionaryEnumConverterInner<TKey, TValue> : 
            JsonConverter<Dictionary<TKey, TValue>> where TKey : struct, Enum
        {
            private readonly JsonConverter<TValue> _valueConverter;
            private Type _keyType;
            private Type _valueType;

            public DictionaryEnumConverterInner(JsonSerializerOptions options)
            {
                // For performance, use the existing converter if available.
                _valueConverter = (JsonConverter<TValue>)options
                    .GetConverter(typeof(TValue));

                // Cache the key and value types.
                _keyType = typeof(TKey);
                _valueType = typeof(TValue);
            }

            public override Dictionary<TKey, TValue> Read(
                ref Utf8JsonReader reader, 
                Type typeToConvert, 
                JsonSerializerOptions options)
            {
                if (reader.TokenType != JsonTokenType.StartObject)
                {
                    throw new JsonException();
                }

                Dictionary<TKey, TValue> value = new Dictionary<TKey, TValue>();

                while (reader.Read())
                {
                    if (reader.TokenType == JsonTokenType.EndObject)
                    {
                        return value;
                    }

                    // Get the key.
                    if (reader.TokenType != JsonTokenType.PropertyName)
                    {
                        throw new JsonException();
                    }

                    string propertyName = reader.GetString();

                    // For performance, parse with ignoreCase:false first.
                    if (!Enum.TryParse(propertyName, ignoreCase: false, out TKey key) &&
                        !Enum.TryParse(propertyName, ignoreCase: true, out key))
                    {
                        throw new JsonException(
                            $"Unable to convert \"{propertyName}\" to Enum \"{_keyType}\".");
                    }

                    // Get the value.
                    TValue v;
                    if (_valueConverter != null)
                    {
                        reader.Read();
                        v = _valueConverter.Read(ref reader, _valueType, options);
                    }
                    else
                    {
                        v = JsonSerializer.Deserialize<TValue>(ref reader, options);
                    }

                    // Add to dictionary.
                    value.Add(key, v);
                }

                throw new JsonException();
            }

            public override void Write(
                Utf8JsonWriter writer, 
                Dictionary<TKey, TValue> value, 
                JsonSerializerOptions options)
            {
                writer.WriteStartObject();

                foreach (KeyValuePair<TKey, TValue> kvp in value)
                {
                    writer.WritePropertyName(kvp.Key.ToString());

                    if (_valueConverter != null)
                    {
                        _valueConverter.Write(writer, kvp.Value, options);
                    }
                    else
                    {
                        JsonSerializer.Serialize(writer, kvp.Value, options);
                    }
                }

                writer.WriteEndObject();
            }
        }
    }
}
```

上記のコードは、この記事の後半で説明する[文字列以外のキーを使用したサポート辞書](#support-dictionary-with-non-string-key)に示されているものと同じです。

## <a name="steps-to-follow-the-basic-pattern"></a>基本的なパターンに従う手順

次の手順では、基本的なパターンに従ってコンバーターを作成する方法について説明します。

* `T` がシリアル化および逆シリアル化される型である <xref:System.Text.Json.Serialization.JsonConverter%601> から派生するクラスを作成します。
* `Read` メソッドをオーバーライドして受信 JSON を逆シリアル化し、型 `T`に変換します。 メソッドに渡された <xref:System.Text.Json.Utf8JsonReader> を使用して、JSON を読み取ります。
* `Write` メソッドをオーバーライドして、`T`型の受信オブジェクトをシリアル化します。 メソッドに渡された <xref:System.Text.Json.Utf8JsonWriter> を使用して JSON を記述します。
* `CanConvert` メソッドは、必要な場合にのみオーバーライドします。 変換する型が `T`型の場合、既定の実装は `true` を返します。 したがって、型 `T` だけをサポートするコンバーターは、このメソッドをオーバーライドする必要はありません。 このメソッドをオーバーライドする必要があるコンバーターの例については、この記事で後述する「[ポリモーフィックな逆シリアル化](#support-polymorphic-deserialization)」を参照してください。

[組み込みのコンバーターソースコード](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json/src/System/Text/Json/Serialization/Converters/)は、カスタムコンバーターを作成するための参照の実装として参照できます。

## <a name="steps-to-follow-the-factory-pattern"></a>ファクトリパターンに従う手順

次の手順では、ファクトリパターンに従ってコンバーターを作成する方法について説明します。

* <xref:System.Text.Json.Serialization.JsonConverterFactory> から派生するクラスを作成します。
* 変換する型が、コンバーターが処理できる型である場合に true を返すように `CanConvert` メソッドをオーバーライドします。 たとえば、コンバーターが `List<T>` 用の場合、`List<int>`、`List<string>`、および `List<DateTime>`だけを処理できます。 
* `CreateConverter` メソッドをオーバーライドして、実行時に提供される変換の種類を処理するコンバータークラスのインスタンスを返します。
* `CreateConverter` メソッドによってインスタンス化されるコンバータークラスを作成します。 

オブジェクトを文字列との間で変換するコードはすべての型で同じではないため、オープンジェネリックにはファクトリパターンが必要です。 オープンジェネリック型 (`List<T>`など) のコンバーターは、背後にあるクローズジェネリック型 (`List<DateTime>`など) のコンバーターを作成する必要があります。 コードは、コンバーターが処理できる各閉じられたジェネリック型を処理するように記述する必要があります。

`Enum` 型はオープンジェネリック型に似ています。 `Enum` のコンバーターは、シーンの背後にある特定の `Enum` (`WeekdaysEnum`など) のコンバーターを作成する必要があります。 

## <a name="error-handling"></a>エラー処理

エラー処理コードで例外をスローする必要がある場合は、メッセージを使用せずに <xref:System.Text.Json.JsonException> をスローすることを検討してください。 この例外の種類では、エラーの原因となった JSON の部分へのパスを含むメッセージが自動的に作成されます。 たとえば、ステートメント `throw new JsonException();` では、次の例のようなエラーメッセージが生成されます。

```text
Unhandled exception. System.Text.Json.JsonException: 
The JSON value could not be converted to System.Object. 
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

メッセージ (`throw new JsonException("Error occurred)`など) を指定した場合でも、例外は <xref:System.Text.Json.JsonException.Path> プロパティのパスを提供します。

## <a name="register-a-custom-converter"></a>カスタムコンバーターを登録する

カスタムコンバーターを*登録*して、`Serialize` および `Deserialize` メソッドで使用されるようにします。 次のいずれかの方法を選択します。

* コンバータークラスのインスタンスを <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> コレクションに追加します。
* カスタムコンバーターを必要とするプロパティに[[jsonconverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute)属性を適用します。
* [[Jsonconverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute)属性をカスタム値型を表すクラスまたは構造体に適用します。

## <a name="registration-sample---converters-collection"></a>登録サンプル-コンバーターコレクション 

`DateTimeOffset`型のプロパティの既定値 `ExampleDateTimeOffsetConverter` する例を次に示します。

```csharp
//...
JsonSerializerOptions options = new JsonSerializerOptions();
options.Converters.Add(new ExampleDateTimeOffsetConverter());
string json = JsonSerializer.Serialize(weatherForecast, options);
```

次の型をシリアル化するとします。

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

カスタムコンバーターが使用されたことを示す JSON 出力の例を次に示します。

```json
{
  "Date": "08/01/2019",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

次のコードでは、カスタム `DateTimeOffset` コンバーターを使用して逆シリアル化するのと同じアプローチを使用します。

```csharp
//...
JsonSerializerOptions options = new JsonSerializerOptions();
options.Converters.Add(new ExampleDateTimeOffsetConverter());
weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json, options);
```

## <a name="registration-sample---jsonconverter-on-a-property"></a>登録のサンプル-[JsonConverter] プロパティ

次のコードでは、`Date` プロパティのカスタムコンバーターを選択します。

```csharp
class WeatherForecastWithConverter
{
    [JsonConverter(typeof(ExampleDateTimeOffsetConverter))]
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

`WeatherForecastWithConverter` をシリアル化および逆シリアル化するコードでは、`JsonSerializeOptions.Converters`を使用する必要はありません。

```csharp
string json = JsonSerializer.Serialize(weatherForecastWithConverter);
```

```csharp
weatherForecast = JsonSerializer.Deserialize<WeatherForecastWithConverter>(json);
```

## <a name="registration-sample---jsonconverter-on-a-type"></a>登録サンプル-[JsonConverter] 型

次に、構造体を作成し、それに `[JsonConverter]` 属性を適用するコードを示します。

```csharp
[JsonConverter(typeof(TemperatureConverter))]
public struct Temperature
{
    public Temperature(int degrees, bool celsius)
    {
        _degrees = degrees;
        _isCelsius = celsius;
    }
    private bool _isCelsius;
    private int _degrees;
    public int Degrees => _degrees;
    public bool IsCelsius => _isCelsius; 
    public bool IsFahrenheit => !_isCelsius;
    public override string ToString() =>
        $"{_degrees.ToString()}{(_isCelsius ? "C" : "F")}";
    public static Temperature Parse(string input)
    {
        int degrees = int.Parse(input.Substring(0, input.Length - 1));
        bool celsius = (input.Substring(input.Length - 1) == "C");
        return new Temperature(degrees, celsius);
    }
}
```

前の構造体のカスタムコンバーターは次のようになります。

```csharp
public class TemperatureConverter : JsonConverter<Temperature>
{
    public override Temperature Read(
        ref Utf8JsonReader reader,
        Type typeToConvert,
        JsonSerializerOptions options)
    {
        Debug.Assert(typeToConvert == typeof(Temperature));
        return Temperature.Parse(reader.GetString());
    }

    public override void Write(
        Utf8JsonWriter writer,
        Temperature value,
        JsonSerializerOptions options)
    {
        writer.WriteStringValue(value.ToString());
    }
}
```

構造体の `[JsonConvert]` 属性は、`Temperature`型のプロパティの既定値としてカスタムコンバーターを登録します。 コンバーターは、シリアル化または逆シリアル化するときに、次の型の `TemperatureC` プロパティで自動的に使用されます。

```csharp
class WeatherForecastWithTemperatureStruct
{
    public DateTimeOffset Date { get; set; }
    public Temperature TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

## <a name="converter-registration-precedence"></a>コンバーターの登録の優先順位

シリアル化または逆シリアル化の際には、次の順序で JSON 要素ごとにコンバーターが選択され、最も高い優先度から順に表示されます。

* `[JsonConverter]` プロパティに適用されます。
* `Converters` コレクションに追加されたコンバーター。
* `[JsonConverter]` カスタム値型または POCO に適用されます。

1つの型に対して複数のカスタムコンバーターが `Converters` コレクションに登録されている場合、`CanConvert` に対して true を返す最初のコンバーターが使用されます。

組み込みのコンバーターは、適用可能なカスタムコンバーターが登録されていない場合にのみ選択されます。

## <a name="converter-samples-for-common-scenarios"></a>一般的なシナリオのコンバーターのサンプル

以下のセクションでは、組み込み機能で処理されない一般的なシナリオに対処するコンバーターのサンプルについて説明します。

### <a name="deserialize-inferred-types-to-object-properties"></a>推論された型のオブジェクトプロパティへの逆シリアル化

`Object`型のプロパティに逆シリアル化すると、`JsonElement` オブジェクトが作成されます。 その理由は、デシリアライザーは、作成する CLR 型を認識しないため、推測しようとしません。 たとえば、JSON プロパティに "true" が含まれている場合、デシリアライザーは、値が `Boolean`であることを推論しません。また、要素に "01/01/2019" がある場合、デシリアライザーは `DateTime`であることを推論しません。

型の推定は不正確になる可能性があります。 デシリアライザーが、小数点のない JSON 番号を `long`として解析する場合、値が最初に `ulong` または `BigInteger`としてシリアル化された場合、範囲外の問題が発生する可能性があります。 数値が最初に `decimal`としてシリアル化された場合、`double` として小数点がある数値を解析すると、精度が失われる可能性があります。

型の推定が必要なシナリオでは、次のコードは `Object` プロパティのカスタムコンバーターを示しています。 コードは次のように変換します。

* `true` と `false` `Boolean`
* `long` または `double` する数値
* `DateTime` する日付
* `string` する文字列
* 他のすべての `JsonElement`

```csharp
using System;
using System.Text.Json;
using System.Text.Json.Serialization;

namespace SystemTextJsonSamples
{
    public class ObjectToInferredTypesConverter
        : JsonConverter<object>
    {
        public override object Read(
            ref Utf8JsonReader reader,
            Type typeToConvert,
            JsonSerializerOptions options)
        {
            if (reader.TokenType == JsonTokenType.True)
            {
                return true;
            }

            if (reader.TokenType == JsonTokenType.False)
            {
                return false;
            }

            if (reader.TokenType == JsonTokenType.Number)
            {
                if (reader.TryGetInt64(out long l))
                {
                    return l;
                }

                return reader.GetDouble();
            }

            if (reader.TokenType == JsonTokenType.String)
            {
                if (reader.TryGetDateTime(out DateTime datetime))
                {
                    return datetime;
                }

                return reader.GetString();
            }

            // Use JsonElement as fallback.
            // Newtonsoft uses JArray or JObject.
            using (JsonDocument document = JsonDocument.ParseValue(ref reader))
            {
                return document.RootElement.Clone();
            }
        }

        public override void Write(
            Utf8JsonWriter writer,
            object value,
            JsonSerializerOptions options)
        {
            throw new InvalidOperationException("Should not get here.");
        }
    }
}
```

次のコードは、コンバーターを登録します。

```csharp
options = new JsonSerializerOptions();
options.Converters.Add(new ObjectToInferredTypesConverter());
```

オブジェクトプロパティを持つ型の例を次に示します。

```csharp
public class WeatherForecastWithObjectProperties
{
    public object Date { get; set; }
    public object TemperatureC { get; set; }
    public object Summary { get; set; }
}
```

次の JSON の例には、`DateTime`、`long`、および `string`として逆シリアル化される値が含まれています。

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
}
```

カスタムコンバーターを使用しない場合、逆シリアル化によって各プロパティに `JsonElement` が挿入されます。

`System.Text.Json.Serialization` 名前空間の[単体テストフォルダー](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/)には、オブジェクトプロパティへの逆シリアル化を処理するカスタムコンバーターの例が多数あります。

### <a name="support-dictionary-with-non-string-key"></a>文字列以外のキーを使用したサポート辞書

ディクショナリコレクションの組み込みサポートは `Dictionary<string, TValue>`用です。 つまり、キーは文字列である必要があります。 キーとして整数またはその他の型を持つディクショナリをサポートするには、カスタムコンバーターが必要です。

次のコードは、`Dictionary<Enum,TValue>`で動作するカスタムコンバーターを示しています。

```csharp
using System;
using System.Collections.Generic;
using System.Reflection;
using System.Text.Json;
using System.Text.Json.Serialization;

namespace SystemTextJsonSamples
{
    public class ConverterDictionaryTKeyEnumTValue : JsonConverterFactory
    {
        public override bool CanConvert(Type typeToConvert)
        {
            if (!typeToConvert.IsGenericType)
            {
                return false;
            }

            if (typeToConvert.GetGenericTypeDefinition() != typeof(Dictionary<,>))
            {
                return false;
            }

            return typeToConvert.GetGenericArguments()[0].IsEnum;
        }

        public override JsonConverter CreateConverter(
            Type type, 
            JsonSerializerOptions options)
        {
            Type keyType = type.GetGenericArguments()[0];
            Type valueType = type.GetGenericArguments()[1];

            JsonConverter converter = (JsonConverter)Activator.CreateInstance(
                typeof(DictionaryEnumConverterInner<,>).MakeGenericType(
                    new Type[] { keyType, valueType }),
                BindingFlags.Instance | BindingFlags.Public,
                binder: null,
                args: new object[] { options },
                culture: null);

            return converter;
        }

        private class DictionaryEnumConverterInner<TKey, TValue> : 
            JsonConverter<Dictionary<TKey, TValue>> where TKey : struct, Enum
        {
            private readonly JsonConverter<TValue> _valueConverter;
            private Type _keyType;
            private Type _valueType;

            public DictionaryEnumConverterInner(JsonSerializerOptions options)
            {
                // For performance, use the existing converter if available.
                _valueConverter = (JsonConverter<TValue>)options
                    .GetConverter(typeof(TValue));

                // Cache the key and value types.
                _keyType = typeof(TKey);
                _valueType = typeof(TValue);
            }

            public override Dictionary<TKey, TValue> Read(
                ref Utf8JsonReader reader, 
                Type typeToConvert, 
                JsonSerializerOptions options)
            {
                if (reader.TokenType != JsonTokenType.StartObject)
                {
                    throw new JsonException();
                }

                Dictionary<TKey, TValue> value = new Dictionary<TKey, TValue>();

                while (reader.Read())
                {
                    if (reader.TokenType == JsonTokenType.EndObject)
                    {
                        return value;
                    }

                    // Get the key.
                    if (reader.TokenType != JsonTokenType.PropertyName)
                    {
                        throw new JsonException();
                    }

                    string propertyName = reader.GetString();

                    // For performance, parse with ignoreCase:false first.
                    if (!Enum.TryParse(propertyName, ignoreCase: false, out TKey key) &&
                        !Enum.TryParse(propertyName, ignoreCase: true, out key))
                    {
                        throw new JsonException(
                            $"Unable to convert \"{propertyName}\" to Enum \"{_keyType}\".");
                    }

                    // Get the value.
                    TValue v;
                    if (_valueConverter != null)
                    {
                        reader.Read();
                        v = _valueConverter.Read(ref reader, _valueType, options);
                    }
                    else
                    {
                        v = JsonSerializer.Deserialize<TValue>(ref reader, options);
                    }

                    // Add to dictionary.
                    value.Add(key, v);
                }

                throw new JsonException();
            }

            public override void Write(
                Utf8JsonWriter writer, 
                Dictionary<TKey, TValue> value, 
                JsonSerializerOptions options)
            {
                writer.WriteStartObject();

                foreach (KeyValuePair<TKey, TValue> kvp in value)
                {
                    writer.WritePropertyName(kvp.Key.ToString());

                    if (_valueConverter != null)
                    {
                        _valueConverter.Write(writer, kvp.Value, options);
                    }
                    else
                    {
                        JsonSerializer.Serialize(writer, kvp.Value, options);
                    }
                }

                writer.WriteEndObject();
            }
        }
    }
}
```

次のコードは、コンバーターを登録します。

```csharp
var serializeOptions = new JsonSerializerOptions();
serializeOptions.Converters.Add(new ConverterDictionaryTKeyEnumTValue());
```

コンバーターは、次の `Enum`を使用する次のクラスの `TemperatureRanges` プロパティをシリアル化および逆シリアル化できます。

```csharp
public class WeatherForecastWithEnumDictionary
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    public Dictionary<SummaryWordsEnum, int> TemperatureRanges { get; set; }
}

public enum SummaryWordsEnum
{
    Cold, Hot
}
```

シリアル化からの JSON 出力は、次の例のようになります。

```json
{

  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "Cold": 20,
    "Hot": 40
  }
}
```

`System.Text.Json.Serialization` 名前空間の[単体テストフォルダー](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/)には、文字列キー以外のディクショナリを処理するカスタムコンバーターの例が多数あります。

### <a name="support-polymorphic-deserialization"></a>ポリモーフィック逆シリアル化のサポート

[ポリモーフィックなシリアル化](system-text-json-how-to.md#serialize-properties-of-derived-classes)ではカスタムコンバーターは必要ありませんが、逆シリアル化にはカスタムコンバーターが必要です。

たとえば、`Person` 抽象基本クラスがあり、`Employee` および `Customer` 派生クラスがあるとします。 ポリモーフィックな逆シリアル化とは、デザイン時に `Person` を逆シリアル化ターゲットとして指定できること、および JSON 内の `Customer` オブジェクトと `Employee` オブジェクトが実行時に正しく逆シリアル化されることを意味します。 逆シリアル化中に、JSON で必要な型を識別する手掛かりを見つける必要があります。 使用できる手掛かりの種類は、シナリオによって異なります。 たとえば、識別子のプロパティを使用できる場合や、特定のプロパティの有無に依存する場合があります。 `System.Text.Json` の現在のリリースでは、ポリモーフィックな逆シリアル化のシナリオを処理する方法を指定する属性が提供されないため、カスタムコンバーターが必要になります。

次のコードは、基底クラス、2つの派生クラス、およびそれらのカスタムコンバーターを示しています。 コンバーターは、ポリモーフィックな逆シリアル化を行うために識別子プロパティを使用します。 型識別子はクラス定義に含まれていませんが、シリアル化中に作成され、逆シリアル化中に読み取られます。

```csharp
public class Person
{
    public string Name { get; set; }
}

public class Customer : Person
{
    public decimal CreditLimit { get; set; }
}

public class Employee : Person
{
    public string OfficeNumber { get; set; }
}
```

```csharp
using System;
using System.Text.Json;
using System.Text.Json.Serialization;

namespace SystemTextJsonSamples
{
    public class PersonConverterWithTypeDiscriminator : JsonConverter<Person>
    {
        enum TypeDiscriminator
        {
            Customer = 1,
            Employee = 2
        }

        public override bool CanConvert(Type typeToConvert)
        {
            return typeof(Person).IsAssignableFrom(typeToConvert);
        }

        public override Person Read(ref Utf8JsonReader reader, Type typeToConvert, JsonSerializerOptions options)
        {
            if (reader.TokenType != JsonTokenType.StartObject)
            {
                throw new JsonException();
            }

            reader.Read();
            if (reader.TokenType != JsonTokenType.PropertyName)
            {
                throw new JsonException();
            }

            string propertyName = reader.GetString();
            if (propertyName != "TypeDiscriminator")
            {
                throw new JsonException();
            }

            reader.Read();
            if (reader.TokenType != JsonTokenType.Number)
            {
                throw new JsonException();
            }

            Person value;
            TypeDiscriminator typeDiscriminator = (TypeDiscriminator)reader.GetInt32();
            switch (typeDiscriminator)
            {
                case TypeDiscriminator.Customer:
                    value = new Customer();
                    break;

                case TypeDiscriminator.Employee:
                    value = new Employee();
                    break;

                default:
                    throw new JsonException();
            }

            while (reader.Read())
            {
                if (reader.TokenType == JsonTokenType.EndObject)
                {
                    return value;
                }

                if (reader.TokenType == JsonTokenType.PropertyName)
                {
                    propertyName = reader.GetString();
                    reader.Read();
                    switch (propertyName)
                    {
                        case "CreditLimit":
                            decimal creditLimit = reader.GetDecimal();
                            ((Customer)value).CreditLimit = creditLimit;
                            break;
                        case "OfficeNumber":
                            string officeNumber = reader.GetString();
                            ((Employee)value).OfficeNumber = officeNumber;
                            break;
                        case "Name":
                            string name = reader.GetString();
                            value.Name = name;
                            break;
                    }
                }
            }

            throw new JsonException();
        }

        public override void Write(Utf8JsonWriter writer, Person value, JsonSerializerOptions options)
        {
            writer.WriteStartObject();

            if (value is Customer customer)
            {
                writer.WriteNumber("TypeDiscriminator", (int)TypeDiscriminator.Customer);
                writer.WriteNumber("CreditLimit", customer.CreditLimit);
            }
            else if (value is Employee employee)
            {
                writer.WriteNumber("TypeDiscriminator", (int)TypeDiscriminator.Employee);
                writer.WriteString("OfficeNumber", employee.OfficeNumber);
            }

            writer.WriteString("Name", value.Name);

            writer.WriteEndObject();
        }
    }
}
```

次のコードは、コンバーターを登録します。

```csharp
options = new JsonSerializerOptions();
options.Converters.Add(new PersonConverterWithTypeDiscriminator());
```

コンバーターは、同じコンバーターを使用して作成された JSON を逆シリアル化できます。たとえば、次のようになります。

```json
[
  {
    "TypeDiscriminator": 1,
    "CreditLimit": 10000,
    "Name": "John"
  },
  {
    "TypeDiscriminator": 2,
    "OfficeNumber": "555-1234",
    "Name": "Nancy"
  }
]
```

## <a name="other-custom-converter-samples"></a>その他のカスタムコンバーターのサンプル

`System.Text.Json.Serialization` ソースコードの[単体テストフォルダー](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/)には、次のような他のカスタムコンバーターのサンプルが含まれています。

* 逆シリアル化時に null を0に変換する `Int32` コンバーター
* 逆シリアル化時に文字列と数値の両方を許可する `Int32` コンバーター
* `Enum` コンバーター
* 外部データを受け入れる `List<T>` コンバーター
* コンマで区切られた数値のリストを処理する `Long[]` コンバーター 

## <a name="additional-resources"></a>その他の技術情報

* [System.string の概要](system-text-json-overview.md)
* [System.string API リファレンス](xref:System.Text.Json)
* [方法: system.string を使用する](system-text-json-how-to.md)
* [組み込みのコンバーターのソースコード](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json/src/System/Text/Json/Serialization/Converters/)
* `System.Text.Json` のカスタムコンバーターに関連する GitHub の問題
  * [36639カスタムコンバーターの概要](https://github.com/dotnet/corefx/issues/36639)
  * [38713オブジェクトへの逆シリアル化について](https://github.com/dotnet/corefx/issues/38713)
  * [40120非文字列キー辞書について](https://github.com/dotnet/corefx/issues/40120)
  * [37787ポリモーフィック逆シリアル化について](https://github.com/dotnet/corefx/issues/37787)
