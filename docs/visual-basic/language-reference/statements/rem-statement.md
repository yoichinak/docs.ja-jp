---
title: REM ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.'
- vb.Rem
- Rem
- "'"
helpviewer_keywords:
- REM statement [Visual Basic]
- comments, Visual Basic code
- code comments, Visual Basic
- Visual Basic code, comments
- "' comment marker character [Visual Basic]"
ms.assetid: 34126d7f-e0f9-476d-91e6-b31b398615dc
ms.openlocfilehash: b25910f5215585914094b7bc4420f537a400934b
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967999"
---
# <a name="rem-statement-visual-basic"></a>REM ステートメント (Visual Basic)
プログラムのソース コードにコメントを記述するために使用します。  
  
## <a name="syntax"></a>構文  
  
```  
REM comment  
' comment  
```  
  
## <a name="parts"></a>指定項目  
 `comment`  
 任意。 含めるコメントのテキスト。 スペースは間で必要な`REM`キーワードと`comment`します。  
  
## <a name="remarks"></a>Remarks  
 配置することができます、`REM`ステートメントまたは行に単独では別のステートメントの後にそれを配置できます。 `REM`ステートメントは、行の最後のステートメントである必要があります。 別のステートメントが続く場合、`REM`からそのステートメントをスペースで区切る必要があります。  
  
 単一引用符を使用することができます (`'`) の代わりに`REM`します。 これはコメントが同じ行に依存して別のステートメントまたは行に単独ではかどうかに当てはまります。  
  
> [!NOTE]
>  続行することはできません、`REM`行連結シーケンスを使用してステートメント (`_`)。 コメントが開始されると、コンパイラは特別な意味の文字をチェックしません。 複数行にコメントを記述する場合は、別の操作を使用して`REM`ステートメントまたはコメント記号 (`'`) 行ごとにします。  
  
## <a name="example"></a>例  
 次の例を示しています、`REM`ステートメントでは、プログラムにコメントを記述するために使用します。 単一引用符文字を使用する方法も示しています (`'`) の代わりに`REM`します。  
  
 [!code-vb[VbVbalrStatements#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>関連項目
- [コード内のコメント](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)
- [方法: コード内でステートメントを分割および連結する](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
