---
title: ポインター比較 - C# プログラミング ガイド
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], comparison
ms.assetid: fcafd514-7405-4deb-8490-cc58efda5495
ms.openlocfilehash: 25bc1c7b701c36d2daf1918986eb6a8e56980990
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65635132"
---
# <a name="pointer-comparison-c-programming-guide"></a>ポインター比較 (C# プログラミング ガイド)
次の演算子を適用して、任意の型のポインターを比較できます。  
  
 **==   !=   \<   >   \<=   >=**  
  
 比較演算子は、2 つのオペランドのアドレスを符号なし整数のように比較します。  
  
## <a name="example"></a>例  
 [!code-csharp[csProgGuidePointers#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#16)]  
  
 [!code-csharp[csProgGuidePointers#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#17)]  
  
## <a name="sample-output"></a>出力例  
 `True`  
  
 `False`  
  
## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)
- [C# 演算子](../../../csharp/language-reference/operators/index.md)
- [ポインターの操作](../../../csharp/programming-guide/unsafe-code-pointers/how-to-increment-and-decrement-pointers.md)
- [ポインター型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [型](../../../csharp/language-reference/keywords/types.md)
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)
- [fixed ステートメント](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
