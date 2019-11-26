---
title: '方法 : 変数のスコープを制御する'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], scope
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- variables [Visual Basic], visibility
- scope [Visual Basic], declared elements
- scope [Visual Basic], variables
- scope [Visual Basic], Visual Basic
- declared elements [Visual Basic], visibility
- visibility [Visual Basic], variables
ms.assetid: 44b7f62a-cb5c-4d50-bce9-60ae68f87072
ms.openlocfilehash: 0ee6ce183310aa836ecdbbc0bc819e0e83d1872d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345377"
---
# <a name="how-to-control-the-scope-of-a-variable-visual-basic"></a>方法: 変数のスコープを制御する (Visual Basic)
Normally, a variable is in *scope*, or visible for reference, throughout the region in which you declare it. In some cases, the variable's *access level* can influence its scope.  
  
 詳細については、「 [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)」を参照してください。  
  
## <a name="scope-at-block-or-procedure-level"></a>Scope at Block or Procedure Level  
  
#### <a name="to-make-a-variable-visible-only-within-a-block"></a>To make a variable visible only within a block  
  
- Place the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) for the variable between the initiating and terminating declaration statements of that block, for example between the `For` and `Next` statements of a `For` loop.  
  
     You can refer to the variable only from within the block.  
  
#### <a name="to-make-a-variable-visible-only-within-a-procedure"></a>To make a variable visible only within a procedure  
  
- Place the `Dim` statement for the variable inside the procedure but outside any block (such as a `With`...`End With` block).  
  
     You can refer to the variable only from within the procedure, including inside any block contained in the procedure.  
  
## <a name="scope-at-module-or-namespace-level"></a>Scope at Module or Namespace Level  
 For convenience, the single term *module level* applies equally to modules, classes, and structures. The access level of a module level variable determines its scope. The namespace that contains the module, class, or structure also influences the scope.  
  
#### <a name="to-make-a-variable-visible-throughout-a-module-class-or-structure"></a>To make a variable visible throughout a module, class, or structure  
  
1. Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.  
  
2. Include the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword in the `Dim` statement.  
  
3. You can refer to the variable from anywhere within the module, class, or structure, but not from outside it.  
  
#### <a name="to-make-a-variable-visible-throughout-a-namespace"></a>To make a variable visible throughout a namespace  
  
1. Place the `Dim` statement for the variable inside the module, class, or structure, but outside any procedure.  
  
2. Include the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) or [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword in the `Dim` statement.  
  
3. You can refer to the variable from anywhere within the namespace containing the module, class, or structure.  
  
## <a name="example"></a>例  
 The following example declares a variable at module level and limits its visibility to code within the module.  
  
```vb  
Module demonstrateScope  
    Private strMsg As String  
    Sub initializePrivateVariable()  
        strMsg = "This variable cannot be used outside this module."  
    End Sub  
    Sub usePrivateVariable()  
        MsgBox(strMsg)  
    End Sub  
End Module  
```  
  
 In the preceding example, all the procedures defined in module `demonstrateScope` can refer to the `String` variable `strMsg`. When the `usePrivateVariable` procedure is called, it displays the contents of the string variable `strMsg` in a dialog box.  
  
 With the following alteration to the preceding example, the string variable `strMsg` can be referred to by code anywhere in the namespace of its declaration.  
  
```vb  
Public strMsg As String  
```  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 The narrower the scope of a variable, the fewer opportunities you have for accidentally referring to it in place of another variable with the same name. You can also minimize problems of reference matching.  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 The narrower the scope of a variable, the smaller the chances that malicious code can make improper use of it.  
  
## <a name="see-also"></a>関連項目

- [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Lifetime in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [変数](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)
