---
title: '方法: クエリ式で暗黙的に型指定されるローカル変数および配列を使用する - C# プログラミング ガイド'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#], how to use
ms.assetid: 6b7354d2-af79-427a-b6a8-f74eb8fd0b91
ms.openlocfilehash: 8e3534abf961ba7b8a41eed592455962e5b551e7
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979035"
---
# <a name="how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression-c-programming-guide"></a>方法: クエリ式で暗黙的に型指定されるローカル変数および配列を使用する (C# プログラミング ガイド)
コンパイラによってローカル変数の型が決定されるようにする場合は、暗黙的に型指定されたローカル変数を使用できます。 クエリ式でよく使用する匿名型を格納するには、暗黙的に型指定されたローカル変数を使用する必要があります。 以下の例では、クエリで暗黙的に型指定されたローカル変数を省略できる場合と、使用しなければならない場合の両方を示します。  
  
 暗黙的に型指定されたローカル変数は、[var](../../../csharp/language-reference/keywords/var.md) コンテキスト キーワードを使用して宣言します。 詳細については、「[暗黙的に型指定されるローカル変数](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)」と「[暗黙的に型指定される配列](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例は、`var` キーワードが必須である一般的なシナリオ (匿名型のシーケンスを生成するクエリ) を示しています。 このシナリオでは、匿名型の型名にアクセスできないため、`var`を使用して `foreach` ステートメントのクエリ変数と反復変数の両方を暗黙的に型指定する必要があります。 匿名型の詳細については、「[匿名型](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)」を参照してください。  
  
 [!code-csharp[csProgGuideLINQ#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#32)]  
  
## <a name="example"></a>例  
 次の例では、同様の状況で `var` キーワードを使用しています。ただし、この場合、`var` の使用はオプションです。 `student.LastName` は文字列であるため、クエリを実行すると文字列のシーケンスが返されます。 したがって、`queryID` の型は、`var` ではなく `System.Collections.Generic.IEnumerable<string>` として宣言できます。 `var` キーワードは利便性のために使用されます。 この例では、`foreach` ステートメントの反復変数は文字列として明示的に型指定されていますが、代わりに `var` を使用して宣言することができます。 反復変数の型は匿名型ではないため、`var` の使用はオプションであり、必須ではありません。 `var` 自体は型ではなく、型を推論して割り当てるようコンパイラに指示する命令です。  
  
 [!code-csharp[csProgGuideLINQ#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#33)]  
  
## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)
- [拡張メソッド](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
- [統合言語クエリ (LINQ)](../../../csharp/linq/index.md)
- [var](../../../csharp/language-reference/keywords/var.md)
- [LINQ クエリ式](../../../csharp/programming-guide/linq-query-expressions/index.md)
