---
title: Function ステートメント
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
ms.openlocfilehash: 8140c7e6267e66c69c20d413a11d04372400c581
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345919"
---
# <a name="function-statement-visual-basic"></a>Function ステートメント (Visual Basic)

Declares the name, parameters, and code that define a `Function` procedure.

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

  省略可能です。 See [Attribute List](attribute-list.md).

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

  省略可能です。 See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).

- `Shadows`

  省略可能です。 See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).

- `Async`

  省略可能です。 See [Async](../../../visual-basic/language-reference/modifiers/async.md).

- `Iterator`

  省略可能です。 See [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).

- `name`

  必須です。 Name of the procedure. 「 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。

- `typeparamlist`

  省略可能です。 List of type parameters for a generic procedure. See [Type List](type-list.md).

- `parameterlist`

  省略可能です。 List of local variable names representing the parameters of this procedure. See [Parameter List](parameter-list.md).

- `returntype`

  Required if `Option Strict` is `On`. Data type of the value returned by this procedure.

- `Implements`

  省略可能です。 Indicates that this procedure implements one or more `Function` procedures, each one defined in an interface implemented by this procedure's containing class or structure. See [Implements Statement](implements-statement.md).

- `implementslist`

  `Implements` を指定する場合は、必ず指定します。 実装される `Function` プロシージャのリストです。

  `implementedprocedure [ , implementedprocedure ... ]`

  `implementedprocedure` の構文と指定項目は次のとおりです。

  `interface.definedname`

  |パーツ|説明|
  |---|---|
  |`interface`|必須です。 Name of an interface implemented by this procedure's containing class or structure.|
  |`definedname`|必須です。 `interface` の中でプロシージャを定義するために使用する名前。|

- `Handles`

  省略可能です。 Indicates that this procedure can handle one or more specific events. See [Handles](handles-clause.md).

- `eventlist`

  `Handles` を指定する場合は、必ず指定します。 List of events this procedure handles.

  `eventspecifier [ , eventspecifier ... ]`

  `eventspecifier` の構文と指定項目は次のとおりです。

  `eventvariable.event`

  |パーツ|説明|
  |---|---|
  |`eventvariable`|必須です。 Object variable declared with the data type of the class or structure that raises the event.|
  |`event`|必須です。 Name of the event this procedure handles.|

- `statements`

  省略可能です。 Block of statements to be executed within this procedure.

- `End Function`

  Terminates the definition of this procedure.

## <a name="remarks"></a>Remarks

All executable code must be inside a procedure. Each procedure, in turn, is declared within a class, a structure, or a module that is referred to as the containing class, structure, or module.

To return a value to the calling code, use a `Function` procedure; otherwise, use a `Sub` procedure.

## <a name="defining-a-function"></a>Defining a Function

You can define a `Function` procedure only at the module level. Therefore, the declaration context for a function must be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block. 詳細については、「[宣言コンテキストと既定のアクセス レベル](declaration-contexts-and-default-access-levels.md)」を参照してください。

`Function` procedures default to public access. アクセス修飾子を使用してこれらのアクセス レベルを調整できます。

A `Function` procedure can declare the data type of the value that the procedure returns. You can specify any data type or the name of an enumeration, a structure, a class, or an interface. If you don't specify the `returntype` parameter, the procedure returns `Object`.

If this procedure uses the `Implements` keyword, the containing class or structure must also have an `Implements` statement that immediately follows its `Class` or `Structure` statement. The `Implements` statement must include each interface that's specified in `implementslist`. However, the name by which an interface defines the `Function` (in `definedname`) doesn't need to match the name of this procedure (in `name`).

> [!NOTE]
> You can use lambda expressions to define function expressions inline. For more information, see [Function Expression](../../../visual-basic/language-reference/operators/function-expression.md) and [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).

## <a name="returning-from-a-function"></a>Returning from a Function

When the `Function` procedure returns to the calling code, execution continues with the statement that follows the statement that called the procedure.

To return a value from a function, you can either assign the value to the function name or include it in a `Return` statement.

The `Return` statement simultaneously assigns the return value and exits the function, as the following example shows.

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

The following example assigns the return value to the function name `myFunction` and then uses the `Exit Function` statement to return.

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

The `Exit Function` and `Return` statements cause an immediate exit from a `Function` procedure. Any number of `Exit Function` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Function` and `Return` statements.

If you use `Exit Function` without assigning a value to `name`, the procedure returns the default value for the data type that's specified in `returntype`. If `returntype` isn't specified, the procedure returns `Nothing`, which is the default value for `Object`.

## <a name="calling-a-function"></a>関数の呼び出し

You call a `Function` procedure by using the procedure name, followed by the argument list in parentheses, in an expression. You can omit the parentheses only if you aren't supplying any arguments. However, your code is more readable if you always include the parentheses.

You call a `Function` procedure the same way that you call any library function such as `Sqrt`, `Cos`, or `ChrW`.

You can also call a function by using the `Call` keyword. In that case, the return value is ignored. Use of the `Call` keyword isn't recommended in most cases. For more information, see [Call Statement](call-statement.md).

Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency. For that reason, you shouldn't use a `Function` procedure in an arithmetic expression when the function changes the value of variables in the same expression.

## <a name="async-functions"></a>Async Functions

The *Async* feature allows you to invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.

If you mark a function with the [Async](../../../visual-basic/language-reference/modifiers/async.md) modifier, you can use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in the function. When control reaches an `Await` expression in the `Async` function, control returns to the caller, and progress in the function is suspended until the awaited task completes. When the task is complete, execution can resume in the function.

> [!NOTE]
> An `Async` procedure returns to the caller when either it encounters the first awaited object that’s not yet complete, or it gets to the end of the `Async` procedure, whichever occurs first.

An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>. An example of an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601> is provided below.

An `Async` function cannot declare any [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parameters.

A [Sub Statement](sub-statement.md) can also be marked with the `Async` modifier. This is primarily used for event handlers, where a value cannot be returned. An `Async` `Sub` procedure can't be awaited, and the caller of an `Async` `Sub` procedure can't catch exceptions that are thrown by the `Sub` procedure.

For more information about `Async` functions, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).

## <a name="iterator-functions"></a>Iterator Functions

An *iterator* function performs a custom iteration over a collection, such as a list or array. An iterator function uses the [Yield](yield-statement.md) statement to return each element one at a time. When a [Yield](yield-statement.md) statement is reached, the current location in code is remembered. 次回、iterator 関数が呼び出されると、この位置から実行が再開されます。

You call an iterator from client code by using a [For Each…Next](for-each-next-statement.md) statement.

The return type of an iterator function can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.

詳細については、「[反復子](../../programming-guide/concepts/iterators.md)」をご覧ください。

## <a name="example"></a>例

The following example uses the `Function` statement to declare the name, parameters, and code that form the body of a `Function` procedure. The `ParamArray` modifier enables the function to accept a variable number of arguments.

[!code-vb[VbVbalrStatements#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#25)]

## <a name="example"></a>例

The following example invokes the function declared in the preceding example.

[!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]

## <a name="example"></a>例

In the following example, `DelayAsync` is an `Async` `Function` that has a return type of <xref:System.Threading.Tasks.Task%601>. `DelayAsync` には、整数を返す `Return` ステートメントがあります。 Therefore the function declaration of `DelayAsync` needs to have a return type of `Task(Of Integer)`. Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer. This is demonstrated in this statement: `Dim result As Integer = Await delayTask`.

The `startButton_Click` procedure is an example of an `Async Sub` procedure. Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement demonstrates: `Await DoSomethingAsync()`. The `startButton_Click` `Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.

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
