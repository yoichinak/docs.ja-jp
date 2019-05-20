---
title: ポインターに対する算術演算 - C# プログラミング ガイド
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], arithmetic operations
ms.assetid: d4f0b623-827e-45ce-8649-cfcebc8692aa
ms.openlocfilehash: b08f9dbf8137e483bd38a4f396732191598532cf
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65635234"
---
# <a name="arithmetic-operations-on-pointers-c-programming-guide"></a>ポインターに対する算術演算 (C# プログラミング ガイド)
このトピックでは、算術演算子 `+` と `-` を使用したポインター操作について説明します。  
  
> [!NOTE]
>  void ポインターには、算術演算を実行できません。  
  
## <a name="adding-and-subtracting-numeric-values-to-or-from-pointers"></a>ポインターに対する数値の加算と減算  
 型が [int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md) のいずれかである値 `n` をポインターに加算できます。 `p` が型 `pointer-type*` のポインターである場合、結果の `p+n` は `p` のアドレスに `n * sizeof(pointer-type)` を加算した結果のポインターです。 同様に、`p-n` は `p` のアドレスから `n * sizeof(pointer-type)` を減算した結果を表すポインターです。  
  
## <a name="subtracting-pointers"></a>ポインターの減算  
 同じ型のポインターを減算することもできます。 結果は常に `long` 型になります。 たとえば場合、`p1` と `p2` が `pointer-type*` 型のポインターである場合、式 `p1-p2` の結果は次のようになります。  
  
 `((long)p1 - (long)p2)/sizeof(pointer-type)`  
  
 算術演算がポインターのドメインをオーバーフローしても、例外は生成されません。生じる結果は実装によって異なります。  
  
## <a name="example"></a>例  
 [!code-csharp[csProgGuidePointers#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#14)]  
  
 [!code-csharp[csProgGuidePointers#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#15)]  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)
- [アンセーフ コードとポインター](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
- [C# 演算子](../../../csharp/language-reference/operators/index.md)
- [ポインターの操作](../../../csharp/programming-guide/unsafe-code-pointers/how-to-increment-and-decrement-pointers.md)
- [ポインター型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [型](../../../csharp/language-reference/keywords/types.md)
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)
- [fixed ステートメント](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
