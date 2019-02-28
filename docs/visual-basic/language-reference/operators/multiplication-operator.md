---
title: '* 演算子 (Visual Basic)'
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
ms.openlocfilehash: a13461d7424415ef553dc9ba00de1bf775fda112
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965320"
---
# <a name="-operator-visual-basic"></a>* 演算子 (Visual Basic)
2 つの数値を乗算します。  
  
## <a name="syntax"></a>構文  
  
```  
number1 * number2  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`number1`|必須。 任意の数式。|  
|`number2`|必須。 任意の数式。|  
  
## <a name="result"></a>結果  
 結果は、製品の`number1`と`number2`します。  
  
## <a name="supported-types"></a>サポートされている型  
 符号なしと浮動小数点型を含め、すべての数値型と`Decimal`します。  
  
## <a name="remarks"></a>Remarks  
 結果のデータ型は、オペランドの型に依存します。 次の表では、結果のデータ型を決定する方法を示します。  
  
|オペランドのデータ型|結果のデータ型|  
|---|---|  
|両方の式が整数データ型 ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)、[バイト](../../../visual-basic/language-reference/data-types/byte-data-type.md)、[短い](../../../visual-basic/language-reference/data-types/short-data-type.md)、 [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)、[整数](../../../visual-basic/language-reference/data-types/integer-data-type.md)、[UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)、[長い](../../../visual-basic/language-reference/data-types/long-data-type.md)、 [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))|数値データ型のデータ型に適した`number1`と`number2`します。 「整数の算術演算による」のテーブルを参照してください。[演算子結果のデータ型](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)します。|  
|両方の式が[10 進数](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|`Decimal`|  
|両方の式が[単一](../../../visual-basic/language-reference/data-types/single-data-type.md)|`Single`|  
|いずれかの式は、浮動小数点データ型 (`Single`または[二重](../../../visual-basic/language-reference/data-types/double-data-type.md)) 両方ではなく`Single`(注`Decimal`浮動小数点データ型ではありません)|`Double`|  
  
 式の評価が場合[Nothing](../../../visual-basic/language-reference/nothing.md)、0 として扱われます。  
  
## <a name="overloading"></a>オーバーロード  
 `*`演算子は、*オーバー ロードされた*、つまり、ことクラスまたは構造体を再定義できますその動作はそのクラスまたは構造体の型。 コードは、このようなクラスまたは構造体に、この演算子を使用する場合は、再定義された動作を確認ください。 詳細については、「 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## <a name="example"></a>例  
 この例では、`*`演算子を 2 つの数値を乗算します。 2 つのオペランドの積になります。  
  
 [!code-vb[VbVbalrOperators#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#4)]  
  
## <a name="see-also"></a>関連項目
- [*= 演算子](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [算術演算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic における算術演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
