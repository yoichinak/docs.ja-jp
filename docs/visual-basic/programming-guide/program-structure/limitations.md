---
title: 制限事項
ms.date: 07/20/2015
helpviewer_keywords:
- limits
- limitations [Visual Basic]
- limitations
- limits, Visual Basic code
- Visual Basic code, limitations
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
ms.openlocfilehash: f7e19977a011565bb4b1536af5cab195f8a01017
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347366"
---
# <a name="visual-basic-limitations"></a>Visual Basic の制限事項
Earlier versions of Visual Basic enforced boundaries in code, such as the length of variable names, the number of variables allowed in modules, and module size. In Visual Basic .NET, these restrictions have been relaxed, giving you greater freedom in writing and arranging your code.  
  
 Physical limits are dependent more on run-time memory than on compile-time considerations. If you use prudent programming practices, and divide large applications into multiple classes and modules, then there is very little chance of encountering an internal Visual Basic limitation.  
  
 The following are some limitations that you might encounter in extreme cases:  
  
- **Name Length.** There is a maximum number of characters for the name of every declared programming element. This maximum applies to an entire qualification string if the element name is qualified. 「 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。  
  
- **Line Length.** There is a maximum of 65535 characters in a physical line of source code. The logical source code line can be longer if you use line continuation characters. See [How to: Break and Combine Statements in Code](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md).  
  
- **Array Dimensions.** There is a maximum number of dimensions you can declare for an array. This limits how many indexes you can use to specify an array element. See [Array Dimensions in Visual Basic](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).  
  
- **String Length.** There is a maximum number of Unicode characters you can store in a single string. See [String Data Type](../../../visual-basic/language-reference/data-types/string-data-type.md).  
  
- **Environment String Length.** There is a maximum of 32768 characters for any environment string used as a command-line argument. This is a limitation on all platforms.  
  
## <a name="see-also"></a>関連項目

- [プログラム構造とコード規則](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [Visual Basic Naming Conventions](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)
