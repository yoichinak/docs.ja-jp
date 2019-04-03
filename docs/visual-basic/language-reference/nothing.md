---
title: Nothing (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Nothing
- vb.Nothing
helpviewer_keywords:
- Nothing keyword [Visual Basic]
- Nothing keyword [Visual Basic], syntax
ms.assetid: 06176e2d-bbf7-4a37-afaa-a86ad21ee99f
ms.openlocfilehash: 97c651dbcc657fbab0706c9a959bd0031c0fe343
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826094"
---
# <a name="nothing-visual-basic"></a>Nothing (Visual Basic)
任意のデータ型の既定値を表します。 参照型の場合、既定値は、`null`参照。 値の型の場合、既定値は、値の型が null 許容かどうかに依存します。  
  
> [!NOTE]
>  Null 非許容値型の場合は、 `Nothing` Visual Basic では異なります`null`でC#します。 Null 非許容値型の変数を設定した場合、Visual Basic で`Nothing`変数が宣言された型の既定値に設定されています。 C#を null 非許容値型の変数を割り当てる場合は、 `null`、コンパイル時エラーが発生します。  
  
## <a name="remarks"></a>Remarks  
 `Nothing` データ型の既定値を表します。 既定値は、変数が、値の型または参照型によって異なります。  
  
 変数を*値の型*直接その値が含まれています。 値の型は、すべての数値データ型を含める`Boolean`、 `Char`、 `Date`、すべての構造、およびすべての列挙体。 変数を*参照型*メモリ内オブジェクトのインスタンスへの参照を格納します。 参照型には、クラス、配列、デリゲート、および文字列が含まれます。 詳細については、「 [Value Types and Reference Types](../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)」を参照してください。  
  
 変数は、値の場合は入力の動作`Nothing`かどうか、変数が null 許容のデータ型によって異なります。 Null 許容値型を表す、追加、`?`修飾子を型名。 割り当てる`Nothing`null 許容型の変数に値を設定`null`します。 詳細と例については、[null 許容値型](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)を参照してください。  
  
 変数が null 許容型でない値型の場合は、割り当てる`Nothing`に設定が既定値にその宣言された型。 その型に変数のメンバーが含まれている場合はすべて既定値に設定します。 次の例は、スカラー型の場合、これを示しています。  
  
 [!code-vb[VbVbalrKeywords#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class2.vb#7)]  
  
 変数が参照型の場合は、割り当てる`Nothing`変数設定、`null`変数の型の参照。 設定されている変数、`null`参照は任意のオブジェクトに関連付けられていません。 次に例を示します。  
  
 [!code-vb[VbVbalrKeywords#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class3.vb#8)]  
  
 変数は参照 (または null 許容値の型) かどうかをチェックするときに`null`、使用しない`= Nothing`または`<> Nothing`します。 常に使用する`Is Nothing`または`IsNot Nothing`します。  
  
 Visual Basic で文字列の場合、空の文字列に等しい`Nothing`します。 そのため、`"" = Nothing`は true。  
  
 次の例を使用する比較を示しています、`Is`と`IsNot`演算子。  
  
 [!code-vb[VbVbalrKeywords#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class4.vb#9)]  
  
 使用せずに変数を宣言する場合、`As`句に設定し、 `Nothing`、変数の型を持つ`Object`します。 この例は`Dim something = Nothing`します。 ここでは、コンパイル時エラーにとき`Option Strict`上と`Option Infer`はオフです。  
  
 割り当てるとき`Nothing`オブジェクト変数を参照しなく任意のオブジェクト インスタンス。 場合は、変数インスタンスを参照していた、設定`Nothing`インスタンス自体を終了しません。 インスタンスが終了し、ガベージ コレクター (GC) が残り、アクティブな参照がないことを検出した後にのみ関連付けられているメモリとシステム リソースを解放します。  
  
 `Nothing` 異なります、<xref:System.DBNull>初期化されていないバリアントをまたはデータベースが存在しない列を表すオブジェクト。  
  
## <a name="see-also"></a>関連項目

- [Dim ステートメント](../../visual-basic/language-reference/statements/dim-statement.md)
- [オブジェクトの有効期間:オブジェクトを作成および破棄する方法](../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)
- [Visual Basic での有効期間](../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Is 演算子](../../visual-basic/language-reference/operators/is-operator.md)
- [IsNot 演算子](../../visual-basic/language-reference/operators/isnot-operator.md)
- [null 許容値型](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
