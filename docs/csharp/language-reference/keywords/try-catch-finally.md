---
title: try-catch-finally - C# リファレンス
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- catch-finally_CSharpKeyword
- catch-finally
helpviewer_keywords:
- finally blocks [C#]
- try-catch statement [C#]
ms.assetid: a1b443b0-ff7a-43ab-b835-0cc9bfbd15ca
ms.openlocfilehash: 66f24994c7fcd2037887507bae65f590e4f90019
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633877"
---
# <a name="try-catch-finally-c-reference"></a>try-catch-finally (C# リファレンス)

通常、`catch` および `finally` は、`try` ブロックのリソースを取得して使用する場合に、対で記述されます。`catch` ブロックで例外的な状況を処理し、`finally` ブロックでリソースを解放します。

 例外の再スローの使用例を含む詳細については、「[try-catch](try-catch.md)」および[例外のスロー](../../../standard/exceptions/index.md)に関するページをご覧ください。 `finally` ブロックの詳細については、「[try-finally](try-finally.md)」を参照してください。

## <a name="example"></a>例

[!code-csharp[csrefKeywordsExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsExceptions/CS/csrefKeywordsExceptions.cs#1)]  

## <a name="c-language-specification"></a>C# 言語仕様

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [C# のキーワード](index.md)
- [try、throw、catch ステートメント (C++)](/cpp/cpp/try-throw-and-catch-statements-cpp)
- [例外処理ステートメント](exception-handling-statements.md)
- [throw](throw.md)
- [方法: 例外を明示的にスローする](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
- [using ステートメント](using-statement.md)
