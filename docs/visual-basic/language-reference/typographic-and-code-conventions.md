---
title: 表記規則とコード規則
ms.date: 07/20/2015
helpviewer_keywords:
- coding conventions [Visual Basic], Visual Basic
- best practices [Visual Basic], coding conventions
- conventions [Visual Basic], Visual Basic coding
- typographic conventions [Visual Basic]
- document conventions [Visual Basic]
- conventions [Visual Basic], documentation
- Visual Basic code, conventions
ms.assetid: 1916cd81-ea9d-4faa-81f7-4a0d864b60f4
ms.openlocfilehash: 4906c5ebadb7ce77f2d0e53b2fc5dbab69c5b41f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352711"
---
# <a name="typographic-and-code-conventions-visual-basic"></a>表記規則とコード規則 (Visual Basic)

Visual Basic documentation uses the following typographic and code conventions.  
  
## <a name="typographic-conventions"></a>Typographic Conventions  
  
|例|説明|  
|-------------|-----------------|  
|`Sub`、 `If`、 `ChDir`、 `Print`、 `True`、 `Debug`|Language-specific keywords and runtime members have initial uppercase letters and are formatted as shown in this example.|  
|**SmallProject**, **ButtonCollection**|Words and phrases you are instructed to type are formatted as shown in this example.|  
|[Module ステートメント](../../visual-basic/language-reference/statements/module-statement.md)|Links you can click to go to another Help page are formatted as shown in this example.|  
|*object*, *variableName*, `argumentList`|Placeholders for information that you supply are formatted as shown in this example.|  
|[ Shadows ], [ *expressionList* ]|In syntax, optional items are enclosed in brackets.|  
|{ `Public` &#124; `Friend` &#124; `Private` }|In syntax, when you must make a choice between two or more items, the items are enclosed in braces and separated by vertical bars.<br /><br /> You must select one, and only one, of the items.|  
|[ `Protected` &#124; `Friend` ]|In syntax, when you have the option of selecting between two or more items, the items are enclosed in square brackets and separated by vertical bars.<br /><br /> You can select any combination of the items, or no item.|  
|[{ `ByVal` &#124; `ByRef` }]|In syntax, when you can select no more than one item, but you can also omit the items completely, the items are enclosed in square brackets surrounded by braces and separated by vertical bars.|  
|*memberName*1, *memberName*2, *memberName*3|Multiple instances of the same placeholder are differentiated by subscripts, as shown in the example.|  
|*memberName1*<br /><br /> ...<br /><br /> *memberNameN*|In syntax, an ellipsis (...) is used to indicate an indefinite number of items of the kind immediately in front of the ellipsis.<br /><br /> In code, ellipses signify code omitted for the sake of clarity.|  
|ESC, ENTER|Key names and key sequences on the keyboard appear in all uppercase letters.|  
|ALT+F1|When plus signs (+) appear between key names, you must hold down one key while pressing the other. For example, ALT+F1 means hold down the ALT key while pressing the F1 key.|  
  
## <a name="code-conventions"></a>Code Conventions  
  
|例|説明|  
|-------------|-----------------|  
|`sampleString = "Hello, world!"`|Code samples appear in a fixed-pitch font and are formatted as shown in this example.|  
|The previous statement sets the value of `sampleString` to "Hello, world!"|Code elements in explanatory text appear in a fixed-pitch font, as shown in this example.|  
|`' This is a comment.`<br /><br /> `REM This is also a comment.`|Code comments are introduced by an apostrophe (') or the REM keyword.|  
|`sampleVar = "This is an " _`<br /><br /> `& "example" _`<br /><br /> `& " of how to continue code."`|A space followed by an underscore ( _) at the end of a line indicates that the statement continues on the following line.|  
  
## <a name="see-also"></a>関連項目

- [Visual Basic の言語リファレンス](../../visual-basic/language-reference/index.md)
- [キーワード](../../visual-basic/language-reference/keywords/index.md)
- [Visual Basic ランタイム ライブラリのメンバー](../../visual-basic/language-reference/runtime-library-members.md)
- [Visual Basic Naming Conventions](../../visual-basic/programming-guide/program-structure/naming-conventions.md)
- [方法 : コード内でステートメントを分割および連結する](../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
- [コード内のコメント](../../visual-basic/programming-guide/program-structure/comments-in-code.md)
