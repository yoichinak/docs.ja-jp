---
title: EscapeQuotes が True に設定されている場合、二重引用符は有効な区切り記号でないため、区切り記号で分けられたフィールドを読み取れません
ms.date: 07/20/2015
f1_keywords:
- vbrTextFieldParser_IllegalDelimiter
ms.assetid: ab8a0c3a-b89c-4617-9e31-7e81f5dca433
ms.openlocfilehash: bc19fc7496b31eabca6dabedf212c89d6f5450d3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61819276"
---
# <a name="unable-to-read-delimited-fields-because-a-double-quote-is-not-a-legal-delimiter-when-escapequotes-is-set-to-true"></a>EscapeQuotes が True に設定されている場合、二重引用符は有効な区切り記号でないため、区切り記号で分けられたフィールドを読み取れません
引用符 (") が区切り文字として指定されており、 `TextFieldParser` が `EscapeQuotes` に設定されているため、 `True`はファイルからの読み取りができません。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   `EscapeQuotes` を `False` に設定します。  
  
## <a name="see-also"></a>関連項目

- [TextFieldParser.SetDelimiters メソッド](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A)
- [TextFieldParser.Delimiters プロパティ](xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A)
- [方法: コンマ区切りのテキスト ファイルを読み取る](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [TextFieldParser オブジェクト](../../visual-basic/language-reference/objects/textfieldparser-object.md)
