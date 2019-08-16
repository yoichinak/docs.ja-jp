---
title: C# 演算子 - C# リファレンス
ms.date: 04/30/2019
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
ms.openlocfilehash: 0e49c28f05d52c704a46806559407381c7eb3530
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971251"
---
# <a name="c-operators-c-reference"></a>C# 演算子 (C# リファレンス)

C# は組み込み型でサポートされている定義済みの演算子を多数提供します。 たとえば、[算術演算子](arithmetic-operators.md)は組み込み数値型のオペランドの算術演算を実行し、[ブール論理演算子](boolean-logical-operators.md)は [bool](../keywords/bool.md) オペランドの論理演算を実行します。

ユーザー定義型は、その型のオペランドに対応する動作を定義する特定の演算子をオーバーロードできます。 詳細については、「[演算子のオーバーロード](operator-overloading.md)」を参照してください。

次の表は、C# の演算子を優先順位の高い順にまとめたものです。 各行内の演算子の優先順位は同じです。

| 演算子 | カテゴリまたは名前 |
| --------- | ---------------- |
| [x.y](member-access-operators.md#member-access-operator-)、[x?.y](member-access-operators.md#null-conditional-operators--and-)、[x?[y]](member-access-operators.md#null-conditional-operators--and-)、[f(x)](member-access-operators.md#invocation-operator-)、[a&#91;x&#93;](member-access-operators.md#indexer-operator-)、[x++](arithmetic-operators.md#increment-operator-)、[x--](arithmetic-operators.md#decrement-operator---)、[new](new-operator.md)、[typeof](type-testing-and-conversion-operators.md#typeof-operator)、[checked](../keywords/checked.md)、[unchecked](../keywords/unchecked.md)、[default](default.md)、[nameof](nameof.md)、[delegate](delegate-operator.md)、[sizeof](sizeof.md)、[stackalloc](stackalloc.md)、[->](pointer-related-operators.md#pointer-member-access-operator--) | 1 次式 |
| [+x](addition-operator.md)、[-x](subtraction-operator.md)、[\!x](boolean-logical-operators.md#logical-negation-operator-)、[~x](bitwise-and-shift-operators.md#bitwise-complement-operator-)、[++x](arithmetic-operators.md#increment-operator-)、[--x](arithmetic-operators.md#decrement-operator---)、[(T)x](type-testing-and-conversion-operators.md#cast-operator-)、[await](../keywords/await.md)、[&x](pointer-related-operators.md#address-of-operator-)、[*x](pointer-related-operators.md#pointer-indirection-operator-)、[true および false](true-false-operators.md) | 単項 |
| [x * y](arithmetic-operators.md#multiplication-operator-)、[x / y](arithmetic-operators.md#division-operator-)、[x % y](arithmetic-operators.md#remainder-operator-) | 乗法|
| [x + y](arithmetic-operators.md#addition-operator-)、[x – y](arithmetic-operators.md#subtraction-operator--) | 加法 |
| [x <\< y](bitwise-and-shift-operators.md#left-shift-operator-)、[x >> y](bitwise-and-shift-operators.md#right-shift-operator-) | シフト |
| [x \< y](comparison-operators.md#less-than-operator-)、[x > y](comparison-operators.md#greater-than-operator-)、[x \<= y](comparison-operators.md#less-than-or-equal-operator-)、[x >= y](comparison-operators.md#greater-than-or-equal-operator-)、[is](type-testing-and-conversion-operators.md#is-operator)、[as](type-testing-and-conversion-operators.md#as-operator) | 関係式と型検査 |
| [x == y](equality-operators.md#equality-operator-), [x != y](equality-operators.md#inequality-operator-) | 等価比較 |
| `x & y` | [ブール演算の論理 AND](boolean-logical-operators.md#logical-and-operator-) または[ビット演算の論理 AND](bitwise-and-shift-operators.md#logical-and-operator-) |
| `x ^ y` | [ブール演算の論理 XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) または[ビット演算の論理 XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) |
| <code>x &#124; y</code> | [ブール演算の論理 OR](boolean-logical-operators.md#logical-or-operator-) または[ビット演算の論理 OR](bitwise-and-shift-operators.md#logical-or-operator-) |
| [x && y](boolean-logical-operators.md#conditional-logical-and-operator-) | 条件 AND |
| [x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) | 条件 OR |
| [x ?? y](null-coalescing-operator.md) | Null 合体演算子 |
| [t ? x : y](conditional-operator.md) | 条件演算子 |
| [x = y](assignment-operator.md)、[x += y](arithmetic-operators.md#compound-assignment)、[x -= y](arithmetic-operators.md#compound-assignment)、[x *= y](arithmetic-operators.md#compound-assignment)、[x /= y](arithmetic-operators.md#compound-assignment)、[x %= y](arithmetic-operators.md#compound-assignment)、[x &= y](boolean-logical-operators.md#compound-assignment)、[x &#124;= y](boolean-logical-operators.md#compound-assignment)、[x ^= y](boolean-logical-operators.md#compound-assignment)、[x <<= y](bitwise-and-shift-operators.md#compound-assignment)、[x >>= y](bitwise-and-shift-operators.md#compound-assignment)、[=>](lambda-operator.md) | 代入とラムダ宣言 |

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [演算子](../../programming-guide/statements-expressions-operators/operators.md)
