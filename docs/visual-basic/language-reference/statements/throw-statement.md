---
title: Throw ステートメント
ms.date: 07/20/2015
f1_keywords:
- vb.Throw
helpviewer_keywords:
- structured exception handling, throw statements
- try-catch exception handling, throw statements
- throw statement [Visual Basic], about throw statements
- throwing exceptions, throw statement
- exception handling, throw statement
- On Error statement [Visual Basic], throwing exceptions
- throwing exceptions
- exception handling, unstructured
- throw statement [Visual Basic]
ms.assetid: a6e07406-5c8a-4498-87a2-8339f3651d62
ms.openlocfilehash: 147345990b625e034e651e69b322bc098d0bd8de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352793"
---
# <a name="throw-statement-visual-basic"></a>Throw ステートメント (Visual Basic)

Throws an exception within a procedure.

## <a name="syntax"></a>構文

```vb
Throw [ expression ]
```

## <a name="part"></a>パーツ

`expression`\
Provides information about the exception to be thrown. Optional when residing in a `Catch` statement, otherwise required.

## <a name="remarks"></a>Remarks

The `Throw` statement throws an exception that you can handle with structured exception-handling code (`Try`...`Catch`...`Finally`) or unstructured exception-handling code (`On Error GoTo`). You can use the `Throw` statement to trap errors within your code because Visual Basic moves up the call stack until it finds the appropriate exception-handling code.

A `Throw` statement with no expression can only be used in a `Catch` statement, in which case the statement rethrows the exception currently being handled by the `Catch` statement.

The `Throw` statement resets the call stack for the `expression` exception. If `expression` is not provided, the call stack is left unchanged. You can access the call stack for the exception through the <xref:System.Exception.StackTrace%2A> property.

## <a name="example"></a>例

The following code uses the `Throw` statement to throw an exception:

[!code-vb[VbVbalrStatements#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#84)]

## <a name="see-also"></a>関連項目

- [Try...Catch...Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [On Error ステートメント](../../../visual-basic/language-reference/statements/on-error-statement.md)
