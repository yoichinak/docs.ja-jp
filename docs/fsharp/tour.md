---
title: F# のツアー
description: 主な機能のいくつかを確認、F#プログラミング言語でこのツアーではコード サンプルを使用します。
ms.date: 11/06/2018
ms.openlocfilehash: 64394342777003b33dd77028739fb7209b9f3c86
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301253"
---
# <a name="tour-of-f"></a>F# のツアー\#

F# について学習する最善の方法は、F# コードを読み書きすることです。 この記事は、F# 言語のいくつかの主な機能の手引きとしての役割を果たし、コンピューターで実行できるいくつかのコード スニペットを示します。 開発環境を設定する方法については、[Getting Started](tutorials/getting-started/index.md) を参照してください。

2 つの主要な概念があるF#: 関数と型。  このツアーではこれら 2 つの概念には、言語の機能を強調します。

## <a name="executing-the-code-online"></a>オンラインでのコードを実行します。

いない場合F#コンピューターにインストールされている、ことができますを実行するすべてのサンプルと共にブラウザーに[お試しくださいF#WebAssembly で](https://tryfsharp.fsbolero.io/)します。 Fable は言語にF#お使いのブラウザーで直接実行します。 REPL で次のサンプルを表示するチェック アウト**サンプル > 学習 > のツアー F#**  Fable レプリケーションの左側のメニュー バーに

## <a name="functions-and-modules"></a>関数、およびモジュール

任意の F# プログラムの最も基本的な部分が***関数***編成***モジュール***します。  [関数](language-reference/functions/index.md)出力を生成する入力に作業を実行し、で構成される[モジュール](language-reference/modules.md)、F# でグループ化する主な方法であります。  使用して定義されている、 [ `let`バインド](language-reference/functions/let-bindings.md)関数の名前し、その引数を定義します。

