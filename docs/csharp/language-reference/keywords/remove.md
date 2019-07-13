---
title: remove コンテキスト キーワード - C# リファレンス
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- remove_CSharpKeyword
helpviewer_keywords:
- remove event accessor [C#]
ms.assetid: c8223426-c17b-4fe2-8406-01564cf1dd2b
ms.openlocfilehash: b5c604cbb0fef158750b0fa487374ab293795fc7
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633719"
---
# <a name="remove-c-reference"></a>remove (C# リファレンス)

`remove` コンテキスト キーワードは、カスタム イベント アクセサーを定義するときに使用されます。このアクセサーは、クライアント コードが[イベント](event.md)から登録を解除するときに呼び出されます。 カスタムの `remove` アクセサーを指定するときは、[add](add.md) アクセサーも指定する必要があります。

## <a name="example"></a>例

次の例は、カスタムの [add](add.md) アクセサーと `remove` アクセサーが指定されているイベントを示しています。 完全な例については、「[方法: インターフェイス イベントを実装する](../../programming-guide/events/how-to-implement-interface-events.md)」をご覧ください。

 [!code-csharp[csrefKeywordsContextual#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#15)]

通常は、独自のカスタム イベント アクセサーを提供する必要はありません。 イベントを宣言するときにコンパイラで自動生成されるアクセサーは、ほとんどのシナリオで利用することができます。

## <a name="see-also"></a>関連項目

- [イベント](../../programming-guide/events/index.md)
