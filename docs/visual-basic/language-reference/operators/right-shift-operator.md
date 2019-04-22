---
title: '>> 演算子 (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.>>
helpviewer_keywords:
- operator>>
- '>> operator [Visual Basic]'
- bit shift operators [Visual Basic]
- operator >>
- right shift operators [Visual Basic]
ms.assetid: 054dc6a6-47d9-47ef-82da-cfa2b59fbf8f
ms.openlocfilehash: 8803dc2e25edde756958a243d429dd30c5c78bcf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58816968"
---
# <a name="-operator-visual-basic"></a>>> 演算子 (Visual Basic)
ビット パターン上で算術右シフトを実行します。  
  
## <a name="syntax"></a>構文  
  
```  
result = pattern >> amount  
```  
  
## <a name="parts"></a>指定項目  
 `result`  
 必須。 整数値。 ビット パターンのシフトの結果。 データ型がの場合と同じ`pattern`します。  
  
 `pattern`  
 必須。 整数の数値式です。 シフトするビット パターンです。 データ型は整数型である必要があります (`SByte`、 `Byte`、 `Short`、 `UShort`、 `Integer`、 `UInteger`、 `Long`、または`ULong`)。  
  
 `amount`  
 必須。 数値式。 ビット パターンをシフトするビット数。 データ型である必要があります`Integer`に拡大変換または`Integer`します。  
  
## <a name="remarks"></a>Remarks  
 算術シフトは循環、つまり、もう一方の端に結果の 1 つの端のシフトは行われません。 算術右シフトの右端のビット位置より後ろのシフトが破棄されと左端 (署名) のビットが左側にある空いたビット位置に反映されます。 つまり、`pattern`負の値を持つ、空いた位置は、いずれかに設定されます。 0 に設定されているそれ以外の場合。  
  
 なお、データ型`Byte`、 `UShort`、 `UInteger`、および`ULong`に反映されるまでの符号ビットがないために、符号がないです。 場合`pattern`の符号なしのいずれかの型、空いた位置は常に 0 に設定します。  
  
 結果が保持できるより多くのビット シフトを防ぐためには、Visual Basic がの値をマスク`amount`のデータ型に対応するサイズのマスクを含む`pattern`します。 これらの値のバイナリとは、シフト数に使用されます。 マスク サイズは次のとおりです。  
  
|データ型 `pattern`|サイズのマスク (10 進数)|サイズのマスク (16 進数)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|&AMP; H00000007|  
|`Short`, `UShort`|16|&AMP; H0000000F|  
|`Integer`, `UInteger`|31|&AMP; H0000001F|  
|`Long`, `ULong`|63|&AMP; H0000003F|  
  
 場合`amount`の値は 0 が`result`の値と同一では、`pattern`します。 場合`amount`が負の場合、符号なしの値として取得され、適切なサイズのマスクでマスクします。  
  
 算術シフトでは、オーバーフロー例外が生成されません。  
  
## <a name="overloading"></a>オーバーロード  
 `>>`演算子は、*オーバー ロードされた*、つまり、ことクラスまたは構造体を再定義できますその動作はそのクラスまたは構造体の型。 コードは、このようなクラスまたは構造体に、この演算子を使用する場合は、再定義された動作を確認ください。 詳細については、「 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例では、`>>`整数値に対して算術右シフトを実行する演算子。 結果は常に同じデータとしてシフトされる式の型を持ちます。  
  
 [!code-vb[VbVbalrOperators#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#14)]  
  
 前の例の結果は次のとおりです。  
  
-   `result1` 2560 (0000 1010 0000 0000) です。  
  
-   `result2` 160 (0000 0000 1010 0000) です。  
  
-   `result3` 2 (0000 0000 0000 0010) です。  
  
-   `result4` 640 (0000 0010 1000 0000) です。  
  
-   `result5` 0 (右側のシフト 15 の桁数) です。  
  
 シフト数`result4`18 として計算されますが 2 と等しいと 15 です。  
  
 次の例では、負の値に算術シフトを示します。  
  
 [!code-vb[VbVbalrOperators#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#55)]  
  
 前の例の結果は次のとおりです。  
  
-   `negresult1` (1111 1110 0000 0000) -512 です。  
  
-   `negresult2` -1 (符号ビットが反映されます) です。  
  
## <a name="see-also"></a>関連項目

- [ビット シフト演算子](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [代入演算子](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [>>= 演算子](../../../visual-basic/language-reference/operators/right-shift-assignment-operator.md)
- [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic における算術演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
