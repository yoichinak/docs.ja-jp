---
title: 演算子の結果のデータ型 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], operator result data types
- result data types [Visual Basic]
- operator result data types [Visual Basic]
- operators [Visual Basic], data types
- data types [Visual Basic], ranges
- operators [Visual Basic], result data types
ms.assetid: 9d524533-e1a1-4aa8-b1b8-622068173d06
ms.openlocfilehash: 45dcc80ee791da1c2731ba32f0ebd34564faf806
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814984"
---
# <a name="data-types-of-operator-results-visual-basic"></a>演算子の結果のデータ型 (Visual Basic)
Visual Basic では、オペランドのデータ型に基づく操作の結果のデータ型を決定します。 場合によっては、データ型のいずれかのオペランドよりも広い範囲をこれがあります。  
  
## <a name="data-type-ranges"></a>データ型の範囲  
 最小から最大値、順序で、該当するデータ型の範囲は次のとおりです。  
  
-   [ブール](../../../visual-basic/language-reference/data-types/boolean-data-type.md): 2 つの値  
  
-   [SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)、[バイト](../../../visual-basic/language-reference/data-types/byte-data-type.md)— 256 の整数の値  
  
-   [短い](../../../visual-basic/language-reference/data-types/short-data-type.md)、 [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md) — 65,536 (6.5... E + 4) 使用可能な整数値  
  
-   [整数](../../../visual-basic/language-reference/data-types/integer-data-type.md)、 [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md) — 4,294,967,296 (4.2. E + 9) 使用可能な整数値  
  
-   [長い](../../../visual-basic/language-reference/data-types/long-data-type.md)、 [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md) — 18,446,744,073,709,551,615 (1.8... E + 19) 使用可能な整数値  
  
-   [10 進](../../../visual-basic/language-reference/data-types/decimal-data-type.md)-1.5... E + 29 可能な整数値、最大の範囲は 7.9... E + 28 (絶対値)  
  
-   [1 つ](../../../visual-basic/language-reference/data-types/single-data-type.md)-最大範囲 3.4 E + 38 (絶対値)  
  
-   [二重](../../../visual-basic/language-reference/data-types/double-data-type.md)-最大範囲 1.7 E + 308 (絶対値)  
  
 Visual Basic データ型の詳細については、[データ型](../../../visual-basic/language-reference/data-types/index.md)を参照してください。  
  
 オペランドが評価された場合に[Nothing](../../../visual-basic/language-reference/nothing.md)、Visual Basic の算術演算子が 0 として処理します。  
  
## <a name="decimal-arithmetic"></a>10 進数の算術演算  
 なお、 [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)データ型はどちらも浮動小数点も整数。  
  
 場合のいずれかのオペランドを`+`、 `–`、 `*`、 `/`、または`Mod`操作が`Decimal`がないと`Single`または`Double`、Visual Basicをもう一方のオペランドを拡大する`Decimal`. 操作の実行`Decimal`、そして結果のデータ型は`Decimal`します。  
  
## <a name="floating-point-arithmetic"></a>浮動小数点演算  
 Visual Basic でのほとんどの浮動小数点演算を実行する[二重](../../../visual-basic/language-reference/data-types/double-data-type.md)などの操作は、最も効率的なデータを入力します。 ただし、1 つのオペランドが場合[単一](../../../visual-basic/language-reference/data-types/single-data-type.md)がないと`Double`、Visual Basic での操作を実行します`Single`します。 各オペランドは、操作の前に適切なデータ型を必要に応じて、拡大変換し、結果がそのデータ型。  
  
### <a name="-and--operators"></a>/、^ 演算子  
 `/`のみの演算子が定義されて、 [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)、[単一](../../../visual-basic/language-reference/data-types/single-data-type.md)と[二重](../../../visual-basic/language-reference/data-types/double-data-type.md)データ型。 Visual Basic の拡大操作の前に適切なデータ型を必要に応じて、各オペランドと結果のデータ型。  
  
 次の表は、結果のデータ型、`/`演算子。 このテーブルは、対称; ことに注意してください。オペランドのデータ型の特定の組み合わせについては、結果のデータ型は、オペランドの順序に関係なく同じです。  
  
||||||  
|---|---|---|---|---|  
||`Decimal`|`Single`|`Double`|任意の整数型|  
|`Decimal`|Decimal (10 進数型)|Single|倍精度浮動小数点型|Decimal (10 進数型)|  
|`Single`|Single|Single|倍精度浮動小数点型|Single|  
|`Double`|倍精度浮動小数点型|倍精度浮動小数点型|倍精度浮動小数点型|倍精度浮動小数点型|  
|任意の整数型|Decimal (10 進数型)|Single|倍精度浮動小数点型|倍精度浮動小数点型|  
  
 `^`のみの演算子が定義されている、`Double`データ型。 Visual Basic の拡大に必要に応じて、各オペランド`Double`、演算、およびデータ型は常に、結果の前に`Double`します。  
  
