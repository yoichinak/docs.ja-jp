---
title: '#ExternalSource ディレクティブ'
ms.date: 07/20/2015
f1_keywords:
- '#Externalsource'
- '#ExternalSource'
- vb.ExternalSource
- Externalsource
- vb.#ExternalSource
- ExternalSource
helpviewer_keywords:
- ExternalSource directive (#ExternalSource)
- '#ExternalSource directive'
ms.assetid: 243bc6a2-34c3-4eeb-a776-9fd2bf988149
ms.openlocfilehash: fa0a40827c1b3865b90c7d796ea4dd364774e1c4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343830"
---
# <a name="externalsource-directive"></a>#ExternalSource ディレクティブ

Indicates a mapping between specific lines of source code and text external to the source.  
  
## <a name="syntax"></a>構文  
  
```vb  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a>指定項目  

 `StringLiteral`  
 The path to the external source.  
  
 `IntLiteral`  
 The line number of the first line of the external source.  
  
 `LogicalLine`  
 The line where the error occurs in the external source.  
  
 `#End ExternalSource`  
 `#ExternalSource` ブロックを終了します。  
  
## <a name="remarks"></a>Remarks  

 This directive is used only by the compiler and the debugger.  
  
 A source file may include external source directives, which indicate a mapping between specific lines of code in the source file and text external to the source, such as an .aspx file. If errors are encountered in the designated source code during compilation, they are identified as coming from the external source.  
  
 External source directives have no effect on compilation and cannot be nested. They are intended for internal use by the application only.  
  
## <a name="see-also"></a>関連項目

- [条件付きコンパイル](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
