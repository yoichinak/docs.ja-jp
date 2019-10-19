---
title: Function ステートメント (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Function
helpviewer_keywords:
- procedures [Visual Basic], creating
- Function procedures [Visual Basic], Function statement syntax
- functions [Visual Basic], function procedures
- ParamArray keyword [Visual Basic], Function statements
- Private keyword [Visual Basic], Function statements
- declarations [Visual Basic], procedures
- procedures [Visual Basic], declaration
- Public keyword [Visual Basic], in Function statement
- ByVal keyword [Visual Basic], Function statements
- procedures [Visual Basic], recursive
- Implements keyword [Visual Basic], Function statements
- procedures [Visual Basic], returning values
- Exit statement [Visual Basic], in Function procedures
- recursive procedures
- As keyword [Visual Basic], in Function statement
- Optional keyword [Visual Basic], Function statements
- Function statement [Visual Basic]
- Visual Basic code, Function procedures
- procedures [Visual Basic], function
- ByRef keyword [Visual Basic], Function statements
- Friend keyword [Visual Basic], Function statements
- End keyword [Visual Basic], Function statements
- Handles keyword [Visual Basic], Function statements
ms.assetid: a4497077-0f46-4ede-a27f-9e8670df52b9
ms.openlocfilehash: 046a3a7d50d15cd3e59205998554a4c330d4552c
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581848"
---
# <a name="function-statement-visual-basic"></a>Function ステートメント (Visual Basic)

@No__t_0 プロシージャを定義する名前、パラメーター、およびコードを宣言します。

## <a name="syntax"></a>構文

```vb
[ <attributelist> ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async | Iterator ]
Function name [ (Of typeparamlist) ] [ (parameterlist) ] [ As returntype ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Function ]
    [ statements ]
End Function
```

## <a name="parts"></a>指定項目

- `attributelist`

  省略可能です。 「[属性リスト](attribute-list.md)」を参照してください。

- `accessmodifier`

  省略可能です。 次のいずれかの値を指定します。

  - [Public](../../../visual-basic/language-reference/modifiers/public.md)

  - [Protected](../../../visual-basic/language-reference/modifiers/protected.md)

  - [Friend](../../../visual-basic/language-reference/modifiers/friend.md)

  - [Private](../../../visual-basic/language-reference/modifiers/private.md)

  - [Protected Friend](../../language-reference/modifiers/protected-friend.md)

  - [Private Protected](../../language-reference/modifiers/private-protected.md)

  「 [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。

- `proceduremodifiers`

  省略可能です。 次のいずれかの値を指定します。

  - [オーバーロード](../../../visual-basic/language-reference/modifiers/overloads.md)

  - [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)

  - [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)

  - [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)

  - [New](../../../visual-basic/language-reference/modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  省略可能です。 「[共有](../../../visual-basic/language-reference/modifiers/shared.md)」を参照してください。

- `Shadows`

  省略可能です。 「[シャドウ](../../../visual-basic/language-reference/modifiers/shadows.md)」を参照してください。

- `Async`

  省略可能です。 「 [Async](../../../visual-basic/language-reference/modifiers/async.md)」を参照してください。

- `Iterator`

  省略可能です。 「[反復子](../../../visual-basic/language-reference/modifiers/iterator.md)」を参照してください。

- `name`

  必須です。 プロシージャの名前。 「 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。

- `typeparamlist`

  省略可能です。 ジェネリックプロシージャの型パラメーターのリスト。 [型リスト](type-list.md)を参照してください。

- `parameterlist`

  省略可能です。 このプロシージャのパラメーターを表すローカル変数名の一覧。 「[パラメーターリスト](parameter-list.md)」を参照してください。

- `returntype`

  @No__t_0 が `On` の場合は必須です。 このプロシージャによって返される値のデータ型。

- `Implements`

  省略可能です。 このプロシージャが1つ以上の `Function` プロシージャを実装することを示します。各プロシージャは、このプロシージャのクラスまたは構造体を含むインターフェイスで定義されています。 「 [Implements ステートメント](implements-statement.md)」を参照してください。

- `implementslist`

  `Implements` を指定する場合は、必ず指定します。 実装される `Function` プロシージャのリストです。

  `implementedprocedure [ , implementedprocedure ... ]`

  `implementedprocedure` の構文と指定項目は次のとおりです。

  `interface.definedname`

  |パーツ|説明|
  |---|---|
  |`interface`|必須です。 このプロシージャのクラスまたは構造体によって実装されるインターフェイスの名前。|
  |`definedname`|必須です。 `interface` の中でプロシージャを定義するために使用する名前。|

- `Handles`

  省略可能です。 このプロシージャが1つ以上の特定のイベントを処理できることを示します。 「[ハンドル](handles-clause.md)」を参照してください。

- `eventlist`

  `Handles` を指定する場合は、必ず指定します。 このプロシージャが処理するイベントの一覧です。

  `eventspecifier [ , eventspecifier ... ]`

  `eventspecifier` の構文と指定項目は次のとおりです。

  `eventvariable.event`

  |パーツ|説明|
  |---|---|
  |`eventvariable`|必須です。 イベントを発生させるクラスまたは構造体のデータ型で宣言されたオブジェクト変数。|
  |`event`|必須です。 このプロシージャが処理するイベントの名前。|

- `statements`

  省略可能です。 このプロシージャ内で実行されるステートメントのブロック。

- `End Function`

  このプロシージャの定義を終了します。

## <a name="remarks"></a>Remarks

すべての実行可能コードは、プロシージャ内になければなりません。 各プロシージャは、クラス、構造体、またはそれを含んでいるクラス、構造体、またはモジュールと呼ばれるモジュール内で宣言されます。

呼び出し元のコードに値を返すには、`Function` プロシージャを使用します。それ以外の場合は、`Sub` プロシージャを使用します。

## <a name="defining-a-function"></a>関数の定義

@No__t_0 プロシージャは、モジュールレベルでのみ定義できます。 したがって、関数の宣言コンテキストは、クラス、構造体、モジュール、またはインターフェイスである必要があり、ソースファイル、名前空間、プロシージャ、またはブロックにすることはできません。 詳細については、「[宣言コンテキストと既定のアクセス レベル](declaration-contexts-and-default-access-levels.md)」を参照してください。

`Function` プロシージャは、既定でパブリックアクセスになります。 アクセス修飾子を使用してこれらのアクセス レベルを調整できます。

@No__t_0 プロシージャでは、プロシージャが返す値のデータ型を宣言できます。 任意のデータ型を指定することも、列挙体、構造体、クラス、またはインターフェイスの名前を指定することもできます。 @No__t_0 パラメーターを指定しない場合、プロシージャは `Object` を返します。

このプロシージャで `Implements` キーワードを使用する場合、含まれるクラスまたは構造体には、その `Class` または `Structure` ステートメントの直後にある `Implements` ステートメントも含まれている必要があります。 @No__t_0 ステートメントには、`implementslist` で指定されている各インターフェイスを含める必要があります。 ただし、インターフェイスが `Function` (`definedname`) を定義する際には、このプロシージャの名前 (`name`) と一致する必要はありません。

> [!NOTE]
> ラムダ式を使用して、関数式をインラインで定義できます。 詳細については、「[関数式](../../../visual-basic/language-reference/operators/function-expression.md)」および「[ラムダ式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)」を参照してください。

## <a name="returning-from-a-function"></a>関数からの戻り

@No__t_0 プロシージャが呼び出し元のコードに戻ると、プロシージャを呼び出したステートメントの後のステートメントで実行が続行されます。

関数から値を返すには、関数名に値を割り当てるか、`Return` ステートメントに値を含めることができます。

次の例に示すように、`Return` ステートメントは、戻り値を同時に割り当てて関数を終了します。

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

次の例では、関数名 `myFunction` に戻り値を代入し、`Exit Function` ステートメントを使用してを返します。

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

@No__t_0 ステートメントおよび `Return` ステートメントを行うと、`Function` プロシージャからすぐに終了します。 プロシージャ内の任意の場所で任意の数の `Exit Function` および `Return` ステートメントを使用できます。また、`Exit Function` と `Return` のステートメントを混在させることができます。

@No__t_1 に値を割り当てずに `Exit Function` を使用する場合、プロシージャは `returntype` で指定されたデータ型の既定値を返します。 @No__t_0 が指定されていない場合、プロシージャは `Nothing` を返します。これは `Object` の既定値です。

## <a name="calling-a-function"></a>関数の呼び出し

@No__t_0 プロシージャを呼び出すには、式の中でプロシージャ名の後にかっこで囲んだ引数リストを使用します。 かっこを省略できるのは、引数を指定しない場合のみです。 ただし、常にかっこを含めると、コードが読みやすくなります。

@No__t_0 プロシージャは、`Sqrt`、`Cos`、`ChrW` などのライブラリ関数を呼び出すのと同じ方法で呼び出すことができます。

@No__t_0 キーワードを使用して関数を呼び出すこともできます。 その場合、戻り値は無視されます。 ほとんどの場合、`Call` キーワードの使用は推奨されていません。 詳細については、「 [Call ステートメント](call-statement.md)」を参照してください。

Visual Basic は、内部効率を向上させるために算術式を再配置することがあります。 そのため、関数が同じ式の変数の値を変更する場合は、算術式で `Function` プロシージャを使用しないでください。

## <a name="async-functions"></a>非同期関数

非同期*機能を*使用すると、明示的なコールバックを使用したり、複数の関数やラムダ式に手動でコードを分割したりすることなく、非同期関数を呼び出すことができます。

関数に[Async](../../../visual-basic/language-reference/modifiers/async.md)修飾子を指定した場合は、関数で[Await](../../../visual-basic/language-reference/operators/await-operator.md)演算子を使用できます。 コントロールが `Async` 関数の `Await` 式に到達すると、コントロールは呼び出し元に戻り、待機中のタスクが完了するまで、関数の進行状況は中断されます。 タスクが完了すると、関数で実行が再開されます。

> [!NOTE]
> @No__t_0 プロシージャは、まだ完了していない最初の待機中のオブジェクトが検出されたとき、または `Async` プロシージャの最後に到達したときに、呼び出し元に返されます。

@No__t_0 関数は、<xref:System.Threading.Tasks.Task%601> または <xref:System.Threading.Tasks.Task> の戻り値の型を持つことができます。 戻り値の型が <xref:System.Threading.Tasks.Task%601> の `Async` 関数の例を次に示します。

@No__t_0 関数で[ByRef](../../../visual-basic/language-reference/modifiers/byref.md)パラメーターを宣言することはできません。

[Sub ステートメント](sub-statement.md)を `Async` 修飾子でマークすることもできます。 これは主に、値を返すことができないイベントハンドラーに使用されます。 @No__t_0 `Sub` プロシージャは待機できません。また、`Async` の `Sub` プロシージャの呼び出し元は、`Sub` プロシージャによってスローされた例外をキャッチできません。

@No__t_0 関数の詳細については、「 [async および Await を使用した非同期プログラミング](../../../visual-basic/programming-guide/concepts/async/index.md)」、「非同期[プログラムでの制御フロー](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)」、および「非同期の[戻り値の型](../../../visual-basic/programming-guide/concepts/async/async-return-types.md)」を参照してください。

## <a name="iterator-functions"></a>Iterator 関数

*反復子*関数は、リストや配列などのコレクションに対してカスタムの反復処理を実行します。 Iterator 関数は[Yield](yield-statement.md)ステートメントを使用して、各要素を1回に1つ返します。 [Yield](yield-statement.md)ステートメントに到達すると、コード内の現在の場所が記憶されます。 次回、iterator 関数が呼び出されると、この位置から実行が再開されます。

For Each を使用して、クライアントコードから反復子を呼び出します。 [次](for-each-next-statement.md)のステートメント。

反復子関数の戻り値の型には、<xref:System.Collections.IEnumerable>、<xref:System.Collections.Generic.IEnumerable%601>、<xref:System.Collections.IEnumerator>、または <xref:System.Collections.Generic.IEnumerator%601> を指定できます。

詳細については、「[反復子](../../programming-guide/concepts/iterators.md)」をご覧ください。

## <a name="example"></a>例

次の例では、`Function` ステートメントを使用して、`Function` プロシージャの本体を形成する名前、パラメーター、およびコードを宣言します。 @No__t_0 修飾子を使用すると、関数は可変個の引数を受け取ることができます。

[!code-vb[VbVbalrStatements#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#25)]

## <a name="example"></a>例

次の例では、前の例で宣言した関数を呼び出します。

[!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]

## <a name="example"></a>例

次の例では、`DelayAsync` は、戻り値の型が <xref:System.Threading.Tasks.Task%601> の `Async` `Function` です。 `DelayAsync` には、整数を返す `Return` ステートメントがあります。 したがって、`DelayAsync` の関数宣言は、戻り値の型 `Task(Of Integer)` である必要があります。 戻り値の型が `Task(Of Integer)` ので、`DoSomethingAsync` 内の `Await` 式の評価では整数が生成されます。 これについては、次のステートメントを `Dim result As Integer = Await delayTask` ます。

@No__t_0 プロシージャは、`Async Sub` プロシージャの一例です。 @No__t_0 は `Async` 関数であるため、次のステートメントで示すように、`DoSomethingAsync` を呼び出すためのタスクを待機する必要があります。 `Await DoSomethingAsync()`。 @No__t_0 `Sub` プロシージャには `Await` 式があるため、`Async` 修飾子を使用して定義する必要があります。

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a>関連項目

- [Sub ステートメント](sub-statement.md)
- [Function プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)
- [パラメーター リスト](parameter-list.md)
- [Dim ステートメント](dim-statement.md)
- [Call ステートメント](call-statement.md)
- [Of](of-clause.md)
- [パラメーター配列](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
- [方法 : ジェネリック クラスを使用する](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [プロシージャのトラブルシューティング](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [ラムダ式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Function 式](../../../visual-basic/language-reference/operators/function-expression.md)
