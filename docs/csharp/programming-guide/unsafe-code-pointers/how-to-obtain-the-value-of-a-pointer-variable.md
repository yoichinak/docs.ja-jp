---
title: '方法 : ポインター変数の値を取得する - C# プログラミング ガイド'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointer expressions [C#], indirection
- pointers [C#], indirection
- variables [C#], pointers
- pointers [C#], * operator
ms.assetid: 460a813a-4995-44c1-9de2-213b91dc7668
ms.openlocfilehash: 9a10bcc809f3ecbc9a0fa9b917940b8e030fab8f
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65635099"
---
# <a name="how-to-obtain-the-value-of-a-pointer-variable-c-programming-guide"></a>方法 : ポインター変数の値を取得する (C# プログラミング ガイド)

ポインターが指す位置にある変数を取得するには、ポインター間接演算子を使用します。 この式は次の形式になります。`p` はポインター型です。  

```csharp
*p;  
```

ポインター型以外の型の式では、単項間接演算子を使用することはできません。 また、[void](../../../csharp/language-reference/keywords/void.md) ポインターに適用することもできません。  

間接演算子を [null](../../../csharp/language-reference/keywords/null.md) ポインターに適用すると、結果は実装によって異なります。  

## <a name="example"></a>例

次の例では、`char` 型の変数に、さまざまな型のポインターを使用してアクセスします。 変数に割り当てられる物理アドレスが変更できるため、`theChar` のアドレスが実行ごとに異なることに注意してください。  

 [!code-csharp[csProgGuidePointers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#5)]  

 [!code-csharp[csProgGuidePointers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#6)]  
  
**theChar の値 = Z**  
**theChar のアドレス = 12F718**  
**pChar の値 = Z**  
**pInt の値 = 90**  

## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)
- [ポインター型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [型](../../../csharp/language-reference/keywords/types.md)
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)
- [fixed ステートメント](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
