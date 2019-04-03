---
title: 文字列とその他の型との変換 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- data type conversion [Visual Basic], string
- conversions [Visual Basic], type
- string conversion [Visual Basic]
- conversions [Visual Basic], data type
- type conversion [Visual Basic], string
- regional options
ms.assetid: c3a99596-f09a-44a5-81dd-1b89a094f1df
ms.openlocfilehash: 1e42fca7800a76cab10fd60058e34d31ae8b8830
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58821662"
---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a>文字列とその他の型との変換 (Visual Basic)
、数値を変換する`Boolean`、または日付/時刻値を、`String`します。 逆方向に変換することもできます。-数値、文字列値から`Boolean`、または`Date`: 文字列の内容は、先のデータ型の有効な値として解釈される場合。 できない場合、実行時エラーが発生します。  
  
 どちらの方向でも、これらすべての割り当ての変換は縮小変換します。 型変換のキーワードを使用する必要があります (`CBool`、 `CByte`、 `CDate`、 `CDbl`、 `CDec`、 `CInt`、 `CLng`、 `CSByte`、 `CShort`、 `CSng`、 `CStr`、`CUInt`、 `CULng`、 `CUShort`、および`CType`)。 <xref:Microsoft.VisualBasic.Strings.Format%2A>と<xref:Microsoft.VisualBasic.Conversion.Val%2A>関数を使用する文字列や数値の間の変換をさらに制御します。  
  
 クラスまたは構造体を定義している場合は、間の変換演算子で型を定義できます`String`と、クラスまたは構造体の型。 詳細については、「[方法 :変換演算子を定義](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)します。  
  
## <a name="conversion-of-numbers-to-strings"></a>数値の文字列への変換  
 使用することができます、`Format`だけでなく、適切な桁の数字を含めることができますが、書式設定された文字列を数値に変換する関数が通貨記号などの記号も書式設定 (など`$`)、何千もの区切り記号または*数字のグループ化シンボル*(など`,`)、および小数点記号 (など`.`)。 `Format` に従って適切なシンボルを自動的に使用して、**地域のオプション**、Windows で指定された設定**コントロール パネル**の です。  
  
 なお、連結したもの (`&`) 演算子は文字列に数値を暗黙的に、次の例は変換できます。  
  
```  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a>文字列の数値への変換  
 使用することができます、`Val`関数を明示的に文字列内の数字を数値に変換します。 `Val` 数字、スペース、タブ、改行、または期間以外の文字を検出するまでは、文字列を読み取ります。 シーケンスは、"& O"と"(& H)"記数法の底を変更して、スキャンが終了します。 読み取りを停止するまで`Val`を数値に適切なすべての文字に変換します。 たとえば、次のステートメントが値を返します`141.825`します。  
  
 `Val("   14   1.825 miles")`  
  
 Visual Basic では、文字列を数値に変換して、使用、**地域のオプション**、Windows で指定された設定**コントロール パネル**何千もの解釈の区切り記号、小数点区切り文字、および通貨記号。 つまり、設定も、別の 1 つ下への変換で成功するように可能性があります。 たとえば、`"$14.20"`が許容される、フランス語のロケールではなく英語 (米国) ロケールにします。  
  
## <a name="see-also"></a>関連項目

- [Visual Basic における型変換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [拡大変換と縮小変換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [暗黙の型変換と明示的な型変換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [方法: オブジェクトを Visual Basic で別の型に変換します。](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [配列変換](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)
- [データの種類](../../../../visual-basic/language-reference/data-types/index.md)
- [データ型変換関数](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [.NET Framework ベースの国際対応アプリケーションの概要](/visualstudio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)
