---
title: add - C# リファレンス
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- add_CSharpKeyword
helpviewer_keywords:
- add event accessor [C#]
ms.assetid: faf30b99-10e8-45cd-ab9a-57585d4d1d8d
ms.openlocfilehash: 1f699e5729354d13bfbe29810bf2c4baf91d2382
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59147915"
---
# <a name="add-c-reference"></a>add (C# リファレンス)
`add` コンテキスト キーワードは、カスタム イベント アクセサーを定義するときに使用されます。このアクセサーは、クライアント コードが[イベント](../../../csharp/language-reference/keywords/event.md)をサブスクライブするときに呼び出されます。 カスタムの `add` アクセサーを指定するときは、[remove](../../../csharp/language-reference/keywords/remove.md) アクセサーも指定する必要があります。  
  
## <a name="example"></a>例  
 次の例は、カスタムの `add` アクセサーと [remove](../../../csharp/language-reference/keywords/remove.md) アクセサーが指定されているイベントを示しています。 完全な例については、「[方法: インターフェイス イベントを実装する](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)」をご覧ください。  
  
[!code-csharp[csrefKeywordsContextual#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#15)]
  
 通常は、独自のカスタム イベント アクセサーを提供する必要はありません。 イベントを宣言するときにコンパイラで自動生成されるアクセサーは、ほとんどのシナリオで利用することができます。  
  
## <a name="see-also"></a>関連項目

- [イベント](../../../csharp/programming-guide/events/index.md)
