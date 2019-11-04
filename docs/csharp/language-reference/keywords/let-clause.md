---
title: let 句 - C# リファレンス
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
ms.openlocfilehash: df3df279d2dbdb59a0a94d9afad37d1a7ddf7b57
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422695"
---
# <a name="let-clause-c-reference"></a>let 句 (C# リファレンス)

クエリ式では、後続の句で使用するために、サブ式の結果を保存すると便利な場合があります。 `let` キーワードを使用してこれを行うことができます。これにより新しい範囲変数を作成し、指定した式の結果でそれを初期化します。 値で初期化されると、範囲変数を使用して別の値を格納することはできません。 ただし、範囲変数がクエリ可能型を保持している場合、クエリを実行できます。

## <a name="example"></a>例

次の例で、`let` は 2 つの方法で使用されます。

1. それ自体を照会できる列挙可能な型を作成します。

2. クエリが値変数 `word` に対して `ToLower` を 1 回のみ呼び出すことができるようにします。 `let` を使用しない場合、`where` 句の各述語内で、`ToLower` を呼び出す必要があります。

[!code-csharp[cscsrefQueryKeywords#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Let.cs#28)]

## <a name="see-also"></a>関連項目

- [C# リファレンス](../../language-reference/index.md)
- [クエリ キーワード (LINQ)](query-keywords.md)
- [統合言語クエリ (LINQ)](../../linq/index.md)
- [C# の LINQ の概要](/dotnet/csharp/programming-guide/concepts/linq/)
- [クエリ式の例外の処理](../../linq/handle-exceptions-in-query-expressions.md)
