---
title: Not 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Not
helpviewer_keywords:
- Boolean expressions, negating
- operators [Visual Basic], bitwise
- negation operator [Visual Basic]
- inverse bit values in variables [Visual Basic]
- bitwise operators [Visual Basic], NOT operator
- bitwise comparison [Visual Basic]
- Not operator [Visual Basic]
- logical negation
- operators [Visual Basic], negation
ms.assetid: 8f2ea83c-d2ed-480a-a474-3042a1cad9b5
ms.openlocfilehash: 4e54fdca9123ad5595eb9a8c5e2ac5bc303a8f6a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824214"
---
# <a name="not-operator-visual-basic"></a>Not 演算子 (Visual Basic)
論理否定を実行、`Boolean`式、または数値式に対してビットごとの否定。  
  
## <a name="syntax"></a>構文  
  
```  
result = Not expression  
```  
  
## <a name="parts"></a>指定項目  
 `result`  
 必須。 すべて`Boolean`または数値式です。  
  
 `expression`  
 必須。 すべて`Boolean`または数値式です。  
  
## <a name="remarks"></a>Remarks  
 `Boolean`式では、次の表はどのように`result`決定されます。  
  
|場合`expression`は|値`result`は|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 数値式の場合、`Not`演算子の任意の数値式のビット値を反転させるし、対応するではビットを設定`result`次の表に従ってします。  
  
|場合にビット`expression`は|内のビット`result`は|  
|-------------------------------|----------------------------|  
|1|0|  
|0|1|  
  
> [!NOTE]
>  論理/ビット処理演算子の他の算術演算子や関係演算子よりも優先順位の低いため、ビットごとの演算は、正確に実行されるようにかっこで囲む必要があります。  
  
## <a name="data-types"></a>データの種類  
 論理否定の場合は、結果のデータ型は`Boolean`します。 ビットごとの否定の結果のデータ型と同じ`expression`します。 ただし、式が場合`Decimal`、結果は`Long`します。  
  
## <a name="overloading"></a>オーバーロード  
 `Not`演算子は、*オーバー ロードされた*、いるクラスまたは構造体を再定義できますの動作のオペランドがそのクラスまたは構造体の型を持つときにすることを意味します。 コードは、このようなクラスまたは構造体に、この演算子を使用する場合は、再定義された動作を確認ください。 詳細については、「 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例では、`Not`に対して論理否定を実行する演算子、`Boolean`式。 結果は、`Boolean`式の値の逆の順序を表す値です。  
  
 [!code-vb[VbVbalrOperators#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#33)]  
  
 前の例の結果を生成する`False`と`True`、それぞれします。  
  
## <a name="example"></a>例  
 次の例では、`Not`数値式のビットごとの論理否定を実行する演算子。 結果パターンのビットは符号ビットを含めて、オペランドのパターンに対応するビットの逆に設定されます。  
  
 [!code-vb[VbVbalrOperators#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#34)]  
  
 前の例では、– 11、– 9、および – 7 の結果をそれぞれ生成されます。  
  
## <a name="see-also"></a>関連項目

- [論理/ビット演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic での論理とビット処理演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
