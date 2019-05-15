---
title: stackalloc キーワード - C# リファレンス
ms.custom: seodec18
ms.date: 04/10/2019
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
helpviewer_keywords:
- stackalloc keyword [C#]
ms.openlocfilehash: 654e225ef98b13aeb4f689e17b1ff378e6002d28
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063916"
---
# <a name="stackalloc-c-reference"></a>stackalloc (C# リファレンス)

`stackalloc` キーワードは、スタックにメモリ ブロックを割り当てるために使用されます。

```csharp
Span<int> block = stackalloc int[100];
```

割り当てられたブロックを `int*` ではなく <xref:System.Span%601?displayName=nameWithType> に割り当てると、安全なブロックでスタックを割り当てることができます。 `unsafe` コンテキストは必須ではありません。

## <a name="remarks"></a>解説

このキーワードは、ローカル変数初期化子でのみ有効です。 次のコードはコンパイル エラーになります。

```csharp
int* block;
// The following assignment statement causes compiler errors. You
// can use stackalloc only when declaring and initializing a local
// variable.
block = stackalloc int[100];
Span<int> span;
// The following assignment statement causes compiler errors. You
// can use stackalloc only when declaring and initializing a local
// variable.
span = stackalloc int[100];
```

C# 7.3 以降では、`stackalloc` 配列に対して配列初期化子構文を使うことができます。 次のすべての宣言では、値が整数 `1`、`2`、`3` である 3 つの要素を含む配列が宣言されています。 2 回目の初期化でメモリを <xref:System.ReadOnlySpan%601> に割り当て、メモリを変更できないことを示します。

```csharp
// Valid starting with C# 7.3
Span<int> first = stackalloc int[3] { 1, 2, 3 };
ReadOnlySpan<int> second = stackalloc int[] { 1, 2, 3 };
Span<int> third = stackalloc[] { 1, 2, 3 };
```

ポインター型が使用される場合、`stackalloc` には [unsafe](unsafe.md) コンテキストが必要です。 詳細については、「[アンセーフ コードとポインター](../../programming-guide/unsafe-code-pointers/index.md)」を参照してください。

`stackalloc` は、C ランタイム ライブラリの [_alloca](/cpp/c-runtime-library/reference/alloca) に似ています。

## <a name="examples"></a>使用例

次の例では、フィボナッチ数列の最初の 20 個の数値を計算して表示します。 それぞれの数値が、前の 2 つの数値の和になっています。 このコードでは、`int` 型の要素を 20 個保持できるサイズのメモリ ブロックが、ヒープではなくスタックに割り当てられ、 そのブロックのアドレスは `Span` `fib` に格納されます。 このメモリは、ガベージ コレクションの対象にはならないため、[fixed](fixed-statement.md) を使用して固定する必要はありません。 メモリ ブロックの有効期間は、そのブロックを定義するメソッドの有効期間に限定されます。 メソッドから制御が戻る前に、メモリを解放することはできません。

[!code-csharp[csrefKeywordsOperator#15](~/samples/snippets/csharp/keywords/StackAllocExamples.cs#1)]

次の例では、整数の `stackalloc` 配列を、要素ごとに 1 ビットが設定されているビット マスクに初期化しています。 これは、C# 7.3 以降で使用可能な新しい初期化子の構文を示しています。

[!code-csharp[csrefKeywordsOperator#15](~/samples/snippets/csharp/keywords/StackAllocExamples.cs#2)]

## <a name="security"></a>セキュリティ

アンセーフ コードはセーフ コードよりも安全性が低いため、可能な限り <xref:System.Span%601> または <xref:System.ReadOnlySpan%601> を使用してください。 ポインターと共に使用したとしても、`stackalloc` を使用すると、共通言語ランタイム (CLR) のバッファー オーバーラン検出機能が自動的に有効になります。 バッファー オーバーランが検出されると、悪意のあるコードが実行される可能性を最小限に抑えるために、プロセスはできる限り迅速に終了されます。

## <a name="c-language-specification"></a>C# 言語仕様

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [C# のキーワード](index.md)
- [演算子のキーワード](operator-keywords.md)
- [アンセーフ コードとポインター](../../programming-guide/unsafe-code-pointers/index.md)
