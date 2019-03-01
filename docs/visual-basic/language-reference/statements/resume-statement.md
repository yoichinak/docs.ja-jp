---
title: Resume ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Resume
- vb.ResumeNext
helpviewer_keywords:
- Next statement [Visual Basic], Resume
- Resume Next statement [Visual Basic]
- execution [Visual Basic], resuming
- run-time errors [Visual Basic], resuming after
- Resume statement [Visual Basic], syntax
- errors [Visual Basic], resuming after
- Error statement [Visual Basic], and Resume statement
- execution
- Resume statement [Visual Basic]
ms.assetid: e24d058b-1a5c-4274-acb9-7d295d3ea537
ms.openlocfilehash: fcb50a9c7e36bab046be25d7f82f91cfe0f9be8e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966919"
---
# <a name="resume-statement"></a>Resume ステートメント
エラー処理ルーチンを完了した後は、実行を再開します。  
  
 非構造化例外処理を使用するのではなく、可能であれば、コード内の構造化例外処理を使用することをお勧め、`On Error`と`Resume`ステートメント。 詳細については、[Try...Catch...Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)を参照してください。  
  
## <a name="syntax"></a>構文  
  
```  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a>指定項目  
 `Resume`  
 必須。 エラー ハンドラーと同じ手順でエラーが発生した場合、エラーの原因となったステートメントを使用して実行を再開します。 呼び出されたプロシージャでエラーが発生した場合は、最後に、エラー処理ルーチンを含むプロシージャから呼び出されたステートメントの実行が再開されます。  
  
 `Next`  
 任意。 エラー ハンドラーと同じ手順でエラーが発生した場合、エラーの原因となったステートメントの直後のステートメントの実行が再開されます。 最後に、エラー処理ルーチンを含むプロシージャから呼び出されたステートメントの直後のステートメントの実行が再開される呼び出されたプロシージャでエラーが発生した場合 (または`On Error Resume Next`ステートメント)。  
  
 `line`  
 任意。 要求で指定した行で実行が再開される`line`引数。 `line`引数を行ラベルまたは行番号、エラー ハンドラーと同じ手順である必要があります。  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
>  非構造化例外処理を使用するのではなく、可能であれば、コード内の構造化例外処理を使用することをお勧め、`On Error`と`Resume`ステートメント。 詳細については、[Try...Catch...Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)を参照してください。  
  
 使用する場合、`Resume`ステートメント任意の場所以外のエラー処理ルーチンで、エラーが発生します。  
  
 `Resume`を含むすべてのプロシージャでは、ステートメントを使用できません、`Try...Catch...Finally`ステートメント。  
  
## <a name="example"></a>例  
 この例では、`Resume`ステートメントをプロシージャのエラー処理を終了し、エラーの原因となったステートメントの実行を再開します。 使用方法を説明するエラー番号 55 が生成された、`Resume`ステートメント。  
  
 [!code-vb[VbVbalrErrorHandling#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#16)]  
  
## <a name="requirements"></a>必要条件  
 **名前空間:**[Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **アセンブリ:** Visual Basic ランタイム ライブラリ (Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>関連項目
- [Try...Catch...Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Error ステートメント](../../../visual-basic/language-reference/statements/error-statement.md)
- [On Error ステートメント](../../../visual-basic/language-reference/statements/on-error-statement.md)
