---
title: 倍精度浮動小数点数型 (Double) (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Double
helpviewer_keywords:
- 'identifier type characters [Visual Basic], #'
- trailing zeros
- real numbers
- trailing 0 characters [Visual Basic]
- 0 characters [Visual Basic], trailing
- literal type characters [Visual Basic], R
- data types [Visual Basic], assigning
- Double data type [Visual Basic]
- '# identifier type character'
- double-precision numbers
- floating-point numbers [Visual Basic], Double data type
- R literal type character [Visual Basic]
- zeros, trailing
- Double data type
ms.assetid: 0c5670f7-fcb1-453a-bef1-374730cd38fd
ms.openlocfilehash: 701d10a334757a96ffd634204c1e1d5eb5418ce6
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824664"
---
# <a name="double-data-type-visual-basic"></a>倍精度浮動小数点数型 (Double) (Visual Basic)
-- をから IEEE の 64 ビット (8 バイト) の倍精度浮動小数点数の符号付き 4.94065645841246544E-負の値と 4.94065645841246544E から 324-324 1.79769313486231570 e + 308 ~正の値。 倍精度数値には、実数の概数が格納されます。  
  
## <a name="remarks"></a>Remarks  
 `Double`データ型最大および最小の大きさを提供しています。  
  
 `Double` の既定値は 0 です。  
  
## <a name="programming-tips"></a>プログラミングのヒント  
  
-   **有効桁数です。** 浮動小数点数を使用するときに、常にないことを正確に表現メモリ内に注意してください。 値の比較などの特定の操作から予期しない結果に可能性と`Mod`演算子。 詳細については、次を参照してください。[データ型のトラブルシューティング](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)します。  
  
-   **後続のゼロ。** 浮動小数点データ型には、末尾のゼロの文字の任意の内部表現はありません。 たとえば、これらは区別されません 4.2000 および 4.2 します。 その結果、末尾のゼロは表示されません表示した場合、または印刷の浮動小数点値。  
  
-   **型宣言文字。** あるリテラルにリテラルの型文字 `R` を付けると、そのリテラルは `Double` に変換されます。 たとえば、整数値が続く場合`R`に値が変更された、`Double`します。  
  
    ```  
    ' Visual Basic expands the 4 in the statement Dim dub As Double = 4R to 4.0:  
    Dim dub As Double = 4.0R  
    ```  
  
     ある識別子に識別子の型文字 `#` を付けると、その識別子は整数型 (`Double`) に変換されます。 次の例では、変数`num`として型指定された、 `Double`:  
  
    ```  
    Dim num# = 3  
    ```  
  
-   **フレームワークの型。** .NET Framework において対応する型は、<xref:System.Double?displayProperty=nameWithType> 構造体です。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Double?displayProperty=nameWithType>
- [データの種類](../../../visual-basic/language-reference/data-types/index.md)
- [Decimal データ型](../../../visual-basic/language-reference/data-types/decimal-data-type.md)
- [Single データ型](../../../visual-basic/language-reference/data-types/single-data-type.md)
- [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [データ型の有効な使用方法](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [トラブルシューティング (データ型)](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [型文字](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
