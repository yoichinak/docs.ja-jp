---
title: '方法: Null 許容型を識別する - C# プログラミング ガイド'
ms.custom: seodec18
description: 型が Null 許容型か、インスタンスが Null 許容型であるかどうかを判断する方法について学習します。
ms.date: 09/24/2018
helpviewer_keywords:
- nullable types [C#], identifying
ms.assetid: d4b67ee2-66e8-40c1-ae9d-545d32c71387
ms.openlocfilehash: 73017b8f4c4c046b428d5270a2ef0241c565b07d
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/21/2019
ms.locfileid: "67307046"
---
# <a name="how-to-identify-a-nullable-type-c-programming-guide"></a>方法: Null 許容型を識別する (C# プログラミング ガイド)

次の例は、<xref:System.Type?displayProperty=nameWithType> インスタンスがクローズ ジェネリック null 許容型 (つまり、指定された型パラメーター `T` を使用する <xref:System.Nullable%601?displayProperty=nameWithType> 型) を表すかどうかを判断する方法を示しています。

[!code-csharp-interactive[whether Type is nullable](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#1)]

例で示されているとおり、<xref:System.Type?displayProperty=nameWithType> オブジェクトの作成には、[typeof](../../language-reference/operators/type-testing-and-conversion-operators.md#typeof-operator) 演算子を使用します。  
  
インスタンスが Null 許容型かどうかを判断したい場合は、<xref:System.Type> インスタンスが前述のコードでテストされるように、<xref:System.Object.GetType%2A?displayProperty=nameWithType> メソッドは使用しないでください。 Null 許容型のインスタンスで <xref:System.Object.GetType%2A?displayProperty=nameWithType> メソッドを呼び出した場合、そのインスタンスは <xref:System.Object> に[ボクシング](using-nullable-types.md#boxing-and-unboxing)されます。 Null 許容型の null 以外のインスタンスのボクシングは、基になる型の値のボクシングと等しいので、<xref:System.Object.GetType%2A> は、Null 許容型の基になる型を表す <xref:System.Type> オブジェクトを返します。

[!code-csharp-interactive[GetType example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#2)]

インスタンスが Null 許容型であるかどうかの判断には、[is](../../language-reference/keywords/is.md) 演算子は使用しないでください。 次の例のとおり、`is` 演算子の使用では、Null 許容型のインスタンスの型とその基になる型は判別できません。

[!code-csharp-interactive[is operator example](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#3)]

次の例のコードを使用すると、インスタンスが Null 許容型であるかどうかを判別することができます。

[!code-csharp-interactive[whether an instance is of a nullable type](../../../../samples/snippets/csharp/programming-guide/nullable-types/IdentifyNullableType.cs#4)]
  
## <a name="see-also"></a>関連項目

- [Null 許容型](index.md)
- [Null 許容型の使用](using-nullable-types.md)
- <xref:System.Nullable.GetUnderlyingType%2A>
