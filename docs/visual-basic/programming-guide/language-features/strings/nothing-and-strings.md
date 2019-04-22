---
title: Visual Basic の Nothing と文字列
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: 5fbcf86261892e3eb8e43ee8eaa3728cd8e42ced
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58841889"
---
# <a name="nothing-and-strings-in-visual-basic"></a>Visual Basic の Nothing と文字列
Visual Basic ランタイムと[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]評価`Nothing`が異なるとなる文字列。  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a>Visual Basic ランタイムと .NET Framework  
 次に例を示します。  
  
 [!code-vb[VbVbalrStrings#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#47)]  
  
 Visual Basic ランタイムは、通常は評価`Nothing`として空の文字列 ("")。 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]ただし、していないと、文字列操作を実行する試行が行われるたびに、例外をスローします`Nothing`します。  
  
## <a name="see-also"></a>関連項目

- [Visual Basic の文字列の概要](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
