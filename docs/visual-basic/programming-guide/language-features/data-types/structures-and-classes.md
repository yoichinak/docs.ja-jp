---
title: 構造体とクラス
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], vs. structures
- structures [Visual Basic]
- classes [Visual Basic]
- structures [Visual Basic], compared to classes
- structures [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: a221e74a-ffcf-4bdc-a0f6-a088a9bf26cc
ms.openlocfilehash: 3353935a74bb77fa4a630e706aa425063c7a610a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346326"
---
# <a name="structures-and-classes-visual-basic"></a>構造体とクラス (Visual Basic)
Visual Basic unifies the syntax for structures and classes, with the result that both entities support most of the same features. However, there are also important differences between structures and classes.  
  
 Classes have the advantage of being reference types — passing a reference is more efficient than passing a structure variable with all its data. On the other hand, structures do not require allocation of memory on the global heap.  
  
 Because you cannot inherit from a structure, structures should be used only for objects that do not need to be extended. Use structures when the object you wish to create has a small instance size, and take into account the performance characteristics of classes versus structures.  
  
## <a name="similarities"></a>Similarities  
 Structures and classes are similar in the following respects:  
  
- Both are *container* types, meaning that they contain other types as members.  
  
- Both have members, which can include constructors, methods, properties, fields, constants, enumerations, events, and event handlers. However, do not confuse these members with the declared *elements* of a structure.  
  
- Members of both can have individualized access levels. For example, one member can be declared `Public` and another `Private`.  
  
- Both can implement interfaces.  
  
- Both can have shared constructors, with or without parameters.  
  
- Both can expose a *default property*, provided that property takes at least one parameter.  
  
- Both can declare and raise events, and both can declare delegates.  
  
## <a name="differences"></a>Differences  
 Structures and classes differ in the following particulars:  
  
- Structures are *value types*; classes are *reference types*. A variable of a structure type contains the structure's data, rather than containing a reference to the data as a class type does.  
  
- Structures use stack allocation; classes use heap allocation.  
  
- All structure elements are `Public` by default; class variables and constants are `Private` by default, while other class members are `Public` by default. This behavior for class members provides compatibility with the Visual Basic 6.0 system of defaults.  
  
- A structure must have at least one nonshared variable or nonshared, noncustom event element; a class can be completely empty.  
  
- Structure elements cannot be declared as `Protected`; class members can.  
  
- A structure procedure can handle events only if it is a [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)`Sub` procedure, and only by means of the [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md); any class procedure can handle events, using either the [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) keyword or the `AddHandler` statement. 詳細については、「[イベント](../../../../visual-basic/programming-guide/language-features/events/index.md)」を参照してください。  
  
- Structure variable declarations cannot specify initializers or initial sizes for arrays; class variable declarations can.  
  
- Structures implicitly inherit from the <xref:System.ValueType?displayProperty=nameWithType> class and cannot inherit from any other type; classes can inherit from any class or classes other than <xref:System.ValueType?displayProperty=nameWithType>.  
  
- Structures are not inheritable; classes are.  
  
- Structures are never terminated, so the common language runtime (CLR) never calls the <xref:System.Object.Finalize%2A> method on any structure; classes are terminated by the garbage collector (GC), which calls <xref:System.Object.Finalize%2A> on a class when it detects there are no active references remaining.  
  
- A structure does not require a constructor; a class does.  
  
- Structures can have nonshared constructors only if they take parameters; classes can have them with or without parameters.  
  
 Every structure has an implicit public constructor without parameters. This constructor initializes all the structure's data elements to their default values. You cannot redefine this behavior.  
  
## <a name="instances-and-variables"></a>Instances and Variables  
 Because structures are value types, each structure variable is permanently bound to an individual structure instance. But classes are reference types, and an object variable can refer to various class instances at different times. This distinction affects your usage of structures and classes in the following ways:  
  
- **Initialization.** A structure variable implicitly includes an initialization of the elements using the structure's parameterless constructor. Therefore, `Dim s As struct1` is equivalent to `Dim s As struct1 = New struct1()`.  
  
- **Assigning Variables.** When you assign one structure variable to another, or pass a structure instance to a procedure argument, the current values of all the variable elements are copied to the new structure. When you assign one object variable to another, or pass an object variable to a procedure, only the reference pointer is copied.  
  
- **Assigning Nothing.** You can assign the value [Nothing](../../../../visual-basic/language-reference/nothing.md) to a structure variable, but the instance continues to be associated with the variable. You can still call its methods and access its data elements, although variable elements are reinitialized by the assignment.  
  
     In contrast, if you set an object variable to `Nothing`, you dissociate it from any class instance, and you cannot access any members through the variable until you assign another instance to it.  
  
- **Multiple Instances.** An object variable can have different class instances assigned to it at different times, and several object variables can refer to the same class instance at the same time. Changes you make to the values of class members affect those members when accessed through another variable pointing to the same instance.  
  
     Structure elements, however, are isolated within their own instance. Changes to their values are not reflected in any other structure variables, even in other instances of the same `Structure` declaration.  
  
- **Equality.** Equality testing of two structures must be performed with an element-by-element test. Two object variables can be compared using the <xref:System.Object.Equals%2A> method. <xref:System.Object.Equals%2A> indicates whether the two variables point to the same instance.  
  
## <a name="see-also"></a>関連項目

- [データの種類](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [複合データ型](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [構造体](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [トラブルシューティング (データ型)](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [構造体とその他のプログラミング要素](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [クラスとオブジェクト](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
