---
title: ステートメント
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], declaring
- colons (:) [Visual Basic]
- constants [Visual Basic], defining
- underlines
- constants [Visual Basic], statements
- blue underline [Visual Basic]
- procedures [Visual Basic], statements
- variables [Visual Basic], assigning
- line breaks [Visual Basic], in code
- executable statements [Visual Basic]
- variables [Visual Basic], defining
- statements [Visual Basic], about statements
ms.assetid: fcfdee1a-82b7-4846-98f7-9ca3f5160089
ms.openlocfilehash: f63f0f0212913f95baab2a8a43c4b7f25a859cd9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401467"
---
# <a name="statements-in-visual-basic"></a>Visual Basic におけるステートメント

Visual Basic のステートメントは、完全な命令です。 キーワード、演算子、変数、定数、および式を含めることができます。 各ステートメントは、次のカテゴリのいずれかに属します。

- **宣言ステートメント**変数、定数、またはプロシージャの名前を指定し、データ型を指定することもできます。

- **実行可能ステートメント**: アクションを開始します。 これらのステートメントは、メソッドまたは関数を呼び出し、コードブロックをループまたは分岐できます。 実行可能ステートメントには、変数または定数に値または式を代入する**代入ステートメント**が含まれます。

このトピックでは、各カテゴリについて説明します。 また、このトピックでは、複数のステートメントを 1 行に結合する方法と、複数行にわたってステートメントを継続する方法についても説明します。

## <a name="declaration-statements"></a>宣言ステートメント

宣言ステートメントを使用して、プロシージャ、変数、プロパティ、配列、および定数に名前を付け、定義します。 プログラミング要素を宣言する場合は、そのデータ型、アクセス レベル、およびスコープを定義することもできます。 詳細については、「[宣言された要素の特性](./declared-elements/declared-element-characteristics.md)」を参照してください。

次の例には、3 つの宣言が含まれています。

