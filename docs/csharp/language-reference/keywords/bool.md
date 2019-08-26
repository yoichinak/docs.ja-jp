---
title: bool キーワード - C# リファレンス
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- bool_CSharpKeyword
- bool
helpviewer_keywords:
- bool keyword [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
ms.openlocfilehash: 3e4e83b52cd6b275e68039693c774f6490f2b88f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606059"
---
# <a name="bool-c-reference"></a>bool (C# リファレンス)

`bool` キーワードは <xref:System.Boolean?displayProperty=nameWithType> の別名です。 ブール値 ([true](true-literal.md) と [false](false-literal.md)) を格納する変数を宣言するために使われます。

> [!NOTE]
> 3 値ロジックをサポートする必要がある場合は、`bool?` 型を使用します。たとえば、3 値ブール型をサポートするデータベースを操作する場合などです。 `bool?` オペランドの場合、定義済みの `&` 演算子と `|` 演算子は 3 値ロジックをサポートします。 詳細については、「[Boolean logical operators (ブール論理演算子)](../operators/boolean-logical-operators.md)」記事の「[Nullable Boolean logical operators (null 許容論理演算子)](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators)」セクションを参照してください。

## <a name="literals"></a>リテラル

`bool` 変数にはブール値を代入できます。 また、`bool` として評価される式も `bool` 変数に代入できます。

[!code-csharp[csrefKeywordsTypes#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#1)]

`bool` 変数の既定値は `false` です。 `bool?` 変数の既定値は `null` です。

## <a name="conversions"></a>変換

C++ では、`bool` 型の値を `int` 型の値に変換できます。つまり、`false` はゼロと同等であり、`true` はゼロ以外の値と同等です。 C# では、`bool` 型と他の型の間に変換はありません。 たとえば、次の `if` ステートメントは C# では無効です。

[!code-csharp[csrefKeywordsTypes#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#2)]

`int` 型の変数をテストするには、0 などの値と明示的に比較する必要があります。次はその例です。

[!code-csharp[csrefKeywordsTypes#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#3)]

## <a name="example"></a>例

この例のプログラムは、キーボードから文字された文字がアルファベットかどうかを調べます。 アルファベットである場合は、小文字か大文字かを調べます。 こうしたチェックは <xref:System.Char.IsLetter%2A> と <xref:System.Char.IsLower%2A> で実行され、どちらも `bool` 型を返します。

[!code-csharp[csrefKeywordsTypes#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#4)]

## <a name="c-language-specification"></a>C# 言語仕様

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [C# のキーワード](./index.md)
- [整数型](../builtin-types/integral-numeric-types.md)
- [組み込み型の一覧表](./built-in-types-table.md)
- [暗黙的な数値変換の一覧表](./implicit-numeric-conversions-table.md)
- [明示的な数値変換の一覧表](./explicit-numeric-conversions-table.md)
