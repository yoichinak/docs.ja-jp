---
title: . 演算子 - C# リファレンス
ms.custom: seodec18
ms.date: 02/25/2019
f1_keywords:
- ._CSharpKeyword
helpviewer_keywords:
- member access operator (.) [C#]
- . operator [C#]
- dot operator (.) [C#]
ms.assetid: a1f54b52-b686-4ae5-a48e-a2a9ebd0eb7b
ms.openlocfilehash: 2661676d53deb874c5e5a90b4443b301730e09df
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/26/2019
ms.locfileid: "56836462"
---
# <a name="-operator-c-reference"></a>. 演算子 (C# リファレンス)

ドット (`.`) は、通常、メンバー アクセスに使用されます。

以下の例に示すように、名前空間のメンバーまたは型にアクセスするために `.` トークンを使います。

- 次の [`using` ディレクティブ](../keywords/using-directive.md)の例に示すように、`.` を使って、名前空間内の入れ子になった名前空間にアクセスします。

  [!code-csharp[nested namespaces](~/samples/snippets/csharp/language-reference/operators/MemberAccessExamples.cs#NestedNamespace)]

- 次のコードに示すように、`.` を使って "*修飾名*" を作成して名前空間内の型にアクセスします。

  [!code-csharp[qualified name](~/samples/snippets/csharp/language-reference/operators/MemberAccessExamples.cs#QualifiedName)]

  [`using` ディレクティブ](../keywords/using-directive.md)を使い、必要に応じて修飾名を利用します。

- 次のコードに示すように、`.` を使って、[型のメンバー](../../programming-guide/classes-and-structs/index.md#members) (静的および非静的) にアクセスします。

  [!code-csharp-interactive[type members](~/samples/snippets/csharp/language-reference/operators/MemberAccessExamples.cs#TypeMemberAccess)]

また、`.` を使って[拡張メソッド](../../programming-guide/classes-and-structs/extension-methods.md)を呼び出すこともできます。

## <a name="operator-overloadability"></a>演算子のオーバーロード可/不可

`.` 演算子はオーバーロードできません。

## <a name="c-language-specification"></a>C# 言語仕様

詳細については、[C# 言語仕様](../language-specification/index.md)に関するページの「[Member access (メンバー アクセス)](~/_csharplang/spec/expressions.md#member-access)」を参照してください。

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミングガイド](../../programming-guide/index.md)
- [C# 演算子](index.md)
- [?. および ?[] 演算子](null-conditional-operators.md)