---
title: '方法 : プロパティ プロシージャを呼び出す'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], property procedures
- procedure calls [Visual Basic], property procedures
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
ms.openlocfilehash: 52e6c62ffb81c480ccc1abf06f04eb780218dbf1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340555"
---
# <a name="how-to-call-a-property-procedure-visual-basic"></a>方法: プロパティ プロシージャを呼び出す (Visual Basic)
You call a property procedure by storing a value in the property or retrieving its value. You access a property the same way you access a variable.  
  
 The property's `Set` procedure stores a value, and its `Get` procedure retrieves the value. However, you do not explicitly call these procedures by name. You use the property in an assignment statement or an expression, just as you would store or retrieve the value of a variable. Visual Basic makes the calls to the property's procedures.  
  
### <a name="to-call-a-propertys-get-procedure"></a>To call a property's Get procedure  
  
1. Use the property name in an expression the same way you would use a variable name. You can use a property anywhere you can use a variable or a constant.  
  
     -または-  
  
     Use the property name following the equal (`=`) sign in an assignment statement.  
  
     The following example reads the value of the <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> property, implicitly calling its `Get` procedure.  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. If the property takes arguments, follow the property name with parentheses to enclose the argument list. If there are no arguments, you can optionally omit the parentheses.  
  
3. Place the arguments in the argument list within the parentheses, separated by commas. Be sure you supply the arguments in the same order that the property defines the corresponding parameters.  
  
 The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.  
  
### <a name="to-call-a-propertys-set-procedure"></a>To call a property's Set procedure  
  
1. Use the property name on the left side of an assignment statement.  
  
     The following example sets the value of the <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> property, implicitly calling the `Set` procedure.  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. If the property takes arguments, follow the property name with parentheses to enclose the argument list. If there are no arguments, you can optionally omit the parentheses.  
  
3. Place the arguments in the argument list within the parentheses, separated by commas. Be sure you supply the arguments in the same order that the property defines the corresponding parameters.  
  
 The value generated on the right side of the assignment statement is stored in the property.  
  
## <a name="see-also"></a>関連項目

- [Property プロシージャ](./property-procedures.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [Property ステートメント](../../../../visual-basic/language-reference/statements/property-statement.md)
- [Differences Between Properties and Variables in Visual Basic](./differences-between-properties-and-variables.md)
- [方法 : プロパティを作成する](./how-to-create-a-property.md)
- [方法 : 複数のアクセス レベルを持つプロパティを宣言する](./how-to-declare-a-property-with-mixed-access-levels.md)
- [How to: Declare and Call a Default Property in Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [方法 : プロパティに値を格納する](./how-to-put-a-value-in-a-property.md)
- [方法 : プロパティから値を取得する](./how-to-get-a-value-from-a-property.md)
- [Get ステートメント](../../../../visual-basic/language-reference/statements/get-statement.md)
- [Set ステートメント](../../../../visual-basic/language-reference/statements/set-statement.md)
