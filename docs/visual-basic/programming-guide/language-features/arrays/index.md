---
title: Visual Basic における配列
ms.date: 12/06/2017
f1_keywords:
- vb.Array
helpviewer_keywords:
- arrays [Visual Basic]
- Visual Basic, arrays
ms.assetid: dbf29737-b589-4443-bee6-a27588d9c67e
ms.openlocfilehash: 6b131d073e10f99feaf770fe5fd3c393551fa5a3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61907175"
---
# <a name="arrays-in-visual-basic"></a>Visual Basic における配列

配列と呼ばれるものの値のセットは、*要素*、互いに論理的に関連します。 たとえば、配列が学校; の各学年の生徒の数の構成可能性があります。配列の各要素は、1 つ学年の生徒の数です。 同様に、配列が、クラスの学生の成績のあります。配列の各要素は、1 つのレベルです。

各データ項目を格納する個々 の変数を可能になります。 たとえば場合は、アプリケーションは、学生の成績を分析し別個の変数の各生徒の成績など、使用できる`englishGrade1`、`englishGrade2`など。このアプローチでは、次の 3 つの主要な制限があります。

- デザイン時に認識する成績の数だけ処理する必要があります。
- 多数の成績を迅速に処理することは、扱いにくくなります。 さらをアプリケーションに重大なバグがある可能性が高くなります。
- 保守が困難になります。 新しい各学年を追加するには、こと、アプリケーション変更、再コンパイル、および再デプロイが必要です。

配列を使用すると、同じ名前で、これらの関連する値を参照してくださいし、呼び出される番号を使用して、*インデックス*または*添字*配列内の位置に基づいて個々 の要素を識別します。 配列内の要素の合計数より 1 小さい値を 0 から配列の範囲のインデックス。 Visual Basic 構文を使用して、配列のサイズを定義する、配列内の要素の合計数ではない、その最も大きいインデックスを指定します。 単位として配列を使用して、その要素を反復処理する機能を正確にデザイン時に含まれる数の要素を把握しなくてを解放します。 します。

説明する前に、簡単な例をいくつか紹介します。

```vb
' Declare a single-dimension array of 5 numbers.
Dim numbers(4) As Integer

'Declare a single-dimension array and set its 4 values.
Dim numbers = New Integer() {1, 2, 4, 8}

' Change the size of an existing array to 16 elements and retain the current values.
ReDim Preserve numbers(15)

' Redefine the size of an existing array and reset the values.
ReDim numbers(15)

' Declare a 6 x 6 multidimensional array.
Dim matrix(5, 5) As Double

' Declare a 4 x 3 multidimensional array and set array element values.
Dim matrix = New Integer(3, 2) {{1, 2, 3}, {2, 3, 4}, {3, 4, 5}, {4, 5, 6}}

' Declare a jagged array
Dim sales()() As Double = New Double(11)() {}
```

## <a name="array-elements-in-a-simple-array"></a>単純な配列の配列要素

という名前の配列を作成しましょう`students`学校の各学年の生徒の数を格納します。 要素のインデックスの範囲は 0 から 6 までです。 この配列の使用は、7 つの変数を宣言するよりも簡単です。

次の図は、`students`配列。 配列の各要素は、次のとおりです。

- 要素のインデックスは、学年を表します (インデックス 0 は幼稚園を表します)。

- 要素に含まれている値は、その学年の生徒の数を表します。

![生徒数の配列を示す図](./media/index/students-array-elements.gif)

次の例には、作成し、配列を使用して Visual Basic のコードが含まれています。

[!code-vb[simple-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/simple-array.vb)]

この例は次の 3 つを行います。

- 宣言を`students`7 つの要素の配列。 数`6`配列の宣言が配列の最後のインデックスを示します。 これは、1 つは、配列内の要素の数よりも小さい。
- 配列内の各要素に値を割り当てます。 配列名を使用して、かっこで囲まれた個々 の要素のインデックスを含む要素にアクセスします。
- 配列の各値が一覧表示します。 この例では、 [ `For` ](../../../language-reference/statements/for-next-statement.md)インデックス番号で、配列の各要素にアクセスするステートメント。

`students` 1 つのインデックスを使用しているために、上記の例では、配列は 1 次元配列。 1 つ以上のインデックスまたは添字を使用する配列と呼びます*多次元*します。 詳細については、この記事の残りの部分を参照してくださいと[Visual Basic で配列の次元](../../language-features/arrays/array-dimensions.md)します。

