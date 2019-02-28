---
title: Visual Basic における算術演算子
ms.date: 07/20/2015
helpviewer_keywords:
- type safety
- operators [Visual Basic], bitwise
- operators [Visual Basic], bit-shift
- bitwise operators [Visual Basic]
- bit-shift operators [Visual Basic]
- zero, division by zero
- operators [Visual Basic], arithmetic
- division [Visual Basic], by zero
- Visual Basic code, operators
- arithmetic operators [Visual Basic], about arithmetic operators
ms.assetid: 325dac7a-ea4f-41d5-8b48-f6e904211569
ms.openlocfilehash: 2bd88b2df91c38d658e46157a9a83ce44ab9f25c
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981271"
---
# <a name="arithmetic-operators-in-visual-basic"></a>Visual Basic における算術演算子
算術演算子を使用して、多くのリテラル、変数、その他の式、関数とプロパティの呼び出し、および定数によって表される数値の計算に関連する一般的な算術演算を実行します。 算術演算子にも分類は、ビット シフト演算子のオペランドのビットごとのレベルで動作し、ビット パターンを左または右にシフトです。  
  
## <a name="arithmetic-operations"></a>算術演算  
 組み合わせて式の中で 2 つの値を追加することができます、 [+ 演算子](../../../../visual-basic/language-reference/operators/addition-operator.md)、一方から他方の減算または、 [-演算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md)例を次に示します。  
  
 [!code-vb[VbVbalrOperators#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#57)]  
  
 否定を使用しても、 [-演算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/subtraction-operator.md)が 1 つだけのオペランドで次の例を示します。  
  
 [!code-vb[VbVbalrOperators#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#58)]  
  
 乗算と除算の使用、 [* 演算子](../../../../visual-basic/language-reference/operators/multiplication-operator.md)と[/演算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/floating-point-division-operator.md)、それぞれに、次の例を示します。  
  
 [!code-vb[VbVbalrOperators#59](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#59)]  
  
 指数演算を使用して、 [^ 演算子](../../../../visual-basic/language-reference/operators/exponentiation-operator.md)例を次に示します。  
  
 [!code-vb[VbVbalrOperators#60](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#60)]  
  
 整数の除算を使用して実施、 [\ 演算子 (Visual Basic)](../../../../visual-basic/language-reference/operators/integer-division-operator.md)します。 整数除算の商を返します、回数の合計を表す整数除数に分割ができます、残りの部分を考慮せず被除数。 除数と被除数の両方が整数型にする必要があります (`SByte`、 `Byte`、 `Short`、 `UShort`、 `Integer`、 `UInteger`、 `Long`、および`ULong`) この演算子。 他のすべての種類は、最初の整数型に変換する必要があります。 次の例では、整数の除算を示します。  
  
 [!code-vb[VbVbalrOperators#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#61)]  
  
 使用して、剰余演算が実行される、 [Mod 演算子](../../../../visual-basic/language-reference/operators/mod-operator.md)します。 この演算子は、整数回数、被除数を除数で割った剰余を返します。 除数と被除数の両方が整数型の場合、返される値は不可欠です。 除数と被除数が浮動小数点型の場合、返される値が浮動小数点もします。 次の例では、この動作を示します。  
  
 [!code-vb[VbVbalrOperators#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbalrOperators#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#63)]  
  
### <a name="attempted-division-by-zero"></a>0 による除算  
 0 による除算では、関連するデータ型によって異なる結果があります。 整数の区分で (`SByte`、 `Byte`、 `Short`、 `UShort`、 `Integer`、 `UInteger`、 `Long`、 `ULong`)、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]スロー、<xref:System.DivideByZeroException>例外。 除算操作で、`Decimal`または`Single`データ型、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]もスローされます、<xref:System.DivideByZeroException>例外。  
  
 関連する浮動小数点の区分で、`Double`データ型の場合は、例外がスローされないと、結果は、クラスのメンバーを表す<xref:System.Double.NaN>、 <xref:System.Double.PositiveInfinity>、または<xref:System.Double.NegativeInfinity>被除数に応じて、します。 次の表に、除算の結果、`Double`値を 0 でします。  
  
|被除数のデータ型|除数のデータ型|被除数の値|結果|  
|---|---|---|---|  
|`Double`|`Double`|0|<xref:System.Double.NaN> (非数学的に定義されている数)|  
|`Double`|`Double`|> 0|<xref:System.Double.PositiveInfinity>|  
|`Double`|`Double`|\< 0|<xref:System.Double.NegativeInfinity>|  
  
 キャッチしたときに、<xref:System.DivideByZeroException>例外、それを処理するためのメンバーを使用することができます。 たとえば、<xref:System.Exception.Message%2A>プロパティは、例外のメッセージ テキストを保持します。 詳細については、[Try...Catch...Finally ステートメント](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)を参照してください。  
  
## <a name="bit-shift-operations"></a>ビット シフト操作  
 ビット シフト操作では、ビット パターン上で算術シフトを実行します。 パターンは、左側のオペランドで含まれているし、右側のオペランドがパターンをシフトする位置の数を指定します。 右側に、パターンを切り替えることができる、 [>> 演算子](../../../../visual-basic/language-reference/operators/right-shift-operator.md)または左側に、 [<< 演算子](../../../../visual-basic/language-reference/operators/left-shift-operator.md)します。  
  
 パターンのオペランドのデータ型である必要があります`SByte`、 `Byte`、 `Short`、 `UShort`、 `Integer`、 `UInteger`、 `Long`、または`ULong`します。 シフト量オペランドのデータ型である必要があります`Integer`に拡大変換する必要がありますまたは`Integer`します。  
  
 算術シフトは循環、つまり、もう一方の端に結果の 1 つの端のシフトは行われません。 シフトによって空いたビット位置は、次のように設定されます。  
  
-   算術左シフトの場合は 0  
  
-   正の数の算術右シフトの場合は 0  
  
-   符号なしのデータ型の算術右シフトの場合は 0 (`Byte`、 `UShort`、 `UInteger`、 `ULong`)  
  
-   負の数値の算術右シフトの 1 (`SByte`、 `Short`、 `Integer`、または`Long`)  
  
 次の例では、シフト、`Integer`左と右の両方の値します。  
  
 [!code-vb[VbVbalrOperators#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#64)]  
  
 算術シフトでは、オーバーフロー例外が生成されません。  
  
## <a name="bitwise-operations"></a>ビットごとの演算  
 論理演算子は、だけでなく`Not`、 `Or`、 `And`、および`Xor`も数値で使用する場合にビットごとの演算を実行します。 詳細については、「ビットごとの操作」を参照してください[論理および Visual Basic でビットごとの演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)します。  
  
## <a name="type-safety"></a>タイプ セーフ  
 オペランドは同じ型ので通常必要があります。 使用した追加を実行している場合など、`Integer`変数、する必要がありますに追加する別`Integer`して、変数は、型の変数に結果を割り当てる必要があります`Integer`もします。  
  
 適切なタイプ セーフをことを確認する方法の 1 つコーディングの推奨手順を使用するが、 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)します。 設定した場合`Option Strict On`、Visual Basic を自動的に実行*タイプ セーフ*変換します。 追加しようとする場合など、`Integer`変数を`Double`変数に値を割り当てると、`Double`変数、操作は正常に続行、ため、`Integer`値に変換できる`Double`データを失うことがなく。 型の安全でない変換でコンパイラ エラーが発生する一方で`Option Strict On`します。 追加しようとする場合など、`Integer`変数を`Double`変数に値を割り当てると、`Integer`変数、コンパイラ エラー結果、ため、`Double`変数を型に暗黙的に変換できません`Integer`。  
  
 設定した場合`Option Strict Off`、ただし、Visual Basic を実行する暗黙的な縮小変換のデータまたは精度の予期しない損失が発生する可能性が。 このため、私たちにを使用することお勧め`Option Strict On`運用環境のコードを記述する場合。 詳細については、「 [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目
- [算術演算子](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [ビット シフト演算子](../../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Visual Basic における比較演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Visual Basic の連結演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
- [Visual Basic での論理とビット処理演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [演算子の効率のよい組み合わせ](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