[!code-fsharp[BasicFunctions](../../samples/snippets/fsharp/tour.fs#L101-L133)]

`let` バインディングでは、値を他の言語での変数のような名前にバインドする方法も。  `let` バインドは***不変***既定では、値または関数の名前をバインドしたら、変更できないことを意味する、インプレースします。  これは、他の言語での変数とは対照的***変更可能な***時間で任意の時点でその値の意味を変更できます。  変更可能なバインディングを必要とする場合は使用できます`let mutable ...`構文。

[!code-fsharp[Immutability](../../samples/snippets/fsharp/tour.fs#L75-L94)]

## <a name="numbers-booleans-and-strings"></a>数値、ブール値、および文字列

.NET 言語として F# をサポートしています、同じ基になる[プリミティブ型](language-reference/primitive-types.md).NET 内に存在します。

さまざまな数値型は F# で表されます。 次に示します。

[!code-fsharp[Numbers](../../samples/snippets/fsharp/tour.fs#L49-L68)]

どのようなブール値を次に示し、基本的な条件付きロジックを実行するようになります。

[!code-fsharp[Bools](../../samples/snippets/fsharp/tour.fs#L142-L152)]

ここでは、どのような basic と[文字列](language-reference/strings.md)操作のようになります。

[!code-fsharp[Strings](../../samples/snippets/fsharp/tour.fs#L158-L180)]

## <a name="tuples"></a>タプル

[タプル](language-reference/tuples.md)は F# の大きな問題です。  これらは、値自体として扱うことができますが、名前のない、順序付けされた値のグループです。  それらの他の値からごとに集計値として考えます。  簡単に、関数から複数の値を返すまたはアドホック便宜上いくつかの値をグループ化など、数多くの用途があります。

[!code-fsharp[Tuples](../../samples/snippets/fsharp/tour.fs#L186-L203)]

F# 4.1、作成することも`struct`組。  これらも相互運用完全にも、C# 7/Visual Basic 15 タプル`struct`組。

[!code-fsharp[Tuples](../../samples/snippets/fsharp/tour.fs#L205-L218)]

ため、注意することが重要`struct`タプルが値型、タプルを参照する暗黙的に変換することはできませんまたはその逆です。  参照と構造体のタプルの間で明示的に変換する必要があります。

## <a name="pipelines-and-composition"></a>パイプラインと合成

などの演算子をパイプ`|>`F# でのデータを処理するときに広く使用されます。 これらの演算子は、柔軟な方法で関数の「パイプライン」を確立するための関数です。 次の例では、方法を利用する機能の単純なパイプラインを構築するこれらの演算子の説明します。

[!code-fsharp[Pipelines](../../samples/snippets/fsharp/tour.fs#L227-L282)]

行われる前のサンプルの F# では、リスト処理関数をファーストクラスの関数を含む多くの機能の使用と[部分適用](language-reference/functions/index.md#partial-application-of-arguments)します。 これらの概念のそれぞれの深い理解がやや高度なことができますになる、する必要がありますがクリア関数を使用してパイプラインを構築するときにデータを処理する方法を簡単にします。

## <a name="lists-arrays-and-sequences"></a>リスト、配列、およびシーケンス

リスト、配列、およびシーケンスは、F# コア ライブラリの次の 3 つのプライマリ コレクション型です。

[一覧表示](language-reference/lists.md)は同じ型の要素の順序付けられた、変更できないコレクションです。  シングル リンク リスト、つまり、大規模な場合、列挙がランダム アクセスと連結するにはあまり適して本来は。  これは通常のリストを表すシングル リンク リストを使用しないでください、人気のある他の言語のリストとは対照的です。

[!code-fsharp[Lists](../../samples/snippets/fsharp/tour.fs#L309-L359)]

[配列](language-reference/arrays.md)が固定サイズ*変更可能な*同じ型の要素のコレクション。  要素の高速なランダム アクセスをサポートし、F# リストのメモリ ブロックが連続するだけであるためよりも高速化されます。

[!code-fsharp[Arrays](../../samples/snippets/fsharp/tour.fs#L368-L407)]

[シーケンス](language-reference/sequences.md)は論理的な一連の同じ型のすべての要素。  これらは、リストと配列を論理的な一連の要素に、"view"をすることのできるより一般的な型です。  これらも目立つことができるので***遅延***、つまり、必要な場合にのみ要素を計算することができます。

[!code-fsharp[Sequences](../../samples/snippets/fsharp/tour.fs#L418-L452)]

## <a name="recursive-functions"></a>再帰関数

コレクションまたは要素のシーケンス処理で通常実行[再帰](language-reference/functions/index.md#recursive-functions)F# でします。  F#サポートが for ループおよび命令型プログラミングでは、再帰をお勧めの正確性を保証するために簡単だからです。

> [!NOTE]
> 次の例を使用してパターン マッチングの利用、`match`式。  この基本的な構成要素はこの記事の後半で説明します。

[!code-fsharp[RecursiveFunctions](../../samples/snippets/fsharp/tour.fs#L461-L500)]

F#これは、ループ コンストラクトと同じ速度ように再帰呼び出しを最適化する方法、末尾呼び出し最適化を完全にサポートがあります。

## <a name="record-and-discriminated-union-types"></a>レコードと判別された共用体型

レコード、共用体の型は、F# コードで使用される 2 つの基本的なデータ型を一般に、F# プログラムでデータを表現する最善の方法は。  これにより、そのクラスのような他の言語は、構造的等値セマンティクスを備えることの主な違いの 1 つです。  つまり、「ネイティブ」の比較が等しいかどうかは簡単です - チェックのいずれかが、他と等しいかどうかだけです。

[レコード](language-reference/records.md)は省略可能なメンバー (メソッドなど) と、名前付きの値の集計。  C# または Java に詳しい場合は、し、これらように思われる Poco または Pojo - と同様に構造的等値と式だけです。

[!code-fsharp[Records](../../samples/snippets/fsharp/tour.fs#L507-L559)]

F# 4.1、レコードとしても表現できます`struct`秒。  これは、`[<Struct>]`属性。

[!code-fsharp[Records](../../samples/snippets/fsharp/tour.fs#L561-L568)]

[判別共用体 (Du)](language-reference/discriminated-unions.md)は値の名前付きのフォームまたはケースの数である可能性があります。  型に格納されたデータには、いくつかの個別の値のいずれかを指定できます。

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L575-L631)]

Du として使用することもできます。*単一ケースの判別共用体*、ドメイン モデリングのプリミティブ型を支援します。  多くの場合、文字列およびその他のプリミティブ型を表すもの、使用されはそのため、特定の意味が与えられます。  ただし、データのプリミティブの表現のみを使用しては、誤って正しくない値を割り当てることになることができます!  個別の単一ケース共用体として情報の各型を表すと、このシナリオでは正確性を適用できます。

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L633-L654)]

単一ケース判別された共用体、基になる値を取得する、上記のサンプルに示すように明示的に unwrap する必要があります。

また、Du もサポート再帰的な定義では、ツリーと本質的に再帰型データを簡単に記述することができます。  たとえば、ここではどのでバイナリ検索ツリーを表すことができます`exists`と`insert`関数。

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L656-L683)]

Du するデータ型にツリーを再帰的な構造を表すため、この再帰構造で動作しているは簡単で、正確性が保証されます。  次に示すパターン マッチングでもサポートされます。

さらに、として Du を表すことができます`struct`を`[<Struct>]`属性。

[!code-fsharp[Unions](../../samples/snippets/fsharp/tour.fs#L685-L696)]

ただし、その際に留意する 2 つの重要事項があります。

1. DU 構造体は、再帰的に定義することはできません。
2. DU 構造体には、そのケースのそれぞれに一意の名前が必要です。

上記に従わないは、コンパイル エラーになります。

## <a name="pattern-matching"></a>パターン マッチ

[パターン照合](language-reference/pattern-matching.md)により、F# の型に対する操作のための正確性が F# 言語機能です。  上記のサンプルのことに気付いたのかなり`match x with ...`構文。  このコンス トラクターにより、コンパイラを強制すると、パターンの完全一致として呼ばれるものを通じて、データ型を使用する場合は、すべての可能なケースのアカウントに、データ型の「形状」を理解することができます。  これは正しいかどうか、非常に強力な巧妙にどのようなコンパイル時にランタイムの問題は、通常「リフト」使用できます。

[!code-fsharp[PatternMatching](../../samples/snippets/fsharp/tour.fs#L705-L742)]

使用は、何かお気付き、`_`パターン。  これと呼ばれますが、[ワイルドカード パターン](language-reference/pattern-matching.md#wildcard-pattern)、「気にしません何かが」と答えるのですが。  、便利ですが誤ってバイパス徹底的なパターンに一致して不要になったコンパイル時の実施メリットを使用して注意が必要ない場合は`_`します。  分解された型の特定の情報が必要ない場合に最適な使用パターン マッチ式内のすべての意味のあるケースを列挙するときと一致する、または最後の句のパターンします。

[アクティブ パターン](language-reference/active-patterns.md)はパターン マッチングで使用する別の強力なコンストラクトです。  それらの分解パターン一致の呼び出しサイトでカスタムのフォームに入力データをパーティション化できます。  これらもパラメーター化できる、ため関数として、パーティションを定義することができます。  アクティブ パターンをサポートするために、前の例を展開するようになります。

[!code-fsharp[ActivePatterns](../../samples/snippets/fsharp/tour.fs#L764-L786)]

## <a name="optional-types"></a>省略可能な型

判別共用体の型の 1 つの特殊なケースは非常に役立つ、F# コア ライブラリの一部であるあるオプションの種類です。

[オプションの種類](language-reference/options.md)は 2 つのケースのいずれかを表す型です: 値、またはまったくありません。  値が場合がありますか、特定の操作からならない可能性がありますのシナリオで使用されます。  どちらの場合も、ランタイムの問題ではなく、コンパイル時の問題のためのアカウントに、必然です。  Api でよく使用されます、`null`を代わりに、"nothing"を表す使用について心配する必要がなくなります`NullReferenceException`多くの場合。

[!code-fsharp[Options](../../samples/snippets/fsharp/tour.fs#L789-L814)]

## <a name="units-of-measure"></a>測定単位

F# の型システムの固有の機能を 1 つの単位を数値リテラルのコンテキストを提供する機能があります。

[測定単位](language-reference/units-of-measure.md)を使用すると、メートル単位などの単位に数値の種類の関連付けが関数を実行したり作業数値リテラルではなく、単位。  これにより、コンパイラに渡された数値リテラルの型によって、特定のコンテキストで意味が、これにより、ランタイム エラー、その種の作業に関連付けられていることを確認できます。

[!code-fsharp[UnitsOfMeasure](../../samples/snippets/fsharp/tour.fs#L817-L842)]

F#コア ライブラリは、多くの SI 単位の種類および単位の変換を定義します。  詳細についてにチェック アウト、 [Microsoft.FSharp.Data.UnitSystems.SI Namespace](https://msdn.microsoft.com/visualfsharpdocs/conceptual/microsoft.fsharp.data.unitsystems.si-namespace-%5bfsharp%5d)します。

## <a name="classes-and-interfaces"></a>クラスとインターフェイス

F#.NET のクラスの完全なサポートがあります[インターフェイス](language-reference/interfaces.md)、[抽象クラス](language-reference/abstract-classes.md)、[継承](language-reference/inheritance.md)など。

[クラス](language-reference/classes.md)は、.NET オブジェクトを表す型がプロパティ、メソッド、およびイベントであることができます、[メンバー](language-reference/members/index.md)します。

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L845-L880)]

ジェネリック クラスの定義も非常に簡単です。

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L883-L908)]

インターフェイスを実装する、いずれかを使用できる`interface ... with`構文または[オブジェクト式](language-reference/object-expressions.md)します。

[!code-fsharp[Classes](../../samples/snippets/fsharp/tour.fs#L911-L934)]

## <a name="which-types-to-use"></a>使用する型

クラス、レコード、判別共用体、およびタプルの存在が重要な質問につながります。 使用すべきでしょうか。  ほとんどライフで、すべてのように、答えは、状況によって異なります。

タプルは、関数から複数の値を返すおよびアドホック集計値の集計を使用して、自体の値として適しています。

レコードは、"からのステップ アップ"組、ラベルと省略可能なメンバーのサポートということです。  データ転送中のプログラムを儀礼的表現に適しています。  構造の等値があるため比較で簡単に使用されます。

判別共用体は数多くの用途がコア特典がアカウントのすべての可能な「図形」ことができるデータに一致するパターンと組み合わせて利用するため可能になります。  

クラスは、情報を表すしても機能するには、その情報を関連付ける必要がある場合などの理由の数が膨大に適しています。  ルールの一般的に、概念的には、一部のデータに関連する機能がある場合は、大きな利点にはクラスとオブジェクト指向プログラミングの原則を使用してます。  クラスも優先されるデータ型 c# と Visual Basic での相互運用するときにこれらの言語では、ほぼすべてのクラスを使用します。

## <a name="next-steps"></a>次の手順

言語の主な機能のいくつかを確認したらには、最初の F# プログラムを作成できるようにする必要があります。  チェック アウト[Getting Started](tutorials/getting-started/index.md)に開発環境を設定して、コードを記述する方法について説明します。

詳細は次の手順は任意できますが、お勧めします[で関数型プログラミングの概要F#](introduction-to-functional-programming/index.md)コア関数型プログラミングの概念に慣れるにします。  これらは、F# で堅牢なアプリケーションの構築に不可欠になります。

また、チェック アウト、 [F# 言語リファレンス](language-reference/index.md)を F# の概念的なコンテンツの包括的なコレクションを参照してください。
