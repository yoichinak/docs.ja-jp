---
title: オブジェクト変数の値
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], values
- values [Visual Basic], of object variables
- data types [Visual Basic], object variable
- variables [Visual Basic], object
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
ms.openlocfilehash: 8b93063d2d97802b1a7fdbc93e01040ff3337753
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351798"
---
# <a name="object-variable-values-visual-basic"></a>オブジェクト変数の値 (Visual Basic)
A variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) can refer to data of any type. The value you store in an `Object` variable is kept elsewhere in memory, while the variable itself holds a pointer to the data.  
  
## <a name="object-classifier-functions"></a>Object Classifier Functions  
 Visual Basic supplies functions that return information about what an `Object` variable refers to, as shown in the following table.  
  
|機能|Returns True if the Object variable refers to|  
|--------------|---------------------------------------------------|  
|<xref:Microsoft.VisualBasic.Information.IsArray%2A>|An array of values, rather than a single value|  
|<xref:Microsoft.VisualBasic.Information.IsDate%2A>|A [Date Data Type](../../../../visual-basic/language-reference/data-types/date-data-type.md) value, or a string that can be interpreted as a date and time value|  
|<xref:Microsoft.VisualBasic.Information.IsDBNull%2A>|An object of type <xref:System.DBNull>, which represents missing or nonexistent data|  
|<xref:Microsoft.VisualBasic.Information.IsError%2A>|An exception object, which derives from <xref:System.Exception>|  
|<xref:Microsoft.VisualBasic.Information.IsNothing%2A>|[Nothing](../../../../visual-basic/language-reference/nothing.md), that is, no object is currently assigned to the variable|  
|<xref:Microsoft.VisualBasic.Information.IsNumeric%2A>|A number, or a string that can be interpreted as a number|  
|<xref:Microsoft.VisualBasic.Information.IsReference%2A>|A reference type (such as a string, array, delegate, or class type)|  
  
 You can use these functions to avoid submitting an invalid value to an operation or a procedure.  
  
## <a name="typeof-operator"></a>TypeOf 演算子  
 You can also use the [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) to determine whether an object variable currently refers to a specific data type. The `TypeOf`...`Is` expression evaluates to `True` if the run-time type of the operand is derived from or implements the specified type.  
  
 The following example uses `TypeOf` on object variables referring to value and reference types.  
  
```vb  
' The following statement puts a value type (Integer) in an Object variable.  
Dim num As Object = 10  
' The following statement puts a reference type (Form) in an Object variable.  
Dim frm As Object = New Form()  
If TypeOf num Is Long Then Debug.WriteLine("num is Long")  
If TypeOf num Is Integer Then Debug.WriteLine("num is Integer")  
If TypeOf num Is Short Then Debug.WriteLine("num is Short")  
If TypeOf num Is Object Then Debug.WriteLine("num is Object")  
If TypeOf frm Is Form Then Debug.WriteLine("frm is Form")  
If TypeOf frm Is Label Then Debug.WriteLine("frm is Label")  
If TypeOf frm Is Object Then Debug.WriteLine("frm is Object")  
```  
  
 The preceding example writes the following lines to the **Debug** window:  
  
 `num is Integer`  
  
 `num is Object`  
  
 `frm is Form`  
  
 `frm is Object`  
  
 The object variable `num` refers to data of type `Integer`, and `frm` refers to an object of class <xref:System.Windows.Forms.Form>.  
  
## <a name="object-arrays"></a>Object Arrays  
 You can declare and use an array of `Object` variables. This is useful when you need to handle a variety of data types and object classes. All the elements in an array must have the same declared data type. Declaring this data type as `Object` allows you to store objects and class instances alongside other data types in the array.  
  
## <a name="see-also"></a>関連項目

- [オブジェクト変数](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [オブジェクト変数の宣言](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [オブジェクト変数の代入](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [方法: オブジェクトの現在のインスタンスを参照する](../../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [方法: オブジェクト変数で参照している型を確認する](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)
- [方法: 2 つのオブジェクトが関連しているかどうかを決める](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [方法: 2 つのオブジェクトが同一であるかどうか判別する](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
- [データの種類](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
