---
title: For...Next ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Step
- vb.Next
- vb.To
- vb.for
helpviewer_keywords:
- infinite loops
- Next keyword [Visual Basic], For...Next statements
- For keyword [Visual Basic], For...Next statements
- Step keyword [Visual Basic], For...Next statements
- operator overloading, For...Next statement
- To keyword [Visual Basic], For...Next statements
- endless loops
- loops, endless
- instructions, repeating
- Next statement [Visual Basic], For...Next
- For...Next statements
- loop structures [Visual Basic], For...Next
- loops, infinite
- Exit statement [Visual Basic], For...Next statements
- For statement [Visual Basic]
ms.assetid: f5fc0d51-67ce-4c36-9f09-31c9a91c94e9
ms.openlocfilehash: 7f982c97bd76288ecd1a8d1f53fc2b25b0bb829e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623885"
---
# <a name="fornext-statement-visual-basic"></a>For...Next ステートメント (Visual Basic)
ステートメントのグループを指定した回数だけ繰り返されます。  
  
## <a name="syntax"></a>構文  
  
```  
For counter [ As datatype ] = start To end [ Step step ]  
    [ statements ]  
    [ Continue For ]  
    [ statements ]  
    [ Exit For ]  
    [ statements ]  
Next [ counter ]  
```  
  
## <a name="parts"></a>指定項目  
  
