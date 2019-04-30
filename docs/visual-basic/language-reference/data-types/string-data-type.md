---
title: 文字列型 (String) (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.String
helpviewer_keywords:
- strings [Visual Basic], character
- strings [Visual Basic], fixed-length
- string keyword [Visual Basic]
- fixed-length strings [Visual Basic], string data type
- literals [Visual Basic], string
- text [Visual Basic], String data type
- $ identifier type character
- String data type
- fixed-length strings
- string literals [Visual Basic]
- data types [Visual Basic], assigning
- String literals [Visual Basic]
- identifier type characters [Visual Basic], $
ms.assetid: 15ac03f5-cabd-42cc-a754-1df3893c25d9
ms.openlocfilehash: 3e87dc6527b4351467b1155439ee8266157c16ff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971716"
---
# <a name="string-data-type-visual-basic"></a>文字列型 (String) (Visual Basic)
0 ~ 65535 の値範囲の符号なし 16 ビット (2 バイト) コード ポイントのシーケンスを保持します。 各*コード ポイント*、または文字コードを 1 つの Unicode 文字を表します。 文字列は、0 からおよそ 20億を含めることができます (2 ^31) の Unicode 文字。  
  
## <a name="remarks"></a>Remarks  
 使用して、`String`データ型の配列の管理オーバーヘッドがなく、複数の文字を保持するために`Char()`、配列の`Char`要素。  
  
 既定値`String`は`Nothing`(null 参照)。 これはいない空の文字列と同じ (値`""`)。  
  
## <a name="unicode-characters"></a>Unicode 文字  
 Unicode の最初の 128 個のコード ポイント (0 ~ 127) は、文字および記号の標準的な US キーボード上に対応します。 これら最初の 128 個のコード ポイントは、ASCII 文字セットの定義と同じです。 2 番目の 128 個のコード ポイント (128 ~ 255) では、ラテン語系のアルファベット文字、アクセント記号、通貨記号、および分数などの特殊文字を表します。 Unicode では、さまざまなシンボルを他のコード ポイント (256 ~ 65535) を使用します。 これには、世界中のテキスト文字、分音記号、および数学的、技術的な記号が含まれます。  
  
 などのメソッドを使用することができます<xref:System.Char.IsDigit%2A>と<xref:System.Char.IsPunctuation%2A>で個々 の文字で、`String`変数を Unicode の分類を決定します。  
  
## <a name="format-requirements"></a>書式の要件  
 囲む必要があります、`String`引用符で囲まれたリテラル (`" "`)。 2 つの連続する引用符を使用する場合は、文字列内の文字の 1 つとして、引用符を含める必要があります、(`""`)。 次に例を示します。  
  
```  
Dim j As String = "Joe said ""Hello"" to me."  
Dim h As String = "Hello"  
' The following messages all display the same thing:  
' "Joe said "Hello" to me."  
MsgBox(j)  
MsgBox("Joe said " & """" & h & """" & " to me.")  
MsgBox("Joe said """ & h & """ to me.")  
```  
  
 文字列に引用符を表す、連続する引用符は開始と終了引用符に依存しないことに注意してください、`String`リテラル。  
  
## <a name="string-manipulations"></a>文字列操作  
 文字列を割り当てると、`String`変数、その文字列は*不変*、その長さまたは内容を変更することができることはできません。 何らかの方法で文字列を変更するとき、Visual Basic は新しい文字列を作成および 1 つ前を破棄します。 `String`変数をポイントし、新しい文字列。  
  
 内容を操作することができます、`String`さまざまな文字列関数を使用して変数。 次の例を示しています、<xref:Microsoft.VisualBasic.Strings.Left%2A>関数  
  
```  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 別のコンポーネントによって作成される文字列は、先頭または末尾のスペースで埋められます可能性があります。 このような文字列を受信する場合は使用できます、 <xref:Microsoft.VisualBasic.Strings.Trim%2A>、 <xref:Microsoft.VisualBasic.Strings.LTrim%2A>、および<xref:Microsoft.VisualBasic.Strings.RTrim%2A>これらのスペースを削除する関数。  
  
 文字列操作の詳細については、次を参照してください。[文字列](../../../visual-basic/programming-guide/language-features/strings/index.md)します。  
  
## <a name="programming-tips"></a>プログラミングのヒント  
  
- **負の数。** 文字がによって保持されていることに注意してください。`String`署名されていないと、負の値を表すことはできません。 いずれの場合も、行わないで`String`数値の値を保持します。  
  
- **相互運用の考慮事項。** 例のオートメーションまたは COM オブジェクト、.NET framework では、作成されていないコンポーネントとやり取りする場合、他の環境では文字列の文字の別のデータ幅 (8 ビット) ことに注意してください。 このようなコンポーネントに 8 ビット文字の文字列引数を渡す場合の宣言として`Byte()`、配列の`Byte`、要素の代わりに`String`新しい Visual Basic コードで。  
  
- **型宣言文字。** 識別子の型文字を付加`$`任意の識別子に強制的に、`String`データ型。 `String` リテラルの型文字がありません。 ただし、コンパイラは、引用符で囲まれたリテラルを扱います (`" "`) として`String`します。  
  
- **フレームワークの型。** .NET Framework に対応する型は、<xref:System.String?displayProperty=nameWithType>クラス。  
  
## <a name="see-also"></a>関連項目

- <xref:System.String?displayProperty=nameWithType>
- [データの種類](../../../visual-basic/language-reference/data-types/index.md)
- [Char データ型](../../../visual-basic/language-reference/data-types/char-data-type.md)
- [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [変換の概要](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [方法: 符号なしの型を使用する Windows の機能を呼び出す](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [データ型の有効な使用方法](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
