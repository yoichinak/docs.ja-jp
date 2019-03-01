---
title: Xor 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Xor
helpviewer_keywords:
- exclusive OR operator [Visual Basic]
- logical exclusion
- operators [Visual Basic], exclusive or
- exclusion operator [Visual Basic]
- operators [Visual Basic], bitwise
- bitwise operators [Visual Basic], XOR operator
- Xor operator [Visual Basic]
- Xor keyword [Visual Basic]
- bitwise comparison [Visual Basic]
ms.assetid: 036000a9-3934-4e7f-a9d0-a816de3d84a6
ms.openlocfilehash: bc3df1fdee5405445b4534a6982383c49b369b01
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980439"
---
# <a name="xor-operator-visual-basic"></a>Xor 演算子 (Visual Basic)
2 つの排他的論理和`Boolean`式、または 2 つの数値式の和を求めます。  
  
## <a name="syntax"></a>構文  
  
```  
result = expression1 Xor expression2  
```  
  
## <a name="parts"></a>指定項目  
 `result`  
 必須。 すべて`Boolean`または数値型の変数。 ブール値の比較の`result`は 2 つの論理和 (排他的論理和)`Boolean`値。 ビットごとの演算`result`は、ビットごと (排他的論理和) の 2 つの数値ビット パターンを表す数値です。  
  
 `expression1`  
 必須。 すべて`Boolean`または数値式です。  
  
 `expression2`  
 必須。 すべて`Boolean`または数値式です。  
  
## <a name="remarks"></a>Remarks  
 ブール値の比較の`result`は`True`場合にのみの 1 つだけ`expression1`と`expression2`に評価される`True`します。 つまり、場合にのみ`expression1`と`expression2`評価に反対`Boolean`値。 次の表はどのように`result`決定されます。  
  
|場合`expression1`は|`expression2`は|値`result`は|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  ブール値の比較で、`Xor`演算子では、両方の式では、プロシージャの呼び出しを含めることが常に評価されます。 相当するショート サーキットはありません`Xor`結果は常に両方のオペランドに依存します。 *ショート サーキット*論理演算子を参照してください[AndAlso 演算子](../../../visual-basic/language-reference/operators/andalso-operator.md)と[OrElse 演算子](../../../visual-basic/language-reference/operators/orelse-operator.md)します。  
  
 ビットごとの演算、`Xor`演算子が 2 つの数値式で同じ位置にビットのビット単位の比較を実行し、対応するでビットを設定`result`次の表に従ってします。  
  
|場合にビット`expression1`は|ビットと`expression2`は|内のビット`result`は|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|0|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
>  論理/ビット処理演算子の他の算術演算子や関係演算子よりも優先順位の低いため、ビットごとの演算は、正確に実行されるようにかっこで囲む必要があります。  
  
 たとえば、5 `Xor` 3 は 6 です。 これが理由を確認するために、5、3 を 101 と 011 のバイナリ表現に変換します。 101 Xor 011 では、110 が 6 の 10 進数のバイナリ表現であるを判断するのに前の表を使用します。  
  
## <a name="data-types"></a>データの種類  
 いずれかのオペランドで構成される場合`Boolean`式と 1 つの数値式では、Visual Basic に変換します、`Boolean`式を数値に (– 1 `True` 0 `False`) し、ビットごとの演算を実行します。  
  
 `Boolean`比較、結果のデータ型は`Boolean`します。 ビット単位の比較結果のデータ型は数値型のデータ型に適した`expression1`と`expression2`します。 「リレーショナルとビットごとの比較」表を参照して[演算子結果のデータ型](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)します。  
  
## <a name="overloading"></a>オーバーロード  
 `Xor`演算子は、*オーバー ロードされた*、つまり、ことクラスまたは構造体を再定義できますその動作はそのクラスまたは構造体の型。 コードは、このようなクラスまたは構造体に、この演算子を使用する場合、再定義された動作を理解することを確認します。 詳細については、「 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例では、 `Xor` 2 つの式に対して論理和 (排他的論理和) を実行する演算子。 結果は、`Boolean`が式の 1 つだけかどうかを表す値`True`します。  
  
 [!code-vb[VbVbalrOperators#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#40)]  
  
 前の例の結果を生成する`False`、 `True`、および`False`、それぞれします。  
  
## <a name="example"></a>例  
 次の例では、`Xor`オペレーターが 2 つの数値式のビットごとの排他的論理和 (排他的論理和) を実行します。 オペランドの対応するビットを 1 つを 1 に設定されている場合、結果のパターンのビットが設定されます。  
  
 [!code-vb[VbVbalrOperators#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#41)]  
  
 前の例では、それぞれ 2、12、14 の結果を生成します。  
  
## <a name="see-also"></a>関連項目
- [論理/ビット演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic での論理とビット処理演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
