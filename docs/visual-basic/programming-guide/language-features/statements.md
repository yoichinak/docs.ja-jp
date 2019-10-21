---
title: Visual Basic におけるステートメント
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
ms.openlocfilehash: e66acae5e98d561883f4ad59853dfd862c8ebfee
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946459"
---
# <a name="statements-in-visual-basic"></a>Visual Basic におけるステートメント

Visual Basic でのステートメントは、完全な命令です。 これは、キーワード、演算子、変数、定数、および式に含めることができます。 各ステートメントは、次のカテゴリのいずれかに属します。

- **宣言ステートメント**変数、定数、またはプロシージャの名前し、データ型を指定できます。

- **実行可能なステートメント**操作を開始します。 メソッドまたは関数の場合、これらのステートメントを呼び出すことができ、ループや分岐のコード ブロックすることができます。 実行可能ステートメントを含む**代入ステートメント**、変数または定数に値または式に代入します。

このトピックでは、各カテゴリについて説明します。 また、このトピックでは、1 行に複数のステートメントを結合する方法と複数行ステートメントを続行する方法について説明します。

## <a name="declaration-statements"></a>宣言ステートメント

宣言ステートメントを使用して名前を指定し、プロシージャ、変数、プロパティ、配列、および定数を定義します。 プログラミング要素を宣言するときに、そのデータ型、アクセス レベル、およびスコープも定義できます。 詳細については、次を参照してください。[宣言された要素の特性](./declared-elements/declared-element-characteristics.md)します。

次の例には、3 つの宣言が含まれています。

