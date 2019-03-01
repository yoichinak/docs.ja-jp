---
title: << 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
ms.openlocfilehash: 329cdf1aea9ca97db000bb5ced8d9e8d6b7a4f58
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970559"
---
# <a name="-operator-visual-basic"></a>\<\< 演算子 (Visual Basic)
ビット パターン上で算術左シフトを実行します。  
  
## <a name="syntax"></a>構文  
  
```  
result = pattern << amount  
```  
  
## <a name="parts"></a>指定項目  
 `result`  
 必須。 整数値。 ビット パターンのシフトの結果。 データ型がの場合と同じ`pattern`します。  
  
 `pattern`  
 必須。 整数の数値式です。 シフトするビット パターンです。 データ型は整数型である必要があります (`SByte`、 `Byte`、 `Short`、 `UShort`、 `Integer`、 `UInteger`、 `Long`、または`ULong`)。  
  
 `amount`  
 必須。 数値式。 ビット パターンをシフトするビット数。 データ型である必要があります`Integer`に拡大変換または`Integer`します。  
  
## <a name="remarks"></a>Remarks  
 算術シフトは循環、つまり、もう一方の端に結果の 1 つの端のシフトは行われません。 算術左シフトでは、結果のデータ型の範囲を超えてシフトが破棄され、右側の空いたビット位置が 0 に設定します。  
  
 結果が保持できるより多くのビットをシフトを防ぐためには、Visual Basic がの値をマスク`amount`のデータ型に対応するサイズのマスクを持つ`pattern`します。 これらの値のバイナリとは、シフト数に使用されます。 マスク サイズは次のとおりです。  
  
|データ型 `pattern`|サイズのマスク (10 進数)|サイズのマスク (16 進数)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|&AMP; H00000007|  
|`Short`, `UShort`|16|&AMP; H0000000F|  
|`Integer`, `UInteger`|31|&AMP; H0000001F|  
|`Long`, `ULong`|63|&AMP; H0000003F|  
  
 場合`amount`の値は 0 が`result`の値と同一では、`pattern`します。 場合`amount`が負の場合、符号なしの値として取得され、適切なサイズのマスクでマスクします。  
  
 算術シフトでは、オーバーフロー例外が生成されません。  
  
> [!NOTE]
>  `<<`演算子は、*オーバー ロードされた*、つまり、ことクラスまたは構造体を再定義できますその動作はそのクラスまたは構造体の型。 場合は、コードでは、この演算子を使用して、このようなクラスまたは構造体で、再定義された動作を理解していることを確認してあります。 詳細については、「 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例では、`<<`演算子を整数値の算術左シフトを実行します。 結果は常に同じデータとしてシフトされる式の型を持ちます。  
  
 [!code-vb[VbVbalrOperators#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#12)]  
  
 前の例の結果は次のとおりです。  
  
-   `result1` 192 (0000 0000 1100 0000) です。  
  
-   `result2` 3072 (0000 1100 0000 0000)。  
  
-   `result3` -32768 (1000 0000 0000 0000) です。  
  
-   `result4` 384 (0000 0001 1000 0000) です。  
  
-   `result5` 0 (シフト 15 桁) です。  
  
 シフト数`result4`17 として計算されますが 1 に等しいと 15 です。  
  
## <a name="see-also"></a>関連項目
- [ビット シフト演算子](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [代入演算子](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<<= 演算子](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)
- [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic における算術演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
