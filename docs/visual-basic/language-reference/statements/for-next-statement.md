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
ms.openlocfilehash: cafd59482036a598814dcd4815fa67a791580045
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046301"
---
# <a name="fornext-statement-visual-basic"></a>For...Next ステートメント (Visual Basic)

ステートメントのグループを指定された回数だけ繰り返します。

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
|`counter`|ステートメントでは`For`必須です。 数値変数。 ループのコントロール変数。 詳細については、このトピックで後述する「 [Counter 引数](#BKMK_Counter)」を参照してください。|
|`datatype`|省略可能です。 の`counter`データ型。 詳細については、このトピックで後述する「 [Counter 引数](#BKMK_Counter)」を参照してください。|
|`start`|必須。 数値式。 `counter` の初期値になります。|
|`end`|必須。 数値式。 の最終的な`counter`値。|
|`step`|省略可能です。 数値式。 がループを通じ`counter`て毎回インクリメントされる量。|
|`statements`|省略可能です。 指定した回数だけ`For`実行`Next`される、との間の1つ以上のステートメント。|
|`Continue For`|省略可能です。 次のループの反復処理に制御を転送します。|
|`Exit For`|省略可能です。 制御を`For`ループの外に転送します。|
|`Next`|必須。 `For`ループの定義を終了します。|

> [!NOTE]
> このステートメントでは、`To`キーワードを使用して、カウンターの範囲を指定します。 このキーワードは [Select...Case ステートメント](../../../visual-basic/language-reference/statements/select-case-statement.md) と配列の宣言でも使用できます。 配列の宣言に関する詳細については、「 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)」を参照してください。

## <a name="simple-examples"></a>簡単な例

使用`For`している...`Next`一連のステートメントを設定された回数繰り返し実行する場合は、構造体。

次の例では、 `index`変数は値1で始まり、ループの繰り返しごとにインクリメントされます。これは、の`index`値が5に達した後に終了します。

[!code-vb[VbVbalrStatements#111](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#111)]

次の例では、 `number`変数は2から開始され、ループの反復ごとに0.25 によって減少し、の`number`値が0になると終了します。 `Step` の`-.25`引数は、ループの各反復処理で値を0.25 ずつ減らします。

[!code-vb[VbVbalrStatements#112](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#112)]

> [!TIP]
> [While...End While ステートメント](../../../visual-basic/language-reference/statements/while-end-while-statement.md)または[Do...Loop ステートメント](../../../visual-basic/language-reference/statements/do-loop-statement.md)は、ループ内でステートメントを実行する回数が事前にわからない場合にうまく機能します。 ただし、特定回数だけループを実行する場合は`For`.`Next`ループの方が適しています。 ループを最初に入力するときに、イテレーションの数を決定します。

## <a name="nesting-loops"></a>ループの入れ子

ループを入れ子`For`にするには、ループを別のループ内に配置します。 入れ子になっ`For`たの例を次に示します。`Next`異なるステップ値を持つ構造体。 外側のループは、ループの反復ごとに文字列を作成します。 内側のループは、ループの反復ごとにループカウンター変数をデクリメントします。

[!code-vb[VbVbalrStatements#113](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#113)]

ループを入れ子にする場合、各ループは`counter`一意の変数を持つ必要があります。

さまざまな種類の制御構造を入れ子にすることもできます。 詳細については、[入れ子になった制御構造](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md) を参照してください。

## <a name="exit-for-and-continue-for"></a>Exit For と Continue For

ステートメント`Exit For`は、 `For`すぐに...`Next` ループし、 `Next`ステートメントの後のステートメントに制御を転送します。

ステートメント`Continue For`は、ループの次の反復処理に制御を直ちに転送します。 詳細については、「 [Continue ステートメント](../../../visual-basic/language-reference/statements/continue-statement.md)」を参照してください。

次の例は、ステートメント`Continue For`と`Exit For`ステートメントの使用方法を示しています。

[!code-vb[VbVbalrStatements#115](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#115)]

には、 `For`任意の数`Exit For`のステートメントを含めることができます...`Next` ループ. 入れ子になっ`For`た... 内で使用された場合`Next` ループし`Exit For` 、最も内側のループを終了して、次の上位レベルの入れ子に制御を転送します。

`Exit For` は何らかの条件 (たとえば、 `If`...`Then`...`Else`構造) を評価した後によく使用されます。 次の条件の場合、`Exit For`を使用できます。

- 反復処理を続行することは不要または不可能です。 この条件は、エラー値または終了要求によって作成できます。

- `Try`...`Catch`...`Finally`ステートメントは例外をキャッチします。 `Finally`ブロックの最後に`Exit For`を使用できます。

- 無限ループがあります。これは、大規模または無限の回数実行されるループです。 このような条件を検出した場合は`Exit For`を使用してループをエスケープすることができます。 詳細については、[Do...Loop ステートメント](../../../visual-basic/language-reference/statements/do-loop-statement.md)を参照してください。

## <a name="technical-implementation"></a>技術的な実装

`For`When...ループが開始され、 `end`Visual Basic が`step`、、およびを評価`start`します。 `Next` Visual Basic は、現時点ではこれらの値のみを`start`評価`counter`し、にを割り当てます。 ステートメントブロックが実行される前に`counter` 、 `end`Visual Basic はと比較されます。 が`counter`既に`end`値より大きい (またはが負`step`の場合は小さい) `For`場合、 `Next`ループは終了し、ステートメントの後のステートメントに制御が移ります。 それ以外の場合は、ステートメントブロックが実行されます。

Visual Basic が`Next`ステートメントを検出するたびに、 `counter` `For`に`step`よってインクリメントされ、ステートメントに戻ります。 ここでも`counter`と`end`を比較し、その結果に応じてブロックを実行するか、ループを終了します。 このプロセスは、 `counter`が`end`成功する`Exit For`か、ステートメントが検出されるまで続行されます。

が渡さ`counter` `end`れるまで、ループは停止しません。 が`counter` に`end`等しい場合、ループは続行されます。 `step`が正で、 `end`  <=  `counter` が負`counter`である場合に、ブロックを実行するかどうかを決定する比較。  >=  `end` `step`

ループ内での`counter`値を変更すると、コードの読み取りやデバッグが困難になることがあります。 、 `start` `step` 、またはの値を変更しても、ループが最初に入力されたときに決定された反復値には影響しません。 `end`

ループを入れ子にした場合、内部レベルの`Next` `Next`ステートメントの前に外側の入れ子レベルのステートメントが検出されると、コンパイラはエラーを通知します。 ただし、コンパイラは、すべて`counter` `Next`のステートメントでを指定した場合にのみ、この重複エラーを検出できます。

### <a name="step-argument"></a>ステップ引数

の値に`step`は、正または負のどちらかを指定できます。 このパラメーターは、次の表に従ってループ処理を決定します。

|**ステップ値**|**ループが実行される場合**|
|--------------------|--------------------------|
|正または0|`counter` <= `end`|
|負|`counter` >= `end`|

の`step`既定値は1です。

### <a name="BKMK_Counter"></a>Counter 引数

次の表は、 `counter`がループ全体`For…Next`を対象とする新しいローカル変数を定義するかどうかを示しています。 この決定は`counter` 、が`datatype`存在し、が既に定義されているかどうかによって異なります。

|存在`datatype`していますか?|は`counter`既に定義されていますか?|Result (に`counter`よって、ループ全体`For...Next`を対象とする新しいローカル変数が定義されているかどうか)|
|----------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------|
|いいえ|[はい]|いいえ。は既に定義されています。 `counter` のスコープがプロシージャ`counter`に対してローカルでない場合は、コンパイル時の警告が発生します。|
|いいえ|いいえ|はい。 データ型は`start`、 `end`、、および`step`の各式から推論されます。 型の推定の詳細については、「[オプション推論ステートメント](../../../visual-basic/language-reference/statements/option-infer-statement.md)と[ローカル型の推論](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)」を参照してください。|
|[はい]|[はい]|はい。ただし、既存`counter`の変数がプロシージャの外部で定義されている場合に限ります。 この変数は個別に保持されます。 既存`counter`の変数のスコープがプロシージャに対してローカルである場合は、コンパイル時エラーが発生します。|
|[はい]|いいえ|はい。|

の`counter`データ型によって、反復処理の種類が決まります。次のいずれかの型である必要があります。

- `Byte` `SByte` `UShort` `Short` 、、`Double`、、、、、、、、または。 `UInteger` `Integer` `ULong` `Long` `Decimal` `Single`

- [Enum ステートメント](../../../visual-basic/language-reference/statements/enum-statement.md)を使用して宣言する列挙体。

- `Object`。

- 次の`T`演算子`B`を持つ型。は、 `Boolean`式で使用できる型です。

  `Public Shared Operator >= (op1 As T, op2 As T) As B`

  `Public Shared Operator <= (op1 As T, op2 As T) As B`

  `Public Shared Operator - (op1 As T, op2 As T) As T`

  `Public Shared Operator + (op1 As T, op2 As T) As T`

`counter` 必要`Next`に応じて、ステートメントで変数を指定できます。 この構文を使用すると、特に入れ子になっ`For`たループがある場合に、プログラムの読みやすさが向上します。 対応`For`するステートメントに表示される変数を指定する必要があります。

、 `start` 、`end`および`counter`の各式は、の型に拡大変換される任意のデータ型に評価されます。 `step` `counter`にユーザー定義型を使用する場合は、、 `end`、または`step`の`start`型`CType`をの`counter`型に変換するために、変換演算子を定義することが必要になる場合があります。

## <a name="example"></a>例

次の例では、ジェネリックリストからすべての要素を削除します。 この例では、[For Each...Next ステートメント](../../../visual-basic/language-reference/statements/for-each-next-statement.md)の代わりに、降順に反復処理する`For`...`Next`ステートメントを使用します。 例では、`removeAt`メソッドで削除された要素の後にある要素のインデックス値がより小さくなるため、この手法を使用します。

[!code-vb[VbVbalrStatements#114](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#114)]

## <a name="example"></a>例

次の例では、列挙[ステートメント](../../../visual-basic/language-reference/statements/enum-statement.md)を使用して宣言された列挙型を反復処理します。

[!code-vb[VbVbalrStatements#116](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#116)]

## <a name="example"></a>例

次の例では、ステートメントの`+`パラメーターは`>=`、、 `-`、、および`<=`の各演算子に対して演算子のオーバーロードを持つクラスを使用しています。

[!code-vb[VbVbalrStatements#117](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class7.vb#117)]

## <a name="see-also"></a>関連項目

- <xref:System.Collections.Generic.List%601>
- [ループ構造](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [While...End While ステートメント](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [Do...Loop ステートメント](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [入れ子になった制御構造](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Exit ステートメント](../../../visual-basic/language-reference/statements/exit-statement.md)
- [コレクション](../../programming-guide/concepts/collections.md)
