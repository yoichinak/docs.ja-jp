---
title: インライン関数
description: 呼び出し元のコードに直接統合される F# インライン関数を使用する方法について説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 12c175e3e46e12d978fe02d3e1fe83142e71a25d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61966596"
---
# <a name="inline-functions"></a>インライン関数

*インライン関数*関数が呼び出し元のコードに直接統合されています。

## <a name="using-inline-functions"></a>インライン関数を使用

静的な型のパラメーターを使用するときに型パラメーターでパラメーター化されるすべての関数はインラインである必要があります。 これは、コンパイラがこれらの型パラメーターを解決できることが保証されます。 通常のジェネリック型パラメーターを使用すると、このような制限はありません。

インライン関数がメンバー制約の使用を有効にする以外には、コードを最適化することができます。 ただし、インライン関数の過剰使用には、コード コンパイラの最適化とライブラリ関数の実装の変更に小さいされにくい可能性があります。 このため、他のすべての最適化手法をしようとした場合を除き、最適化のインライン関数の使用を避ける必要があります。 関数またはメソッドのインラインを行うことができます、パフォーマンスが向上がありますは常に大文字と小文字になっていません。 そのため、こと、特定の関数をインラインで行う実際には正の影響を確認するのにパフォーマンスの測定値を使用することも必要があります。

`inline`修飾子は、最上位レベルで、モジュール レベルまたはクラスで、メソッド レベルでの関数に適用できます。

次のコード例は、最上位レベル、インライン インスタンス メソッドをおよびインラインの静的メソッドで、インライン関数を示しています。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet201.fs)]

## <a name="inline-functions-and-type-inference"></a>インライン関数と型推論

有無`inline`に影響が推論を入力します。 これは、非インライン関数のことはできませんが、インライン関数が静的に解決できる型のパラメーターがあるためです。 次のコード例は、場合を示しています、`inline`を静的に解決される型パラメーターを持つ関数を使用しているので便利です、`float`変換演算子。

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet202.fs)]

なし、`inline`修飾子、型の推論はこの場合、特定の種類を実行する関数`int`します。 ただし、`inline`修飾子は、関数が静的に解決される型パラメーターを持つと推論も。 `inline`修飾子、型は、次の場所に推論されます。

```fsharp
^a -> unit when ^a : (static member op_Explicit : ^a -> float)
```

これは、関数への変換をサポートする任意の型を受け取ることを意味**float**します。

## <a name="see-also"></a>関連項目

- [関数](index.md)
- [制約](../generics/constraints.md)
- [静的に解決される型パラメーター](../generics/statically-resolved-type-parameters.md)