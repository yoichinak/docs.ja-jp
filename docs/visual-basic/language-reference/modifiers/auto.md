---
title: 自動
ms.date: 07/20/2015
f1_keywords:
- vb.Auto
helpviewer_keywords:
- Auto keyword [Visual Basic], external references
- Declare statement [Visual Basic], marshaling strings
- Auto keyword [Visual Basic]
- Auto keyword [Visual Basic], marshaling strings
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
ms.openlocfilehash: 7ea46e5f8b882bb986f23e792b240bad0c5be7a5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351617"
---
# <a name="auto-visual-basic"></a>Auto (Visual Basic)
Specifies that Visual Basic should marshal strings according to .NET Framework rules based on the external name of the external procedure being declared.  
  
 When you call a procedure defined outside your project, the Visual Basic compiler does not have access to the information it must have to call the procedure correctly. This information includes where the procedure is located, how it is identified, its calling sequence and return type, and the string character set it uses. The [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) creates a reference to an external procedure and supplies this necessary information.  
  
 The `charsetmodifier` part in the `Declare` statement supplies the character set information for marshaling strings during a call to the external procedure. It also affects how Visual Basic searches the external file for the external procedure name. The `Auto` modifier specifies that Visual Basic should marshal strings according to .NET Framework rules, and that it should determine the base character set of the run-time platform and possibly modify the external procedure name if the initial search fails. For more information, see "Character Sets" in [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md).  
  
 If no character set modifier is specified, `Ansi` is the default.  
  
## <a name="remarks"></a>Remarks  
 The `Auto` modifier can be used in this context:  
  
 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Smart Device Developer Notes  
 This keyword is not supported.  
  
## <a name="see-also"></a>関連項目

- [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)
- [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)
- [キーワード](../../../visual-basic/language-reference/keywords/index.md)
