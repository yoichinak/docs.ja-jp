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
ms.openlocfilehash: 16149ce42e3476cf07a62298f83734fee9ec7253
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957768"
---
# <a name="rem-statement-visual-basic"></a>REM ステートメント (Visual Basic)
プログラムのソースコードに説明の解説を含めるために使用されます。  
  
## <a name="syntax"></a>構文  
  
```  
REM comment  
' comment  
```  
  
## <a name="parts"></a>指定項目  
 `comment`  
 任意。 追加するコメントのテキスト。 キーワードと`REM` `comment`の間にはスペースが必要です。  
  
## <a name="remarks"></a>Remarks  
 ステートメントを`REM`行に単独で配置することも、別のステートメントの後の行に配置することもできます。 `REM`ステートメントは、行の最後のステートメントである必要があります。 別のステートメントの後にある`REM`場合は、をスペースでそのステートメントから区切る必要があります。  
  
 では`'` `REM`なく単一引用符 () を使用できます。 これは、コメントが同じ行で別のステートメントに続くか、または行に単独で存在するかにかかわらず当てはまります。  
  
> [!NOTE]
> 行連結シーケンス ( `REM` `_`) を使用してステートメントを続行することはできません。 コメントが開始されると、コンパイラは文字が特別な意味を持つかどうかを検査しません。 複数行のコメントの場合は、各行`REM`に別のステートメントまたは`'`コメント記号 () を使用します。  
  
## <a name="example"></a>例  
 次の例は、 `REM`ステートメントを示しています。これは、プログラムに説明の解説を含めるために使用されます。 また、の`'` `REM`代わりに単一引用符文字 () を使用する方法についても説明します。  
  
 [!code-vb[VbVbalrStatements#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>関連項目

- [コード内のコメント](../../../visual-basic/programming-guide/program-structure/comments-in-code.md)
- [方法: コード内でステートメントを分割および連結する](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
