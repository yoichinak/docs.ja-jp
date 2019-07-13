---
title: 既定の値式 - C# プログラミング ガイド
ms.custom: seodec18
description: 既定の値式は、あらゆる参照型または値型の既定値を生成します
ms.date: 04/25/2018
helpviewer_keywords:
- generics [C#], default keyword
- default keyword [C#], generic programming
ms.openlocfilehash: 8e10a5de73e8d49f1a380fb8945b98ac797ef270
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54575542"
---
# <a name="default-value-expressions-c-programming-guide"></a>既定の値式 (C# プログラミング ガイド)

既定の値式 `default(T)` では、型 `T` の既定値が生成されます。 次の表は、さまざまな型に対して生成される値の一覧です。

|型|既定値|
|---------|---------|
|すべての参照型|`null`|
|数値型|0|
|[bool](../../language-reference/keywords/bool.md)|`false`|
|[char](../../language-reference/keywords/char.md)|`'\0'`|
|[enum](../../language-reference/keywords/enum.md)|式 `(E)0` によって生成される値。`E` は列挙型識別子です。|
|[struct](../../language-reference/keywords/struct.md)|すべての値型フィールドが既定値に設定され、すべての参照型フィールドが `null` に設定された値。|
|null 許容型|<xref:System.Nullable%601.HasValue%2A> プロパティが `false` で、<xref:System.Nullable%601.Value%2A> プロパティが未定義のインスタンス。|

既定の値式は、ジェネリック クラスおよびメソッドで特に役立ちます。 ジェネリックの使用で発生する問題の 1 つは、次のことがあらかじめわかっていない場合に、パラメーター化された型 `T` に既定値を割り当てる方法です。

- `T` が参照型または値型のどちらか。
- `T` が値型の場合、数値か構造体か。

 パラメーター化された型 `T` の変数 `t` が指定されている場合、ステートメント `t = null` は `T` が参照型の場合にのみ有効です。 割り当て `t = 0` は数値型でのみ機能し、構造体では機能しません。 これを解決するには、既定の値式を使用します。

```csharp
T t = default(T);
```

`default(T)` 式は、ジェネリック クラスやメソッドに制限されません。 既定の値式は、任意のマネージド型で使用できます。 次の式のいずれかが有効です。

 [!code-csharp[csProgGuideGenerics#1](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-value-expressions.cs)]

 `GenericList<T>` クラスの次の例は、ジェネリック クラスに `default(T)` 演算子を使う方法を示します。 詳細については、「[ジェネリックの概要](../generics/introduction-to-generics.md)」を参照してください。

 [!code-csharp[csProgGuideGenerics#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#Snippet41)]

## <a name="default-literal-and-type-inference"></a>既定のリテラルと型推論

C# 7.1 より、コンパイラが式の型を推定できる場合、`default` リテラルを既定の値式に使用することができます。 `default` リテラルは同等の `default(T)` (`T` は推定型) と同じ値を生成します。 これにより、型を複数回宣言する冗長さが低減され、コードが簡潔になります。 `default` リテラルは、次の場所のいずれかで使用できます。

- 変数初期化子
- 変数の代入
- オプションのパラメーターの既定値の宣言
- メソッド呼び出しの引数の値の提供
- return ステートメント (または式のようなメンバー内の式)

次の例は、既定の値式の `default` リテラルの多くの使用法を示しています。

[!code-csharp[csProgGuideGenerics#3](../../../../samples/snippets/csharp/programming-guide/statements-expressions-operators/default-literal.cs)]

## <a name="see-also"></a>関連項目

- <xref:System.Collections.Generic>
- [C# プログラミング ガイド](../index.md)
- [ジェネリック (C# プログラミング ガイド)](../generics/index.md)
- [ジェネリック メソッド](../generics/generic-methods.md)
- [.NET のジェネリック](~/docs/standard/generics/index.md)
- [既定値の一覧表](../../language-reference/keywords/default-values-table.md)
