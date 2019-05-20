---
title: '方法 : ポインターを使用してメンバーにアクセスする - C# プログラミング ガイド'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], member access
ms.assetid: 1e998498-8c85-4a78-8ce2-4d8c20f08342
ms.openlocfilehash: d0ca4a0b2189ee652ad1d9c2b63690306a651df4
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65635073"
---
# <a name="how-to-access-a-member-with-a-pointer-c-programming-guide"></a>方法 : ポインターを使用してメンバーにアクセスする (C# プログラミング ガイド)
安全ではないコンテキストで宣言されている構造体のメンバーにアクセスするには、次の例のように、メンバー アクセス演算子を利用できます。`p` は、メンバー `x` を含む[構造体](../../../csharp/language-reference/keywords/struct.md)を指すポインターです。  
  
```  
CoOrds* p = &home;  
p -> x = 25; //member access operator ->  
```  
  
## <a name="example"></a>例  
 この例では、2 つの座標 (`x` と `y`) を含む[構造体](../../../csharp/language-reference/keywords/struct.md) `CoOrds` が宣言され、インスタンス化されています。 メンバー アクセス演算子 `->` とインスタンス `home` を指すポインターを使用することで、`x` と `y` に値が割り当てられます。  
  
> [!NOTE]
>  式 `p->x` は式 `(*p).x` と等しく、2 つの式のいずれを利用しても同じ結果が得られることに注目してください。  
  
 [!code-csharp[csProgGuidePointers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#9)]  
  
 [!code-csharp[csProgGuidePointers#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#10)]  
  
## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)
- [ポインター型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [型](../../../csharp/language-reference/keywords/types.md)
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)
- [fixed ステートメント](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
