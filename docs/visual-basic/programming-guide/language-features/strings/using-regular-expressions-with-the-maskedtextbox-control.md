---
title: Visual Basic の MaskedTextBox コントロールによる正規表現を使用する
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], regular expressions
- strings [Visual Basic], masked edit
ms.assetid: 2a048fb0-7053-487d-b2c5-ffa5e22ed6f9
ms.openlocfilehash: e0165fb8d573878ae19378b2656d89627680b804
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62024509"
---
# <a name="using-regular-expressions-with-the-maskedtextbox-control-in-visual-basic"></a>Visual Basic の MaskedTextBox コントロールによる正規表現を使用する
この例を使用する正規表現を単純に変換する方法、<xref:System.Windows.Forms.MaskedTextBox>コントロール。  
  
## <a name="description-of-the-masking-language"></a>マスクの言語の説明  
 標準<xref:System.Windows.Forms.MaskedTextBox>で使用される 1 つに基づいてマスク言語、 `Masked Edit` Visual Basic 6.0 を制御し、そのプラットフォームから移行するユーザーにとって馴染み深いにする必要があります。  
  
 <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>のプロパティ、<xref:System.Windows.Forms.MaskedTextBox>コントロールを使用するどのような入力マスクを指定します。 マスクは、1 つ以上の次の表からマスク要素から成る文字列である必要があります。  
  
|要素のマスク|説明|正規表現の要素|  
|---------------------|-----------------|--------------------------------|  
|0|0 から 9 までの 1 桁。 入力は必須です。|\d|  
|9|数字またはスペース。 省略可能。|[\d] でしょうか。|  
|#|数字またはスペース。 省略可能。 この位置は、マスク内の空白のまま、これは、領域としてレンダリングされます。 プラス (+) マイナス記号 (-) 記号が許可されているとします。|[\d+-] でしょうか。|  
|L|ASCII 文字。 入力は必須です。|[- A-za-z]|  
|?|ASCII 文字。 省略可能。|[- A-za-z] でしょうか。|  
|&|文字です。 入力は必須です。|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]|  
|C|文字です。 省略可能。|[\p{Ll}\p{Lu}\p{Lt}\p{Lm}\p{Lo}]?|  
|A|英数字。 省略可能。|\W|  
|.|カルチャに応じた小数点のプレース ホルダーです。|使用できません。|  
|,|何千ものカルチャに適したプレース ホルダーです。|使用できません。|  
|:|カルチャに適切な時刻の区切り記号。|使用できません。|  
|/|カルチャに応じた日付の区切り記号。|使用できません。|  
|$|カルチャに適した通貨記号。|使用できません。|  
|\<|すべての文字を小文字に変換します。|使用できません。|  
|>|大文字に続くすべての文字に変換します。|使用できません。|  
|&#124;|前の shift キーを元に戻しますか下方向にシフトします。|使用できません。|  
|&#92;|リテラルにすることでマスク文字をエスケープします。 "\\\\"円記号のエスケープ シーケンスです。|&#92;|  
|その他のすべての文字。|リテラル。 内のユーザーとしてマスク以外のすべての要素が表示されます<xref:System.Windows.Forms.MaskedTextBox>します。|その他のすべての文字。|  
  
 小数点 (.)、桁区切り (,)、時間 (:)、日付 (/)、および ($) の通貨記号は、アプリケーションのカルチャによって定義されているこれらのシンボルを表示するときに、既定。 使用して別のカルチャのシンボルを表示することを強制することができます、<xref:System.Windows.Forms.MaskedTextBox.FormatProvider%2A>プロパティ。  
  
## <a name="regular-expressions-and-masks"></a>正規表現とマスク  
 正規表現とマスクを使用するには、ユーザー入力を検証する、完全に同等ではありません。 正規表現は、マスクより複雑なパターンを表すことができますより簡潔かつカルチャに応じた形式で、マスクは、同じ情報を表すことができます。  
  
 次の表は、それぞれの 4 つの正規表現と同等のマスクを比較します。  
  
|正規表現|マスク|メモ|  
|------------------------|----------|-----------|  
|`\d{2}/\d{2}/\d{4}`|`00/00/0000`|`/`マスク内の文字は論理日付の区切り記号、およびアプリケーションの現在のカルチャに適切な日付の区切り記号として、ユーザーに表示されます。|  
|`\d{2}-[A-Z][a-z]{2}-\d{4}`|`00->L<LL-0000`|2 つの小文字初期大文字で 3 桁の月の省略形が表示される米国形式の日付 (日、月の省略形、および年)。|  
|`(\(\d{3}\)-)?\d{3}-d{4}`|`(999)-000-0000`|米国の電話番号、市外局番の省略可能です。 場合は、ユーザーは、省略可能な文字を入力するつもりはなく、彼女のスペースを入力するかマウス ポインターを最初の 0 で表される、マスク内の位置に直接配置します。|  
|`$\d{6}.00`|`$999,999.00`|0 ~ 999999 の範囲内の通貨値。 通貨、1/10,000 のおよび 10 進数の文字は、対応するカルチャに固有の実行時に置き換えられます。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.MaskedTextBox.Mask%2A>
- <xref:System.Windows.Forms.MaskedTextBox>
- [Visual Basic における文字列の検証](../../../../visual-basic/programming-guide/language-features/strings/validating-strings.md)
- [MaskedTextBox コントロール](../../../../framework/winforms/controls/maskedtextbox-control-windows-forms.md)
