---
title: オブジェクトとしての配列 - C# プログラミング ガイド
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: 9905168662496c46d20f191c04f21d8630d02fa2
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2019
ms.locfileid: "72772107"
---
# <a name="arrays-as-objects-c-programming-guide"></a>オブジェクトとしての配列 (C# プログラミング ガイド)

C# の配列は、実際はオブジェクトです。C や C++ の場合のように、単なるアドレス指定可能な連続メモリ領域ではありません。 <xref:System.Array> はすべての配列型の抽象基本データ型で、 <xref:System.Array> のプロパティとその他のクラス メンバーを使用できます。 この例としては、<xref:System.Array.Length%2A> プロパティを使用して、配列の長さを取得します。 `numbers` 配列の長さ `5` を `lengthOfNumbers` という変数に代入するコードは、次のようになります。

[!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]

<xref:System.Array> クラスには、配列の並べ替え、検索、コピーを行うための便利なメソッドやプロパティが他にも多数用意されています。

## <a name="example"></a>例

次の例では、<xref:System.Array.Rank%2A> プロパティを使用して、配列の次元数を表示します。

[!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]

## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [配列](./index.md)
- [1 次元配列](./single-dimensional-arrays.md)
- [多次元配列](./multidimensional-arrays.md)
- [ジャグ配列](./jagged-arrays.md)
