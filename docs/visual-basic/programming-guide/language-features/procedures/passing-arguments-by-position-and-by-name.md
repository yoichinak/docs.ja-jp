---
title: 位置と名前による引数渡し
ms.date: 02/01/2018
helpviewer_keywords:
- arguments [Visual Basic], passing by name
- procedures [Visual Basic], arguments
- := passing arguments
- procedure arguments
- Visual Basic code, procedures
- named arguments [Visual Basic], passing arguments
- arguments [Visual Basic], passing by position
- Function procedures [Visual Basic], passing arguments
- named parameters [Visual Basic], passing arguments
- named arguments
- passing parameters [Visual Basic], named parameter arguments
- passing parameters [Visual Basic], by position
- procedures [Visual Basic], calling
- named parameters
- Sub procedures [Visual Basic], passing arguments
- argument passing
- passing parameters [Visual Basic], by name
- argument passing [Visual Basic], by position
- arguments [Visual Basic], listing by name
ms.assetid: 1ad7358f-1da9-48da-a95b-f3c7ed41eff3
ms.openlocfilehash: b6588335f7634cc87a9fc14cbfc4ba80baad1abb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352618"
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a>位置と名前による引数渡し (Visual Basic)

When you call a `Sub` or `Function` procedure, you can pass arguments *by position* — in the order in which they appear in the procedure's definition — or you can pass them *by name*, without regard to position.

When you pass an argument by name, you specify the argument's declared name followed by a colon and an equal sign (`:=`), followed by the argument value. You can supply named arguments in any order.

For example, the following `Sub` procedure takes three arguments:

[!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]

When you call this procedure, you can supply the arguments by position, by name, or by using a mixture of both.

## <a name="passing-arguments-by-position"></a>Passing Arguments by Position

You can call the `Display` method with its arguments passed by position and delimited by commas, as shown in the following example:

[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)]

If you omit an optional argument in a positional argument list, you must hold its place with a comma. The following example calls the `Display` method without the `age` argument:

[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)]

## <a name="passing-arguments-by-name"></a>Passing Arguments by Name

Alternatively, you can call `Display` with the arguments passed by name, also delimited by commas, as shown in the following example:

[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)]

Passing arguments by name in this way is especially useful when you call a procedure that has more than one optional argument. If you supply arguments by name, you do not have to use consecutive commas to denote missing positional arguments. Passing arguments by name also makes it easier to keep track of which arguments you are passing and which ones you are omitting.

## <a name="mixing-arguments-by-position-and-by-name"></a>Mixing Arguments by Position and by Name

You can supply arguments both by position and by name in a single procedure call, as shown in the following example:

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)]

In the preceding example, no extra comma is necessary to hold the place of the omitted `age` argument, since `birth` is passed by name.

In versions of Visual Basic before 15.5, when you supply arguments by a mixture of position and name, the positional arguments must all come first. Once you supply an argument by name, any remaining arguments must all be passed by name.  For example, the following call to the `Display` method displays compiler error [BC30241: Named argument expected](../../../misc/bc30241.md).

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)]

Starting with Visual Basic 15.5, positional arguments can follow named arguments if the ending positional arguments are in the correct position. If compiled under Visual Basic 15.5, the previous call to the `Display` method compiles successfully and no longer generates compiler error [BC30241](../../../misc/bc30241.md).

This ability to mix and match named and positional arguments in any order is particularly useful when you want to use a named argument to make your code more readable. For example, the following `Person` class constructor requires two arguments of type `Person`, both of which can be `Nothing`.

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)]

Using mixed named and positional arguments helps to make the intent of the code clear when the value of the `father` and `mother` arguments is `Nothing`:

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)]

To follow positional arguments with named arguments, you must add the following element to your Visual Basic project (\*.vbproj) file:

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

For more information see [setting the Visual Basic language version](../../../language-reference/configure-language-version.md).

## <a name="restrictions-on-supplying-arguments-by-name"></a>Restrictions on Supplying Arguments by Name

You cannot pass arguments by name to avoid entering required arguments. You can omit only the optional arguments.

You cannot pass a parameter array by name. This is because when you call the procedure, you supply an indefinite number of comma-separated arguments for the parameter array, and the compiler cannot associate more than one argument with a single name.

## <a name="see-also"></a>関連項目

- [手順](./index.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [方法: プロシージャに引数を渡す](./how-to-pass-arguments-to-a-procedure.md)
- [引数の値渡しと参照渡し](./passing-arguments-by-value-and-by-reference.md)
- [省略可能なパラメーター](./optional-parameters.md)
- [パラメーター配列](./parameter-arrays.md)
- [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)
- [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)
