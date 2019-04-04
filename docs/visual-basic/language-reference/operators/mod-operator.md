---
title: Mod 演算子 (Visual Basic)
ms.date: 04/24/2018
f1_keywords:
- vb.Mod
helpviewer_keywords:
- remainder (Mod operator)
- division operator [Visual Basic], Mod operator
- modulus operator [Visual Basic], Visual Basic
- Mod operator [Visual Basic]
- operators [Visual Basic], division
- arithmetic operators [Visual Basic], Mod
- math operators [Visual Basic]
ms.assetid: 6ff7e40e-cec8-4c77-bff6-8ddd2791c25b
ms.openlocfilehash: b127c50f3319d4fe7c4890fc3bffb295baa37466
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58840173"
---
# <a name="mod-operator-visual-basic"></a>Mod 演算子 (Visual Basic)
2 つの数値を除算し、残りの部分のみを返します。  
  
## <a name="syntax"></a>構文  
  
```  
number1 Mod number2  
```  
  
## <a name="parts"></a>指定項目  
 `number1`  
 必須。 任意の数式。  
  
 `number2`  
 必須。 任意の数式。  
  
## <a name="supported-types"></a>サポートされている型  
 すべての数値型。 これには、符号なしと浮動小数点型が含まれますと`Decimal`します。  
  
## <a name="result"></a>結果

結果は、剰余`number1`で除算`number2`します。 たとえば、式`14 Mod 4`2 に評価されます。  

> [!NOTE]
> 間に相違がある*残りの部分*と*剰余*数学では、負の数値ごとに異なる結果にします。 `Mod` Visual Basic、.NET Framework で演算子`op_Modulus`演算子、および基になる[rem](<xref:System.Reflection.Emit.OpCodes.Rem>) IL 命令が剰余演算を実行します。

結果、`Mod`操作には、被除数の符号が保持されます`number1`、ため、正または負の値があります。 結果は常に、範囲内 (-`number2`、 `number2`)、排他的な。 例:

```vb
Public Module Example
   Public Sub Main()
      Console.WriteLine($" 8 Mod  3 = {8 Mod 3}")
      Console.WriteLine($"-8 Mod  3 = {-8 Mod 3}")
      Console.WriteLine($" 8 Mod -3 = {8 Mod -3}")
      Console.WriteLine($"-8 Mod -3 = {-8 Mod -3}")
   End Sub
End Module
' The example displays the following output:
'       8 Mod  3 = 2
'      -8 Mod  3 = -2
'       8 Mod -3 = 2
'      -8 Mod -3 = -2
```

## <a name="remarks"></a>Remarks  
 いずれか`number1`または`number2`浮動小数点の値は、浮動小数点除算の剰余が返されます。 結果のデータ型のデータ型の除算の結果としてすべての可能な値を保持できる最小のデータ型は、`number1`と`number2`します。  
  
 場合`number1`または`number2`に評価される[Nothing](../../../visual-basic/language-reference/nothing.md)、0 として扱われます。  
  
 関連する演算子を以下に示します。  
  
-   [\ 演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)除算の商の整数を返します。 たとえば、式`14 \ 4`3 に評価されます。  
  
-   [/演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)浮動小数点数として、残りの部分を含む、完全な商を返します。 たとえば、式`14 / 4`3.5 に評価されます。  
  
## <a name="attempted-division-by-zero"></a>0 による除算  
 場合`number2`の動作を 0 に評価される、`Mod`演算子はオペランドのデータ型によって異なります。 整数の除算をスローする<xref:System.DivideByZeroException>例外。 浮動小数点除算が返されます<xref:System.Double.NaN>します。  
  
## <a name="equivalent-formula"></a>同等の数式  
 式`a Mod b`は、次の数式のいずれかに相当します。  
  
 `a - (b * (a \ b))`  
  
 `a - (b * Fix(a / b))`  
  
## <a name="floating-point-imprecision"></a>浮動小数点は誤差  
 浮動小数点数を使用するときに、常がない正確な 10 進表記メモリに注意してください。 これは、値の比較などの特定の操作から予期しない結果につながりますできますと`Mod`演算子。 詳細については、[データ型のトラブルシューティング](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)を参照してください。  
  
## <a name="overloading"></a>オーバーロード  
 `Mod`演算子は、*オーバー ロードされた*、つまり、クラスまたは構造体がその動作を再定義できます。 コードが適用される場合`Mod`クラスまたはそのようなオーバー ロードを含む構造体のインスタンスに再定義された動作を理解することを確認します。 詳細については、「 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例では、`Mod`演算子を 2 つの数値を除算し、残りの部分のみを返します。 どちらかの数値が浮動小数点数の場合は、残りの部分を表す浮動小数点数になります。  
  
 [!code-vb[VbVbalrOperators#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#31)]  
  
## <a name="example"></a>例  
 次の例では、浮動小数点のオペランドの誤差の可能性を示します。 最初のステートメントでは、オペランドは`Double`0.2 であり、無限に繰り返される 0.20000000000000001 として格納されている値を持つバイナリ小数部分。 2 番目のステートメントでは、リテラルの型文字`D`強制的にオペランドは両方とも`Decimal`0.2 であり、正確に表現します。  
  
 [!code-vb[VbVbalrOperators#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#32)]  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- [算術演算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [トラブルシューティング (データ型)](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Visual Basic における算術演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [\ 演算子 (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)
