---
title: WriteOnly
ms.date: 07/20/2015
f1_keywords:
- WriteOnly
- vb.WriteOnly
helpviewer_keywords:
- write-only properties
- WriteOnly keyword [Visual Basic]
- sensitive data, protecting
- properties [Visual Basic], write-only
- sensitive data
ms.assetid: 488d2899-b09f-4cee-92f0-6f9f9fc4f944
ms.openlocfilehash: 847617ea6534089857a759fbea3bb16a3a5a36a1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344189"
---
# <a name="writeonly-visual-basic"></a>WriteOnly (Visual Basic)
Specifies that a property can be written but not read.  
  
## <a name="remarks"></a>Remarks  
  
## <a name="rules"></a>ルール  
 **Declaration Context.** `WriteOnly` は、モジュール レベルでのみ使用できます。 This means the declaration context for a `WriteOnly` property must be a class, structure, or module, and cannot be a source file, namespace, or procedure.  
  
 You can declare a property as `WriteOnly`, but not a variable.  
  
## <a name="when-to-use-writeonly"></a>When to Use WriteOnly  
 Sometimes you want the consuming code to be able to set a value but not discover what it is. For example, sensitive data, such as a social registration number or a password, needs to be protected from access by any component that did not set it. In these cases, you can use a `WriteOnly` property to set the value.  
  
> [!IMPORTANT]
> When you define and use a `WriteOnly` property, consider the following additional protective measures:  
  
- **Overriding.** If the property is a member of a class, allow it to default to [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md), and do not declare it `Overridable` or `MustOverride`. This prevents a derived class from making undesired access through an override.  
  
- **Access Level.** If you hold the property's sensitive data in one or more variables, declare them [Private](../../../visual-basic/language-reference/modifiers/private.md) so that no other code can access them.  
  
- **Encryption.** Store all sensitive data in encrypted form rather than in plain text. If malicious code somehow gains access to that area of memory, it is more difficult to make use of the data. Encryption is also useful if it is necessary to serialize the sensitive data.  
  
- **Resetting.** When the class, structure, or module defining the property is being terminated, reset the sensitive data to default values or to other meaningless values. This gives extra protection when that area of memory is freed for general access.  
  
- **Persistence.** Do not persist any sensitive data, for example on disk, if you can avoid it. Also, do not write any sensitive data to the Clipboard.  
  
 The `WriteOnly` modifier can be used in this context:  
  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="see-also"></a>関連項目

- [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [キーワード](../../../visual-basic/language-reference/keywords/index.md)
