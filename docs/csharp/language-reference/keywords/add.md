---
title: add - C# リファレンス
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- add_CSharpKeyword
helpviewer_keywords:
- add event accessor [C#]
ms.assetid: faf30b99-10e8-45cd-ab9a-57585d4d1d8d
ms.openlocfilehash: 1cf82e3d048e465d533e87dc639a13071b41544a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606043"
---
# <a name="add-c-reference"></a>add (C# リファレンス)
`add` コンテキスト キーワードは、カスタム イベント アクセサーを定義するときに使用されます。このアクセサーは、クライアント コードが[イベント](./event.md)をサブスクライブするときに呼び出されます。 カスタムの `add` アクセサーを指定するときは、[remove](./remove.md) アクセサーも指定する必要があります。  
  
## <a name="example"></a>例  
 次の例は、カスタムの `add` アクセサーと [remove](./remove.md) アクセサーが指定されているイベントを示しています。 完全な例については、「[方法: インターフェイス イベントを実装する](../../programming-guide/events/how-to-implement-interface-events.md)」をご覧ください。  
  
[!code-csharp[csrefKeywordsContextual#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#15)]
  
 通常は、独自のカスタム イベント アクセサーを提供する必要はありません。 イベントを宣言するときにコンパイラで自動生成されるアクセサーは、ほとんどのシナリオで利用することができます。  
  
## <a name="see-also"></a>関連項目

- [イベント](../../programming-guide/events/index.md)
