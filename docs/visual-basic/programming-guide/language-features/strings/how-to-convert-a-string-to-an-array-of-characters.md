---
title: '方法: 文字列を文字の配列に変換する'
ms.date: 07/20/2015
helpviewer_keywords:
- character arrays [Visual Basic], converting strings
- arrays [Visual Basic], converting strings to
- examples [Visual Basic], string conversion
- strings [Visual Basic], converting to arrays
- string conversion [Visual Basic], arrays
ms.assetid: 1b54b686-ab29-413b-adce-6bd5422376eb
ms.openlocfilehash: d2f7128f97e576d37216d3aa9736921f13f77004
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352446"
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a>方法: Visual Basic で文字列を文字の配列に変換する
文字列を解析する場合など、文字列の文字と文字列内でのそれらの文字の位置に関するデータがあると便利な場合があります。 この例では、文字列の <xref:System.String.ToCharArray%2A> メソッドを呼び出して、文字列の文字の配列を取得する方法を示します。  
  
## <a name="example"></a>例  
 この例は、文字列を `Char` 配列に分割する方法と、文字列を Unicode テキスト文字の `String` 配列に分割する方法を示しています。 この区別の理由は、Unicode テキスト文字は 2つ以上の `Char` 文字 (サロゲート ペアや結合文字シーケンスなど) で構成できるからです。 詳細については、<xref:System.Globalization.TextElementEnumerator> に関する記事、および「[The Unicode Standard (Unicode 標準)](https://www.unicode.org/standard/standard.html)」をご覧ください。  
  
 [!code-vb[VbVbalrStrings#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#75)]  
  
## <a name="example"></a>例  
 文字列を Unicode テキスト文字に分割する方が難しいですが、文字列の視覚的な表現に関する情報が必要な場合に、これが必要となります。 この例では、<xref:System.Globalization.StringInfo.SubstringByTextElements%2A> メソッドを使用して、文字列を構成する Unicode テキスト文字に関する情報を取得します。  
  
 [!code-vb[VbVbalrStrings#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#76)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.String.Chars%2A>
- <xref:System.Globalization.StringInfo?displayProperty=nameWithType>
- [方法: 文字列の文字にアクセスする](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md)
- [Visual Basic で、文字列型とその他のデータ型との変換を行う](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)
- [文字列](../../../../visual-basic/programming-guide/language-features/strings/index.md)
