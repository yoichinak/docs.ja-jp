---
title: Main() とコマンドライン引数 - C# プログラミング ガイド
ms.custom: seodec18
ms.date: 08/02/2017
f1_keywords:
- CS5001
- main_CSharpKeyword
- Main
helpviewer_keywords:
- Main method [C#]
- C# language, command-line arguments
- arguments [C#], command-line
- command line [C#], arguments
- command-line arguments [C#], Main method
ms.assetid: 73a17231-cf96-44ea-aa8a-54807c6fb1f4
ms.openlocfilehash: f1cbbc6081c0e2f3e29d49f413e00c7346ea7e60
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61678843"
---
# <a name="main-and-command-line-arguments-c-programming-guide"></a>Main() とコマンドライン引数 (C# プログラミング ガイド)

`Main` メソッドは、C# アプリケーションのエントリ ポイントです (ライブラリおよびサービスでは、エントリ ポイントとしての `Main` メソッドは必要ありません)。アプリケーションを起動すると、最初に `Main` メソッドが呼び出されます。

 C# プログラムのエントリ ポイントは 1 つのみです。 `Main` メソッドを持つクラスが 2 つ以上ある場合、プログラムをコンパイルする際に **/main** コンパイラ オプションを使用して、どの `Main` メソッドをエントリ ポイントとして使用するかを指定する必要があります。 詳細については、「[/main (C# コンパイラ オプション)](../../../csharp/language-reference/compiler-options/main-compiler-option.md)」を参照してください。

 [!code-csharp[csProgGuideMain#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#17)]

## <a name="overview"></a>概要

- `Main` メソッドは実行可能プログラムのエントリ ポイントであり、ここでプログラムの制御を開始および終了します。
- `Main` は、クラスまたは構造体の内部で宣言されます。 `Main` は [static](../../../csharp/language-reference/keywords/static.md) である必要がありますが、[public](../../../csharp/language-reference/keywords/public.md) である必要はありません (先ほどの例では、既定の [private](../../../csharp/language-reference/keywords/private.md) のアクセスを受け取ります)。外側のクラスまたは構造体は、static である必要はありません。
- `Main` の戻り値の型は、`void` または `int` のいずれかになります。C# 7.1 以降では `Task` または `Task<int>` になる場合もあります。
- `Main` で `Task` または `Task<int>` が返される場合に限り、`Main` の宣言に [`async`](../../language-reference/keywords/async.md) 修飾子を含めることができます。 この条件により、`async void Main` メソッドが明確に除外されることに注意してください。
- `Main` メソッドを宣言する際、コマンドライン引数を含む `string[]` パラメーターは指定してもしなくてもかまいません。 Visual Studio を使用して Windows アプリケーションを作成する場合、このパラメーターを手動で追加するか <xref:System.Environment> クラスを使用して、コマンドライン引数を取得できます。 パラメーターは、インデックス 0 のコマンドライン引数として読み取られます。 C や C++ とは異なり、プログラムの名前が最初のコマンドライン引数として扱われることはありません。

コンソール アプリケーションの `Main` で `await` を使用して非同期操作を開始する必要がある場合、戻り値の型 `async`、`Task`、`Task<int>` を追加することでプログラム コードを簡略化できます。

## <a name="c-language-specification"></a>C# 言語仕様

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>関連項目

- [csc.exe を使用したコマンド ラインからのビルド](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)
- [メソッド](../../../csharp/programming-guide/classes-and-structs/methods.md)
- [インサイド C# プログラム](../../../csharp/programming-guide/inside-a-program/index.md)
