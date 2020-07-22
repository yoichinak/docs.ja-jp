---
title: 配列 - C# プログラミング ガイド
description: C# の配列データ構造に、同じ型の複数の変数を格納します。 配列を宣言するには、型を指定するか、任意の型を格納する場合は Object を指定します。
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: e302ff2e4c2488c4899c4eb99a666d2d322119ce
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474736"
---
# <a name="arrays-c-programming-guide"></a>配列 (C# プログラミング ガイド)

配列データ構造体には、同じ型の複数の変数を格納できます。 配列は、要素の型を指定することで宣言します。 配列に任意の型の要素を格納する場合は、その型として `object` を指定できます。 C# の統一型システムでは、すべての型 (定義済み、ユーザー定義、参照型、および値の型) が、直接または間接的に <xref:System.Object> を継承します。

```csharp
type[] arrayName;
```

## <a name="example"></a>例

次の例では、1 次元配列、多次元配列、およびジャグ配列を作成しています。

[!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]

## <a name="array-overview"></a>配列の概要

配列には、次の特徴があります。

- 配列は、[1 次元配列](single-dimensional-arrays.md)、[多次元配列](multidimensional-arrays.md)、または[ジャグ配列](jagged-arrays.md)のいずれかになります。
- 次元数と各次元の長さは、配列インスタンスの作成時に設定されます。 インスタンスの有効期間中にこれらの値を変更することはできません。
- 数値配列要素の既定値はゼロに設定され、参照要素は null に設定されます。
- ジャグ配列は配列の配列です。そのため、配列要素は参照型で、`null` に初期化されます。
- 配列には、ゼロから始まるインデックスが付けられます。`n` 個の要素を含む配列には、`0` から `n-1` までのインデックスが付けられます。
- 配列の要素および配列型は、どのような型でもかまいません。
- 配列型は、抽象基本型 <xref:System.Array> から派生した[参照型](../../language-reference/keywords/reference-types.md)です。 この型は <xref:System.Collections.IEnumerable> と <xref:System.Collections.Generic.IEnumerable%601> を実装するので、C# のすべての配列で [foreach](../../language-reference/keywords/foreach-in.md) 反復処理を使用できます。

## <a name="related-sections"></a>関連項目

- [オブジェクトとしての配列](arrays-as-objects.md)
- [配列での foreach の使用](using-foreach-with-arrays.md)
- [引数としての配列の受け渡し](passing-arrays-as-arguments.md)

## <a name="c-language-specification"></a>C# 言語仕様

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [コレクション](../concepts/collections.md)
