---
title: 引数の値渡しと参照渡しの違い
ms.date: 07/20/2015
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- procedures [Visual Basic], passing arguments
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
ms.assetid: 5f5c38fe-3e2d-494c-8fff-f4025b55ec93
ms.openlocfilehash: 84ec3bac2532b2cef72ddda347251bc987801c3b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74341230"
---
# <a name="differences-between-passing-an-argument-by-value-and-by-reference-visual-basic"></a>引数の値渡しと参照渡しの違い (Visual Basic)
When you pass one or more arguments to a procedure, each argument corresponds to an underlying programming element in the calling code. You can pass either the value of this underlying element, or a reference to it. This is known as the *passing mechanism*.  
  
## <a name="passing-by-value"></a>値渡し  
 You pass an argument *by value* by specifying the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) keyword for the corresponding parameter in the procedure definition. When you use this passing mechanism, Visual Basic copies the value of the underlying programming element into a local variable in the procedure. The procedure code does not have any access to the underlying element in the calling code.  
  
## <a name="passing-by-reference"></a>Passing by Reference  
 You pass an argument *by reference* by specifying the [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword for the corresponding parameter in the procedure definition. When you use this passing mechanism, Visual Basic gives the procedure a direct reference to the underlying programming element in the calling code.  
  
## <a name="passing-mechanism-and-element-type"></a>Passing Mechanism and Element Type  
 The choice of passing mechanism is not the same as the classification of the underlying element type. Passing by value or by reference refers to what Visual Basic supplies to the procedure code. A value type or reference type refers to how a programming element is stored in memory.  
  
 However, the passing mechanism and element type are interrelated. The value of a reference type is a pointer to the data elsewhere in memory. This means that when you pass a reference type by value, the procedure code has a pointer to the underlying element's data, even though it cannot access the underlying element itself. For example, if the element is an array variable, the procedure code does not have access to the variable itself, but it can access the array members.  
  
## <a name="ability-to-modify"></a>Ability to Modify  
 When you pass a nonmodifiable element as an argument, the procedure can never modify it in the calling code, whether it is passed `ByVal` or `ByRef`.  
  
 For a modifiable element, the following table summarizes the interaction between the element type and the passing mechanism.  
  
|要素型|Passed `ByVal`|Passed `ByRef`|  
|------------------|--------------------|--------------------|  
|Value type (contains only a value)|The procedure cannot change the variable or any of its members.|The procedure can change the variable and its members.|  
|Reference type (contains a pointer to a class or structure instance)|The procedure cannot change the variable but can change members of the instance to which it points.|The procedure can change the variable and members of the instance to which it points.|  
  
## <a name="see-also"></a>関連項目

- [手順](./index.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [方法: プロシージャに引数を渡す](./how-to-pass-arguments-to-a-procedure.md)
- [引数の値渡しと参照渡し](./passing-arguments-by-value-and-by-reference.md)
- [変更できる引数と変更できない引数の違い](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [方法: プロシージャ引数の値を変更する](./how-to-change-the-value-of-a-procedure-argument.md)
- [方法: プロシージャ引数の値が変化しないようにする](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [方法: 引数の値渡しを強制する](./how-to-force-an-argument-to-be-passed-by-value.md)
- [位置と名前による引数渡し](./passing-arguments-by-position-and-by-name.md)
- [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
