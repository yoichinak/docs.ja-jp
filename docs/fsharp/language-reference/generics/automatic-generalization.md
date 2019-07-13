---
title: 自動ジェネリック化
description: どの F# 自動的に一般化引数と関数の種類可能であれば、複数の種類で動作させることについて説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 8fc61b5e0c227474a5e913b37f4c0dad9b235a6f
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641868"
---
# <a name="automatic-generalization"></a>自動ジェネリック化

F#関数と式の型を評価する推論を使用してに入力します。 このトピックでは、どの F# 自動的に一般化引数と関数の種類可能な限り、複数の種類で動作させることについて説明します。

## <a name="automatic-generalization"></a>自動ジェネリック化

F#関数の型の推定の実行時に、コンパイラは、指定されたパラメーターをジェネリックにできるかどうかを決定します。 コンパイラは、各パラメーターを調べ、関数は、そのパラメーターの特定の種類に依存しているかどうかを決定します。 そうでない場合をジェネリック型が推論されます。

次のコード例では、ジェネリックと、コンパイラが推論される関数を示しています。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet101.fs)]

型が推論`'a -> 'a -> 'a`します。

種類は、同じの不明な型の 2 つの引数を受け取り、その同じ型の値を返します関数であることを示します。 前の関数ができる理由の 1 つジェネリックは、大きい-演算子よりも (`>`) 自体が、ジェネリック。 大きい-より演算子がある署名`'a -> 'a -> bool`します。 すべての演算子は、ジェネリックとそのパラメーターの型を一般化することはできません、関数のコードは、非ジェネリック関数または演算子とパラメーターの型を使用している場合。

`max`は汎用的で、これで使える型など`int`、`float`これに、次の例に示すようにします。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet102.fs)]

ただし、同じ型の 2 つの引数がある必要があります。 署名が`'a -> 'a -> 'a`ではなく、`'a -> 'b -> 'a`します。 そのため、次のコードは、型が一致しないため、エラーを生成します。

```fsharp
// Error: type mismatch.
let biggestIntFloat = max 2.0 3
```

`max`関数でも使用できますか大きい方をサポートする任意の型の演算子よりもします。 そのためも使用できますが、文字列の次のコードに示すようにします。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet104.fs)]

## <a name="value-restriction"></a>値の制限

コンパイラは、不変の単純な値で明示的な引数を持つ完全な関数定義でのみ自動ジェネリック化を実行します。

これは、十分には、特定の型にするのには制限されませんが、汎化可能ながもコードをコンパイルしようとする場合、コンパイラがエラーを発行することを意味します。 この問題のエラー メッセージがこの制約として値の自動ジェネリック化を参照、*値制限*します。

通常、構成要素は、ジェネリックしたいが、コンパイラが不十分な情報を一般化し、ときに、または意図せずに、非ジェネリック コンストラクトに十分な情報を入力を省略すると、値制限エラーが発生します。 値制限エラーの解決策より完全で、次の方法のいずれかの型の推論の問題は制約より明確な情報を提供することです。

- 値またはパラメーターに明示的な型注釈の追加、非ジェネリックの型を制限します。

- 問題は、関数の合成などの汎用関数を定義する汎化できない構成要素を使用して、または不完全カリー化された関数の引数に適用は、通常の関数定義として関数を書き直してください。 お試しください。

- 問題が複雑すぎるために一般化する式の場合は、ように関数に、未使用のパラメーターを追加することで。

- 明示的なジェネリック型パラメーターを追加します。 このオプションはほとんど使用されません。

- 次のコード例は、これらの各シナリオを示します。

ケース 1:式が複雑すぎます。 この例では、一覧で`counter`を`int option ref`、単純な変更できない値は定義されていませんが。

```fsharp
let counter = ref None
// Adding a type annotation fixes the problem:
let counter : int option ref = ref None
```

ケース 2:汎化できない構成要素を使用して、ジェネリック関数を定義します。 この例では、コンストラクトは汎化できない構成を関数の引数の部分的なアプリケーションが伴うので。

```fsharp
let maxhash = max << hash
// The following is acceptable because the argument for maxhash is explicit:
let maxhash obj = (max << hash) obj
```

ケース 3:未使用のパラメーターを追加します。 この式が汎化の単純でないため、コンパイラは値制限エラーを発行します。

```fsharp
let emptyList10 = Array.create 10 []
// Adding an extra (unused) parameter makes it a function, which is generalizable.
let emptyList10 () = Array.create 10 []
```

ケース 4:型パラメーターを追加します。

```fsharp
let arrayOf10Lists = Array.create 10 []
// Adding a type parameter and type annotation lets you write a generic value.
let arrayOf10Lists<'T> = Array.create 10 ([]:'T list)
```

最後の場合、値には型関数の場合、次のようになど多くのさまざまな種類の値を作成するために使用できるようになります。

```fsharp
let intLists = arrayOf10Lists<int>
let floatLists = arrayOf10Lists<float>
```

## <a name="see-also"></a>関連項目

- [型推論](../type-inference.md)
- [ジェネリック](index.md)
- [静的に解決される型パラメーター](statically-resolved-type-parameters.md)
- [制約](constraints.md)