[!code-vb[VbVbalrStatements#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#80)]

最初の宣言はステートメント`Sub`です。 一致する`End Sub`ステートメントと共に、 という名前`applyFormat`のプロシージャを宣言します。 また、これを`Public`参照`applyFormat`できるコードは、それを呼び出すことができることを意味します。

2 番目の`Const`宣言は、`limit``Integer`定数 を宣言するステートメントで、データ型と値 33 を指定します。

3 番目の`Dim`宣言は、変数`thisWidget`を宣言するステートメントです。 データ型は特定のオブジェクト、つまりクラスから作成されたオブジェクトです`Widget`。 変数は、任意の基本データ型、または使用しているアプリケーションで公開される任意のオブジェクト型として宣言できます。

### <a name="initial-values"></a>初期値

宣言ステートメントを含むコードを実行すると、宣言された要素に必要なメモリが確保されます。 要素に値が格納されている場合、Visual Basic では、その値がデータ型の既定値に初期化されます。 詳細については[、Dim ステートメント](../../language-reference/statements/dim-statement.md)の「動作」を参照してください。

次の例に示すように、初期値を宣言の一部として変数に割り当てることができます。

[!code-vb[VbVbalrStatements#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#81)]

変数がオブジェクト変数の場合、次の例に示すように[、New Operator](../../../visual-basic/language-reference/operators/new-operator.md)キーワードを使用して宣言するときに、そのクラスのインスタンスを明示的に作成できます。

[!code-vb[VbVbalrStatements#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#82)]

宣言ステートメントで指定した初期値は、実行がその宣言ステートメントに達するまで変数に割り当てられません。 その時点まで、変数にはデータ型の既定値が含まれます。

## <a name="executable-statements"></a>実行可能ステートメント

実行可能ステートメントは、アクションを実行します。 プロシージャを呼び出したり、コード内の別の場所に分岐したり、複数のステートメントをループ処理したり、式を評価したりできます。 代入ステートメントは、実行可能ステートメントの特殊なケースです。

次の例では、`If...Then...Else`制御構造を使用して、変数の値に基づいてさまざまなコード ブロックを実行します。 各コード ブロック内では、`For...Next`ループは指定された回数だけ実行されます。

[!code-vb[VbVbalrStatements#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#83)]

前`If`の例のステートメントは、パラメーター`clockwise`の値をチェックします。 値が の`True`場合は、`spinClockwise`のメソッド`aWidget`を呼び出します。 値が の`False`場合は、`spinCounterClockwise`のメソッド`aWidget`を呼び出します。 制御`If...Then...Else`構造の最後は`End If`で終わります。

各`For...Next`ブロック内のループは、パラメータの値と同じ回数だけ適切なメソッドを`revolutions`呼び出します。

## <a name="assignment-statements"></a>割り当てステートメント

代入ステートメントは代入演算子を実行しますが、これは代入演算子 (`=`) の右側の値を取得し、それを左の要素に格納します。

[!code-vb[VbVbalrStatements#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#73)]

前の例では、代入ステートメントはリテラル値 42 を変数`v`に格納します。

### <a name="eligible-programming-elements"></a>適格なプログラミング要素

代入演算子の左側にあるプログラミング要素は、値を受け入れて格納できる必要があります。 つまり、変数またはプロパティは[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)ではないか、配列要素である必要があります。 代入ステートメントのコンテキストでは、このような要素は"left *value" の左辺値*と呼ばれることがあります。

代入演算子の右側の値は、リテラル、定数、変数、プロパティ、配列要素、その他の式、または関数呼び出しの任意の組み合わせで構成される式によって生成されます。 次の例を使って説明します。

[!code-vb[VbVbalrStatements#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#74)]

前の例では、変数に保持されている値`y`を変数`z`に保持されている値に追加し、関数`findResult`の呼び出しによって返される値を加算します。 この式の合計値は、 variable`x`に格納されます。

### <a name="data-types-in-assignment-statements"></a>代入ステートメントのデータ型

次の例に示すように、代入演算子は数値に`String`加えて値を割り当てることもできます。

[!code-vb[VbVbalrStatements#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#75)]

次の例に`Boolean`示すように、リテラルまたは`Boolean`式を`Boolean`使用して値を割り当てることもできます。

[!code-vb[VbVbalrStatements#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#76)]

同様に、 、`Char``Date`または`Object`データ型のプログラミング要素に適切な値を割り当てることができます。 また、オブジェクトインスタンスを、そのインスタンスの作成元クラスとして宣言された要素に割り当てることもできます。

### <a name="compound-assignment-statements"></a>複合割当ステートメント

*複合代入ステートメント*は、プログラミング要素に代入する前に、式に対して演算を実行します。 次の例は、`+=`演算子の左側の変数の値を右側の式の値だけインクリメントする、これらの演算子の 1 つを示しています。

[!code-vb[VbVbalrStatements#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#77)]

上の例では、 の値`n`に 1 を加算し、その新`n`しい値を に格納します。 これは、次のステートメントと同等の速記です。

[!code-vb[VbVbalrStatements#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#78)]

このタイプの演算子を使用して、さまざまな複合代入演算を実行できます。 これらの演算子の一覧と、演算子の詳細については、「[代入演算子](../../../visual-basic/language-reference/operators/assignment-operators.md)」を参照してください。

次の例に示すように、`&=`連結代入演算子 ( ) は、既存の文字列の末尾に文字列を追加する場合に便利です。

[!code-vb[VbVbalrStatements#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#79)]

### <a name="type-conversions-in-assignment-statements"></a>代入ステートメントでの型変換

変数、プロパティ、または配列要素に代入する値は、その代入先要素に適したデータ型である必要があります。 一般に、変換先要素と同じデータ型の値を生成する必要があります。 ただし、代入時に他の型に変換できる型もあります。

データ型間の変換については、「 [Visual Basic での型変換](./data-types/type-conversions.md)」を参照してください。 簡単に言うと、Visual Basic では、指定した型の値が、その値を拡大する他の任意の型に自動的に変換されます。 *拡大変換*は、実行時に常に成功し、データを失わない変換です。 たとえば、Visual Basic では、`Integer`値が`Double`適切な`Integer`場合に変換`Double`されます。 詳細については、「 [Widening and Narrowing Conversions](./data-types/widening-and-narrowing-conversions.md)」を参照してください。

*縮小変換*(拡大しない変換) は、実行時に失敗したり、データが失われるリスクを負ったりします。 型変換関数を使用して明示的に縮小変換を実行するか、または を設定してすべての変換を暗黙的に実行するようにコンパイラに指示`Option Strict Off`することができます。 詳細については、「[暗黙的および明示的な変換](./data-types/implicit-and-explicit-conversions.md)」を参照してください。

## <a name="putting-multiple-statements-on-one-line"></a>複数のステートメントを 1 行に配置する

コロン (`:`) 文字で区切られた 1 行に複数のステートメントを指定できます。 次の例を使って説明します。

[!code-vb[VbVbalrStatements#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#70)]

この形式の構文は便利ですが、コードの読み取りや保守が困難になります。 したがって、1 つのステートメントを 1 行に保持することをお勧めします。

## <a name="continuing-a-statement-over-multiple-lines"></a>複数行にわたるステートメントの継続

ステートメントは通常 1 行に収まりますが、長すぎる場合は、行`_`連結シーケンスを使用して次の行に続けることができます。 次の例では、`MsgBox`実行可能ステートメントは 2 行にわたって続きます。

[!code-vb[VbVbalrStatements#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#71)]

### <a name="implicit-line-continuation"></a>暗黙の行継続

多くの場合、アンダースコア文字 ( )`_`を使用せずに、次の連続する行でステートメントを続けることができます。 次の構文要素は、次のコード行でステートメントを暗黙的に続行します。

- コンマの後`,`( ) を指定します。 次に例を示します。

   [!code-vb[VbVbalrLineContinuation#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#1)]

- 左括弧 (`(`) の後、 または閉`)`じかっこ ( ) の前に表示されます。 次に例を示します。

   [!code-vb[VbVbalrLineContinuation#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#2)]

- 中かっこ (`{`) の後、または右中かっこ (`}`) の前に表示します。 次に例を示します。

    [!code-vb[VbVbalrLineContinuation#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#3)]

    詳細については、「[オブジェクト初期化子 : 名前付き型および匿名型](./objects-and-classes/object-initializers-named-and-anonymous-types.md)または[コレクション初期化子](./collection-initializers/index.md)」を参照してください。

- オープンな埋め込み`<%=`式 ( ) の後、または`%>`XML リテラル内の埋め込み式 ( ) の終了前。 次に例を示します。

   [!code-vb[VbVbalrLineContinuation#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#4)]

   詳細については[、「XML での埋め込み式](./xml/embedded-expressions-in-xml.md)」を参照してください。

- 連結演算子 ( )`&`の後に 次に例を示します。

   [!code-vb[VbVbcnConventions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/vb/Class1.vb#9)]

   詳細については、「[機能別に表示される演算子](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)」を参照してください。

- 代入演算子 (`=` `&=`, `:=` `+=`, `-=` `*=`, `/=` `\=`, `^=` `<<=`, `>>=`, , , , , , , , , , , , , )。 次に例を示します。

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   詳細については、「[機能別に表示される演算子](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)」を参照してください。

- 式の中の`+`二`-`項`/`演算子`*` `Mod`( `<>` `<`, `>` `<=`, `>=` `^` `>>` `<<` `Like` `Xor`, , , , , , , , , , , , , , , , , , ) を実行します。 `And` `AndAlso` `Or` `OrElse` 次に例を示します。

   [!code-vb[VbVbalrLineContinuation#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#7)]

   詳細については、「[機能別に表示される演算子](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)」を参照してください。

- 演算子と`Is``IsNot`演算子の後。 次に例を示します。

   [!code-vb[VbVbalrLineContinuation#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#8)]

   詳細については、「[機能別に表示される演算子](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)」を参照してください。

- メンバー修飾子文字 (`.`) の後、およびメンバー名の前。 次に例を示します。

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   ただし、`With`ステートメントを使用する場合、または型の`_`初期化リストに値を指定する場合は、メンバー修飾子文字の後に行連結文字 ( ) を含める必要があります。 ステートメントまたはオブジェクト初期化リストを使用`=``With`している場合は、代入演算子 (例えば) の後の行を改行することを検討してください。 次に例を示します。

   [!code-vb[VbVbalrLineContinuation#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#14)]

   詳細については[、「.」を参照してください。ステートメント](../../../visual-basic/language-reference/statements/with-end-with-statement.md)または[オブジェクト初期化子で終わる: 名前付き型と匿名型](./objects-and-classes/object-initializers-named-and-anonymous-types.md)。

- XML 軸プロパティの修飾子`.`( `.@` `...`または ) の後に指定します。 ただし、キーワードを使用する場合は、メンバー修飾子`_`を指定する場合は、 行連結文字 ( `With` ) を含める必要があります。 次に例を示します。

   [!code-vb[VbVbalrLineContinuation#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#9)]

   詳細については、「 [XML 軸のプロパティ 」](../../../visual-basic/language-reference/xml-axis/index.md)を参照してください。

- 属性を指定した場合、非参照 (<) より小さい符号`>`の後、またはより大きい記号 ( ) の前。 属性を指定する場合も、より`>`大きな符号 ( ) の後に指定します。 ただし、アセンブリ レベルまたはモジュール レベルの属性`_`を指定する場合は、行連結文字 ( ) を含める必要があります。 次に例を示します。

   [!code-vb[VbVbalrLineContinuation#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#10)]

   詳細については、「属性の[概要](../../../visual-basic/programming-guide/concepts/attributes/index.md)」を参照してください。

- 前後のクエリ演算子 (`Aggregate` `Distinct`, `From` `Group By`, `Group Join` `Join`, `Let` `Order By` `Select` `Skip` `Skip While` `Take` `Take While` `Descending`, , , , , , , , , , , , , , , , ) 。 `Where` `In` `Into` `On` `Ascending` 複数のキーワード`Order By`( 、 、、、、、、、、 `Group Join` `Take While`) で構成されるクエリ演算子の`Skip While`キーワードの間に線を引くことはできません。 次に例を示します。

   [!code-vb[VbVbalrLineContinuation#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#11)]

   詳細については、「[クエリ](../../../visual-basic/language-reference/queries/index.md)」を参照してください。

- ステートメント内`In`のキーワードの`For Each`後。 次に例を示します。

   [!code-vb[VbVbalrLineContinuation#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#12)]

   詳細については、[For Each...Next ステートメント](../../../visual-basic/language-reference/statements/for-each-next-statement.md) を参照してください。

- コレクション初期化`From`子のキーワードの後。 次に例を示します。

   [!code-vb[VbVbalrLineContinuation#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#13)]

   詳細については、「[コレクション初期化子](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)」を参照してください。

## <a name="adding-comments"></a>コメントの追加

ソースコードは、それを書いたプログラマーにとっても、必ずしも自明ではありません。 そのため、コードを文書化するために、ほとんどのプログラマは埋め込みコメントを自由に使用しています。 コード内のコメントは、後で読んだり作業したりする人に対して、プロシージャや特定の命令を説明できます。 Visual Basic では、コンパイル時にコメントは無視され、コンパイルされたコードには影響しません。

コメント行はアポストロフィ (`'`)`REM`で始まるか、またはスペースで始まります。 文字列内を除くコード内の任意の場所に追加できます。 ステートメントにコメントを追加するには、アポストロフィまたは`REM`ステートメントの後ろにコメントを挿入します。 コメントは、独自の行に行うこともできます。 次の例では、これらの可能性を示します。

[!code-vb[VbVbalrStatements#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#72)]

## <a name="checking-compilation-errors"></a>コンパイル エラーの確認

コード行を入力した後、その行に青い波線が表示される場合 (エラー メッセージも表示される場合があります)、ステートメントに構文エラーが表示されます。 ステートメントの問題を調べるには(タスクリストを見るか、マウスポインタでエラーをポイントしてエラーメッセージを読む)、それを修正する必要があります。 コード内のすべての構文エラーを修正するまで、プログラムは正しくコンパイルできません。

## <a name="related-sections"></a>関連項目

|期間|定義|
|---|---|
|[代入演算子](../../../visual-basic/language-reference/operators/assignment-operators.md)|などの代入演算子`=``*=`を含む言語リファレンス ページへのリンクを`&=`提供します。|
|[演算子および式](./operators-and-expressions/index.md)|要素と演算子を組み合わせて新しい値を生成する方法を示します。|
|[方法 : コード内でステートメントを分割および連結する](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)|1 つのステートメントを複数の行に分割する方法と、複数のステートメントを同じ行に配置する方法を示します。|
|[方法 : ステートメントへのラベル付け](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)|コード行にラベルを付ける方法を示します。|
