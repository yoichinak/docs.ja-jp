---
title: 匿名型と組型の選択
description: 匿名型とタプル型のどちらかを選択するのが適切な場合について説明します。
ms.date: 06/29/2020
ms.technology: dotnet-standard
ms.openlocfilehash: bc17695830a42a6eed9d60c0e097ee9d02a7957e
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803769"
---
# <a name="choosing-between-anonymous-and-tuple-types"></a>匿名型と組型の選択

適切な種類を選択するには、他の種類と比較して使いやすさ、パフォーマンス、およびトレードオフを考慮する必要があります。 匿名型は、C# 3.0 以降で使用できますが、ジェネリック <xref:System.Tuple%602?displayProperty=nameWithType> 型は .NET Framework 4.0 で導入されました。 その後、言語レベルのサポートで新しいオプションが導入されました。たとえば、名前が示すように、 <xref:System.ValueTuple%602?displayProperty=nameWithType> 匿名型の柔軟性を持つ値型を提供します。 この記事では、もう一方の型を選択するのが適切な場合について説明します。

## <a name="usability-and-functionality"></a>使いやすさと機能

匿名型は、C# 3.0 で統合言語クエリ (LINQ) 式を使用して導入されました。 LINQ では、開発者は多くの場合、クエリの結果を、使用しているオブジェクトからいくつかの select プロパティを保持する匿名型に射影します。 次の例では、オブジェクトの配列をインスタンス化 <xref:System.DateTime> し、2つのプロパティを持つ匿名型に射影されたオブジェクトを反復処理しています。

```csharp-interactive
var dates = new[]
{
    DateTime.UtcNow.AddHours(-1),
    DateTime.UtcNow,
    DateTime.UtcNow.AddHours(1),
};

foreach (var anonymous in
             dates.Select(
                 date => new { Formatted = $"{date:MMM dd, yyyy hh:mm zzz}", date.Ticks }))
{
    Console.WriteLine($"Ticks: {anonymous.Ticks}, formatted: {anonymous.Formatted}");
}
```

匿名型は演算子を使用してインスタンス化され、 [`new`](../../csharp/language-reference/operators/new-operator.md) プロパティの名前と型は宣言から推論されます。 同じアセンブリ内の複数の匿名オブジェクト初期化子が、同じ順序で同じ名前と型を持つプロパティのシーケンスを指定した場合、コンパイラはそれらのオブジェクトを同じ型のインスタンスとして扱います。 これらのオブジェクトは、コンパイラで生成された同一の型情報を共有します。

前の C# スニペットでは、次のコンパイラで生成された C# クラスと同様に、2つのプロパティを持つ匿名型を射影しています。

```csharp
internal sealed class f__AnonymousType0
{
    public string Formatted { get; }
    public long Ticks { get; }

    public f__AnonymousType0(string formatted, long ticks)
    {
        Formatted = formatted;
        Ticks = ticks;
    }
}
```

詳細については、「[匿名型](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)」を参照してください。 LINQ クエリへの射影では、組と同じ機能が存在します。組にプロパティを選択できます。 これらの組は、匿名型の場合と同様に、クエリを通過します。 ここで、を使用して、次の例を考えてみ `System.Tuple<string, long>` ます。

```csharp-interactive
var dates = new[]
{
    DateTime.UtcNow.AddHours(-1),
    DateTime.UtcNow,
    DateTime.UtcNow.AddHours(1),
};

foreach (var tuple in
            dates.Select(
                date => new Tuple<string, long>($"{date:MMM dd, yyyy hh:mm zzz}", date.Ticks)))
{
    Console.WriteLine($"Ticks: {tuple.Item2}, formatted: {tuple.Item1}");
}
```

