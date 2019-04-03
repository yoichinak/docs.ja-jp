---
title: シーケンス
description: 大規模な順序付けられたデータのコレクションを持っていてもすべての要素を使用すると必ずしも期待しないときに、F# シーケンスを使用する方法について説明します。
ms.date: 02/19/2019
ms.openlocfilehash: a7791be5e8bd07d81fe9e890fc5896b181f0cb39
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/21/2019
ms.locfileid: "56583928"
---
# <a name="sequences"></a>シーケンス

> [!NOTE]
> この記事の API リファレンスのリンクをクリックすると MSDN に移動します。  docs.microsoft.com API リファレンスは完全ではありません。

A*シーケンス*論理的な一連の要素は、すべて 1 つの型。 シーケンスは、大規模な順序付けられたデータのコレクションがあるが、すべての要素を使用する予定がない場合に特に便利です。 シーケンスは、すべての要素を使用ない状況で一覧よりも優れたパフォーマンスを提供できるように、シーケンスの個々 の要素としてのみ計算が必要です。 シーケンスがによって表される、`seq<'T>`エイリアスである型の`System.Collections.Generic.IEnumerable`します。 そのため、実装する .NET Framework 型`System.IEnumerable`シーケンスとして使用できます。 [Seq モジュール](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684)シーケンスに関する操作のサポートを提供します。

## <a name="sequence-expressions"></a>シーケンス式

A*シーケンス式*シーケンスに評価される式を指定します。 シーケンス式は、いくつかの形式にかかります。 最も単純な形式では、範囲を指定します。 たとえば、 `seq { 1 .. 5 }` 1 と 5 のエンドポイントを含む 5 つの要素を含むシーケンスを作成します。 指定され、増分 (したりデクリメント) 2 つの二重ピリオドの間。 たとえば、次のコードは、10 の倍数のシーケンスを作成します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1502.fs)]

シーケンス式、順序の値を生成する F# 式で構成されます。 使用できる、`yield`キーワード、シーケンスの一部となる値を生成します。

例を次に示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1503.fs)]

使用することができます、`->`演算子の代わりに`yield`を省略した場合、`do`キーワードは、次の例に示すようにします。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1504.fs)]

次のコードでは、グリッドを表す配列にインデックスと共に座標ペアの一覧を生成します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1505.fs)]

`if`シーケンスで使用される式はフィルターです。 たとえば、関数がある場合、唯一の素数のシーケンスを生成する`isprime`型の`int -> bool`、次のように、シーケンスを作成します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1506.fs)]

使用すると`yield`または`->`シーケンスの 1 つの要素を生成する、イテレーションの各反復処理が必要です。 各イテレーションが要素のシーケンスを生成した場合を使用して、`yield!`します。 その場合は、各反復処理で生成された要素は、最後のシーケンスを生成するために連結されます。

シーケンス式で複数の式を組み合わせることができます。 それぞれの式によって生成された要素が連結されます。 例については、このトピックの「例」セクションを参照してください。

## <a name="examples"></a>使用例

最初の例では、イテレーション、フィルター、および配列を生成する yield を含むシーケンス式を使用します。 このコードは、1 ~ 100 のコンソールに素数のシーケンスを出力します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1507.fs)]

次のコードでは`yield`それぞれ 2 つの要素と、製品で構成される 3 つの要素の組で構成される乗算テーブルを作成します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1508.fs)]

使用例を次に示します`yield!`を個々 のシーケンスを 1 つの最終的なシーケンスに結合します。 この場合、バイナリ ツリーの各サブツリーのシーケンスは、最後のシーケンスを生成するために、再帰関数で連結されます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1509.fs)]

## <a name="using-sequences"></a>シーケンスの使用

シーケンスと同じ機能の多くをサポートして[一覧](lists.md)します。 シーケンスは、グループ化し、キー生成関数を使用してカウントなどの操作もサポートします。 シーケンスは、サブシーケンスを抽出するためもさまざまな関数をサポートします。

