---
title: '| 演算子 - C# リファレンス'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '|_CSharpKeyword'
helpviewer_keywords:
- bitwise OR operator [C#]
- '| operator [C#]'
- binary operator (|) [C#]
ms.assetid: 82d6bb78-54c8-40bf-b679-531180ddaf70
ms.openlocfilehash: 38f8e21dbd07868441e0c4fbb6074f9897905222
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59312879"
---
# <a name="-operator-c-reference"></a>| 演算子 (C# リファレンス)

整数型と `bool` には、2 項 `|` 演算子が事前定義されています。 整数型の場合、`|` はそのオペランドのビットごとの OR を計算します。 `bool` オペランドの場合、`|` は、そのオペランドの論理 OR を計算します。つまり、結果は、両方のオペランドが `false` の場合にのみ `false` になります。

## <a name="remarks"></a>解説

バイナリ `|` 演算子では、[条件 OR 演算子](boolean-logical-operators.md#conditional-logical-or-operator-) `||` とは対照的に、最初の演算子の値に関係なく、両方の演算子が評価されます。

ユーザー定義型は `|` 演算子をオーバーロードできます (「[演算子](../keywords/operator.md)」を参照)。

## <a name="example"></a>例

 [!code-csharp[csRefOperators#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#31)]

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [C# 演算子](index.md)