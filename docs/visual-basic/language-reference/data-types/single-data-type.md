---
title: 単精度浮動小数点型 (Single) (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Single
helpviewer_keywords:
- Single data type
- F literal type character [Visual Basic]
- trailing zeros
- real numbers
- literal type characters [Visual Basic], F
- trailing 0 characters [Visual Basic]
- identifier type characters [Visual Basic], !
- single-precision numbers
- '! identifier type character'
- 0 characters [Visual Basic], trailing
- data types [Visual Basic], assigning
- floating-point numbers [Visual Basic], Single data type
- numbers [Visual Basic], real
- zeros, trailing
- numbers [Visual Basic], floating point
ms.assetid: 224a2795-4cd5-496c-8f7a-a4f05a06d45d
ms.openlocfilehash: b90fdb562f9d65858ac477321a18067cc6e621a2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58833326"
---
# <a name="single-data-type-visual-basic"></a>単精度浮動小数点型 (Single) (Visual Basic)
IEEE 32 ビット (4 バイト) の単精度浮動小数点数が 3.4028235 e + 38 までの値の範囲の符号付き - 1.401298E を通じて-負の値と 1.401298E から 45-45 から 3.4028235 e + 38 までの正の値。 単精度の数値では、実数の概算値を格納します。  
  
## <a name="remarks"></a>Remarks  
 使用して、`Single`データ型の完全なデータの幅を必要としない浮動小数点値を含む`Double`します。 場合によっては、共通言語ランタイムでをパックできる場合があります、`Single`変数、緊密に協力し、メモリ消費量を保存します。  
  
 `Single` の既定値は 0 です。  
  
## <a name="programming-tips"></a>プログラミングのヒント  
  
-   **有効桁数です。** 浮動小数点数を使用する場合が常にないことを正確に表現メモリ内に留意してください。 値の比較などの特定の操作から予期しない結果に可能性と`Mod`演算子。 詳細については、次を参照してください。[データ型のトラブルシューティング](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)します。  
  
-   **拡大します。** `Single`拡大変換後のデータ型`Double`します。 つまり、変換できる`Single`に`Double`遭遇することがなく、<xref:System.OverflowException?displayProperty=nameWithType>エラー。  
  
-   **後続のゼロ。** 浮動小数点データ型には、末尾の 0 文字の任意の内部表現はありません。 たとえば、これらは区別されません 4.2000 および 4.2 します。 その結果、末尾の 0 文字では、表示または浮動小数点値を印刷するときに表示されません。  
  
-   **型宣言文字。** あるリテラルにリテラルの型文字 `F` を付けると、そのリテラルは `Single` に変換されます。 ある識別子に識別子の型文字 `!` を付けると、その識別子は整数型 (`Single`) に変換されます。  
  
-   **フレームワークの型。** .NET Framework において対応する型は、<xref:System.Single?displayProperty=nameWithType> 構造体です。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Single?displayProperty=nameWithType>
- [データの種類](../../../visual-basic/language-reference/data-types/index.md)
- [Decimal データ型](../../../visual-basic/language-reference/data-types/decimal-data-type.md)
- [Double 型](../../../visual-basic/language-reference/data-types/double-data-type.md)
- [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [データ型の有効な使用方法](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [トラブルシューティング (データ型)](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
