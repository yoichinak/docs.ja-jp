---
title: C# 演算子
ms.date: 04/04/2018
f1_keywords:
- cs.operators
helpviewer_keywords:
- boolean operators [C#]
- expressions [C#], operators
- logical operators [C#]
- operators [C#]
- Visual C#, operators
- indirection operators [C#]
- assignment operators [C#]
- shift operators [C#]
- relational operators [C#]
- bitwise operators [C#]
- address operators [C#]
- keywords [C#], operators
- arithmetic operators [C#]
ms.assetid: 0301e31f-22ad-49af-ac3c-d5eae7f0ac43
ms.openlocfilehash: f4267caeb6301950b9f6a8b9545a47b9f48e7920
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61689815"
---
# <a name="c-operators"></a>C# 演算子

C# には、多くの演算子が用意されています。演算子とは、式で実行する演算 (数値演算、インデックス作成、関数呼び出しなど) を指定する記号のことです。 多くの演算子は、ユーザー定義型に適用する際に[オーバーロード](../../programming-guide/statements-expressions-operators/overloadable-operators.md)して、その意味を変更できます。

整数型に対する演算 (`==`、`!=`、`<`、`>`、`&`、`|`) は、通常、列挙型 (`enum`) で使用できます。

ここでは、C# の演算子を優先順位の高い順に示します。 各セクションの演算子の優先順位は同じです。

## <a name="primary-operators"></a>主な演算子

優先順位が最も高い演算子です。

[x.y](member-access-operator.md) – メンバー アクセス。

[x?.y](null-conditional-operators.md) – null 条件付きのメンバー アクセス。 左側のオペランドが `null` に評価される場合に `null` を返します。

[x?[y]](null-conditional-operators.md) - null 条件付きのインデックス アクセス。 左側のオペランドが `null` に評価される場合に `null` を返します。

[f(x)](invocation-operator.md) – 関数の呼び出し。

[a&#91;x&#93;](index-operator.md) – 集約オブジェクトのインデックス作成。

[x++](arithmetic-operators.md#increment-operator-) – 後置インクリメント。 x の値を返した後、1 大きくなった (通常は整数 1 が加算された) x の値で格納場所を更新します。

[x--](arithmetic-operators.md#decrement-operator---) – 後置デクリメント。 x の値を返した後、1 小さくなった (通常は整数 1 が減算された) x の値で格納場所を更新します。

[new](../keywords/new-operator.md) – 型のインスタンス化。

[typeof](../keywords/typeof.md) – オペランドを表す <xref:System.Type> オブジェクトを返します。

[checked](../keywords/checked.md) – 整数演算のオーバーフロー チェックを有効にします。

[unchecked](../keywords/unchecked.md) – 整数演算のオーバーフロー チェックを無効にします。 これがコンパイラの既定の動作です。

[default(T)](../../programming-guide/statements-expressions-operators/default-value-expressions.md) – 型 T の既定の値を生成します。

[Delegate](../../programming-guide/statements-expressions-operators/anonymous-methods.md) – delegate インスタンスを宣言して返します。

[sizeof](../keywords/sizeof.md) – 型オペランドのサイズをバイト単位で返します。

[->](dereference-operator.md) – メンバー アクセスと組み合わせてポインターを逆参照します。

## <a name="unary-operators"></a>単項演算子

これらの演算子は、前のセクションより優先順位が低く、次のセクションより優先順位が高くなります。

[+x](addition-operator.md) – x の値を返します。

[-x](subtraction-operator.md) – 数値の否定。

[\!x](boolean-logical-operators.md#logical-negation-operator-) – 論理否定。

[~x](bitwise-and-shift-operators.md#bitwise-complement-operator-) – ビットごとの補数。

[++x](arithmetic-operators.md#increment-operator-) – 前置インクリメント。 1 大きくなった (通常は整数 1 が加算された) x の値で格納場所を更新した後に x の値を返します。

[--x](arithmetic-operators.md#decrement-operator---) – 前置デクリメント。 1 小さくなった (通常は整数 1 が減算された) x の値で格納場所を更新した後に x の値を返します。

[(T)x](invocation-operator.md) – 型キャスト。

[await](../keywords/await.md) – `Task` を待機します。

[&x](and-operator.md) – アドレス。

[*x](multiplication-operator.md) – 逆参照。

[true 演算子](../keywords/true-false-operators.md) - オペランドが確実に true であることを示す[ブール](../keywords/bool.md)値 `true` を返します。

[false 演算子](../keywords/true-false-operators.md) - オペランドが確実に false であることを示す[ブール](../keywords/bool.md)値 `true` を返します。

## <a name="multiplicative-operators"></a>乗算演算子

これらの演算子は、前のセクションより優先順位が低く、次のセクションより優先順位が高くなります。

[x * y](arithmetic-operators.md#multiplication-operator-) – 乗算。

[x / y](arithmetic-operators.md#division-operator-) – 除算。 オペランドが整数の場合、結果は 0 に近い整数になるように切り捨てられます (例: `-7 / 2 is -3`)。

[x % y](arithmetic-operators.md#remainder-operator-) – 剰余。 オペランドが整数の場合、x を y で除算した剰余を返します。  `q = x / y` で `r = x % y` の場合、`x = q * y + r` になります。

## <a name="additive-operators"></a>加法演算子

これらの演算子は、前のセクションより優先順位が低く、次のセクションより優先順位が高くなります。

[x + y](arithmetic-operators.md#addition-operator-) – 加算。

[x – y](arithmetic-operators.md#subtraction-operator--) – 減算。

## <a name="shift-operators"></a>シフト演算子

これらの演算子は、前のセクションより優先順位が低く、次のセクションより優先順位が高くなります。

[x <\<  y](bitwise-and-shift-operators.md#left-shift-operator-) – ビットを左へシフトし、右側には 0 を格納します。

[x >> y](bitwise-and-shift-operators.md#right-shift-operator-) – ビットを右へシフトします。 左側のオペランドが `int` または `long` の場合、左側のビットには符号ビットが格納されます。 左側のオペランドが `uint` または `ulong` の場合、左側のビットには 0 が格納されます。

## <a name="relational-and-type-testing-operators"></a>関係演算子と型検査演算子

これらの演算子は、前のセクションより優先順位が低く、次のセクションより優先順位が高くなります。

[x \< y](less-than-operator.md) – より小さい (x が y より小さい場合は true)。

[x > y](greater-than-operator.md) – より大きい (x が y より大きい場合は true)。

[x \<= y](less-than-equal-operator.md) – 以下。

[x >= y](greater-than-equal-operator.md) – 以上。

[is](../keywords/is.md) – 型の互換性。 評価される左側のオペランドを右側のオペランドで指定された型 (静的な型) にキャストできる場合は、true を返します。

[as](../keywords/as.md) – 型変換。 左側のオペランドを右側のオペランドで指定された型 (静的な型) にキャストして返します。ただし、`(T)x` が例外をスローした場合、`as` は `null` を返します。

## <a name="equality-operators"></a>等値演算子

これらの演算子は、前のセクションより優先順位が低く、次のセクションより優先順位が高くなります。

[x == y](equality-operators.md#equality-operator-) – 等価比較。 既定では、`string` 以外の参照型の場合、参照の等価性を返します (等価テスト)。 ただし、型は `==` をオーバーロードできるため、同一性のテストが目的の場合は `object` で `ReferenceEquals` メソッドを使用することをお勧めします。

[x != y](equality-operators.md#inequality-operator-) – 等しくない。 `==` のコメントを参照してください。 型が `==` をオーバーロードする場合は、`!=` をオーバーロードする必要があります。

## <a name="logical-and-operator"></a>論理 AND 演算子

この演算子は、前のセクションより優先順位が低く、次のセクションより優先順位が高くなります。

`x & y` – `bool` オペランドの場合は[論理 AND](boolean-logical-operators.md#logical-and-operator-)、整数型のオペランドの場合は[ビットごとの論理 AND](bitwise-and-shift-operators.md#logical-and-operator-)。

## <a name="logical-xor-operator"></a>論理 XOR 演算子

この演算子は、前のセクションより優先順位が低く、次のセクションより優先順位が高くなります。

`x ^ y` – `bool` オペランドの場合は[論理 XOR](boolean-logical-operators.md#logical-exclusive-or-operator-)、整数型のオペランドの場合は[ビットごとの論理 XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-)。

## <a name="logical-or-operator"></a>論理演算子 OR

この演算子は、前のセクションより優先順位が低く、次のセクションより優先順位が高くなります。

`x | y` – `bool` オペランドの場合は[論理 OR](boolean-logical-operators.md#logical-or-operator-)、整数型のオペランドの場合は[ビットごとの論理 OR](bitwise-and-shift-operators.md#logical-or-operator-)。

## <a name="conditional-and-operator"></a>条件 AND 演算子

この演算子は、前のセクションより優先順位が低く、次のセクションより優先順位が高くなります。

[x && y](boolean-logical-operators.md#conditional-logical-and-operator-) – 論理 AND。 最初のオペランドが false に評価される場合、C# では 2 番目のオペランドが評価されません。

## <a name="conditional-or-operator"></a>条件 OR 演算子

この演算子は、前のセクションより優先順位が低く、次のセクションより優先順位が高くなります。

[x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) – 論理 OR。 最初のオペランドが true に評価される場合、C# では 2 番目のオペランドが評価されません。

## <a name="null-coalescing-operator"></a>Null 合体演算子

この演算子は、前のセクションより優先順位が低く、次のセクションより優先順位が高くなります。

[x ?? y](null-coalescing-operator.md) – `x` が `null` 以外の場合は x を返します。null の場合は `y` を返します。

## <a name="conditional-operator"></a>条件演算子

この演算子は、前のセクションより優先順位が低く、次のセクションより優先順位が高くなります。

[t ? x : y](conditional-operator.md) – テスト `t` が true に評価される場合は `x` を評価して返します。それ以外の場合は `y` を評価して返します。

## <a name="assignment-and-lambda-operators"></a>代入演算子とラムダ演算子

これらの演算子は、前のセクションより優先順位が低く、次のセクションより優先順位が高くなります。

[x = y](assignment-operator.md) – 代入。

[x += y](addition-assignment-operator.md) – インクリメント。 `y` の値を `x` の値に加算した結果を `x` に格納し、新しい値を返します。 `x` が `event` を指定した場合、`y` は、C# によってイベント ハンドラーとして追加される適切な関数である必要があります。

[x -= y](subtraction-assignment-operator.md) – デクリメント。 `y` の値を `x` の値から減算した結果を `x` に格納し、新しい値を返します。 `x` で `event` を指定する場合、`y` は C# によってイベント ハンドラーとして削除される適切な関数である必要があります。

[x *= y](arithmetic-operators.md#compound-assignment) – 乗算代入。 `y` の値を `x` の値に乗算した結果を `x` に格納し、新しい値を返します。

[x /= y](arithmetic-operators.md#compound-assignment) – 除算代入。 `x` の値を `y` の値で除算した結果を `x` に格納し、新しい値を返します。

[x %= y](arithmetic-operators.md#compound-assignment) – 剰余代入。 `x` の値を `y` の値で除算した剰余を `x` に格納し、新しい値を返します。

[x &= y](boolean-logical-operators.md#compound-assignment) – AND 代入。 `y` の値と `x` の値の AND 演算を行った結果を `x` に格納し、新しい値を返します。

[x &#124;= y](boolean-logical-operators.md#compound-assignment) – OR 代入。 `y` の値と `x` の値の OR 演算を行った結果を `x` に格納し、新しい値を返します。

[x ^= y](boolean-logical-operators.md#compound-assignment) – XOR 代入。 `y` の値と `x` の値の XOR 演算を行った結果を `x` に格納し、新しい値を返します。

[x <<= y](bitwise-and-shift-operators.md#compound-assignment) – 左シフト代入。 `x` の値を `y` で指定した分だけ左へシフトした結果を `x` に格納し、新しい値を返します。

[x >>= y](bitwise-and-shift-operators.md#compound-assignment) – 右シフト代入。 `x` の値を `y` で指定した分だけ右へシフトした結果を `x` に格納し、新しい値を返します。

[=>](lambda-operator.md) – ラムダ宣言。

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [C#](../../index.md)
- [オーバーロード可能な演算子](../../programming-guide/statements-expressions-operators/overloadable-operators.md)
- [C# のキーワード](../keywords/index.md)
