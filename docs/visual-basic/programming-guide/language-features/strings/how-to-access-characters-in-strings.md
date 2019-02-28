---
title: '方法: Visual Basic における文字列の文字をアクセス'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: f2831333008844c959c3625698fce6c485450683
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967556"
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a>方法: Visual Basic における文字列の文字をアクセス
この例では、使用、<xref:System.String.Chars%2A>文字列で指定した場所にある文字にアクセスするプロパティ。  
  
## <a name="example"></a>例  
 場合によっては文字、文字列と、文字列内の文字の位置に関するデータを使用すると便利です。 文字の配列としての文字列を考えることができます (`Char`インスタンス); を通じてその文字のインデックスを参照することで特定の文字を取得することができます、<xref:System.String.Chars%2A>プロパティ。  
  
 [!code-vb[VbVbalrStrings#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#49)]  
  
 `index`のパラメーター、<xref:System.String.Chars%2A>プロパティは 0 から始まります。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 <xref:System.String.Chars%2A>プロパティが指定した位置にある文字を返します。 ただし、Unicode 文字の一部は、1 つ以上の文字で表されます。 Unicode 文字を使用する方法の詳細については、次を参照してください。[方法。文字列を文字の配列に変換](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)します。  
  
 <xref:System.String.Chars%2A>プロパティがスローされます、<xref:System.IndexOutOfRangeException>例外場合、`index`パラメーターは、文字列の長さ以上には 0 より小さい場合、または  
  
## <a name="see-also"></a>関連項目
- <xref:System.String.Chars%2A>
- [方法: 文字列を文字の配列に変換します。](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)
- [Visual Basic で、文字列型とその他のデータ型との変換を行う](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)
- [文字列](../../../../visual-basic/programming-guide/language-features/strings/index.md)
