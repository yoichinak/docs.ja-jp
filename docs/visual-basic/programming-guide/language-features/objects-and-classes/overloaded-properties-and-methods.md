---
title: Overloaded properties and methods
ms.date: 07/20/2015
helpviewer_keywords:
- properties [Visual Basic], overloading
- methods [Visual Basic], overloading
- shadowing
- names [Visual Basic], multiple procedures with same
- procedures [Visual Basic], multiples with same name
- classes [Visual Basic], properties
- classes [Visual Basic], methods
- method overloading
- Overloads keyword [Visual Basic], overloaded members
ms.assetid: b686fb97-e7d7-4001-afaa-6650cba08f0d
ms.openlocfilehash: a5017d371f8a01436020443b2e3466c78fc35d21
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346089"
---
# <a name="overloaded-properties-and-methods-visual-basic"></a>Overloaded properties and methods (Visual Basic)

Overloading is the creation of more than one procedure, instance constructor, or property in a class with the same name but different argument types.

## <a name="overloading-usage"></a>Overloading usage

Overloading is especially useful when your object model dictates that you employ identical names for procedures that operate on different data types. For example, a class that can display several different data types could have `Display` procedures that look like this:

[!code-vb[VbVbalrOOP#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#64)]

Without overloading, you would need to create distinct names for each procedure, even though they do the same thing, as shown next:

[!code-vb[VbVbalrOOP#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#65)]

Overloading makes it easier to use properties or methods because it provides a choice of data types that can be used. For example, the overloaded `Display` method discussed previously can be called with any of the following lines of code:

[!code-vb[VbVbalrOOP#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#66)]

At run time, Visual Basic calls the correct procedure based on the data types of the parameters you specify.

## <a name="overloading-rules"></a>Overloading rules

 You create an overloaded member for a class by adding two or more properties or methods with the same name. Except for overloaded derived members, each overloaded member must have different parameter lists, and the following items cannot be used as a differentiating feature when overloading a property or procedure:

- Modifiers, such as `ByVal` or `ByRef`, that apply to a member, or parameters of the member.

- Names of parameters

- Return types of procedures

The `Overloads` keyword is optional when overloading, but if any overloaded member uses the `Overloads` keyword, then all other overloaded members with the same name must also specify this keyword.

Derived classes can overload inherited members with members that have identical parameters and parameter types, a process known as *shadowing by name and signature*. If the `Overloads` keyword is used when shadowing by name and signature, the derived class's implementation of the member will be used instead of the implementation in the base class, and all other overloads for that member will be available to instances of the derived class.

If the `Overloads` keyword is omitted when overloading an inherited member with a member that has identical parameters and parameter types, then the overloading is called *shadowing by name*. Shadowing by name replaces the inherited implementation of a member, and it makes all other overloads unavailable to instances of the derived class and its decedents.

The `Overloads` and `Shadows` modifiers cannot both be used with the same property or method.

### <a name="example"></a>例

The following example creates overloaded methods that accept either a `String` or `Decimal` representation of a dollar amount and return a string containing the sales tax.

#### <a name="to-use-this-example-to-create-an-overloaded-method"></a>To use this example to create an overloaded method

1. Open a new project and add a class named `TaxClass`.

2. `TaxClass` クラスに次のコードを追加します。

    [!code-vb[VbVbalrOOP#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#67)]

3. Add the following procedure to your form.

    [!code-vb[VbVbalrOOP#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#68)]

4. Add a button to your form and call the `ShowTax` procedure from the `Button1_Click` event of the button.

5. Run the project and click the button on the form to test the overloaded `ShowTax` procedure.

At run time, the compiler chooses the appropriate overloaded function that matches the parameters being used. When you click the button, the overloaded method is called first with a `Price` parameter that is a string and the message, "Price is a String. Tax is $5.12" is displayed. `TaxAmount` is called with a `Decimal` value the second time and the message, "Price is a Decimal. Tax is $5.12" is displayed.

## <a name="see-also"></a>関連項目

- [クラスとオブジェクト](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [Shadowing in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Sub ステートメント](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [継承の基本](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)
- [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)
- [オーバーロード](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
