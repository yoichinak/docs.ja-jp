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
ms.openlocfilehash: 269d905ad59a162af4e790e29d3753f090f511bd
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975005"
---
# <a name="for-eachnext-statement-visual-basic"></a>For Each...Next ステートメント (Visual Basic)
ステートメントのグループをコレクション内の各要素に対して繰り返されます。  
  
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
|`element`|必要な`For Each`ステートメント。 省略可能で、`Next`ステートメント。 変数。 コレクションの要素を反復処理するために使用します。|  
|`datatype`|場合に、必ず`element`既に宣言されていません。 データ型`element`します。|  
|`group`|必須。 コレクション型またはオブジェクト型を含む変数を指定します。 コレクションを参照、`statements`られます。|  
|`statements`|任意。 1 つまたは複数のステートメント間`For Each`と`Next`内の各項目で実行される`group`します。|  
|`Continue For`|任意。 先頭に制御を転送、`For Each`ループします。|  
|`Exit For`|任意。 うちに制御を転送、`For Each`ループします。|  
|`Next`|必須。 定義を終了、`For Each`ループします。|  
  
## <a name="simple-example"></a>簡単な例  
 使用して、 `For Each`.`Next`コレクションまたは配列の各要素の一連のステートメントを繰り返し表示するときにループ処理します。  
  
