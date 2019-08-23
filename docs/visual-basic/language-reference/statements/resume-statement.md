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
ms.openlocfilehash: 884bdaa0c19508b5a6bf6377568a53acc6880518
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957692"
---
# <a name="resume-statement"></a>Resume ステートメント
エラー処理ルーチンが終了した後、実行を再開します。  
  
 構造化例外処理は、構造化されていない例外処理と`On Error` `Resume`ステートメントおよびステートメントを使用するのではなく、可能な限りコードで使用することをお勧めします。 詳細については、[Try...Catch...Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)を参照してください。  
  
## <a name="syntax"></a>構文  
  
```  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a>指定項目  
 `Resume`  
 必須。 エラーがエラーハンドラーと同じ手順で発生した場合は、エラーの原因となったステートメントを使用して実行が再開されます。 呼び出されたプロシージャでエラーが発生した場合、エラー処理ルーチンを含むプロシージャから最後に呼び出されたステートメントで実行が再開されます。  
  
 `Next`  
 任意。 エラーハンドラーと同じプロシージャでエラーが発生した場合は、エラーの原因となったステートメントの直後のステートメントを使用して実行が再開されます。 呼び出されたプロシージャでエラーが発生した場合、エラー処理ルーチン (または`On Error Resume Next`ステートメント) を含むプロシージャから最後に呼び出されたステートメントの直後にあるステートメントを使用して、実行が再開されます。  
  
 `line`  
 任意。 実行は、必要な`line`引数で指定した行で再開されます。 `line`引数は、行ラベルまたは行番号であり、エラーハンドラーと同じプロシージャ内にある必要があります。  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
> 構造化例外処理は、構造化されていない例外`On Error`処理、および`Resume`ステートメントおよびステートメントを使用するのではなく、可能な限りコードで使用することをお勧めします。 詳細については、[Try...Catch...Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)を参照してください。  
  
 エラー処理ルーチンで`Resume`以外の場所にあるステートメントを使用すると、エラーが発生します。  
  
 ステートメントは、ステートメントを`Try...Catch...Finally`含むプロシージャ内では使用できません。 `Resume`  
  
## <a name="example"></a>例  
 この例では`Resume` 、ステートメントを使用してプロシージャ内のエラー処理を終了し、エラーの原因となったステートメントを使用して実行を再開します。 ステートメントの使用方法を示すために、 `Resume`エラー番号55が生成されます。  
  
 [!code-vb[VbVbalrErrorHandling#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#16)]  
  
## <a name="requirements"></a>必要条件  
 **名前空間:** [Microsoft. Visual Basic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **組み立て**Visual Basic ランタイム ライブラリ (Microsoft.VisualBasic.dll)  
  
## <a name="see-also"></a>関連項目

- [Try...Catch...Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [Error ステートメント](../../../visual-basic/language-reference/statements/error-statement.md)
- [On Error ステートメント](../../../visual-basic/language-reference/statements/on-error-statement.md)
