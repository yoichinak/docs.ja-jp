---
title: where (ジェネリック型制約) - C# リファレンス
ms.custom: seodec18
ms.date: 04/12/2018
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.openlocfilehash: 3982c97bc56b42237700343b2572d1bba930bbbd
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422778"
---
# <a name="where-generic-type-constraint-c-reference"></a>where (ジェネリック型制約) (C# リファレンス)

ジェネリック定義の `where` 句では、型の制約を指定します。この型は、ジェネリック型、メソッド、デリゲート、またはローカル関数における型パラメーターの引数として使用されます。 制約では、インターフェイス (基底クラス) を指定したり、参照、値、またはアンマネージド型となるジェネリック型を要求したりすることができます。 それらにより型引数が処理する必要がある機能が宣言されえます。

たとえば、型パラメーター `T` が <xref:System.IComparable%601> インターフェイスを実装するように、次のように `MyGenericClass` ジェネリック クラスを宣言できます。

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#1)]

> [!NOTE]
> クエリ式での where 句の詳細については、「[where 句](where-clause.md)」を参照してください。

`where` 句には基底クラスの制約を含めることもできます。 基底クラスの制約は、ジェネリック型の型引数として使用する型には、ジェネリック型の型引数として使用される基底クラスとして指定されているクラス (または基底クラス自体) が含まれている必要があることを指定します。 基底クラスの制約を使用する場合は、型パラメーターに関する制約よりも前に制約を記述する必要があります。 一部の型は、基底クラスの制約として許可されません (<xref:System.Object>、<xref:System.Array>、<xref:System.ValueType>)。 C# 7.3 より前は、<xref:System.Enum>、<xref:System.Delegate>、<xref:System.MulticastDelegate> も基底クラスの制約として許可されていません。 次の例では、この型は基底クラスとして指定できるようになったことを示しています。

[!code-csharp[using an interface constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#2)]

`where` 句では、型が `class` または `struct` であることを指定できます。 `struct` 制約では、`System.ValueType` の基底クラスの制約を指定する必要はありません。 `System.ValueType` 型は基底クラスの制約として使用できません。 `class` 制約と `struct` 制約の両方の例を次に示します。

[!code-csharp[using the class and struct constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#3)]

`where` 句には、`unmanaged` 制約を含めることもできます。 `unmanaged` 制約では、**アンマネージド型**と呼ばれる型に対して型パラメーターを制限します。 **アンマネージド型**は参照型ではない型であり、任意の入れ子のレベルに参照型フィールドを含みません。 `unmanaged` 制約を使用すると、C# でローレベルの相互運用コードを記述しやすくなります。 この制約では、すべてのアンマネージド型にわたって再利用可能なルーチンを可能にします。 `unmanaged` 制約は、`class` や `struct` 制約と組み合わせることはできません。 `unmanaged` 制約は `struct` にする必要がある型を適用します。

[!code-csharp[using the unmanaged constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#4)]

`where` 句には、コンストラクター制約 `new()` を含めることもできます。 その制約では、`new` 演算子を使用して型パラメーターのインスタンスを作成できるようにします。 [new() 制約](new-constraint.md)に基づいて、コンパイラは、指定されている型引数には、アクセス可能なパラメーターなしの (または既定の) コンストラクターが必要であることを認識します。 次に例を示します。

[!code-csharp[using the new constraint](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#5)]

`new()` 制約は `where` 句の最後に示されます。 `new()` 制約は、`struct` や `unmanaged` 制約と組み合わせることはできません。 それらの制約を満たすすべての型には、`new()` 制約を重複させて、アクセス可能なパラメーターなしのコンストラクターが含まれている必要があります。

複数の型パラメーターがある場合には、型パラメーターごとに `where` 句を 1 つずつ使用します。次に例を示します。

[!code-csharp[using multiple where constraints](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#6)]

次の例に示すように、ジェネリック メソッドの型パラメーターにも制約を適用できます。

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#7)]

デリゲートに対する型パラメーター制約を記述する構文は、メソッドの構文と同じである点に注意してください。

[!code-csharp[where constraints with generic methods](../../../../samples/snippets/csharp/keywords/GenericWhereConstraints.cs#8)]

汎用デリゲートについては、「[汎用デリゲート](../../../csharp/programming-guide/generics/generic-delegates.md)」を参照してください。

制約の構文と使用方法の詳細については、「[型パラメーターの制約](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)」を参照してください。

## <a name="c-language-specification"></a>C# 言語仕様

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>関連項目

- [C# リファレンス](../../../csharp/language-reference/index.md)
- [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)
- [ジェネリックの概要](../../../csharp/programming-guide/generics/index.md)
- [new 制約](../../../csharp/language-reference/keywords/new-constraint.md)
- [型パラメーターの制約](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)
