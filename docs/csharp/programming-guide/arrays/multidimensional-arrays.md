---
title: 多次元配列 - C# プログラミング ガイド
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], multidimensional
- multidimensional arrays [C#]
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
ms.openlocfilehash: df9063d0616b72ad15c9c48fa4459a6dc98b77c1
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972613"
---
# <a name="multidimensional-arrays-c-programming-guide"></a>多次元配列 (C# プログラミング ガイド)

配列は 1 つ以上の配列を持つことができます。 たとえば、次の宣言は、4 行と 2 列の 2 次元の配列を作成します。  
  
 [!code-csharp[csProgGuideArrays#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#11)]  
  
 次の宣言は、4、2、3 の 3 次元配列を作成します。  
  
 [!code-csharp[csProgGuideArrays#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#12)]  
  
## <a name="array-initialization"></a>配列の初期化

 次の例に示すように、宣言時に配列を初期化することができます。  
  
 [!code-csharp[csProgGuideArrays#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#13)]  
  
 また、順位を指定せずに配列を初期化することもできます。  
  
 [!code-csharp[csProgGuideArrays#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#14)]  
  
 初期化せずに配列変数を宣言する場合、`new` 演算子を使用して配列を変数に代入する必要があります。 `new` の使用を次の例に示します。  
  
 [!code-csharp[csProgGuideArrays#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#15)]  
  
 次の例では、特定の配列要素に値を代入します。  
  
 [!code-csharp[csProgGuideArrays#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#16)]  
  
 同様に、次の例では、特定の配列要素の値を取得して、それを変数 `elementValue` に代入します。  
  
 [!code-csharp[csProgGuideArrays#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#42)]  
  
 次のコード例では、配列要素を既定値に初期化します (ジャグ配列を除く)。  
  
 [!code-csharp[csProgGuideArrays#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#17)]  
  
## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)
- [配列](../../../csharp/programming-guide/arrays/index.md)
- [1 次元配列](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)
- [ジャグ配列](../../../csharp/programming-guide/arrays/jagged-arrays.md)
