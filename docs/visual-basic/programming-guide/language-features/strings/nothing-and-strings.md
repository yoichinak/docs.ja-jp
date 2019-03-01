---
title: Visual Basic の Nothing と文字列
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: 873c4e40a0b12dd657d3294785e04dd9efc23956
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967985"
---
# <a name="nothing-and-strings-in-visual-basic"></a>Visual Basic の Nothing と文字列
Visual Basic ランタイムと[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]評価`Nothing`が異なるとなる文字列。  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a>Visual Basic ランタイムと .NET Framework  
 次に例を示します。  
  
 [!code-vb[VbVbalrStrings#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#47)]  
  
 Visual Basic ランタイムは、通常は評価`Nothing`として空の文字列 ("")。 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]ただし、していないと、文字列操作を実行する試行が行われるたびに、例外をスローします`Nothing`します。  
  
## <a name="see-also"></a>関連項目
- [Visual Basic の文字列の概要](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
