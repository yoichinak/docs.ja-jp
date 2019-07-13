---
title: Narrowing (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.narrowing
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Narrowing keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: a207ee91-aca4-4771-b4e2-713f029bf2bb
ms.openlocfilehash: eb5f021371291483b8eb2a13727a9fda94540638
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61920641"
---
# <a name="narrowing-visual-basic"></a>Narrowing (Visual Basic)
示します変換演算子 (`CType`) クラスまたは構造体を元のクラスまたは構造体の有効値の一部を保持することができない可能性がある型に変換します。  
  
## <a name="converting-with-the-narrowing-keyword"></a>縮小のキーワードを使用して変換します。  
 変換の手順を指定する必要があります`Public Shared`に加えて`Narrowing`します。  
  
 縮小変換は常にではありません、実行時に成功し失敗したり、データ損失が発生できます。 例としては、`Long`に`Integer`、`String`に`Date`、および派生型に基本型。 基本データ型が派生型のすべてのメンバーが含まれていない可能性があります、ため、派生型のインスタンスではないために、この最後の変換が縮小します。  
  
 場合`Option Strict`は`On`、コードを使用する必要があります`CType`のすべての縮小変換します。  
  
 `Narrowing`キーワードは、このコンテキストで使用できます。  
  
 [Operator ステートメント](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
## <a name="see-also"></a>関連項目

- [Operator ステートメント](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Widening](../../../visual-basic/language-reference/modifiers/widening.md)
- [拡大変換と縮小変換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [方法: 演算子を定義します。](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [CType 関数](../../../visual-basic/language-reference/functions/ctype-function.md)
- [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)
