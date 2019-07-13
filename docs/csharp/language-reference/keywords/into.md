---
title: into - C# リファレンス
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- into_CSharpKeyword
- into
helpviewer_keywords:
- into keyword [C#]
ms.assetid: 81ec62c1-f0b1-4755-8a31-959876e77f65
ms.openlocfilehash: b209062a2a3e563ea8e70cb7883d9bbfa3662231
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631517"
---
# <a name="into-c-reference"></a>into (C# リファレンス)

`into` コンテキスト キーワードは、[group](group-clause.md)、[join](join-clause.md)、または [select](select-clause.md) 句の結果を新しい識別子に保存するための一時的な識別子を作成するために使用できます。 この識別子自体を追加のクエリ コマンドのジェネレーターにすることができます。 `group` または `select` 句で使用する場合、新しい識別子の使用は*継続*と呼ばれることもあります。

## <a name="example"></a>例

次の例では、`into` キーワードを使用して、推定の型 `IGrouping` を持つ一時的な識別子 `fruitGroup` を有効にする方法を示します。 識別子を使用すると、各グループに対して <xref:System.Linq.Enumerable.Count%2A> メソッドを呼び出し、2 つ以上の単語を含むグループのみを選択することができます。

[!code-csharp[cscsrefQueryKeywords#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Into.cs#18)]

`group` 句での `into` の使用は、各グループに対して追加のクエリ操作を実行する場合にのみ必要です。 詳しくは、「[group 句](group-clause.md)」をご覧ください。

`join` 句での `into` の使用例については、「[join 句](join-clause.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [クエリ キーワード (LINQ)](query-keywords.md)
- [LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md)
- [group 句](group-clause.md)
