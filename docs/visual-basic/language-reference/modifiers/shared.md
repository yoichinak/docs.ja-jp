---
title: Shared
ms.date: 07/20/2015
f1_keywords:
- vb.Shared
helpviewer_keywords:
- Shared keyword [Visual Basic]
- members [Visual Basic], shared
- shared members
- nonshared
- shared [elements VB]
- elements [Visual Basic], shared
ms.assetid: 2bf7cf2c-b0dd-485e-8749-b5d674dab4cd
ms.openlocfilehash: 98fa25d2283408dfb80e82fbc620a1b284e5c530
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349124"
---
# <a name="shared-visual-basic"></a>Shared (Visual Basic)
Specifies that one or more declared programming elements are associated with a class or structure at large, and not with a specific instance of the class or structure.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="when-to-use-shared"></a>When to Use Shared  
 Sharing a member of a class or structure makes it available to every instance, rather than *nonshared*, where each instance keeps its own copy. This is useful, for example, if the value of a variable applies to the entire application. If you declare that variable to be `Shared`, then all instances access the same storage location, and if one instance changes the variable's value, all instances access the updated value.  
  
 Sharing does not alter the access level of a member. For example, a class member can be shared and private (accessible only from within the class), or nonshared and public. For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>ルール  
  
- **Declaration Context.** `Shared` は、モジュール レベルでのみ使用できます。 This means the declaration context for a `Shared` element must be a class or structure, and cannot be a source file, namespace, or procedure.  
  
- **Combined Modifiers.** You cannot specify `Shared` together with [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md), [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md), [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md), or [Static](../../../visual-basic/language-reference/modifiers/static.md) in the same declaration.  
  
- **Accessing.** You access a shared element by qualifying it with its class or structure name, not with the variable name of a specific instance of its class or structure. You do not even have to create an instance of a class or structure to access its shared members.  
  
     The following example calls the shared procedure <xref:System.Double.IsNaN%2A> exposed by the <xref:System.Double> structure.  
  
     `If Double.IsNaN(result) Then MsgBox("Result is mathematically undefined.")`  
  
- **Implicit Sharing.** You cannot use the `Shared` modifier in a [Const Statement](../../../visual-basic/language-reference/statements/const-statement.md), but constants are implicitly shared. Similarly, you cannot declare a member of a module or an interface to be `Shared`, but they are implicitly shared.  
  
## <a name="behavior"></a>動作  
  
- **Storage.** A shared variable or event is stored in memory only once, no matter how many or few instances you create of its class or structure. Similarly, a shared procedure or property holds only one set of local variables.  
  
- **Accessing through an Instance Variable.** It is possible to access a shared element by qualifying it with the name of a variable that contains a specific instance of its class or structure. Although this usually works as expected, the compiler generates a warning message and makes the access through the class or structure name instead of the variable.  
  
- **Accessing through an Instance Expression.** If you access a shared element through an expression that returns an instance of its class or structure, the compiler makes the access through the class or structure name instead of evaluating the expression. This produces unexpected results if you intended the expression to perform other actions as well as returning the instance. 次に例を示します。  
  
    ```vb
    Sub main()  
        shareTotal.total = 10  
        ' The preceding line is the preferred way to access total.  
        Dim instanceVar As New shareTotal  
        instanceVar.total += 100  
        ' The preceding line generates a compiler warning message and  
        ' accesses total through class shareTotal instead of through  
        ' the variable instanceVar. This works as expected and adds  
        ' 100 to total.  
        returnClass().total += 1000  
        ' The preceding line generates a compiler warning message and  
        ' accesses total through class shareTotal instead of calling  
        ' returnClass(). This adds 1000 to total but does not work as  
        ' expected, because the MsgBox in returnClass() does not run.  
        MsgBox("Value of total is " & CStr(shareTotal.total))  
    End Sub  
    Public Function returnClass() As shareTotal  
        MsgBox("Function returnClass() called")  
        Return New shareTotal  
    End Function  
    Public Class shareTotal  
        Public Shared total As Integer  
    End Class  
    ```  
  
     In the preceding example, the compiler generates a warning message both times the code accesses the shared variable `total` through an instance. In each case it makes the access directly through the class `shareTotal` and does not make use of any instance. In the case of the intended call to the procedure `returnClass`, this means it does not even generate a call to `returnClass`, so the additional action of displaying "Function returnClass() called" is not performed.  
  
 `Shared` 修飾子は、次のコンテキストで使用できます。  
  
 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Operator ステートメント](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>関連項目

- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
- [Static](../../../visual-basic/language-reference/modifiers/static.md)
- [Lifetime in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [手順](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [構造体](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [クラスとオブジェクト](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
