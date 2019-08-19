---
title: '数値を計算する方法 (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- operator precedence
- operators [Visual Basic]
- expressions [Visual Basic], numeric
- calculations [Visual Basic], numeric expressions
- precedence [Visual Basic], of operators
- Visual Basic code, operators
- Visual Basic code, expressions
- numeric expressions
ms.assetid: ba6bf43d-bd96-49b8-b1de-4a7797551372
ms.openlocfilehash: 3e367a10a3e703241c7417d3ea17068018becb5a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649728"
---
# <a name="how-to-calculate-numeric-values-visual-basic"></a>数値を計算する方法 (Visual Basic)
数値式を使用して数値を計算することができます。 *数値式*リテラル、定数、および数値の値を表す変数を含む式とそれらの値に対して作用する演算子です。  
  
## <a name="calculating-numeric-values"></a>数値の計算  
  
#### <a name="to-calculate-a-numeric-value"></a>数値の値を計算するには  
  
- 数値式に 1 つまたは複数の数値リテラル、定数、および変数を結合します。 次の例は、いくつかの有効な数値式です。  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     最初の 3 つの行では、リテラル、定数、および変数を示します。 各 1 つは、単独で有効な数値式を形成します。 最後の行は、2 つのリテラルと変数の組み合わせを示しています。  
  
     数値式を単独で、完全な Visual Basic ステートメントが形成されていませんことに注意してください。 式は、完全なステートメントの一部として使用する必要があります。  
  
#### <a name="to-store-a-numeric-value"></a>数値の値を格納するには  
  
- 代入ステートメントを使用して、次の例に示すように、変数に数値式で表される値を割り当てることができます。  
  
     [!code-vb[VbVbalrOperators#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#82)]  
  
     前の例では、等値演算子の右側にある式の値 (`=`) 変数に割り当てられている`j`、演算子の左側にあるため、 `j` 276 に評価されます。  
  
     詳細については、「[ステートメント](../../../../visual-basic/language-reference/statements/index.md)」を参照してください。  
  
## <a name="multiple-operators"></a>複数の演算子  
 数値式には、複数の演算子が含まれている場合、演算子の優先順位のルールで評価される順序が決まります。 演算子の優先順位のルールを無効にするには、; 上記の例のように、かっこで囲まれた式を囲みます。囲まれた式は、最初に評価されます。  
  
#### <a name="to-override-normal-operator-precedence"></a>標準の演算子の優先順位をオーバーライドするには  
  
- かっこを使用して、先に実行する操作を囲みます。 次の例では、オペランドと演算子が同じで、2 つの異なる結果を示します。  
  
     [!code-vb[VbVbalrOperators#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#83)]  
  
     前の例では、計算で`j`加算演算子を実行します (`+`) 最初ので、かっこで囲んで`(67 + i)`通常の優先順位とに割り当てられた値をオーバーライド`j`276 (4 回 69) は、します。 計算`k`、通常の優先順位の演算子を実行します (`*`する前に`+`) とに割り当てられた値`k`270 (268 および 2)。  
  
     詳細については、次を参照してください。 [Visual Basic における演算子の優先順位](../../../../visual-basic/language-reference/operators/operator-precedence.md)します。  
  
## <a name="see-also"></a>関連項目

- [演算子および式](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [値の比較](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [ステートメント](../../../../visual-basic/language-reference/statements/index.md)
- [Visual Basic における演算子の優先順位](../../../../visual-basic/language-reference/operators/operator-precedence.md)
- [算術演算子](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [演算子の効率のよい組み合わせ](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