> [!TIP]
>  A[をしています.次のステートメントの](../../../visual-basic/language-reference/statements/for-next-statement.md)うまくときに、ループの各繰り返しを制御変数に関連付けるし、その変数の最初と最後の値を決定します。 ただし、コレクションを扱う場合は、最初と最後の値の概念は意味のあると、コレクションは、要素の数がわからないとは限りません。 このような場合で、 `For Each`.`Next`ループは、多くの場合、ことをお勧めします。  
  
 次の例では、 `For Each`.`Next` ステートメントは、リスト コレクションのすべての要素を反復処理します。  
  
 [!code-vb[VbVbalrStatements#121](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#121)]  
  
 例については、次を参照してください。[コレクション](../../../standard/collections/index.md)と[配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)します。  
  
## <a name="nested-loops"></a>入れ子になったループ  
 入れ子にすることができます`For Each`内に別の 1 つのループを配置することでループします。  
  
 次の例で入れ子になった`For Each`.`Next` 構造体。  
  
 [!code-vb[VbVbalrStatements#122](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#122)]  
  
 各ループが一意ありますループを入れ子にすると`element`変数。  
  
 さまざまな種類を 1 つの制御構造の入れ子にすることもできます。 詳細については、次を参照してください。[制御構造の入れ子になった](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)します。  
  
## <a name="exit-for-and-continue-for"></a>終了しの続行  
 [Exit For](../../../visual-basic/language-reference/statements/exit-statement.md)ステートメントは、実行を終了する、 `For`.`Next` これに続くステートメントにループと転送の制御、`Next`ステートメント。  
  
 `Continue For`ステートメント コントロールに直ちに移します、ループの次の反復処理します。 詳細については、次を参照してください。 [Continue ステートメント](../../../visual-basic/language-reference/statements/continue-statement.md)します。  
  
 次の例は、使用する方法を示します、`Continue For`と`Exit For`ステートメント。  
  
 [!code-vb[VbVbalrStatements#123](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#123)]  
  
 任意の数を配置する`Exit For`内のステートメントを`For Each`ループします。 使用すると内で入れ子になった`For Each`ループ、`Exit For`実行を入れ子の上位のレベルへの最も内側のループと転送コントロールを終了します。  
  
 `Exit For` いくつかの条件の評価後は、よく使用など、 `If`.`Then`...`Else`構造体。 使用する`Exit For`次の条件。  
  
-   反復処理を続けることは不要なか不可能です。 これは、エラー値や終了要求によって発生する可能性があります。  
  
-   例外がキャッチされました、 `Try`.`Catch`...`Finally`.使用する場合があります`Exit For`の最後に、`Finally`ブロックします。  
  
-   何度も長時間または無限でも実行できるループ、無限ループがあります。 このような条件を検出した場合は使用できます`Exit For`ループを抜けます。 詳細については、次を参照してください[操作を行います...ステートメントをループ](../../../visual-basic/language-reference/statements/do-loop-statement.md)です。  
  
## <a name="iterators"></a>Iterators  
 使用する、*反復子*コレクションに対するカスタム イテレーションを実行します。 関数は、反復子または`Get`アクセサー。 使用して、`Yield`ステートメントを一度に 1 つのコレクションの各要素を返します。  
  
 使用して、反復子を呼び出す、`For Each...Next`ステートメント。 `For Each` ループの各イテレーションは、反復子を呼び出します。 ときに、`Yield`ステートメントが反復子の式に到達、`Yield`ステートメントが返され、コードの現在の場所が保持されます。 次回、反復子が呼び出されると、この位置から実行が再開されます。  
  
 次の例では、反復子関数を使用します。 Iterator 関数が、`Yield`内にあるステートメント、[をしています.[次へ]](../../../visual-basic/language-reference/statements/for-next-statement.md)ループします。 `ListEvenNumbers`メソッドは、の各反復処理、`For Each`ステートメント本体は、次に進みますこの反復子関数の呼び出しを作成します。`Yield`ステートメント。  
  
 [!code-vb[VbVbalrStatements#127](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#127)]  
  
 詳細については、次を参照してください。[反復子](../../programming-guide/concepts/iterators.md)、 [Yield ステートメント](../../../visual-basic/language-reference/statements/yield-statement.md)、および[反復子](../../../visual-basic/language-reference/modifiers/iterator.md)します。  
  
## <a name="technical-implementation"></a>技術的な実装  
 ときに、 `For Each`.`Next` ステートメントが実行されて、Visual Basic では、コレクション、ループの開始前に、1 つだけの時間を評価します。 ステートメント ブロックが変更された場合`element`または`group`、これらの変更は、ループの反復処理に影響はありません。  
  
 ときに、コレクション内のすべての要素連続的に割り当てられている`element`、`For Each`停止をループし、次のステートメントのパスを制御、`Next`ステートメント。  
  
 場合`element`宣言されていない、このループの外側に宣言する必要がありますで、`For Each`ステートメント。 型を宣言する`element`を使用して明示的に、`As`ステートメント、またはするを型の推定の型を割り当てるを利用できます。 どちらの場合のスコープで`element`ループの本体します。 ただし、宣言することはできません`element`外側と、ループ内での両方。  
  
 必要に応じて指定することができます`element`で、`Next`ステートメント。 入れ子にしていない場合は特に、プログラムの読みやすさが向上しますこの`For Each`ループします。 対応する表示されるものと同じ変数を指定する必要があります`For Each`ステートメント。  
  
 値を変更しないようにする`element`ループ内で。 これを行うことが難しくを読み取って、コードをデバッグします。 値を変更する`group`コレクションまたはその要素は、ループが最初に入力されたときに決定されたには影響しません。  
  
 場合に、ループが入れ子しているときに、`Next`する前に、外側の入れ子レベルのステートメントが見つかりましたが、`Next`コンパイラがエラーを内部レベルの。 ただし、コンパイラが検出できるこれを指定する場合にのみ、エラーを重複`element`ですべて`Next`ステートメント。  
  
 特定の順序でコレクションを走査することで、コードが依存している場合、 `For Each`.`Next`ループが最適な選択肢はありませんが、コレクション、列挙子オブジェクトの特性がわかっている場合を除き公開します。 走査の順序がによっての Visual Basic では、によって決定されていない、<xref:System.Collections.IEnumerator.MoveNext%2A>列挙子オブジェクトのメソッド。 コレクションの要素が、最初に返される予測できないことのため、 `element`、特定の要素の後に返される次であるか。 など、さまざまなループ構造を使用して、信頼性の高い結果を実現することがあります`For`.`Next`または`Do`.`Loop`.  
  
 データ型`element`の要素のデータを入力するようにある必要があります`group`に変換できます。  
  
 データ型`group`コレクションまたは列挙可能なである配列を参照する参照型である必要があります。 つまり通常`group`を実装するオブジェクトを指す、<xref:System.Collections.IEnumerable>のインターフェイス、`System.Collections`名前空間または<xref:System.Collections.Generic.IEnumerable%601>のインターフェイス、`System.Collections.Generic`名前空間。 `System.Collections.IEnumerable` 定義、<xref:System.Collections.IEnumerable.GetEnumerator%2A>メソッドで、コレクションの列挙子オブジェクトを返します。 列挙子オブジェクトを実装して、`System.Collections.IEnumerator`のインターフェイス、`System.Collections`名前空間を公開し、<xref:System.Collections.IEnumerator.Current%2A>プロパティおよび<xref:System.Collections.IEnumerator.Reset%2A>と<xref:System.Collections.IEnumerator.MoveNext%2A>メソッド。 Visual Basic では、これらを使用して、コレクションをスキャンします。  
  
### <a name="narrowing-conversions"></a>縮小変換  
 ときに`Option Strict`に設定されている`On`、通常、縮小変換でコンパイラ エラーが発生します。 `For Each`ステートメント、ただし、内の要素からの変換`group`に`element`が評価され、実行時に実行し、縮小変換によるコンパイラ エラーが抑制されます。  
  
 割り当て、次の例で`m`の初期値として`n`ときにコンパイルされません`Option Strict`ためではへの変換、`Long`を`Integer`縮小変換です。 `For Each`ステートメントでは、コンパイラ エラーがないへの代入も報告`number`から同じ変換が必要`Long`に`Integer`します。 `For Each`数が多いを含むステートメントでは、実行時エラーが発生したときに<xref:Microsoft.VisualBasic.CompilerServices.Conversions.ToInteger%2A>膨大な数に適用されます。  
  
 [!code-vb[VbVbalrStatements#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class3.vb#89)]  
  
### <a name="ienumerator-calls"></a>IEnumerator の呼び出し  
 ときの実行、 `For Each`.`Next`ループの開始、ことを確認します Visual Basic`group`は有効なコレクション オブジェクトを参照します。 それ以外の場合は、例外をスローします。 それ以外の場合、呼び出し、<xref:System.Collections.IEnumerator.MoveNext%2A>メソッドと<xref:System.Collections.IEnumerator.Current%2A>最初の要素を返す列挙子オブジェクトのプロパティ。 場合`MoveNext`がない、次の要素は、コレクションが空の場合を示します、`For Each`停止をループし、次のステートメントのパスを制御、`Next`ステートメント。 Visual Basic の場合は、設定`element`に最初の要素と、ステートメント ブロックを実行します。  
  
 Visual Basic が発生するたびに、`Next`にステートメントを返します、`For Each`ステートメント。 もう一度呼び出して`MoveNext`と`Current`ブロックが実行か、次の要素と、もう一度返しますまたは、結果に応じて、ループを停止します。 までこのプロセスは継続`MoveNext`次の要素がないことを示しますまたは`Exit For`ステートメントが見つかりました。  
  
 **コレクションを変更します。** によって返される列挙子オブジェクト<xref:System.Collections.IEnumerable.GetEnumerator%2A>通常変更することは、コレクションを追加、削除、置換、またはいずれかの要素の順序を変更します。 開始した後に、コレクションを変更する場合、 `For Each`.`Next`ループ列挙子オブジェクトが無効と要素にアクセスするには、次の試行により、<xref:System.InvalidOperationException>例外。  
  
 ただし、この変更のブロックされていない決定 Visual Basic での実装ではなく、<xref:System.Collections.IEnumerable>インターフェイス。 実装することは`IEnumerable`で反復処理中に変更できるようにします。 このような動的な変更を行うを検討している場合の特性を理解するように、`IEnumerable`を使用するコレクションを実装します。  
  
 **コレクションの要素を変更します。** <xref:System.Collections.IEnumerator.Current%2A>列挙子オブジェクトのプロパティが[ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)、し、各コレクションの要素のローカル コピーを返します。 つまり、要素自体を変更できないことで、 `For Each`.`Next`ループします。 対して行った変更の影響からローカルのコピーのみ`Current`基になるコレクションにも反映されていないとします。 ただし、要素が参照型の場合は、ポイントするインスタンスのメンバーを変更できます。 次の例では、変更、`BackColor`のそれぞれに所属`thisControl`要素。 ただし、変更することはできません、`thisControl`自体。  
  
```vb  
Sub lightBlueBackground(ByVal thisForm As System.Windows.Forms.Form)  
    For Each thisControl As System.Windows.Forms.Control In thisForm.Controls  
        thisControl.BackColor = System.Drawing.Color.LightBlue  
    Next thisControl  
End Sub  
```  
  
 前の例を変更できます、`BackColor`のそれぞれに所属`thisControl`要素、それを変更できませんが`thisControl`自体。  
  
 **配列の反復処理します。** <xref:System.Array>クラスが実装する、<xref:System.Collections.IEnumerable>インターフェイスでは、すべての配列を公開、<xref:System.Array.GetEnumerator%2A>メソッド。 つまり、配列を反復処理できること、 `For Each`.`Next`ループします。 ただし、配列の要素のみを読み取ることができます。 変更することはできません。  
  
## <a name="example"></a>例  
 次の例を使用して、C:\ ディレクトリ内のすべてのフォルダーを一覧表示、<xref:System.IO.DirectoryInfo>クラス。  
  
 [!code-vb[VbVbalrStatements#124](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#124)]  
  
## <a name="example"></a>例  
 次の例では、コレクションを並べ替えるための手順を示しています。 例では、並べ替えのインスタンスを`Car`クラスに格納されている、<xref:System.Collections.Generic.List%601>します。 `Car` クラスは、<xref:System.IComparable%601> のメソッドの実装を必要とする <xref:System.IComparable%601.CompareTo%2A> インターフェイスを実装します。  
  
 呼び出しごとに、<xref:System.IComparable%601.CompareTo%2A>メソッドは、並べ替えに使用される単一の比較。 `CompareTo` メソッドのユーザーが作成したコードは、現在のオブジェクトと別のオブジェクトとの各比較の値を戻します。 現在のオブジェクトが別のオブジェクトよりも小さい場合はゼロ未満の値を、大きい場合はゼロ以上の値を、等しい場合はゼロを戻します。 これによって、より大きい、より小さい、等しい、の条件をコードに定義することができます。  
  
 `ListCars` のメソッドでは、`cars.Sort()` ステートメントがリストを並べ替えます。 <xref:System.Collections.Generic.List%601.Sort%2A> の <xref:System.Collections.Generic.List%601> メソッドへの呼び出しによって、`CompareTo` メソッドは `Car` 内の `List` オブジェクトに自動的に呼び出されます。  
  
 [!code-vb[VbVbalrStatements#125](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class9.vb#125)]  
  
## <a name="see-also"></a>関連項目
- [コレクション](../../../standard/collections/index.md)
- [For...Next ステートメント](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [ループ構造](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [While...End While ステートメント](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Do...Loop ステートメント](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [拡大変換と縮小変換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [オブジェクト初期化子:名前付きの匿名型](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [コレクション初期化子](../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)
