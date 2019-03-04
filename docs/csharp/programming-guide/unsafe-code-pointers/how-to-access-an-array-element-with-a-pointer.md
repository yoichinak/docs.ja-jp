---
title: '方法: ポインターを使用して配列要素にアクセスする - C# プログラミング ガイド'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], array access
ms.assetid: 6c46f2af-a730-4855-8638-f136d9abaa12
ms.openlocfilehash: 7b2991776ca032aa53111187a061835725cfe223
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965606"
---
# <a name="how-to-access-an-array-element-with-a-pointer-c-programming-guide"></a>方法: ポインターを使用して配列要素にアクセスする (C# プログラミング ガイド)

安全ではないコンテキストでは、次の例のように、ポインターを利用してメモリ内の要素にアクセスできます。

```csharp
char* charPointer = stackalloc char[123];
for (int i = 65; i < 123; i++)
{
    charPointer[i] = (char)i; //access array elements
}
```

角かっこ内の式は `int`、`uint`、`long`、`ulong` に暗黙的に変換できるものでなければなりません。 演算 `p[e]` は `*(p+e)` と等しくなります。 C や C++ と同様に、ポインターで要素にアクセスする行為では、範囲外のエラーがチェックされません。

## <a name="example"></a>例

この例では、123 のメモリ場所が文字配列 `charPointer` に割り当てられます。 この配列を利用し、2 つの [for](../../../csharp/language-reference/keywords/for.md) ループの小文字と大文字が表示されます。

式 `charPointer[i]` は式 `*(charPointer + i)` と等しく、2 つの式のいずれを利用しても同じ結果が得られることに注目してください。

 [!code-csharp[csProgGuidePointers#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#11)]

 [!code-csharp[csProgGuidePointers#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#12)]

**大文字:**  
**ABCDEFGHIJKLMNOPQRSTUVWXYZ**  
**小文字:**  
**abcdefghijklmnopqrstuvwxyz**  

## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)
- [ポインター式](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [ポインター型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [型](../../../csharp/language-reference/keywords/types.md)
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)
- [fixed ステートメント](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
