---
title: System.string での DateTime と DateTimeOffset のサポート
description: System.string ライブラリでの DateTime 型と DateTimeOffset 型のサポートの概要について説明します。
ms.technology: dotnet-standard
author: layomia
ms.author: laakinri
ms.date: 07/22/2019
helpviewer_keywords:
- JSON, Serializer, Utf8
- JSON DateTime, JSON DateTimeOffset
- DateTime, DateTimeOffset
- JsonSerializer, Utf8JsonReader, Utf8JsonWriter, JsonElement, JsonDocument
- JSON Serializer, JSON Reader, JSON Writer
- Converter, JSON Converter, DateTime Converter
- ISO, ISO 8601, ISO 8601-1:2019
ms.openlocfilehash: 182694a3d2df02d5e2c709e33a02bd9fa7d20383
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69973216"
---
# <a name="datetime-and-datetimeoffset-support-in-systemtextjson"></a>System.string での DateTime と DateTimeOffset のサポート

System.string ライブラリは、ISO 8601:-2019 拡張プロファイルに従っ<xref:System.DateTime>て<xref:System.DateTimeOffset> 、との値を解析して書き込みます。
[コンバーター](https://docs.microsoft.com/dotnet/api/system.text.json.serialization.jsonconverter-1?view=netcore-3.0)は、を使用した<xref:System.Text.Json.JsonSerializer>シリアル化と逆シリアル化のためのカスタムサポートを提供します。

## <a name="support-for-the-iso-8601-12019-format"></a>ISO 8601-1:2019 形式のサポート

<xref:System.Text.Json.JsonSerializer> <xref:System.DateTime> <xref:System.DateTimeOffset> 、 、<xref:System.Text.Json.Utf8JsonReader> 、および<xref:System.Text.Json.JsonElement>の各型は、ISO 8601-1:2019 形式の拡張プロファイルに従って、解析および書き込みとテキスト表現を行います。たとえば、2019-07-26t16 のようになります。 <xref:System.Text.Json.Utf8JsonWriter>: 59:57-05:00。

<xref:System.DateTime>および<xref:System.DateTimeOffset>データは、次の<xref:System.Text.Json.JsonSerializer>方法でシリアル化できます。

[!code-csharp[example-serializing-with-jsonserializer](~/samples/snippets/standard/datetime/json/serializing-with-jsonserializer.cs)]

また、次のように<xref:System.Text.Json.JsonSerializer>して逆シリアル化することもできます。

[!code-csharp[example-deserializing-with-jsonserializer-valid](~/samples/snippets/standard/datetime/json/deserializing-with-jsonserializer-valid.cs)]

既定のオプションでは<xref:System.DateTime> 、 <xref:System.DateTimeOffset>入力およびテキスト表現は拡張 ISO 8601-1:2019 プロファイルに準拠している必要があります。
プロファイルに準拠していない表現を逆シリアル化<xref:System.Text.Json.JsonSerializer>しようとする<xref:System.Text.Json.JsonException>と、がスローされます。

[!code-csharp[example-deserializing-with-jsonserializer-error](~/samples/snippets/standard/datetime/json/deserializing-with-jsonserializer-error.cs)]

は<xref:System.Text.Json.JsonDocument> 、JSON ペイロードの内容 (や<xref:System.DateTimeOffset>表現を含む) <xref:System.DateTime>への構造化されたアクセスを提供します。 次の例では、温度のコレクションを指定した場合に、月曜日の平均温度を計算できる方法を示しています。

[!code-csharp[example-computing-with-jsondocument-valid](~/samples/snippets/standard/datetime/json/computing-with-jsondocument-valid.cs)]

準拠<xref:System.DateTime>していない形式<xref:System.Text.Json.JsonDocument>のペイロードで平均温度を計算しようとすると<xref:System.FormatException>、がをスローします。

[!code-csharp[example-computing-with-jsondocument-error](~/samples/snippets/standard/datetime/json/computing-with-jsondocument-error.cs)]

下位レベル<xref:System.Text.Json.Utf8JsonWriter>の書き込み<xref:System.DateTime>と<xref:System.DateTimeOffset>データ:

[!code-csharp[example-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/writing-with-utf8jsonwriter.cs)]

<xref:System.Text.Json.Utf8JsonReader>と<xref:System.DateTime>データ<xref:System.DateTimeOffset>を解析します。

[!code-csharp[example-reading-with-utf8jsonreader-valid](~/samples/snippets/standard/datetime/json/reading-with-utf8jsonreader-valid.cs)]

に<xref:System.Text.Json.Utf8JsonReader>準拠していない形式を読み取ろうとすると、 <xref:System.FormatException>がスローされます。

[!code-csharp[example-reading-with-utf8jsonreader-error](~/samples/snippets/standard/datetime/json/reading-with-utf8jsonreader-error.cs)]

## <a name="custom-support-for-xrefsystemdatetime-and-xrefsystemdatetimeoffset-in-xrefsystemtextjsonjsonserializer"></a><xref:System.DateTime> と<xref:System.DateTimeOffset>のカスタムサポート<xref:System.Text.Json.JsonSerializer>

シリアライザーでカスタムの解析または書式設定を実行する場合は、[カスタムコンバーター](https://docs.microsoft.com/dotnet/api/system.text.json.serialization.jsonconverter-1?view=netcore-3.0)を実装できます。
以下は例です。

### <a name="using-datetimeoffsetparse-and-datetimeoffsettostring"></a>および`DateTime(Offset).Parse`を使用する`DateTime(Offset).ToString`

入力<xref:System.DateTime>または<xref:System.DateTimeOffset>テキスト表現の形式を特定できない場合は`DateTime(Offset).Parse` 、コンバーターの読み取りロジックでメソッドを使用できます。 これにより、を使用できるようになります。さまざまな<xref:System.DateTime>形式と<xref:System.DateTimeOffset>テキスト形式のサポート (iso 8601 以外の文字列や iso 8601 形式の拡張 iso 8601-1:2019 プロファイルに準拠していないなど) のサポート。 この方法では、シリアライザーのネイティブ実装よりもパフォーマンスが大幅に低下します。

シリアル化の場合は、コンバーター `DateTime(Offset).ToString`の書き込みロジックでメソッドを使用できます。 これにより、標準<xref:System.DateTime>の<xref:System.DateTimeOffset> [日付と時刻の形式](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings)、および[カスタムの日付と時刻](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings)の書式を使用して、との値を書き込むことができます。
これは、シリアライザーのネイティブ実装を使用する場合よりも、パフォーマンスが大幅に低下します。

[!code-csharp[example-showing-datetime-parse](~/samples/snippets/standard/datetime/json/datetime-converter-examples/example1/Program.cs)]

> [!NOTE]
> を実装<xref:System.Text.Json.Serialization.JsonConverter%601>するとき`T` 、 <xref:System.DateTime>およびが`typeToConvert`の場合、パラメーター `typeof(DateTime)`は常にになります。
パラメーターは、ポリモーフィックなケースを処理する場合や、ジェネリックを`typeof(T)`使用してパフォーマンスの高い方法を実現する場合に便利です。

### <a name="using-xrefsystembufferstextutf8parser-and-xrefsystembufferstextutf8formatter"></a>および<xref:System.Buffers.Text.Utf8Parser>を使用する<xref:System.Buffers.Text.Utf8Formatter>

入力<xref:System.DateTime>または<xref:System.DateTimeOffset>テキスト表現が "R"、"l"、"O"、"G" のいずれかの[標準日時書式指定文字列](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings)に準拠している場合、または必要に応じて、コンバーターロジックで高速 utf-8 ベースの解析および書式設定メソッドを使用できます。これらの形式のいずれかに従って書き込みます。 これは、および`DateTime(Offset).Parse` `DateTime(Offset).ToString`を使用するよりもはるかに高速です。

次の例は、 <xref:System.DateTime> ["R" 標準形式](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-rfc1123-r-r-format-specifier)に従って値をシリアル化および逆シリアル化するカスタムコンバーターを示しています。

[!code-csharp[example-showing-utf8-parser-and-formatter](~/samples/snippets/standard/datetime/json/datetime-converter-examples/example2/Program.cs)]

> [!NOTE]
> "R" 標準形式の長さは常に29文字です。

### <a name="using-datetimeoffsetparse-as-a-fallback-to-the-serializers-native-parsing"></a>シリアライザー `DateTime(Offset).Parse`のネイティブ解析へのフォールバックとしての使用

通常、入力<xref:System.DateTime>または<xref:System.DateTimeOffset>データが拡張 ISO 8601-1:2019 プロファイルに準拠していることが予想される場合は、シリアライザーのネイティブ解析ロジックを使用できます。 また、場合によっては、フォールバックメカニズムを実装することもできます。
この例では、を使用して<xref:System.DateTime> <xref:System.Text.Json.Utf8JsonReader.TryGetDateTime(System.DateTime@)>テキスト表現の解析に失敗した後に、コンバーター <xref:System.DateTime.Parse(System.String)>がを使用してデータを正常に解析することを示しています。

[!code-csharp[example-showing-datetime-parse-as-fallback](~/samples/snippets/standard/datetime/json/datetime-converter-examples/example3/Program.cs)]

## <a name="the-extended-iso-8601-12019-profile-in-systemtextjson"></a>System.string の拡張された ISO 8601-1:2019 プロファイル

### <a name="date-and-time-components"></a>日付と時刻のコンポーネント

で<xref:System.Text.Json>実装されている拡張 ISO 8601-1:2019 プロファイルは、日付と時刻の表現に関して次のコンポーネントを定義します。 これらのコンポーネントは、解析と書式設定<xref:System.DateTime>および<xref:System.DateTimeOffset>表現の際にサポートされるさまざまな粒度レベルを定義するために使用されます。

| コンポーネント       | Format                      | 説明                                                                     |
|-----------------|-----------------------------|---------------------------------------------------------------------------------|
| Year            | "yyyy"                      | 0001-9999                                                                       |
| Month           | "MM"                        | 01-12                                                                           |
| Day             | "dd"                        | 01-28、01-29、01-30、01-31 (月/年)                                  |
| Hour            | "HH"                        | 00-23                                                                           |
| Minute          | "mm"                        | 00-59                                                                           |
| Second          | "ss"                        | 00-59                                                                           |
| 2番目の分数 | "FFFFFFF"                   | 最低1桁、最大16桁                                      |
| 時間のオフセット     | "K"                         | "Z" または "(' + '/'-') HH ': ' mm '                                                |
| 部分的な時間    | "HH ': ' mm ': ' ss [FFFFFFF]"     | UTC オフセット情報なしの時間                                             |
| 完全な日付       | "yyyy'-'mm'-'dd't'hh-' MM'-' dd"            | カレンダーの日付                                                                   |
| フルタイム       | "Partial time'K"           | 現地時刻と UTC の時差を使用した日の UTC または現地時刻 |
| 日付/時刻       | "' 完全な日付 ' ' ' ' ' ' ' は完全な時刻 '" になります。 | カレンダーの日付と時刻。例: 2019-07-26T16:59:57-05:00                   |

### <a name="support-for-parsing"></a>解析のサポート

解析のために次の粒度のレベルが定義されています。

1. ' 完全な日付 '
    1. "yyyy'-'mm'-'dd't'hh-' MM'-' dd"

2. "' Full date ' ' ' Hour ' ': ' ' Minute '"
    1. "yyyy'-'mm'-'dd't'hh-' MM'-' + ': ' MM '

3. "' 完全な日付 ' t ' ' Partial time '"
    1. "yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' MM ': ' ss ' ([並べ替え可能な (" s ") 書式指定子](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))
    2. "yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' MM ': ' ss '. 'FFFFFFF

4. "' Full date ' ' ' Time Time ' ': ' ' Minute ' ' Time offset '"
    1. "yyyy'-'mm'-'dd't'hh-" MM'-' Dd' T' HH ': ' mmZ "
    2. "yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' Hh ': ' mm (' + '/'-') HH ': ' mm '

5. ' 日時 '
    1. "yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' MM ': ' ssZ '
    2. "yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' MM ': ' ss '. 'FFFFFFFZ "
    3. "yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' mm ': ' ss (' + '/'-') HH ': ' mm '
    4. "yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' MM ': ' ss '. 'FFFFFFF (' + '/'-') HH ': ' mm "

秒の小数部がある場合は、少なくとも1つの数字が必要です。`2019-07-26T00:00:00.`は使用できません。
最大16桁の小数部を使用できますが、最初の7だけが解析されます。 それを超えるものはゼロと見なされます。
たとえば、 `2019-07-26T00:00:00.1234567890`はのよう`2019-07-26T00:00:00.1234567`に解析されます。
これは、この解決に限定<xref:System.DateTime>された実装との互換性を維持するためのものです。

うるう秒はサポートされていません。

### <a name="support-for-formatting"></a>書式設定のサポート

次の粒度レベルは、書式設定のために定義されています。

1. "' 完全な日付 ' t ' ' Partial time '"
    1. "yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' MM ': ' ss ' ([並べ替え可能な (" s ") 書式指定子](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))

        秒の小数部<xref:System.DateTime>を含まない、オフセット情報を使用せずに、を書式設定するために使用します。

    2. "yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' MM ': ' ss '. 'FFFFFFF

        秒の小数部<xref:System.DateTime>のオフセット情報を使用せずに、を書式設定するために使用します。

2. ' 日時 '
    1. "yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' MM ': ' ssZ '

        秒の小数部<xref:System.DateTime>を<xref:System.DateTimeOffset>含まないか、UTC オフセットを使用して、またはの書式を設定するために使用します。

    2. "yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' MM ': ' ss '. 'FFFFFFFZ "

        秒の小数部<xref:System.DateTime>と<xref:System.DateTimeOffset> UTC オフセットを使用して、またはの書式を設定するために使用します。

    3. "yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' mm ': ' ss (' + '/'-') HH ': ' mm '

        秒の小数部<xref:System.DateTime>を<xref:System.DateTimeOffset>含まない、またはローカルオフセットを使用して、またはの書式を設定するために使用します。

    4. "yyyy'-'mm'-'dd't'hh-' MM'-' Dd' T' HH ': ' MM ': ' ss '. 'FFFFFFF (' + '/'-') HH ': ' mm "

        秒の小数部<xref:System.DateTime>と<xref:System.DateTimeOffset>ローカルオフセットを使用して、またはの書式を設定するために使用します。
