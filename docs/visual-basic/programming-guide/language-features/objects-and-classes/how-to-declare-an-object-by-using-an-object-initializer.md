---
title: '方法 : オブジェクト初期化子を使用してオブジェクトを宣言する'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring objects using object initializer
- object initializers [Visual Basic]
- initializers [Visual Basic]
- Video How tos, Visual Basic
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
ms.openlocfilehash: ae04d338b61027c3917ad3a7f62ff40f0a95e53e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347137"
---
# <a name="how-to-declare-an-object-by-using-an-object-initializer-visual-basic"></a>方法: オブジェクト初期化子を使用してオブジェクトを宣言する (Visual Basic)
Object initializers enable you to declare and instantiate an instance of a class in a single statement. In addition, you can initialize one or more members of the instance at the same time, without invoking a parameterized constructor.  
  
 When you use an object initializer to create an instance of a named type, the parameterless constructor for the class is called, followed by initialization of designated members in the order you specify.  
  
 The following procedure shows how to create an instance of a `Student` class in three different ways. The class has first name, last name, and class year properties, among others. Each of the three declarations creates a new instance of `Student`, with property `First` set to "Michael", property `Last` set to "Tucker", and all other members set to their default values. The result of each declaration in the procedure is equivalent to the following example, which does not use an object initializer.  
  
 [!code-vb[VbVbalrObjectInit#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#20)]  
  
 For an implementation of the `Student` class, see [How to: Create a List of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md). You can copy the code from that topic to set up the class and create a list of `Student` objects to work with.  
  
### <a name="to-create-an-object-of-a-named-class-by-using-an-object-initializer"></a>To create an object of a named class by using an object initializer  
  
1. Begin the declaration as if you planned to use a constructor.  
  
     `Dim student1 As New Student`  
  
2. Type the keyword `With`, followed by an initialization list in braces.  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3. In the initialization list, include each property that you want to initialize and assign an initial value to it. The name of the property is preceded by a period.  
  
     [!code-vb[VbVbalrObjectInit#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#21)]  
  
     You can initialize one or more members of the class.  
  
4. Alternatively, you can declare a new instance of the class and then assign a value to it. First, declare an instance of `Student`:  
  
     `Dim student2 As Student`  
  
5. Begin the creation of an instance of `Student` in the normal way.  
  
     `Dim student2 As Student = New Student`  
  
6. Type `With` and then an object initializer to initialize one or more members of the new instance.  
  
     [!code-vb[VbVbalrObjectInit#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#22)]  
  
7. You can simplify the definition in the previous step by omitting `As Student`. If you do this, the compiler determines that `student3` is an instance of `Student` by using local type inference.  
  
     [!code-vb[VbVbalrObjectInit#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#23)]  
  
     For more information, see [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
## <a name="see-also"></a>関連項目

- [ローカル型の推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [方法: 項目のリストを作成する](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)
- [オブジェクト初期化子 : 名前付きの型と匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
