---
title: / 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb./
helpviewer_keywords:
- division operator [Visual Basic], floating point
- floating-point numbers [Visual Basic], division operator
- slash (/) operator
- zero, division by zero
- operators [Visual Basic], arithmetic
- arithmetic operators [Visual Basic], division
- division [Visual Basic], by zero
- operators [Visual Basic], division
- division operator [Visual Basic], syntax
- / operator [Visual Basic]
- math operators [Visual Basic]
ms.assetid: 335e97f2-c434-439e-9064-76973a051101
ms.openlocfilehash: af2316f92e2904eee1e8c046b34b8147e40cb513
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825067"
---
# <a name="-operator-visual-basic"></a>/ 演算子 (Visual Basic)
2 つの数値を除算し、浮動小数点の結果を返します。  
  
## <a name="syntax"></a>構文  
  
```  
expression1 / expression2  
```  
  
## <a name="parts"></a>指定項目  
 `expression1`  
 必須。 任意の数式。  
  
 `expression2`  
 必須。 任意の数式。  
  
## <a name="supported-types"></a>サポートされている型  
 符号なしと浮動小数点型を含め、すべての数値型と`Decimal`します。  
  
## <a name="result"></a>結果  
 結果は、完全な商の`expression1`で割った値`expression2`剰余を含むです。  
  
 [\ 演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)残りの部分を削除します。 整数の商を返します。  
  
## <a name="remarks"></a>Remarks  
 結果のデータ型は、オペランドの型に依存します。 次の表では、結果のデータ型を決定する方法を示します。  
  
|オペランドのデータ型|結果のデータ型|  
|------------------------|----------------------|  
|両方の式が整数データ型 ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)、[バイト](../../../visual-basic/language-reference/data-types/byte-data-type.md)、[短い](../../../visual-basic/language-reference/data-types/short-data-type.md)、 [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)、[整数](../../../visual-basic/language-reference/data-types/integer-data-type.md)、[UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)、[長い](../../../visual-basic/language-reference/data-types/long-data-type.md)、 [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))|`Double`|  
|1 つの式は、[単一](../../../visual-basic/language-reference/data-types/single-data-type.md)データ型とその他のではありません、 [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Single`|  
|1 つの式は、 [10 進](../../../visual-basic/language-reference/data-types/decimal-data-type.md)データ型とその他のではありません、[単一](../../../visual-basic/language-reference/data-types/single-data-type.md)または[Double](../../../visual-basic/language-reference/data-types/double-data-type.md)|`Decimal`|  
|いずれかの式を[二重](../../../visual-basic/language-reference/data-types/double-data-type.md)データ型|`Double`|  
  
 除算を実行すると、前に、整数の数値式が上位変換する`Double`します。 Visual Basic がから結果を変換しようとした場合、結果は、整数データ型を割り当てる、`Double`その型にします。 結果がその型に適合しない場合は、例外がスローすることができます。 具体的には、このヘルプ ページの「0 による除算」を参照してください。  
  
 場合`expression1`または`expression2`に評価される[Nothing](../../../visual-basic/language-reference/nothing.md)、0 として扱われます。  
  
## <a name="attempted-division-by-zero"></a>0 による除算  
 場合`expression2`を 0 に評価される、`/`演算子はオペランドのデータ型の動作が異なります。 次の表では、可能な動作を示します。  
  
|オペランドのデータ型|動作場合`expression2`は 0 です|  
|------------------------|---------------------------------------|  
|浮動小数点 (`Single`または`Double`)|無限大を返します (<xref:System.Double.PositiveInfinity>または<xref:System.Double.NegativeInfinity>)、または<xref:System.Double.NaN>(非数) 場合`expression1`もゼロです|  
|`Decimal`|スローされます。 <xref:System.DivideByZeroException>|  
|整数 (符号付きまたは符号なし)|スローの整数型への変換を試行<xref:System.OverflowException>整数型を受け入れることはできませんので<xref:System.Double.PositiveInfinity>、 <xref:System.Double.NegativeInfinity>、または <xref:System.Double.NaN>|  
  
> [!NOTE]
>  `/`演算子は、*オーバー ロードされた*、つまり、ことクラスまたは構造体を再定義できますその動作はそのクラスまたは構造体の型。 コードは、このようなクラスまたは構造体に、この演算子を使用する場合は、再定義された動作を確認ください。 詳細については、「 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## <a name="example"></a>例  
 この例では、`/`浮動小数点除算を実行する演算子。 結果は、2 つのオペランドの商。  
  
 [!code-vb[VbVbalrOperators#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#16)]  
  
 前の例の式では、2.5 と 3.333333 の値を返します。 結果が浮動小数点では常にことに注意してください (`Double`) 場合でも、両方のオペランドが整数の定数、します。  
  
## <a name="see-also"></a>関連項目

- [/= 演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [\ 演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)
- [演算子の結果のデータ型](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)
- [算術演算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic における算術演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
