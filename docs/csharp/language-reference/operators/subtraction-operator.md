---
title: '- 演算子 - C# リファレンス'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- -_CSharpKeyword
helpviewer_keywords:
- '- operator [C#]'
- subtraction operator (-) [C#]
ms.assetid: 4de7a4fa-c69d-48e6-aff1-3130af970b2d
ms.openlocfilehash: 920981addd5c779c9ad1c666ef45e1de5cd23408
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633003"
---
# <a name="--operator-c-reference"></a>- 演算子 (C# リファレンス)

`-` 演算子には、単項演算子としての働きと 2 項演算子としての働きとがあります。

## <a name="remarks"></a>解説

すべての数値型には、単項 `-` 演算子が事前定義されています。 数値型に対する単項 `-` 演算の結果は、オペランドの反転の数値となります。

最初のオペランドから 2 番目のオペランドを減算するために、すべての数値型と列挙型に 2 項 `-` 演算子が事前定義されています。

2 項 `-` 演算子はデリゲート型にも備わっており、その場合、デリゲートの削除が実行されます。

単項 `-` 演算子と 2 項 `-` 演算子は、ユーザー定義型でオーバーロードすることができます。 詳細については、「[operator キーワード](../keywords/operator.md)」を参照してください。

## <a name="example"></a>例

[!code-csharp[csRefOperators#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#40)]

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [C# 演算子](index.md)
