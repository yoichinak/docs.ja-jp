---
title: 文字列
description: について説明しますが、どのようにF#'string' 型では、変更不可のテキストを表す Unicode 文字のシーケンスとして。
ms.date: 07/05/2019
ms.openlocfilehash: ec895723cc6d21a701a27b5d70d053bb681ce2b3
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/09/2019
ms.locfileid: "67660594"
---
# <a name="strings"></a>文字列

> [!NOTE]
> この記事の API リファレンスのリンクをクリックすると MSDN に移動します。  docs.microsoft.com API リファレンスは完全ではありません。

`string`型が Unicode 文字のシーケンスとして変更不可のテキストを表します。 `string` は、.NET Framework の `System.String` のエイリアスです。

## <a name="remarks"></a>Remarks

文字列リテラルは引用符 (") 文字で区切られます。 円記号 ( \\ ) 特定の特殊文字をエンコードするために使用します。 円記号と、次の文字の組み合わせと呼ばれる、*エスケープ シーケンス*します。 エスケープ シーケンスが F# 文字列リテラルは、次の表に示すでサポートされています。

|文字|エスケープ シーケンス|
|---------|---------------|
|警告|`\a`|
|バックスペース|`\b`|
|フォーム フィード|`\f`|
|改行|`\n`|
|キャリッジ リターン|`\r`|
|タブ|`\t`|
|垂直タブ|`\v`|
|円記号|`\\`|
|引用符|`\"`|
|アポストロフィ|`\'`|
|Unicode 文字|`\DDD` (場所`D`10 進数を示す数字です - 000 の範囲 255。 たとえば、 `\231` ="ç")。|
|Unicode 文字|`\xHH` (場所`H`の 16 進数値です 00 ~ FF; の範囲を示しますたとえば、 `\xE7` ="ç")。|
|Unicode 文字|`\uHHHH` (UTF-16)(場所`H`の 16 進数値です 0000 - FFFF; の範囲を示します。 たとえば、 `\u00E7` =「ç」)|
|Unicode 文字|`\U00HHHHHH` (UTF-32)(場所`H`の 16 進数値です 000000 - 10 ffff; の範囲を示します。 たとえば、 `\U0001F47D` ="👽")|

> [!IMPORTANT]
> `\DDD`エスケープ シーケンスは、その他のほとんどの言語でなどのない 8 進数表記の 10 進表記。 したがって、桁`8`と`9`有効では、一連の`\032`空白を表します (u+0020)、8 進数表記で同じコード ポイントになりますが、`\040`します。

> [!NOTE]
> 0 の範囲に制約されている - 255 (0 xff)、`\DDD`と`\x`エスケープ シーケンスは、実質的に、 [ISO 8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout)文字セットの最初の 256 個の Unicode コード ポイントと一致するためです。

前にある場合、@ 記号、リテラルには、逐語的文字列。 つまり、2 つの引用符文字が 1 つの引用符文字として解釈される点が異なりますエスケープ シーケンスが無視します。

さらに、文字列の場合は、三重引用符で囲まれている可能性があります。 この場合、すべてのエスケープ シーケンスは無視されます、二重引用符文字も含まれます。 埋め込まれた文字列を引用符で囲まれたを含む文字列を指定するには、逐語的文字列または三重引用符で囲まれた文字列か、使用できます。 逐語的文字列を使用する場合は、一重引用符文字を示す 2 つの引用符文字を指定する必要があります。 三重引用符で囲まれた文字列を使用する場合は、文字列の末尾として解析することがなく、単一引用符文字を使用できます。 この方法は、XML または埋め込まれた引用符を含むその他の構造を操作する場合に便利です。

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

コードでは、文字列は、改行が受け入れられ、改行以外として解釈されますとして改行、円記号が改行の前に最後の文字。 次の行の先頭の空白文字には、円記号を使用する場合は無視されます。 次のコードには、文字列が生成されます。`str1`値を持つ`"abc\ndef"`と文字列`str2`値を持つ`"abcdef"`します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

文字列の個々 の文字は、次のように配列に似た構文を使用してアクセスできます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

出力は `b`になります。

または、次のコードに示すように、配列スライス構文を使用して部分文字列を抽出することができます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

出力は次のとおりです。

```
abc
def
```

ASCII 文字列型の符号なしバイトの配列で表現できます`byte[]`します。 サフィックスを追加する`B`を ASCII 文字列であることを示すリテラル文字列にします。 ASCII 文字列リテラルのバイト配列を使用では、Unicode のエスケープ シーケンスを除く、Unicode 文字列として同じエスケープ シーケンスをサポートします。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a>文字列演算子

文字列を連結する 2 つの方法があります: を使用して、`+`演算子またはを使用して、`^`演算子。 `+`演算子が、.NET Framework の文字列処理機能との互換性を維持します。

次の例は、文字列の連結を示しています。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a>String クラス

文字列を入力するためF#.NET Framework では実際には、`System.String`すべての入力、`System.String`メンバーが使用可能です。 これが含まれています、`+`演算子、文字列の連結に使用される、`Length`プロパティ、および`Chars`プロパティで、文字列を Unicode 文字の配列として返します。 文字列の詳細については、次を参照してください。`System.String`します。

使用して、`Chars`プロパティの`System.String`文字列の個々 の文字の次のコードに示すように、インデックスを指定することでアクセスできます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a>文字列のモジュール

含まれている文字列の処理の追加機能、`String`でモジュール、`FSharp.Core`名前空間。 詳細については、次を参照してください。 [Core.String モジュール](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d)します。

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
