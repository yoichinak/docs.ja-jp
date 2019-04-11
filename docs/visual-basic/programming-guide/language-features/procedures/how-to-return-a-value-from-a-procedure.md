---
title: '方法: プロシージャ (Visual Basic) から値を返す'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], returning from
- procedures [Visual Basic], returning a value
ms.assetid: 4bcc4724-2b4e-4df8-9b4b-16054607f87d
ms.openlocfilehash: 8b53df1634d2b9971bc44c968a17db81cac3924f
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59307887"
---
# <a name="how-to-return-a-value-from-a-procedure-visual-basic"></a>方法: プロシージャ (Visual Basic) から値を返す
A`Function`プロシージャに値を返す呼び出し元のコードを実行するか、`Return`ステートメントまたはを戻したり、`Exit Function`または`End Function`ステートメント。  
  
### <a name="to-return-a-value-using-the-return-statement"></a>Return ステートメントを使用して値を返す  
  
1. 配置、`Return`でプロシージャのタスクが完了した後の時点でのステートメント。  
  
2. に従って、`Return`呼び出し元のコードを取得するキーワード、値を生成する式をします。  
  
3. 同じプロシージャ内に複数の `Return` ステートメントを含めることができます。  
  
     次`Function`プロシージャが最長の辺の三角形の斜辺を計算し、呼び出し元のコードに返します。  
  
     [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
     次の例では、一般的な呼び出しを`hypotenuse`、返される値を格納します。  
  
     [!code-vb[VbVbcnProcedures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#6)]  
  
### <a name="to-return-a-value-using-exit-function-or-end-function"></a>Exit 関数または終了関数を使用して値を返す  
  
1. 内の少なくとも 1 か所で、`Function`プロシージャ、プロシージャ名に値を割り当てます。  
  
2. 実行すると、`Exit Function`または`End Function`ステートメントでは、Visual Basic は、プロシージャの名前を最も最近割り当てられた値を返します。  
  
3. 同じプロシージャ内に複数の `Exit Function` ステートメントを含めることができ、さらに同じプロシージャ内に `Return` ステートメントと `Exit Function` ステートメントを混在させることができます。  
  
4. 1 つのみできます`End Function`内のステートメントを`Function`プロシージャ。  
  
     詳細と例を参照してください「戻り値」[関数ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)します。  
  
## <a name="see-also"></a>関連項目

- [手順](./index.md)
- [Sub プロシージャ](./sub-procedures.md)
- [プロパティ プロシージャ](./property-procedures.md)
- [演算子プロシージャ](./operator-procedures.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [Function ステートメント](../../../../visual-basic/language-reference/statements/function-statement.md)
- [Return ステートメント](../../../../visual-basic/language-reference/statements/return-statement.md)
- [方法: 値を返すプロシージャを作成する](./how-to-create-a-procedure-that-returns-a-value.md)
- [方法: 値を返すプロシージャを呼び出す](./how-to-call-a-procedure-that-returns-a-value.md)
