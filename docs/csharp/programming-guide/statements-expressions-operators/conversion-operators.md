---
title: 変換演算子 - C# プログラミング ガイド
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, conversion operators
- conversion operators [C#]
- operators [C#], conversion
- user-defined conversions [C#]
ms.assetid: c5ad73a3-d57b-4d2b-b4c9-24e3c2856efc
ms.openlocfilehash: 43e81a342377b155fafe26bd0430384cddad5fd4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64608231"
---
# <a name="conversion-operators-c-programming-guide"></a>変換演算子 (C# プログラミング ガイド)

C# を使用すると、クラスまたは構造体に関する変換を宣言し、クラスまたは構造体を別のクラスまたは構造体に、または基本型に変換することができます。 変換は演算子と同様の方法で定義され、変換先の型に由来する名前が付けられます。 変換する引数の型と変換結果の型の両方ではなく一方を、含んでいる型にする必要があります。  
  
 [!code-csharp[csProgGuideStatements#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#10)]  
  
## <a name="conversion-operators-overview"></a>変換演算子の概要

 変換演算子には、次の特徴があります。  
  
- `implicit` として宣言される変換は、必要なときに自動的に発生します。  
  
- `explicit` として宣言される変換には、キャストの呼び出しが必要です。  
  
- すべての変換は、`static` として宣言する必要があります。  
  
## <a name="related-sections"></a>関連項目

 詳細情報  
  
- [変換演算子の使用](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md)  
  
- [キャストと型変換](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
  
- [方法: 構造体間にユーザー定義の変換を実装する](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
  
- [explicit](../../../csharp/language-reference/keywords/explicit.md)  
  
- [implicit](../../../csharp/language-reference/keywords/implicit.md)  
  
- [static](../../../csharp/language-reference/keywords/static.md)  
  
## <a name="see-also"></a>関連項目

- <xref:System.Convert>
- [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)
- [Chained user-defined explicit conversions in C#](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/) (C# でのユーザー定義の明示的変換の連結)