リスト、配列、セット、およびマップなど、多くのデータ型はシーケンスでは暗黙的に列挙可能なコレクションであるためです。 実装する任意の .NET Framework データ型をさらに、引数が動作との共通の F# データ型では、シーケンスを受け取る関数`System.Collections.Generic.IEnumerable<'T>`します。 リスト、リストを受け取ることができるを引数として関数には、この操作を比較します。 型`seq<'T>`の型の省略形は、`IEnumerable<'T>`します。 つまり、任意の型を実装するジェネリック`System.Collections.Generic.IEnumerable<'T>`、設定を含む配列、リスト、および F#、およびもほとんど、.NET Framework コレクション型のマップと互換性のある、`seq`を入力し、シーケンスが必要とされる場所に使用することができます。

## <a name="module-functions"></a>モジュール関数

[Seq モジュール](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684)で、 [Microsoft.FSharp.Collections 名前空間](https://msdn.microsoft.com/library/24f64e5f-5030-47d0-9759-8d3e398ed13f)シーケンスを操作するための関数が含まれています。 これらの関数は、すべてこれらの型の列挙可能なしたがって、シーケンスとして扱うことができますのでに、リスト、配列、マップ、およびセット同様を使用します。

## <a name="creating-sequences"></a>シーケンスの作成

前述のように、シーケンス式を使用して、または特定の関数を使用してシーケンスを作成できます。

使用して空のシーケンスを作成する[Seq.empty](https://msdn.microsoft.com/library/3c7f1c69-6117-4782-b2da-0e04d6854f59)を使用して 1 つだけ指定した要素のシーケンスを作成することも[Seq.singleton](https://msdn.microsoft.com/library/9b8cc460-a282-4ec5-b29a-630ab17e9de7)します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet9.fs)]

使用することができます[Seq.init](https://msdn.microsoft.com/library/059de69d-812c-4f8e-be86-88aa72101576)を要素が指定した関数を使用して作成されたシーケンスを作成します。 シーケンスのサイズを指定します。 この関数と同じように[List.init](https://msdn.microsoft.com/library/dd38c096-0ea8-4858-be6b-794b90418b83)要素は、シーケンスの反復処理が完了するまでは作成されません。 次のコードは、`Seq.init` の使用例です。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet10.fs)]

出力は次のようになります。

```
0 10 20 30 40
```

使用して[Seq.ofArray](https://msdn.microsoft.com/library/299cd4d9-be72-4511-aac8-089e1ddaac99)と[Seq.ofList&#60;' T&#62;関数](https://msdn.microsoft.com/visualfsharpdocs/conceptual/seq.oflist%5b%27t%5d-function-%5bfsharp%5d)、配列とリストからシーケンスを作成することができます。 ただし、変換することも配列とリストのシーケンスにキャスト演算子を使用しています。 両方の手法は、次のコードに表示されます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet11.fs)]

使用して[Seq.cast](https://msdn.microsoft.com/library/1d087db3-a8b2-41dd-8ddc-227544529334)、シーケンスを作成するには、弱く型指定されたコレクションで定義されているものなどから`System.Collections`します。 このような弱く型指定されたコレクションの要素型である`System.Object`非ジェネリックを使用して列挙と`System.Collections.Generic.IEnumerable&#96;1`型。 次のコードの使用を示します`Seq.cast`に変換する、`System.Collections.ArrayList`シーケンスにします。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet12.fs)]

無限のシーケンスを使用して定義することができます、 [Seq.initInfinite](https://msdn.microsoft.com/library/d1804e53-da92-48ec-8d6e-57eaf4c62bef)関数。 このようなシーケンスは、要素のインデックスから各要素を生成する関数を提供します。 レイジー評価; のため、無限のシーケンスが可能指定した関数を呼び出すことによって、必要に応じて、要素が作成されます。 次のコード例では、浮動小数点、ここでは、代替の一連の連続した整数の 2 乗の逆数の無限のシーケンスを生成します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet13.fs)]

[Seq.unfold](https://msdn.microsoft.com/library/7d9232fc-742e-42bc-bdf7-6f130f0eff21)状態を受け取り、シーケンスの後続の各要素を生成するためにそれを変換する計算関数からシーケンスを生成します。 状態は、値は、各要素の計算に使用し、各要素の計算を変更できます。 2 番目の引数`Seq.unfold`シーケンスを開始するために使用される初期値です。 `Seq.unfold` 返すことによって、シーケンスを終了することができます、状態のオプションの種類を使用して、`None`値。 次のコードは、シーケンスの 2 つの例を示しています。`seq1`と`fib`、によって生成される、`unfold`操作。 まず、`seq1`は最大 20 の番号を持つ単純なシーケンスだけです。 次に、`fib`を使用して`unfold`フィボナッチ シーケンスを計算します。 フィボナッチ シーケンス内の各要素は、前の 2 つのフィボナッチ数の合計であるために、状態値は、前の 2 つの数値のシーケンスで構成される組になります。 初期値は`(1,1)`シーケンス内の最初の 2 つの数値。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet14.fs)]

出力は次のとおりです。

```
The sequence seq1 contains numbers from 0 to 20.

0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20

The sequence fib contains Fibonacci numbers.

2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597
```

次のコードでは、ここで説明されているを生成し、無限のシーケンスの値を計算するシーケンス モジュールの関数の多くを使用する例を示します。 コードは、実行に数分をかかります。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet15.fs)]

## <a name="searching-and-finding-elements"></a>検索して、要素の検索

シーケンスは、リストで使用できる機能をサポートします。[Seq.exists](https://msdn.microsoft.com/library/428c97bf-599d-4c39-a5b9-f8717c198ad1)、 [Seq.exists2](https://msdn.microsoft.com/library/efdf14a4-27f7-4dc1-9281-52639e66d565)、 [Seq.find](https://msdn.microsoft.com/library/02c21ecd-97e5-4e99-a4c1-b4d0b730b7d8)、 [Seq.findIndex](https://msdn.microsoft.com/library/96dfe86b-df15-4d92-8316-7cd6055e09f3)、 [Seq.pick](https://msdn.microsoft.com/library/a87bc771-55f7-43f9-94f9-33d8f9bf325d)、 [Seq.tryFind](https://msdn.microsoft.com/library/ac43c6f5-4dc7-4e9a-a222-00b5736aee47)、および[Seq.tryFindIndex](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a)します。 シーケンスの使用可能なこれらの関数のバージョンの検索対象の要素に達するまでのシーケンスを評価します。 例については、[一覧](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d)を参照してください。

## <a name="obtaining-subsequences"></a>サブシーケンスの取得

[Seq.filter](https://msdn.microsoft.com/library/7f2e9850-a660-460c-9831-3bbff5613770)と[Seq.choose](https://msdn.microsoft.com/library/63b83b06-4b24-4239-bf69-a2c12d891395)はシーケンスの要素が評価されるまで、フィルタ リングと選択が発生しない点を除いて、一覧については、使用できる対応する関数のようにします。

[Seq.truncate](https://msdn.microsoft.com/library/1892dfeb-308e-45e2-857a-3c3405d02244)から別のシーケンスをシーケンスを作成しますが、シーケンスの指定した要素数に制限します。 [Seq.take](https://msdn.microsoft.com/library/6e75f701-640b-4c4a-9d63-4313fc090596)指定の数のシーケンスの先頭からの要素のみを含む新しいシーケンスを作成します。 指定するためより少ないシーケンスの要素がある場合`Seq.take`スロー、`System.InvalidOperationException`します。 間の差`Seq.take`と`Seq.truncate`される`Seq.truncate`要素の数が指定した数よりも少ない場合、エラーは発生しません。

次のコードの動作を示します点と相違`Seq.truncate`と`Seq.take`します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet16.fs)]

出力では、エラーが発生する前に次に示します。

```
1 4 9 16 25 
1 4 9 16 25 36 49 64 81 100 
1 4 9 16 25 
1 4 9 16 25 36 49 64 81 100
```

使用して[Seq.takeWhile](https://msdn.microsoft.com/library/19eea4ce-66e0-4353-b015-72eb03421d92)、述語関数 (ブール関数) を指定し、述語は、元のシーケンスの要素から成る別のシーケンスからシーケンスの作成`true`が終了します。述語を返す最初の要素の前に`false`します。 [Seq.skip](https://msdn.microsoft.com/library/b4eb3f08-8594-4d17-8180-852c6c688bf1)指定したもう 1 つのシーケンスの最初の要素数をスキップし、残りの要素を返すシーケンスを返します。 [Seq.skipWhile](https://msdn.microsoft.com/library/fb729021-2a3c-430f-83c3-0b37526f1a16)述語を返す限り、別のシーケンスの最初の要素をスキップしてシーケンスを返します`true`、述語がを返す最初の要素で始まる残りの要素を返します`false`.

次のコード例の動作を示しています点と相違`Seq.takeWhile`、 `Seq.skip`、および`Seq.skipWhile`します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet17.fs)]

出力は次のとおりです。

```
1 4 9 
36 49 64 81 100 
16 25 36 49 64 81 100
```

## <a name="transforming-sequences"></a>シーケンスに変換します。

[Seq.pairwise](https://msdn.microsoft.com/library/210dcf26-4e24-4d83-af6d-a8288b2ae4b1)入力シーケンスの一連の要素がタプルにグループ化する新しいシーケンスを作成します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet18.fs)]

[Seq.windowed](https://msdn.microsoft.com/library/8b565b8f-d645-4dba-be22-099075fe4744)などは`Seq.pairwise`タプルのシーケンスを生成するには、代わりに、隣接する要素のコピーを格納する配列のシーケンスを生成する点を除いて、(、*ウィンドウ*) シーケンスから。 各配列内には、隣接する要素の数を指定します。

次のコード例は、`Seq.windowed` の使用方法を示します。 この場合、ウィンドウ内の要素の数は 3 です。 この例では`printSeq`、上記のコード例で定義されています。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet180.fs)]

出力は次のとおりです。

最初のシーケンス。

```
1.0 1.5 2.0 1.5 1.0 1.5 

Windows of length 3: 
[|1.0; 1.5; 2.0|] [|1.5; 2.0; 1.5|] [|2.0; 1.5; 1.0|] [|1.5; 1.0; 1.5|] 

Moving average: 
1.5 1.666666667 1.5 1.333333333
```

## <a name="operations-with-multiple-sequences"></a>複数のシーケンスでの操作

[Seq.zip](https://msdn.microsoft.com/library/0a5df8bf-0d48-44ce-bff4-e8ef1df5bca4)と[Seq.zip3](https://msdn.microsoft.com/library/ef13bebb-22ae-4eb9-873b-87dd29154d16) 2 または 3 つのシーケンスを受け取り、タプルのシーケンスを生成します。 これらの関数は、対応する関数を使用できるようには[一覧](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d)します。 2 つ以上のシーケンスに 1 つのシーケンスを分離する対応する機能はありません。 シーケンスのこの機能を必要がある場合、リストに、シーケンスを変換し、使用して[List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21)します。

## <a name="sorting-comparing-and-grouping"></a>並べ替え、比較、およびグループ化

リストの並べ替え関数は、シーケンスでも動作します。 これが含まれています[Seq.sort](https://msdn.microsoft.com/library/327ea595-e77c-4529-b61e-8c6cbf5ec92e)と[Seq.sortBy](https://msdn.microsoft.com/library/4f8b4fb9-bf20-49d9-b4ee-dcc906c8208f)します。 これらの関数は、シーケンス全体を反復処理します。

使用して 2 つのシーケンスを比較する、 [Seq.compareWith](https://msdn.microsoft.com/library/5a740135-0b3a-4545-816f-8f91cc31290f)関数。 関数は、さらに、一連の要素を比較し、最初の等しくないペアを見つけたときに停止します。 追加の要素は、比較には影響しません。


  `Seq.compareWith` の使用方法を次のコードに示します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet19.fs)]

前のコードでは、最初の要素のみが計算され、検査すると、し、結果は-1。

[Seq.countBy](https://msdn.microsoft.com/library/721702a5-150e-4fe8-81cd-ffbf8476cc1f)という値を生成する関数を受け取り、*キー*要素ごとにします。 各要素に対してこの関数を呼び出すことによって各要素のキーが生成されます。 `Seq.countBy` キーの値とキーの各値を生成する要素の数を含むシーケンスを返します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet201.fs)]

出力は次のとおりです。

```
(1, 34) (2, 33) (0, 33)
```

前の出力は、2、キーを生成する 33 の値と 0 キーを生成した 33 値 34 1、キーの生成元のシーケンスの要素があったことを示しています。

呼び出すことによって、シーケンスの要素をグループ化できます[Seq.groupBy](https://msdn.microsoft.com/library/d46a04df-1a42-40cc-a368-058c9c5806fd)します。 `Seq.groupBy` シーケンスと要素からキーを生成する関数を受け取ります。 関数は、シーケンスの各要素に対して実行されます。 `Seq.groupBy` それぞれの組の最初の要素がキーで、2 つ目は、そのキーを生成する要素のシーケンスは、タプルのシーケンスを返します。

次のコード例は、の使用を示しています。`Seq.groupBy`を 0、1、および 2 は、個別のキー値を持つ 3 つのグループに 1 から 100 の数値のシーケンスをパーティション分割します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet202.fs)]

出力は次のとおりです。

```
(1, seq [1; 4; 7; 10; ...]) (2, seq [2; 5; 8; 11; ...]) (0, seq [3; 6; 9; 12; ...])
```

呼び出すことによって、重複する要素を排除するシーケンスを作成する[Seq.distinct](https://msdn.microsoft.com/library/99d01014-7e0e-4e7b-9d0a-41a61d93f401)します。 使用することもできます[Seq.distinctBy](https://msdn.microsoft.com/library/9293293b-9420-49c8-848f-401a9cd49b75)、各要素に対して呼び出されるキー生成関数を受け取ります。 結果のシーケンスに固有のキーのある、元のシーケンスの要素が含まれています以前の要素に重複するキーの生成後の要素は破棄されます。


  `Seq.distinct` の使用方法を次のコード例に示します。 `Seq.distinct` バイナリの数値を表すシーケンスを生成して、表示のみの個別の要素には 0 と 1 で示されます。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet22.fs)]

次のコード例`Seq.distinctBy`負と正の数値を含むシーケンスを開始し、キー生成関数と絶対値関数を使用します。 結果のシーケンスには負の数値がシーケンスの前表示され、したがって、同じ絶対値が正の数値ではなく、選択するために、シーケンス内の負の数値に対応するすべての正の数値がありません。値、またはキー。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet23.fs)]

## <a name="readonly-and-cached-sequences"></a>読み取り専用とキャッシュされたシーケンス

[Seq.readonly](https://msdn.microsoft.com/library/88059cb4-3bb0-4126-9448-fbcd48fe13a7)シーケンスの読み取り専用コピーを作成します。 `Seq.readonly` 配列などの読み取り/書き込みコレクションがあるし、元のコレクションを変更したくない場合に役立ちます。 この関数は、データのカプセル化を保持するために使用できます。 次のコード例では、配列を含む型が作成されます。 プロパティは、配列を公開しますが、配列を返す代わりを使用して、配列から作成されたシーケンスを返します`Seq.readonly`します。

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet24.fs)]

[Seq.cache](https://msdn.microsoft.com/library/d197f9cc-08bf-4986-9869-246e72ca73f0)シーケンスの保存されているバージョンを作成します。 使用して、`Seq.cache`を避けるために再評価シーケンス、または、シーケンスを使用して複数のスレッドが、各要素は、1 回だけに機能を確認する必要があります。 複数のスレッドによって使用されているシーケンスがある場合は、する 1 つのスレッドを列挙し、元のシーケンスの値を計算することができ、残りのスレッドは、キャッシュされたシーケンスを使用できます。

## <a name="performing-computations-on-sequences"></a>シーケンスに対する計算の実行

などは、一覧のような単純な算術演算[Seq.average](https://msdn.microsoft.com/library/609d793b-c70f-4e36-9ab4-d928056d65b8)、 [Seq.sum](https://msdn.microsoft.com/library/01208515-4880-4358-91f5-af34f66dc77a)、 [Seq.averageBy](https://msdn.microsoft.com/library/47c855c1-2dbd-415a-885e-b909d9d3e4f8)、 [Seq.sumBy](https://msdn.microsoft.com/library/68cca78c-94ed-4a45-9b8d-34d2c5f2b1b1)など。

[Seq.fold](https://msdn.microsoft.com/library/30c4c95a-9563-4c96-bbe1-f7aacfd026e3)、 [Seq.reduce](https://msdn.microsoft.com/library/a2ad4f64-ac69-47d2-92f0-7173d9dfeae9)、および[Seq.scan](https://msdn.microsoft.com/library/7e2d23e9-f153-4411-a884-b6d415ff627e)はリストの使用できる対応する関数のようにします。 シーケンスは、リストをサポートするこれらの関数の完全なバリエーションのサブセットをサポートします。 詳細と例については、[一覧](lists.md)を参照してください。

## <a name="see-also"></a>関連項目

- [F# 言語リファレンス](index.md)
- [F# の型](fsharp-types.md)
