---
title: からNewtonsoft.Json.NET へのSystem.Text.Json移行
author: tdykstra
ms.author: tdykstra
no-loc:
- System.Text.Json
- Newtonsoft.Json
ms.date: 01/10/2020
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 957bafcdf69d5792702962db6598458a0c8ec974
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291568"
---
# <a name="how-to-migrate-from-newtonsoftjson-to-systemtextjson"></a>Newtonsoft. Json から System.Text.Json に移行する方法

この記事では[、Newtonsoft.Json](https://www.newtonsoft.com/json)から に<xref:System.Text.Json>移行する方法について説明します。

名前空間`System.Text.Json`は、JavaScript オブジェクト表記 (JSON) へのシリアル化および逆シリアル化の機能を提供します。 ライブラリ`System.Text.Json`は[.NET Core 3.0](https://aka.ms/netcore3download)の共有フレームワークに含まれています。 他のターゲット フレームワークの場合は、[パッケージ](https://www.nuget.org/packages/System.Text.Json)をインストールします。 パッケージは次の機能をサポートしています。

* .NET 標準 2.0 以降のバージョン
* .NET Framework 4.7.2 以降のバージョン
* NET コア 2.0、2.1、および 2.2

`System.Text.Json`は、主にパフォーマンス、セキュリティ、標準準拠に重点を置いています。 既定の動作にはいくつかの重要な違いがあり、機能のパリティを持つことを`Newtonsoft.Json`目的としていません。 一部のシナリオでは`System.Text.Json`、組み込みの機能はありませんが、推奨される回避策があります。 その他のシナリオでは、回避策は実用的ではありません。 アプリケーションが欠落している機能に依存している場合は、[シナリオのサポートを](https://github.com/dotnet/runtime/issues/new)追加できるかどうかを調べるために問題を報告することを検討してください。

<!-- For information about which features might be added in future releases, see the [Roadmap](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md). [Restore this when the roadmap is updated.]-->

この記事<xref:System.Text.Json.JsonSerializer>のほとんどは、API の使用方法について説明しますが<xref:System.Text.Json.JsonDocument>、(ドキュメント オブジェクト モデルまたは DOM を表す)、<xref:System.Text.Json.Utf8JsonReader>および<xref:System.Text.Json.Utf8JsonWriter>型の使用方法に関するガイダンスも含まれています。

## <a name="table-of-differences-between-newtonsoftjson-and-systemtextjson"></a>ニュートンソフト.Jsonとシステム.Text.Jsonの違いの表

次の表に`Newtonsoft.Json`、機能`System.Text.Json`と同等の機能を示します。 同等の項目は、次のカテゴリに分類されます。

* 組み込み機能によってサポートされます。 類似した動作を`System.Text.Json`取得するには、属性またはグローバル オプションを使用する必要があります。
* サポートされていない場合は、回避策が可能です。 回避策はカスタム[コンバータで、](system-text-json-converters-how-to.md)機能と`Newtonsoft.Json`完全に同等の機能を提供しない場合があります。 これらの一部については、サンプル コードを例として提供します。 これらの`Newtonsoft.Json`機能に依存している場合、移行には .NET オブジェクト モデルの変更またはその他のコードの変更が必要になります。
* サポートされていない場合、回避策は実用的または可能ではありません。 これらの`Newtonsoft.Json`機能に依存している場合、移行は大きな変更なしには不可能です。

| ニュートンソフト.Json 機能                               | 同等の値 |
|-------------------------------------------------------|-----------------------------|
| 既定で大文字と小文字を区別しない逆シリアル化           | ✔️[プロパティ名大文字小文字を区別しないグローバル設定](#case-insensitive-deserialization) |
| キャメル ケース プロパティ名                             | [✔️ プロパティ名ポリシーグローバル設定](system-text-json-how-to.md#use-camel-case-for-all-json-property-names) |
| 最小限の文字エスケープ                            | ✔️[厳密な文字エスケープ、構成可能](#minimal-character-escaping) |
| `NullValueHandling.Ignore`グローバル設定             | [✔️Null 値グローバル オプションを無視します。](system-text-json-how-to.md#exclude-all-null-value-properties) |
| コメントを許可する                                        | [✔️読み取りコメント処理グローバル設定](#comments) |
| 末尾のカンマを許可する                                 | ✔️[トレーリングコンマグローバル設定を許可します。](#trailing-commas) |
| カスタム コンバータ登録                         | ✔️[優先順位が異なります](#converter-registration-precedence) |
| 既定では最大の深さなし                           | ✔️[デフォルトの最大深さ 64、構成可能](#maximum-depth) |
| 幅広いタイプのサポート                    | ⚠️[一部の型にはカスタム コンバータが必要です](#types-without-built-in-support) |
| 文字列を数値として逆シリアル化する                        | ⚠️[サポートされていない、回避策、サンプル](#quoted-numbers) |
| 非文字列キー`Dictionary`を使用して逆シリアル化する          | ⚠️[サポートされていない、回避策、サンプル](#dictionary-with-non-string-key) |
| 多型シリアル化                             | ⚠️[サポートされていない、回避策、サンプル](#polymorphic-serialization) |
| 多型逆シリアル化                           | ⚠️[サポートされていない、回避策、サンプル](#polymorphic-deserialization) |
| 推論された型をプロパティに逆シリアル`object`化する      | ⚠️[サポートされていない、回避策、サンプル](#deserialization-of-object-properties) |
| JSON`null`リテラルを null 非許容値型に逆シリアル化する | ⚠️[サポートされていない、回避策、サンプル](#deserialize-null-to-non-nullable-type) |
| 変更できないクラスと構造体への逆シリアル化          | ⚠️[サポートされていない、回避策、サンプル](#deserialize-to-immutable-classes-and-structs) |
| `[JsonConstructor]` 属性                         | ⚠️[サポートされていない、回避策、サンプル](#specify-constructor-to-use) |
| `Required`属性の`[JsonProperty]`設定        | ⚠️[サポートされていない、回避策、サンプル](#required-properties) |
| `NullValueHandling`属性の`[JsonProperty]`設定 | ⚠️[サポートされていない、回避策、サンプル](#conditionally-ignore-a-property)  |
| `DefaultValueHandling`属性の`[JsonProperty]`設定 | ⚠️[サポートされていない、回避策、サンプル](#conditionally-ignore-a-property)  |
| `DefaultValueHandling`グローバル設定                 | ⚠️[サポートされていない、回避策、サンプル](#conditionally-ignore-a-property) |
| `DefaultContractResolver`プロパティを除外する       | ⚠️[サポートされていない、回避策、サンプル](#conditionally-ignore-a-property) |
| `DateTimeZoneHandling`、`DateFormatString`設定   | ⚠️[サポートされていない、回避策、サンプル](#specify-date-format) |
| コールバック                                             | ⚠️[サポートされていない、回避策、サンプル](#callbacks) |
| パブリック フィールドと非パブリック フィールドのサポート              | ⚠️[サポートされていない、回避策](#public-and-non-public-fields) |
| 内部およびプライベート プロパティのセッターとゲッターのサポート | ⚠️[サポートされていない、回避策](#internal-and-private-property-setters-and-getters) |
| `JsonConvert.PopulateObject` メソッド                   | ⚠️[サポートされていない、回避策](#populate-existing-objects) |
| `ObjectCreationHandling`グローバル設定               | ⚠️[サポートされていない、回避策](#reuse-rather-than-replace-properties) |
| セッターを使用せずにコレクションに追加する                    | ⚠️[サポートされていない、回避策](#add-to-collections-without-setters) |
| `PreserveReferencesHandling`グローバル設定           | ❌[サポートされていません](#preserve-object-references-and-handle-loops) |
| `ReferenceLoopHandling`グローバル設定                | ❌[サポートされていません](#preserve-object-references-and-handle-loops) |
| 属性の`System.Runtime.Serialization`サポート | ❌[サポートされていません](#systemruntimeserialization-attributes) |
| `MissingMemberHandling`グローバル設定                | ❌[サポートされていません](#missingmemberhandling) |
| 引用符を付けずにプロパティ名を許可する                   | ❌[サポートされていません](#json-strings-property-names-and-string-values) |
| 文字列値の前後に単一引用符を使用できるようにする              | ❌[サポートされていません](#json-strings-property-names-and-string-values) |
| 文字列プロパティに文字列以外の JSON 値を許可する    | ❌[サポートされていません](#non-string-values-for-string-properties) |

これは、機能の`Newtonsoft.Json`完全なリストではありません。 このリストには[、GitHub](https://github.com/dotnet/runtime/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json)の問題または[StackOverflow](https://stackoverflow.com/questions/tagged/system.text.json)投稿で要求された多くのシナリオが含まれています。 現在サンプル コードを持たないシナリオの 1 つに回避策を実装し、ソリューションを共有する場合は、このページの[[フィードバック](/dotnet/standard/serialization/system-text-json-migrate-from-newtonsoft-how-to#feedback)] セクションでこの**ページ**を選択します。 これにより GitHub の問題が作成され、このページの下部に一覧表示されます。

## <a name="differences-in-default-jsonserializer-behavior-compared-to-newtonsoftjson"></a>ニュートンソフト.Jsonとの既定の JsonSerializer 動作の違い

<xref:System.Text.Json>は、既定では厳密であり、決定論的な動作を強調して、呼び出し元に代わって推測や解釈を回避します。 このライブラリは、パフォーマンスとセキュリティのために意図的にこの方法で設計されています。 `Newtonsoft.Json`デフォルトでは柔軟性があります。 設計におけるこの根本的な違いは、デフォルトの動作における以下の特定の違いの多くの背景にあります。

### <a name="case-insensitive-deserialization"></a>大文字と小文字を区別しない逆シリアル化

逆シリアル化中`Newtonsoft.Json`に、既定で、大文字と小文字を区別しないプロパティ名の一致を行います。 デフォルト<xref:System.Text.Json>では大文字と小文字が区別され、完全一致を行うため、パフォーマンスが向上します。 大文字と小文字を区別しない一致を実行する方法については、「大文字と小文字を[区別しないプロパティの一致](system-text-json-how-to.md#case-insensitive-property-matching)」を参照してください。

ASP.NET Core を`System.Text.Json`使用して間接的に使用している場合は、 のような`Newtonsoft.Json`動作を得るために何もする必要はありません。 ASP.NET Core では、[キャメル 大文字/小文字を区別するプロパティ名](system-text-json-how-to.md#use-camel-case-for-all-json-property-names)と、使用時の`System.Text.Json`大文字と小文字を区別しない一致の設定を指定します。

### <a name="minimal-character-escaping"></a>最小限の文字エスケープ

シリアル化の`Newtonsoft.Json`際、文字をエスケープせずに使用させることは比較的許容されます。 つまり、文字のコード ポイントの場所`\uxxxx``xxxx`に置き換えるわけではありません。 エスケープする場合は、文字の前に a を`\`出力します (たとえば、 `"` `\"`になります)。 <xref:System.Text.Json>デフォルトでは、クロスサイト スクリプティング (XSS) 攻撃や情報漏えい攻撃に対する多層防御保護を提供するために、より多くの文字をエスケープし、6 文字のシーケンスを使用してエスケープします。 `System.Text.Json`は、デフォルトで非 ASCII 文字をすべてエスケープするので、 で`StringEscapeHandling.EscapeNonAscii``Newtonsoft.Json`使用している場合は何もする必要はありません。 `System.Text.Json`また、デフォルトでは HTML に依存する文字もエスケープされます。 既定`System.Text.Json`の動作をオーバーライドする方法については、「[文字エンコードのカスタマイズ](system-text-json-how-to.md#customize-character-encoding)」を参照してください。

### <a name="comments"></a>説明

逆シリアル化中`Newtonsoft.Json`は、既定で JSON 内のコメントを無視します。 デフォルト<xref:System.Text.Json>では[、RFC 8259](https://tools.ietf.org/html/rfc8259)仕様に例外が含まれていないため、コメントの例外がスローされます。 コメントを許可する方法については、「[コメントと末尾のカンマを許可する](system-text-json-how-to.md#allow-comments-and-trailing-commas)」を参照してください。

### <a name="trailing-commas"></a>末尾のコンマ

逆シリアル化中`Newtonsoft.Json`は、既定で末尾のコンマは無視されます。 また、複数の後続のコンマも無視されます (`[{"Color":"Red"},{"Color":"Green"},,]`たとえば、 )。 デフォルト<xref:System.Text.Json>では[、RFC 8259](https://tools.ietf.org/html/rfc8259)仕様では例外が許可されていないため、末尾のコンマに対して例外がスローされます。 それらを`System.Text.Json`受け入れる方法については、「[コメントと末尾のカンマを許可する](system-text-json-how-to.md#allow-comments-and-trailing-commas)」を参照してください。 複数の後続のカンマを許可する方法はありません。

### <a name="converter-registration-precedence"></a>コンバータの登録優先順位

カスタム`Newtonsoft.Json`コンバーターの登録優先順位は次のとおりです。

* プロパティの属性
* タイプの属性
* [コンバータコレクション](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonSerializerSettings_Converters.htm)

この順序は、`Converters`コレクション内のカスタム コンバーターが、型レベルで属性を適用することによって登録されたコンバーターによってオーバーライドされることを意味します。 これらの登録は、プロパティ レベルの属性によってオーバーライドされます。

カスタム<xref:System.Text.Json>コンバーターの登録優先順位は異なります。

* プロパティの属性
* <xref:System.Text.Json.JsonSerializerOptions.Converters>コレクション
* タイプの属性

ここでの違いは、コレクション内のカスタム`Converters`コンバーターが型レベルで属性をオーバーライドすることです。 この優先順位の背後にある意図は、実行時の変更をデザイン時の選択よりも優先することです。 優先順位を変更する方法はありません。

カスタム コンバータ登録の詳細については、「カスタム コンバータ[の登録](system-text-json-converters-how-to.md#register-a-custom-converter)」を参照してください。

### <a name="maximum-depth"></a>最大深度

`Newtonsoft.Json`デフォルトでは、最大深度制限はありません。 既定<xref:System.Text.Json>の制限は 64 で、設定で構成できます<xref:System.Text.Json.JsonSerializerOptions.MaxDepth?displayProperty=nameWithType>。

### <a name="json-strings-property-names-and-string-values"></a>JSON 文字列 (プロパティ名と文字列値)

逆シリアル化中`Newtonsoft.Json`は、二重引用符、一重引用符、または引用符なしで囲まれたプロパティ名を受け入れます。 二重引用符または単一引用符で囲まれた文字列値を受け入れます。 たとえば、`Newtonsoft.Json`次の JSON を受け入れます。

```json
{
  "name1": "value",
  'name2': "value",
  name3: 'value'
}
```

`System.Text.Json`[RFC 8259](https://tools.ietf.org/html/rfc8259)仕様では、その形式が必要であり、有効な JSON と見なされる唯一の形式であるため、プロパティ名と文字列値は二重引用符で囲まれます。

単一引用符で囲まれた値は、次のメッセージを伴う[JsonException](xref:System.Text.Json.JsonException)になります。

```
''' is an invalid start of a value.
```

### <a name="non-string-values-for-string-properties"></a>文字列プロパティの非文字列値

`Newtonsoft.Json`文字列型のプロパティへの逆シリアル化には、数値やリテラルなどの非`true`文字列`false`値を受け入れます。 次のクラスに正常に逆シリアル`Newtonsoft.Json`化する JSON の例を次に示します。

```json
{
  "String1": 1,
  "String2": true,
  "String3": false
}
```

```csharp
public class ExampleClass
{
    public string String1 { get; set; }
    public string String2 { get; set; }
    public string String3 { get; set; }
}
```

`System.Text.Json`文字列以外の値を文字列プロパティに逆シリアル化しません。 文字列フィールドに対して受信された文字列以外の値は、次のメッセージを伴う[JsonException](xref:System.Text.Json.JsonException)になります。

```
The JSON value could not be converted to System.String.
```

## <a name="scenarios-using-jsonserializer-that-require-workarounds"></a>回避策を必要とする JsonSerializer を使用するシナリオ

次のシナリオは組み込み機能ではサポートされていませんが、回避策は可能です。 回避策はカスタム[コンバータで、](system-text-json-converters-how-to.md)機能と`Newtonsoft.Json`完全に同等の機能を提供しない場合があります。 これらの一部については、サンプル コードを例として提供します。 これらの`Newtonsoft.Json`機能に依存している場合、移行には .NET オブジェクト モデルの変更またはその他のコードの変更が必要になります。

### <a name="types-without-built-in-support"></a>組み込みサポートなしの型

<xref:System.Text.Json>では、次の型に対する組み込みのサポートは提供されません。

* <xref:System.Data.DataTable>および関連するタイプ
* F# 型 ([判別共用体](../../fsharp/language-reference/discriminated-unions.md)、[レコードの種類](../../fsharp/language-reference/records.md)、[匿名レコードの種類](../../fsharp/language-reference/anonymous-records.md)など ) 。
* <xref:System.Dynamic.ExpandoObject>
* <xref:System.TimeZoneInfo>
* <xref:System.Numerics.BigInteger>
* <xref:System.TimeSpan>
* <xref:System.DBNull>
* <xref:System.Type>
* <xref:System.ValueTuple>および関連付けられているジェネリック型

組み込みサポートを持たない型に対してカスタム コンバーターを実装できます。

### <a name="quoted-numbers"></a>引用符で囲まれた数字

`Newtonsoft.Json`JSON 文字列で表される数値をシリアル化または逆シリアル化できます (引用符で囲まれています)。 たとえば、 の代わりに`{"DegreesCelsius":"23"}`を受`{"DegreesCelsius":23}`け入れることができます。 で動作を有効にするには<xref:System.Text.Json>、次の例のようなカスタム コンバーターを実装します。 コンバーターは、 として定義`long`されたプロパティを処理します。

* それらを JSON 文字列としてシリアル化します。
* 逆シリアル化中に引用符内の JSON 番号と数値を受け入れます。

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/LongToStringConverter.cs)]

このカスタム コンバーターを登録するには`long`、個々のプロパティの[属性を使用](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-property)するか[、](system-text-json-converters-how-to.md#registration-sample---converters-collection)<xref:System.Text.Json.JsonSerializerOptions.Converters>またはコレクションにコンバーターを追加します。

### <a name="dictionary-with-non-string-key"></a>文字列以外のキーを持つディクショナリ

`Newtonsoft.Json`型のコレクションをサポート`Dictionary<TKey, TValue>`しています。 の辞書コレクションの組み込みサポート<xref:System.Text.Json>は に限定`Dictionary<string, TValue>`されます。 つまり、キーは文字列である必要があります。

整数または他の型をキーとして使用するディクショナリをサポートするには、「カスタム コンバータ[を記述する方法](system-text-json-converters-how-to.md#support-dictionary-with-non-string-key)」の例のようなコンバータを作成します。

### <a name="polymorphic-serialization"></a>多型シリアル化

`Newtonsoft.Json`自動的にポリモーフィックなシリアル化を行います。 の限定ポリモーフィックシリアル化機能の詳細については<xref:System.Text.Json>、「[派生クラスのプロパティのシリアル化](system-text-json-how-to.md#serialize-properties-of-derived-classes)」を参照してください。

ここで説明する回避策は、派生クラスを含むプロパティを type`object`として定義することです。 それが不可能な場合は、「カスタム コンバータを記述する方法」の例`Write`のように、継承型階層全体のメソッド[を使用してコンバータを作成する方法があります](system-text-json-converters-how-to.md#support-polymorphic-deserialization)。

### <a name="polymorphic-deserialization"></a>多型逆シリアル化

`Newtonsoft.Json`には、`TypeNameHandling`シリアル化中に型名メタデータを JSON に追加する設定があります。 逆シリアル化中にメタデータを使用して、ポリモーフィック逆シリアル化を実行します。 <xref:System.Text.Json>[ポリモーフィックなシリアル化](system-text-json-how-to.md#serialize-properties-of-derived-classes)の範囲は限られていますが、多型逆シリアル化はできません。

ポリモーフィック逆シリアル化をサポートするには、「カスタム コンバータ[を記述する方法](system-text-json-converters-how-to.md#support-polymorphic-deserialization)」の例のようなコンバータを作成します。

### <a name="deserialization-of-object-properties"></a>オブジェクト プロパティの逆シリアル化

に`Newtonsoft.Json`<xref:System.Object>逆シリアル化すると、次のようになります。

* JSON ペイロード内のプリミティブ値の型 (`null`以外) を推論し、格納されている`string` `long`、 `double` `boolean`、 `DateTime` 、または 、ボックス化されたオブジェクトとして返します。 *プリミティブ値*は、JSON 番号、文字列`true`、、、、、、、、`null``false`などの単一の JSON 値です。
* JSON`JObject`ペイロード`JArray`内の複雑な値の or を返します。 *複合値*は、中かっこ ( )`{}`内の JSON キーと値のペアの集合、`[]`または角かっこ内の値のリスト ( ) です。 中かっこまたは角かっこ内のプロパティと値には、追加のプロパティまたは値を含めることができます。
* ペイロードに JSON リテラルがある場合に`null`null 参照を返します。

<xref:System.Text.Json>に逆シリアル化`JsonElement`するたびに、プリミティブ値と複合値の両方に<xref:System.Object>ボックス化されたボックスを格納します。

* `object` プロパティ。
* ディクショナリ`object`値。
* 配列`object`の値。
* ルート`object`.

ただし、`System.Text.Json`ペイロード`null`に JSON`Newtonsoft.Json`リテラルが含まれる場合は、同じ`null`ものを扱い、null 参照を返します。

`object`プロパティの型の推論を実装するには、「カスタム コンバータを[記述する方法](system-text-json-converters-how-to.md#deserialize-inferred-types-to-object-properties)」の例のようなコンバータを作成します。

### <a name="deserialize-null-to-non-nullable-type"></a>null を null 非許容型に逆シリアル化する

`Newtonsoft.Json`次のシナリオでは例外はスローされません。

* `NullValueHandling`は に`Ignore`設定され、
* 逆シリアル化中、JSON には null 非許容値型の null 値が含まれます。

同じシナリオでは、<xref:System.Text.Json>例外をスローします。 (対応する NULL 処理設定<xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType>は .)

ターゲット型を所有している場合、最適な回避策は、問題のプロパティを null 可能にすることです (`int`たとえば`int?`、 に変更します)。

もう 1 つの回避策は、型の null 値を処理する次の例のように`DateTimeOffset`、型のコンバーターを作成することです。

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DateTimeOffsetNullHandlingConverter.cs)]

このカスタム コンバーターを登録するには[、プロパティの属性を使用するか、](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-property)<xref:System.Text.Json.JsonSerializerOptions.Converters>[またはコレクションにコンバーターを追加](system-text-json-converters-how-to.md#registration-sample---converters-collection)します。

**注:** 上記のコンバーターは、既定値を指定する`Newtonsoft.Json`POKO の**場合とは異なる方法で NULL**値を処理します。 たとえば、次のコードがターゲット オブジェクトを表しているとします。

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

上記のコンバータを使用して、次の JSON を逆シリアル化するとします。

```json
{
  "Date": null,
  "TemperatureCelsius": 25,
  "Summary": null
}
```

逆シリアル化の`Date`後、プロパティは 1/1/0001 (`default(DateTimeOffset)`) 、つまり、コンストラクターに設定された値が上書きされます。 同じ POCO と`Newtonsoft.Json`JSON を指定すると、逆シリアル化は 2001/1/1/2001 をプロパティに`Date`残します。

### <a name="deserialize-to-immutable-classes-and-structs"></a>変更できないクラスと構造体への逆シリアル化

`Newtonsoft.Json`パラメーターを持つコンストラクターを使用できるため、変更できないクラスおよび構造体に逆シリアル化できます。 <xref:System.Text.Json>は、パブリックなパラメーターなしのコンストラクターのみをサポートします。 回避策として、カスタム コンバータのパラメータを持つコンストラクタを呼び出すことができます。

複数のコンストラクタパラメータを持つ変更できない構造体を次に示します。

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ImmutablePoint.cs#ImmutablePoint)]

次に、この構造体をシリアル化および逆シリアル化するコンバータを示します。

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ImmutablePointConverter.cs)]

このカスタム コンバーター[をコレクションに追加](system-text-json-converters-how-to.md#registration-sample---converters-collection)して登録します。 <xref:System.Text.Json.JsonSerializerOptions.Converters>

オープンジェネリック プロパティを処理する同様のコンバータの例については、[組み込みのキーと値のペアを](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/JsonValueConverterKeyValuePair.cs)参照してください。

### <a name="specify-constructor-to-use"></a>使用するコンストラクタを指定する

属性`Newtonsoft.Json``[JsonConstructor]`を使用すると、POCO に逆シリアル化するときに呼び出すコンストラクターを指定できます。 <xref:System.Text.Json>はパラメーターなしのコンストラクターのみをサポートします。 回避策として、カスタム コンバーターで必要なコンストラクターを呼び出すことができます。 「[変更できないクラスと構造体への逆シリアル化](#deserialize-to-immutable-classes-and-structs)」の例を参照してください。

### <a name="required-properties"></a>必須プロパティ

では`Newtonsoft.Json`、属性を設定`Required`してプロパティが必要であることを指定します。 `[JsonProperty]` `Newtonsoft.Json`必要とマークされたプロパティの値が JSON で受信されない場合は、例外がスローされます。

<xref:System.Text.Json>ターゲット型のプロパティの 1 つに値が受け取られない場合は、例外をスローしません。 たとえば、クラスがある場合は、`WeatherForecast`次のようになります。

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

次の JSON はエラーなしで逆シリアル化されます。

```json
{
    "TemperatureCelsius": 25,
    "Summary": "Hot"
}
```

JSON にプロパティがない`Date`場合に逆シリアル化が失敗するようにするには、カスタム コンバーターを実装します。 次のサンプル コンバータ コードは、逆シリアル`Date`化の完了後にプロパティが設定されていない場合に例外をスローします。

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastRequiredPropertyConverter.cs)]

[POCO クラスの属性を使用するか、](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type)またはコレクションに[コンバーターを追加](system-text-json-converters-how-to.md#registration-sample---converters-collection)して、このカスタム<xref:System.Text.Json.JsonSerializerOptions.Converters>コンバーターを登録します。

このパターンに従う場合は、再帰的にまたは<xref:System.Text.Json.JsonSerializer.Serialize%2A><xref:System.Text.Json.JsonSerializer.Deserialize%2A>を呼び出すときに options オブジェクトを渡さないでください。 options オブジェクトには、<xref:System.Text.Json.JsonSerializerOptions.Converters%2A>コレクションが含まれています。 または に`Serialize``Deserialize`渡すと、カスタム コンバーターがそれ自体を呼び出し、スタック オーバーフロー例外を発生させる無限ループを作成します。 デフォルトのオプションが実現できない場合は、必要な設定でオプションの新しいインスタンスを作成します。 この方法は、新しいインスタンスが個別にキャッシュされるため、遅くなります。

上記のコンバーター コードは、簡略化された例です。 属性[([JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute)や異なるオプション (カスタム エンコーダーなど) を処理する必要がある場合は、追加のロジックが必要になります。 また、このコード例では、コンストラクターで既定値が設定されているプロパティは処理されません。 この方法では、次のシナリオが区別されません。

* JSON にプロパティがありません。
* NULL 非許容型のプロパティは JSON に存在しますが、値は型の既定値です`int`( の場合は 0 など)。
* NULL 許容値型のプロパティが JSON に存在しますが、値は null です。

### <a name="conditionally-ignore-a-property"></a>プロパティを条件付きで無視する

`Newtonsoft.Json`では、シリアル化または逆シリアル化のプロパティを条件付きで無視する方法がいくつかあります。

* `DefaultContractResolver`を使用して、任意の条件に基づいて、含めるまたは除外するプロパティを選択できます。
* の`NullValueHandling`設定`DefaultValueHandling`と設定`JsonSerializerSettings`では、すべての null 値または既定値のプロパティを無視する必要があることを指定できます。
* 属性`NullValueHandling`の`DefaultValueHandling`と`[JsonProperty]`の設定を使用すると、null または既定値に設定した場合に無視する必要がある個々のプロパティを指定できます。

<xref:System.Text.Json>では、シリアル化中にプロパティを省略する次の方法が用意されています。

* プロパティの[[JsonIgnore]](system-text-json-how-to.md#exclude-individual-properties)属性を使用すると、シリアル化中に JSON からプロパティが省略されます。
* [IgnoreNullValues](system-text-json-how-to.md#exclude-all-null-value-properties)グローバル オプションを使用すると、すべての null 値プロパティを除外できます。
* [[IgnoreReadOnlyProperties]](system-text-json-how-to.md#exclude-all-read-only-properties)グローバル オプションを使用すると、すべての読み取り専用プロパティを除外できます。

これらのオプション**では、次の機能は使用できません**。

* 型の既定値を持つすべてのプロパティを無視します。
* 型の既定値を持つ選択したプロパティを無視します。
* 選択したプロパティの値が null の場合は無視します。
* 実行時に評価された任意の条件に基づいて、選択したプロパティを無視します。

この機能を使用するために、カスタム コンバータを作成できます。 POCO のサンプルと、このアプローチを示すカスタム コンバーターを次に示します。

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastRuntimeIgnoreConverter.cs)]

値が null、空の`Summary`文字列、または "N/A" の場合、プロパティはシリアル化から省略されます。

[クラスの属性を使用するか、](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type)またはコレクションに[コンバーターを追加](system-text-json-converters-how-to.md#registration-sample---converters-collection)して、このカスタム<xref:System.Text.Json.JsonSerializerOptions.Converters>コンバーターを登録します。

このアプローチでは、次の場合に追加のロジックが必要になります。

* POCO には、複雑なプロパティが含まれています。
* カスタム エンコーダーなどの`[JsonIgnore]`属性やオプションを処理する必要があります。

### <a name="specify-date-format"></a>日付形式の指定

`Newtonsoft.Json`では、プロパティおよび型の`DateTime`シリアル化および`DateTimeOffset`逆シリアル化方法を制御する方法がいくつか用意されています。

* この`DateTimeZoneHandling`設定を使用して、すべての`DateTime`値を UTC 日付としてシリアル化できます。
* 設定`DateFormatString`と`DateTime`コンバータを使用して、日付文字列の書式をカスタマイズできます。

で<xref:System.Text.Json>、組み込みのサポートを持っている唯一の形式は、広く採用され、明確に、そして正確にラウンド トリップを行うため、ISO 8601-1:2019 です。 その他の形式を使用するには、カスタム コンバータを作成します。 詳細については、「[システム.Text.Json の日時と日時オフセットのサポート](../datetime/system-text-json-support.md)」を参照してください。

### <a name="callbacks"></a>コールバック

`Newtonsoft.Json`では、シリアル化または逆シリアル化プロセスのいくつかのポイントでカスタム コードを実行できます。

* OnDeserializing (オブジェクトの逆シリアル化を開始するとき)
* OnDeserialized (オブジェクトの逆シリアル化が完了した場合)
* OnSerializing (オブジェクトのシリアル化を開始するとき)
* OnSerialized (オブジェクトのシリアル化が完了したとき)

では<xref:System.Text.Json>、カスタム コンバータを記述してコールバックをシミュレートできます。 POCO のカスタム コンバーターの例を次に示します。 コンバーターには、コールバックに対応する各ポイントにメッセージを表示するコードが`Newtonsoft.Json`含まれています。

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastCallbacksConverter.cs)]

[クラスの属性を使用するか、](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type)またはコレクションに[コンバーターを追加](system-text-json-converters-how-to.md#registration-sample---converters-collection)して、このカスタム<xref:System.Text.Json.JsonSerializerOptions.Converters>コンバーターを登録します。

上記のサンプルに従ってカスタム コンバーターを使用する場合:

* コード`OnDeserializing`は、新しい POCO インスタンスにアクセスできません。 逆シリアル化の開始時に新しい POCO インスタンスを操作するには、そのコードを POCO コンストラクターに配置します。
* を再帰的に呼び出すとき`Serialize`に options`Deserialize`オブジェクトを渡さないでください。 options オブジェクトには、`Converters`コレクションが含まれています。 または に`Serialize``Deserialize`渡すと、コンバーターが使用され、無限ループが発生し、スタック オーバーフロー例外が発生します。

### <a name="public-and-non-public-fields"></a>パブリック フィールドと非パブリック フィールド

`Newtonsoft.Json`プロパティだけでなく、フィールドのシリアル化や逆シリアル化もできます。 <xref:System.Text.Json>パブリック プロパティでのみ動作します。 カスタム コンバーターは、この機能を提供できます。

### <a name="internal-and-private-property-setters-and-getters"></a>内部およびプライベート プロパティのセッターとゲッター

`Newtonsoft.Json`属性を使用して、プライベートプロパティと内部プロパティセッターとゲッター`JsonProperty`を使用できます。 <xref:System.Text.Json>は、パブリックセッターのみをサポートします。 カスタム コンバーターは、この機能を提供できます。

### <a name="populate-existing-objects"></a>既存のオブジェクトのデータを作成する

メソッド`JsonConvert.PopulateObject`は、`Newtonsoft.Json`新しいインスタンスを作成する代わりに、JSON ドキュメントをクラスの既存のインスタンスに逆シリアル化します。 <xref:System.Text.Json>既定のパブリック パラメーターなしコンストラクターを使用して、常にターゲット型の新しいインスタンスを作成します。 カスタム コンバーターは、既存のインスタンスに逆シリアル化できます。

### <a name="reuse-rather-than-replace-properties"></a>プロパティを置換するのではなく再利用する

この`Newtonsoft.Json``ObjectCreationHandling`設定では、逆シリアル化中に置き換えるのではなく、プロパティ内のオブジェクトを再利用することを指定できます。 <xref:System.Text.Json>プロパティ内のオブジェクトは常に置き換えられます。  カスタム コンバーターは、この機能を提供できます。

### <a name="add-to-collections-without-setters"></a>セッターを使用せずにコレクションに追加する

逆シリアル化中`Newtonsoft.Json`に、プロパティに setter がない場合でも、コレクションにオブジェクトを追加します。 <xref:System.Text.Json>は、セッターを持たないプロパティを無視します。 カスタム コンバーターは、この機能を提供できます。

## <a name="scenarios-that-jsonserializer-currently-doesnt-support"></a>現在サポートされていないシナリオ

次のシナリオでは、回避策は実用的または可能ではありません。 これらの`Newtonsoft.Json`機能に依存している場合、移行は大きな変更なしには不可能です。

### <a name="preserve-object-references-and-handle-loops"></a>オブジェクト参照を保持し、ループを処理する

既定では、`Newtonsoft.Json`値でシリアル化します。 たとえば、同じ`Person`オブジェクトへの参照を含む 2 つのプロパティがオブジェクトに含まれている場合、`Person`そのオブジェクトのプロパティの値は JSON に複製されます。

`Newtonsoft.Json`には、`PreserveReferencesHandling`参照で`JsonSerializerSettings`シリアル化できる設定があります。

* 最初`Person`のオブジェクトに対して作成された JSON に識別子メタデータが追加されます。
* 2 番目`Person`のオブジェクト用に作成される JSON には、プロパティ値ではなく、その識別子への参照が含まれています。

`Newtonsoft.Json`また、例外`ReferenceLoopHandling`をスローするのではなく、循環参照を無視できる設定もあります。

<xref:System.Text.Json>値によるシリアル化のみをサポートし、循環参照の例外をスローします。

### <a name="systemruntimeserialization-attributes"></a>シリアル化属性

<xref:System.Text.Json>名前空間の`System.Runtime.Serialization`属性 (`DataMemberAttribute`および`IgnoreDataMemberAttribute`など) はサポートされていません。

### <a name="octal-numbers"></a>8 進数

`Newtonsoft.Json`は、先行ゼロの数値を 8 進数として扱います。 <xref:System.Text.Json>[RFC 8259](https://tools.ietf.org/html/rfc8259)仕様では、それらを許可しないため、先行ゼロは許可されません。

### <a name="missingmemberhandling"></a>行方不明のメンバーハンドリング

`Newtonsoft.Json`JSON にターゲット型に存在しないプロパティが含まれている場合は、逆シリアル化中に例外をスローするように構成できます。 <xref:System.Text.Json>[[JsonExtensionData] 属性](system-text-json-how-to.md#handle-overflow-json)を使用する場合を除き、JSON の追加プロパティは無視されます。 メンバーの機能が見つからない場合の回避策はありません。

### <a name="tracewriter"></a>トレースライター

`Newtonsoft.Json`を使用して、シリアル化`TraceWriter`または逆シリアル化によって生成されたログを表示してデバッグできます。 <xref:System.Text.Json>ログを記録しません。

## <a name="jsondocument-and-jsonelement-compared-to-jtoken-like-jobject-jarray"></a>JToken と比較した Json ドキュメントと Json 要素 (JObject、JArray など)

<xref:System.Text.Json.JsonDocument?displayProperty=fullName>には、既存の JSON ペイロードから**読み取り専用**のドキュメント オブジェクト モデル (DOM) を解析および構築する機能が用意されています。 DOM は、JSON ペイロード内のデータへのランダム アクセスを提供します。 ペイロードを構成する JSON 要素には、この型<xref:System.Text.Json.JsonElement>を使用してアクセスできます。 この`JsonElement`型は、JSON テキストを一般的な .NET 型に変換する API を提供します。 `JsonDocument`プロパティを<xref:System.Text.Json.JsonDocument.RootElement>公開します。

### <a name="jsondocument-is-idisposable"></a>Json ドキュメントは破棄可能です

`JsonDocument`では、データのメモリ内ビューがプールされたバッファに構築されます。 したがって、`JObject`または`JArray``Newtonsoft.Json`とは`JsonDocument`異なり、`IDisposable`型は using ブロック内で実装し、使用する必要があります。

有効期間の所有権`JsonDocument`を譲渡し、呼び出し元に責任を破棄する場合にのみ、API から を返します。 ほとんどのシナリオでは、これは必要ありません。 呼び出し元が JSON ドキュメント全体を操作する<xref:System.Text.Json.JsonElement.Clone%2A>必要がある<xref:System.Text.Json.JsonDocument.RootElement%2A>場合は、<xref:System.Text.Json.JsonElement>の を返します。 呼び出し元が JSON ドキュメント内の特定の要素を操作<xref:System.Text.Json.JsonElement.Clone%2A>する必要<xref:System.Text.Json.JsonElement>がある場合は、 の を返します。 または サブ要素`RootElement`を直接返す場合、`Clone`を作成せずに、その要素を所有するが破棄された後に`JsonElement``JsonDocument`返されたにアクセスできません。

次に、作成する必要がある例を示します`Clone`。

```csharp
public JsonElement LookAndLoad(JsonElement source)
{
    string json = File.ReadAllText(source.GetProperty("fileName").GetString());

    using (JsonDocument doc = JsonDocument.Parse(json))
    {
        return doc.RootElement.Clone();
    }
}
```

上記のコードでは、`JsonElement``fileName`プロパティを含む を想定しています。 JSON ファイルを開き、`JsonDocument`を作成します。 このメソッドは、呼び出し元がドキュメント全体を操作することを想定しているので、`Clone`の`RootElement`を返します。

を受け取`JsonElement`り、サブ要素を返す場合は、サブ要素の を`Clone`返す必要はありません。 呼び出し元は、渡`JsonDocument`されたが`JsonElement`属するを維持する責任があります。 次に例を示します。

```csharp
public JsonElement ReturnFileName(JsonElement source)
{
   return source.GetProperty("fileName");
}
```

### <a name="jsondocument-is-read-only"></a>Json ドキュメントは読み取り専用です。

DOM<xref:System.Text.Json>は、JSON 要素を追加、削除、または変更することはできません。 パフォーマンスを向上させ、一般的な JSON ペイロード サイズ (つまり、1 MB) を解析するための割り当てを減らす方法<設計されています。 現在、変更可能な DOM を使用しているシナリオの場合は、次のいずれかの回避策が可能です。

* 最初から構築`JsonDocument`するには (つまり、既存の JSON ペイロードを`Parse`メソッドに渡さずに)、JSON テキストを`Utf8JsonWriter`書き込み、そこから出力を解析して新`JsonDocument`しい .
* 既存`JsonDocument`の を変更するには、それを使用して JSON テキストを書き込み、書き込み中に変更を`JsonDocument`加え、そこから出力を解析して新しい .
* の API`JObject.Merge`と`JContainer.Merge`同等の既存の JSON ドキュメント`Newtonsoft.Json`をマージするには、[この GitHub](https://github.com/dotnet/corefx/issues/42466#issuecomment-570475853)の問題を参照してください。

### <a name="jsonelement-is-a-union-struct"></a>JsonElement は共用体構造体です。

`JsonDocument`は、任意`RootElement`の JSON 要素<xref:System.Text.Json.JsonElement>を包含する共用体構造体型である型のプロパティとして公開します。 `Newtonsoft.Json`では、 、 `JObject`、`JArray``JToken`などの専用の階層型を使用します。 `JsonElement`は、検索および列挙が可能であり、JSON 要素を`JsonElement`.NET 型に具体化するために使用できます。

### <a name="how-to-search-a-jsondocument-and-jsonelement-for-sub-elements"></a>サブ要素の Json ドキュメントと JsonElement を検索する方法

または`JObject``JArray`を使用して JSON`Newtonsoft.Json`トークンを検索する場合、それらはいくつかの辞書で検索されるため、比較的高速になる傾向があります。 これに対して、検索`JsonElement`ではプロパティのシーケンシャル検索が必要になるため、比較的低速です (`TryGetProperty`たとえば、 を使用する場合)。 <xref:System.Text.Json>は、ルックアップ時間ではなく、初期解析時間を最小限に抑えるように設計されています。 したがって、オブジェクトを検索する際のパフォーマンスを最適化するには、次`JsonDocument`の方法を使用します。

* 独自のインデックス処理やループを実行<xref:System.Text.Json.JsonElement.EnumerateArray%2A>するのではなく<xref:System.Text.Json.JsonElement.EnumerateObject%2A>、組み込みの列挙子 ( と ) を使用します。
* を使用`RootElement`して、すべてのプロパティを通じて全体`JsonDocument`でシーケンシャル検索を行う必要はありません。 代わりに、JSON データの既知の構造に基づいて、ネストされた JSON オブジェクトを検索します。 たとえば、`Grade`オブジェクト内の`Student`プロパティを探している場合は、`Student`プロパティを検索するすべての`Grade``JsonElement`オブジェクトを検索するのではなく、オブジェクトをループ処理してそれぞれの値を`Grade`取得します。 後者を実行すると、同じデータに対して不要なパスが渡されます。

コード例については、「[データへのアクセスに JsonDocument を使用する](system-text-json-how-to.md#use-jsondocument-for-access-to-data)」を参照してください。

## <a name="utf8jsonreader-compared-to-jsontextreader"></a>テキストリーダーと比較した Utf8Json リーダー

<xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName>は、UTF-8 エンコードされた JSON テキストの高性能で低い割り当て、前方専用のリーダーであり[、ReadOnlySpan\<バイト>または ReadOnlySequence](xref:System.ReadOnlySpan%601)[\<バイト>](xref:System.Buffers.ReadOnlySequence%601)から読み取られます。 `Utf8JsonReader`は、カスタム パーサーとデシリアライザーの構築に使用できる低レベルの型です。

以下のセクションでは、 を使用`Utf8JsonReader`する際に推奨されるプログラミング パターンについて説明します。

### <a name="utf8jsonreader-is-a-ref-struct"></a>構造体です。

`Utf8JsonReader`型は ref*構造体*であるため、[いくつかの制限があります](../../csharp/language-reference/keywords/ref.md#ref-struct-types)。 たとえば、ref 構造体以外のクラスまたは構造体にフィールドとして格納することはできません。 高いパフォーマンスを実現するには、この型は`ref struct`、ref 構造体である[入力の\<ReadOnlySpan バイト>](xref:System.ReadOnlySpan%601)をキャッシュする必要があるため、この型をする必要があります。 また、この型は状態を保持するため、変更可能です。 したがって、値ではなく**ref で渡**します。 値を渡すと、構造体のコピーが作成され、状態の変更は呼び出し元からは見えません。 これは、クラスであるため`Newtonsoft.Json``Newtonsoft.Json``JsonTextReader`、異なります。 ref 構造体の使用方法の詳細については、「[安全で効率的な C# コードを記述](../../csharp/write-safe-efficient-code.md)する 」を参照してください。

### <a name="read-utf-8-text"></a>UTF-8 テキストを読む

を使用しながら最高のパフォーマンスを`Utf8JsonReader`実現するには、UTF-16 文字列としてではなく、UTF-8 テキストとして既にエンコードされている JSON ペイロードを読み取ります。 コード例については[、「Utf8JsonReader を使用してデータをフィルターする](system-text-json-how-to.md#filter-data-using-utf8jsonreader)」を参照してください。

### <a name="read-with-a-stream-or-pipereader"></a>ストリームまたはパイプリーダーで読み取る

utf-8`Utf8JsonReader`エンコード[された ReadOnlySpan\<バイト>](xref:System.ReadOnlySpan%601)または[ReadOnlySequence\<バイト>](xref:System.Buffers.ReadOnlySequence%601)からの読み取り (これは、<xref:System.IO.Pipelines.PipeReader>からの読み取りの結果) をサポートしています。

同期読み取りでは、ストリームの末尾まで JSON ペイロードをバイト配列に読み取り、それをリーダーに渡すことができます。 文字列 (UTF-16 としてエンコード) から読み取る<xref:System.Text.Encoding.UTF8>場合は、 を呼び出します。<xref:System.Text.Encoding.GetBytes%2A> まず、文字列を UTF-8 エンコードされたバイト配列に変換します。 その後、それをに`Utf8JsonReader`渡します。

入力は`Utf8JsonReader`JSON テキストと見なされるため、UTF-8 バイトの順序マーク (BOM) は無効な JSON と見なされます。 呼び出し元は、データをリーダーに渡す前にフィルター処理する必要があります。

コード例については[、「Utf8JsonReader を使用](system-text-json-how-to.md#use-utf8jsonreader)する」を参照してください。

### <a name="read-with-multi-segment-readonlysequence"></a>マルチセグメント読み取り専用シーケンスで読み取り

JSON 入力が[ReadOnlySpan\<バイト>](xref:System.ReadOnlySpan%601)の場合、読み取りループを実行するときに、リーダーの`ValueSpan`プロパティから各 JSON 要素にアクセスできます。 ただし、入力が[ReadOnlySequence\<バイト>](xref:System.Buffers.ReadOnlySequence%601) (これは、 から読み取られた結果) の<xref:System.IO.Pipelines.PipeReader>場合、一部の JSON`ReadOnlySequence<byte>`要素はオブジェクトの複数のセグメントにまたがって行われる可能性があります。 これらの要素は、連続したメモリ<xref:System.Text.Json.Utf8JsonReader.ValueSpan%2A>ブロックからアクセスできません。 代わりに、入力としてマルチセグメント`ReadOnlySequence<byte>`がある場合は、リーダーのプロパティ<xref:System.Text.Json.Utf8JsonReader.HasValueSequence%2A>をポーリングして、現在の JSON 要素にアクセスする方法を理解します。 推奨されるパターンを次に示します。

```csharp
while (reader.Read())
{
    switch (reader.TokenType)
    {
        // ...
        ReadOnlySpan<byte> jsonElement = reader.HasValueSequence ?
            reader.ValueSequence.ToArray() :
            reader.ValueSpan;
        // ...
    }
}
```

### <a name="use-valuetextequals-for-property-name-lookups"></a>プロパティ名の検索に ValueTextEquals を使用する

プロパティ名の検索<xref:System.Text.Json.Utf8JsonReader.ValueSpan%2A>を呼び出<xref:System.MemoryExtensions.SequenceEqual%2A>して、バイト単位の比較を行う場合は使用しないでください。 代<xref:System.Text.Json.Utf8JsonReader.ValueTextEquals%2A>わりに、そのメソッドは JSON でエスケープされた文字をエスケープしないために呼び出します。 "name" という名前のプロパティを検索する方法を示す例を次に示します。

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ValueTextEqualsExample.cs?name=SnippetDefineUtf8Var)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ValueTextEqualsExample.cs?name=SnippetUseUtf8Var&highlight=11)]

### <a name="read-null-values-into-nullable-value-types"></a>NULL 値を NULL 許容値型に読み取る

`Newtonsoft.Json`には<xref:System.Nullable%601>、 などの`ReadAsBoolean`を返す`Null``TokenType`API が用意されており、 を`bool?`返して 処理を行います。 組み込み`System.Text.Json`API は、null 非許容値型のみを返します。 たとえば、<xref:System.Text.Json.Utf8JsonReader.GetBoolean%2A?displayProperty=nameWithType>を返`bool`します。 JSON で見つかった`Null`場合は例外をスローします。 次の例では、null 値型を返し、1 つは既定値を返すことによって、null を処理する 2 つの方法を示します。

```csharp
public bool? ReadAsNullableBoolean()
{
    _reader.Read();
    if (_reader.TokenType == JsonTokenType.Null)
    {
        return null;
    }
    if (_reader.TokenType != JsonTokenType.True && _reader.TokenType != JsonTokenType.False)
    {
        throw new JsonException();
    }
    return _reader.GetBoolean();
}
```

```csharp
public bool ReadAsBoolean(bool defaultValue)
{
    _reader.Read();
    if (_reader.TokenType == JsonTokenType.Null)
    {
        return defaultValue;
    }
    if (_reader.TokenType != JsonTokenType.True && _reader.TokenType != JsonTokenType.False)
    {
        throw new JsonException();
    }
    return _reader.GetBoolean();
}
```

### <a name="multi-targeting"></a>マルチターゲット

特定のターゲット フレームワークに対`Newtonsoft.Json`して引き続き使用する必要がある場合は、マルチターゲットと 2 つの実装を持つことができます。 しかし、これは簡単なものではなく、いくつかの`#ifdefs`ソースの重複が必要になります。 できるだけ多くのコードを共有する 1 つの方法は`ref struct`、ラッパー`Utf8JsonReader`を`Newtonsoft.Json``JsonTextReader`作成することです。 このラッパーは、動作の違いを分離しながら、公開サーフェス領域を統一します。 これにより、主に型の構築に対する変更を分離し、参照によって新しい型を渡すことができます。 これは[、Microsoft.Extensions.依存関係モデル](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/3.1.0/)ライブラリが従うパターンです。

* [UnifiedJsonReader.JsonTextReader.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonReader.JsonTextReader.cs)
* [UnifiedJsonReader.Utf8JsonReader.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonReader.Utf8JsonReader.cs)

## <a name="utf8jsonwriter-compared-to-jsontextwriter"></a>テキストライターと比較した Utf8Json ライター

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName>は、 、、 `String` `Int32`、および などの一般的な .NET 型から UTF-8`DateTime`エンコードされた JSON テキストを書き込む高性能な方法です。 ライターは、カスタム シリアライザーの構築に使用できる低レベルの型です。

以下のセクションでは、 を使用`Utf8JsonWriter`する際に推奨されるプログラミング パターンについて説明します。

### <a name="write-with-utf-8-text"></a>UTF-8 テキストで書く

を使用しながら最高のパフォーマンスを`Utf8JsonWriter`実現するには、UTF-16 文字列としてではなく、UTF-8 テキストとして既にエンコードされている JSON ペイロードを記述します。 既知<xref:System.Text.Json.JsonEncodedText>の文字列プロパティ名と値を静的としてキャッシュおよび事前エンコードし、UTF-16 文字列リテラルを使用するのではなく、ライターに渡すために使用します。 これは、UTF-8 バイト配列をキャッシュして使用するよりも高速です。

この方法は、カスタムエスケープを実行する必要がある場合にも機能します。 `System.Text.Json`文字列の書き込み中にエスケープを無効にすることはできません。 ただし、ライターにオプションとして独自のカスタム<xref:System.Text.Encodings.Web.JavaScriptEncoder>を渡したり、エスケープを行うために独自`JsonEncodedText``JavascriptEncoder`のカスタムを作成し、文字列の代わりにを`JsonEncodedText`書き込んだりすることもできます。 詳しくは、[文字エンコードのカスタマイズ](system-text-json-how-to.md#customize-character-encoding)を参照してください。

### <a name="write-raw-values"></a>生の値を書き込む

この`Newtonsoft.Json``WriteRawValue`メソッドは、値が予期される場所に生の JSON を書き込みます。 <xref:System.Text.Json>は直接対応するものはありませんが、有効な JSON のみが記述されていることを確認する回避策を次に示します。

```csharp
using JsonDocument doc = JsonDocument.Parse(string);
doc.WriteTo(writer);
```

### <a name="customize-character-escaping"></a>文字エスケープのカスタマイズ

[StringEscapeHandling](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_StringEscapeHandling.htm)の設定`JsonTextWriter`では、ASCII 以外のすべての文字**または**HTML 文字をエスケープするオプションを提供しています。 デフォルトでは、`Utf8JsonWriter`非 ASCII**文字と**HTML 文字はすべてエスケープされます。 このエスケープは、多層防御セキュリティ上の理由から行われます。 別のエスケープ ポリシーを指定するには、<xref:System.Text.Encodings.Web.JavaScriptEncoder>を作成<xref:System.Text.Json.JsonWriterOptions.Encoder?displayProperty=nameWithType>し、 を設定します。 詳しくは、[文字エンコードのカスタマイズ](system-text-json-how-to.md#customize-character-encoding)を参照してください。

### <a name="customize-json-format"></a>JSON 形式のカスタマイズ

`JsonTextWriter`には、以下の設定が含`Utf8JsonWriter`まれており、同等の設定はありません。

* [インデント](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_Indentation.htm)- インデントする文字数を指定します。 `Utf8JsonWriter`常に 2 文字のインデントを行います。
* [インデント文字 -](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_IndentChar.htm)インデントに使用する文字を指定します。  `Utf8JsonWriter`常に空白を使用します。
* [QuoteChar](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_QuoteChar.htm) - 文字列値を囲むために使用する文字を指定します。  `Utf8JsonWriter`常に二重引用符を使用します。
* [QuoteName](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_QuoteName.htm) - プロパティ名を引用符で囲むかどうかを指定します。  `Utf8JsonWriter`常に引用符でそれらを囲みます。

これらの方法で生成`Utf8JsonWriter`される JSON をカスタマイズできる回避策はありません。

### <a name="write-null-values"></a>NULL 値を書き込む

を使用`Utf8JsonWriter`して NULL 値を書き込むには、次のステートメントを呼び出します。

* <xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A>を使用して、値として null を持つキーと値のペアを書き込みます。
* <xref:System.Text.Json.Utf8JsonWriter.WriteNullValue%2A>を使用して、JSON 配列の要素として null を書き込みます。

文字列プロパティの場合、文字列が null で<xref:System.Text.Json.Utf8JsonWriter.WriteString%2A>、 <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A> `WriteNull`と と`WriteNullValue`同じである場合。

### <a name="write-timespan-uri-or-char-values"></a>書き込み時間スパン、URI、または文字の値

`JsonTextWriter`には`WriteValue`[、TimeSpan](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_18.htm) [、Uri](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_22.htm)、および[char](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_3.htm)値のメソッドが用意されています。 `Utf8JsonWriter`同等のメソッドはありません。 代わりに、これらの値を文字列としてフォーマットし`ToString()`(たとえば、 を<xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A>呼び出して) し、 を呼び出します。

### <a name="multi-targeting"></a>マルチターゲット

特定のターゲット フレームワークに対`Newtonsoft.Json`して引き続き使用する必要がある場合は、マルチターゲットと 2 つの実装を持つことができます。 しかし、これは簡単なものではなく、いくつかの`#ifdefs`ソースの重複が必要になります。 できるだけ多くのコードを共有する 1 つの方法は、ラッパー`Utf8JsonWriter`を`Newtonsoft``JsonTextWriter`作成することです。 このラッパーは、動作の違いを分離しながら、公開サーフェス領域を統一します。 これにより、主にタイプの構築に対する変更を分離できます。 [次](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/3.1.0/)の表に従います。

* [UnifiedJsonWriter.JsonTextWriter.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonWriter.JsonTextWriter.cs)
* [UnifiedJsonWriter.Utf8JsonWriter.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonWriter.Utf8JsonWriter.cs)

## <a name="additional-resources"></a>その他のリソース

<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)[Restore this when the roadmap is updated.]-->
* [System.Text.Json概要](system-text-json-overview.md)
* [使用方法System.Text.Json](system-text-json-how-to.md)
* [カスタム コンバーターを記述する方法](system-text-json-converters-how-to.md)
* [でサポートされている日時と日時オフセットSystem.Text.Json](../datetime/system-text-json-support.md)
* [System.Text.JsonAPI リファレンス](xref:System.Text.Json)
* [System.Text.Json.シリアル化 API リファレンス](xref:System.Text.Json.Serialization)
