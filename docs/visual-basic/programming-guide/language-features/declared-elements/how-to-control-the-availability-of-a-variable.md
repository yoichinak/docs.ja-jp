---
title: '方法 : 変数の可用性を制御する'
ms.date: 07/20/2015
helpviewer_keywords:
- access levels, declared elements
- Private keyword [Visual Basic], accessing variables
- access levels, variables
- Public keyword [Visual Basic], accessing variables
- Friend keyword [Visual Basic], accessing variables
- variables [Visual Basic], access level
- declared elements [Visual Basic], access level
- Protected keyword [Visual Basic], accessing variables
ms.assetid: eaf4f073-7922-43ce-ae1e-90ff376ae947
ms.openlocfilehash: 886b57909cf6ba25dbaceea5c5f06eb4e3ba6f1f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345390"
---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a>方法: 変数の可用性を制御する (Visual Basic)
You control the availability of a variable by specifying its *access level*. The access level determines what code has permission to read or write to the variable.  
  
- *Member variables* (defined at module level and outside any procedure) default to public access, which means any code that can see them can access them. You can change this by specifying an access modifier.  
  
- *Local variables* (defined inside a procedure) nominally have public access, although only code within their procedure can access them. You cannot change the access level of a local variable, but you can change the access level of the procedure that contains it.  
  
 For more information, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="private-and-public-access"></a>Private and Public Access  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a>To make a variable accessible only from within its module, class, or structure  
  
1. Place the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) for the variable inside the module, class, or structure, but outside any procedure.  
  
2. Include the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword in the `Dim` statement.  
  
     You can read or write to the variable from anywhere within the module, class, or structure, but not from outside it.  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a>To make a variable accessible from any code that can see it  
  
1. For a member variable, place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.  
  
2. Include the [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword in the `Dim` statement.  
  
     You can read or write to the variable from any code that interoperates with your assembly.  
  
 -または-  
  
1. For a local variable, place the `Dim` statement for the variable inside a procedure.  
  
2. Do not include the `Public` keyword in the `Dim` statement.  
  
     You can read or write to the variable from anywhere within the procedure, but not from outside it.  
  
## <a name="protected-and-friend-access"></a>Protected and Friend Access  
 You can limit the access level of a variable to its class and any derived classes, or to its assembly. You can also specify the union of these limitations, which allows access from code in any derived class or in any other place in the same assembly. You specify this union by combining the `Protected` and `Friend` keywords in the same declaration.  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a>To make a variable accessible only from within its class and any derived classes  
  
1. Place the `Dim` statement for the variable inside a class, but outside any procedure.  
  
2. Include the [Protected](../../../../visual-basic/language-reference/modifiers/protected.md) keyword in the `Dim` statement.  
  
     You can read or write to the variable from anywhere within the class, as well as from within any class derived from it, but not from outside any class in the derivation chain.  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a>To make a variable accessible only from within the same assembly  
  
1. Place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.  
  
2. Include the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) keyword in the `Dim` statement.  
  
     You can read or write to the variable from anywhere within the module, class, or structure, as well as from any code in the same assembly, but not from outside the assembly.  
  
## <a name="example"></a>例  
 The following example shows declarations of variables with `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private` access levels. Note that when the `Dim` statement specifies an access level, you do not need to include the `Dim` keyword.  
  
```vb  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 The more restrictive the access level of a variable, the smaller the chances that malicious code can make improper use of it.  
  
## <a name="see-also"></a>関連項目

- [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)
- [Public](../../../../visual-basic/language-reference/modifiers/public.md)
- [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)
- [Private](../../../../visual-basic/language-reference/modifiers/private.md)
