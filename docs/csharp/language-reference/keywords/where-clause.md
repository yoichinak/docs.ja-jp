---
title: where 句 - C# リファレンス
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- whereclause_CSharpKeyword
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
ms.openlocfilehash: fc259f0e0a83d2f55bf2d50fa336c9201b8b5bef
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633225"
---
# <a name="where-clause-c-reference"></a>where 句 (C# リファレンス)

`where` 句をクエリ式で使用して、クエリ式で返されるデータ ソースの要素を指定します。 ブール条件 (*述語*) を (範囲変数で参照される) 各ソース要素に適用し、指定した条件に該当するものを返します。 単一のクエリ式に複数の `where` 句を含めることができ、単一の句に複数の述語部分式を含めることができます。

## <a name="example"></a>例

次の例では、`where` 句で、5 未満の数値を除くすべての数値を除外します。 `where` 句を削除すると、データ ソースのすべての数値が返されます。 式 `num < 5` は、各要素に適用される述語です。

[!code-csharp[cscsrefQueryKeywords#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#5)]

## <a name="example"></a>例

単一の `where` 句内には、[&&](../operators/boolean-logical-operators.md#conditional-logical-and-operator-) および [&#124;&#124;](../operators/boolean-logical-operators.md#conditional-logical-or-operator-) 演算子を使用して、必要な数の述語を指定できます。 次の例のクエリでは、5 未満の偶数のみを選択するために 2 つの述語を指定します。

[!code-csharp[cscsrefQueryKeywords#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#6)]  

## <a name="example"></a>例

`where` 句には、ブール値を返す 1 つ以上のメソッドを含めることができます。 次の例の `where` 句では、範囲変数の現在の値が偶数であるか、奇数であるかを判断するためのメソッドを使用します。

[!code-csharp[cscsrefQueryKeywords#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Where.cs#7)]

## <a name="remarks"></a>解説

`where` 句はフィルター メカニズムです。 クエリ式のほぼどこにでも指定できますが、最初の句や最後の句にすることはできません。 `where` 句は、ソース要素のフィルター処理をグループ化の前に行うか後に行うかによって、[group](group-clause.md) 句の前または後に指定できます。

指定した述語がデータ ソース内の要素に対して有効でない場合は、コンパイル時エラーが発生します。 これは、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] で提供される厳密な型チェックの 1 つの利点です。

コンパイル時に、`where` キーワードは <xref:System.Linq.Enumerable.Where%2A> 標準クエリ演算子メソッドの呼び出しに変換されます。

## <a name="see-also"></a>関連項目

- [クエリ キーワード (LINQ)](query-keywords.md)
- [from 句](from-clause.md)
- [select 句](select-clause.md)
- [データのフィルター処理](../../programming-guide/concepts/linq/filtering-data.md)
- [LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md)
- [C# の LINQ の概要](../../programming-guide/concepts/linq/getting-started-with-linq.md)