## <a name="creating-an-array"></a>配列の作成

いくつかの方法では、配列のサイズを定義できます。

- 配列が宣言されている場合は、サイズを指定できます。

  [!code-vb[creating1](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#1)]

- 使用することができます、`New`句が作成されたときに、配列のサイズを指定します。

  [!code-vb[creating2](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#2)]

使用してサイズを再定義できますを既存の配列がある場合、 [ `ReDim` ](../../../language-reference/statements/redim-statement.md)ステートメント。 指定することができます、`ReDim`ステートメントが、配列内にある値を保持または空の配列を作成することを指定することができます。 次に、 `ReDim` ステートメントを使用して既存の配列のサイズを変更する例をいくつか示します。

[!code-vb[redimensioning](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#3)]

詳細については、次を参照してください。、 [ReDim ステートメント](../../../language-reference/statements/redim-statement.md)します。

## <a name="storing-values-in-an-array"></a>配列内の値を格納します。

配列のそれぞれの位置には、 `Integer`型のインデックスを使用してアクセスできます。 かっこで囲まれたインデックスを使用して配列のそれぞれの位置を参照することで、配列の値を格納および取得することができます。 多次元配列のインデックスは、コンマ (,) で区切られます。 配列の次元ごとに 1 つのインデックスが必要です。

次の例では、配列の値を取得および保存されるいくつかのステートメントを示します。

[!code-vb[store-and-retrieve](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/store-and-retrieve.vb)]

## <a name="populating-an-array-with-array-literals"></a>配列リテラルの配列への取り込み

配列リテラルを使用すると、同時に作成する初期値のセットを含む配列を設定できます。 配列リテラルは、中かっこ (`{}`) で囲んだ値のコンマ区切りの一覧で構成されます。

配列リテラルを使用して配列を作成する場合、配列の型を指定するか、型の推定を使用して配列の型を決定することができます。 次の例では、両方のオプションを示します。

[!code-vb[create-with-literals](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#4)]

型の推定を使用する場合、配列の型はによって決まります、*優先型*リテラル値の一覧にします。 主要な型は、配列内の他のすべての型が拡大変換できる型です。 この一意の型を特定できない場合、最も優先度の高い型は、配列内の他のすべての型から縮小変換できる一意の型になります。 これらの一意の型をどちらも特定できない場合は、 `Object`が最も優先度の高い型になります。 たとえば、配列リテラルに指定された値の一覧に `Integer`型、 `Long`型、および `Double`型の値が含まれている場合、結果の配列の型は `Double`です。 `Integer`と`Long`にのみ拡大変換`Double`、`Double`は、主要な型です。 詳細については、「 [Widening and Narrowing Conversions](../../language-features/data-types/widening-and-narrowing-conversions.md)」を参照してください。

> [!NOTE]
> 型の推定は、型のメンバーのローカル変数として定義されている配列に対してのみ使用できます。 クラス レベルの配列リテラルで定義されている配列がの型は、明示的な型定義がない場合は、`Object[]`します。 詳細については、次を参照してください。[ローカル型推論](../variables/local-type-inference.md)します。

前の例を定義する注`values`型の配列として`Double`場合でも、すべての配列リテラルが型`Integer`します。 この配列を作成するには、配列リテラル内の値に拡大変換することができますので`Double`値。

作成してを使用して多次元配列を設定できる*配列リテラルを入れ子になった*します。 入れ子になった配列リテラルには、結果の配列で一貫性のあるディメンションの数が必要です。 次の例では、入れ子になった配列リテラルを使用して、整数の 2 次元配列を作成します。

[!code-vb[nested-array-literals](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#5)]

入れ子になった配列リテラルを使用して配列を作成し、入れ子になった配列リテラル内の要素の数が一致しない場合、エラーが発生します。 エラーは、配列リテラルより次元数が異なるが、配列変数を明示的に宣言する場合にも発生します。

1 次元配列にすることができますと同様、入れ子になった配列リテラルに多次元配列を作成するときに型の推定に依存することができます。 推定された型が、主要なすべての入れ子レベルのすべての配列リテラル内のすべての値の型です。 次の例は、2 次元配列の型を作成`Double[,]`型の値から`Integer`と`Double`します。

[!code-vb[nested-type-inference](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#6)]

その他の例では、次を参照してください。[方法。Visual Basic で配列変数を初期化](../../language-features/arrays/how-to-initialize-an-array-variable.md)します。

## <a name="iterating-through-an-array"></a>配列を反復処理します。

最大最小のインデックスとは、最上位から、配列内の各要素にアクセスする配列を反復処理するときに、最下位にします。 通常、いずれかを使用して、[をしています.次のステートメントの](../../../language-reference/statements/for-next-statement.md)または[ごとにしています.次のステートメントの](../../../language-reference/statements/for-each-next-statement.md)配列の要素を反復処理します。 呼び出すことができますが、配列の上限がわからないときに、<xref:System.Array.GetUpperBound%2A?displayProperty=nameWithType>インデックスの最大値を取得します。 最小のインデックス値がほぼ常に 0 を呼び出すことができます、<xref:System.Array.GetLowerBound%2A?displayProperty=nameWithType>インデックスの最小値を取得します。

次の例を使用して、1 次元配列を反復処理、 [ `For...Next` ](../../../language-reference/statements/for-next-statement.md)ステートメント。

[!code-vb[iterate-one-dimensional-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate1d.vb)]

次の例を使用して、多次元配列を反復処理を[ `For...Next` ](../../../language-reference/statements/for-next-statement.md)ステートメント。 <xref:System.Array.GetUpperBound%2A> メソッドには、次元を指定するパラメーターがあります。 `GetUpperBound(0)` 最初の次元の最も大きいインデックスを返しますと`GetUpperBound(1)`2 番目の次元の最も大きいインデックスを返します。

[!code-vb[iterate-two-dimensional-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate2d.vb)]

次の例では、[ごとにしています.次のステートメントの](../../../language-reference/statements/for-each-next-statement.md)1 次元配列と、2 次元配列を反復処理します。

[!code-vb[iterate-for-each-next](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate-for-each-next.vb)]

## <a name="array-size"></a>配列のサイズ

配列のサイズは、そのすべての次元の長さの積です。 これは、現在配列に含まれている要素の総数を表します。  たとえば、次の例は、各ディメンション内の 4 つの要素を持つ 2 次元配列を宣言します。 例の出力を示しています、配列のサイズは 16 ((3 + 1) または * (3 + 1)。

[!code-vb[array-size](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size.vb)]

> [!NOTE]
> 配列のサイズには、この説明は、ジャグ配列には適用されません。 ジャグ配列およびジャグ配列のサイズを判断する方法については、次を参照してください。、[ジャグ配列](#jagged-arrays)セクション。

配列のサイズは、<xref:System.Array.Length%2A?displayProperty=nameWithType> プロパティを使用して確認できます。 使用して多次元配列の各次元の長さを見つけることができます、<xref:System.Array.GetLength%2A?displayProperty=nameWithType>メソッド。

サイズを変更できる配列変数を新しい配列のオブジェクトを割り当てることで、またはを使用して、 [ `ReDim`ステートメント](../../../language-reference/statements/redim-statement.md)ステートメント。 次の例では、 `ReDim` 51 要素を配列に 100 要素の配列を変更するステートメント。

[!code-vb[resize-an-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size2.vb)]

配列のサイズを扱う際に考慮する必要がある点がいくつかあります。

|||
|---|---|
|次元の長さ|各次元のインデックスには 0 から上限の範囲、つまり 0 から始まります。 したがって、特定の次元の長さは、そのディメンションの宣言された上限よりも大きい値のいずれかです。|
|長さの制限|配列のすべての次元の長さの最大値に制限されて、`Integer`はデータ型は、<xref:System.Int32.MaxValue?displayProperty=nameWithType>または (2 ^31) - 1。 しかし、配列のサイズの総数も、システムで利用できるメモリによって制限されます。 使用可能なメモリの容量を超える配列を初期化しようとした場合は、ランタイム、<xref:System.OutOfMemoryException>します。|
|サイズおよび要素のサイズ|配列のサイズは、その要素のデータ型には依存しません。 サイズは、常にメモリ内で使用されるバイト数ではなく、要素の合計数を表します。|
|メモリの使用量|配列がどのようにメモリに格納されるかに関して、前提を置くことは安全ではありません。 ストレージは、プラットフォームのデータ幅が異なると変わります。したがって、同じ配列でも、32 ビットのシステムよりも 64 ビットのシステムの方が多くのメモリを使用します。 配列を初期化すると、システム構成に応じて、要素をできるだけ近くに集めるように、またはすべてがハードウェア自体の境界に合致するように、共通言語ランタイム (CLR: Common Language Runtime) によってストレージが割り当てられます。 また、配列は制御情報のためにストレージのオーバーヘッドを必要とします。このオーバーヘッドは、次元が追加されるごとに増加します。|

## <a name="the-array-type"></a>配列型

すべての配列が、データ型のことで、その要素のデータ型とは異なります。 すべての配列を包括する 1 つのデータ型はありません。 代わりに、配列のデータ型は、配列の次元数 ( *ランク*) と配列の要素のデータ型によって決まります。 のみがある場合に同じランクを入力し、その要素が同じデータ型を持つ 2 つの配列変数は、同じデータ。 配列の次元の長さは、配列のデータ型には影響しません。

すべての配列は、<xref:System.Array?displayProperty=nameWithType> クラスから継承しています。また、`Array` 型として変数を宣言できますが、`Array` 型の配列は作成できません。 たとえば、次のコードを宣言しますが、`arr`型の変数を`Array`を呼び出すと、<xref:System.Array.CreateInstance%2A?displayProperty=nameWithType>配列、配列の型をインスタンス化するメソッドは、object[] のことがわかった。

[!code-vb[array-class](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-class.vb)]

また、[ReDim ステートメント](../../../language-reference/statements/redim-statement.md) は、`Array` 型として宣言された変数上では使用できません。 これらの理由やタイプ セーフでは、特定の種類としてすべての配列を宣言することをお勧めします。

いくつかの方法で、配列またはその要素のいずれかのデータ型を知ることができます。

- 呼び出すことができます、<xref:System.Object.GetType%2A>メソッドを取得する変数を<xref:System.Type>変数の実行時の型を表すオブジェクト。 <xref:System.Type> オブジェクトでは、プロパティおよびメソッドに詳細情報が保持されます。
- 変数を渡すことができます、<xref:Microsoft.VisualBasic.Information.TypeName%2A>を取得する関数を`String`実行時の型の名前に置き換えます。

次の例では、両方は、`GetType`メソッドと`TypeName`配列の型を決定する関数。 配列型は`Byte(,)`します。 なお、<xref:System.Type.BaseType%2A?displayProperty=nameWithType>もプロパティでは、バイト配列の基本型があることを示します、<xref:System.Array>クラス。

[!code-vb[array-type](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/array-type.vb)]

## <a name="arrays-as-return-values-and-parameters"></a>戻り値およびパラメーターとしての配列

`Function` プロシージャから配列を返すには、[Function ステートメント](../../../language-reference/statements/function-statement.md)の戻り値の型として配列のデータ型と次元数を指定します。 関数内で、同じデータ型と次元数を持つローカルの配列変数を宣言します。 [Return ステートメント](../../../language-reference/statements/return-statement.md)には、かっこを使用せずにローカルの配列変数を含めます。

配列を `Sub` プロシージャまたは `Function` プロシージャのパラメーターとして指定するには、パラメーターを配列として定義して、データ型と次元数を指定します。 プロシージャの呼び出しでは、配列変数を同じデータ型と次元数を渡します。

次の例では、`GetNumbers`関数が返される、 `Integer()`、型の 1 次元配列`Integer`します。 `ShowNumbers` プロシージャは、 `Integer()` の引数を受け取ります。

[!code-vb[return-value-and-params](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params.vb)]

次の例では、`GetNumbersMultiDim`関数が返される、 `Integer(,)`、型の 2 次元配列`Integer`します。  `ShowNumbersMultiDim` プロシージャは、 `Integer(,)` の引数を受け取ります。

[!code-vb[multidimensional-return-value](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params-2d.vb)]

## <a name="jagged-arrays"></a>ジャグ配列

アプリケーションのデータ構造は、2 次元の配列であっても四角形の 2 次元配列ではない場合があります。 たとえば、月の毎日の最高気温のデータを格納するのに配列を使用可能性があります。 配列の最初の次元は、1 か月を表しますが、2 番目の次元は、日数を表すし、1 か月の日数は一様ではないです。 A*ジャグ配列*と呼ばれることも、*配列の配列*、このようなシナリオに適しています。 ジャグ配列は、配列要素も配列です。 ジャグ配列と、ジャグ配列の各要素は、1 次元でも多次元でもかまいません。

次の例では、数か月の各要素が日の配列の配列を使用します。 異なる月の日数の数が異なるため、ジャグ配列を使用します。  この例では、ジャグ配列を作成し、値を割り当てる、取得、およびその値を表示する方法を示します。

[!code-vb[jagged-arrays](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged.vb)]

前の例では、要素ごとの単位でのジャグ配列に値を割り当ててを使用して、`For...Next`ループします。 入れ子になった配列リテラルを使用してジャグ配列の要素に値を割り当てることもできます。 ただし、使用しようとすると、入れ子になった配列リテラル (たとえば、 `Dim valuesjagged = {{1, 2}, {2, 3, 4}}`) コンパイラ エラーが発生[BC30568](../../../,,/../misc/bc30568.md)します。 エラーを修正するには、内側の配列リテラルをかっこで囲みます。 かっこは、強制的に配列のリテラル式を評価して、次の例では、外側の配列リテラルには、結果として得られる値が使用されます。

[!code-vb[jagged-array-initialization](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-assign.vb)]

ジャグ配列は、配列の要素を格納する 1 次元配列です。 そのため、<xref:System.Array.Length%2A?displayProperty=nameWithType>プロパティおよび`Array.GetLength(0)`メソッドは、1 次元の配列要素の数を返すと`Array.GetLength(1)`がスローされます、<xref:System.IndexOutOfRangeException>ジャグ配列が多次元ではないためです。 各サブ配列の値を取得することによって各サブ配列の要素の数を決定する<xref:System.Array.Length%2A?displayProperty=nameWithType>プロパティ。 次の例では、ジャグ配列の要素の数を決定する方法を示します。

[!code-vb[jagged-array-size](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-length.vb)]

## <a name="zero-length-arrays"></a>長さ 0 の配列

Visual Basic は初期化されていない配列間で区別されます (値が配列`Nothing`) と*長さ 0 の配列*または空の配列 (配列の要素を持たない)。初期化されていない配列は、いずれかの次元がされていないまたは任意の値がそれに割り当てられます。 例:

```vb
Dim arr() As String
```

長さ 0 の配列は、-1 のディメンションと宣言されます。 例:

```vb
Dim arrZ(-1) As String
```

次のような場合に、長さ 0 の配列を作成する必要があります。

- リスクを負わず、<xref:System.NullReferenceException>例外、コードのメンバーにアクセスする必要があります、<xref:System.Array>クラスなど、<xref:System.Array.Length%2A>または<xref:System.Array.Rank%2A>、または Visual Basic の関数を呼び出す<xref:Microsoft.VisualBasic.Information.UBound%2A>します。

- 確認する必要がない単純なコードを保持する`Nothing`特殊なケースとして。

- コードで、長さ 0 の配列を 1 つ以上のプロシージャに渡す必要があるアプリケーション プログラミング インターフェイス (API: Application Programming Interface) とやり取りする場合、または API の 1 つ以上のプロシージャから長さ 0 の配列が返される場合。

## <a name="splitting-an-array"></a>配列の分割

場合によっては、複数の配列に 1 つの配列を分割する必要があります。 これには、配列が分割されるポイントを識別して、2 つ以上の個別の配列に配列を送信が含まれます。

> [!NOTE]
> このセクションでは、何らかの区切り記号に基づいて文字列配列に 1 つの文字列を分割は説明しません。 文字列の分割方法の詳細については、次を参照してください。、<xref:System.String.Split%2A?displayProperty=nameWithType>メソッド。

配列に分割するための最も一般的な条件は次のとおりです。

- 配列の要素数。 たとえば、数と等しい部分約を指定した要素数を超える配列に分割します。 このため、いずれかによって返される値を使用することができます、<xref:System.Array.Length%2A?displayProperty=nameWithType>または<xref:System.Array.GetLength%2A?displayProperty=nameWithType>メソッド。

- 配列の位置を示す区切り記号として機能する要素の値を分割する必要があります。 呼び出すことによって特定の値を検索することができます、<xref:System.Array.FindIndex%2A?displayProperty=nameWithType>と<xref:System.Array.FindLastIndex%2A?displayProperty=nameWithType>メソッド。

呼び出して個々 の配列を作成できますし、配列を分割する位置のインデックス、インデックスを特定した後、<xref:System.Array.Copy%2A?displayProperty=nameWithType>メソッド。

次の例では、配列がほぼ等しいサイズの 2 つの配列に分割します。 (配列の要素の合計数が奇数の場合は、最初の配列が 2 番目の要素が 1 つです。)

[!code-vb[splitting-an-array-by-length](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/split1.vb)]

次の例では、値は"zzz"配列の区切り記号として機能する要素の有無に基づいて 2 つの配列に文字列の配列を分割します。 新しい配列には、区切り記号を含む要素を含めないでください。

[!code-vb[splitting-an-array-by-delimiter](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/split2.vb)]

## <a name="joining-arrays"></a>配列への参加

1 つの大きな配列に、さまざまな配列を組み合わせることもできます。 これを行うには、使用することも、<xref:System.Array.Copy%2A?displayProperty=nameWithType>メソッド。

> [!NOTE]
> このセクションでは、1 つの文字列に文字列の配列を結合するには説明しません。 文字列の配列を結合する方法については、次を参照してください。、<xref:System.String.Join%2A?displayProperty=nameWithType>メソッド。

新しい配列に各配列の要素をコピーする前に、まず新しい配列を十分に格納されるよう、配列を初期化することを確認する必要があります。 2 つの方法のいずれかでこれを行うことができます。

- 使用して、 [ `ReDim Preserve` ](../../../language-reference/statements/redim-statement.md)ステートメントを動的に新しい要素を追加する前に、配列を展開します。 これは、最も簡単な方法では、大きな配列をコピーするときにパフォーマンスの低下と過剰なメモリ消費量で発生する可能性が。
- 新しいの大きな配列の必要な要素の合計数を計算し、各ソース配列の要素を追加します。

次の例では、1 つの配列に 10 個の要素を持つ 4 つの配列を追加するのに 2 番目のアプローチを使用します。

[!code-vb[joining-an-array](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/join.vb)]

ソース配列が小さすべてここでは、ため各新しい配列の要素を追加、配列を展開も動的にします。 次の例でこれを確認できます。

[!code-vb[joining-an-array-dynamically](~/samples/snippets/visualbasic/programming-guide/language-features/arrays/join2.vb)]

## <a name="collections-as-an-alternative-to-arrays"></a>配列の代わりとしてのコレクション

配列は、数が固定されている厳密に型指定されたオブジェクトの作成および処理に最も適しています。 コレクションは、オブジェクトのグループをより柔軟に処理できます。 使用して配列のサイズを明示的に変更することが必要する、配列とは異なり、 [ `ReDim`ステートメント](../../../language-reference/statements/redim-statement.md)コレクションの拡大し、アプリケーションの変更のニーズに合わせて動的に縮小します。

使用すると`ReDim`Visual Basic 配列のディメンションを変更する新しい配列を作成および 1 つ前を解放します。 これには、実行時間がかかります。 そのため、頻繁に変更するかを使用している項目の数が必要な項目の最大数を予測できない場合は、通常取得されますパフォーマンスを向上させるコレクションを使用しています。

コレクションによっては、コレクションに含まれるオブジェクトのキーを割り当てると、そのキーを使用してオブジェクトを迅速に取り出すことができます。

含まれる要素が 1 つのデータ型だけのコレクションの場合は、 <xref:System.Collections.Generic?displayProperty=nameWithType> 名前空間のクラスのいずれかを使用できます。 ジェネリック コレクションでは、タイプ セーフが強制されるため、他のデータ型を追加することはできません。

コレクションの詳細については、「[コレクション](../../concepts/collections.md)」を参照してください。

## <a name="related-topics"></a>関連トピック

|用語|定義|
|----------|----------------|
|[Array Dimensions in Visual Basic](../../language-features/arrays/array-dimensions.md)|配列のランクと次元について説明します。|
|[方法: Visual Basic で配列変数を初期化します。](../../language-features/arrays/how-to-initialize-an-array-variable.md)|配列に初期値を設定する方法について説明します。|
|[方法: Visual Basic で配列を並べ替える](../../language-features/arrays/how-to-sort-an-array.md)|配列の要素をアルファベット順に並べ替える方法について説明します。|
|[方法: 1 つの配列を別の配列に代入します。](../../language-features/arrays/how-to-assign-one-array-to-another-array.md)|配列を別の配列変数に代入するときの手順と規則を説明します。|
|[配列のトラブルシューティング](../../language-features/arrays/troubleshooting-arrays.md)|配列を使用しているときに発生する一般的な問題について説明します。|

## <a name="see-also"></a>関連項目

- <xref:System.Array?displayProperty=nameWithType>
- [Dim ステートメント](../../../language-reference/statements/dim-statement.md)
- [ReDim ステートメント](../../../language-reference/statements/redim-statement.md)
