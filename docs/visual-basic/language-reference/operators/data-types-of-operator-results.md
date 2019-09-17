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
ms.openlocfilehash: bc7f29ae0e29a4c2fbfdf2e40d2226e174a06d3a
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856047"
---
# <a name="data-types-of-operator-results-visual-basic"></a>演算子の結果のデータ型 (Visual Basic)
Visual Basic は、オペランドのデータ型に基づいて、操作の結果のデータ型を決定します。 場合によっては、これがいずれかのオペランドよりも範囲の広いデータ型である可能性があります。  
  
## <a name="data-type-ranges"></a>データ型の範囲  
 関連するデータ型の範囲は、小さい方から順に、次のようになります。  
  
- [ブール](../../../visual-basic/language-reference/data-types/boolean-data-type.md)値: 2 つの値を指定できます。  
  
- [SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)、 [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md) -256 可能な整数値  
  
- [Short](../../../visual-basic/language-reference/data-types/short-data-type.md)、 [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md) -65536 (6.5... E + 4) 可能な整数値  
  
- [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)、 [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md) -4294967296 (4.2... E + 9) 可能な整数値  
  
- [Long](../../../visual-basic/language-reference/data-types/long-data-type.md)、 [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md) -18446744073709551615 (1.8... E + 19) 可能な整数値  
  
- [10 進](../../../visual-basic/language-reference/data-types/decimal-data-type.md)-1.5... e + 29 可能な整数値、最大範囲 7.9... e + 28 (絶対値)  
  
- [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) : 最大範囲 3.4... E + 38 (絶対値)  
  
- [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) -最大範囲 1.7... E + 308 (絶対値)  
  
 Visual Basic のデータ型の詳細については、「[データ型](../../../visual-basic/language-reference/data-types/index.md)」を参照してください。  
  
 オペランドが[Nothing](../../../visual-basic/language-reference/nothing.md)と評価された場合、Visual Basic 算術演算子は0として処理します。  
  
## <a name="decimal-arithmetic"></a>10進数の算術演算  
 [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)データ型は、浮動小数点と整数のどちらでもないことに注意してください。  
  
 `+` 、`–`、 `Single` `Decimal` `Double`、、または`Mod`演算のオペランドのいずれかがであり、もう一方のオペランドがまたはでない場合は、Visual Basic もう一方のオペランドをに拡大変換します。 `/` `*` `Decimal`. このメソッドはで`Decimal`操作を実行し、結果のデータ型は`Decimal`です。  
  
## <a name="floating-point-arithmetic"></a>浮動小数点演算  
 Visual Basic は、ほとんどの浮動小数点演算を[Double](../../../visual-basic/language-reference/data-types/double-data-type.md)で実行します。これは、このような操作にとって最も効率的なデータ型です。 一方のオペランドが[Single](../../../visual-basic/language-reference/data-types/single-data-type.md)で、もう一方のオペランドが`Double`でない場合、Visual Basic は`Single`で操作を実行します。 必要に応じて各オペランドを適切なデータ型に変換し、その結果をそのデータ型に変換します。  
  
### <a name="-and--operators"></a>/および ^ 演算子  
 演算子は、 [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)、[Single](../../../visual-basic/language-reference/data-types/single-data-type.md)、および[Double](../../../visual-basic/language-reference/data-types/double-data-type.md)データ型に対してのみ定義されます。`/` 演算の前に各オペランドを適切なデータ型に拡大変換すると、結果のデータ型は Visual Basic になります。  
  
 次の表は、 `/`演算子の結果のデータ型を示しています。 このテーブルは対称であることに注意してください。オペランドデータ型の特定の組み合わせについては、オペランドの順序に関係なく、結果のデータ型は同じになります。  
  
||||||  
|---|---|---|---|---|  
||`Decimal`|`Single`|`Double`|任意の整数型|  
|`Decimal`|Decimal (10 進数型)|Single|倍精度浮動小数点型|Decimal (10 進数型)|  
|`Single`|Single|Single|倍精度浮動小数点型|Single|  
|`Double`|倍精度浮動小数点型|倍精度浮動小数点型|倍精度浮動小数点型|倍精度浮動小数点型|  
|任意の整数型|Decimal (10 進数型)|Single|倍精度浮動小数点型|倍精度浮動小数点型|  
  
 演算子は、 `Double`データ型に対してのみ定義されます。 `^` 演算の前に各オペランドを`Double`必要に応じて拡大 Visual Basic し、結果のデータ`Double`型は常にになります。  
  
## <a name="integer-arithmetic"></a>整数演算  
 整数演算の結果のデータ型は、オペランドのデータ型によって異なります。 一般に、Visual Basic では、次のポリシーを使用して結果のデータ型を決定します。  
  
- 二項演算子の両方のオペランドのデータ型が同じである場合、結果はそのデータ型になります。 例外は`Boolean`です。これはに`Short`強制されます。  
  
- 符号なしのオペランドが符号付きのオペランドに含まれている場合、結果の符号付きの型は、少なくともいずれかのオペランドと同じ範囲になります。  
  
- それ以外の場合、結果は通常、2つのオペランドデータ型のうち、大きい方になります。  
  
 結果のデータ型は、どちらのオペランドデータ型とも異なる場合があることに注意してください。  
  
> [!NOTE]
> 結果のデータ型は、操作の結果として得られるすべての値を保持するのに十分な大きさではありません。 値が結果のデータ型に対して大きすぎる場合は、例外が発生する可能性があります。<xref:System.OverflowException>  
  
### <a name="unary--and--operators"></a>単項 + 演算子と–演算子  
 次の表は、2つの単項演算子`+`と`–`の結果のデータ型を示しています。  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|前置`+`|Short|SByte|Byte|Short|UShort|整数型|UInteger|Long|ULong|  
