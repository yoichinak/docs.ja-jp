---
title: '方法: Visual Basic での文字の配列を文字列に変換します。'
ms.date: 07/20/2015
helpviewer_keywords:
- character arrays [Visual Basic], converting strings
- arrays [Visual Basic], converting strings to
- examples [Visual Basic], string conversion
- strings [Visual Basic], converting to arrays
- string conversion [Visual Basic], arrays
ms.assetid: 1b54b686-ab29-413b-adce-6bd5422376eb
ms.openlocfilehash: 63368f41aec674922ae44a3f1c9816709b981c9b
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974407"
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a>方法: Visual Basic での文字の配列を文字列に変換します。
場合によっては文字、文字列および文字列を解析する際など、文字列内の文字の位置に関するデータを使用すると便利です。 この例を呼び出して、文字列の文字列で文字の配列を取得する方法を示しています。<xref:System.String.ToCharArray%2A>メソッド。  
  
## <a name="example"></a>例  
 文字列を分割する方法を示します、`Char`に文字列を分割する方法と、配列、 `String` Unicode テキスト文字の配列。 この違いの理由は 2 つ以上の Unicode テキスト文字で構成されること`Char`文字 (サロゲート ペアや組み合わせ文字のシーケンス)。 詳細については、次を参照してください。<xref:System.Globalization.TextElementEnumerator>と[Unicode 標準](https://www.unicode.org/standard/standard.html)します。  
  
 [!code-vb[VbVbalrStrings#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#75)]  
  
## <a name="example"></a>例  
 Unicode テキスト文字、文字列を分割することが難しくなりますが、これは、文字列の視覚的表現についての情報が必要な場合に必要です。 この例では、<xref:System.Globalization.StringInfo.SubstringByTextElements%2A>文字列を構成する Unicode 文字に関する情報を取得します。  
  
 [!code-vb[VbVbalrStrings#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#76)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.String.Chars%2A>
- <xref:System.Globalization.StringInfo?displayProperty=nameWithType>
- [方法: 文字列の文字をアクセス](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md)
- [Visual Basic で、文字列型とその他のデータ型との変換を行う](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)
- [文字列](../../../../visual-basic/programming-guide/language-features/strings/index.md)
