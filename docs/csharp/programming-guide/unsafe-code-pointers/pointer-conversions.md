---
title: ポインター変換 - C# プログラミング ガイド
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], conversions
ms.assetid: f0e87502-477a-4ede-a31f-7a3e262e46fb
ms.openlocfilehash: 3cef2f2d2af2d285504daea14aa57c55b9e9a21b
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833459"
---
# <a name="pointer-conversions-c-programming-guide"></a>ポインター変換 (C# プログラミング ガイド)
定義済みの暗黙的なポインター変換を次の表に示します。 暗黙的な変換は、メソッドの呼び出しや代入ステートメントなど、多くの状況で発生することがあります。  
  
## <a name="implicit-pointer-conversions"></a>暗黙的なポインター変換  
  
|ソース|ターゲット|  
|----------|--------|  
|任意のポインター型|void*|  
|null|任意のポインター型|  
  
 明示的なポインター変換は、暗黙的な変換がない場合に、キャスト式を使用して、変換を実行するために使用します。 次の表はこの変換についてまとめたものです。  
  
## <a name="explicit-pointer-conversions"></a>明示的なポインター変換  
  
|ソース|ターゲット|  
|----------|--------|  
|任意のポインター型|その他のポインター型|  
|sbyte、byte、short、ushort、int、uint、long または ulong|任意のポインター型|  
|任意のポインター型|sbyte、byte、short、ushort、int、uint、long または ulong|  
  
## <a name="example"></a>例  
 次の例では、`int` へのポインターは `byte` へのポインターに変換されます。 ポインターは、変数の最下位バイト アドレスを指すことに注意してください。 `int` のサイズ (4 バイト) まで結果を連続してインクリメントする場合、変数の残りのバイトを表示することができます。  
  
 [!code-csharp[csProgGuidePointers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#3)]  
  
 [!code-csharp[csProgGuidePointers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#4)]  
  
## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)
- [ポインター型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [型](../../../csharp/language-reference/keywords/types.md)
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)
- [fixed ステートメント](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/operators/stackalloc.md)
