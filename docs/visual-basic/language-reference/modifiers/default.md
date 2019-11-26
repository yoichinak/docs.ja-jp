---
title: 既定
ms.date: 07/20/2015
f1_keywords:
- vb.Default
helpviewer_keywords:
- defaults, properties
- properties [Visual Basic], default
- default properties, in Visual Basic
- Default keyword [Visual Basic]
- default properties
ms.assetid: 45fce9b9-d212-4b2d-ab86-6e359b8b57af
ms.openlocfilehash: ad4c9528f208cc2c31f07b0506d1b049a7568c86
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351577"
---
# <a name="default-visual-basic"></a>Default (Visual Basic)
Identifies a property as the default property of its class, structure, or interface.  
  
## <a name="remarks"></a>Remarks  
 A class, structure, or interface can designate at most one of its properties as the *default property*, provided that property takes at least one parameter. If code makes a reference to a class or structure without specifying a member, Visual Basic resolves that reference to the default property.  
  
 Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read. If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property. This can lead to compiler errors or subtle run-time logic errors.  
  
 You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) to set compiler type checking to `On`.  
  
 If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.  
  
 Because of these disadvantages, you should consider not defining default properties. For code readability, you should also consider always referring to all properties explicitly, even default properties.  
  
 The `Default` modifier can be used in this context:  
  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>関連項目

- [How to: Declare and Call a Default Property in Visual Basic](../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)
- [キーワード](../../../visual-basic/language-reference/keywords/index.md)
