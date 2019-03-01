---
title: C# 8.0 の新機能 - C# ガイド
description: C# 8.0 で使用できる新しい機能の概要を説明します。 この記事は、プレビュー 2 での最新のものです。
ms.date: 02/12/2019
ms.openlocfilehash: 874420775215502ebdacb8420b3fe0e027d6660f
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/23/2019
ms.locfileid: "56747623"
---
# <a name="whats-new-in-c-80"></a>C# 8.0 の新機能

C# 言語では、プレビュー 2 で既に試すことができる多くの機能強化が行われています。 プレビュー 2 で追加された新機能は次のとおりです。

- [パターン マッチングの拡張機能](#more-patterns-in-more-places):
  * [switch 式](#switch-expressions)
  * [プロパティのパターン](#property-patterns)
  * [タプル パターン](#tuple-patterns)
  * [位置指定パターン](#positional-patterns)
- [using 宣言](#using-declarations)
- [静的ローカル関数](#static-local-functions)
- [破棄可能な ref 構造体](#disposable-ref-structs)

以下の言語機能は、C# 8.0 プレビュー 1 で初めて導入されたものです。

- [Null 許容参照型](#nullable-reference-types)
- [非同期ストリーム](#asynchronous-streams)
- [インデックスと範囲](#indices-and-ranges)

> [!NOTE]
> この記事の最後の更新は、C# 8.0 プレビュー 2 に関するものです。

この記事の以降では、これらの機能について簡単に説明します。 詳細な記事がある場合は、それらのチュートリアルと概要へのリンクが提供されています。

## <a name="more-patterns-in-more-places"></a>より多くの場所でより多くのパターン

**パターン マッチング**では、関連はあっても種類が異なるデータをまたがってシェイプに依存する機能を提供するツールが用意されています。 C# 7.0 では、[`is`](../language-reference/keywords/is.md) 式と [`switch`](../language-reference/keywords/switch.md) ステートメントを使用することで、型パターンと定数パターンの構文が導入されました。 これらの機能では、データと機能が分かれて存在するプログラミング パラダイムのサポートに向けた最初の試験的なステップが示されました。 業界はマイクロサービスと他のクラウド ベース アーキテクチャに向けて移動しており、他の言語ツールが必要になっています。

C# 8.0 では、このボキャブラリが展開されて、コードのより多くの場所で、より多くのパターン式を使用できます。 データと機能が分かれているときは、これらの機能を検討してください。 アルゴリズムがオブジェクトのランタイム型以外の事実に依存している場合は、パターン マッチングを検討してください。 これらの手法では、設計を表現する別の方法が提供されます。

新しい場所での新しいパターンだけでなく、C# 8.0 では**再帰パターン**が追加されています。 パターン式の結果は式です。 再帰パターンは、単に、別のパターン式の出力に適用されるパターン式です。

### <a name="switch-expressions"></a>switch 式

多くの場合、[`switch`](../language-reference/keywords/switch.md) ステートメントでは、その各 `case` ブロックで値が生成されます。 **switch 式**を使用すると、より簡潔な式の構文を使用できます。 反復的な `case` や `break` キーワード、および中かっこの数が少なくなります。  たとえば、虹の色を示す次のような列挙型について考えます。

```csharp
public enum Rainbow
{
    Red,
    Orange,
    Yellow,
    Blue,
    Indigo,
    Violet
}
```

switch 式を含む次のメソッドを使用して、`Rainbow` の値をその RGB 値に変換できます。

```csharp
public static RGBColor FromRainbow(Rainbow colorBand) =>
    colorBand switch
    {
        Rainbow.Red    => new RGBColor(0xFF, 0x00, 0x00),
        Rainbow.Orange => new RGBColor(0xFF, 0x7F, 0x00),
        Rainbow.Yellow => new RGBColor(0xFF, 0xFF, 0x00),
        Rainbow.Blue   => new RGBColor(0x00, 0x00, 0xFF),
        Rainbow.Indigo => new RGBColor(0x4B, 0x00, 0x82),
        Rainbow.Violet => new RGBColor(0x94, 0x00, 0xD3),
        _              => throw new ArgumentException(message: "invalid enum value", paramName: nameof(colorBand)),
    };
```

この構文ではいくつかの点が改良されています。

- 変数は `switch` キーワードの前にあります。 順序を変えることで、switch ステートメントからの switch 式の視覚的な区別が容易になります。
- `case` 要素と `:` 要素は、`=>` に置き換えられます。 より簡潔でわかりやすくなります。
- `default` ケースは、`_` 破棄に置き換えられます。
- 本体は式であり、ステートメントではありません。

従来の `switch` ステートメントを使用した同等のコードと比較してください。

```csharp
public static RGBColor fromRainbowClassic(Rainbow colorBand)
{
    switch (colorBand)
    {
        case Rainbow.Red:
            return new RGBColor(0xFF, 0x00, 0x00);
        case Rainbow.Orange:
            return new RGBColor(0xFF, 0x7F, 0x00);
        case Rainbow.Yellow:
            return new RGBColor(0xFF, 0xFF, 0x00);
        case Rainbow.Blue:
            return new RGBColor(0x00, 0x00, 0xFF);
        case Rainbow.Indigo:
            return new RGBColor(0x4B, 0x00, 0x82);
        case Rainbow.Violet:
            return new RGBColor(0x94, 0x00, 0xD3);
        default:
            throw new ArgumentException(message: "invalid enum value", paramName: nameof(colorBand));
    };
}
```

### <a name="property-patterns"></a>プロパティ パターン

**プロパティ パターン**を使用すると、調査対象のオブジェクトのプロパティと照合することができます。 購入者の住所に基づいて消費税を計算する必要がある eコマース サイトについて考えます。 そのような計算は、`Address` クラスの核心的な役割ではありません。 時間とともに、おそらくは住所の形式の変更より頻繁に、変更されます。 消費税の金額は、住所の `State` プロパティに依存します。 次のメソッドでは、プロパティ パターンを使用して、住所と価格から消費税を計算しています。

```csharp
public static decimal ComputeSalesTax(Address location, decimal salePrice) =>
    location switch
    {
        { State: "WA" } => salePrice * 0.06M,
        { State: "MN" } => salePrice * 0.75M,
        { State: "MI" } => salePrice * 0.05M,
        // other cases removed for brevity...
        _ => 0M
    };
    ```

Pattern matching creates a concise syntax for expressing this algorithm.

### Tuple patterns

Some algorithms depend on multiple inputs. **Tuple patterns** allow you to switch based on multiple values expressed as a [tuple](../tuples.md).  The following code shows a switch expression for the game *rock, paper, scissors*:

```csharp
public static string RockPaperScissors(string first, string second)
    => (first, second) switch
    {
        ("rock", "paper") => "rock is covered by paper. Paper wins.",
        ("rock", "scissors") => "rock breaks scissors. Rock wins.",
        ("paper", "rock") => "paper covers rock. Paper wins.",
        ("paper", "scissors") => "paper is cut by scissors. Scissors wins.",
        ("scissors", "rock") => "scissors is broken by rock. Rock wins.",
        ("scissors", "paper") => "scissors cuts paper. Scissors wins.",
        (_, _) => "tie"
    };
    ```

The messages indicate the winner. The discard case represents the three combinations for ties, or other text inputs.

### Positional patterns

Some types include a `Deconstruct` method that deconstructs its properties into discrete variables. When a `Deconstruct` method is accessible, you can use **positional patterns** to inspect properties of the object and use those properties for a pattern.  Consider the following `Point` class that includes a `Deconstruct` method to create discrete variables for `X` and `Y`:

```csharp
public class Point
{
    public int X { get; }
    public int Y { get; }

    public Point(int x, int y) => (X, Y) = (x, y);

    public void Deconstruct(out int x, out int y) =>
        (x, y) = (X, Y);
}
```

次のメソッドでは、**位置指定パターン**を使用して、`x` と `y` の値を抽出しています。 その後、`when` 句を使用して、点のクワドラントを決定します。

```csharp
static string Quadrant(Point p) => p switch
{
    (0, 0) => "origin",
    (var x, var y) when x > 0 && y > 0 => "Quadrant 1",
    (var x, var y) when x < 0 && y > 0 => "Quadrant 2",
    (var x, var y) when x < 0 && y < 0 => "Quadrant 3",
    (var x, var y) when x > 0 && y < 0 => "Quadrant 4",
    (var x, var y) => "on a border",
    _ => "unknown"
};
```

前の switch での破棄パターンは、`x` または `y` のどちらか一方が 0 のときに一致しますが、両方とも 0 のときには一致しません。 switch 式は、値を生成するか、または例外をスローする必要があります。 どのケースとも一致しない場合、switch 式は例外をスローします。 可能性のあるすべてのケースが switch 式でカバーされていない場合、コンパイラで警告が生成されます。

## <a name="using-declarations"></a>using 宣言

**using 宣言**は、`using` キーワードが前に付いている変数宣言です。 宣言されている変数を外側のスコープの最後に破棄する必要があることを、コンパイラに伝えます。 たとえば、テキスト ファイルを書き込む次のようなコードについて考えます。

```csharp
static void WriteLinesToFile(IEnumerable<string> lines)
{
    using var file = new System.IO.StreamWriter("WriteLines2.txt");
    foreach (string line in lines)
    {
        // If the line doesn't contain the word 'Second', write the line to the file.
        if (!line.Contains("Second"))
        {
            file.WriteLine(line);
        }
    }
// file is disposed here
}
```

上の例では、メソッドの右中かっこに達した時点で、ファイルは破棄されます。 そこは、`file` が宣言されているスコープの末端です。 上記のコードは、従来の [using ステートメント](../language-reference/keywords/using-statement.md)を使用する次のコードと同等です。


```csharp
static void WriteLinesToFile(IEnumerable<string> lines)
{
    using (var file = new System.IO.StreamWriter("WriteLines2.txt"))
    {
        foreach (string line in lines)
        {
            // If the line doesn't contain the word 'Second', write the line to the file.
            if (!line.Contains("Second"))
            {
                file.WriteLine(line);
            }
        }
    } // file is disposed here
}
```

上の例では、`using` ステートメントに関連付けられている右中かっこに達すると、ファイルは破棄されます。

どちらの場合も、コンパイラでは `Dispose()` の呼び出しが生成されます。 using ステートメント内の式を破棄できない場合、コンパイラでエラーが生成されます。

## <a name="static-local-functions"></a>静的ローカル関数

`static` 修飾子をローカル関数に追加することにより、ローカル関数で外側のスコープの変数がキャプチャ (参照) されないようにすることができます。 それを行うと、`CS8421` "静的ローカル関数は <variable> への参照を含むことができない" が生成されます。 

次のコードについて考えてみましょう。 ローカル関数 `LocalFunction` は、外側のスコープ (`M` メソッド) で宣言されている変数 `y` にアクセスしています。 そのため、`LocalFunction` では `static` 修飾子を宣言することはできません。

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

次のコードには、静的ローカル関数が含まれています。 外側のスコープ内のどの変数にもアクセスしていないため、静的にすることができます。

```csharp
int M()
{
    int y = 5;
    int x = 7;
    return Add(x, y);

    static int Add(int left, int right) => left + right;
}
```

## <a name="disposable-ref-structs"></a>破棄可能な ref 構造体

`ref` 修飾子付きで宣言されている `struct` ではインターフェイスを実装できないので、<xref:System.IDisposable> を実装できません。 したがって、`ref struct` を破棄できるようにするには、アクセス可能な `void Dispose()` メソッドを持っている必要があります。 これは、`readonly ref struct` 宣言にも当てはまります。

## <a name="nullable-reference-types"></a>null 許容参照型

null 許容注釈コンテキスト内では、参照型のすべての変数は、**null 非許容参照型**と見なされます。 変数が null 許容であることを示したい場合は、型名に `?` を追加し、**null 許容参照型**として変数を宣言する必要があります。

null 非許容参照型の場合は、コンパイラでフロー分析を使用して、ローカル変数が宣言時に null 以外の値に初期化されることが確認されます。 フィールドは、構築時に初期化される必要があります。 変数が使用可能ないずれかのコンストラクターの呼び出しまたは初期化子によって設定されていない場合、コンパイラで警告が生成されます。 さらに、null 非許容参照型に、null になる可能性がある値を割り当てることはできません。

null 許容参照型の場合は、null に割り当てられたり初期化されたりしないことは確認されません。 ただし、null 許容参照型の変数が null 非許容参照型にアクセスしたり割り当てられたりするときは、その前に、コンパイラでフロー分析を使用して、null 値のチェックが行われます。

詳しくは、「[null 許容参照型](../nullable-references.md)」の概要をご覧ください。 この [null 許容参照型チュートリアル](../tutorials/nullable-reference-types.md)の新しいアプリケーションを使って、自分で試してみてください。 既存のコードベースを null 許容参照型を使用するように移行する手順について詳しくは、[null 許容参照型を使用するようにアプリケーションを移行する方法についてのチュートリアル](../tutorials/upgrade-to-nullable-references.md)に関する記事をご覧ください。

## <a name="asynchronous-streams"></a>非同期ストリーム

C# 8.0 以降では、ストリームを非同期的に作成して使用することができます。 非同期ストリームを返すメソッドには、次の 3 つの特徴があります。

1. `async` 修飾子を使用して宣言されています。
1. <xref:System.Collections.Generic.IAsyncEnumerable%601> を返します。
1. メソッドに、連続する要素を非同期ストリームで返すための `yield return` ステートメントが含まれています。

非同期ストリームを使用するには、ストリームの要素を列挙するときに、`foreach` キーワードの前に `await` キーワードを追加する必要があります。 `await` キーワードを追加するには、非同期ストリームを列挙するメソッドが、`async` 修飾子を使用して宣言されていて、`async` メソッドに対して許可される型を返すようになっている必要があります。 通常は、<xref:System.Threading.Tasks.Task> または <xref:System.Threading.Tasks.Task%601> を返すことを意味します。 <xref:System.Threading.Tasks.ValueTask> または <xref:System.Threading.Tasks.ValueTask%601> にすることもできます。 同じメソッドで非同期ストリームの使用と生成の両方を行うことができます。これは、そのメソッドが <xref:System.Collections.Generic.IAsyncEnumerable%601> を返すことを意味します。 次のコードでは、1 から 20 の値のシーケンスが生成され、各値の間に 100 ミリ秒の待機が設けられています。

```csharp
public static async System.Collections.Generic.IAsyncEnumerable<int> GenerateSequence()
{
    for (int i = 0; i < 20; i++)
    {
        await Task.Delay(100);
        yield return i;
    }
}
```

シーケンスの列挙は、`await foreach` ステートメントを使用して行います。

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

[非同期ストリームの作成と使用](../tutorials/generate-consume-asynchronous-stream.md)に関するチュートリアルを使用して、自分で非同期ストリームを試すことができます。

## <a name="indices-and-ranges"></a>インデックスと範囲

範囲とインデックスでは、配列、<xref:System.Span%601>、または <xref:System.ReadOnlySpan%601> 内の部分範囲を指定するための簡潔な構文が提供されます。

**末尾から**インデックスを指定することができます。 **末尾から**指定するには、`^` 演算子を使用します。 `array[2]` が "先頭から 2 番目" の要素を意味することには慣れているでしょう。 今後、`array[^2]` は "末尾から 2 番目" の要素を意味するようになります。 インデックス `^0` は、"末尾" つまり最後の要素の後のインデックスを意味します。

**範囲**は、**範囲演算子** `..` を使用して指定できます。 たとえば、`0..^0` は配列の範囲全体を指定します。0 は先頭からですが、末尾の 0 は含まれません。 どちらのオペランドでも、"先頭から" または "末尾から" を使用できます。 さらに、どちらのオペランドも省略できます。 先頭インデックスの既定値は `0`、末尾インデックスの既定値は `^0` です。

いくつか例を見てみましょう。 先頭および末尾からのインデックスの注釈が付けられた、次のような配列について考えます。

```csharp
var words = new string[]
{
                // index from start    index from end
    "The",      // 0                   ^9
    "quick",    // 1                   ^8
    "brown",    // 2                   ^7
    "fox",      // 3                   ^6
    "jumped",   // 4                   ^5
    "over",     // 5                   ^4
    "the",      // 6                   ^3
    "lazy",     // 7                   ^2
    "dog"       // 8                   ^1
};
```

各要素のインデックスによって "先頭から" と "末尾から" の概念が強調されており、その範囲では範囲の末尾が除外されています。 配列全体の "先頭" は最初の要素です。 配列全体の "末尾" は、最後の要素の "*後*" です。

最後の単語は、`^1` というインデックスで取得することができます。

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

次のコードでは、単語 "quick"、"brown"、"fox" から成る部分範囲が作成されます。 それには、`words[1]` から `words[3]` までが含まれます。 要素 `words[4]` は範囲内ではありません。

```csharp
var brownFox = words[1..4];
```

次のコードでは、"lazy" と "dog" の部分範囲が作成されます。 それには、`words[^2]` と `words[^1]` が含まれます。 末尾インデックス `words[^0]` は含まれません。

```csharp
var lazyDog = words[^2..^0];
```

次の例では、先頭と末尾の一方または両方が開いている範囲が作成されます。

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the, "lazy" and "dog"
```

変数として範囲を宣言することもできます。

```csharp
Range phrase = 1..4;
```

その場合、範囲は文字 `[` と `]` の内側で使用できます。

```csharp
var text = words[phrase];
```
