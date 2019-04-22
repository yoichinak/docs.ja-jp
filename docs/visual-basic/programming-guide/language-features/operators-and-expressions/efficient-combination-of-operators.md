---
title: 演算子の効率のよい組み合わせ (Visual Basic)
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
ms.openlocfilehash: 8f5dd6c56b3e4576b9d798e0e5e10b2996f558dc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58841259"
---
# <a name="efficient-combination-of-operators-visual-basic"></a>演算子の効率のよい組み合わせ (Visual Basic)
複雑な式は、さまざまな演算子を含めることができます。 次に例を示します。  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 前の例などの複雑な式を作成するには、演算子の優先順位の規則について理解する必要があります。 詳細については、次を参照してください。 [Visual Basic における演算子の優先順位](../../../../visual-basic/language-reference/operators/operator-precedence.md)します。  
  
## <a name="parenthetical-expressions"></a>かっこで囲まれた式  
 多くの場合、演算子の優先順位によって決定されるとは異なる順序で演算を実行します。 例を次に示します。  
  
 `x = z * y + 4`  
  
 前の例を乗算します`z`によって`y`、結果を追加します`4`します。 追加する場合は`y`と`4`には、結果を乗算する前に`z`かっこを使用して通常の演算子の優先順位をオーバーライドすることができます。 式をかっこで囲んで、演算子の優先順位に関係なく、最初に、評価される式を強制します。 最初に、加算を行うには、前の例を強制するには、次の例のように書き直すことができます。  
  
 `x = z * (y + 4)`  
  
 前の例では、追加`y`と`4`、によってその合計を掛けた`z`します。  
  
### <a name="nested-parenthetical-expressions"></a>入れ子になったかっこで囲まれた式  
 複数のレベルのさらに優先順位をオーバーライドするためにかっこで式を入れ子にすることができます。 かっこで囲まれた最も深く入れ子になった式は、最も深く入れ子になったこれに最も深く入れ子になった、および最後に式を次に最初に評価されます。 次に例を示します。  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 前の例では、`z + 2`は、最初に評価し、その他のかっこで囲まれた式。 指数演算は、通常は、加算や乗算より高い優先順位はこの例での最後に評価されます他の式がかっこで囲まれているためです。  
  
## <a name="see-also"></a>関連項目

- [Visual Basic における算術演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Visual Basic における比較演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Visual Basic での論理とビット処理演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [論理/ビット演算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [ブール式](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [値の比較](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [方法: 数値を計算します。](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)
- [Visual Basic における演算子の優先順位](../../../../visual-basic/language-reference/operators/operator-precedence.md)
