---
title: $ - 文字列補間 - C# リファレンス
ms.custom: seodec18
description: 文字列補間では、従来の複合文字列の書式設定よりも読み取りやすく、便利な構文を書式指定文字列の出力に提供します。
ms.date: 04/29/2019
f1_keywords:
- $_CSharpKeyword
- $
helpviewer_keywords:
- $ special character [C#]
- $ language element [C#]
- string interpolation [C#]
- interpolated string [C#]
author: pkulikov
ms.author: ronpet
ms.openlocfilehash: 1f0d63a549daa9fecd0cce3a7e5a6496929c37d2
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202960"
---
# <a name="---string-interpolation-c-reference"></a>$ - 文字列補間 (C# リファレンス)

`$` 特殊文字は、リテラル文字列を*挿入文字列*として識別します。 挿入文字列は、*補間式*が含まれている可能性がある文字列リテラルです。 挿入文字列が結果の文字列に解決されると、補間式を含む項目は、式の結果の文字列表現によって置き換えられます。 この機能は C# 6 以降のバージョンの言語で使用できます。

文字列補間では、[複合文字列の書式設定](../../../standard/base-types/composite-formatting.md)機能よりも読み取りやすく便利な構文を使用して書式指定された文字列を作成できます。 次の例では、両方の機能を使用して、同じ出力を生成します。

[!code-csharp-interactive[compare with composite formatting](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#1)]

## <a name="structure-of-an-interpolated-string"></a>挿入文字列の構造

文字列リテラルを挿入文字列として識別するため、先頭に `$` の記号を追加してください。 `$` と文字列リテラルを開始する `"` の間に空白を入れることはできません。 空白を入れると、コンパイル時エラーが発生します。

補間式を含む項目の構造は、次のとおりです。

```csharp
{<interpolationExpression>[,<alignment>][:<formatString>]}
```

角かっこ内の要素は省略可能です。 次の表は、それぞれの要素の説明です。

|要素|説明|
|-------------|-----------------|
|`interpolationExpression`|書式設定される結果を生成する式です。 `null` 結果の文字列表現は、<xref:System.String.Empty?displayProperty=nameWithType> です。|
|`alignment`|補間式の結果の文字列表現で、最小文字数を定義する値を持つ定数式です。 正の場合は、文字列表現は右揃えで配置され、負の場合は、左揃えで配置されます。 詳細については、「[Alignment コンポーネント](../../../standard/base-types/composite-formatting.md#alignment-component)」を参照してください。|
|`formatString`|式の結果の型によってサポートされる書式指定文字列です。 詳細については、「[Format String コンポーネント](../../../standard/base-types/composite-formatting.md#format-string-component)」を参照してください。|

次の例では、前述したオプションの書式設定コンポーネントを使用します。

[!code-csharp-interactive[specify alignment and format string](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#2)]

## <a name="special-characters"></a>特殊文字

挿入文字列で生成された文字列にかっこ "{" または "}" を含めるには、2 つのかっこ "{{" または "}}" を使用します。 詳細については、「[エスケープ中かっこ ({})](../../../standard/base-types/composite-formatting.md#escaping-braces)」を参照してください。

コロン (":") が補間式の項目で特別な意味を持つときに、補間式で[条件演算子](../operators/conditional-operator.md)を使用するには、その式を丸かっこで囲みます。

次の例では、かっこを結果の文字列に含める方法、および補間式で条件演算子を使用する方法を示します。

[!code-csharp-interactive[example with ternary conditional operator](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#3)]

逐語的挿入文字列は、`@` 文字が続く `$` 文字で始まります。 逐語的文字列の詳細については、[string](../keywords/string.md) と [逐語的識別子](verbatim.md)に関するトピックを参照してください。

> [!NOTE]
> `$` トークンは、逐語的挿入文字列の `@` トークンの前に置く必要があります。

## <a name="implicit-conversions-and-specifying-iformatprovider-implementation"></a>暗黙的な変換と `IFormatProvider` 実装の指定

挿入文字列から暗黙の変換を行う方法は 3 種類あります。

1. 挿入文字列から <xref:System.String> インスタンスへの変換。これは、適切に書式設定された文字列表現の結果で置き換えられる、補間式の項目を含む挿入文字列分析の結果です。 この変換では、現在のカルチャを使用します。

1. 書式設定される式の結果と、挿入文字列から複合書式指定文字列を表す <xref:System.FormattableString> インスタンスへの変換。 これは、単一の <xref:System.FormattableString> インスタンスから、カルチャ固有のコンテンツを持つ複数の結果文字列の作成を可能にするものです。 そのためには、次のいずれかのメソッドを呼び出します。

      - <xref:System.Globalization.CultureInfo.CurrentCulture> の結果文字列を生成する <xref:System.FormattableString.ToString> オーバーロード。
      - <xref:System.Globalization.CultureInfo.InvariantCulture> の結果文字列を生成する <xref:System.FormattableString.Invariant%2A> メソッド。
      - 特定のカルチャの結果文字列を生成する <xref:System.FormattableString.ToString(System.IFormatProvider)> メソッド。

    <xref:System.FormattableString.ToString(System.IFormatProvider)> メソッドを使用して、カスタム書式設定をサポートする <xref:System.IFormatProvider> インターフェイスのユーザー定義の実装を提供することもできます。 詳細については、「[ICustomFormatter を使用したカスタム書式設定](../../../standard/base-types/formatting-types.md#custom-formatting-with-icustomformatter)」を参照してください。

1. 挿入文字列から <xref:System.IFormattable> インスタンスへの変換。これは、単一の <xref:System.IFormattable> インスタンスから、カルチャ固有のコンテンツを持つ複数の結果文字列の作成も可能にするものです。

次の例では、カルチャ固有の結果の文字列を作成するために、<xref:System.FormattableString> への暗黙の変換を使用します。

[!code-csharp-interactive[create culture-specific result strings](~/samples/snippets/csharp/language-reference/tokens/string-interpolation.cs#4)]

## <a name="additional-resources"></a>その他の技術情報

文字列補間を初めてお使いの場合は、[C# の文字列補完](../../tutorials/exploration/interpolated-strings.yml)に関する対話形式チュートリアルを参照してください。 また、補完された文字列を使用して書式設定された文字列を生成する方法を示したもう 1 つのチュートリアル「[C# における文字列補完](../../tutorials/string-interpolation.md)」も確認してください。

## <a name="compilation-of-interpolated-strings"></a>補完文字列のコンパイル

補完文字列が `string` 型の場合、通常は <xref:System.String.Format%2A?displayProperty=nameWithType> メソッドの呼び出しに変換されます。 分析後の動作が連結と等しくなるようであれば、コンパイラでは、<xref:System.String.Format%2A?displayProperty=nameWithType> を <xref:System.String.Concat%2A?displayProperty=nameWithType> に置換する場合があります。

補間文字列の型が <xref:System.IFormattable> または <xref:System.FormattableString> の場合、コンパイラは <xref:System.Runtime.CompilerServices.FormattableStringFactory.Create%2A?displayProperty=nameWithType> メソッドの呼び出しを生成します。

## <a name="c-language-specification"></a>C# 言語仕様

詳しくは、[C# 言語仕様](~/_csharplang/spec/introduction.md)に関するページの[補完文字列](~/_csharplang/spec/expressions.md#interpolated-strings)のセクションを参照してください。

## <a name="see-also"></a>関連項目

- <xref:System.String.Format%2A?displayProperty=nameWithType>
- <xref:System.FormattableString?displayProperty=nameWithType>
- <xref:System.IFormattable?displayProperty=nameWithType>
- [複合書式指定](../../../standard/base-types/composite-formatting.md)
- [数値結果テーブルの書式設定](../keywords/formatting-numeric-results-table.md)
- [文字列](../../programming-guide/strings/index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [C# 特殊文字](index.md)
- [C# リファレンス](../index.md)