## <a name="integer-arithmetic"></a>整数の算術演算  
 整数演算の結果のデータ型は、オペランドのデータ型に依存します。 一般に、Visual Basic では、結果のデータ型を決定するため、次のポリシーを使用します。  
  
-   二項演算子の両方のオペランドが同じであるかどうか、結果がそのデータ型をデータ型します。 例外は、 `Boolean`、これは強制的に`Short`します。  
  
-   符号付きのオペランドの符号なしのオペランドが参加すると場合、結果には符号付きの型で、最低どちらかのオペランドとして。  
  
-   それ以外の場合、結果は、通常の 2 つのオペランドのデータ型のうち、大きい方。  
  
 結果のデータ型がありますいずれかのオペランドのデータ型と同じに注意してください。  
  
> [!NOTE]
>  結果のデータ型は、常に、操作によって発生したすべての可能な値を保持するのに十分な大きさされません。 <xref:System.OverflowException>値が大きすぎて結果のデータ型の場合、例外が発生することができます。  
  
### <a name="unary--and--operators"></a>単項 + と ~ 演算子  
 次の表は、2 つの単項演算子の結果のデータ型を示します`+`と`–`します。  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|単項 `+`|Short|SByte|Byte|Short|UShort|整数型|UInteger|Long|ULong|  
|単項 `–`|Short|SByte|Short|Short|整数型|整数型|Long|Long|Decimal (10 進数型)|  
  
### <a name="-and--operators"></a><\< >> 演算子  
 次の表は、2 つのビット シフト演算子の結果のデータ型を示します`<<`と`>>`します。 各ビット シフト演算子は、Visual Basic は、左側のオペランド (シフトするビット パターン) の単項演算子として扱います。  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`<<`, `>>`|Short|SByte|Byte|Short|UShort|整数型|UInteger|Long|ULong|  
  
 左のオペランドが場合`Decimal`、 `Single`、 `Double`、または`String`、Visual Basic に変換しようとしました。 `Long` 、演算、およびデータ型は、結果の前に`Long`します。 右側のオペランド (シフトするビット位置の数) である必要があります`Integer`または型に拡大変換を`Integer`します。  
  
### <a name="binary----and-mod-operators"></a>バイナリ +、-、*、および Mod 演算子  
 次の表は、結果のバイナリ データ型`+`と`–`演算子と`*`と`Mod`演算子。 このテーブルは、対称; ことに注意してください。オペランドのデータ型の特定の組み合わせについては、結果のデータ型は、オペランドの順序に関係なく同じです。  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Short|SByte|Short|Short|整数型|整数型|Long|Long|Decimal (10 進数型)|  
|`SByte`|SByte|SByte|Short|Short|整数型|整数型|Long|Long|Decimal (10 進数型)|  
|`Byte`|Short|Short|Byte|Short|UShort|整数型|UInteger|Long|ULong|  
|`Short`|Short|Short|Short|Short|整数型|整数型|Long|Long|Decimal (10 進数型)|  
|`UShort`|整数型|整数型|UShort|整数型|UShort|整数型|UInteger|Long|ULong|  
|`Integer`|整数型|整数型|整数型|整数型|整数型|整数型|Long|Long|Decimal (10 進数型)|  
|`UInteger`|Long|Long|UInteger|Long|UInteger|Long|UInteger|Long|ULong|  
|`Long`|Long|Long|Long|Long|Long|Long|Long|Long|Decimal (10 進数型)|  
|`ULong`|Decimal (10 進数型)|Decimal (10 進数型)|ULong|Decimal (10 進数型)|ULong|Decimal (10 進数型)|ULong|Decimal (10 進数型)|ULong|  
  
