---
title: 数値データ型 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- integral types [Visual Basic], Visual Basic
- Short data type [Visual Basic], numeric data types
- Double data type [Visual Basic], numeric data types
- Long data type [Visual Basic], Visual Basic numeric data types
- numbers [Visual Basic], whole
- fractions
- numbers
- whole numbers
- integer numbers
- numbers [Visual Basic], integer
- fractional data types [Visual Basic]
- mantissas, of fractional numbers
- mantissas
- data types [Visual Basic], numeric
- Integer data type [Visual Basic], numeric data types
- exponent, of fractional numbers
- integers [Visual Basic]
- numeric data types [Visual Basic], Visual Basic
- Single data type [Visual Basic], numeric types
- Decimal data type [Visual Basic], numeric data types
ms.assetid: a27bd4d0-7e14-43eb-9cc4-b42eaab323c9
ms.openlocfilehash: 75e60cb2a3a934956099ce6fc7d81bf6ecea4d11
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663376"
---
# <a name="numeric-data-types-visual-basic"></a>数値データ型 (Visual Basic)
Visual Basic では、いくつかを提供*数値データ型*のさまざまな表現での数値を処理します。 *整数*型整数を表すのみ (正、負、および 0)、および*非整数*型では、数値を表す整数と小数部の両方でします。  
  
 Visual Basic のデータ型のサイド バイ サイドで比較を示す表を参照してください[データ型](../../../../visual-basic/language-reference/data-types/index.md)します。  
  
## <a name="integral-numeric-types"></a>整数数値型  
 *整数データ型*は小数部のない数だけを表す。  
  
 *署名*整数データ型は[SByte データ型](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)(8 ビット)、 [Short データ型](../../../../visual-basic/language-reference/data-types/short-data-type.md)(16 ビット)、[Integer データ型](../../../../visual-basic/language-reference/data-types/integer-data-type.md)(32 ビット)、および[Long データ型](../../../../visual-basic/language-reference/data-types/long-data-type.md)(64 ビット)。 変数は、小数部ではなく整数を常に保存する場合、これらの型のいずれかとして宣言します。  
  
 *符号なし*整数型には[Byte データ型](../../../../visual-basic/language-reference/data-types/byte-data-type.md)(8 ビット)、 [UShort データ型](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)(16 ビット)、 [UInteger データ型](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)(32 ビット)、および[Ulong 型](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)(64 ビット)。 バイナリ データ、または不明な性質のデータが、変数が含まれる場合は、これらの型のいずれかとしてを宣言します。  
  
### <a name="performance"></a>パフォーマンス  
 算術演算は、他のデータ型よりも整数型の高速です。 最も高速なは、`Integer`と`UInteger`Visual Basic における型。  
  
### <a name="large-integers"></a>大きな整数  
 大きい整数値を保持する必要がある場合、`Integer`データ型が保持できる、使用することができます、`Long`代わりにデータを入力します。 `Long` 変数は、9,223,372,036,854,775,807 を通じて-9,223,372,036,854,775,808 から番号を保持できます。 操作を`Long`でよりも少し低速`Integer`します。  
  
 使用することがさらに大きな値が必要な場合、 [Decimal データ型](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)します。 経由で 79,228,162,514,264,337,593,543,950,335-79,228,162,514,264,337,593,543,950,335 から番号を保持できる、`Decimal`変数の場合は、小数点以下桁数を使用しないでください。 ただし、操作を`Decimal`番号は、その他の任意の数値データ型よりも非常に遅くなります。  
  
### <a name="small-integers"></a>小さい整数  
 完全な範囲を必要としない場合、`Integer`に使用できるデータの種類、`Short`データ型は、-32,768 ~ 32,767 の整数を格納することができます。 最小の整数の範囲の`SByte`データ型は-128 から 127 までの整数値を格納します。 共通言語ランタイムに格納できる場合があります、非常に多数の小さい整数を保持する変数があれば、`Short`と`SByte`変数より効率的にして、メモリ消費量を保存します。 ただし、操作を`Short`と`SByte`でよりもやや低速`Integer`します。  
  
