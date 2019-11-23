---
title: コード内の特殊文字
ms.date: 07/20/2015
f1_keywords:
- vb.)
- vb.(
- vb.colon
- vb.!
- vb..
- 'vb.:'
helpviewer_keywords:
- special characters [Visual Basic], in code
- parentheses [Visual Basic], using in code
- colons (:)
- period character in code
- dot operator (.)
- dictionary access operator [Visual Basic]
- concatenation operators [Visual Basic], special characters in code
- concatenation operators [Visual Basic], vs. addition operator
- '! operator'
- separators [Visual Basic], using in code
- operators [Visual Basic], dictionary access
- ': separator character'
- member access operator [Visual Basic]
- addition operator [Visual Basic]
- operators [Visual Basic], member access
- . operator
- exclamation points
- separators
- exclamation point operator (!)
- Visual Basic code, special characters
ms.assetid: 310dce0c-45b5-4e0d-83e9-32df258d2a3e
ms.openlocfilehash: f4ab35b56d48ae86bdb024ffea27735b39decdc2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347268"
---
# <a name="special-characters-in-code-visual-basic"></a>コード内の特殊文字 (Visual Basic)
Sometimes you have to use special characters in your code, that is, characters that are not alphabetical or numeric. The punctuation and special characters in the Visual Basic character set have various uses, from organizing program text to defining the tasks that the compiler or the compiled program performs. 実行するオペレーションを指定するのには使用されません。  
  
## <a name="parentheses"></a>Parentheses  
 Use parentheses when you define a procedure, such as a `Sub` or `Function`. You must enclose all procedure argument lists in parentheses. You also use parentheses for putting variables or arguments into logical groups, especially to override the default order of operator precedence in a complex expression. 次に例を示します。  
  
 [!code-vb[VbVbcnConventions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#11)]  
  
 Following execution of the previous code, the value of `d` is 8.225 and the value of `e` is 3. The calculation for `d` uses the default precedence of `/` over `+` and is equivalent to `d = b + (c / a)`. The parentheses in the calculation for `e` override the default precedence.  
  
## <a name="separators"></a>[区切り記号]  
 Separators do what their name suggests: they separate sections of code. In Visual Basic, the separator character is the colon (`:`). Use separators when you want to include multiple statements on a single line instead of separate lines. This saves space and improves the readability of your code. The following example shows three statements separated by colons.  
  
 [!code-vb[VbVbcnConventions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#12)]  
  
 For more information, see [How to: Break and Combine Statements in Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).  
  
 The colon (`:`) character is also used to identify a statement label. For more information, see [How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md).  
  
## <a name="concatenation"></a>連結  
 Use the `&` operator for *concatenation*, or linking strings together. Do not confuse it with the `+` operator, which adds together numeric values. If you use the `+` operator to concatenate when you operate on numeric values, you can obtain incorrect results. 次に例を示します。  
  
 [!code-vb[VbVbcnConventions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#13)]  
  
 Following execution of the previous code, the value of `resultA` is 21.01 and the value of `resultB` is "10.0111".  
  
## <a name="member-access-operators"></a>Member Access Operators  
 To access a member of a type, you use the dot (`.`) or exclamation point (`!`) operator between the type name and the member name.  
  
### <a name="dot--operator"></a>Dot (.) Operator  
 Use the `.` operator on a class, structure, interface, or enumeration as a member access operator. The member can be a field, property, event, or method. 次に例を示します。  
  
 [!code-vb[VbVbcnConventions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#14)]  
  
### <a name="exclamation-point--operator"></a>Exclamation Point (!) Operator  
 Use the `!` operator only on a class or interface as a dictionary access operator. The class or interface must have a default property that accepts a single `String` argument. The identifier immediately following the `!` operator becomes the argument value passed to the default property as a string. 次に例を示します。  
  
 [!code-vb[VbVbcnConventions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#15)]  
  
 The three output lines of `MsgBox` all display the value `32856`. The first line uses the traditional access to property `index`, the second makes use of the fact that `index` is the default property of class `hasDefault`, and the third uses dictionary access to the class.  
  
 Note that the second operand of the `!` operator must be a valid Visual Basic identifier not enclosed in double quotation marks (`" "`). In other words, you cannot use a string literal or string variable. The following change to the last line of the `MsgBox` call generates an error because `"X"` is an enclosed string literal.  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
> References to default collections must be explicit. In particular, you cannot use the `!` operator on a late-bound variable.  
  
 The `!` character is also used as the `Single` type character.  
  
## <a name="see-also"></a>関連項目

- [プログラム構造とコード規則](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [型文字](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