[!code-vb[VbVbalrStatements#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#80)]

最初の宣言は、`Sub`ステートメント。 その照合と共に`End Sub`という名前のプロシージャ宣言ステートメントでは、`applyFormat`します。 指定する`applyFormat`は`Public`、つまり、それを参照できる任意のコードで呼び出すことができます。

2 番目の宣言は、`Const`ステートメントでは、定数を宣言しますが、`limit`を指定して、`Integer`データ型と 33 の値。

3 番目の宣言は、`Dim`ステートメントでは、変数を宣言しますが、`thisWidget`します。 データ型は、特定のオブジェクト、つまりからオブジェクトが作成された、`Widget`クラス。 任意の基本データ型、または使用するアプリケーションで公開されているオブジェクトの種類の変数を宣言することができます。

### <a name="initial-values"></a>初期値

宣言ステートメントを含むコードを実行すると、Visual Basic は、宣言された要素に必要なメモリを予約します。 要素には、値が含まれる、Visual Basic により、データ型の既定値に初期化します。 詳細については、「動作」を参照してください[Dim ステートメント](../../language-reference/statements/dim-statement.md)します。

次の例に示すように、その宣言の一部として変数に初期値を割り当てることができます。

[!code-vb[VbVbalrStatements#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#81)]

使用して宣言するときに、明示的にそのクラスのインスタンスを作成する変数がオブジェクト変数の場合は、 [New 演算子](../../../visual-basic/language-reference/operators/new-operator.md)キーワードでは、次の例として示します。

[!code-vb[VbVbalrStatements#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#82)]

宣言ステートメントに達するまで、宣言ステートメントで指定した初期値が変数に代入しないことに注意してください。 それまでは、変数には、そのデータ型の既定値が含まれています。

## <a name="executable-statements"></a>実行可能なステートメント

実行可能なステートメントは、操作を実行します。 式を評価するプロシージャのコードでいくつかのステートメントをループ処理する別の場所に分岐を呼び出すこともできます。 代入ステートメントは、実行可能なステートメントの特殊なケースです。

次の例では、`If...Then...Else`変数の値に基づくコードの別のブロックを実行する構造を制御します。 各コード ブロック内で、`For...Next`ループの実行回数を指定します。

[!code-vb[VbVbalrStatements#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#83)]

`If`ステートメントは上記の例では、パラメーターの値を確認します。`clockwise`します。 値が場合`True`、呼び出し、`spinClockwise`メソッドの`aWidget`します。 値が場合`False`、呼び出し、`spinCounterClockwise`メソッドの`aWidget`します。 `If...Then...Else`制御構造が終わる`End If`します。

`For...Next`各ブロック内でループ メソッドを呼び出して適切な時間数の値と等しく、`revolutions`パラメーター。

## <a name="assignment-statements"></a>代入ステートメント

代入ステートメントは、代入演算子の右側にある値を取得するので構成されている、代入演算を実行 (`=`) 次の例のように、左の要素に格納することです。

[!code-vb[VbVbalrStatements#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#73)]

前の例では、代入ステートメントは、変数のリテラル値 42 を格納`v`します。

### <a name="eligible-programming-elements"></a>対象となるプログラミング要素

代入演算子の左側にあるプログラミング要素は、そのまま使用し、値を格納できる必要があります。 つまり、変数またはプロパティが必要があります[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)、または配列要素があります。 代入ステートメントのコンテキストでこのような要素とも呼ばれます、*左辺値*の「左辺値です」。

代入演算子の右側にある値は、リテラル、定数、変数、プロパティ、配列の要素、その他の式、または関数呼び出しの組み合わせで構成される、式によって生成されます。 次に例を示します。

[!code-vb[VbVbalrStatements#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#74)]

上記の例では、変数に保持された値を追加します。`y`変数に保持された値に`z`、し、関数の呼び出しによって返される値を追加`findResult`します。 この式の合計値が変数に格納し、`x`します。

### <a name="data-types-in-assignment-statements"></a>代入ステートメントでのデータ型

数値の値に加えて、代入演算子は割り当てることができますも`String`値は、次の例に示すようにします。

[!code-vb[VbVbalrStatements#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#75)]

割り当てることもできます`Boolean`値のいずれかを使用して、`Boolean`リテラルまたは`Boolean`式として次の例を示しています。

[!code-vb[VbVbalrStatements#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#76)]

同様のプログラミング要素に適切な値を割り当てることができます、 `Char`、 `Date`、または`Object`データ型。 そのインスタンスの作成元のクラスを指定して宣言された要素をオブジェクトのインスタンスを割り当てることもできます。

### <a name="compound-assignment-statements"></a>複合代入ステートメント

*複合代入ステートメント*最初プログラミング要素に割り当てる前に、式に対して操作を実行します。 次の例は、これらの演算子のいずれかを示しています`+=`右側の式の値によって、演算子の左側にある変数の値をインクリメントします。

[!code-vb[VbVbalrStatements#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#77)]

前の例の値に 1 を加算する`n`でその新しい値を格納して`n`します。 短縮形は、次のステートメントのと同じです。

[!code-vb[VbVbalrStatements#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#78)]

この種類の演算子を使用して、さまざまな複合代入演算を実行できます。 これらの演算子とその詳細情報の一覧は、次を参照してください。[代入演算子](../../../visual-basic/language-reference/operators/assignment-operators.md)します。

連結代入演算子 (`&=`) の既存の末尾に文字列を追加する場合に便利ですが、次の例に示すように、文字列します。

[!code-vb[VbVbalrStatements#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#79)]

### <a name="type-conversions-in-assignment-statements"></a>代入ステートメントでの型変換

変換先の要素に適切なデータ型の変数、プロパティ、または配列要素に割り当てる値がある必要があります。 一般に、目的の要素のと同じデータ型の値を生成しようとする必要があります。 ただし、一部の種類は、割り当ての際に他の型に変換できます。

データ型の間で変換する方法については、次を参照してください。 [Visual Basic における型変換](./data-types/type-conversions.md)します。 簡単に言うと Visual Basic は、他の型、拡大変換に指定された型の値を自動的に変換します。 A*拡大変換*は 1 つを常に実行時に成功すると、すべてのデータが失われない。 Visual Basic の変換など、`Integer`値を`Double`適切な場合、ため`Integer`に拡大変換されます`Double`します。 詳細については、[拡大変換と縮小変換](./data-types/widening-and-narrowing-conversions.md)に関するページを参照してください。

*縮小変換*(拡大変換がないもの) の実行時に、エラーまたはデータ損失のリスクを実行します。 縮小変換を明示的に実行するには、型変換関数を使用して、または暗黙的に設定してすべての変換を実行するコンパイラに指示できます`Option Strict Off`します。 詳細については、次を参照してください。[暗黙的および明示的な変換](./data-types/implicit-and-explicit-conversions.md)します。

## <a name="putting-multiple-statements-on-one-line"></a>1 つの行に複数のステートメントを配置します。

コロンで区切られた 1 行に複数のステートメントがあることができます (`:`) 文字。 次に例を示します。

[!code-vb[VbVbalrStatements#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#70)]

場合によっては便利な場合の構文は、この形式により、コード読み取りおよびメンテナンスが困難です。 そのため、行に 1 つのステートメントを維持することをお勧めします。

## <a name="continuing-a-statement-over-multiple-lines"></a>複数の行にまたがるステートメント

ステートメントは、通常は 1 つの行に収まるが長すぎるときに、スペースとアンダー スコア文字で構成される行連結シーケンスを使用して次の行に続けることができます (`_`) 後にキャリッジ リターン。 次の例では、`MsgBox`に 2 行の実行可能ステートメントが続きます。

[!code-vb[VbVbalrStatements#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#71)]

### <a name="implicit-line-continuation"></a>暗黙的な行継続

多くの場合、せずに続行できますステートメントを次の連続する行にアンダー スコア文字を使用して (`_`)。 次の構文要素は、次のコード行で暗黙的に、ステートメントを続行します。

- コンマの後に (`,`)。 例えば:

   [!code-vb[VbVbalrLineContinuation#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#1)]

- 始めかっこの後 (`(`) または閉じかっこの前に、(`)`)。 例えば:

   [!code-vb[VbVbalrLineContinuation#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#2)]

- かっこの後 (`{`) または右中かっこの前に (`}`)。 例:

    [!code-vb[VbVbalrLineContinuation#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#3)]

    詳細については、次を参照してください。[オブジェクト初期化子。名前付きの匿名型](./objects-and-classes/object-initializers-named-and-anonymous-types.md)または[コレクション初期化子](./collection-initializers/index.md)します。

- 埋め込み式、開かれた後 (`<%=`) または埋め込み式の終了前に (`%>`) XML リテラル内で。 例えば:

   [!code-vb[VbVbalrLineContinuation#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#4)]

   詳細については、次を参照してください。 [XML での埋め込み式](./xml/embedded-expressions-in-xml.md)します。

- 連結演算子の後に (`&`)。 例えば:

   [!code-vb[VbVbcnConventions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/vb/Class1.vb#9)]

   詳細については、次を参照してください。[機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)します。

- 代入演算子の後 (`=`、 `&=`、 `:=`、 `+=`、 `-=`、 `*=`、 `/=`、 `\=`、 `^=`、 `<<=`、 `>>=`)。 例えば:

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   詳細については、次を参照してください。[機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)します。

- 二項演算子の後 (`+`、 `-`、 `/`、 `*`、 `Mod`、 `<>`、 `<`、 `>`、 `<=`、 `>=`、 `^`、 `>>`、`<<`、 `And`、 `AndAlso`、 `Or`、 `OrElse`、 `Like`、 `Xor`) 式内で。 例えば:

   [!code-vb[VbVbalrLineContinuation#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#7)]

   詳細については、次を参照してください。[機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)します。

- 後に、`Is`と`IsNot`演算子。 例えば:

   [!code-vb[VbVbalrLineContinuation#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#8)]

   詳細については、次を参照してください。[機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)します。

- メンバー修飾子文字の後 (`.`) とメンバー名の前にします。 例えば:

   [!code-vb[VbVbalrLineContinuation#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#5)]

   ただし、行連結文字を含める必要があります (`_`) を使用するメンバーの修飾子文字を以下に、`With`ステートメントまたは型の初期化リスト内の値を指定します。 代入演算子の後で改行を検討してください (たとえば、 `=`) を使用する場合`With`ステートメントやオブジェクトの初期化リスト。 例:

   [!code-vb[VbVbalrLineContinuation#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#14)]

   詳細については、次を参照してください[としています... ステートメントで終了して](../../../visual-basic/language-reference/statements/with-end-with-statement.md)または[オブジェクト初期化子。名前付きの匿名型](./objects-and-classes/object-initializers-named-and-anonymous-types.md)します。

- XML 軸プロパティ修飾子の後 (`.`または`.@`または`...`)。 ただし、行連結文字を含める必要があります (`_`) を使用するときにメンバー修飾子を指定すると、`With`キーワード。 例えば:

   [!code-vb[VbVbalrLineContinuation#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#9)]

   詳細については、次を参照してください。 [XML 軸プロパティ](../../../visual-basic/language-reference/xml-axis/index.md)します。

- 小後-不等号 (<)、または前に、大きい-不等号 (`>`) 属性を指定するとします。 大きい後も、不等号 (`>`) 属性を指定するとします。 ただし、行連結文字を含める必要があります (`_`) アセンブリ レベルまたはモジュール レベルの属性を指定するとします。 例えば:

   [!code-vb[VbVbalrLineContinuation#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#10)]

   詳細については、次を参照してください。[属性の概要](../../../visual-basic/programming-guide/concepts/attributes/index.md)します。

- クエリ演算子の前後に (`Aggregate`、 `Distinct`、 `From`、 `Group By`、 `Group Join`、 `Join`、 `Let`、 `Order By`、 `Select`、 `Skip`、 `Skip While`、 `Take`、 `Take While`、 `Where`、 `In`、 `Into`、 `On`、 `Ascending`、および`Descending`)。 複数のキーワードで構成されているクエリ演算子のキーワードの間に行を分割することはできません (`Order By`、 `Group Join`、 `Take While`、および`Skip While`)。 例えば:

   [!code-vb[VbVbalrLineContinuation#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#11)]

   詳細については、次を参照してください。[クエリ](../../../visual-basic/language-reference/queries/index.md)します。

- 後に、`In`キーワード、`For Each`ステートメント。 例えば:

   [!code-vb[VbVbalrLineContinuation#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#12)]

   詳細については、[For Each...Next ステートメント](../../../visual-basic/language-reference/statements/for-each-next-statement.md)を参照してください。

- 後に、`From`コレクション初期化子内のキーワード。 例えば:

   [!code-vb[VbVbalrLineContinuation#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrlinecontinuation/vb/module1.vb#13)]

   詳細については、「[コレクション初期化子](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)」を参照してください。

## <a name="adding-comments"></a>コメントを追加します。

ソース コードは自明ですが、それを記述したプログラマにも常にします。 そのコードを文書化するには、そのため、プログラマのほとんどに利用リベラル派埋め込まれたコメント。 コード内のコメントには、プロシージャ、またはすべてのユーザーの読み取りまたは後で使用する特定の命令を説明します。 Visual Basic は、コンパイル時に、コメントを無視し、コンパイル済みコードには影響しません。

コメント行はアポストロフィで始まります (`'`) または`REM`スペースします。 追加できる任意の場所コードでは、以外の文字列内で。 ステートメントにコメントを追加するには、アポストロフィを挿入または`REM`後、ステートメントの後に、コメント、します。 コメントは、独自の個別の行に移動できます。 次の例では、これらの可能性を示します。

[!code-vb[VbVbalrStatements#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#72)]

## <a name="checking-compilation-errors"></a>コンパイル エラーの確認

後のコード行を入力する場合は、(エラー メッセージが表示されることも) 青色の波下線付きの行が表示されます、ステートメントに構文エラーがあります。 (タスク一覧で検索またはポインターを合わせると、マウス ポインターをエラーとエラー メッセージを読み取って) で新機能については、ステートメントで間違ったと、修正する必要があります。 コードですべての構文エラーを修正するまで、プログラムは正常にコンパイルは失敗します。

## <a name="related-sections"></a>関連項目

|用語|定義|
|---|---|
|[代入演算子](../../../visual-basic/language-reference/operators/assignment-operators.md)|代入演算子をカバーするなどの言語リファレンスのページへのリンクを提供`=`、 `*=`、および`&=`します。|
|[演算子および式](./operators-and-expressions/index.md)|新しい値を取得する演算子を含む要素を結合する方法を示します。|
|[方法: コード内でステートメントを分割および連結する](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)|1 つのステートメントを複数の行に分割する方法と同じ行に複数のステートメントを配置する方法を示します。|
|[方法: ステートメントへのラベル付け](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)|コードの行にラベル付けする方法を示します。|
