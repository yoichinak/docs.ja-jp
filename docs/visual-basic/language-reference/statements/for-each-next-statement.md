---
title: For Each...Next ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ForEach
- vb.ForEachNext
- vb.Each
- ForEachNext
helpviewer_keywords:
- infinite loops
- Next statement [Visual Basic], For Each...Next
- endless loops
- loop structures [Visual Basic], For Each...Next
- loops, endless
- Each keyword [Visual Basic]
- instructions, repeating
- For Each statement [Visual Basic]
- collections, instruction repetition
- loops, infinite
- For Each...Next statements
- For keyword [Visual Basic], For Each...Next statements
- Exit statement [Visual Basic], For Each...Next statements
- iteration
ms.assetid: ebce3120-95c3-42b1-b70b-fa7da40c75e2
ms.openlocfilehash: ebfd05a39c290e379bea2b925e7ea30c40d303fe
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046314"
---
# <a name="for-eachnext-statement-visual-basic"></a>For Each...Next ステートメント (Visual Basic)

コレクション内の各要素に対してステートメントのグループを繰り返します。

## <a name="syntax"></a>構文

```
For Each element [ As datatype ] In group
    [ statements ]
    [ Continue For ]
    [ statements ]
    [ Exit For ]
    [ statements ]
Next [ element ]
```

## <a name="parts"></a>指定項目

|用語|定義|
|---|---|
|`element`|ステートメントでは`For Each`必須です。 ステートメントでは`Next`省略可能です。 変動. コレクションの要素を反復処理するために使用されます。|
|`datatype`|が on [`Option Infer`](option-infer-statement.md) (既定値) また`element`はが`Option Infer`既に宣言されている場合は`element`省略可能。がオフであり、まだ宣言されていない場合は必須。 `element` のデータ型です。|
|`group`|必須。 コレクション型またはオブジェクトである型を持つ変数。 を繰り返すコレクション`statements`を参照します。|
|`statements`|省略可能です。 内の`For Each` `Next` 各項目に対して実行される、との間の1つ`group`以上のステートメント。|
|`Continue For`|省略可能です。 `For Each`ループの開始位置に制御を転送します。|
|`Exit For`|省略可能です。 制御を`For Each`ループの外に転送します。|
|`Next`|必須。 `For Each`ループの定義を終了します。|

## <a name="simple-example"></a>簡単な例

使用する`For Each`...`Next`コレクションまたは配列の各要素に対して一連のステートメントを繰り返す場合にループします。

> [!TIP]
> [For...Next ステートメント](../../../visual-basic/language-reference/statements/for-next-statement.md)うまくときに、ループの各繰り返しを制御変数に関連付けるし、その変数の最初と最後の値を決定します。 ただし、コレクションを処理する場合、初期値と最終値の概念は意味がなく、コレクションに含まれる要素の数がわかるとは限りません。 この種類のケースでは`For Each`、...`Next`ループは多くの場合に適しています。

次の例では`For Each`、...`Next` ステートメントは、リストコレクションのすべての要素を反復処理します。

