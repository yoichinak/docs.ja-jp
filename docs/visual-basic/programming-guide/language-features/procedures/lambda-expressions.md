---
title: ラムダ式
ms.date: 07/20/2015
f1_keywords:
- vb.LambdaFunction
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
ms.openlocfilehash: 1827eb5630ed217527de25fc9d9c2bb8994b9aff
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249670"
---
# <a name="lambda-expressions-visual-basic"></a>ラムダ式 (Visual Basic)

*ラムダ式*は、デリゲートが有効な場所であれば、名前のない関数またはサブルーチンです。 ラムダ式は、関数またはサブルーチンで、単一行または複数行の場合があります。 現在のスコープからラムダ式に値を渡すことができます。

> [!NOTE]
> この`RemoveHandler`ステートメントは例外です。 のデリゲート パラメーターにラムダ式を 渡すことはできません`RemoveHandler`。

ラムダ式は、標準の`Function`関数`Sub`またはサブルーチンを作成するのと同じように、 or キーワードを使用して作成します。 ただし、ラムダ式はステートメントに含まれます。

次の例は、引数をインクリメントして値を返すラムダ式です。 この例では、関数の単一行と複数行のラムダ式の構文の両方を示します。

[!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]

次の例は、コンソールに値を書き込むラムダ式です。 この例では、サブルーチンの単一行と複数行のラムダ式の構文の両方を示しています。

[!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]

前の例では、ラムダ式が変数名に割り当てられていることに注意してください。 変数を参照するたびに、ラムダ式を呼び出します。 次の例に示すように、ラムダ式を同時に宣言して呼び出すこともできます。

[!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]