|パーツ|説明|  
|----------|-----------------|  
|`counter`|必要な`For`ステートメント。 数値型の変数。 ループ コントロール変数。 詳細については、次を参照してください。[カウンター引数](#BKMK_Counter)このトピックで後述します。|  
|`datatype`|省略可能です。 データ型`counter`します。 詳細については、次を参照してください。[カウンター引数](#BKMK_Counter)このトピックで後述します。|  
|`start`|必須。 数値式。 `counter` の初期値になります。|  
|`end`|必須。 数値式。 最終値`counter`します。|  
|`step`|省略可能です。 数値式。 量`counter`ループのたびに増加します。|  
|`statements`|省略可能です。 1 つまたは複数のステートメント間`For`と`Next`指定された回数を実行します。|  
|`Continue For`|省略可能です。 次のループの反復処理の制御を転送します。|  
|`Exit For`|省略可能です。 うちに制御を転送、`For`ループします。|  
|`Next`|必須。 定義を終了、`For`ループします。|  
  
> [!NOTE]
> このステートメントでは、`To`キーワードを使用して、カウンターの範囲を指定します。 このキーワードは [Select...Case ステートメント](../../../visual-basic/language-reference/statements/select-case-statement.md) と配列の宣言でも使用できます。 配列の宣言に関する詳細については、[Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md) を参照してください。  
  
## <a name="simple-examples"></a>簡単な例  
 使用する、 `For`.`Next`時間数の一連のステートメントを繰り返し表示するときに構造体します。  
  
 次の例では、`index`変数の値が 1 で開始し、終了の値の後に、ループの反復ごとにインクリメントされます`index`5 に到達します。  
  
 [!code-vb[VbVbalrStatements#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#111)]  
  
 次の例では、`number`変数が 2 から開始し、終了の値の後に、ループの各反復処理で 0.25 を消費`number`が 0 になります。 `Step`の引数`-.25`ループの各反復処理で 0.25 で値を減らします。  
  
 [!code-vb[VbVbalrStatements#112](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#112)]  
  
> [!TIP]
> [While...End While ステートメント](../../../visual-basic/language-reference/statements/while-end-while-statement.md)または[Do...Loop ステートメント](../../../visual-basic/language-reference/statements/do-loop-statement.md)は、ループ内でステートメントを実行する回数が事前にわからない場合にうまく機能します。 ただし、特定回数だけループを実行する場合は`For`.`Next`ループの方が適しています。 ループを最初に入力するときに、イテレーションの数を決定します。  
  
## <a name="nesting-loops"></a>ループの入れ子  
 入れ子にすることができます`For`内に別の 1 つのループを配置することでループします。 次の例で入れ子になった`For`.`Next`異なるステップ値を持つ構造体。 外側のループは、ループのイテレーションごとに文字列を作成します。 内側のループのイテレーションごとのループ カウンター変数をデクリメントをループします。  
  
 [!code-vb[VbVbalrStatements#113](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#113)]  
  
 ループを入れ子にする場合は、各ループが一意必要があります`counter`変数。  
  
 さまざまな種類の制御構造を入れ子にすることもできます。 詳細については、[入れ子になった制御構造](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)を参照してください。  
  
## <a name="exit-for-and-continue-for"></a>終了しの続行  
 `Exit For`ステートメントがすぐに終了させる、 `For`.`Next` これに続くステートメントにループと転送の制御、`Next`ステートメント。  
  
 `Continue For`ステートメント コントロールに直ちに移します、ループの次の反復処理します。 詳細については、次を参照してください。 [Continue ステートメント](../../../visual-basic/language-reference/statements/continue-statement.md)します。  
  
 次の例では、使用、`Continue For`と`Exit For`ステートメント。  
  
 [!code-vb[VbVbalrStatements#115](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#115)]  
  
 任意の数を配置する`Exit For`内のステートメントを`For`.`Next` ループします。 使用すると内で入れ子になった`For`.`Next` ループ、`Exit For`最も内側のループを終了し、入れ子の上位のレベルに制御を転送します。  
  
  `Exit For` は何らかの条件 (たとえば、 `If`...`Then`...`Else`構造) を評価した後によく使用されます。次の条件の場合、`Exit For`を使用できます。 
  
- 反復処理を続けることは不要なか不可能です。 エラー値や終了要求は、この条件を作成可能性があります。  
  
- `Try`...`Catch`...`Finally`ステートメントは例外をキャッチします。`Finally`ブロックの最後に`Exit For`を使用できます。   
  
- 何度も長時間または無限でも実行できるループ、無限ループがあります。 このような条件を検出した場合は`Exit For`を使用してループをエスケープすることができます。 詳細については、[Do...Loop ステートメント](../../../visual-basic/language-reference/statements/do-loop-statement.md)を参照してください。  
  
## <a name="technical-implementation"></a>技術的な実装  
 ときに、 `For`.`Next`ループの開始、Visual Basic の評価`start`、 `end`、および`step`します。 Visual Basic では、この時間とし、割り当てにのみこれらの値を評価`start`に`counter`します。 ステートメントの前にブロックが実行、Visual Basic の比較`counter`に`end`します。 場合`counter`よりも大きいは既に、`end`値 (より小さい場合、または`step`が負の値)、`For`ループが終了と制御に続くステートメントに渡す、`Next`ステートメント。 それ以外の場合、ステートメント ブロックが実行されます。  
  
 Visual Basic が発生するたびに、`Next`インクリメント ステートメントでは、`counter`によって`step`に戻って、`For`ステートメント。 もう一度比較`counter`に`end`、もう一度、ブロックが実行か、その結果に応じて、ループが終了したとします。 までこのプロセスは継続`counter`渡します`end`または`Exit For`ステートメントが見つかりました。  
  
 まで、ループが停止しない`counter`経過`end`します。 場合`counter`と等しい`end`ループが続行されます。 ブロックを実行するかどうかを決定する比較では、 `counter`  <=  `end`場合`step`が正の値と`counter`  >=  `end`場合`step`が負の値。  
  
 値を変更する場合`counter`ループ内で、コードは読み取り、デバッグが難しくなります。 値を変更する`start`、 `end`、または`step`ループが最初に入力すると判断した反復値には影響しません。  
  
 ループを入れ子にする場合、コンパイラはエラーが発生したかどうか、`Next`する前に外側の入れ子レベルのステートメント、`Next`内部レベルのステートメント。 ただし、コンパイラが検出できるこれを指定する場合にのみ、エラーを重複`counter`ですべて`Next`ステートメント。  
  
### <a name="step-argument"></a>手順の引数  
 値`step`正または負にすることができます。 このパラメーターは、次の表に従って、ループ処理を決定します。  
  
|**ステップ値**|**場合、ループが実行されます。**|  
|--------------------|--------------------------|  
|正またはゼロ|`counter` <= `end`|  
|負|`counter` >= `end`|  
  
 既定値の`step`は 1 です。  
  
### <a name="BKMK_Counter"></a> カウンターの引数  
 次の表に示すかどうか`counter`全体をスコープは、新しいローカル変数を定義します。`For…Next`ループします。 この決定によって異なるかどうか`datatype`が存在するかどうかおよび`counter`は既に定義されています。  
  
|`datatype`存在でしょうか。|`counter`既に定義されていますか?|結果 (かどうか`counter`全体をスコープは、新しいローカル変数を定義します`For...Next`ループ)。|  
|----------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------|  
|いいえ|[はい]|いいえ、ため`counter`は既に定義されています。 場合のスコープ`counter`いない、プロシージャに対してローカルに、コンパイル時に警告が発生します。|  
|いいえ|いいえ|はい。 データ型から推論されます、 `start`、 `end`、および`step`式。 型の推定については、次を参照してください。 [Option Infer ステートメント](../../../visual-basic/language-reference/statements/option-infer-statement.md)と[ローカル型推論](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)します。|  
|[はい]|[はい]|[はい] が場合にのみ、既存の`counter`プロシージャの外部変数が定義されています。 その変数は別に維持します。 場合、既存のスコープ`counter`変数は、プロシージャに対してローカルに、コンパイル時エラーが発生します。|  
|[はい]|いいえ|はい。|  
  
 データ型`counter`イテレーションでは、次の種類のいずれかを指定する必要がありますの種類を決定します。  
  
- A `Byte`、 `SByte`、 `UShort`、 `Short`、 `UInteger`、 `Integer`、 `ULong`、 `Long`、 `Decimal`、 `Single`、または`Double`します。  
  
- 列挙体を使用して宣言する、 [Enum ステートメント](../../../visual-basic/language-reference/statements/enum-statement.md)します。  
  
- `Object`。  
  
- 型`T`、次の演算子を持つ場所`B`型で使用できるは、`Boolean`式。  
  
     `Public Shared Operator >= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator <= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator - (op1 As T, op2 As T) As T`  
  
     `Public Shared Operator + (op1 As T, op2 As T) As T`  
  
 必要に応じて指定することができます、`counter`変数、`Next`ステートメント。 入れ子にしていない場合は特に、この構文は、プログラムの読みやすさを向上`For`ループします。 対応する表示される変数を指定する必要があります`For`ステートメント。  
  
 `start`、 `end`、および`step`式が評価される任意のデータ型の型を拡張する`counter`します。 ユーザー定義型を使用する場合`counter`、定義する必要がありますが、`CType`変換演算子の型に変換する`start`、 `end`、または`step`の型に`counter`。  
  
## <a name="example"></a>例  
 次の例では、ジェネリック リストからすべての要素を削除します。 この例では、[For Each...Next ステートメント](../../../visual-basic/language-reference/statements/for-each-next-statement.md)の代わりに、降順に反復処理する`For`...`Next`ステートメントを使用します。 例では、`removeAt`メソッドで削除された要素の後にある要素のインデックス値がより小さくなるため、この手法を使用します。  
  
 [!code-vb[VbVbalrStatements#114](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#114)]  
  
## <a name="example"></a>例  
 次の例を使用して宣言されている列挙型を反復処理、 [Enum ステートメント](../../../visual-basic/language-reference/statements/enum-statement.md)します。  
  
 [!code-vb[VbVbalrStatements#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#116)]  
  
## <a name="example"></a>例  
 次の例では、ステートメントのパラメーターが演算子のオーバー ロードを持つクラスを使用して、 `+`、 `-`、 `>=`、および`<=`演算子。  
  
 [!code-vb[VbVbalrStatements#117](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#117)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Collections.Generic.List%601>
- [ループ構造](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [While...End While ステートメント](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Do...Loop ステートメント](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [入れ子になった制御構造](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit ステートメント](../../../visual-basic/language-reference/statements/exit-statement.md)
- [コレクション](../../programming-guide/concepts/collections.md)
