---
title: ディレクティブ (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
ms.openlocfilehash: 38d54feae5cf7bf41a825d1f6000811e2b56f319
ms.sourcegitcommit: 4c41ec195caf03d98b7900007c3c8e24eba20d34
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/20/2019
ms.locfileid: "67268210"
---
# <a name="directives-visual-basic"></a>ディレクティブ (Visual Basic)
このセクションのトピックでは、Visual Basic ソース コードのコンパイラ ディレクティブについて説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [#Const ディレクティブ](../../../visual-basic/language-reference/directives/const-directive.md)--コンパイラ定数の定義  
  
 [#ExternalSource ディレクティブ](../../../visual-basic/language-reference/directives/externalsource-directive.md)--ソース行とソース外部のテキストの間のマッピングを示します  
  
 [#If.Then... #Else ディレクティブ](../../../visual-basic/language-reference/directives/if-then-else-directives.md)--選択したコード ブロックのコンパイル  
  
 [#Region ディレクティブ](../../../visual-basic/language-reference/directives/region-directive.md): 折りたたむし、Visual Studio エディターでコードのセクションを非表示にします。  
  
 **#Disable、#Enable** : 無効にして、コードの領域の特定の警告を有効にします。  
  
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