### <a name="-operator"></a>\ 演算子  
 次の表は、結果のデータ型、`\`演算子。 このテーブルは、対称; ことに注意してください。オペランドのデータ型の特定の組み合わせについては、結果のデータ型は、オペランドの順序に関係なく同じです。  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Short|SByte|Short|Short|整数型|整数型|Long|Long|Long|  
|`SByte`|SByte|SByte|Short|Short|整数型|整数型|Long|Long|Long|  
|`Byte`|Short|Short|Byte|Short|UShort|整数型|UInteger|Long|ULong|  
|`Short`|Short|Short|Short|Short|整数型|整数型|Long|Long|Long|  
|`UShort`|整数型|整数型|UShort|整数型|UShort|整数型|UInteger|Long|ULong|  
|`Integer`|整数型|整数型|整数型|整数型|整数型|整数型|Long|Long|Long|  
|`UInteger`|Long|Long|UInteger|Long|UInteger|Long|UInteger|Long|ULong|  
|`Long`|Long|Long|Long|Long|Long|Long|Long|Long|Long|  
|`ULong`|Long|Long|ULong|Long|ULong|Long|ULong|Long|ULong|  
  
 場合のいずれかのオペランド、`\`演算子は[Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)、[単一](../../../visual-basic/language-reference/data-types/single-data-type.md)、または[二重](../../../visual-basic/language-reference/data-types/double-data-type.md)、Visual Basic に変換しようとしました[時間の長い](../../../visual-basic/language-reference/data-types/long-data-type.md)。、演算、およびデータ型は、結果の前に`Long`します。  
  
## <a name="relational-and-bitwise-comparisons"></a>リレーショナルとビットごとの比較  
 リレーショナル操作の結果のデータ型 (`=`、 `<>`、 `<`、 `>`、 `<=`、 `>=`) は常に`Boolean`[ブール データ型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)します。 論理操作に対しても同様です (`And`、 `AndAlso`、 `Not`、 `Or`、 `OrElse`、 `Xor`) で`Boolean`オペランド。  
  
 論理演算の結果のデータ型は、オペランドのデータ型に依存します。 なお`AndAlso`と`OrElse`に対してのみ定義されます`Boolean`、Visual Basic を必要に応じて、各オペランドを変換します`Boolean`操作を実行する前にします。  
  
### <a name="-----and--operators"></a>=、<>、 \<、>、 \<、=、> = 演算子  
 両方のオペランドが場合`Boolean`、Visual Basic では考慮`True`をより小さい`False`します。 場合は、数値型と比較されます、`String`を変換しようとしている Visual Basic、`String`に`Double`操作の前にします。 A`Char`または`Date`オペランドは同じデータ型のオペランドとのみ比較できます。 結果のデータ型は常に`Boolean`します。  
  
### <a name="bitwise-not-operator"></a>ビットごとの Not 演算子  
 次の表は、結果のビットごとのデータ型`Not`演算子。  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Not`|ブール型|SByte|Byte|Short|UShort|整数型|UInteger|Long|ULong|  
  
 オペランドが場合`Decimal`、 `Single`、 `Double`、または`String`、Visual Basic に変換しようとしました。 `Long` 、演算、およびデータ型は、結果の前に`Long`します。  
  
### <a name="bitwise-and-or-and-xor-operators"></a>ビット演算子、または、および Xor 演算子  
 次の表は、結果のビットごとのデータ型`And`、 `Or`、および`Xor`演算子。 このテーブルは、対称; ことに注意してください。オペランドのデータ型の特定の組み合わせについては、結果のデータ型は、オペランドの順序に関係なく同じです。  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|ブール型|SByte|Short|Short|整数型|整数型|Long|Long|Long|  
|`SByte`|SByte|SByte|Short|Short|整数型|整数型|Long|Long|Long|  
|`Byte`|Short|Short|Byte|Short|UShort|整数型|UInteger|Long|ULong|  
|`Short`|Short|Short|Short|Short|整数型|整数型|Long|Long|Long|  
|`UShort`|整数型|整数型|UShort|整数型|UShort|整数型|UInteger|Long|ULong|  
|`Integer`|整数型|整数型|整数型|整数型|整数型|整数型|Long|Long|Long|  
|`UInteger`|Long|Long|UInteger|Long|UInteger|Long|UInteger|Long|ULong|  
|`Long`|Long|Long|Long|Long|Long|Long|Long|Long|Long|  
|`ULong`|Long|Long|ULong|Long|ULong|Long|ULong|Long|ULong|  
  
 オペランドは場合`Decimal`、 `Single`、 `Double`、または`String`、Visual Basic に変換しようとしました。`Long`前に、演算、および結果のデータ型が同じ場合と、そのオペランドが既に`Long`します。  
  
## <a name="miscellaneous-operators"></a>その他の演算子  
 `&`演算子の連結に対してのみ定義されます`String`オペランド。 Visual Basic の変換を必要に応じて、各オペランド`String`、演算、およびデータ型は常に、結果の前に`String`します。 目的で、`&`演算子、すべての変換を`String`拡大変換と見なされる場合でも`Option Strict`は`On`。  
  
 `Is`と`IsNot`演算子が両方のオペランドは参照型である必要があります。 `TypeOf`.`Is`式は、参照型である最初のオペランドとデータ型の名前を指定する 2 番目のオペランドが必要です。 これらすべてのケースの結果データ型は`Boolean`します。  
  
 `Like`のパターンに一致するのみの演算子が定義されている`String`オペランド。 Visual Basic が、必要に応じて各オペランドを変換しようとしています。`String`操作の前にします。 結果のデータ型は常に`Boolean`します。  
  
## <a name="see-also"></a>関連項目

- [データの種類](../../../visual-basic/language-reference/data-types/index.md)
- [演算子および式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Visual Basic における算術演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Visual Basic における比較演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [演算子](../../../visual-basic/language-reference/operators/index.md)
- [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [算術演算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [比較演算子](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)
