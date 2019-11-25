---
title: 演算子の効率のよい組み合わせ
ms.date: 07/20/2015
helpviewer_keywords:
- expressions [Visual Basic], parentheses
- operators [Visual Basic], associativity
- expressions [Visual Basic], operators
- operators [Visual Basic], precedence
- Visual Basic code, operators
- Visual Basic code, expressions
- operators [Visual Basic], complex expressions
- expressions [Visual Basic], complex
- parentheses [Visual Basic], complex expressions
- numeric expressions
ms.assetid: bd22340e-b5be-458b-8772-3916c02309a4
ms.openlocfilehash: 83ad53e4c75490a75eba0f80a6bf0f078aa4d426
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348996"
---
# <a name="efficient-combination-of-operators-visual-basic"></a>演算子の効率のよい組み合わせ (Visual Basic)
Complex expressions can contain many different operators. 次に例を示します。  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 Creating complex expressions such as the one in the preceding example requires a thorough understanding of the rules of operator precedence. For more information, see [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).  
  
## <a name="parenthetical-expressions"></a>Parenthetical Expressions  
 Often you want operations to proceed in a different order from that determined by operator precedence. 例を次に示します。  
  
 `x = z * y + 4`  
  
 The preceding example multiplies `z` by `y`, then adds the result to `4`. But if you want to add `y` and `4` before multiplying the result by `z`, you can override normal operator precedence by using parentheses. By enclosing an expression in parentheses, you force that expression to be evaluated first, regardless of operator precedence. To force the preceding example to do the addition first, you could rewrite it as in the following example.  
  
 `x = z * (y + 4)`  
  
 The preceding example adds `y` and `4`, then multiplies that sum by `z`.  
  
### <a name="nested-parenthetical-expressions"></a>Nested Parenthetical Expressions  
 You can nest expressions in multiple levels of parentheses to override precedence even further. The expressions most deeply nested in parentheses are evaluated first, followed by the next most deeply nested, and so on to the least deeply nested, and finally the expressions outside parentheses. 次に例を示します。  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 In the preceding example, `z + 2` is evaluated first, then the other parenthetical expressions. Exponentiation, which normally has higher precedence than addition or multiplication, is evaluated last in this example because the other expressions are enclosed in parentheses.  
  
## <a name="see-also"></a>関連項目

- [Arithmetic Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Comparison Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [Logical/Bitwise Operators (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [ブール式](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [値の比較](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [方法 : 数値を計算する](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)
- [Visual Basic における演算子の優先順位](../../../../visual-basic/language-reference/operators/operator-precedence.md)
