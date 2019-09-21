---
title: オブジェクトとしての配列 - C# プログラミング ガイド
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: fd4496e0f84953204ad8c3f40db699e911c3f477
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597361"
---
# <a name="arrays-as-objects-c-programming-guide"></a>オブジェクトとしての配列 (C# プログラミング ガイド)

C# の配列は、実際はオブジェクトです。C や C++ の場合のように、単なるアドレス指定可能な連続メモリ領域ではありません。 <xref:System.Array> はすべての配列型の抽象基本データ型で、 <xref:System.Array> のプロパティとその他のクラス メンバーを使用できます。 この例としては、<xref:System.Array.Length%2A> プロパティを使用して、配列の長さを取得する場合などがあります。 `numbers` 配列の長さ `5` を `lengthOfNumbers` という変数に代入するコードは、次のようになります。  
  
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
