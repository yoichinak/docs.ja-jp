---
title: オブジェクトの型の決定
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], discovering which an object belongs to
- types [Visual Basic], determining Visual Basic object types
- object variables [Visual Basic], testing values
- TypeOf...Is expression, object type at run time
- TypeName function
- objects [Visual Basic], type determining
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
ms.openlocfilehash: a77cc0603a0b61f58a4aa703c4b1e6ef4c26729c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345199"
---
# <a name="determining-object-type-visual-basic"></a>オブジェクトの型の決定 (Visual Basic)
Generic object variables (that is, variables you declare as `Object`) can hold objects from any class. When using variables of type `Object`, you may need to take different actions based on the class of the object; for example, some objects might not support a particular property or method. Visual Basic provides two means of determining which type of object is stored in an object variable: the `TypeName` function and the `TypeOf...Is` operator.  
  
## <a name="typename-and-typeofis"></a>TypeName and TypeOf…Is  
 The `TypeName` function returns a string and is the best choice when you need to store or display the class name of an object, as shown in the following code fragment:  
  
 [!code-vb[VbVbalrOOP#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#92)]  
  
 The `TypeOf...Is` operator is the best choice for testing an object's type, because it is much faster than an equivalent string comparison using `TypeName`. The following code fragment uses `TypeOf...Is` within an `If...Then...Else` statement:  
  
 [!code-vb[VbVbalrOOP#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#93)]  
  
 A word of caution is due here. The `TypeOf...Is` operator returns `True` if an object is of a specific type, or is derived from a specific type. Almost everything you do with Visual Basic involves objects, which include some elements not normally thought of as objects, such as strings and integers. These objects are derived from and inherit methods from <xref:System.Object>. When passed an `Integer` and evaluated with `Object`, the `TypeOf...Is` operator returns `True`. The following example reports that the parameter `InParam` is both an `Object` and an `Integer`:  
  
 [!code-vb[VbVbalrOOP#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#94)]  
  
 The following example uses both `TypeOf...Is` and `TypeName` to determine the type of object passed to it in the `Ctrl` argument. The `TestObject` procedure calls `ShowType` with three different kinds of controls.  
  
#### <a name="to-run-the-example"></a>例を実行するには  
  
1. Create a new Windows Application project and add a <xref:System.Windows.Forms.Button> control, a <xref:System.Windows.Forms.CheckBox> control, and a <xref:System.Windows.Forms.RadioButton> control to the form.  
  
2. From the button on your form, call the `TestObject` procedure.  
  
3. Add the following code to your form:  
  
     [!code-vb[VbVbalrOOP#95](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#95)]  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.Information.TypeName%2A>
- [文字列名によるプロパティまたはメソッドの呼び出し](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md)
- [Object 型](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [If...Then...Else ステートメント](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [String データ型](../../../../visual-basic/language-reference/data-types/string-data-type.md)
- [Integer データ型](../../../../visual-basic/language-reference/data-types/integer-data-type.md)
