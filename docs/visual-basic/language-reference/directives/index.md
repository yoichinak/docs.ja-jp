---
title: ディレクティブ
ms.date: 07/20/2015
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
ms.openlocfilehash: d76e10ad5ce8ad3accdc84f97146e0816048d8f3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343802"
---
# <a name="directives-visual-basic"></a>ディレクティブ (Visual Basic)

このセクションのトピックでは、Visual Basic ソース コードのコンパイラ ディレクティブについて説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  

 [#Const Directive](../../../visual-basic/language-reference/directives/const-directive.md) -- Define a compiler constant  
  
 [#ExternalSource Directive](../../../visual-basic/language-reference/directives/externalsource-directive.md) -- Indicate a mapping between source lines and text external to the source  
  
 [#If...Then...#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) -- Compile selected blocks of code  
  
 [#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md) -- Collapse and hide sections of code in the Visual Studio editor  
  
 **#Disable, #Enable** -- Disable and enable specific warnings for regions of code.  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
```  
  
 警告コードのコンマ区切りリストを無効および有効にすることもできます。  
  
## <a name="related-sections"></a>関連項目  

 [Visual Basic の言語リファレンス](../../../visual-basic/language-reference/index.md)  
  
 [Visual Basic](../../../visual-basic/index.md)
