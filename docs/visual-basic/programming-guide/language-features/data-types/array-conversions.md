---
title: 配列の変換
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], converting type
- type conversion [Visual Basic], arrays
- conversions [Visual Basic], type
- arrays [Visual Basic], data types
- conversions [Visual Basic], data type
- object arrays [Visual Basic], converting type
- data type conversion [Visual Basic], array conversions
- conversions [Visual Basic], array types
- object arrays
ms.assetid: fceff7d2-a1b7-44c7-b9aa-8bd831d8a444
ms.openlocfilehash: 622ebe8a77f2dfbeb35e0408be48622d93d409c6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345858"
---
# <a name="array-conversions-visual-basic"></a>配列の変換 (Visual Basic)
You can convert an array type to a different array type provided you meet the following conditions:  
  
- **Equal Rank.** The ranks of the two arrays must be the same, that is, they must have the same number of dimensions. However, the lengths of the respective dimensions do not need to be the same.  
  
- **Element Data Type.** The data types of the elements of both arrays must be reference types. You cannot convert an `Integer` array to a `Long` array, or even to an `Object` array, because at least one value type is involved. 詳細については、「 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)」を参照してください。  
  
- **Convertibility.** A conversion, either widening or narrowing, must be possible between the element types of the two arrays. An example that fails this requirement is an attempted conversion between a `String` array and an array of a class derived from <xref:System.Attribute?displayProperty=nameWithType>. These two types have nothing in common, and no conversion of any kind exists between them.  
  
 A conversion of one array type to another is widening or narrowing depending on whether the conversion of the respective elements is widening or narrowing. 詳細については、「 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)」を参照してください。  
  
## <a name="conversion-to-an-object-array"></a>Conversion to an Object Array  
 When you declare an `Object` array without initializing it, its element type is `Object` as long as it remains uninitialized. When you set it to an array of a specific class, it takes on the type of that class. However, its underlying type is still `Object`, and you can subsequently set it to another array of an unrelated class. Since all classes derive from `Object`, you can change the array's element type from any class to any other class.  
  
 In the following example, no conversion exists between types `student` and `String`, but both derive from `Object`, so all assignments are valid.  
  
```vb  
' Assume student has already been defined as a class.  
Dim testArray() As Object  
' testArray is still an Object array at this point.  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
testArray = New student(3) {}  
' testArray is now of type student().  
testArray = names  
' testArray is now a String array.  
```  
  
### <a name="underlying-type-of-an-array"></a>Underlying Type of an Array  
 If you originally declare an array with a specific class, its underlying element type is that class. If you subsequently set it to an array of another class, there must be a conversion between the two classes.  
  
 In the following example, `students` is a `student` array. Since no conversion exists between `String` and `student`, the last statement fails.  
  
```vb  
Dim students() As student  
Dim names() As String = New String(3) {"Name0", "Name1", "Name2", "Name3"}  
students = New Student(3) {}  
' The following statement fails at compile time.  
students = names  
```  
  
## <a name="see-also"></a>関連項目

- [データの種類](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [暗黙の型変換と明示的な型変換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [文字列とその他の型との変換](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [How to: Convert an Object to Another Type in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [データの種類](../../../../visual-basic/language-reference/data-types/index.md)
- [データ型変換関数](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
