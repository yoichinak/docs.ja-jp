---
title: メンバー アクセス演算子 - C# リファレンス
description: 型のメンバーにアクセスするために使用できる C# 演算子について説明します。
ms.date: 05/09/2019
author: pkulikov
f1_keywords:
- ._CSharpKeyword
- '[]_CSharpKeyword'
- ()_CSharpKeyword
helpviewer_keywords:
- member access operators [C#]
- member access operator [C#]
- dot operator [C#]
- . operator [C#]
- subscript operator [C#]
- square brackets [] operator [C#]
- indexer operator [C#]
- '[] operator [C#]'
- null-conditional operators [C#]
- Elvis operator [C#]
- ?. operator [C#]
- ?[] operator [C#]
- invocation operator [C#]
- method call [C#]
- method invocation [C#]
- delegate invocation [C#]
- () operator [C#]
ms.openlocfilehash: de0715a2ac946fa47f0d83ac8569595e622f0b97
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758085"
---
# <a name="member-access-operators-c-reference"></a>メンバー アクセス演算子 (C# リファレンス)

型のメンバーにアクセスするときは、次の演算子を使用できます。

- [`.` (メンバー アクセス) ](#member-access-operator-): 名前空間または型のメンバーにアクセスします
- [`[]` (配列要素またはインデクサー アクセス) ](#indexer-operator-): 配列要素または型のインデクサーにアクセスします
- [`?.` および `?[]` (null 条件演算子)](#null-conditional-operators--and-): オペランドが null でない場合にのみ、メンバーまたは要素へのアクセス操作を実行します
- [`()` (呼び出し)](#invocation-operator-): アクセスしたメソッドを呼び出すか、デリゲートを呼び出します

## <a name="member-access-operator-"></a>メンバー アクセス演算子 .

以下の例に示すように、名前空間のメンバーまたは型にアクセスするために `.` トークンを使います。

- 次の [`using` ディレクティブ](../keywords/using-directive.md)の例に示すように、`.` を使って、名前空間内の入れ子になった名前空間にアクセスします。

  [!code-csharp[nested namespaces](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NestedNamespace)]

- 次のコードに示すように、`.` を使って "*修飾名*" を作成して名前空間内の型にアクセスします。

  [!code-csharp[qualified name](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#QualifiedName)]

  [`using` ディレクティブ](../keywords/using-directive.md)を使い、必要に応じて修飾名を利用します。

- 次のコードに示すように、`.` を使って、[型のメンバー](../../programming-guide/classes-and-structs/index.md#members) (静的および非静的) にアクセスします。

  [!code-csharp-interactive[type members](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#TypeMemberAccess)]

また、`.` を使って[拡張メソッド](../../programming-guide/classes-and-structs/extension-methods.md)にアクセスすることもできます。

## <a name="indexer-operator-"></a>インデクサー演算子 []

通常、角かっこ `[]` は、配列、インデクサー、またはポインター要素へのアクセスに使用されます。

### <a name="array-access"></a>配列へのアクセス

次の例は、配列要素へのアクセス方法を示しています。

[!code-csharp-interactive[array access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Arrays)]

配列インデックスが配列の対応するディメンションの範囲に含まれない場合、<xref:System.IndexOutOfRangeException> がスローされます。

前述の例が示すように、配列型の宣言と配列インスタンスのインスタンス化にも角かっこを使用します。

配列の詳細については、「[配列](../../programming-guide/arrays/index.md)」を参照してください。

### <a name="indexer-access"></a>インデクサーへのアクセス

次の例では、インデクサーへのアクセスを示すために .NET <xref:System.Collections.Generic.Dictionary%602> 型を使用します。

[!code-csharp-interactive[indexer access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Indexers)]

インデクサーを使用すると、配列のインデックス作成と同様の方法でユーザー定義型のインスタンスのインデックスを作成することができます。 整数である必要がある配列インデックスとは異なり、任意の型を持つインデクサー引数を宣言できます。

インデクサーの詳細については、「[インデクサー](../../programming-guide/indexers/index.md)」を参照してください。

### <a name="other-usages-of-"></a>[] の他の使用方法

ポインター要素へのアクセスの詳細については、[ポインターに関連する演算子](pointer-related-operators.md)に関する記事の「[ポインター要素アクセス演算子 []](pointer-related-operators.md#pointer-element-access-operator-)」セクションを参照してください。

角かっこは、[属性](../../programming-guide/concepts/attributes/index.md)を指定するためにも使用されます。

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a>Null 条件演算子 ?. および ?[]

C# 6 以降で使用できる Null 条件付き演算子は、そのオペランドが null 以外と評価された場合にのみ、オペランドにメンバー アクセス操作 (`?.`) または要素アクセス操作 (`?[]`) を適用します。 オペランドが `null` と評価された場合、演算子を適用した結果は `null` です。 Null 条件メンバー アクセス演算子 `?.` は Elvis 演算子とも呼ばれます。

Null 条件演算子はショートサーキットです。 つまり、条件付きのメンバーまたは要素アクセス操作のチェーン内にある 1 つの操作から `null` が返された場合、残りのチェーンは実行されません。 次の例では、`A` が `null` と評価されると `B` は評価されず、`A` または `B` が `null` と評価されると `C` は評価されません。

```csharp
A?.B?.Do(C);
A?.B?[C];
```

`?.` および `?[]` 演算子の使用例を次に示します。

[!code-csharp-interactive[null-conditional operators](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NullConditional)]

前述の例では、[NULL 合体演算子](null-coalescing-operator.md)の使用方法も示しています。 NULL 合体演算子は、NULL 条件演算の結果が `null` の場合に評価する代替の式を指定するために使用することができます。

### <a name="thread-safe-delegate-invocation"></a>スレッドセーフなデリゲートの呼び出し

次のコードに示すように、`?.` 演算子を使用してデリゲートが null 以外かどうかを確認し、それをスレッドセーフな方法で呼び出します (たとえば、[イベントを発生させる](../../../standard/events/how-to-raise-and-consume-events.md)場合)。

```csharp
PropertyChanged?.Invoke(…)
```

このコードは、C# 5 以前で使用する次のコードと同等です。

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

## <a name="invocation-operator-"></a>呼び出し演算子 ()

かっこ `()` は、[メソッド](../../programming-guide/classes-and-structs/methods.md)を呼び出すとき、または[デリゲート](../../programming-guide/delegates/index.md)を呼び出すときに使用します。

メソッドを呼び出す方法 (引数を指定した場合と指定しない場合) とデリゲートを呼び出す方法の例を次に示します。

[!code-csharp-interactive[invocation with ()](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Invocation)]

かっこは、[`new`](../keywords/new-operator.md) 演算子を使用して[コンストラクター](../../programming-guide/classes-and-structs/constructors.md)を呼び出すときにも使用します。

### <a name="other-usages-of-"></a>() の他の使用方法

式に含まれる演算を評価する順序を指定する場合にもかっこを使用します。 詳細については、「[演算子](../../programming-guide/statements-expressions-operators/operators.md)」記事の「[かっこの追加](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses)」セクションを参照してください。 優先順位順に並べられた演算子の一覧については、「[C# 演算子](index.md)」を参照してください。

変換演算子を呼び出す[キャスト式](invocation-operator.md#cast-expression)もかっこを使用します。

## <a name="operator-overloadability"></a>演算子のオーバーロード可/不可

`.` および `()` 演算子はオーバーロードできません。 `[]` 演算子も、オーバーロードできない演算子と見なされます。 ユーザー定義型を使用したインデックス作成をサポートするには、[インデクサー](../../programming-guide/indexers/index.md)を使用してください。

## <a name="c-language-specification"></a>C# 言語仕様

詳細については、「[C# 言語仕様](~/_csharplang/spec/introduction.md)」の次のセクションを参照してください。

- [メンバー アクセス](~/_csharplang/spec/expressions.md#member-access)
- [要素アクセス](~/_csharplang/spec/expressions.md#element-access)
- [NULL 条件演算子](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [呼び出し式](~/_csharplang/spec/expressions.md#invocation-expressions)

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミングガイド](../../programming-guide/index.md)
- [C# 演算子](index.md)
- [?? (Null 合体演算子)](null-coalescing-operator.md)
