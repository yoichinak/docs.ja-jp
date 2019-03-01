---
title: C# 7.0 の新機能 - C# ガイド
description: C# 言語のバージョン 7.0 での新機能の概要を説明します。
ms.date: 12/21/2016
ms.assetid: fd41596d-d0c2-4816-b94d-c4d00a5d0243
ms.openlocfilehash: 0646eaa999579e5347007dd71defcc643c19c7f9
ms.sourcegitcommit: 2b986afe4ce9e13bbeec929c9737757eb61de60e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/22/2019
ms.locfileid: "56665083"
---
# <a name="whats-new-in-c-70"></a>C# 7.0 の新機能

C# 7.0 では、C# 言語に多くの新機能が追加されます。
* [`out` 変数](#out-variables)
    - `out` の値は、それが使用されるメソッドの引数としてインラインで宣言できます。
* [タプル](#tuples)
    - 複数のパブリック フィールドを含む、軽量で名前のない型を作成できます。 コンパイラおよび IDE ツールでは、このような型のセマンティクスが認識されます。
* [破棄](#discards)
    - 破棄は、割り当てられた値を考慮しない場合に割り当てで使用された、一時的な書き込み専用の値です。 タプルおよびユーザー定義の型を分解する場合や、メソッドを `out` パラメーターを使用して呼び出す場合に特に便利です。
* [パターン一致](#pattern-matching)
    - これらの型のメンバーの任意の型と値に基づいて、分岐ロジックを作成できます。
* [`ref` ローカル変数と戻り値](#ref-locals-and-returns)
    - メソッドのローカル変数と戻り値は、他のストレージへの参照になります。
* [ローカル関数](#local-functions)
    - 関数を他の関数の中に入れ子にして、関数のスコープと可視性を制限することができます。
* [式形式のメンバーの追加](#more-expression-bodied-members)
    - 式を使用して作成できるメンバーが増加しました。
* [`throw` 式](#throw-expressions)
    - `throw` がステートメントだったためにこれまで許可されなかったコード コンストラクトで例外をスローできるようになりました。 
* [一般化された async の戻り値の型](#generalized-async-return-types)
    - `async` 修飾子を使って宣言したメソッドは、`Task` と `Task<T>` に加えて他の型を返すことができます。
* [数値リテラルの構文の改善](#numeric-literal-syntax-improvements)
    - 新しいトークンにより、数値定数の読みやすさが向上します。

このトピックの残りの部分では、各機能について説明します。 機能ごとに、その背後にある論拠のほか、 構文についても説明します。 また、新機能の使用により、開発者としての生産性が向上するサンプル シナリオもいくつか紹介します。 

## <a name="out-variables"></a>`out` 変数

`out` パラメーターをサポートする既存の構文は、このバージョンで改良されました。  

以前は、out 変数の宣言とその初期化を 2 つの異なるステートメントに分離する必要がありました。

[!code-csharp[OutVariableOldStyle](../../../samples/snippets/csharp/new-in-7/program.cs#03_OutVariableOldStyle "classic out variable declaration")]

現在は、別の宣言ステートメントを記述するのではなく、メソッド呼び出しの引数リストで `out` 変数を宣言できるようになりました。

[!code-csharp[OutVariableDeclarations](../../../samples/snippets/csharp/new-in-7/program.cs#01_OutVariableDeclarations "Out variable declarations")]

上記のように、わかりやすくするために `out` 変数の型を指定することができます。 ただし、この言語では、次のように暗黙的に型指定されたローカル変数を使用できます。

[!code-csharp[OutVarVariableDeclarations](../../../samples/snippets/csharp/new-in-7/program.cs#02_OutVarVariableDeclarations "Implicitly typed Out variable")]

* コードが読みやすくなる。 
    - out 変数は、使用する場所で宣言します。その場所より上にある別の行で宣言しません。
* 初期値を割り当てる必要がない。
    - `out` 変数は、メソッド呼び出し内の使用場所で宣言することにより、割り当てる前に誤って使用することがなくなります。

この機能の最も一般的な用途は `Try` パターンになります。 このパターンでは、メソッドは、成功または失敗を示す `bool` と、メソッドが成功した場合に結果を提供する `out` 変数を返します。

`out` 変数の宣言を使用すると、宣言された変数は if ステートメントの外側のスコープに "リーク" されます。 これにより、その後はこの変数を使用することができます。

```csharp
if (!int.TryParse(input, out int result))
{    
    return null;
}

return result;
```

## <a name="tuples"></a>タプル

> [!NOTE]
> 新しいタプル機能を使用するには、<xref:System.ValueTuple> 型が必要です。
> 型が含まれていないプラットフォームで使用する場合は、NuGet パッケージ [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/) を追加する必要があります。
>
> これは、フレームワークで提供される型に依存するその他の言語機能に似ています。 たとえば、`INotifyCompletion` インターフェイスに依存する `async` や `await`、`IEnumerable<T>` に依存する LINQ などがあります。 ただし、.NET がプラットフォームにさらに依存しなくなりつつあるため、配信メカニズムもそれに応じて変わりつつあります。 .NET Framework が、言語コンパイラと同じ周期で配布されるとは限りません。 新しい言語機能が新しい型に依存する場合、それらの型は、言語機能の配布時に NuGet パッケージとして入手できます。 これらの新しい型は .NET 標準 API に追加され、フレームワークの一部として配信されるため、NuGet パッケージは必要なくなります。

C# には、設計の意図を説明するために使用される、クラスと構造体の豊富な構文が用意されています。 ところが、場合によっては、その豊富な構文を使用するために、余分な作業が必要になることがあります。この場合、メリットはごくわずかです。 複数のデータ要素を含む単純な構造を必要とするメソッドを記述することはよくあります。 このようなシナリオをサポートするために、C# には "*タプル*" が追加されました。 タプルとは、データ メンバーを表す複数のフィールドを含む軽量なデータ構造です。
フィールドは検証されず、独自のメソッドを定義することはできません。

> [!NOTE]
> タプルは C# 7.0 より前で使用できましたが、効率的でなく、言語サポートがありませんでした。
> これは、タプル要素が `Item1` や `Item2` などとしてのみ参照できることを意味しました。 C# 7.0 では、タプルの言語サポートが導入されたことで、新しい、より効率的なタプル型を使用するフィールドのセマンティック名が有効になります。

タプルを作成するには、各メンバーを値に割り当てます。

[!code-csharp[UnnamedTuple](../../../samples/snippets/csharp/new-in-7/program.cs#04_UnnamedTuple "Unnamed tuple")]

その割り当てによってメンバーが `Item1` と `Item2` のタプルが作成され、<xref:System.Tuple> と同じようにして使用できるようになります。構文を変更してタプルの各メンバーにセマンティック名を提供するタプルを作成することができます。

[!code-csharp[NamedTuple](../../../samples/snippets/csharp/new-in-7/program.cs#05_NamedTuple "Named tuple")]

`namedLetters` タプルには、`Alpha` と `Beta` と呼ばれるフィールドが含まれています。 これらの名前は、コンパイル時にのみ存在し、実行時にリフレクションを使用してタプルを検査するときなどには保持されません。

タプルの割り当てでは、代入の右辺でフィールドの名前を指定することもできます。

[!code-csharp[ImplicitNamedTuple](../../../samples/snippets/csharp/new-in-7/program.cs#06_ImplicitNamedTuple "Implicitly named tuple")]

代入の左辺と右辺の両方でフィールドの名前を指定することができます。

[!code-csharp[NamedTupleConflict](../../../samples/snippets/csharp/new-in-7/program.cs#07_NamedTupleConflict "Named tuple conflict")]

上記の行では、警告 `CS8123` が生成されます。これは、代入の右辺にある名前 (`Alpha` と `Beta`) が左辺にある名前 (`First` と `Second`) と競合するために無視されることを示しています。

上の例では、タプルを宣言する基本的な構文を示しています。 タプルは、`private` メソッドと `internal` メソッドの戻り値の型として最も有用です。 タプルは、これらのメソッドで複数の離散値を返すためのシンプルな構文です。返される型を定義する `class` または `struct` を作成する手間がかからない。 新しい型を作成する必要はありません。

タプルの作成は、より効率的かつ生産的です。
タプルは、複数の値を保持するデータ構造を定義するための、よりシンプルで軽量な構文です。 次の例のメソッドは、整数のシーケンス内で見つかった最小値と最大値を返します。

[!code-csharp[TupleReturningMethod](../../../samples/snippets/csharp/new-in-7/program.cs#08_TupleReturningMethod "Tuple returning method")]

このようにタプルを使用すると、いくつかの利点があります。

* 返される型を定義する `class` または `struct` を作成する手間がかからない。 
* 新しい型を作成する必要がない。
* 言語の拡張により、<xref:System.Tuple.Create``1(``0)> メソッドを呼び出す必要がなくなる。

メソッドの宣言では、返されるタプルのフィールドに名前を指定します。 このメソッドを呼び出した場合の戻り値は、`Max` と `Min` というフィールドを含むタプルです。

[!code-csharp[CallingTupleMethod](../../../samples/snippets/csharp/new-in-7/program.cs#09_CallingTupleMethod "Calling a tuple returning method")]

状況によっては、メソッドから返されたタプルのメンバーをばらすことが必要になる場合もあります。  そのためには、タプル内のそれぞれの値に対して別個の変数を宣言します。 この操作は、タプルの "*分解*" と呼ばれます。

[!code-csharp[CallingWithDeconstructor](../../../samples/snippets/csharp/new-in-7/program.cs#10_CallingWithDeconstructor "Deconstructing a tuple")]

.NET でも任意の型に同様の分解を指定することができます。 そのためには、`Deconstruct` メソッドをクラスのメンバーとして記述します。 その `Deconstruct` メソッドは、抽出する各プロパティ用に一連の `out` 引数を提供します。 次の `Point` クラスを考えてみましょう。このクラスは、`X` 座標と `Y` 座標を抽出するデコンストラクター メソッドを指定しています。

[!code-csharp[PointWithDeconstruction](../../../samples/snippets/csharp/new-in-7/point.cs#11_PointWithDeconstruction "Point with deconstruction method")]
 
`Point` をタプルに割り当てて、個々のフィールドを抽出できます。

[!code-csharp[DeconstructPoint](../../../samples/snippets/csharp/new-in-7/program.cs#12_DeconstructPoint "Deconstruct a point")]

`Deconstruct` メソッドで定義された名前に制約されません。 割り当ての一環として、抽出変数の名前を変更してもかまいません。  

[!code-csharp[DeconstructNames](../../../samples/snippets/csharp/new-in-7/program.cs#13_DeconstructNames "Deconstruct with new names")]

タプルの詳細については、[タプルのトピック](../tuples.md)を参照してください。

## <a name="discards"></a>破棄

`out` パラメーターを使用してタプルを分解したりメソッドを呼び出したりする場合に、使用する予定がなく、考慮にも入れない値の変数の定義を強制されることが多くあります。 C# ではこのシナリオを処理するために*破棄*のサポートを追加しています。 破棄は名前が `_` (アンダースコア (_) 文字) の書き込み専用の変数で、破棄するすべての値をこの 1 つの変数に割り当てることができます。 破棄は未割り当ての変数に似ています。代入ステートメントとは異なり、破棄はコードで使用できません。

次のシナリオでは破棄はサポートされません。

* タプルまたはユーザー定義の型を分解する場合。

* [out](../language-reference/keywords/out-parameter-modifier.md) パラメーターを使用してメソッドを呼び出す場合。

* [is](../language-reference/keywords/is.md) および [switch](../language-reference/keywords/switch.md) ステートメントによるパターン マッチング操作。

* 割り当ての値を破棄として明示的に識別する必要がある場合の、スタンドアロン識別子。

次の例は、ある都市の 2 つの異なる年度のデータを含む 6 つのタプルを戻す `QueryCityDataForYears` メソッドを定義しています。 この例のメソッド呼び出しでは、メソッドによって戻された 2 つの人口の値のみが考慮されているため、タプルの残りの値はタプルの分解時に破棄として扱われます。

[!code-csharp[Tuple-discard](../../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

詳細については、[破棄](../discards.md)に関するページを参照してください。

## <a name="pattern-matching"></a>パターン マッチング

"*パターン マッチング*" は、オブジェクトの型以外のプロパティでメソッドのディスパッチを実装できるようにする機能です。 オブジェクトの型に基づいたメソッドのディスパッチに慣れている方も多いはずです。 オブジェクト指向プログラミングでは、仮想メソッドとオーバーライド メソッドには、オブジェクトの型に基づくメソッドのディスパッチを実装するための言語構文が用意されています。 基底クラスと派生クラスは異なる実装を提供します。 パターン マッチング式により、この概念が拡張されたため、継承階層を介して関連していない型やデータ要素に同様のディスパッチ パターンを簡単に実装できるようになります。 

パターン マッチングでは、`is` 式と `switch` 式がサポートされています。 どちらの式でも、オブジェクトとそのプロパティを検査して、そのオブジェクトが必要なパターンを満たしているかどうかを判定できます。 パターンに追加の規則を指定するには、`when` キーワードを使用します。

### <a name="is-expression"></a>`is` 式

`is` パターン式を使用すると、使い慣れた [`is` 演算子](../language-reference/keywords/is.md#pattern-matching-with-is)を拡張して、その型を超えてオブジェクトを照会できます。

では、簡単なシナリオから始めましょう。 ここでは、関連付けられていない型を操作するアルゴリズムをパターン マッチング式で簡単にする方法を示すために、いくつかの機能をこのシナリオに追加します。 まず、サイコロの出目の合計を計算するメソッドを追加します。

[!code-csharp[SumDieRolls](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#14_SumDieRolls "Sum die rolls")]

複数のサイコロを使った場合はそれぞれの出目の合計を求める必要があることがすぐにわかります。 入力シーケンスの一部は、単一の数字ではなく複数の結果になる場合があります。

[!code-csharp[SumDieRollsWithGroups](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#15_SumDieRollsWithGroups "Sum die rolls with groups")]

このシナリオでは、`is` パターン式が非常にうまく機能します。 型のチェックの一環として、変数の初期化を記述します。 これにより、検証されたランタイム型の新しい変数が作成されます。

これらのシナリオをさらに拡張していくと、さらに多くの `if` ステートメントと `else if` ステートメントを作成することになります。 それが扱いにくくなったら、`switch` パターン式に切り替えることをお勧めします。

### <a name="switch-statement-updates"></a>`switch` ステートメントの更新

"*一致式*" には、既に C# 言語に含まれている `switch` ステートメントに基づいた、使い慣れた構文があります。 ここで、新しいケースを追加する前に、一致式を使用するように既存のコードを変換してみましょう。 

[!code-csharp[SumUsingSwitch](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#16_SumUsingSwitch "Sum using switch")]

一致式の構文は `is` 式の構文とは若干異なり、型と変数を `case` 式の先頭で宣言します。

一致式では定数もサポートされます。 これにより、単純なケースが取り除かれるため、時間を節約できます。

[!code-csharp[SwitchWithConstants](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#17_SwitchWithConstants "Switch with constants")]

上のコードでは、`int` の特殊なケースとして `0` のケース、入力がない場合の特殊なケースとして `null` のケースが追加されています。 これは、switch パターン式の重要な新機能の 1 つを示しています。ここでは、`case` 式の順序が重要になります。 `0` のケースは、一般的な `int` のケースの前に記述する必要があります。 そうしないと、一致する最初のパターンは、値が `0` であっても `int` のケースになります。 後のケースが先に処理されるように一致式の順序を誤って指定すると、コンパイラはそこにフラグを設定し、エラーを生成します。

これと同じ動作により、空の入力シーケンスに対する特殊なケースにも対応できます。
このコードから、要素を持つ `IEnumerable` 項目のケースは一般的な `IEnumerable` ケースの前に配置する必要があることがわかります。

このバージョンでは、`default` ケースも追加されています。 `default` ケースは、常に最後に評価されます。ソース内で記述される順序は関係ありません。 そのため、慣習として、`default` ケースを最後に配置します。

最後に、新しいスタイルのサイコロ用に最後の `case` を追加しましょう。 ゲームによっては、より広範な数字を表すためにパーセンタイル ダイスが使用される場合があります。 

> [!NOTE]
> 10 面のパーセンタイル ダイスを 2 つ使用すると、0 から 99 までのすべての数字を表すことができます。 1 つのサイコロの面には、`00`、`10`、`20`、`90` のようなラベルが付けられています。 もう 1 つのサイコロの面には、`0`、`1`、`2`、`9` のようなラベルが付けられています。 2 つのサイコロの数字を加算すると、0 から 99 までのすべての数字を取得することができます。

この種類のサイコロをコレクションに追加するには、まずパーセンタイル ダイスを表す型を定義します。 `TensDigit` プロパティは値 `0`、`10`、`20` を、最大 `90` まで格納します。

[!code-csharp[18_PercentileDice](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#18_PercentileDice "Percentile Die type")]

次に、新しい型の `case` 一致式を追加します。

[!code-csharp[SwitchWithNewTypes](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#19_SwitchWithNewTypes "Include Percentile Die type")]

パターン マッチング式の新しい構文を使用すると、オブジェクトの型やその他のプロパティに基づいたディスパッチ アルゴリズムを、明確かつ簡潔な構文を使用して簡単に作成できます。 パターン マッチング式は、継承によって関連付けられていないデータ型に対してこれらのコンストラクトを有効にします。

パターン マッチングの詳細については、[C# のパターン マッチング](../pattern-matching.md)に特化したトピックを参照してください。

## <a name="ref-locals-and-returns"></a>ref ローカル変数と戻り値

この機能により、他の場所に定義されている変数への参照を使用したり返したりするアルゴリズムが実現します。 1 つの例として、大規模なマトリックスを使用していて、特定の特性を持つ 1 つの場所を探します。 1 つのメソッドでは、マトリックス内の単一の場所に 2 つのインデックスが返されます。

[!code-csharp[FindReturningIndices](../../../samples/snippets/csharp/new-in-7/MatrixSearch.cs#20_FindReturningIndices "Find returning indices")]

このコードには多くの問題があります。 まず、これは、タプルを返すパブリック メソッドです。 この言語ではこれがサポートされていますが、パブリック API にはユーザー定義型 (クラスまたは構造体) をお勧めします。

2 つ目に、このメソッドは、マトリックスの項目のインデックスを返します。
そのため、呼び出し元は、これらのインデックスを使用してマトリックスを逆参照し、1 つの要素を変更するコードを記述することになります。

[!code-csharp[UpdateItemFromIndices](../../../samples/snippets/csharp/new-in-7/program.cs#21_UpdateItemFromIndices "Update Item From Indices")]

それよりも、変更するマトリックス内の要素への "*参照*" を返すメソッドを記述することをお勧めします。 以前のバージョンでは、これを実現するには、アンセーフ コードを使用し、`int` へのポインターを返す方法しかありません。

それでは、一連の変更を確認しながら、ref ローカル変数の機能と、内部ストレージへの参照を返すメソッドの作成方法を説明します。
その過程で、ref 戻り値および ref ローカル変数の機能の誤用を防ぐための規則についても説明します。

まず、タプルの代わりに `ref int` を返すように `Find` メソッドの宣言を変更します。 次に、2 つのインデックスの代わりに、マトリックスに格納されている値を返すように、return ステートメントを変更します。

```csharp
// Note that this won't compile. 
// Method declaration indicates ref return,
// but return statement specifies a value return.
public static ref int Find2(int[,] matrix, Func<int, bool> predicate)
{
    for (int i = 0; i < matrix.GetLength(0); i++)
        for (int j = 0; j < matrix.GetLength(1); j++)
            if (predicate(matrix[i, j]))
                return matrix[i, j];
    throw new InvalidOperationException("Not found");
}
```

メソッドが `ref` 変数を返すことを宣言する際に、それぞれの return ステートメントに `ref` キーワードも追加する必要があります。 これは、参照渡しを示します。これにより、後でコードを読む開発者にも、そのメソッドが参照渡しで返すことがわかります。

[!code-csharp[FindReturningRef](../../../samples/snippets/csharp/new-in-7/MatrixSearch.cs#22_FindReturningRef "Find returning by reference")]

このメソッドはマトリックス内の整数値への参照を返すため、呼び出し側のコードを修正する必要があります。  `var` 宣言は、`valItem` がタプルではなく `int` であることを意味します。

[!code-csharp[AssignRefReturnToValue](../../../samples/snippets/csharp/new-in-7/program.cs#23_AssignRefReturnToValue "Assign ref return to value")]

上記の例の 2 番目の `WriteLine` ステートメントで出力される値は `42` であり、`24` ではありません。 変数 `valItem` は、`int` であり、`ref int` ではありません。 `var` キーワードを使用すると、コンパイラは、型を指定できますが、`ref` 修飾子を暗黙的に追加しません。 代わりに、`ref return` によって参照される値が代入の左辺にある変数に "*コピー*" されます。 この変数は `ref` ローカル変数ではありません。

目的の結果を得るために、`ref` 修飾子をローカル変数の宣言に追加して、戻り値が参照の場合に変数が参照になるようにする必要があります。

[!code-csharp[AssignRefReturn](../../../samples/snippets/csharp/new-in-7/program.cs#24_AssignRefReturn "Assign ref return")]

上記の例の 2 番目の `WriteLine` ステートメントは、値 `24` を出力します。これは、マトリックスのストレージが変更されたことを示しています。 ローカル変数は `ref` 修飾子で宣言されており、`ref` 戻り値を受け取ります。 `ref` 変数は宣言時に初期化する必要があります。宣言と初期化を分けることはできません。

C# 言語には、これ以外に、`ref` ローカル変数と戻り値の誤用を防ぐ規則が 3 つあります。

* 標準的なメソッドの戻り値を `ref` ローカル変数に割り当てることはできません。
    - したがって、`ref int i = sequence.Count();` のようなステートメントは使用できません。
* 有効期間がメソッドの実行期間を超えない変数に `ref` を返すことはできません。
    - つまり、ローカル変数または類似のスコープの変数への参照を返すことはできません。
* `ref` ローカル変数と戻り値は、非同期メソッドと共に使用することはできません。
    - コンパイラは、非同期メソッドが戻るときに、参照先の変数が、最終的な値に設定されているかどうかを認識できません。

ref ローカル変数および ref 戻り値の追加により、値のコピーを回避したり、逆参照操作を複数回実行したりすることで、より効率的なアルゴリズムを実現できます。

戻り値に `ref` を追加することは、[ソース互換性がある変更](version-update-considerations.md#source-compatible-changes)です。 既存のコードはコンパイルされますが、参照戻り値は割り当て時にコピーされます。 呼び出し元は、戻り値を参照として格納するために、戻り値の記憶域を `ref` ローカル変数に更新する必要があります。

詳しくは、[ref](../language-reference/keywords/ref.md) キーワードに関する記事をご覧ください。

## <a name="local-functions"></a>ローカル関数

クラスの多くの設計には、1 つの場所からのみ呼び出されるメソッドが含まれます。 このような追加のプライベート メソッドを使用することで、各メソッドのサイズを小さくし、その焦点を絞ることができます。 ただし、このプライベート メソッドにより、初めてクラスを読むときに理解しにくくなる場合があります。 これらのメソッドは、単一の呼び出し元の場所のコンテキストの外部でも理解する必要があります。

そのような設計では、"*ローカル関数*" を使用すると、別のメソッドのコンテキスト内でメソッドを宣言することができます。 これにより、クラスを読むときに、ローカル メソッドが、それが宣言されているコンテキストからのみ呼び出されることを容易に理解できます。

ローカル関数には、パブリック反復子メソッドとパブリック非同期メソッドという 2 つの非常に一般的なユース ケースがあります。 どちらの種類のメソッドも、プログラマーが期待するよりも遅くエラーを報告するコードを生成します。 反復子メソッドの場合、例外が検出されるのは、返されたシーケンスを列挙するコードを呼び出した場合のみです。 非同期メソッドの場合、例外が検出されるのは、返された `Task` が待機状態になったときのみです。

それでは、反復子メソッドから見ていきましょう。

[!code-csharp[IteratorMethod](../../../samples/snippets/csharp/new-in-7/Iterator.cs#25_IteratorMethod "Iterator method")]

下のコードでは、不適切な方法で反復子メソッドを呼び出しています。

[!code-csharp[CallIteratorMethod](../../../samples/snippets/csharp/new-in-7/program.cs#26_CallIteratorMethod "Call iterator method")]

例外は、`resultSet` が作成されたときではなく、`resultSet` が反復処理されたときにスローされます。
ここに示した例では、ほとんどの開発者が問題を迅速に診断できるでしょう。 ところが、より大きなコードベースでは、多くの場合、反復子を作成するコードが結果を列挙するコードの近くにあるわけではありません。 パブリック メソッドですべての引数を検証し、プライベート メソッドで列挙型を生成するように、コードをリファクタリングすることができます。

[!code-csharp[IteratorMethodRefactored](../../../samples/snippets/csharp/new-in-7/Iterator.cs#27_IteratorMethodRefactored "Iterator method refactored")]

このリファクタリングしたバージョンでは、例外が即座にスローされます。これは、パブリック メソッドが反復子メソッドではないためです。つまり、`yield return` 構文を使用するのは、プライベート メソッドのみです。 ただし、このリファクタリングには潜在的な問題があります。 プライベート メソッドは、パブリック インターフェイス メソッドからのみ呼び出す必要があります。そうしないと、すべての引数の検証がスキップされるためです。
クラスを読む開発者がこの事実を発見するには、クラス全体を読み、`alphabetSubsetImplementation` メソッドへの他の参照を検索する必要があります。

`alphabetSubsetImplementation` をパブリック API メソッド内のローカル関数として宣言することで、この設計の意図をより明確にすることができます。

[!code-csharp[22_IteratorMethodLocal](../../../samples/snippets/csharp/new-in-7/Iterator.cs#28_IteratorMethodLocal "Iterator method with local function")]

上記のバージョンでは、ローカル メソッドが外部メソッドのコンテキストでのみ参照されることが明確になっています。 また、ローカル関数の規則により、開発者が誤ってクラス内の別の場所からローカル関数を呼び出して、引数の検証をバイパスできないようになっています。

同じ手法を `async` メソッドで使用すると、引数の検証で発生する例外が非同期操作の開始前にスローされることを保証できます。

[!code-csharp[TaskExample](../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#29_TaskExample "Task returning method with local function")]

> [!NOTE]
> ローカル関数によってサポートされる設計の中には、"*ラムダ式*" を使用して実現できるものもあります。 興味のある方は、[その違いの詳細を確認してください](../local-functions-vs-lambdas.md)。

## <a name="more-expression-bodied-members"></a>式形式のメンバーの追加

C# 6 では、メンバー関数の[式形式のメンバー](csharp-6.md#expression-bodied-function-members)と読み取り専用プロパティが導入されました。 C# 7.0 では、式として実装できる許可されたメンバーが拡張されます。 C# 7.0 では、"*コンストラクター*"、"*ファイナライザー*"、`get` アクセサー、および `set` アクセサーを "*プロパティ*" と "*インデクサー*" に実装できます。 それぞれの例を次のコードに示します。

[!code-csharp[ExpressionBodiedMembers](../../../samples/snippets/csharp/new-in-7/expressionmembers.cs#36_ExpressionBodiedEverything "new expression-bodied members")]

> [!NOTE]
> この例ではファイナライザーは必要ありませんが、その構文を紹介するために示しています。 アンマネージ リソースを解放する必要がない限り、クラスにファイナライザーを実装しないでください。 また、アンマネージ リソースを直接管理する代わりに、<xref:System.Runtime.InteropServices.SafeHandle> クラスの使用を検討する必要もあります。

式形式のメンバー用のこれらの新しい場所は、C# 言語の重要なマイルストーンです。これらの機能は、オープン ソースの [Roslyn](https://github.com/dotnet/Roslyn) プロジェクトに関わるコミュニティ メンバーによって実装されました。

メソッドを式のようなメンバーに変更することは、[バイナリ互換性がある変更](version-update-considerations.md#binary-compatible-changes)です。

## <a name="throw-expressions"></a>throw 式

C# では、`throw` は常にステートメントでした。 `throw` は式ではなくステートメントであるため、使用できない C# コンストラクトがありました。 これには、条件式、null 結合式、および一部のラムダ式が含まれます。 式形式のメンバーが追加されたことにより、さらに多くの場所で `throw` 式が役に立つようになりました。 C# 7.0 では、このようなコンストラクトを記述できるように、"*throw 式*" が導入されています。

その構文は、`throw` ステートメントに常に使用してきた構文と同じです。 唯一の違いは、条件式などの新しい場所に配置できるようになったことです。

[!code-csharp[Throw_ExpressionExample](../../../samples/snippets/csharp/new-in-7/throwexpressions.cs#37_Throw_ExpressionExample "conditional throw expressions")]

この機能により、初期化式で throw 式を使用できるようになります。

[!code-csharp[ThrowInInitialization](../../../samples/snippets/csharp/new-in-7/throwexpressions.cs#38_ThrowInInitialization "conditional throw expressions")]

以前は、これらの初期化は、コンストラクターの本体に throw ステートメントを使用して、コンストラクター内で行う必要がありました。


[!code-csharp[ThrowInConstructor](../../../samples/snippets/csharp/new-in-7/throwexpressions.cs#39_ThrowInConstructor "throw statements")]

> [!NOTE]
> 前述のコンストラクトのどちらにおいても、オブジェクトの構築中に例外がスローされます。 多くの場合、これらの例外から回復するのは困難です。
> そのため、構築中に例外をスローする設計は推奨しません。

## <a name="generalized-async-return-types"></a>一般化された async の戻り値の型

非同期メソッドから `Task` オブジェクトを返すと、特定のパスでパフォーマンスのボトルネックが発生する可能性があります。 `Task` は参照型です。したがって、これを使うことは、オブジェクトを割り当てることを意味します。 `async` 修飾子で宣言されたメソッドがキャッシュされた結果を返すか、同期的に完了する場合、追加の割り当ては、コードのパフォーマンスが重要なセクションにおいて大きな時間コストにつながります。 厳密なループ処理でこのような割り当てが発生した場合、非常にコストがかかる場合があります。

新しい言語機能は、非同期メソッドが、`Task`、`Task<T>`、`void` に加えて他の型を返す可能性があることを意味します。 返される型は引き続き非同期パターンを満たす必要があります。つまり、`GetAwaiter` メソッドはアクセス可能である必要があります。 1 つの具体的な例として、この新しい言語機能を使用するために .NET Framework に `ValueTask` 型が追加されました。 

[!code-csharp[UsingValueTask](../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#30_UsingValueTask "Using ValueTask")]

> [!NOTE]
> <xref:System.Threading.Tasks.ValueTask%601> 型を使用するには、NuGet パッケージ [`System.Threading.Tasks.Extensions`](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) を追加する必要があります。

単純な最適化では、これまで `Task` が使用されていた場所に `ValueTask` を使用します。 ただし、手動で追加の最適化を実行する場合は、非同期処理の結果をキャッシュし、その結果を以降の呼び出しで再利用できます。 `ValueTask` 構造体には `Task` パラメーターを持つコンストラクターがあるため、既存の非同期メソッドの戻り値から `ValueTask` を構築できます。

[!code-csharp[AsyncOptimizedValueTask](../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#31_AsyncOptimizedValueTask "Return async result or cached value")]

すべてのパフォーマンスに関する推奨事項と同様に、コードに大規模な変更を加える前に、両方のバージョンのベンチマークを計測する必要があります。

戻り値が `await` ステートメントのターゲットである場合、<xref:System.Threading.Tasks.Task%601> から <xref:System.Threading.Tasks.ValueTask%601> への API の変更は[ソース互換性がある変更](version-update-considerations.md#source-compatible-changes)です。 一般的に、`ValueTask` への互換はそうではありません。

## <a name="numeric-literal-syntax-improvements"></a>数値リテラルの構文の改善

数値定数を読み間違えると、コードを初めて読むときにコードを理解するのが難しくなる場合があります。 これは、数値がビット マスクや数値以外の記号として使用されている場合にありがちなことです。 C# 7.0 では、使用目的に応じて最も読みやすい形式で簡単に数値を記述しできるように、"*バイナリ リテラル*" と "*桁区切り文字*" という 2 つの新機能が導入されました。

ビット マスクを作成しているときや、数値をバイナリで表現するとコードが最も読みやすくなる場合は、数字をバイナリで記述します。

[!code-csharp[BinaryConstants](../../../samples/snippets/csharp/new-in-7/Program.cs#32_BinaryConstants "Binary constants")]

定数の先頭にある `0b` は、数値が 2 進数として記述されていることを示します。

バイナリ数値は非常に長くなる場合があるため、ビット パターンが見やすくなるように、桁区切り記号として `_` が導入されました。

[!code-csharp[ThousandSeparators](../../../samples/snippets/csharp/new-in-7/Program.cs#33_ThousandSeparators "Thousands separators")]

桁区切り記号は定数のどこにでも置くことができます。 10 進数の場合は、3 桁の区切り記号として使用するのが一般的です。

[!code-csharp[LargeIntegers](../../../samples/snippets/csharp/new-in-7/Program.cs#34_LargeIntegers "Large integer")]

桁区切り記号は、`decimal` 型、`float` 型、`double` 型でも使用できます。

[!code-csharp[OtherConstants](../../../samples/snippets/csharp/new-in-7/Program.cs#35_OtherConstants "non-integral constants")]

これらをまとめると、数値定数をさらに見やすい状態で宣言できます。
