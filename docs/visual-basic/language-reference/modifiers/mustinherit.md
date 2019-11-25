---
title: MustInherit
ms.date: 07/20/2015
f1_keywords:
- MustInherit
- vb.MustInherit
helpviewer_keywords:
- classes [Visual Basic], abstract
- MustInherit classes [Visual Basic], MustInherit keyword
- abstract classes [Visual Basic], MustInherit class
- MustInherit keyword [Visual Basic]
ms.assetid: b8f05185-90e3-4dd7-adc2-90d852fab5b4
ms.openlocfilehash: 30befaaf194d78d26a57f29c59bf0a603e9f07a3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351496"
---
# <a name="mustinherit-visual-basic"></a>MustInherit (Visual Basic)
Specifies that a class can be used only as a base class and that you cannot create an object directly from it.  
  
## <a name="remarks"></a>Remarks  
 The purpose of a *base class* (also known as an *abstract class*) is to define functionality that is common to all the classes derived from it. This saves the derived classes from having to redefine the common elements. In some cases, this common functionality is not complete enough to make a usable object, and each derived class defines the missing functionality. In such a case, you want the consuming code to create objects only from the derived classes. You use `MustInherit` on the base class to enforce this.  
  
 Another use of a `MustInherit` class is to restrict a variable to a set of related classes. You can define a base class and derive all these related classes from it. The base class does not need to provide any functionality common to all the derived classes, but it can serve as a filter for assigning values to variables. If your consuming code declares a variable as the base class, Visual Basic allows you to assign only an object from one of the derived classes to that variable.  
  
 The .NET Framework defines several `MustInherit` classes, among them <xref:System.Array>, <xref:System.Enum>, and <xref:System.ValueType>. <xref:System.ValueType> is an example of a base class that restricts a variable. All value types derive from <xref:System.ValueType>. If you declare a variable as <xref:System.ValueType>, you can assign only value types to that variable.  
  
## <a name="rules"></a>ルール  
  
- **Declaration Context.** You can use `MustInherit` only in a `Class` statement.  
  
- **Combined Modifiers.** You cannot specify `MustInherit` together with `NotInheritable` in the same declaration.  
  
## <a name="example"></a>例  
 The following example illustrates both forced inheritance and forced overriding. The base class `shape` defines a variable `acrossLine`. The classes `circle` and `square` derive from `shape`. They inherit the definition of `acrossLine`, but they must define the function `area` because that calculation is different for each kind of shape.  
  
 [!code-vb[VbVbalrKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class1.vb#2)]  
  
 You can declare `shape1` and `shape2` to be of type `shape`. However, you cannot create an object from `shape` because it lacks the functionality of the function `area` and is marked `MustInherit`.  
  
 Because they are declared as `shape`, the variables `shape1` and `shape2` are restricted to objects from the derived classes `circle` and `square`. Visual Basic does not allow you to assign any other object to these variables, which gives you a high level of type safety.  
  
## <a name="usage"></a>使用方法  
 The `MustInherit` modifier can be used in this context:  
  
 [Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)  
  
## <a name="see-also"></a>関連項目

- [Inherits ステートメント](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [キーワード](../../../visual-basic/language-reference/keywords/index.md)
- [継承の基本](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
