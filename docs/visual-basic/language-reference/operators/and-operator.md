---
title: And 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.And
helpviewer_keywords:
- operators [Visual Basic], bitwise
- logical conjunction
- bitwise AND operator [Visual Basic]
- conjunction operator [Visual Basic]
- And operator [Visual Basic]
- bitwise operators [Visual Basic], AND operator
- operators [Visual Basic], conjunction
- bitwise comparison [Visual Basic]
ms.assetid: 2ea711f3-439a-4c7c-9e3a-1ffe3b0d6046
ms.openlocfilehash: 7e25f25677fa684427bdaf00cea73916ffbad655
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818619"
---
# <a name="and-operator-visual-basic"></a>And 演算子 (Visual Basic)
2 つの論理積を求めます`Boolean`式、または 2 つの数値式のビットごとの積。  
  
## <a name="syntax"></a>構文  
  
```  
result = expression1 And expression2  
```  
  
## <a name="parts"></a>指定項目  
 `result`  
 必須。 すべて`Boolean`または数値式です。 ブール値の比較の`result`は 2 つの論理積`Boolean`値。 ビットごとの演算`result`は 2 つの数値ビット パターンのビットごとの積を表す数値です。  
  
 `expression1`  
 必須。 すべて`Boolean`または数値式です。  
  
 `expression2`  
 必須。 すべて`Boolean`または数値式です。  
  
## <a name="remarks"></a>Remarks  
 ブール値の比較の`result`は`True`場合にのみ、両方`expression1`と`expression2`に評価される`True`します。 次の表はどのように`result`決定されます。  
  
|場合`expression1`は|`expression2`は|値`result`は|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  ブール値の比較で、`And`演算子では、両方の式では、プロシージャの呼び出しを含めることが常に評価されます。 [AndAlso 演算子](../../../visual-basic/language-reference/operators/andalso-operator.md)実行*ショート サーキット*、つまり、その場合`expression1`は`False`、し`expression2`は評価されません。  
  
 数値の値に適用すると、`And`演算子が 2 つの数値式で同じ位置にビットのビット単位の比較を実行し、対応するでビットを設定`result`次の表に従ってします。  
  
|場合にビット`expression1`は|ビットと`expression2`は|内のビット`result`は|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|0|  
|0|1|0|  
|0|0|0|  
  
> [!NOTE]
>  論理/ビット処理演算子の他の算術演算子や関係演算子よりも優先順位の低いため、ビットごとの演算は、正確な結果を確認するためにかっこで囲む必要があります。  
  
## <a name="data-types"></a>データの種類  
 いずれかのオペランドで構成される場合`Boolean`式と 1 つの数値式では、Visual Basic に変換します、`Boolean`式を数値に (– 1 `True` 0 `False`) し、ビットごとの演算を実行します。  
  
 ブール値の比較結果のデータ型は`Boolean`します。 ビット単位の比較結果のデータ型は数値型のデータ型に適した`expression1`と`expression2`します。 「リレーショナルとビットごとの比較」表を参照して[演算子結果のデータ型](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)します。  
  
> [!NOTE]
>  `And`演算子は、*オーバー ロードされた*、つまり、ことクラスまたは構造体を再定義できますその動作はそのクラスまたは構造体の型。 コードは、このようなクラスまたは構造体に、この演算子を使用する場合は、再定義された動作を確認ください。 詳細については、「 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例では、`And`演算子を 2 つの式に対して論理積を実行します。 結果は、`Boolean`が両方の式かどうかを表す値`True`します。  
  
 [!code-vb[VbVbalrOperators#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#22)]  
  
 前の例の結果を生成する`True`と`False`、それぞれします。  
  
## <a name="example"></a>例  
 次の例では、`And`オペレーターが 2 つの数値式のビットごとの論理積を実行します。 オペランドの対応するビットが 1 に設定する両方の場合、結果パターンのビットが設定されます。  
  
 [!code-vb[VbVbalrOperators#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#23)]  
  
 前の例では、それぞれ 8、2、および 0 の場合の結果を生成します。  
  
## <a name="see-also"></a>関連項目

- [論理/ビット演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [AndAlso 演算子](../../../visual-basic/language-reference/operators/andalso-operator.md)
- [Visual Basic での論理とビット処理演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
