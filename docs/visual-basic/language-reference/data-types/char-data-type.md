---
title: 文字型 (Char) (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Char
helpviewer_keywords:
- literal type characters [Visual Basic], C
- Char data type
- C literal type character [Visual Basic]
- data types [Visual Basic], assigning
- Char data type [Visual Basic], character literals
ms.assetid: cd7547a9-7855-4e8e-b216-35d74a362657
ms.openlocfilehash: b50c902f69f7602dbad4663dc35bf0a2b932973f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832091"
---
# <a name="char-data-type-visual-basic"></a>文字型 (Char) (Visual Basic)
0 から 65535 まで符号なし 16 ビット (2 バイト) コード ポイントを保持します。 各*コード ポイント*、または文字コードを 1 つの Unicode 文字を表します。  
  
## <a name="remarks"></a>Remarks  
 使用して、`Char`データ型は、1 つのみを保持する必要があるときのオーバーヘッドは必要ありません、文字`String`します。 使用することができる場合によっては`Char()`、配列の`Char`要素、複数の文字を保持するためにします。  
  
 既定値`Char`コード ポイント 0 の文字します。  
  
## <a name="unicode-characters"></a>Unicode 文字  
 Unicode の最初の 128 個のコード ポイント (0 ~ 127) は、文字および記号の標準的な US キーボード上に対応します。 これら最初の 128 個のコード ポイントは、ASCII 文字セットの定義と同じです。 2 番目の 128 個のコード ポイント (128 ~ 255) では、ラテン語系のアルファベット文字、アクセント記号、通貨記号、および分数などの特殊文字を表します。 Unicode では、記号、世界中のテキスト文字、分音記号、数学的、技術的な記号などのさまざまな他のコード ポイント (256 ~ 65535) を使用します。  
  
 などのメソッドを使用する<xref:System.Char.IsDigit%2A>と<xref:System.Char.IsPunctuation%2A>上、 `Char` Unicode 分類を決定する変数。  
  
## <a name="type-conversions"></a>型変換  
 Visual Basic では直接間変換されません`Char`と数値の型。 使用することができます、<xref:Microsoft.VisualBasic.Strings.Asc%2A>または<xref:Microsoft.VisualBasic.Strings.AscW%2A>に変換する関数を`Char`値を`Integer`コード ポイントを表します。 使用することができます、<xref:Microsoft.VisualBasic.Strings.Chr%2A>または<xref:Microsoft.VisualBasic.Strings.ChrW%2A>関数に変換する、`Integer`値を`Char`を持つ、そのコード ポイント。  
  
 型チェック スイッチの場合 ([Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)) は、1 文字の文字列としてそれを識別するリテラルにリテラルの型文字を追加する必要があります、`Char`データ型。 次に例を示します。  
  
```  
Option Strict On  
Dim charVar As Char  
' The following statement attempts to convert a String literal to Char.  
' Because Option Strict is On, it generates a compiler error.  
charVar = "Z"  
' The following statement succeeds because it specifies a Char literal.  
charVar = "Z"C  
```  
  
## <a name="programming-tips"></a>プログラミングのヒント  
  
-   **負の数。** `Char` 符号なしの型は、負の値を表すことはできません。 いずれの場合も、行わないで`Char`数値の値を保持します。  
  
-   **相互運用の考慮事項。** 例のオートメーションまたは COM オブジェクト、.NET framework では、作成されていないコンポーネントを使用する場合、他の環境では文字型の別のデータ幅 (8 ビット) ことに注意してください。 このようなコンポーネントに 8 ビットの引数を渡すと場合、宣言として`Byte`の代わりに`Char`で新しい Visual Basic コードです。  
  
-   **拡大します。** `Char`拡大変換後のデータ型`String`します。 つまり、変換できる`Char`に`String`は発生しませんし、<xref:System.OverflowException?displayProperty=nameWithType>エラー。  
  
-   **型宣言文字。** リテラルの型文字を付加する`C`1 文字の文字列にリテラルを強制的に、`Char`データ型。 `Char` 識別子の型文字がありません。  
  
-   **フレームワークの型。** .NET Framework において対応する型は、<xref:System.Char?displayProperty=nameWithType> 構造体です。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Char?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [データの種類](../../../visual-basic/language-reference/data-types/index.md)
- [String データ型](../../../visual-basic/language-reference/data-types/string-data-type.md)
- [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [方法: 符号なしの型を使用する Windows の機能を呼び出す](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [データ型の有効な使用方法](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
