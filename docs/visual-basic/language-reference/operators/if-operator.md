---
title: If 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.IfOperator
- IfOperator
helpviewer_keywords:
- ternary operators [Visual Basic]
- conditional execution
- If expressions [Visual Basic]
- conditional operator [Visual Basic]
- If Operator [Visual Basic]
ms.assetid: dd56c9df-7cd4-442c-9ba6-20c70ee44c8f
ms.openlocfilehash: 9ab01755d75c91ce87acf83e7f406b26c466aef6
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834636"
---
# <a name="if-operator-visual-basic"></a>If 演算子 (Visual Basic)
ショート サーキット評価の条件付きで 2 つの値のいずれかを返すを使用します。 `If`演算子は、3 つの引数と 2 つの引数に呼び出すことができます。  
  
## <a name="syntax"></a>構文  
  
```  
If( [argument1,] argument2, argument3 )  
```  
  
## <a name="if-operator-called-with-three-arguments"></a>演算子は、3 つの引数で呼び出された場合  
 ときに`If`呼びますとしてキャスト可能な値に 3 つの引数を使用すると、最初の引数を評価する必要があります、`Boolean`します。 ある`Boolean`が評価され、返されるその他の 2 つの引数の値が決定されます。 次の一覧に適用される場合にのみ、`If`演算子が 3 つの引数を使用して呼び出されました。  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`argument1`|必須。 `Boolean`. 評価し、返すその他の引数のどちらを決定します。|  
|`argument2`|必須。 `Object`. 評価され、返された場合`argument1`に評価される`True`します。|  
|`argument3`|必須。 `Object`. 評価され、返された場合`argument1`に評価される`False`場合`argument1`は、 [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean`に評価される変数[Nothing](../../../visual-basic/language-reference/nothing.md)します。|  
  
 `If`のように 3 つの引数で呼び出される演算子の動作、`IIf`関数を使用するショート サーキット評価します。 `IIf`関数は、引数の 3 つすべてを常に評価は、`If`を 3 つの引数を持つ演算子が 2 つのみを評価します。 最初の`If`引数が評価され、結果としてキャスト、`Boolean`値、`True`または`False`します。 値が場合`True`、`argument2`が評価され、その値が返されますが、`argument3`は評価されません。 場合の値、`Boolean`式が`False`、`argument3`が評価され、その値が返されますが、`argument2`は評価されません。 次の例の使用方法を示します`If`3 つの引数を使用する場合。  
  
 [!code-vb[VbVbalrOperators#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#100)]  
  
 次の例では、値のショート サーキット評価します。 変数を分割しようと 2 つの例を示します`number`変数によって`divisor`する場合を除く`divisor`は 0 です。 その場合は、0 が返され、実行時エラーになるために、除算を実行する試行は行われません。 `If`ショート サーキット評価の式の使用、2 番目または 3 番目の引数の最初の引数の値に応じてのいずれかが評価されます。 最初の引数が true の場合除数 0 ではないと、2 番目の引数を評価し、除算を実行しても安全です。 最初の引数が false の場合は、3 番目の引数のみが評価され、0 が返されます。 そのため、除数が 0 の場合は行われません、除算およびエラー結果を実行します。 ただし、ため`IIf`は使いませんショート サーキット評価、最初の引数が false の場合も、2 番目の引数が評価されます。 これにより、実行時の 0 除算エラーです。  
  
 [!code-vb[VbVbalrOperators#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#101)]  
  
## <a name="if-operator-called-with-two-arguments"></a>演算子は、2 つの引数で呼び出された場合  
 最初の引数`If`を省略できます。 これにより、オペレーターにのみ 2 つの引数を使用して呼び出すことができます。 次の一覧に適用される場合にのみ、`If`演算子が 2 つの引数と呼ばれます。  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`argument2`|必須。 `Object`. 参照または null 許容型である必要があります。 評価され、以外の値に評価するときに返される`Nothing`します。|  
|`argument3`|必須。 `Object`. 評価され、返された場合`argument2`に評価される`Nothing`します。|  
  
 ときに、`Boolean`引数を省略すると、最初の引数が参照または null 許容型にする必要があります。 最初の引数が評価された場合`Nothing`、2 番目の引数の値が返されます。 その他のすべてのケースでは、最初の引数の値が返されます。 次の例では、この評価のしくみを示しています。  
  
 [!code-vb[VbVbalrOperators#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#102)]  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.Interaction.IIf%2A>
- [null 許容値型](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Nothing](../../../visual-basic/language-reference/nothing.md)
