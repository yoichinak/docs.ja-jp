---
title: '方法: 変数のアドレスを取得する - C# プログラミング ガイド'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- variables [C#], address of
- pointers [C#], & operator
- pointer expressions [C#], address-of operator
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
ms.openlocfilehash: bc5776bc57096b88a71ff786915553ae9aa04b7b
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65635059"
---
# <a name="how-to-obtain-the-address-of-a-variable-c-programming-guide"></a>方法: 変数のアドレスを取得する (C# プログラミング ガイド)

固定変数に評価される単項式のアドレスを取得するには、address-of 演算子 `&` を使用します。  
  
```csharp  
int number;  
int* p = &number; //address-of operator &  
```  
  
 address-of 演算子は、変数にのみ適用できます。 変数が移動可能な変数である場合、[fixed ステートメント](../../../csharp/language-reference/keywords/fixed-statement.md)を使用して変数のアドレスを取得する前に、一時的に変数を固定できます。 移動可能変数の詳細については、「[固定と移動可能変数](/dotnet/csharp/language-reference/language-specification/unsafe-code#fixed-and-moveable-variables)」を参照してください。 
  
 ユーザーは変数が初期化されていることを確認する必要があります。 変数が初期化されていない場合、コンパイラはエラー メッセージを発行しません。  
  
 定数または値のアドレスを取得できません。  
  
## <a name="example"></a>例  
 この例では、`int`、`p` へのポインターを宣言し、整数変数 `number` のアドレスを代入します。 変数 `number` は `*p` への代入の結果として初期化されます。 この代入ステートメントをコメント アウトする場合は、変数 `number` の初期化が削除されますが、コンパイル時のエラーは発生しません。  

> [!NOTE]
> [`-unsafe`](../../language-reference/compiler-options/unsafe-compiler-option.md) コンパイラ オプションを指定してこの例をコンパイルしてください。
  
 [!code-csharp[address-of-a-variable](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#8)]  
  
## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)
- [ポインター型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [型](../../../csharp/language-reference/keywords/types.md)
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)
- [fixed ステートメント](../../../csharp/language-reference/keywords/fixed-statement.md)
- [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md)