を使用すると、 <xref:System.Tuple%602?displayProperty=nameWithType> インスタンスは、、などの番号付きの項目プロパティを公開し `Item1` `Item2` ます。 プロパティ名は序数のみを提供するため、これらのプロパティ名を使用すると、プロパティ値の意図を理解するのが難しくなります。 さらに、 `System.Tuple` 型は参照 `class` 型です。 <xref:System.ValueTuple%602?displayProperty=nameWithType>ただし、は値 `struct` 型です。 次の C# スニペットでは、を使用してを `ValueTuple<string, long>` に射影しています。 この場合、リテラル構文を使用してが割り当てられます。

```csharp-interactive
var dates = new[]
{
    DateTime.UtcNow.AddHours(-1),
    DateTime.UtcNow,
    DateTime.UtcNow.AddHours(1),
};

foreach (var (formatted, ticks) in
            dates.Select(
                date => (Formatted: $"{date:MMM dd, yyyy at hh:mm zzz}", date.Ticks)))
{
    Console.WriteLine($"Ticks: {ticks}, formatted: {formatted}");
}
```

C# では、型を持つタプルの言語サポートと、次のセマンティクスが用意されてい <xref:System.ValueTuple> ます。

- [組の代入](../../csharp/tuples.md#assignment-and-tuples)
- [タプル分解](../../csharp/deconstruct.md)(タプルに限定されません)
- [タプルの等価性のチェック](../../csharp/tuples.md#equality-and-tuples)
- [タプル プロジェクション初期化子](../../csharp/tuples.md#tuple-projection-initializers)

ただし、上記の例はすべて機能的に同等です。使いやすさとその基盤となる実装にはわずかな違いがあります。

## <a name="tradeoffs"></a>トレードオフ

常に over、匿名型を使用することもでき <xref:System.ValueTuple> <xref:System.Tuple> ますが、考慮すべきトレードオフがあります。 型は変更 <xref:System.ValueTuple> <xref:System.Tuple> 可能ですが、は読み取り専用です。 式ツリーでは匿名型を使用できますが、タプルは使用できません。 次の表に、主な相違点の概要を示します。

### <a name="key-differences"></a>主要な相違点

| 名前                     | アクセス修飾子 | Type     | カスタムプロパティ名 | 分解のサポート | 式ツリーのサポート |
|--------------------------|-----------------|----------|----------------------|------------------------|-------------------------|
| 匿名型          | `internal`      | `class`  | ✔️                   | ❌                     | ✔️                     |
| <xref:System.Tuple>      | `public`        | `class`  | ❌                   | ❌                     | ✔️                     |
| <xref:System.ValueTuple> | `public`        | `struct` | ✔️                   | ✔️                     | ❌                     |

### <a name="serialization"></a>シリアル化

型を選択する際の重要な考慮事項の1つは、シリアル化する必要があるかどうかです。 シリアル化とは、オブジェクトの状態を永続化または転送できる形式に変換するプロセスのことです。 詳細については、「[シリアル化](../../csharp/programming-guide/concepts/serialization/index.md)」を参照してください。 シリアル化が重要な場合は、 `class` 匿名型または組型よりもまたはを作成することを `struct` お勧めします。

## <a name="performance"></a>パフォーマンス

これらの種類の間のパフォーマンスは、シナリオによって異なります。 主な影響は、割り当てとコピーの間のトレードオフです。 ほとんどの場合、影響は小さくなります。 大きな影響が生じる可能性がある場合は、決定を通知するために測定値を取得する必要があります。

## <a name="conclusion"></a>まとめ

組と匿名型のどちらかを選択する開発者として、考慮すべきいくつかの要素があります。 一般に、[式ツリー](../../csharp/expression-trees.md)を使用していないときに、タプル構文に慣れている場合は、 <xref:System.ValueTuple> プロパティに柔軟に値型を指定することをお勧めします。 式ツリーを使用していて、プロパティに名前を付けたい場合は、[匿名型] を選択します。 それ以外の場合は、 <xref:System.Tuple>を指定します。

## <a name="see-also"></a>関連項目

- [匿名型](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [式ツリー](../../csharp/expression-trees.md)
- [フレームワーク デザインのガイドライン](index.md)
- [タプル型](../../csharp/tuples.md)
- [型のデザインのガイドライン](type.md)
