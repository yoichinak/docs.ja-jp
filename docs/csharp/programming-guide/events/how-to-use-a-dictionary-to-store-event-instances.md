---
title: '方法 : ディクショナリを使用してイベント インスタンスを格納する - C# プログラミング ガイド'
ms.custom: seodec18
ms.date: 03/11/2019
helpviewer_keywords:
- events [C#], storing instances in a Dictionary
ms.assetid: 9512c64d-5aaf-40cd-b941-ca2a592f0064
ms.openlocfilehash: f8522e499887398402f63c7788bbc6c6c4f57782
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/18/2019
ms.locfileid: "57845276"
---
# <a name="how-to-use-a-dictionary-to-store-event-instances-c-programming-guide"></a>方法 : ディクショナリを使用してイベント インスタンスを格納する (C# プログラミング ガイド)

`add` および `remove` カスタム イベント アクセサーの 1 つの用途は、各イベントにフィールドを割り当てることなく多数のイベントを公開することですが、代わりに、次の例に示すように、<xref:System.Collections.Generic.Dictionary%602> インスタンスを使用してイベント インスタンスを格納します。 これが便利なのは、ある型に多数のイベントがあるが、ほとんどのイベントがサブスクライブされないことが予期される場合だけです。

[!code-csharp[csProgGuideEvents#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#9)]

この実装は、C# 言語仕様の[デリゲートの追加と削除](~/_csharplang/spec/delegates.md#delegate-invocation)のための動作に準拠しています。

[lock](../../language-reference/keywords/lock-statement.md) ステートメントは、イベント ハンドラーを使用してディクショナリに "*アクセスする*" ためにのみ使用されていることに注意してください。 デッドロックまたはロックの競合が発生する可能性があるため、`lock` ステートメントの本文でイベント ハンドラーを呼び出さないでください。

## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)
- [イベント](../../../csharp/programming-guide/events/index.md)
- [デリゲート](../../../csharp/programming-guide/delegates/index.md)
