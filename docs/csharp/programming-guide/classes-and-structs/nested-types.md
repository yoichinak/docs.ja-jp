---
title: 入れ子にされた型 - C# プログラミング ガイド
ms.custom: seodec18
ms.date: 07/10/2017
helpviewer_keywords:
- nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
ms.openlocfilehash: de2e369702c48047835bc49b98df8f48fbd13480
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596526"
---
# <a name="nested-types-c-programming-guide"></a>入れ子にされた型 (C# プログラミング ガイド)
[クラス](../../language-reference/keywords/class.md)や[構造体](../../language-reference/keywords/struct.md)の中で定義された型は、入れ子にされた型と呼ばれます。 次に例を示します。  
  
 [!code-csharp[csProgGuideObjects#68](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#68)]  
  
外側の型がクラスまたは構造体のいずれであっても、入れ子にされた型は既定で [private](../../language-reference/keywords/private.md) になります。これらにはその包含する型からのみアクセスできます。 前の例では、`Nested` クラスは外部の型にアクセスできません。 

次のように、[アクセス修飾子](../../language-reference/keywords/access-modifiers.md)を指定して、入れ子にされた型のアクセシビリティを定義することもできます。

- **クラス**の入れ子にされた型は、[public](../../language-reference/keywords/public.md)、[protected](../../language-reference/keywords/protected.md)、[internal](../../language-reference/keywords/internal.md)、[protected internal](../../language-reference/keywords/protected-internal.md)、[private](../../language-reference/keywords/private.md)、[private protected](../../language-reference/keywords/private-protected.md) になります。 

   ただし、[シール クラス](../../language-reference/keywords/sealed.md)内で `protected`、`protected internal`、`private protected` の入れ子にされたクラスを定義すると、コンパイラの警告 [CS0628](../../misc/cs0628.md)、"新規のプロテクト メンバーがシール クラスで宣言されました" が生成されます。
  
- **構造体**の入れ子にされた型は、は、[public](../../language-reference/keywords/public.md)、[internal](../../language-reference/keywords/internal.md)、または [private](../../language-reference/keywords/private.md) のいずれかが可能です。
  
次の例では、`Nested` クラスを public にします。
  
 [!code-csharp[csProgGuideObjects#69](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#69)]  
  
 入れ子にされた型 (内側の型) は、包含する型 (外側の型) にアクセスできます。 包含する型にアクセスするには、その型を引数として入れ子にされた型のコンストラクターに渡します。 次に例を示します。  
  
 [!code-csharp[csProgGuideObjects#70](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#70)]  
  
 入れ子にされた型は、包含する型にアクセス可能なすべてのメンバーにアクセスできます。 入れ子にされた型は、継承されたプロテクト メンバーを含む、包含する型のプライベート メンバーとプロテクト メンバーにアクセスできます。  
  
 上記の宣言では、クラス `Nested` の完全名は `Container.Nested` です。 これは、次のように入れ子になったクラスの新しいインスタンスを作成するときに使用される名前です。  
  
 [!code-csharp[csProgGuideObjects#71](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#71)]  
  
## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [クラスと構造体](./index.md)
- [アクセス修飾子](./access-modifiers.md)
- [コンストラクター](./constructors.md)
