---
title: XML リテラルでの空白文字 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- white space [XML in Visual Basic]
- XML literals [Visual Basic], white space
ms.assetid: dfe3a9ff-d69a-418e-a6b5-476f4ed84219
ms.openlocfilehash: 08be345557d10a528aa03234883eba1b3a31beaa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054940"
---
# <a name="white-space-in-xml-literals-visual-basic"></a>XML リテラルでの空白文字 (Visual Basic)
作成時に、Visual Basic コンパイラは XML リテラルの有意の空白文字だけが組み込まれて、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]オブジェクト。 余分な空白文字は組み込まれません。  
  
## <a name="significant-and-insignificant-white-space"></a>有意の空白文字  
 XML リテラルの空白文字は、のみの 3 つの領域には重要です。  
  
- 属性値に含まれる場合。  
  
- 要素のテキスト コンテンツの一部であるし、テキストには、その他の文字も含まれています。  
  
- 要素のテキスト コンテンツの埋め込み式に含まれる場合。  
  
 それ以外の場合、コンパイラとして意味のない空白文字を処理しでは、含まれません、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]リテラルのオブジェクト。  
  
 余分な空白を XML リテラルに含めるには、文字列リテラルの空白を含む埋め込み式を使用します。  
  
> [!NOTE]
>  場合、 `xml:space` XML 要素リテラルの属性が表示されたら、Visual Basic コンパイラにはで属性が含まれています、<xref:System.Xml.Linq.XElement>オブジェクトが、この属性は、コンパイラによる空白の処理方法を変更していないを追加します。  
  
## <a name="examples"></a>使用例  
 次の例には、外部と内部の 2 つの XML 要素が含まれています。 両方の要素には、そのテキスト コンテンツ内の空白が含まれます。 空白と XML 要素のみが含まれているため、外側の要素内の空白は意味はありません。 空白文字とテキストが含まれているために、内部の要素内の空白は重要です。  
  
 [!code-vb[VbXMLSamples#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#29)]  
  
 実行すると、このコードは、次のテキストを表示します。  
  
```xml  
<outer>  
  <inner>  
                                          Inner text  
                                      </inner>  
</outer>  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic での XML の作成](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
