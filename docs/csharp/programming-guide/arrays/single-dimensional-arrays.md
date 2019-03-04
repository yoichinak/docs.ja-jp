---
title: 1 次元配列 - C# プログラミング ガイド
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: 719e4463806c9c7e8b5407f2494c3b548ffa43e8
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/01/2019
ms.locfileid: "57200781"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a>1 次元配列 (C# プログラミング ガイド)

次の例のように、5 つの整数の 1 次元配列を宣言することができます。  
  
 [!code-csharp[csProgGuideArrays#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#4)]  
  
 この配列は、`array[0]` から `array[4]` の要素を含んでいます。 [new](../../../csharp/language-reference/keywords/new.md) 演算子を使用して、配列を作成し、配列要素を既定値に初期化します。 この例では、すべての配列要素はゼロに初期化されます。  
  
 同じ方法では、文字列要素を格納する配列を宣言できます。 次に例を示します。  
  
 [!code-csharp[csProgGuideArrays#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#5)]  
  
## <a name="array-initialization"></a>配列の初期化

 宣言時に配列を初期化することができます。この場合、初期化リスト内の要素の数によって長さが既に提供されているので、長さ指定子は必要ありません。 次に例を示します。  
  
 [!code-csharp[csProgGuideArrays#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#6)]  
  
 文字列の配列は、同じ方法で初期化できます。 配列の各要素が曜日の名前で初期化される文字列配列の宣言を次に示します。  
 
 ```csharp
 string[] weekDays = new string[] { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };
 ```
  
 宣言時に配列を初期化する場合は、次のショートカットを使用できます。  
  
 [!code-csharp[csProgGuideArrays#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#8)]  
  
 初期化せずに配列変数を宣言できますが、配列をこの変数に割り当てるときに、`new` 演算子を使用する必要があります。 次に例を示します。  
  
 [!code-csharp[csProgGuideArrays#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#9)]  
  
 C# 3.0 で暗黙的に型指定される配列が導入されます。 詳細については、「[暗黙的に型指定される配列](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)」を参照してください。  
  
## <a name="value-type-and-reference-type-arrays"></a>値の型と参照型の配列

 次の配列の宣言を検討してみます。  
  
 [!code-csharp[csProgGuideArrays#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#10)]  
  
 このステートメントの結果は、`SomeType` が値型か参照型かによって決まります。 値型の場合、ステートメントはそれそれが型 `SomeType` である 10 個の要素の配列を作成します。 `SomeType` が参照型の場合、ステートメントは、それぞれが null 参照に初期化される 10 個の要素の配列を作成します。  
  
 値型と参照型の詳細については、「[型](../../../csharp/language-reference/keywords/types.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Array>
- [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)
- [配列](../../../csharp/programming-guide/arrays/index.md)
- [多次元配列](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)
- [ジャグ配列](../../../csharp/programming-guide/arrays/jagged-arrays.md)
