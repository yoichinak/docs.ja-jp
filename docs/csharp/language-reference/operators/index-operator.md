---
title: '[] 演算子 - C# リファレンス'
ms.custom: seodec18
ms.date: 01/10/2019
f1_keywords:
- '[]_CSharpKeyword'
helpviewer_keywords:
- subscript operator [C#]
- square brackets [ ] operator [C#]
- '[] operator [C#]'
- indexing operator [C#]
ms.assetid: 5c16bb45-88f7-45ff-b42c-1af1972b042c
ms.openlocfilehash: 9088393f61d300ee76e56e320bec17b4a79bfebb
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/26/2019
ms.locfileid: "56835591"
---
# <a name="-operator-c-reference"></a>[] 演算子 (C# リファレンス)

通常、角かっこ `[]` は、配列、インデクサー、またはポインター要素へのアクセスに使用されます。

ポインター要素へのアクセスの詳細については、「[ポインターを使用して配列要素にアクセスする方法](../../programming-guide/unsafe-code-pointers/how-to-access-an-array-element-with-a-pointer.md)」を参照してください。

角かっこは、[属性](../../programming-guide/concepts/attributes/index.md)を指定するためにも使用されます。

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="array-access"></a>配列へのアクセス

次の例は、配列要素へのアクセス方法を示しています。

[!code-csharp-interactive[array access](~/samples/snippets/csharp/language-reference/operators/IndexOperatorExamples.cs#Arrays)]

配列インデックスが配列の対応するディメンションの範囲に含まれない場合、<xref:System.IndexOutOfRangeException> がスローされます。

前述の例が示すように、配列型の宣言と配列インスタンスのインスタンス化にも角かっこを使用します。

配列の詳細については、「[配列](../../programming-guide/arrays/index.md)」を参照してください。

## <a name="indexer-access"></a>インデクサーへのアクセス

次の例では、インデクサーへのアクセスを示すために .NET <xref:System.Collections.Generic.Dictionary%602> 型を使用します。

[!code-csharp-interactive[indexer access](~/samples/snippets/csharp/language-reference/operators/IndexOperatorExamples.cs#Indexers)]

インデクサーを使用すると、配列のインデックス作成と同様の方法でユーザー定義型のインスタンスのインデックスを作成することができます。 整数である必要がある配列インデックスとは異なり、任意の型を持つインデクサー引数を宣言できます。

インデクサーの詳細については、「[インデクサー](../../programming-guide/indexers/index.md)」を参照してください。

## <a name="operator-overloadability"></a>演算子のオーバーロード可/不可

要素へのアクセス `[]` はオーバーロード可能な演算子とは見なされていません。 ユーザー定義型を使用したインデックス作成をサポートするには、[インデクサー](../../programming-guide/indexers/index.md)を使用してください。

## <a name="c-language-specification"></a>C# 言語仕様

詳細については、「[C# 言語仕様](../language-specification/index.md)」の「[要素へのアクセス](~/_csharplang/spec/expressions.md#element-access)」と「[ポインターの要素へのアクセス](~/_csharplang/spec/unsafe-code.md#pointer-element-access)」を参照してください。

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミングガイド](../../programming-guide/index.md)
- [C# 演算子](index.md)
- [配列](../../programming-guide/arrays/index.md)
- [インデクサー](../../programming-guide/indexers/index.md)
- [ポインター型](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [属性](../../programming-guide/concepts/attributes/index.md)
- [?. および ?[] 演算子](null-conditional-operators.md)