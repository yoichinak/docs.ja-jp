---
title: Widening (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.widening
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Widening keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 646ae263-94d3-40a2-b0cc-64f619292f56
ms.openlocfilehash: d7d43d4f5f931881d5c8b663c719fe7f92559799
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825314"
---
# <a name="widening-visual-basic"></a>Widening (Visual Basic)
示します変換演算子 (`CType`) クラスまたは構造体を元のクラスまたは構造体のすべての値を保持できる型に変換します。  
  
## <a name="converting-with-the-widening-keyword"></a>拡大のキーワードを使用して変換します。  
 変換の手順を指定する必要があります`Public Shared`に加えて`Widening`します。  
  
 拡大変換では、実行時に常に成功して、データの損失が発生することはありません。 例としては、`Single`に`Double`、`Char`に`String`、およびその基本型に派生型。 派生型が基本型のすべてのメンバーを含まれており、基本データ型のインスタンスであるため、この最後の変換が拡大します。  
  
 使用側コードが使用する必要はありません`CType`拡大変換では、たとえ`Option Strict`は`On`。  
  
 `Widening`キーワードは、このコンテキストで使用できます。  
  
 [Operator ステートメント](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 たとえばの拡大と縮小変換の演算子の定義を参照してください[方法。変換演算子を定義](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)します。  
  
## <a name="see-also"></a>関連項目

- [Operator ステートメント](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [拡大変換と縮小変換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [方法: 演算子を定義します。](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [CType 関数](../../../visual-basic/language-reference/functions/ctype-function.md)
- [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [方法: 変換演算子を定義します。](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
