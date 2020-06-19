---
title: '* 演算子'
ms.date: 07/20/2015
f1_keywords:
- vb.*
helpviewer_keywords:
- arithmetic operators [Visual Basic], multiplication
- operators [Visual Basic], multiplication
- '* operator [Visual Basic]'
- multiplication operator [Visual Basic], syntax
- math operators [Visual Basic]
ms.assetid: 2b210382-99da-4195-89ba-b1d06f5e89ad
ms.openlocfilehash: 4f6a8ea2c5f4e23791afdfe98d2a08bf67219048
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348363"
---
# <a name="-operator-visual-basic"></a>* 演算子 (Visual Basic)
2 つの数値を乗算します。  
  
## <a name="syntax"></a>構文  
  
```vb  
number1 * number2  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`number1`|必須です。 任意の数式。|  
|`number2`|必須です。 任意の数式。|  
  
## <a name="result"></a>結果  
 結果は `number1` と `number2` の積になります。  
  
## <a name="supported-types"></a>サポートされている型  
 すべての数値型。これには、符号なしおよび浮動小数点型と `Decimal` が含まれます。  
  
## <a name="remarks"></a>Remarks  
 結果のデータ型は、オペランドの型によって異なります。 次の表は、結果のデータ型がどのように決定されるかを示しています。  
  
|オペランドのデータ型|結果のデータ型|  
|---|---|  
|両方の式が整数データ型 ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)、[Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md)、[Short](../../../visual-basic/language-reference/data-types/short-data-type.md)、[UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)、[Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)、[UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)、[Long](../../../visual-basic/language-reference/data-types/long-data-type.md)、[ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))|`number1` と `number2` のデータ型に適した数値データ型。 「[演算子の結果のデータ型](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)」の「整数演算」の表を参照してください。|  
|両方の式が [decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|`Decimal`|  
|両方の式が [Single](../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`|  
|一方の式が浮動小数点データ型 (`Single` または [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)) で、両方が `Single` ではない (`Decimal` は浮動小数点データ型ではないので注意してください)|`Double`|  
  
 式が [Nothing](../../../visual-basic/language-reference/nothing.md) に評価される場合、0 として扱われます。  
  
## <a name="overloading"></a>オーバーロード  
 `*` 演算子は "*オーバーロード*" できます。つまり、オペランドがクラスまたは構造体の型を持っているときに、クラスまたは構造体はその動作を再定義できます。 コードで、そのようなクラスまたは構造体に対してこの演算子が使用される場合は、再定義された動作を理解していることを確認してください。 詳細については、「 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## <a name="example"></a>例  
 この例では、`*` 演算子を使用して 2 つの数値を乗算しています。 結果は 2 つのオペランドの積になります。  
  
 [!code-vb[VbVbalrOperators#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#4)]  
  
## <a name="see-also"></a>関連項目

- [*= 演算子](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [算術演算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic における算術演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
