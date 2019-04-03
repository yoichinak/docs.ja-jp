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
ms.openlocfilehash: 0277b6f24e62ed5f0cad3dae225c86fffc4c09b9
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58835298"
---
# <a name="or-operator-visual-basic"></a>Or 演算子 (Visual Basic)
2 つの論理和演算を実行します。`Boolean`式、または 2 つの数値式のビットごとの論理和。  
  
## <a name="syntax"></a>構文  
  
```  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a>指定項目  
 `result`  
 必須。 すべて`Boolean`または数値式です。 `Boolean`比較、`result`は 2 つの包括的論理和`Boolean`値。 ビットごとの演算`result`は 2 つの数値ビット パターンの包括的論理和を表す数値です。  
  
 `expression1`  
 必須。 すべて`Boolean`または数値式です。  
  
 `expression2`  
 必須。 すべて`Boolean`または数値式です。  
  
## <a name="remarks"></a>Remarks  
 `Boolean`比較、`result`は`False`場合にのみ、両方`expression1`と`expression2`に評価される`False`します。 次の表はどのように`result`決定されます。  
  
|場合`expression1`は|`expression2`は|値`result`は|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  `Boolean` 、比較、`Or`演算子では、両方の式では、プロシージャの呼び出しを含めることが常に評価されます。 [OrElse 演算子](../../../visual-basic/language-reference/operators/orelse-operator.md)実行*ショート サーキット*、つまり、その場合`expression1`は`True`、し`expression2`は評価されません。  
  
 ビットごとの演算、`Or`演算子が 2 つの数値式で同じ位置にビットのビット単位の比較を実行し、対応するでビットを設定`result`次の表に従ってします。  
  
|場合にビット`expression1`は|ビットと`expression2`は|内のビット`result`は|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
>  論理/ビット処理演算子の他の算術演算子や関係演算子よりも優先順位の低いため、ビットごとの演算は、正確に実行されるようにかっこで囲む必要があります。  
  
## <a name="data-types"></a>データの種類  
 いずれかのオペランドで構成される場合`Boolean`式と 1 つの数値式では、Visual Basic に変換します、`Boolean`式を数値に (– 1 `True` 0 `False`) し、ビットごとの演算を実行します。  
  
 `Boolean`比較、結果のデータ型は`Boolean`します。 ビット単位の比較結果のデータ型は数値型のデータ型に適した`expression1`と`expression2`します。 「リレーショナルとビットごとの比較」表を参照して[演算子結果のデータ型](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)します。  
  
## <a name="overloading"></a>オーバーロード  
 `Or`演算子は、*オーバー ロードされた*、つまり、ことクラスまたは構造体を再定義できますその動作はそのクラスまたは構造体の型。 コードは、このようなクラスまたは構造体に、この演算子を使用する場合は、再定義された動作を確認ください。 詳細については、「 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例では、`Or`オペレーターが 2 つの式の包括的論理和演算を実行します。 結果は、`Boolean`を表す値が 2 つの式のいずれかどうか`True`します。  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 前の例の結果を生成する`True`、 `True`、および`False`、それぞれします。  
  
## <a name="example"></a>例  
 次の例では、`Or`オペレーターが 2 つの数値式のビットごとの包括的論理和を実行します。 オペランドの対応するビットのいずれかを 1 に設定されている場合、結果のパターンのビットが設定されます。  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 前の例では、それぞれ 10、14、および 14 の結果を生成します。  
  
## <a name="see-also"></a>関連項目

- [論理/ビット演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [OrElse 演算子](../../../visual-basic/language-reference/operators/orelse-operator.md)
- [Visual Basic での論理とビット処理演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
