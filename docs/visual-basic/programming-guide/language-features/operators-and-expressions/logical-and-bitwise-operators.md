---
title: Visual Basic の論理演算子とビット処理演算子
ms.date: 07/20/2015
helpviewer_keywords:
- short-circuiting
- Boolean expressions
- logical operators [Visual Basic], Boolean expressions
- operators [Visual Basic], logical
- AndAlso operator [Visual Basic]
- Not operator [Visual Basic], Boolean expressions
- Xor operator [Visual Basic], Boolean expressions
- And operator [Visual Basic], logical operators
- logical operators [Visual Basic]
- expressions [Visual Basic], Boolean
- Or operator [Visual Basic], logical operators
- Visual Basic code, operators
- short-circuiting [Visual Basic], logical operators
- logical operators [Visual Basic], short-circuiting
- Visual Basic code, expressions
- logical operators [Visual Basic], binary
- OrElse operator [Visual Basic]
- logical operators [Visual Basic], unary
ms.assetid: ca474e13-567d-4b1d-a18b-301433705e57
ms.openlocfilehash: 40076b2ad6606b4c565bcd39dbeea9e55da47211
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963319"
---
# <a name="logical-and-bitwise-operators-in-visual-basic"></a>Visual Basic の論理演算子とビット処理演算子
論理演算子は`Boolean` 、式を比較`Boolean`し、結果を返します。 `And` 、`Or`、 `Not` 、 、およびの各演算子は2つのオペランドを受け取りますが、演算子は単項演算であるため、二項演算子`AndAlso`です。 `OrElse` `Xor` これらの演算子の一部では、整数値に対してビットごとの論理演算を実行することもできます。  
  
