---
title: Boolean データ型 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.FALSE
- vb.TRUE
- vb.Boolean
helpviewer_keywords:
- Boolean data type
- Boolean values [Visual Basic], False keyword
- False keyword [Visual Basic]
- True keyword [Visual Basic]
- Boolean values [Visual Basic], True keyword
ms.assetid: 4858e630-4813-4216-a55e-f4d0feb884e4
ms.openlocfilehash: 7b64302d801a08f976de0ec969983c821f7a8471
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58841221"
---
# <a name="boolean-data-type-visual-basic"></a>Boolean データ型 (Visual Basic)
値を保持できるのみ`True`または`False`します。 キーワード`True`と`False`の 2 つの状態に対応して`Boolean`変数。  
  
## <a name="remarks"></a>Remarks  
 使用して、[Boolean データ型 (Visual Basic)](../../../visual-basic/language-reference/data-types/boolean-data-type.md) true または false などの 2 つの状態値が含まれてはい/いいえ、またはオン/オフにします。  
  
 `Boolean` の既定値は `False` です。  
  
 `Boolean` 値は、数値として格納しないと、番号に相当する、保存された値が意図されていません。 数値と等価の値に依存するコードを記述する必要がありますしない`True`と`False`します。 使用を制限する必要があります、可能な限り`Boolean`変数を論理値に設計されています。  
  
## <a name="type-conversions"></a>型変換  
 Visual Basic でに数値データ型の値を変換するときに`Boolean`、0 になります`False`他のすべての値になると`True`します。 Visual Basic の変換と`Boolean`値、数値型を`False`が 0 になると`True`-1 になります。  
  
 間で変換する際に`Boolean`値と、数値データ型を保持する .NET Framework の変換メソッドは常に生成しない Visual Basic の変換キーワードと同じ結果に注意してください。 Visual Basic の変換には、以前のバージョンと互換性のある動作が保持されるためです。 詳細についてを参照してください「ブール型は変換する数値型不適切」[データ型のトラブルシューティング](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)します。  
  
## <a name="programming-tips"></a>プログラミングのヒント  
  
-   **負の数。** `Boolean` 数値型ではないと、負の値を表すことはできません。 いずれの場合も、行わないで`Boolean`数値の値を保持します。  
  
-   **型宣言文字。** `Boolean` リテラルの型文字または識別子の型文字がありません。  
  
-   **フレームワークの型。** .NET Framework において対応する型は、<xref:System.Boolean?displayProperty=nameWithType> 構造体です。  
  
## <a name="example"></a>例  
 次の例では、`runningVB`は、`Boolean`変数で、単純なはい/いいえの設定を格納します。  
  
```  
Dim runningVB As Boolean  
' Check to see if program is running on Visual Basic engine.  
If scriptEngine = "VB" Then  
    runningVB = True  
End If  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Boolean?displayProperty=nameWithType>
- [データの種類](../../../visual-basic/language-reference/data-types/index.md)
- [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [データ型の有効な使用方法](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [トラブルシューティング (データ型)](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [CType 関数](../../../visual-basic/language-reference/functions/ctype-function.md)
