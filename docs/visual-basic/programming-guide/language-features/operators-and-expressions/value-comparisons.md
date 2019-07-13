---
title: 値の比較 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], comparing values
- Visual Basic code, operators
- Visual Basic code, expressions
- comparison operators [Visual Basic], comparing expressions
- numeric expressions
- operators [Visual Basic], comparison
- expressions [Visual Basic], comparing
ms.assetid: 60da0c76-9458-4afc-97e9-44a7939c064c
ms.openlocfilehash: 270b226d0a1aa7d08721e6f9ed36d68492685af3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864392"
---
# <a name="value-comparisons-visual-basic"></a>値の比較 (Visual Basic)
比較演算子は、数値変数の値を比較する式を作成できます。 これらの式を返す、`Boolean`比較が true かどうかに基づいて、値または false。 このような式の例は次のとおりです。  
  
 `45 > 26`  
  
 `26 > 45`  
  
 最初の式の評価が`True`45 が 26 よりも大きいためです。 2 番目の例を評価する`False`26 は 45 より大きいためです。  
  
 この方法での数値式を比較することもできます。 次の例のように、複雑な式を比較する式をできます自体あります。  
  
 `x / 45 * (y +17) >= System.Math.Sqrt(z) / (p - (x * 16))`  
  
 上記の複雑な式には、リテラル、変数、および関数呼び出しが含まれています。 比較演算子の両側の式を評価し、結果として得られる値が比較を使用し、`>=`比較演算子。 左側にある式の値がより大きいか、右の式の値と等しい、全体の式の評価が`True`。 それ以外に評価されます`False`します。  
  
 値を比較する式で最もよく使用される`If...Then`構造は、次の例に示すようにします。  
  
 [!code-vb[VbVbalrOperators#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#84)]  
  
 `=`符号は、比較演算子と代入演算子。 比較演算子として使用する場合は、次の例に示すように、左側の値が、右側の値と等しいかどうかを評価します。  
  
 [!code-vb[VbVbalrOperators#85](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#85)]  
  
 任意の場所、比較式を使用することもできます。、`Boolean`の値が必要なようにこのような、 `If`、 `While`、 `Loop`、または`ElseIf`ステートメント、またはへの割り当てに値を渡しているか、`Boolean`変数。 次の例では、比較式によって返される値が割り当てられている、`Boolean`変数。  
  
 [!code-vb[VbVbalrOperators#86](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#86)]  
  
## <a name="see-also"></a>関連項目

- [ブール式](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [演算子および式](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Visual Basic における比較演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [方法: 数値を計算します。](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)
- [Visual Basic における演算子の優先順位](../../../../visual-basic/language-reference/operators/operator-precedence.md)