## <a name="unary-logical-operator"></a>単項論理演算子  
 [Not 演算子](../../../../visual-basic/language-reference/operators/not-operator.md)は、 `Boolean`式の論理*否定*を実行します。 これにより、オペランドの論理逆が生成されます。 式がと`True`評価された場合`False` `Not` 、はを返します。 `False`式がと`True`評価された場合、 `Not`はを返します。 次に例を示します。  
  
 [!code-vb[VbVbalrOperators#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#77)]  
  
## <a name="binary-logical-operators"></a>二項論理演算子  
 [And 演算子](../../../../visual-basic/language-reference/operators/and-operator.md)は、2 `Boolean`つの式の論理積を実行します。 両方`True`の式がに`True`評価される場合、はを返します。`And` 少なくとも1つの式がに`False`評価さ`And`れる`False`場合、はを返します。  
  
 [Or 演算子](../../../../visual-basic/language-reference/operators/or-operator.md)は、2 `Boolean`つの式の論理*和*を実行します。 いずれかの式が`True`に評価された`True`場合、また`True`は両方がと評価された場合、 `Or`はを返します。 どちらの式もに`True`評価`Or`さ`False`れない場合、はを返します。  
  
 [Xor 演算子](../../../../visual-basic/language-reference/operators/xor-operator.md)は、2 `Boolean`つの式に対して論理的な除外を実行します。 1つの式だけがと`True`評価される場合、 `Xor`両方`True`ではなく、が返されます。 両方`True`の式がと評価されるか、両方`False`がに`False`評価される場合、 `Xor`はを返します。  
  
 次の例は、 `And`、 `Or`、および`Xor`の各演算子を示しています。  
  
 [!code-vb[VbVbalrOperators#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#78)]  
  
## <a name="short-circuiting-logical-operations"></a>ショートサーキット論理操作  
 [AndAlso 演算子](../../../../visual-basic/language-reference/operators/andalso-operator.md)は、2 `And` `Boolean`つの式に対して論理積も実行するという点で、演算子と非常によく似ています。 2つの間の主な違い`AndAlso`は、が*ショートサーキット*動作を示す点です。 `AndAlso`式の最初の式がに`False`評価される場合、2番目の式は評価されません。これは`AndAlso` 、 `False`最終的な結果を変更できず、がを返すためです。  
  
 同様に、 [OrElse 演算子](../../../../visual-basic/language-reference/operators/orelse-operator.md)は、2 `Boolean`つの式の短絡論理和を実行します。 `OrElse`式の最初の式がに`True`評価される場合、2番目の式は評価されません。これは`OrElse` 、 `True`最終的な結果を変更できず、がを返すためです。  
  
### <a name="short-circuiting-trade-offs"></a>ショートサーキットトレードオフ  
 ショートサーキットを使用すると、論理演算の結果を変更できない式を評価しないことで、パフォーマンスを向上させることができます。 ただし、その式が追加のアクションを実行する場合、ショートサーキットはこれらのアクションをスキップします。 たとえば、式に`Function`プロシージャへの呼び出しが含まれている場合、式が短いサーキットの場合、そのプロシージャは呼び出されず、に含まれる追加の`Function`コードは実行されません。 このため、関数は、ときどき実行される場合があり、正しくテストされない可能性があります。 または、プログラムロジックがの`Function`コードに依存している場合もあります。  
  
 次の例は、 `And`、 `Or`、および対応するショートサーキットの違いを示しています。  
  
 [!code-vb[VbVbalrOperators#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#81)]  
  
 [!code-vb[VbVbalrOperators#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#80)]  
  
 [!code-vb[VbVbalrOperators#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#79)]  
  
 前の例では、の一部の重要な`checkIfValid()`コードは、サーキットの呼び出しでは実行されないことに注意してください。 はショート`If`サーキットで`checkIfValid()`はない`12 > 45`ため`False` 、`And`最初のステートメントはを返します。 2番`If`目のステートメントは`checkIfValid()`を呼び出しません`False`。 `AndAlso`がを返した場合`12 > 45` 、2番目の式がショートサーキットされるためです。 3番`If`目のステートメントは`12 < 45`を`True`返します`Or`が、はショートサーキットではないため、を呼び出し`checkIfValid()`ます。 4 `If`番目のステートメントは`checkIfValid()`を呼び出しません`True`。 `OrElse`がを返した場合`12 < 45` 、2番目の式がショートサーキットされるためです。  
  
## <a name="bitwise-operations"></a>ビットごとの演算  
 ビットごとの演算では、2つの整数値が binary (base 2) 形式で評価されます。 これらは、対応する位置のビットを比較し、比較に基づいて値を割り当てます。 次の例は、 `And`演算子を示しています。  
  
 [!code-vb[VbVbalrConcepts#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConcepts/VB/Class1.vb#2)]  
  
 前の例では、の`x`値を1に設定しています。 これは、次の理由で発生します。  
  
- 値はバイナリとして扱われます。  
  
     3バイナリ形式の 3 = 011  
  
     5バイナリ形式 = 101  
  
- 演算子`And`は、一度に1つのバイナリ位置 (ビット) をバイナリ表現と比較します。 指定された位置にある両方のビットが1の場合、結果内のその位置に1が配置されます。 どちらかのビットが0の場合は、結果内のその位置に0が配置されます。 前の例では、これは次のように動作します。  
  
     011 (バイナリ形式の場合は 3)  
  
     101 (バイナリ形式で 5)  
  
     001 (バイナリ形式の結果)  
  
- 結果は decimal として扱われます。 値001は 1 `x`のバイナリ表現であり、= 1 です。  
  
 ビットごと`Or`の演算は似ていますが、比較対象のビットのいずれかまたは両方が1の場合、結果ビットに1が割り当てられる点が異なります。 `Xor`比較されたビットの1つ (両方ではない) が1の場合、結果のビットに1を割り当てます。 `Not`1つのオペランドを受け取り、符号ビットを含むすべてのビットを反転し、その値を結果に代入します。 つまり、符号付き正の数値の`Not`場合、は常に負の値を返し、 `Not`負の数値の場合は正の値または0を返します。  
  
 演算子`AndAlso` と`OrElse`演算子は、ビットごとの演算をサポートしません。  
  
> [!NOTE]
> ビットごとの演算は、整数型に対してのみ実行できます。 浮動小数点値は、ビットごとの演算を続行する前に、整数型に変換する必要があります。  
  
## <a name="see-also"></a>関連項目

- [論理/ビット演算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [ブール式](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [Visual Basic の算術演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Visual Basic の比較演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Visual Basic での連結演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
- [演算子の効率のよい組み合わせ](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