|前置`–`|Short|SByte|Short|Short|整数型|整数型|Long|Long|Decimal (10 進数型)|  
  
### <a name="-and--operators"></a><\<and > > 演算子  
 次の表は、2つのビットシフト演算子`<<`と`>>`の結果のデータ型を示しています。 Visual Basic は、各ビットシフト演算子を左オペランド (シフトされるビットパターン) で単項演算子として扱います。  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`<<`, `>>`|Short|SByte|Byte|Short|UShort|整数型|UInteger|Long|ULong|  
  
 左側の`Decimal`オペランドが`Single` `Long` `String`、、 `Long`、またはの場合、Visual Basic は演算の前に変換しようとし、結果のデータ型はです。 `Double` 右オペランド (シフトするビット位置の数) は、または`Integer`に`Integer`拡大変換される型である必要があります。  
  
### <a name="binary----and-mod-operators"></a>二項演算子 +、– \*、、および Mod 演算子  
 次の表は、 `+`バイナリおよび`–`演算子の結果のデータ型と`*` 、および`Mod`演算子を示しています。 このテーブルは対称であることに注意してください。オペランドデータ型の特定の組み合わせについては、オペランドの順序に関係なく、結果のデータ型は同じになります。  
  
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
  
### <a name="-operator"></a>\\ 演算子  
 次の表は、 `\`演算子の結果のデータ型を示しています。 このテーブルは対称であることに注意してください。オペランドデータ型の特定の組み合わせについては、オペランドの順序に関係なく、結果のデータ型は同じになります。  
  
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
  
 `\`演算子のいずれかのオペランドが[Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)、 [Single](../../../visual-basic/language-reference/data-types/single-data-type.md)、または[Double](../../../visual-basic/language-reference/data-types/double-data-type.md)の場合、Visual Basic は演算の前に[Long](../../../visual-basic/language-reference/data-types/long-data-type.md)への変換を試み、結果`Long`のデータ型はになります。  
  
## <a name="relational-and-bitwise-comparisons"></a>関係とビットごとの比較  
 `=`リレーショナル操作の結果のデータ型 ( `<`、 `<>`、、 `>` `<=`、、 `>=`) は、常`Boolean`に[ブールデータ型](../../../visual-basic/language-reference/data-types/boolean-data-type.md)です。 オペランド`And`の`AndAlso` `Or` `Not`論理演算`OrElse`(、、、、 、`Xor`) でも同じことが当てはまります。 `Boolean`  
  
 ビットごとの論理演算の結果のデータ型は、オペランドのデータ型によって異なります。 とはに対し`Boolean`てのみ定義されており、Visual Basic は演算を`Boolean`実行する前に、必要に応じて各オペランドをに変換します。 `OrElse` `AndAlso`  
  
### <a name="-----and--operators"></a>=、< >、 \<、>、 \<=、および > = 演算子  
 両方のオペランドが`Boolean`の場合、 `True` Visual Basic はより`False`小さいと見なされます。 数値型とを比較`String`した場合、Visual Basic 操作の前に、 `Double` `String`をに変換しようとします。 または`Date`のオペランドは、同じデータ型の別のオペランドとのみ比較できます。 `Char` 結果のデータ型は常`Boolean`にです。  
  
### <a name="bitwise-not-operator"></a>ビットごとの Not 演算子  
 次の表は、ビットごと`Not`の演算子の結果のデータ型を示しています。  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Not`|ブール型|SByte|Byte|Short|UShort|整数型|UInteger|Long|ULong|  
  
 オペランド`Decimal`が`Single` `String` `Long`、、 `Long` 、またはの場合、Visual Basic は演算の前に変換しようとし、結果のデータ型はです。 `Double`  
  
### <a name="bitwise-and-or-and-xor-operators"></a>ビットごとの And、Or、および Xor 演算子  
 次の表は、ビットごと`And`の、 `Or`、および`Xor`演算子の結果のデータ型を示しています。 このテーブルは対称であることに注意してください。オペランドデータ型の特定の組み合わせについては、オペランドの順序に関係なく、結果のデータ型は同じになります。  
  
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
  
 オペランド`Decimal`が`Single` `String` `Long`、、 `Long` 、またはの場合、Visual Basic は演算の前に変換しようとし、結果のデータ型はそのオペランドが既に存在していた場合と同じになります。 `Double`  
  
## <a name="miscellaneous-operators"></a>その他の演算子  
 演算子`&`は、オペランドの`String`連結に対してのみ定義されます。 Visual Basic は、必要に応じて`String`各オペランドを演算の前に変換し、結果`String`のデータ型は常にになります。 `&`演算子の目的では、が`On`の場合`Option Strict`で`String`も、へのすべての変換は拡大と見なされます。  
  
 `Is` および`IsNot`演算子では、両方のオペランドが参照型である必要があります。 `TypeOf`...`Is`式では、最初のオペランドが参照型で、2番目のオペランドがデータ型の名前である必要があります。 これらのすべての場合、結果のデータ`Boolean`型はです。  
  
 演算子`Like`は、オペランドの`String`パターンマッチングに対してのみ定義されます。 Visual Basic は、各オペランドを操作の前`String`に必要に応じて変換しようとします。 結果のデータ型は常`Boolean`にです。  
  
## <a name="see-also"></a>関連項目

- [データの種類](../../../visual-basic/language-reference/data-types/index.md)
- [演算子および式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Visual Basic の算術演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Visual Basic の比較演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [演算子](../../../visual-basic/language-reference/operators/index.md)
- [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [算術演算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [比較演算子](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)
