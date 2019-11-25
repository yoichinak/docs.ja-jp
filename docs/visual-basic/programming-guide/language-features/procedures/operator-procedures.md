---
title: 演算子プロシージャ
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
ms.assetid: 8c513d38-246b-4fb7-8b75-29e1364e555b
ms.openlocfilehash: b395f5fcf1b89bb49e55e207c4910e95f2aae69d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345999"
---
# <a name="operator-procedures-visual-basic"></a>演算子プロシージャ (Visual Basic)

An operator procedure is a series of Visual Basic statements that define the behavior of a standard operator (such as `*`, `<>`, or `And`) on a class or structure you have defined. This is also called *operator overloading*.

## <a name="when-to-define-operator-procedures"></a>When to Define Operator Procedures

When you have defined a class or structure, you can declare variables to be of the type of that class or structure. Sometimes such a variable needs to participate in an operation as part of an expression. To do this, it must be an operand of an operator.

Visual Basic defines operators only on its fundamental data types. You can define the behavior of an operator when one or both of the operands are of the type of your class or structure.

For more information, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).

## <a name="types-of-operator-procedure"></a>Types of Operator Procedure

An operator procedure can be one of the following types:

- A definition of a unary operator where the argument is of the type of your class or structure.

- A definition of a binary operator where at least one of the arguments is of the type of your class or structure.

- A definition of a conversion operator where the argument is of the type of your class or structure.

- A definition of a conversion operator that returns the type of your class or structure.

 Conversion operators are always unary, and you always use `CType` as the operator you are defining.

## <a name="declaration-syntax"></a>宣言の構文

The syntax for declaring an operator procedure is as follows:

```vb
Public Shared [Widening | Narrowing] Operator operatorsymbol ( operand1 [,  operand2 ]) As datatype

' Statements of the operator procedure.

End Operator
```

You use the `Widening` or `Narrowing` keyword only on a type conversion operator. The operator symbol is always [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) for a type conversion operator.

You declare two operands to define a binary operator, and you declare one operand to define a unary operator, including a type conversion operator. All operands must be declared `ByVal`.

You declare each operand the same way you declare parameters for [Sub Procedures](./sub-procedures.md).

### <a name="data-type"></a>データの種類

Because you are defining an operator on a class or structure you have defined, at least one of the operands must be of the data type of that class or structure. For a type conversion operator, either the operand or the return type must be of the data type of the class or structure.

For more details, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).

## <a name="calling-syntax"></a>Calling Syntax

You invoke an operator procedure implicitly by using the operator symbol in an expression. You supply the operands the same way you do for predefined operators.

The syntax for an implicit call to an operator procedure is as follows:

`Dim testStruct As`  *structurename*

`Dim testNewStruct As`  *structurename*  `= testStruct`  *operatorsymbol*  `10`

### <a name="illustration-of-declaration-and-call"></a>Illustration of Declaration and Call

The following structure stores a signed 128-bit integer value as the constituent high-order and low-order parts. It defines the `+` operator to add two `veryLong` values and generate a resulting `veryLong` value.

[!code-vb[VbVbcnProcedures#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#23)]

The following example shows a typical call to the `+` operator defined on `veryLong`.

[!code-vb[VbVbcnProcedures#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#24)]

## <a name="see-also"></a>関連項目

- [手順](./index.md)
- [Sub プロシージャ](./sub-procedures.md)
- [Function プロシージャ](./function-procedures.md)
- [Property プロシージャ](./property-procedures.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [Operator ステートメント](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [方法 : 演算子を定義する](./how-to-define-an-operator.md)
- [方法 : 変換演算子を定義する](./how-to-define-a-conversion-operator.md)
- [方法 : 演算子プロシージャを呼び出す](./how-to-call-an-operator-procedure.md)
- [方法: 演算子を定義するクラスを使用する](./how-to-use-a-class-that-defines-operators.md)
