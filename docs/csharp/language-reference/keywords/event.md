---
title: event - C# リファレンス
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- event
- remove
- event_CSharpKeyword
- add
helpviewer_keywords:
- event keyword [C#]
ms.assetid: 7858fd85-153b-4259-85d0-6aa13c35f174
ms.openlocfilehash: 9575d6e998ff709b06f1da21abd17a3629c17029
ms.sourcegitcommit: 26f4a7697c32978f6a328c89dc4ea87034065989
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/28/2019
ms.locfileid: "66251037"
---
# <a name="event-c-reference"></a>event (C# リファレンス)
`event` キーワードを使用し、パブリッシャー クラス内にイベントを宣言します。  
  
## <a name="example"></a>例  
 次の例では、基になるデリゲート型として <xref:System.EventHandler> を使用するイベントを宣言し、発生させる方法について説明します。 ジェネリック <xref:System.EventHandler%601> デリゲート型を使う方法、およびイベントをサブスクライブしてイベント ハンドラー メソッドを作成する方法も示す完全なコード例については、「[方法: .NET Framework ガイドラインに準拠したイベントを発行する](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)」をご覧ください。  
  
 [!code-csharp[csrefKeywordsModifiers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#7)]
  
 イベントは、宣言元 (パブリッシャー クラス) のクラスまたは構造体内でしか呼び出せない特殊なマルチキャスト デリゲートです。 他のクラスまたは構造体がイベントを受信登録した場合、パブリッシャー クラスがイベントを発生させると、他のクラスまたは構造体のイベント ハンドラー メソッドが呼び出されます。 詳細およびコード例については、「[イベント](../../../csharp/programming-guide/events/index.md)」および「[デリゲート](../../../csharp/programming-guide/delegates/index.md)」を参照してください。  
  
 イベントは、[public](../../../csharp/language-reference/keywords/public.md)、[private](../../../csharp/language-reference/keywords/private.md)、[protected](../../../csharp/language-reference/keywords/protected.md)、[internal](../../../csharp/language-reference/keywords/internal.md)、[protected internal](../../../csharp/language-reference/keywords/protected-internal.md) または [private protected](../../../csharp/language-reference/keywords/private-protected.md) としてマークできます。 これらのアクセス修飾子により、クラスのユーザーがイベントにアクセスする方法が定義されます。 詳細については、「[アクセス修飾子](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)」を参照してください。  
  
## <a name="keywords-and-events"></a>キーワードとイベント  
 イベントには次のキーワードが適用されます。  
  
|キーワード|説明|詳細情報|  
|-------------|-----------------|--------------------------|  
|[static](../../../csharp/language-reference/keywords/static.md)|クラスのインスタンスが存在しない場合でも、呼び出し元がいつでもイベントを使用できるようになります。|[静的クラスと静的クラス メンバー](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)|  
|[virtual](../../../csharp/language-reference/keywords/virtual.md)|[override](../../../csharp/language-reference/keywords/override.md) キーワードを使用してイベントの動作をオーバーライドすることを派生クラスに許可します。|[継承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)|  
|[sealed](../../../csharp/language-reference/keywords/sealed.md)|派生クラスでは、それが仮想ではなくなったことを指定します。||  
|[abstract](../../../csharp/language-reference/keywords/abstract.md)|コンパイラはイベント アクセサー ブロックの `add` と `remove` を生成しません。したがって、派生クラスは固有の実装を提供する必要があります。||  
  
 イベントは、[static](../../../csharp/language-reference/keywords/static.md) キーワードを使用して静的イベントとして宣言されることもあります。 その場合、クラスのインスタンスが存在しなくても、呼び出し元がいつでもイベントを使用できるようになります。 詳細については、「[静的クラスと静的クラス メンバー](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)」を参照してください。  
  
 イベントは、[virtual](../../../csharp/language-reference/keywords/virtual.md) キーワードを使用して仮想イベントとしてマークできます。 その場合、派生クラスでは、[override](../../../csharp/language-reference/keywords/override.md) キーワードを使用してイベントの動作をオーバーライドできます。 詳細については、「[継承](../../../csharp/programming-guide/classes-and-structs/inheritance.md)」を参照してください。 仮想イベントをオーバーライドするイベントは、[sealed](../../../csharp/language-reference/keywords/sealed.md) にすることもできます。その場合、派生クラスでは、イベントが仮想でなくなります。 最後に、イベントは [abstract](../../../csharp/language-reference/keywords/abstract.md) として宣言できます。その場合、コンパイラはイベント アクセサー ブロックの `add` と `remove` を生成しません。 したがって、派生クラスごとに固有の実装を提供する必要があります。  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目

- [C# リファレンス](../../../csharp/language-reference/index.md)
- [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)
- [C# のキーワード](../../../csharp/language-reference/keywords/index.md)
- [add](../../../csharp/language-reference/keywords/add.md)
- [remove](../../../csharp/language-reference/keywords/remove.md)
- [修飾子](../../../csharp/language-reference/keywords/modifiers.md)
- [方法: デリゲートを結合する (マルチキャスト デリゲート)](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)
