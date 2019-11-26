---
title: 複合データ型
ms.date: 04/25/2017
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types [Visual Basic]
- composite data types [Visual Basic]
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures [Visual Basic], composite data types
- classes [Visual Basic], composite types
- types [Visual Basic], composite
ms.assetid: 62970f2e-52c0-4369-8963-613820f1f434
ms.openlocfilehash: 1c099c5082f1c4173a50c70998c99135c94821e6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346376"
---
# <a name="composite-data-types-visual-basic"></a>複合データ型 (Visual Basic)
In addition to the elementary data types Visual Basic supplies, you can also assemble items of different types to create *composite data types* such as structures, arrays, and classes. You can build composite data types from elementary types and from other composite types. For example, you can define an array of structure elements, or a structure with array members.  
  
## <a name="data-types"></a>データの種類  
 A composite type is different from the data type of any of its components. For example, an array of `Integer` elements is not of the `Integer` data type.  
  
 An array data type is normally represented using the element type, parentheses, and commas as necessary. For example, a one-dimensional array of `String` elements is represented as `String()`, and a two-dimensional array of `Boolean` elements is represented as `Boolean(,)`.  
  
## <a name="structure-types"></a>Structure Types  
 There is no single data type comprising all structures. Instead, each definition of a structure represents a unique data type, even if two structures define identical elements in the same order. However, if you create two or more instances of the same structure, Visual Basic considers them to be of the same data type.  
  
## <a name="tuples"></a>タプル

A tuple is a lightweight structure that contains two or more fields whose types are predefined. Tuples are supported starting with Visual Basic 2017. Tuples are most commonly used to return multiple values from a single method call without having to pass arguments by reference or packaging the returned fields in a more heavy-weight class or structure. See the [Tuples](tuples.md) topic for more information on tuples.

## <a name="array-types"></a>Array Types  
 There is no single data type comprising all arrays. The data type of a particular instance of an array is determined by the following:  
  
- The fact of being an array  
  
- The rank (number of dimensions) of the array  
  
- The element type of the array  
  
 In particular, the length of a given dimension is not part of the instance's data type. 次に例を示します。  
  
```vb  
Dim arrayA( ) As Byte = New Byte(12) {}  
Dim arrayB( ) As Byte = New Byte(100) {}  
Dim arrayC( ) As Short = New Short(100) {}  
Dim arrayD( , ) As Short  
Dim arrayE( , ) As Short = New Short(4, 10) {}  
```  
  
 In the preceding example, array variables `arrayA` and `arrayB` are considered to be of the same data type — `Byte()` — even though they are initialized to different lengths. Variables `arrayB` and `arrayC` are not of the same type because their element types are different. Variables `arrayC` and `arrayD` are not of the same type because their ranks are different. Variables `arrayD` and `arrayE` have the same type — `Short(,)` — because their ranks and element types are the same, even though `arrayD` is not yet initialized.  
  
 For more information on arrays, see [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md).  
  
## <a name="class-types"></a>クラスの種類  
 There is no single data type comprising all classes. Although one class can inherit from another class, each is a separate data type. Multiple instances of the same class are of the same data type. If you assign one class instance variable to another, not only do they have the same data type, they point to the same class instance in memory.  
  
 For more information on classes, see [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md).  
  
## <a name="see-also"></a>関連項目

- [データの種類](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [基本データ型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Generic Types in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [構造体](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [トラブルシューティング (データ型)](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [方法 : 変数内で複数の値を保持する](../../../../visual-basic/programming-guide/language-features/data-types/how-to-hold-more-than-one-value-in-a-variable.md)
