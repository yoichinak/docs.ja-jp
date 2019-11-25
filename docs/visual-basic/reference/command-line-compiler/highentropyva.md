---
title: -highentropyva
ms.date: 03/10/2018
helpviewer_keywords:
- highentropyva compiler option (Visual Basic)
- /highentropyva compiler option (Visual Basic)
ms.assetid: ff25f20a-6ca2-467b-9e52-5cf439f5028e
ms.openlocfilehash: 7934dcaada4675bf687624bef5ed1ea25e842832
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344251"
---
# <a name="-highentropyva-visual-basic"></a>-highentropyva (Visual Basic)
Indicates whether a 64-bit executable or an executable that's marked by the [-platform:anycpu](../../../visual-basic/reference/command-line-compiler/platform.md) compiler option supports high entropy Address Space Layout Randomization (ASLR).  
  
## <a name="syntax"></a>構文  
  
```console  
-highentropyva[+ | -]  
```  
  
## <a name="arguments"></a>引数  
 `+` &#124; `-`  
 省略可能です。 The option is off by default or if you specify `-highentropyva-`. The option is on if you specify `-highentropyva` or `-highentropyva+`.  
  
## <a name="remarks"></a>Remarks  
 If you specify this option, compatible versions of the Windows kernel can use higher degrees of entropy when the kernel randomizes the address space layout of a process as part of ASLR. If the kernel uses higher degrees of entropy, a larger number of addresses can be allocated to memory regions such as stacks and heaps. これによって特定のメモリ領域の位置を推測しづらくなる効果が得られます。  
  
 When the option is on, the target executable and any modules on which it depends must be able to handle pointer values that are larger than 4 gigabytes (GB) when those modules are running as 64-bit processes.  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
