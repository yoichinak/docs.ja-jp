---
title: 宣言コンテキストと既定のアクセス レベル
ms.date: 07/20/2015
helpviewer_keywords:
- module level, defined
- declaration contexts, Visual Basic
- procedure level, defined
- namespace level, defined
- access levels, Visual Basic
- access levels, default levels
ms.assetid: bf63b96e-e825-4745-88c8-5dae222728db
ms.openlocfilehash: 1ba25d830b1e7529bdf09c1195cc1fe7f9b2243b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354103"
---
# <a name="declaration-contexts-and-default-access-levels-visual-basic"></a>宣言コンテキストと既定のアクセス レベル (Visual Basic)
This topic describes which Visual Basic types can be declared within which other types, and what their access levels default to if not specified.  
  
## <a name="declaration-context-levels"></a>Declaration Context Levels  
 The *declaration context* of a programming element is the region of code in which it is declared. This is often another programming element, which is then called the *containing element*.  
  
 The levels for declaration contexts are the following:  
  
- *Namespace level* — within a source file or namespace but not within a class, structure, module, or interface  
  
- *Module level* — within a class, structure, module, or interface but not within a procedure or block  
  
- *Procedure level* — within a procedure or block (such as `If` or `For`)  
  
 The following table shows the default access levels for various declared programming elements, depending on their declaration contexts.  
  
|宣言された要素|Namespace level|Module level|Procedure level|  
|----------------------|---------------------|------------------|---------------------|  
|Variable ([Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md))|使用できません|`Private` (`Public` in `Structure`, not allowed in `Interface`)|`Public`|  
|Constant ([Const Statement](../../../visual-basic/language-reference/statements/const-statement.md))|使用できません|`Private` (`Public` in `Structure`, not allowed in `Interface`)|`Public`|  
|Enumeration ([Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md))|`Friend`|`Public`|使用できません|  
|Class ([Class Statement](../../../visual-basic/language-reference/statements/class-statement.md))|`Friend`|`Public`|使用できません|  
|Structure ([Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md))|`Friend`|`Public`|使用できません|  
|Module ([Module Statement](../../../visual-basic/language-reference/statements/module-statement.md))|`Friend`|使用できません|使用できません|  
|Interface ([Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md))|`Friend`|`Public`|使用できません|  
|Procedure ([Function Statement](../../../visual-basic/language-reference/statements/function-statement.md), [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md))|使用できません|`Public`|使用できません|  
|External reference ([Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md))|使用できません|`Public` (not allowed in `Interface`)|使用できません|  
|Operator ([Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md))|使用できません|`Public` (not allowed in `Interface` or `Module`)|使用できません|  
|Property ([Property Statement](../../../visual-basic/language-reference/statements/property-statement.md))|使用できません|`Public`|使用できません|  
|Default property ([Default](../../../visual-basic/language-reference/modifiers/default.md))|使用できません|`Public` (not allowed in `Module`)|使用できません|  
|Event ([Event Statement](../../../visual-basic/language-reference/statements/event-statement.md))|使用できません|`Public`|使用できません|  
|Delegate ([Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md))|`Friend`|`Public`|使用できません|  
  
 For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="see-also"></a>関連項目

- [Friend](../../../visual-basic/language-reference/modifiers/friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Public](../../../visual-basic/language-reference/modifiers/public.md)
