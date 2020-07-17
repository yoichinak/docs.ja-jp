---
title: 自動ジェネリック化
description: どの F# 自動的に一般化引数と関数の種類可能であれば、複数の種類で動作させることについて説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 501749a190d9770cbcd9848e3d528cba32fe6762
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630626"
---
# <a name="automatic-generalization"></a>自動ジェネリック化

F#型の推定を使用して、関数と式の型を評価します。 このトピックでは、どの F# 自動的に一般化引数と関数の種類可能な限り、複数の種類で動作させることについて説明します。

## <a name="automatic-generalization"></a>自動ジェネリック化

コンパイラF#は、関数に対して型の推定を実行するときに、指定されたパラメーターをジェネリックにできるかどうかを判断します。 コンパイラは各パラメーターを調べ、関数がそのパラメーターの特定の型に依存しているかどうかを判断します。 そうでない場合、型はジェネリックとして推論されます。

次のコード例は、コンパイラがジェネリックと推論する関数を示しています。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet101.fs)]

型はと`'a -> 'a -> 'a`して推論されます。

型は、これが同じ不明な型の2つの引数を受け取り、同じ型の値を返す関数であることを示します。 前の関数がジェネリックになる理由の1つは、大なり演算子 (`>`) 自体がジェネリックであることです。 大なり演算子にはシグネチャ`'a -> 'a -> bool`があります。 すべての演算子がジェネリックであるとは限りません。関数内のコードが非ジェネリック関数または演算子と共にパラメーター型を使用している場合、そのパラメーターの型を一般化することはできません。

は`max`ジェネリックであるため、次の例に示すよう`int`に`float`、、などの型で使用できます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet102.fs)]

ただし、2つの引数は同じ型である必要があります。 署名はで`'a -> 'a -> 'a`あり、 `'a -> 'b -> 'a`ではありません。 したがって、次のコードでは、型が一致しないため、エラーが発生します。

```fsharp
// Error: type mismatch.
let biggestIntFloat = max 2.0 3
```

関数`max`は、大なり演算子をサポートするすべての型でも動作します。 したがって、次のコードに示すように、文字列で使用することもできます。

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-3/snippet104.fs)]

## <a name="value-restriction"></a>値の制限

コンパイラは、明示的な引数を持つ完全な関数定義と、単純な変更できない値に対してのみ、自動汎化を実行します。

これは、特定の型としては十分に制約されていないが、汎化できないコードをコンパイルしようとすると、コンパイラがエラーを発行することを意味します。 この問題のエラーメッセージは、値の*制限*として、値の自動汎化に対するこの制限を示しています。

通常、値制限エラーは、構造体をジェネリックにする必要があるものの、コンパイラがそれを一般化するための情報が不足している場合、または非ジェネリックコンストラクトで十分な型情報を誤って省略した場合に発生します。 値制限エラーの解決策は、次のいずれかの方法で、型推論の問題をより詳細に制限するために、より明示的な情報を提供することです。

- 明示的な型の注釈を値またはパラメーターに追加することにより、型を非ジェネリックに制約します。

- 関数コンポジションや不完全なカリー化関数の引数など、ジェネリック関数を定義するために汎化不可能なコンストラクトを使用している場合は、関数を通常の関数定義として書き直してください。

- 問題が複雑すぎて一般化できない式である場合は、余分な未使用のパラメーターを追加して関数にします。

- 明示的なジェネリック型パラメーターを追加します。 このオプションはほとんど使用されません。

- 次のコード例は、これらの各シナリオを示しています。

ケース 1:式が複雑すぎます。 この例では、リスト`counter`はであること`int option ref`を意図していますが、単純な変更できない値として定義されていません。

```fsharp
let counter = ref None
// Adding a type annotation fixes the problem:
let counter : int option ref = ref None
```

ケース 2:汎化できない構成体を使用してジェネリック関数を定義する。 この例では、構造体は、関数の引数の部分的な適用を伴うため、汎化できません。

```fsharp
let maxhash = max << hash
// The following is acceptable because the argument for maxhash is explicit:
let maxhash obj = (max << hash) obj
```

ケース 3:使用されていない余分なパラメーターを追加しています。 この式は一般化には不十分であるため、コンパイラは値の制限のエラーを発行します。

```fsharp
let emptyList10 = Array.create 10 []
// Adding an extra (unused) parameter makes it a function, which is generalizable.
let emptyList10 () = Array.create 10 []
```

ケース 4:型パラメーターを追加しています。

```fsharp
let arrayOf10Lists = Array.create 10 []
// Adding a type parameter and type annotation lets you write a generic value.
let arrayOf10Lists<'T> = Array.create 10 ([]:'T list)
```

最後の例では、値が型の関数になり、次のように、さまざまな型の値を作成するために使用できます。

```fsharp
let intLists = arrayOf10Lists<int>
let floatLists = arrayOf10Lists<float>
```

## <a name="see-also"></a>関連項目

- [型推論](../type-inference.md)
- [ジェネリック](index.md)
- [静的に解決される型パラメーター](statically-resolved-type-parameters.md)
- [制約](constraints.md)
