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
ms.openlocfilehash: ac47b6d7fa4861d18646a23f442caccc4062852f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819308"
---
# <a name="logical-and-bitwise-operators-in-visual-basic"></a>Visual Basic の論理演算子とビット処理演算子
論理演算子は比較`Boolean`式と戻り値、`Boolean`結果。 `And`、 `Or`、 `AndAlso`、 `OrElse`、および`Xor`演算子は*バイナリ*中に 2 つのオペランドを考慮に入れるため、`Not`演算子は*単項* 1 つのオペランドがかかるためです。 整数値のビットごとの論理操作を実行中これらの演算子のこともできます。  
  
## <a name="unary-logical-operator"></a>単項論理演算子  
 [Not 演算子](../../../../visual-basic/language-reference/operators/not-operator.md)論理実行*否定*上、`Boolean`式。 オペランドの論理上の逆になります。 式が評価された場合`True`、し`Not`返します`False`に式が評価された場合は`False`、し`Not`を返します`True`します。 次に例を示します。  
  
 [!code-vb[VbVbalrOperators#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#77)]  
  
## <a name="binary-logical-operators"></a>二項論理演算子  
 [And 演算子](../../../../visual-basic/language-reference/operators/and-operator.md)論理実行*組み合わせて*2 つ`Boolean`式。 両方の式が評価される場合`True`、し`And`返します`True`します。 少なくとも 1 つの式の評価された場合`False`、し`And`返します`False`します。  
  
 [または演算子](../../../../visual-basic/language-reference/operators/or-operator.md)論理を実行します*和*または*包含*2 つ`Boolean`式。 いずれかの式が評価された場合`True`、または両方を評価する`True`、し`Or`返します`True`。 どちらの式に評価される場合`True`、`Or`返します`False`します。  
  
 [Xor 演算子](../../../../visual-basic/language-reference/operators/xor-operator.md)論理実行*除外*2 つ`Boolean`式。 正確に 1 つの式が評価された場合`True`、検出されると`Xor`返します`True`します。 両方の式が評価される場合`True`に評価される両方または`False`、`Xor`返します`False`します。  
  
 次の例を示しています、 `And`、 `Or`、および`Xor`演算子。  
  
 [!code-vb[VbVbalrOperators#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#78)]  
  
## <a name="short-circuiting-logical-operations"></a>ショート サーキット論理操作  
 [AndAlso 演算子](../../../../visual-basic/language-reference/operators/andalso-operator.md)とよく似ていますが、`And`演算子、2 つの論理積を実行するに`Boolean`式。 2 つの主な違いは`AndAlso`展示*ショート サーキット*動作します。 場合、最初の式で、`AndAlso`式に評価されます`False`、最終結果を変更できないために、2 番目の式は評価されませんしと`AndAlso`を返します`False`。  
  
 同様に、 [OrElse 演算子](../../../../visual-basic/language-reference/operators/orelse-operator.md)ショート サーキットの 2 つの論理和演算を実行します。`Boolean`式。 場合、最初の式で、`OrElse`式に評価されます`True`、最終結果を変更できないために、2 番目の式は評価されませんしと`OrElse`を返します`True`。  
  
### <a name="short-circuiting-trade-offs"></a>ショート サーキットのトレードオフ  
 ショート サーキット論理演算の結果を変更することはできませんを式が評価されないので、パフォーマンスが向上できます。 ただし、その式では、追加のアクションを実行する場合は、これらのアクションをスキップ ショート サーキットします。 たとえば、次の式にはへの呼び出しが含まれています、`Function`プロシージャ、式が、ショート サーキットであり、追加のコードに含まれる場合に、プロシージャが呼び出されないこと、`Function`は実行されません。 そのため、関数は、ごくまれにしか、実行を正しくテストいない可能性があります。 または、プログラム ロジックのコードに依存、`Function`します。  
  
 次の例は、違いを示しています。 `And`、 `Or`、および対応するショート サーキットします。  
  
 [!code-vb[VbVbalrOperators#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#81)]  
  
 [!code-vb[VbVbalrOperators#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#80)]  
  
 [!code-vb[VbVbalrOperators#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#79)]  
  
 前の例で重要なコード内`checkIfValid()`呼び出しがショート サーキット場合に実行されません。 最初の`If`ステートメント呼び出し`checkIfValid()`にもかかわらず`12 > 45`返します`False`ため、`And`ショート サーキットはありません。 2 番目`If`ステートメントは呼び出しません`checkIfValid()`ため、ときに`12 > 45`を返します`False`、`AndAlso`実行せずに 2 番目の式。 3 番目`If`ステートメント呼び出し`checkIfValid()`場合でも`12 < 45`返します`True`ため、`Or`ショート サーキットはありません。 4 番目`If`ステートメント呼び出されません`checkIfValid()`ため、ときに`12 < 45`返します`True`、 `OrElse` 2 番目の式を実行せずにします。  
  
## <a name="bitwise-operations"></a>ビットごとの演算  
 ビットごとの演算では、(基本 2) をバイナリ形式で 2 つの整数値を評価します。 対応する位置のビットを比較され、比較に基づいて値を割り当てます。 次の例を示しています、`And`演算子。  
  
 [!code-vb[VbVbalrConcepts#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConcepts/VB/Class1.vb#2)]  
  
 前の例の値を設定する`x`を 1 にします。 これは、次の理由で発生します。  
  
-   値はバイナリとして扱われます。  
  
     バイナリ形式の 3 011 を =  
  
     バイナリ形式で 5 101 を =  
  
-   `And`演算子は、バイナリ表現を一度に 1 つのバイナリ位置 (ビット) を比較します。 指定した位置にある両方のビットが 1 の場合は、1 が結果にその位置に配置されます。 いずれかのビットが 0 の場合、0 は、結果にその位置に配置されます。 前の例が正常に機能としては、次のように。  
  
     011 (バイナリ形式では 3)  
  
     101 (バイナリ形式では 5)  
  
     001 (バイナリ形式の結果)  
  
-   結果は、10 進数として扱われます。 001 値は、1 のバイナリ表現があるため`x`= 1。  
  
 ビット演算`Or`操作は同様、ですが、ビットごとの一方または両方が 1 の場合、結果のビットを 1 が割り当てられます。 `Xor` (両方ではなく) ビットごとの 1 つだけが 1 の場合は、結果のビットに 1 を割り当てます。 `Not` 1 つのオペランドを受け取ると、符号ビットを含むすべてのビットを反転し、結果にその値を割り当てます。 つまり、正の数値を署名の`Not`常に負の値を返しますと負の数値の`Not`常に正の値または 0 の値を返します。  
  
 `AndAlso`と`OrElse`演算子はビットごとの演算をサポートしていません。  
  
> [!NOTE]
>  ビットごとの演算は、整数型のみで実行できます。 ビットごとの操作を続行する前に、浮動小数点値を整数型に変換する必要があります。  
  
## <a name="see-also"></a>関連項目

- [論理/ビット演算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [ブール式](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [Visual Basic における算術演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Visual Basic における比較演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Visual Basic の連結演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
- [演算子の効率のよい組み合わせ](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
