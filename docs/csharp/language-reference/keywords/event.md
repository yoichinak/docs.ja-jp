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
ms.openlocfilehash: 4149663422908069b5b65ed3c32ccc6dbdfd7729
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605805"
---
# <a name="event-c-reference"></a>event (C# リファレンス)
`event` キーワードを使用し、パブリッシャー クラス内にイベントを宣言します。  
  
## <a name="example"></a>例  
 次の例では、基になるデリゲート型として <xref:System.EventHandler> を使用するイベントを宣言し、発生させる方法について説明します。 ジェネリック <xref:System.EventHandler%601> デリゲート型を使う方法、およびイベントをサブスクライブしてイベント ハンドラー メソッドを作成する方法も示す完全なコード例については、「[方法: .NET Framework ガイドラインに準拠したイベントを発行する](../../programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)」をご覧ください。  
  
 [!code-csharp[csrefKeywordsModifiers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#7)]
  
 イベントは、宣言元 (パブリッシャー クラス) のクラスまたは構造体内でしか呼び出せない特殊なマルチキャスト デリゲートです。 他のクラスまたは構造体がイベントを受信登録した場合、パブリッシャー クラスがイベントを発生させると、他のクラスまたは構造体のイベント ハンドラー メソッドが呼び出されます。 詳細およびコード例については、「[イベント](../../programming-guide/events/index.md)」および「[デリゲート](../../programming-guide/delegates/index.md)」を参照してください。  
  
 イベントは、[public](./public.md)、[private](./private.md)、[protected](./protected.md)、[internal](./internal.md)、[protected internal](./protected-internal.md) または [private protected](./private-protected.md) としてマークできます。 これらのアクセス修飾子により、クラスのユーザーがイベントにアクセスする方法が定義されます。 詳細については、「[アクセス修飾子](../../programming-guide/classes-and-structs/access-modifiers.md)」を参照してください。  
  
## <a name="keywords-and-events"></a>キーワードとイベント  
 イベントには次のキーワードが適用されます。  
  
|Keyword|説明|詳細情報|  
|-------------|-----------------|--------------------------|  
|[static](./static.md)|クラスのインスタンスが存在しない場合でも、呼び出し元がいつでもイベントを使用できるようになります。|[静的クラスと静的クラス メンバー](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)|  
|[virtual](./virtual.md)|[override](./override.md) キーワードを使用してイベントの動作をオーバーライドすることを派生クラスに許可します。|[継承](../../programming-guide/classes-and-structs/inheritance.md)|  
|[sealed](./sealed.md)|派生クラスでは、それが仮想ではなくなったことを指定します。||  
|[abstract](./abstract.md)|コンパイラはイベント アクセサー ブロックの `add` と `remove` を生成しません。したがって、派生クラスは固有の実装を提供する必要があります。||  
  
 イベントは、[static](./static.md) キーワードを使用して静的イベントとして宣言されることもあります。 その場合、クラスのインスタンスが存在しなくても、呼び出し元がいつでもイベントを使用できるようになります。 詳細については、「[静的クラスと静的クラス メンバー](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)」を参照してください。  
  
 イベントは、[virtual](./virtual.md) キーワードを使用して仮想イベントとしてマークできます。 その場合、派生クラスでは、[override](./override.md) キーワードを使用してイベントの動作をオーバーライドできます。 詳細については、「[継承](../../programming-guide/classes-and-structs/inheritance.md)」を参照してください。 仮想イベントをオーバーライドするイベントは、[sealed](./sealed.md) にすることもできます。その場合、派生クラスでは、イベントが仮想でなくなります。 最後に、イベントは [abstract](./abstract.md) として宣言できます。その場合、コンパイラはイベント アクセサー ブロックの `add` と `remove` を生成しません。 したがって、派生クラスごとに固有の実装を提供する必要があります。  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [C# のキーワード](./index.md)
- [add](./add.md)
- [remove](./remove.md)
- [修飾子](./modifiers.md)
- [方法: デリゲートを結合する (マルチキャスト デリゲート)](../../programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)
