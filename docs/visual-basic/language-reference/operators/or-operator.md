---
title: Or 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Or
helpviewer_keywords:
- Or operator [Visual Basic]
- operators [Visual Basic], bitwise
- inclusive Or operator [Visual Basic]
- bitwise operators [Visual Basic], OR operator
- Or keyword [Visual Basic]
- operators [Visual Basic], inclusive or
- operators [Visual Basic], disjunction
- bitwise comparison [Visual Basic]
- logical disjunction
- disjunction operator [Visual Basic]
ms.assetid: 41ed6905-bf3d-468a-9e3b-03c10d461891
ms.openlocfilehash: 1d11a6d009f6ecfea9fb1a86b00c67b87d5555dc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955841"
---
# <a name="or-operator-visual-basic"></a>Or 演算子 (Visual Basic)
2 `Boolean`つの式の場合は論理和、2つの数値式の場合はビットごとの和を実行します。  
  
## <a name="syntax"></a>構文  
  
```  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a>指定項目  
 `result`  
 必須。 `Boolean` Or 数値式。 比較`Boolean`のため`result`に、は2つ`Boolean`の値の包括論理和です。 ビットごとの演算`result`の場合、は、2つの数値ビットパターンの包括的なビットごとの和を表す数値です。  
  
 `expression1`  
 必須。 `Boolean` Or 数値式。  
  
 `expression2`  
 必須。 `Boolean` Or 数値式。  
  
## <a name="remarks"></a>Remarks  
 比較`Boolean`の場合`result` 、 `False`はとの`expression1`両方`False`がに評価される場合にのみになります。 `expression2` 次の表は、 `result`がどのように決定されるかを示しています。  
  
|が`expression1`の場合|と`expression2`は|の`result`値はです。|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> 比較では、演算子`Or`は常に両方の式を評価します。これにはプロシージャ呼び出しを含めることができます。 `Boolean` [OrElse 演算子](../../../visual-basic/language-reference/operators/orelse-operator.md)は*ショートサーキット*を実行します。つまり、 `expression1`が`True`の場合`expression2` 、は評価されません。  
  
 ビットごとの演算の`Or`場合、演算子は2つの数値式で同一の位置指定ビットのビットごと`result`の比較を実行し、次の表に従って、に対応するビットを設定します。  
  
|の`expression1`ビットがの場合|との`expression2`ビットは|の`result`ビットはです。|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
> 論理演算子とビット処理演算子は、他の算術演算子および関係演算子より優先順位が低いので、ビットごとの演算は、正確な実行を保証するためにかっこで囲む必要があります。  
  
## <a name="data-types"></a>データの種類  
 `Boolean`オペランドが1つの式と1つの数値式で構成され`Boolean`ている場合、Visual Basic は式を数値`True`に変換し`False`(の場合は–1、の場合は 0)、ビットごとの演算を実行します。  
  
 比較の場合、結果のデータ型は`Boolean`になります。 `Boolean` ビットごとの比較の場合、結果のデータ型は、および`expression1` `expression2`のデータ型に適した数値型になります。 「[演算子の結果のデータ型](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)」の「リレーショナルおよびビットごとの比較」の表を参照してください。  
  
## <a name="overloading"></a>オーバーロード  
 演算子はオーバーロードできます。つまり、クラスまたは構造体がそのクラスまたは構造体の型を持つ場合に、クラスまたは構造体がその動作を再定義できます。 `Or` コードでこのようなクラスまたは構造体に対してこの演算子を使用する場合は、再定義された動作を理解していることを確認してください。 詳細については、「 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例では`Or` 、演算子を使用して、2つの式の包括論理和を実行します。 結果は、2 `Boolean`つの式のいずれかがで`True`あるかどうかを表す値です。  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 前の例では、 `True` `True`それぞれ、、 `False`およびの結果が生成されます。  
  
## <a name="example"></a>例  
 次の例では`Or` 、演算子を使用して、2つの数値式の個々のビットに対して包括的論理和を実行します。 オペランドの対応するビットのいずれかが1に設定されている場合、結果パターンのビットは設定されます。  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 前の例では、それぞれ10、14、14の結果が生成されます。  
  
## <a name="see-also"></a>関連項目

- [論理/ビット演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [OrElse 演算子](../../../visual-basic/language-reference/operators/orelse-operator.md)
- [Visual Basic の論理演算子とビット処理演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