[!code-vb[VbVbalrStatements#121](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#121)]

その他の例については、「[コレクション](../../../standard/collections/index.md)と[配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)」を参照してください。

## <a name="nested-loops"></a>入れ子になったループ

ループを入れ子`For Each`にするには、ループを別のループ内に配置します。

入れ子になっ`For Each`たの例を次に示します。`Next` 構成.

[!code-vb[VbVbalrStatements#122](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#122)]

ループを入れ子にする場合、各ループは一意`element`の変数を持つ必要があります。

また、さまざまな種類の制御構造を相互に入れ子にすることもできます。 詳細については、[入れ子になった制御構造](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md) を参照してください。

## <a name="exit-for-and-continue-for"></a>Exit For と Continue For

[Exit For](../../../visual-basic/language-reference/statements/exit-statement.md)ステートメントを実行すると、 `For`...`Next` ループし、 `Next`ステートメントの後のステートメントに制御を転送します。

ステートメント`Continue For`は、ループの次の反復処理に制御を直ちに転送します。 詳細については、「 [Continue ステートメント](../../../visual-basic/language-reference/statements/continue-statement.md)」を参照してください。

次の例は、ステートメントと`Continue For` `Exit For`ステートメントの使用方法を示しています。

[!code-vb[VbVbalrStatements#123](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#123)]

ループ内には、任意`Exit For`の数のステートメントを含めることができます。 `For Each` 入れ子になっ`For Each`たループ内`Exit For`で使用された場合、実行は最も内側のループを終了し、次の上位レベルの入れ子に制御を転送します。

`Exit For`は、たとえば`If`... などの条件を評価した後に使用されることがよくあります。`Then`...`Else`構造体。 次の条件の場合、`Exit For`を使用できます。

- 反復処理を続行することは不要または不可能です。 これは、エラー値または終了要求が原因である可能性があります。

- 例外がキャッチされまし`Try`た...`Catch`...`Finally`.`Finally`ブロックの最後に`Exit For`を使用できます。

- 無限ループがあります。これは、大規模または無限の回数実行されるループです。 このような条件を検出した場合は`Exit For`を使用してループをエスケープすることができます。 詳細については、次を参照してください[操作を行います...ステートメントをループ](../../../visual-basic/language-reference/statements/do-loop-statement.md)です。

## <a name="iterators"></a>Iterators

*反復子*を使用して、コレクションに対してカスタムの反復処理を実行します。 反復子は、関数または`Get`アクセサーにすることができます。 また、ステートメント`Yield`を使用して、コレクションの各要素を1つずつ返します。

反復子を呼び出すには、 `For Each...Next`ステートメントを使用します。 `For Each` ループの各イテレーションは、反復子を呼び出します。 反復子で`Yield` ステートメントに到達すると、ステートメント内の式が返され、コード内の現在の位置が保持`Yield`されます。 次回、反復子が呼び出されると、この位置から実行が再開されます。

次の例では、iterator 関数を使用します。 Iterator 関数が、`Yield`内にあるステートメント、[For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md)ループします。 メソッドでは、 `For Each`ステートメント本体の各反復処理によって、次`Yield`のステートメントに進む反復子関数の呼び出しが作成されます。 `ListEvenNumbers`

[!code-vb[VbVbalrStatements#127](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#127)]

詳細については、「[反復子](../../programming-guide/concepts/iterators.md)、 [Yield ステートメント](../../../visual-basic/language-reference/statements/yield-statement.md)、および[反復子](../../../visual-basic/language-reference/modifiers/iterator.md)」を参照してください。

## <a name="technical-implementation"></a>技術的な実装

`For Each`When...`Next` ステートメントを実行すると、ループが開始される前に、Visual Basic によってコレクションが1回だけ評価されます。 ステートメントブロックにまたは`element`が`group`変更された場合、これらの変更はループの反復に影響しません。

コレクション内のすべての要素がに`element`連続して割り当てられている場合、ループは停止し、 `Next`ステートメントに続くステートメントに制御が`For Each`移ります。

[オプションの推論](option-infer-statement.md)が on (既定の設定) の場合、Visual Basic コンパイラはの`element`データ型を推論できます。 Off `element`で、ループの外側で宣言されていない場合は、 `For Each`ステートメントで宣言する必要があります。 の`element`データ型を明示的に宣言するに`As`は、句を使用します。 要素のデータ型が... の外部`For Each`で定義されている場合を除きます。`Next`コンストラクト、そのスコープはループの本体です。 ループの外側と外側`element`の両方を宣言することはできないことに注意してください。

必要に応じて`element` 、 `Next`ステートメントでを指定できます。 これにより、特に入れ子になっ`For Each`たループがある場合に、プログラムの読みやすさが向上します。 対応`For Each`するステートメントに表示されるものと同じ変数を指定する必要があります。

ループ内のの`element`値を変更しないようにすることもできます。 これにより、コードの読み取りとデバッグが困難になる可能性があります。 の`group`値を変更しても、ループが最初に入力されたときに決定されたコレクションまたはその要素には影響しません。

ループを入れ子にしているとき`Next`に、入れ子レベルが外側のステートメントが内部`Next`レベルのの前に見つかった場合、コンパイラはエラーを通知します。 ただし、コンパイラは、すべて`element` `Next`のステートメントでを指定した場合にのみ、この重複エラーを検出できます。

コードが特定の順序でコレクションを走査することに依存し`For Each`ている場合は、...`Next`コレクションが公開する列挙子オブジェクトの特性がわかっていない限り、ループは最適な選択ではありません。 走査の順序は Visual Basic によって決定されるの<xref:System.Collections.IEnumerator.MoveNext%2A>ではなく、列挙子オブジェクトのメソッドによって決定されます。 したがって、コレクションのどの要素がに`element`最初に返されるか、または特定の要素の後に返される次の要素を予測できない場合があります。 別のループ構造 ( `For`... など) を使用して、より信頼性の高い結果を得ることができます。または`Do`... `Next``Loop`.

ランタイムは、の`group`要素をに`element`変換できる必要があります。 [`Option Strict`] ステートメントは、拡大変換と縮小変換の両方が許可`Option Strict`されるかどうかを制御します (がオフ、既定値)`Option Strict` 。または、拡大変換のみが許可されるかどうかを制御します (がオン)。 詳細については、「[縮小変換](#narrowing-conversions)」を参照してください。

の`group`データ型は、コレクションまたは列挙可能な配列を参照する参照型である必要があります。 最も`group`一般的には、は、名前空間の`System.Collections` <xref:System.Collections.IEnumerable>インターフェイスまた<xref:System.Collections.Generic.IEnumerable%601>は`System.Collections.Generic`名前空間のインターフェイスを実装するオブジェクトを参照します。 `System.Collections.IEnumerable`コレクションの列挙子オブジェクトを返すメソッドを定義します。<xref:System.Collections.IEnumerable.GetEnumerator%2A> 列挙子オブジェクトは、 `System.Collections.IEnumerator` `System.Collections`名前空間のインターフェイスを実装し<xref:System.Collections.IEnumerator.Current%2A> 、プロパティ、 <xref:System.Collections.IEnumerator.Reset%2A>メソッド<xref:System.Collections.IEnumerator.MoveNext%2A> 、およびメソッドを公開します。 Visual Basic は、これらを使用してコレクションを走査します。

### <a name="narrowing-conversions"></a>縮小変換

が`Option Strict` に`On`設定されている場合、縮小変換は通常、コンパイラエラーになります。 ただし、 `group` `element`ステートメントでは、の要素からへの変換が実行時に評価されて実行され、縮小変換によって発生するコンパイラエラーは抑制されます。 `For Each`

次の例では、を`m` `Option Strict` `n` onに`Long`した場合、の初期値としての割り当てはコンパイルされません。これは、からへの変換が縮小変換であるためです。`Integer` ただし、 `number` `Long` `Integer`ステートメントでは、への代入でからへの変換が必要な場合でも、コンパイラエラーは報告されません。 `For Each` 多数の数値が含まれている<xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A> ステートメントでは、が大きい数値に適用されると、実行時エラーが発生します。`For Each`

[!code-vb[VbVbalrStatements#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class3.vb#89)]

### <a name="ienumerator-calls"></a>IEnumerator 呼び出し

実行`For Each`時に...ループが開始され、 `group`が有効なコレクションオブジェクトを参照していることを Visual Basic 確認します。 `Next` そうでない場合は、例外がスローされます。 それ以外の場合は<xref:System.Collections.IEnumerator.MoveNext%2A> 、最初の<xref:System.Collections.IEnumerator.Current%2A>要素を返すために、列挙子オブジェクトのメソッドとプロパティを呼び出します。 は、次の要素がないことを`For Each` `Next` 示します。つまり、コレクションが空の場合、ループは停止し、ステートメントに続くステートメントに制御`MoveNext`が移ります。 それ以外の場合`element` 、Visual Basic は最初の要素に設定され、ステートメントブロックが実行されます。

Visual Basic が`Next`ステートメントを検出`For Each`するたびに、ステートメントに戻ります。 ここでも`MoveNext` 、 `Current`とを呼び出して次の要素を返します。もう一度、ブロックを実行するか、結果に応じてループを停止します。 このプロセスは、 `MoveNext`次の要素が存在しないこと、 `Exit For`またはステートメントが検出されるまで続行されます。

**コレクションを変更しています。** 通常、によって<xref:System.Collections.IEnumerable.GetEnumerator%2A>返される列挙子オブジェクトでは、要素の追加、削除、置換、または並べ替えによってコレクションを変更することはできません。 を`For Each`開始した後にコレクションを変更した場合loop を使用すると、列挙子オブジェクトが無効になり、次に要素に<xref:System.InvalidOperationException>アクセスしようとすると例外が発生します。 `Next`

ただし、この変更のブロックは Visual Basic によって決定されるのではなく<xref:System.Collections.IEnumerable> 、インターフェイスの実装によって決まります。 の実装`IEnumerable`は、反復処理中の変更を可能にする方法で行うことができます。 このような動的な変更を検討している場合は、使用している`IEnumerable`コレクションの実装の特性を理解していることを確認してください。

**コレクション要素を変更しています。** 列挙子オブジェクトのプロパティは [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md) であり、各コレクション要素のローカルコピーを返し<xref:System.Collections.IEnumerator.Current%2A>ます。 つまり、 `For Each`次のようにして、要素自体を変更することはできません。`Next` loop。 行った変更は、からの`Current`ローカルコピーにのみ影響し、基になるコレクションには反映されません。 ただし、要素が参照型の場合は、その要素が指すインスタンスのメンバーを変更できます。 次の例では`BackColor` 、各`thisControl`要素のメンバーを変更します。 ただし、それ自体を変更`thisControl`することはできません。

```vb
Sub lightBlueBackground(ByVal thisForm As System.Windows.Forms.Form)
    For Each thisControl As System.Windows.Forms.Control In thisForm.Controls
        thisControl.BackColor = System.Drawing.Color.LightBlue
    Next thisControl
End Sub
```

前の例では、 `BackColor`各`thisControl`要素のメンバーを変更することは`thisControl`できますが、変更することはできません。

**配列を走査しています。** クラスは<xref:System.Array> <xref:System.Collections.IEnumerable>インターフェイスを実装するため<xref:System.Array.GetEnumerator%2A> 、すべての配列がメソッドを公開します。 これは、 `For Each`... を使用して配列を反復処理できることを意味します。`Next` loop。 ただし、読み取ることができるのは配列要素だけです。 変更することはできません。

## <a name="example"></a>例

次の例では、C:\ 内のすべてのフォルダーを一覧表示します。クラスを使用し<xref:System.IO.DirectoryInfo>たディレクトリ。

[!code-vb[VbVbalrStatements#124](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#124)]

## <a name="example"></a>例

次の例では、コレクションを並べ替えるための手順を示しています。 この例では、 `Car` <xref:System.Collections.Generic.List%601>に格納されているクラスのインスタンスを並べ替えます。 `Car` クラスは、<xref:System.IComparable%601> のメソッドの実装を必要とする <xref:System.IComparable%601.CompareTo%2A> インターフェイスを実装します。

<xref:System.IComparable%601.CompareTo%2A>メソッドを呼び出すたびに、並べ替えに使用される1つの比較が行われます。 `CompareTo` メソッドのユーザーが作成したコードは、現在のオブジェクトと別のオブジェクトとの各比較の値を戻します。 現在のオブジェクトが別のオブジェクトよりも小さい場合はゼロ未満の値を、大きい場合はゼロ以上の値を、等しい場合はゼロを戻します。 これによって、より大きい、より小さい、等しい、の条件をコードに定義することができます。

`ListCars` のメソッドでは、`cars.Sort()` ステートメントがリストを並べ替えます。 <xref:System.Collections.Generic.List%601.Sort%2A> の <xref:System.Collections.Generic.List%601> メソッドへの呼び出しによって、`CompareTo` メソッドは `Car` 内の `List` オブジェクトに自動的に呼び出されます。

[!code-vb[VbVbalrStatements#125](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#125)]

## <a name="see-also"></a>関連項目

- [コレクション](../../../standard/collections/index.md)
- [For...Next ステートメント](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [ループ構造](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [While...End While ステートメント](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Do...Loop ステートメント](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [拡大変換と縮小変換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [オブジェクト初期化子:名前付きの型と匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [コレクション初期化子](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)
