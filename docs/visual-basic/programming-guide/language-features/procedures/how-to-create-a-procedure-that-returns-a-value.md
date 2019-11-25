---
title: '方法 : 値を返すプロシージャを作成する'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], returning a value
ms.assetid: 8ee19f95-a9ef-4033-963b-d224dca207c4
ms.openlocfilehash: 218dbb52abc0100724d38d10be91ef24252d5226
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349722"
---
# <a name="how-to-create-a-procedure-that-returns-a-value-visual-basic"></a>方法: 値を返すプロシージャを作成する (Visual Basic)
You use a `Function` procedure to return a value to the calling code.  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a>To create a procedure that returns a value  
  
1. Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.  
  
2. In the `Function` statement, follow the `Function` keyword with the name of the procedure, and then the parameter list in parentheses.  
  
3. Follow the parentheses with an `As` clause to specify the data type of the returned value.  
  
4. Place the procedure's code statements between the `Function` and `End Function` statements.  
  
5. Use a `Return` statement to return the value to the calling code.  
  
     The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     The following example shows a typical call to `hypotenuse`.  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>関連項目

- [手順](./index.md)
- [Sub プロシージャ](./sub-procedures.md)
- [Property プロシージャ](./property-procedures.md)
- [演算子プロシージャ](./operator-procedures.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [Function ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)
- [方法 : プロシージャから値を返す](./how-to-return-a-value-from-a-procedure.md)
- [方法: 値を返すプロシージャを呼び出す](./how-to-call-a-procedure-that-returns-a-value.md)