ラムダ式は、関数呼び出しの値として返されるか (このトピックの後の[「Context」](#context)セクションの例で示されているように)、デリゲート型を受け取るパラメーターに引数として渡されます。

[!code-vb[VbVbalrLambdas#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class2.vb#8)]

## <a name="lambda-expression-syntax"></a>ラムダ式の構文

ラムダ式の構文は、標準関数またはサブルーチンの構文に似ています。 相違点は、次のとおりです。

- ラムダ式に名前がありません。

- ラムダ式には、 や`Overloads``Overrides`などの修飾子を指定できません。

- 単一行のラムダ関数では、`As`戻り値の型を指定する句は使用しません。 その代わりに、ラムダ式の本体が評価する値から型が推論されます。 たとえば、ラムダ式の本体が の場合`cust.City = "London"`、その戻り値`Boolean`の型は です。

- 複数行のラムダ関数では、句を使用して戻り値の型`As`を指定するか、または`As`戻り値の型が推論されるように句を省略できます。 複数行`As`のラムダ関数に対して句を省略すると、戻り値の型は、複数行のラムダ関数のすべての`Return`ステートメントから主要な型であると推論されます。 *ドミナント型*は、他のすべての型が拡大できる一意の型です。 この一意の型を決定できない場合、主要な型は、配列内の他のすべての型が絞り込むことができる一意の型になります。 これらの一意の型をどちらも特定できない場合は、 `Object`が最も優先度の高い型になります。 この場合、に設定`Option Strict``On`されている場合は、コンパイラ エラーが発生します。

     たとえば、ステートメントに指定された`Return`式に 、 `Integer` `Long`、 、および`Double`の値が含まれている場合、結果`Double`の配列は型 です。 両方`Integer`に`Long`広く`Double`、そして`Double`唯一. そのため、 `Double` が最も優先度の高い型になります。 詳細については、「 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)」を参照してください。

- 単一行関数の本体は、ステートメントではなく値を返す式である必要があります。 単一行`Return`関数のステートメントはありません。 単一行関数によって返される値は、関数本体の式の値です。

- 単一行のサブルーチンの本体は、単一行のステートメントでなければなりません。

- 単一行の関数およびサブルーチンには、 または`End Function``End Sub`ステートメントは含まれません。

- `As`ラムダ式パラメーターのデータ型は、キーワードを使用して指定するか、パラメーターのデータ型を推論できます。 すべてのパラメーターにデータ型を指定するか、またはすべて推論する必要があります。

- `Optional`および`Paramarray`パラメーターは許可されません。

- ジェネリック パラメーターは使用できません。

## <a name="async-lambdas"></a>非同期ラムダ

[非同期](../../../../visual-basic/language-reference/modifiers/async.md)演算子キーワードと[Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md)キーワードを使用すると、非同期処理を組み込んだラムダ式とステートメントを簡単に作成できます。 たとえば、次に示す Windows フォーム例には、非同期メソッド `ExampleMethodAsync`を呼び出して待機するイベント ハンドラーが含まれています。

```vb
Public Class Form1

    Async Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click
        ' ExampleMethodAsync returns a Task.
        Await ExampleMethodAsync()
        TextBox1.Text = vbCrLf & "Control returned to button1_Click."
    End Sub

    Async Function ExampleMethodAsync() As Task
        ' The following line simulates a task-returning asynchronous process.
        Await Task.Delay(1000)
    End Function

End Class
```

[AddHandler ステートメント](../../../../visual-basic/language-reference/statements/addhandler-statement.md)で非同期ラムダを使用して、同じイベント ハンドラーを追加できます。 次の例に示すように、このハンドラーを追加するには、ラムダ パラメーター リストの前に `Async` 修飾子を追加します。

```vb
Public Class Form1

    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load
        AddHandler Button1.Click,
            Async Sub(sender1, e1)
                ' ExampleMethodAsync returns a Task.
                Await ExampleMethodAsync()
                TextBox1.Text = vbCrLf & "Control returned to Button1_ Click."
            End Sub
    End Sub

    Async Function ExampleMethodAsync() As Task
        ' The following line simulates a task-returning asynchronous process.
        Await Task.Delay(1000)
    End Function

End Class
```

非同期メソッドの作成方法と使用方法の詳細については、「[非同期と Await を使用した非同期プログラミング](../../../../visual-basic/programming-guide/concepts/async/index.md)」を参照してください。

## <a name="context"></a>Context

ラムダ式は、そのコンテキストを定義されているスコープと共有します。 このオブジェクトには、包含スコープで記述されたコードと同じアクセス権があります。 これには、メンバー変数、関数とサブ、および`Me`パラメーター、および、そのスコープ内のローカル変数へのアクセスが含まれます。

格納スコープ内のローカル変数およびパラメーターへのアクセスは、そのスコープの有効期間を超えて拡張できます。 ラムダ式を参照するデリゲートがガベージ コレクションで使用できない限り、元の環境の変数へのアクセスは保持されます。 次の例では、ラム`target`ダ式`playTheGame`が`makeTheGame`定義されているメソッドに対して変数がローカルになります。 返されたラムダ式は、`takeAGuess`に`Main`割り当てられ、依然としてローカル変数`target`にアクセスできます。

[!code-vb[VbVbalrLambdas#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class6.vb#12)]

入れ子になったラムダ式のアクセス権の範囲を示す例を次に示します。 返されたラムダ式が`Main``aDel`から実行されると、 は、次の要素にアクセスします。

- 定義されているクラスのフィールド。`aField`

- 定義されているクラスのプロパティ。`aProp`

- 定義されているメソッド`functionWithNestedLambda`のパラメータ:`level1`

- のローカル変数`functionWithNestedLambda`。`localVar`

- 入れ子になっているラムダ式のパラメータ。`level2`

 [!code-vb[VbVbalrLambdas#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class3.vb#9)]

## <a name="converting-to-a-delegate-type"></a>デリゲート型への変換

ラムダ式は、互換性のあるデリゲート型に暗黙的に変換できます。 互換性の一般的な要件については、「[デリゲート変換の緩和](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)」を参照してください。 たとえば、次のコード例は、暗黙的にデリゲートシグネチャに`Func(Of Integer, Boolean)`変換するラムダ式または一致するデリゲート シグネチャを示しています。

[!code-vb[VbVbalrLambdas#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#16)]

次のコード例は、暗黙的に変換するラムダ式`Sub(Of Double, String, Double)`、または一致するデリゲート シグネチャを示しています。

[!code-vb[VbVbalrLambdas#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/class7.vb#23)]

ラムダ式をデリゲートに割り当てたり、プロシージャに引数として渡したりするときには、パラメーター名を指定できますが、そのデータ型を省略して、デリゲートから型を取得できます。

## <a name="examples"></a>例

- 次の例では、null 許容値`True`型引数に値が割り当てられている場合、およびその`False`値が の場合`Nothing`に返すラムダ式を定義します。

     [!code-vb[VbVbalrLambdas#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#4)]

- 次の例では、配列の最後の要素のインデックスを返すラムダ式を定義します。

     [!code-vb[VbVbalrLambdas#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#5)]

## <a name="see-also"></a>関連項目

- [プロシージャ](./index.md)
- [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [デリゲート](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Function ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub ステートメント](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [null 許容値型](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [方法 : Visual Basic でプロシージャを別のプロシージャに渡す](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [方法: ラムダ式を作成する](./how-to-create-a-lambda-expression.md)
- [厳密でないデリゲート変換](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
