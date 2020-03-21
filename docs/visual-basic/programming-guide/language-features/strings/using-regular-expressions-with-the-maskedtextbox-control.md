---
title: MaskedTextBox コントロールによる正規表現を使用する
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], regular expressions
- strings [Visual Basic], masked edit
ms.assetid: 2a048fb0-7053-487d-b2c5-ffa5e22ed6f9
ms.openlocfilehash: b997f6f495fca51e888bb995fee0361d29d68048
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148285"
---
# <a name="using-regular-expressions-with-the-maskedtextbox-control-in-visual-basic"></a>Visual Basic の MaskedTextBox コントロールによる正規表現を使用する
この例では、コントロールを使用するために単純な正規表現を変換する<xref:System.Windows.Forms.MaskedTextBox>方法を示します。  
  
## <a name="description-of-the-masking-language"></a>マスキング言語の説明  
 標準<xref:System.Windows.Forms.MaskedTextBox>のマスク言語は、Visual Basic 6.0`Masked Edit`のコントロールで使用される言語に基づいており、そのプラットフォームから移行するユーザーになじみのあるものにする必要があります。  
  
 コントロール<xref:System.Windows.Forms.MaskedTextBox.Mask%2A>のプロパティは<xref:System.Windows.Forms.MaskedTextBox>、使用する定型入力を指定します。 マスクは、次の表の 1 つ以上のマスク要素で構成される文字列である必要があります。  
  
|マスキング要素|説明|正規表現要素|  
|---------------------|-----------------|--------------------------------|  
|0|0 から 9 までの任意の 1 つの数字。 入力が必要です。|\d|  
|9|数字またはスペース。 入力はオプションです。|[ \d]?|  
|#|数字またはスペース。 入力はオプションです。 マスク内でこの位置を空白のままにすると、スペースとしてレンダリングされます。 プラス (+) とマイナス (-) 記号が許可されます。|[ \d+-] ?|  
|L|ASCII 文字。 入力が必要です。|[a-zA-Z]|  
|?|ASCII 文字。 入力はオプションです。|[a-zA-Z]?|  
|&|文字です。 入力が必要です。|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]|  
|C|文字です。 入力はオプションです。|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]?|  
|A|英数字。 入力はオプションです。|\W|  
|.|カルチャに適した小数点のプレースホルダー。|使用できません。|  
|,|カルチャに適した千のプレースホルダー。|使用できません。|  
|:|カルチャに適した時刻区切り記号。|使用できません。|  
|/|カルチャに適した日付区切り記号。|使用できません。|  
|$|カルチャに適した通貨記号。|使用できません。|  
|\<|その後の文字をすべて小文字に変換します。|使用できません。|  
|>|後に続くすべての文字を大文字に変換します。|使用できません。|  
|&#124;|前のシフトを上または下に戻します。|使用できません。|  
|&#92;|マスク文字をエスケープしてリテラルに変換します。 "\\\\" は、バックスラッシュのエスケープ シーケンスです。|&#92;|  
|その他のすべての文字。|リテラル。 マスク以外のすべての要素は、 内<xref:System.Windows.Forms.MaskedTextBox>に自分自身として表示されます。|その他のすべての文字。|  
  
 10 進数 (.)、1000 分 (,)、時刻 (:)、日付 (/)、通貨 ($) の各シンボルは、既定でアプリケーションのカルチャで定義されているシンボルを表示します。 プロパティを使用して、別のカルチャのシンボルを強制的に<xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A>表示できます。  
  
## <a name="regular-expressions-and-masks"></a>正規表現とマスク  
 正規表現とマスクを使用してユーザー入力を検証することはできますが、完全に同じではありません。 正規表現はマスクよりも複雑なパターンを表現できますが、マスクは同じ情報をより簡潔に、文化的に関連する形式で表現できます。  
  
 次の表は、4 つの正規表現と、それぞれに対応するマスクを比較しています。  
  
|Regular Expression|Mask|Notes|  
|------------------------|----------|-----------|  
|`\d{2}/\d{2}/\d{4}`|`00/00/0000`|マスク`/`内の文字は論理的な日付区切り記号であり、アプリケーションの現在のカルチャに適した日付区切り記号としてユーザーに表示されます。|  
|`\d{2}-[A-Z][a-z]{2}-\d{4}`|`00->L<LL-0000`|3 文字の月の省略形が、先頭の大文字と小文字の後に続く 2 つの小文字で表示される米国の形式の日付 (日、月の省略形、年) です。|  
|`(\(\d{3}\)-)?\d{3}-d{4}`|`(999)-000-0000`|米国の電話番号、市外局番はオプションです。 ユーザーがオプションの文字を入力しない場合は、スペースを入力するか、最初の 0 で表されるマスク内の位置にマウスポインターを直接置くことができます。|  
|`$\d{6}.00`|`$999,999.00`|0 ~ 999999 の範囲の通貨値。 通貨、1000 分、および 10 進数の文字は、実行時にカルチャ固有の同等の文字に置き換えられます。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>
- <xref:System.Windows.Forms.MaskedTextBox>
- [Visual Basic における文字列の検証](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
- [MaskedTextBox コントロール](../../../../framework/winforms/controls/maskedtextbox-control-windows-forms.md)
