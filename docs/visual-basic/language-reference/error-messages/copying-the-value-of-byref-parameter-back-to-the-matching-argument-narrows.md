---
title: "'ByRef' パラメーター '<parametername>' の値を一致する引数へ戻してコピーすると、型 '<typename1>' から型 '<typename2>' に下位変換します"
ms.date: 07/20/2015
f1_keywords:
- bc32053
- vbc32053
helpviewer_keywords:
- BC32053
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
ms.openlocfilehash: fa8607bf72dfb344048ec82514182dcb6810274d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58817163"
---
# <a name="copying-the-value-of-byref-parameter-parametername-back-to-the-matching-argument-narrows-from-type-typename1-to-type-typename2"></a>'ByRef' パラメーターの値をコピー '\<parametername >' 型から縮小変換、一致する引数に戻して'\<typename1 >' 型に '\<typename2 >'
プロシージャは、対応するパラメーターの型を拡張する引数を指定して呼び出され、パラメーターから、引数への変換は縮小します。  
  
 クラスまたは構造体を定義するときは、そのクラスまたは構造体の型を他の型に変換する 1 つまたは複数の変換演算子を定義できます。 その他の型をクラスまたは構造体の型に変換する逆の変換演算子を定義することもできます。 プロシージャ呼び出しでクラスまたは構造体の型を使用すると、Visual Basic は、対応するパラメーターの型の引数の型に変換するのにこれらの変換演算子を使用できます。  
  
 引数を渡す場合[ByRef](../../../visual-basic/language-reference/modifiers/byref.md)、Visual Basic は、ローカル変数の参照を渡す代わりにプロシージャに引数の値をコピーすることがあります。 このような場合は、プロシージャが返されるときに Visual Basic する必要がありますにコピーしてローカル変数の値戻す呼び出し元のコードの引数。  
  
 `ByRef` 引数の値がプロシージャにコピーされ、引数とパラメーターが同じ型である場合、変換は必要ありません。 種類が異なる場合は、Visual Basic が双方向で変換する必要があります。 型のいずれかがクラスまたは構造体の型の場合は、Visual Basic は両方と、他の型の間を変換する必要があります。 これらの変換のいずれかを拡大すると場合、逆の変換は縮小可能性があります。  
  
 **エラー ID:** BC32053  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   可能であれば、Visual Basic は、変換を行う必要はありませんので、プロシージャのパラメーターとして、同じ種類の呼び出し元の引数を使用します。  
  
-   パラメーター型とは異なる引数型を使用してプロシージャを呼び出す必要があり、呼び出し元の引数に値を返す必要がない場合は、 [ByRef](../../../visual-basic/language-reference/modifiers/byval.md) ではなく `ByRef`になるようにパラメーターを定義します。  
  
-   呼び出し元の引数に値を返す場合は、定義として逆の変換演算子[Widening](../../../visual-basic/language-reference/modifiers/widening.md)、可能な場合。  
  
## <a name="see-also"></a>関連項目

- [プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [プロシージャのパラメーターと引数](../../../visual-basic/programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [引数の値渡しと参照渡し](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [演算子プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [Operator ステートメント](../../../visual-basic/language-reference/statements/operator-statement.md)
- [方法: 演算子を定義します。](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [方法: 変換演算子を定義します。](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [Visual Basic における型変換](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [拡大変換と縮小変換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