### <a name="unsigned-integers"></a>符号なし整数  
 変数には、負の数を保持する必要はありませんを使用することがわかっている場合、*型の unsigned*`Byte`、 `UShort`、 `UInteger`、および`ULong`します。 正の整数を 2 回よりも小さい符号付きの型を対応するこれらのデータ型の各保持できます (`SByte`、 `Short`、 `Integer`、および`Long`)。 パフォーマンスの面では、各符号なしの型は、対応する符号付きの型と同じくらい効率的です。 具体的には、`UInteger`と共有`Integer`されるすべての基本の数値データ型の中で最も効率的なの区別します。  
  
## <a name="nonintegral-numeric-types"></a>非整数の数値型  
 *整数以外のデータ型*は整数と小数部の両方を持つ数値を表す。  
  
 非整数の数値データ型は`Decimal`(128 ビットの固定小数点)、 [1 つのデータ型](../../../../visual-basic/language-reference/data-types/single-data-type.md)(32 ビットの浮動小数点)、および[Double データ型](../../../../visual-basic/language-reference/data-types/double-data-type.md)(64 ビットの浮動小数点)。 署名されたすべての種類です。 変数には、小数が含まれることができる場合、これらの型のいずれかとしてを宣言します。  
  
 `Decimal` 浮動小数点データ型はありません。 `Decimal` 番号は、バイナリの整数値と値のどの部分が、小数を指定する整数のスケール ファクターがあります。  
  
 使用することができます`Decimal`money 値変数。 利点は、値の有効桁数です。 `Double`データ型が高速で、以下のメモリが必要ですが、丸め誤差が発生します。 `Decimal`データ型は小数点以下桁数が 28 を完全な精度を保持します。  
  
 浮動小数点 (`Single`と`Double`) の数値よりも大きい範囲がある`Decimal`数値しますが、丸め誤差が発生することができます。 浮動小数点型のサポート有効桁数よりも少ない`Decimal`ですより大きい値を表すことができます。  
  
 非整数の数値で表現できる mmmEeee、として mmm は、*仮数*(有効桁数) eee であり、*指数*(10 の累乗) します。 非整数型の最上位の正の値は 7.9228162514264337593543950335 e + 28 `Decimal`、3.4028235 e + 38`Single`との-1.79769313486231570e+308`Double`します。  
  
### <a name="performance"></a>パフォーマンス  
 `Double` 小数部のデータ型の中で最も効率的な現在のプラットフォーム上のプロセッサでは、倍精度浮動小数点演算を実行するためです。 ただし、操作を`Double`などの整数型と同様に高速でない`Integer`します。  
  
### <a name="small-magnitudes"></a>小さい絶対値  
 (0 に最も近い)、最小の可能な大きさの数値の`Double`変数に保持できます - 4.94065645841246544E のような小さい-324 の負の値および 4.94065645841246544E-の正の値。  
  
### <a name="small-fractional-numbers"></a>小さい小数  
 完全な範囲を必要としない場合、`Double`に使用できるデータの種類、 `Single` - 3.4028235 e + 38 ~ 3.4028235 e + 38 から浮動小数点数を格納できるデータ型。 最も小さいマグニチュード`Single`変数は、- 1.401298E-45 の負の値および 1.401298-正の値の 45。 非常に多くの小規模の浮動小数点数を保持する変数があれば、共通言語ランタイムが格納できる場合があります、`Single`変数より効率的にして、メモリ消費量を保存します。  
  
## <a name="see-also"></a>関連項目

- [基本データ型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [文字データ型](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)
- [その他のデータ型](../../../../visual-basic/programming-guide/language-features/data-types/miscellaneous-data-types.md)
- [トラブルシューティング (データ型)](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [方法: 符号なしの型を使用する Windows の機能を呼び出す](../../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
